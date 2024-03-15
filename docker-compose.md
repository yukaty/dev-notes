# Docker Compose

- [Docker Compose](#docker-compose-1)
- [Services](#services)
- [compose.yml](#composeyml)
- [Commands](#commands)


## Docker Compose

Docker Compose is a tool for defining and running multi-container applications.

## Services
Services refer to independent functional units that make up an application, such as:

- Web server
- Database
- Backend application

These services can run as independent containers by Docker Compose.

## compose.yml
Docker Compose uses YAML files to define application services. Using the file, the `docker compose up` command can start multiple services at once.

Example:
```yaml
services:          # the containers that composes your app
  web:             # the name of the first service
    image: "my-web-app:latest"
    ports:         # The ports to expose: <host:container>
      - "5000:5000"
    depends_on:    # Docker Compose will start services in dependency order
      - db         # The web service starts after the db service
  db:              # The name of the second service
    image: "postgres:latest"
    environment:   # the environment variables
      POSTGRES_DB: example_db
      POSTGRES_USER: db_user
      POSTGRES_PASSWORD: secret
```

## Commands

In Compose V2, use `docker compose` instead of `docker-compose`.

- **Build Services**:
  ```bash
  docker compose build
  ```
  Build all services defined in `compose.yml`.

- **Start Services**:
  ```bash
  docker compose up
  ```
  Start services defined in `compose.yml`. Use `-d` for detached mode.

- **Stop Services**:
  ```bash
  docker compose stop
  ```
  Stop running services.

- **Remove Services**:
  ```bash
  docker compose down
  ```
  Stop services and remove containers, networks, and volumes.

- **View Logs**:
  ```bash
  docker compose logs
  ```
  View logs of all services defined in `compose.yml`.

- **Exec:**
  ```
  docker-compose exec [service-name] /bin/bash
  ```
  Execute a command in a running container.

- **Run**:
  ```
  docker compose run --rm [service-name] sh -c "[shell-commands]"
  ```
  Runs a one-off command against a service.

  - `--rm`: Automatically removes the container once the command has finished executing.
  - `[service-name]`: The service where the command should be executed.
  - `sh -c`: A shell command that tells the container to execute the following command.
  - `[shell-commands]`: The actual command being run in the shell.

  - Example:
    ```
    docker compose run --rm app sh -c "python manage.py test"
    ```

