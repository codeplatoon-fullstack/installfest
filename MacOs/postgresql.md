# PostgreSQL

In VS code, inside of your `zsh` terminal. We will install PostgreSQL
by running the following command:

```zsh
    brew install postgresql
```

Now we can make sure PostgreSQL is started:

```zsh
    brew services restart postgresql@14
```

To enter PostgreSQL we will have to enter the postgres account.
```zsh
    #Enter PostgreSQL
    psql postgres
    #You should see your terminal change into:
    postgres=# 
    #To exit PostgreSQL run the following command:
    \q
```
