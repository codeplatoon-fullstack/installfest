# Installing Postgres on Ubuntu Linux

We will now install PostgreSQL by running the following command:

```bash
$ sudo apt install postgresql postgresql-contrib
```

Before starting the PostreSQL service, a database must be initialized:

```
sudo postgresql-setup --initdb --unit postgresql
```

Start a PostgreSQL instance (in the background) and have it start everytime you log in like so:

```bash
sudo systemctl enable --now postgresql
```

To enter PostgreSQL we will switch our shell user to one named `postgres`, and then we can enter the running PostgreSQL instance.

```bash
# switch to the user `postgres`
$ sudo -i -u postgres

# connect to the running PostgreSQL instance
$ psql
```

If your terminal now looks like it does below, you have succesfully installed PostgreSQL:

```
postgres=#
```

Now we are going at a ROLE in POSTGRES:

```
CREATE ROLE <your user name> LOGIN;
```

To exit out of this environment type

```
postgres=# \q
```

You will still be logged in as the user 'postgres' even after this step, so either close the terminal outright or press `Ctrl-D` to return to the regular terminal environment you began in.
