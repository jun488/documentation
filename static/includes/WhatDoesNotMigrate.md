&newline

Although TrueNAS attempts to keep most of your 13.0-U6.x configuration data when upgrading to TrueNAS 24.04 and later releases, some 13.0-specific items do not transfer.
These are the items that do not migrate from 13.0-U6.x:

* Microsoft OneDrive Cloud Sync credentials and tasks. OneDrive compatibility is not available in TrueNAS.
* FreeBSD GELI encryption. If you have GELI-encrypted pools on your system that you plan to import into TrueNAS 24.04 and later, you must migrate your data from the GELI pool to a non-GELI encrypted pool before migrating to TrueNAS.
* Malformed certificates. TrueNAS validates the system certificates when a 13.0-U6.x system migrates to 24.04 or later. When a malformed certificate is found, TrueNAS generates a new self-signed certificate to ensure system accessibility.
* 13.0-U6.x plugins and jails. Save the configuration information for your plugin and back up any stored data.
  After completing the TrueNAS 24.04 or later install, add the equivalent TrueNAS application using the **Apps** option.
  If your 13.0-U6.x plugin is not listed as an available application in TrueNAS, use the **Custom App** option to add it as an application and import data from the backup into a new TrueNAS dataset for the application.
* NIS data.
* System tunables.
* ZFS boot environments.
* SMB auxiliary parameters. As of TrueNAS 23.10 (Cobia), the **Auxiliary Parameters** option is no longer available in the UI as a configurable option.
  We recommend removing any auxiliary parameter settings in 13.-U6.x before migrating to TrueNAS 24.10 or earlier.
* AFP shares also do not transfer, but migrate into an SMB share with AFP compatibility enabled.
* 13.0-U6.x `netcli` utility. A new CLI utility is used for the Console Setup Menu and other commands issued in a CLI.
  By default, any TrueNAS user account with `netcli` as the chosen Shell updates to use the `nologin` option instead.
  See the Users Screens reference article for descriptions of all Shell options.
* SAS multipath is not supported in TrueNAS 24.04 and later.
* TrueNAS 13 account names beginning with a number are not supported in TrueNAS 24.04 and later.
  Usernames in 24.04 and later must begin with a letter or an underscore. Before attempting a migration, review the local user accounts and rename or replace any accounts that begin with a numeric character (0-9).
* VM storage and its basic configuration transfer over during a migration, but you need to double-check the VM configuration and the network interface settings specifically before starting the VM.