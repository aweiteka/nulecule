# Wordpress Atomic App

## Requirements

* atomic CLI or other runtime implementation of nulecule spec
* kubectl client on host with access to kubernetes master
* docker client on host

## Running

1. Create an answerfile.conf with these contents. **NOTE:** db_pass for mysql and wordpress must match
```
[general]
provider=kubernetes

[wordpress-app]
db_pass=<yourpasswd>
wp_public_ip=<public IP of a kube node>

[mysql-app]
db_pass=<yourpasswd>
```

1. From the directory in step one, install the app files and review if desired

```
$ [sudo] atomic install aweiteka/wordpress:app
```

1. Run the application.

```
$ [sudo] atomic run aweiteka/wordpress:app
```

1. This should deploy wordpress with mysql on kubernetes. Once everything is state "Running" load the public IP address in a browser.

