For our services running on AWS, we have staging and production RDS postgres servers we use for the services.
Rather than creating a new RDS instance per application, we have multiple databases running on the single cluster.

To add a new database, you can look up the credentials in lastpass, and then connect to the db.

After you have connected, you can use the following commands to create a new db for a `service`:

```
create role service with createdb login password 'password';
create database service owner service;
grant all privileges on database service to service;
grant all privileges on database service to rdsadmin;
```

