# Heroku

- [Heroku CLI Commands](#heroku-cli-commands)
- [Link to Heroku Git](#link-to-heroku-git)
    - [Checking Current Heroku Git Links](#checking-current-heroku-git-links)
    - [Linking a Heroku App](#linking-a-heroku-app)
- [Deploy Spring Boot App](#deploy-spring-boot-app)
  - [Prepare for deploying with Heroku](#prepare-for-deploying-with-heroku)
  - [Prepare for deploying with Heroku](#prepare-for-deploying-with-heroku-1)
- [JawsDB](#jawsdb)


## Heroku CLI Commands

- `heroku login`
  - Login to Heroku via browser to complete authentication

- `heroku login -i`
  - Login to Heroku using the CLI only

- `heroku apps`
  - Lists all Heroku apps

- `heroku addons`
  - Lists all add-ons that are available for your Heroku applications

- `heroku local web`
  - Starts your application locally using the Heroku Local tool

- `heroku config`
  - Displays the config vars (environment variables) for an application

## Link to Heroku Git
When executing commands with Heroku CLI, it's necessary to specify the application using the `-a` option, basically.

However, if the current directory is linked to a Heroku Git remote, using the `-a` option is unnecessary.

#### Checking Current Heroku Git Links
To verify which Heroku Git remote is linked to the current directory:

```sh
git remote -v
```

#### Linking a Heroku App
To link a Heroku app to the current directory, establish a Heroku Git remote:

```sh
heroku git:remote -a <app_name>
```

This command associates the current directory with the specified Heroku app, simplifying command execution within that directory.


## Deploy Spring Boot App

### Prepare for deploying with Heroku
1. Create `application-prod.properties` for production:
  ```properties
  application-production.properties
  spring.datasource.url=${DB_URL}
  spring.datasource.username=${DB_USERNAME}
  spring.datasource.password=${DB_PASSWORD}
  spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
  spring.sql.init.encoding=utf-8
  spring.sql.init.mode=always

  spring.mail.host=smtp.gmail.com
  spring.mail.port=587
  spring.mail.username=${MAIL_USERNAME}
  spring.mail.password=${MAIL_PASSWORD}
  spring.mail.properties.mail.smtp.auth=true
  spring.mail.properties.mail.smtp.starttls.enable=true
  ```
  Note: Add profiles for dev environment to `.gitignore`.

2. Create `Procfile` to specify the command Heroku will use to start your app:
  ```
  web: java -Dserver.port=$PORT $JAVA_OPTS -jar -Dspring.profiles.active=prod target/*.jar
  ```
  Using `-Dspring.profiles.active`, Spring will load the `application-xxx.properties` file.

3. Create `system.properties` to specify the Java version for Heroku.
  ```
  java.runtime.version=21
  ```

### Prepare for deploying with Heroku

1. Login to Heroku:
```
heroku login -i
```
2. Create an app container on Heroku for deployment:
```
heroku apps:create -a <app-name>
```
3. Heroku officially supports PostgreSQL. To use MySQL, add the JawsDB add-on:
```
heroku addons:create jawsdb:kitefin
```
4. Retrieve the database information:
```
heroku config:get JAWSDB_URL
```
5. Set the environment variables in Heroku to reference in `application-prod.properties`:
```properties
heroku config:set DB_URL=jdbc:mysql://<database hostname>
heroku config:set DB_USERNAME=<database username>
heroku config:set DB_PASSWORD=<database password>
heroku config:set MAIL_USERNAME=<your Gmail address>
heroku config:set MAIL_PASSWORD=<mail password>
```
6. Deploy your application to Heroku:
```
git push heroku main
```
7. Open the application in your browser:
```
heroku open
```


## JawsDB

I added the JawsDB add-on to my app for using MySQL.

Once I tried to see the data on MySQL Workbench, I got an error below:

```
$ mysql -h <hostname> -u <username> -p <default_schema>
Enter password:
ERROR 1226 (42000): User '**********' has exceeded the 'max_user_connections' resource (current value: 10)
```

I tried to free up connections by stopping the app and workbench, but the error still occurred.

The JawsDB official documentation doesn't clearly mention this error. However, it states that the `max_questions` limit for the Free Plan is 3,600 per hour. Once this limit is reached, it will be reset after one hour, allowing queries to be executed again.

What is the difference between 'max_questions' and 'max_user_connections'?

- `max_user_connections` is the maximum number of simultaneous connections that a single user can establish with the database.
- `max_questions` is the maximum number of queries that a single user can execute within an hour.

Okay, I tried login again an hour after getting the error:
```
mysql> SHOW VARIABLES LIKE 'max_user_connections';
+----------------------+-------+
| Variable_name        | Value |
+----------------------+-------+
| max_user_connections | 10    |
+----------------------+-------+
```
When running the `SHOW PROCESSLIST` command, I found running MySQL Workbench requires at least 2 connections. Also, once I logged in the app, the process was reached to 10, but still working.

I'm not sure but it is likely that 'max_user_connections' is also reset every hour.