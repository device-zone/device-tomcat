# device-tomcat

Provides the base for server appliances based on Apache Tomcat.

Tomcat appliances do the following:

- All parameters passed to the device commands are syntax checked and canonicalised, with bash completion.
- Each tomcat appliance runs in a discrete tomcat, independent of each other.
- Binds securely to the unix domain socket /tmp/.s.tomcat-[application]-[instance]
- Autostarts on server restart.
- Zero Trust configuration.

Each application is implemented in discrete appliances that depend on this one.

# device-tomcat-docs

An example of a service that exposes the Apache Tomcat documentation web application.

This appliance extension does the following:

- All parameters passed to the device commands are syntax checked and canonicalised,
  with bash completion.
- Allows setting of a path where the docs will be hosted.
- Requires of the setting of a database connection, as provided by the Postgresql Appliance
  at: https://github.com/device-zone/device-postgresql
- The database connection is not used, but demonstrates how it might be configured and
  passed into Tomcat.

## before

- Deploy the device-tomcat-docs package.

```
[root@server ~]# dnf install device-tomcat-docs
```

## add instance

To add an instance called "my-tomcat-docs" hosted at path /my-tomcat-docs, run this.

```
[root@server ~]# device services app tomcat-docs add name=my-tomcat-docs path=/tomcat-docs database=my-database
```

## remove instance

To remove an instance called "my-tomcat-docs", run this.

```
[root@server ~]# device services app tomcat-docs remove my-tomcat-docs
```


