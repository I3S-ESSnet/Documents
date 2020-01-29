# Dev track - deployment

[IS2 on GCP](http://i3s-dev.appspot.com/is2/)

## What has been done ?

Create a service account for the IS2 terraforming: terraform-deployment
Create a /terraform directory on the is2 git repo
Create an baseline TF script
Create with the script the DB instance (Postgre 11)
Create the appengine instance
Deploy the container using gcloud CLI
Set the database connection string right

## DB setup with Terraform

...

## Application setup with Terraform

old app.Dockerfile replaced by Dockerfile (naming needed by Appengine cli) ==> we also made sure to have a unique Dockerfile for is2 Java app, environment variables are used to inject specific conf, eg. database connection string.

using also `gcloud` for deployment

## Connection to the DB

We'll follow this guide: https://cloud.google.com/sql/docs/postgres/connect-app-engine

instance name: i3s-dev:europe-west1:is2-master-instance

Public network name: external-access

IT WORKS when using the application.properties file with:

```
spring.datasource.url=jdbc:postgresql:///postgres?cloudSqlInstance=i3s-dev:europe-west1:is2-master-instance&socketFactory=com.google.cloud.sql.postgres.SocketFactory
spring.datasource.username=postgres
spring.datasource.password=postgres
spring.datasource.driverClassName=org.postgresql.Driver
spring.datasource.platform=postgresql
```

TODO make it work with env var in the Dockerfile

Error related to the connection pool, set the `max_connections` flag to `1024` through the UI, it seems it is not possible via the terraform script.

# Resources

https://learn.hashicorp.com/terraform/gcp/build
https://www.terraform.io/docs/providers/google/r/sql_database_instance.html
https://github.com/gruntwork-io/terraform-google-sql/tree/master/examples/postgres-private-ip
https://www.terraform.io/docs/providers/google/guides/provider_reference.html#full-reference
