Installing PostgreSQL
=====================

PostgreSQL is free and open source.  The recommended method of installing PostgreSQL is to use a packaged installer from EnterpriseDB.  This includes download packages for multiple operating systems:

- Linux 32bit
- Linux 64bit
- Windows 32bit
- Windows 64bit
- Mac OSX

| Download | Description |
| -------- | ----------- |
| [EnterpriseDB](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads#windows) | Packaged versions of PostgreSQL, including admin client for multiple operating systems |
| [Source code](https://www.postgresql.org/ftp/source/v9.6.2/) | Source code download for postgreSQL v9.6.2 |

Install using EnterpriseDB (Windows)
---------------------------------------

1. Run the installer
2. When prompted to create a password choose an appropriate password for the service and superuser account.  Further accounts can be created later on if required.
3. The default port is 5432.  Leave this as is unless you need to run on a different port.
4. Leave as the Default Locale
5. Deselect the option to run StackBuilder after the install.

PostgreSQL should now be installed!  By default the EnterpriseDB package comes with pgAdmin 4.  This is the current default client.

Turning off the server
----------------------

When installed, by default the database server will run when the server (or PC) is started.  To change this you can turn off the automatic startup.  In Windows:

1. Open the start menu and search for 'services.msc'.  Run this.
2. Scroll down the list of services and find Postgres.
3. Set Right click > Properties > Startup Type > Manual.
4. Within this properties window you can also start and stop the service.

Linked servers
--------------

When installed, PostgreSQL can be set up on a server to allow remote connection from clients.  It can also handle connections from other database technologies, such as SQL Server.  For example if you wanted to transfer data between clients, or set up databases that queried each other.  This would be using SQL Server Linked Server technology.

For more info on connecting a PostgreSQL database as a linked server see [SQL Server and PostgreSQL linked server configuration](https://www.mssqltips.com/sqlservertip/3662/sql-server-and-postgresql-linked-server-configuration--part-2/).