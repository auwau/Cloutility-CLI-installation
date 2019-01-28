# Cloutility installation (command-line)
This document describes how to install Auwau Cloutility via Microsoft Windows Server's command-line interface (CLI).

First, download the software-installer to your compatible Microsoft Windows Server. Then launch the CLI by pressing the `Windows r` key-combination, typing `cmd` in the input field, and pressing the `enter`/`return` key. Now `cd` into the folder where the software-installer is located.


## Properties
This section details the properties which need to be specified for the software-installer.

IMPORTANT: Please ensure that values are written immediately after the "=", i.e. without a space, e.g. `USER_NAME=Administrator`.

The command-line installer takes the following properties:

- `USER_ACCOUNT_TYPE`=`system` | `currentAccount`.
- `DOMAIN_NAME`=[omit for `system` or Windows user account] | Microsoft Active Directory domain name, e.g. `MYDOMAIN`.
- `USER_NAME`=[omit for `system`] | Name of Microsoft Windows or Active Directory user account, e.g. `Administrator`.
- `USER_PASSWORD`=[omit for `system`] | Password for Microsoft Windows or Active Directory user account, e.g. `Password123`.
- `SERVER_PROP`=AddressForSqlServer\InstanceName, e.g. `.\sqlexpress2017`.
- `PORT_PROP`=Port number, e.g. `1433` | `NULL` (e.g. for Cloutility + SQL on same host-machine).
- `DATABASE_PROP`=Database (name), e.g. `CloudPortal`.
- `SQL_AUTHORIZATION_STYLE`=`TrustedConnection` | `UserDefined`.
- `SQL_USER`=[omit for `TrustedConnection`] | SQL Server Authentication username, e.g. `sa`.
- `SQL_PASSWORD`=[omit for `TrustedConnection`] | SQL Server Authentication password, e.g. `Password123`.


## Format
Remove property/value pairs from the following command according to your configuration.
```
"{software-installer name}.exe" /qn DOMAIN_NAME=%DOMAIN_NAME% USER_ACCOUNT_TYPE=%USER_ACCOUNT_TYPE% USER_NAME=%USER_NAME% USER_PASSWORD=%USER_PASSWORD% SERVER_PROP=%SERVER_PROP% PORT_PROP=%PORT_PROP% DATABASE_PROP=%DATABASE_PROP% SQL_AUTHORIZATION_STYLE=%SQL_AUTHORIZATION_STYLE% SQL_USER=%SQL_USER% SQL_PASSWORD=%SQL_PASSWORD% /L* "C:\Cloutility-install.log"
```


## Examples
- Software-installer build `3649`.


### Cloutility + SQL on same host-machine - SQL Server account with Windows Authentication
```
"Cloutility-v1.0.3649.0.exe" /qn USER_ACCOUNT_TYPE=currentAccount USER_NAME=Administrator USER_PASSWORD=Password123 SERVER_PROP=.\SQLEXPRESS2017 PORT_PROP=NULL DATABASE_PROP=Cloutility SQL_AUTHORIZATION_STYLE=TrustedConnection /L* "C:\Cloutility-install.log"
```
