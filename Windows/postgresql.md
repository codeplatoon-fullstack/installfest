# PostgreSQL

In VS code, inside of your `bash` terminal. We will install PostgreSQL
by running the following command:

```bash
    sudo apt install postgresql postgresql-contrib
```

Now we can make sure PostgreSQL is started:

```bash
    sudo service postgresql start
```

To enter PostgreSQL we will have to enter the postgres account, and then enter PostgreSQL.
```bash
    #enter the postgres account
    sudo -i -u postgres
    
    #or
    su postgres

    #enter PostgreSQL(the actual database)
    psql
```

If you'd like to check what port PostgreSQL is running in, you could type in the following on
the terminal:
```bash
    pg_lsclusters
```

A table will pop up on the terminal, under the Owner header look for postgres, then go left
you'll see the Status and after that you'll see the port. Typically the port will be 5432.

In case port 5432 is occupied by a different process run the following:

```bash
    #this will find out what is currently on port 5432 and tell you which PID belongs to you
    netstat -aon | findstr 5432
    
    #it will provide the following
    TCP    [::]:5432[::]:0                 LISTENING       18996
    
    #this will kill the current process using port 5432 
    taskkill /pid 18996 /f <desired pid>
```
