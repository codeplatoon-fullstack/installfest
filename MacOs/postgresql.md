# PostgreSQL

In VS code, inside of your `bash` terminal. We will install PostgreSQL
by running the following command:

```bash
    brew install postgresql
```

Now we can make sure PostgreSQL is started:

```bash
    brew services restart postgresql@14
```

To enter PostgreSQL we will have to enter the postgres account.
```bash
    #Enter PostgreSQL
    psql postgres
    #You should see your terminal change into:
    postgres=# 
    #To exit PostgreSQL run the following command:
    \q
```
