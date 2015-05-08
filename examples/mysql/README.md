# MySQL Atomic App

## Requirements

* atomic CLI or other runtime implementation of nulecule spec
* kubectl client on host with access to kubernetes master
* docker client on host

## Using as composite application

Many times you want to use a database as part of an application such as wordpress. You may use this as a component in your application. Use the following snippet in your `Nulecule` file.

```
graph:
  mysql-app:
    source: docker://aweiteka/mysql:app
```

## Running standalone

1. Create an answerfile.conf with these contents. **NOTE:** db_pass for mysql and wordpress must match
```
[general]
provider=kubernetes

[mysql-app]
db_pass=<yourpasswd>
```

1. From the directory in step one, install the app files and review if desired

```
$ [sudo] atomic install aweiteka/mysql:app
```

1. Run the application.

```
$ [sudo] atomic run aweiteka/mysql:app
```

1. This should deploy mysql on kubernetes.

