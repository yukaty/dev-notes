# Git
- [Basic Git Commands](#basic-git-commands)
  - [Show commit logs with options](#show-commit-logs-with-options)
  - [Modify the last commit](#modify-the-last-commit)
  - [Check the URL of remote repo](#check-the-url-of-remote-repo)
  - [Overwrite of local file from origin repo](#overwrite-of-local-file-from-origin-repo)
- [Tips](#tips)
  - [Remove files from Git tracking](#remove-files-from-git-tracking)
  - [Delete .git and Push to a New Repository](#delete-git-and-push-to-a-new-repository)
  - [Clone a repo and Push it to a new repo](#clone-a-repo-and-push-it-to-a-new-repo)
  - [Duplicate a repository](#duplicate-a-repository)
- [Tag](#tag)
  - [Creating a Tag](#creating-a-tag)
  - [Reverting to a Specific Point and Creating a New Branch](#reverting-to-a-specific-point-and-creating-a-new-branch)
- [.gitignore Examples](#gitignore-examples)
  - [Python](#python)

## Basic Git Commands
Basic commands that I tend to forget!

### Show commit logs with options

```
git log --since=2019-03-01 --until=2019-03-31 --author="Karen" --grep="refactor"
```

### Modify the last commit

```
git add .
git commit --amend
git push -f origin master
```

### Check the URL of remote repo
```
git remote -v
```

### Overwrite of local file from origin repo
```
git fetch
git checkout -m <branch> <file>
```

## Tips

### Remove files from Git tracking

The `git rm --cached` command removes files from Git tracking without deleting them from the working directory.

To remove a single file:
```
git rm --cached <filename>
```

To remove an entire directory recursively:
```
git rm -r --cached <directory>/
```

Then commit the changes and push them to the remote repository. Don't forget to add the files and directories to `.gitignore`.

```
git commit -m "Untrack files in .gitignore"
git push
```

### Delete .git and Push to a New Repository
- Scenario: You need a clean start without any previous history.

1. Clone the repository:
   ```
   git clone <EXISTING_REPO_URL>
   ```

2. Move into the cloned directory:
   ```
   cd <CLONED_REPO_NAME>
   ```

3. Delete the `.git` directories recursively:
   ```
   rm -rf .git
   ```

4. Initialize a new Git repository:
   ```
   git init
   git remote add origin <NEW_REPO_URL>
   ```
5. Push files to the new repo:
   ```
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

### Clone a repo and Push it to a new repo

- Scenario: You want to start a new project based on an existing repository.
- The history and commits are preserved except of repository-specific settings.

1. Clone a repo:
    ```
    git clone <REPOSITORY_URL>
    ```
2. Remove the existing remote URL:
    ```
    git remote rm origin
    ```
3. Add a new remote URL:
    ```
    git remote add origin <NEW_URL>
    ```
4. Push some changes to the new repo:
    ```
    git add .
    git commit -m "<comment>"
    git push origin main
    ```

### Duplicate a repository

- Scenario: You need a complete backup of the repository.
- All repository data is duplicated.

1. Create a bare clone of the repository.
   ```
   git clone --bare <OLD_REPO_URL>
   ```
2. Mirror-push to the new repository.
   ```
   cd old-repository.git
   git push --mirror <NEW_REPO_URL>
   ```

## Tag
A tag in a repository is a name that points to a specific commit. You can list all tags with `git tag`

### Creating a Tag
1. Find the commit hash of a specific commit:
   ```
   git log
   ```

2. Create a new tag:
    ```bash
    git tag <tag-name> <commit-hash>

    # To annotate the tag
    git tag -a <tag-name> <commit-hash> -m "Release v2.0"
    ```

3. Push the Tag to GitHub:
    ```bash
    git push origin <tag-name>
    ```

### Reverting to a Specific Point and Creating a New Branch

1. Update the Local Repository to the Latest State
   ```bash
   git pull origin <branch>
   ```
2. Revert to a Specific Point

   ```bash
   git checkout <commit-hash or tag>
   ```
3. Create a New Branch

   ```bash
   git checkout -b <new-branch-name>
   ```
4. Push to GitHub
   ```bash
   git push origin <new-branch-name>
   ```

## .gitignore Examples

### Python
```
# Python files
*.pyc  # Compiled Python bytecode
*.pyo  # Optimized Python bytecode
*.pyd  # Python script made into a Windows DLL
__pycache__ # Directory for Python 3 bytecode

# Django files
db.sqlite3  # SQLite database file for Django
/static     # Directory for static files in Django

# Virtual environment files
venv/      # Directory for a Python virtual environment
.env       # Environment variables

# OS generated files
.DS_Store  # File created by macOS
*~         # Temporary files created by many text editors
```