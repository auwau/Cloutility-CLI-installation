# Cloutility installation (command-line)
This document describes how to install Auwau Cloutility via Microsoft Windows Server's command-line interface (CLI).

First, download the software-installer to your compatible Microsoft Windows Server. Then launch the CLI by pressing the `Windows r` key-combination, typing `cmd` in the input field, and pressing the `enter`/`return` key. Now `cd` into the folder where the software-installer is located.


## Properties
This section details the properties which need to be specified for the software-installer.

IMPORTANT: Please ensure that values are written immediately after the "=", i.e. without a space, e.g. `USER_NAME=Administrator`.

The command-line installer takes the following properties:

- `CLI_USER_ACCOUNT_TYPE`=`system` | `currentAccount`.
- `CLI_DOMAIN_NAME`=[omit for `system` or Windows user account] | Microsoft Active Directory domain name, e.g. `MYDOMAIN`.
- `CLI_USER_NAME`=[omit for `system`] | Name of Microsoft Windows or Active Directory user account, e.g. `Administrator`.
- `CLI_USER_PASSWORD`=[omit for `system`] | Password for Microsoft Windows or Active Directory user account, e.g. `Password123`.
- `CLI_SERVER_PROP`=AddressForSqlServer\InstanceName, e.g. `.\sqlexpress2017`.
- `CLI_PORT_PROP`=Port number, e.g. `1433` | `NULL` (e.g. for Cloutility + SQL on same host-machine).
- `CLI_DATABASE_PROP`=Database (name), e.g. `CloudPortal`.
- `CLI_SQL_AUTHORIZATION_STYLE`=`TrustedConnection` | `UserDefined`.
- `CLI_SQL_USER`=[omit for `TrustedConnection`] | SQL Server Authentication username, e.g. `sa`.
- `CLI_SQL_PASSWORD`=[omit for `TrustedConnection`] | SQL Server Authentication password, e.g. `Password123`.


## Format
Remove property/value pairs from the following command according to your configuration.

> The properties/values `/L*V "C:\Cloutility-install.log` specifies that an installation-log should be written to the specified destination.

### Command format (full GUI, but no input)
```
"{software-installer name}.exe" /norestart /qr CLI_USER_ACCOUNT_TYPE=%USER_ACCOUNT_TYPE% CLI_DOMAIN_NAME=%DOMAIN_NAME% CLI_USER_NAME=%USER_NAME% CLI_USER_PASSWORD=%USER_PASSWORD% CLI_SERVER_PROP=%SERVER_PROP% CLI_PORT_PROP=%PORT_PROP% CLI_DATABASE_PROP=%DATABASE_PROP% CLI_SQL_AUTHORIZATION_STYLE=%SQL_AUTHORIZATION_STYLE% CLI_SQL_USER=%SQL_USER% CLI_SQL_PASSWORD=%SQL_PASSWORD% /L*V "C:\Cloutility-install.log"
```
> The `/qr` flag causes the installer to display the full graphical user-interface, but without requiring any user-input as the remainder of the command contains the required values.

### Command format (no GUI)
```
"{software-installer name}.exe" /norestart /qn CLI_USER_ACCOUNT_TYPE=%USER_ACCOUNT_TYPE% CLI_DOMAIN_NAME=%DOMAIN_NAME% CLI_USER_NAME=%USER_NAME% CLI_USER_PASSWORD=%USER_PASSWORD% CLI_SERVER_PROP=%SERVER_PROP% CLI_PORT_PROP=%PORT_PROP% CLI_DATABASE_PROP=%DATABASE_PROP% CLI_SQL_AUTHORIZATION_STYLE=%SQL_AUTHORIZATION_STYLE% CLI_SQL_USER=%SQL_USER% CLI_SQL_PASSWORD=%SQL_PASSWORD% /L*V "C:\Cloutility-install.log" /passive
```
> The `/qn` flag causes the installer to run without displaying a graphical user-interface.

## Examples
- Software-installer build `4252`.


### Cloutility + SQL on same host-machine - SQL Server account with Windows Authentication
```
"Cloutility-v1.0.4252.0.exe" /norestart /qr CLI_USER_ACCOUNT_TYPE=currentAccount CLI_USER_NAME=Administrator CLI_USER_PASSWORD=Password123 CLI_SERVER_PROP=.\SQLEXPRESS2019 CLI_PORT_PROP=NULL CLI_DATABASE_PROP=Cloutility CLI_SQL_AUTHORIZATION_STYLE=TrustedConnection /L*V "C:\Cloutility-install.log"
```
