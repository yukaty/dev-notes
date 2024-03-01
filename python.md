# Python

- [venv](#venv)


## venv
`venv` is a tool in Python that allows you to create isolated environments. Each environment can have its own installed packages. It is useful to work on multiple projects that require different versions of the same package.

```sh
mkdir webenv
python3 -m venv webenv
source webenv/bin/activate
```
If you want to deactivate the virtual env
```sh
deactivate
```
