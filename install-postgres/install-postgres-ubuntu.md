# Install Postgres: Ubuntu v22

Following are instructions for installing Postgresql on Ubuntu v22. These steps should work on most linux systems, however you will have to modify certain commands - perhaps using the `yum` package manager instead of `apt`, or using a different service manager program instead of `systemctl` (controlling systemd).

Much of this guide is borrowed from [this Digital Ocean guide on installing postgres on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-postgresql-on-ubuntu-22-04-quickstart)

Additional resources are:
- https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-database#install-postgresql
- https://ubuntu.com/server/docs/databases-postgresql

## Install postgresql with your package manager

We will install postgresql and its dependencies using our OS's package manager. For Ubuntu this is apt.

```bash
sudo apt update
sudo apt install postgresql 
sudo apt install postgresql-contrib
```

## Check that postgresql is up and running as a service

Postgres should now be installed and set up as a service on our OS. Ubuntu uses systemd to manage services, and we will use systemd via systemctl to confirm postgres is now up and running.

We are going to tell our OS to start a postgresql service in the background every time we log in, and, we are going to confirm it is currently running.
If you are not on Ubuntu, you will have to modify this command.

```bash
sudo systemctl enable --now postgresql
sudo systemctl status postgresql
```

## Configure the postgres service to always run on startup

```bash
https://github.com/codeplatoon-devops/curriculum/tree/main/unsorted/install-postgres

## Check that the psql client is installed & we can use it

psql is a command-line client for connecting to and interacting with postgres. It should have been installed, lets confirm thats the case:

```bash
which psql
psql --version
```

## Create a postgres role & db for our Linux user account

A "postgres" Linux user was created when postgres was installed, along with a "postgres" Postgresql role (aka user), and, a "postgres" database is created in Postgresql by default. 

The way postgres is set up, if you are on a Linux user account **and there is a postgres role with the same name**, you don't need to use a password with psql when connecting to postgres.

We are going to use sudo to, as the "postgres" Linux user, connect to postgres via psql using the "postgres" role (aka user). This role is a postgres super-admin, and, we will use it to make **another** postgres role that has the same name as our **current** linux user account - the one we normally use.

Use whoami to confirm your `<LINUX_USER_NAME>` (by default it may be "ubuntu"), and this is the name of the postgres role we will create.
```bash
whoami
sudo -u postgres createuser --interactive
```

**Say "yes" to being a "super user".**

Lastly, each postgres role needs to be associated with a database. If we create a database with the same name as our new role, when we log in using psql, it will connect to that database by default.

```
sudo -u postgres psql
```

Now, in psql create the db and confirm its there:

```psql
postgres=# CREATE DATABASE <LINUX_USER_NAME>;
postgres=# \l
postgres=# \q
```

## Test that we can easily connect with our new postgres role

Now we should be able to just run `psql` on the command line to connect:

```bash
psql
```

If that works, we are good-to-go!