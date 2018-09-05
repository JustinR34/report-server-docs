---
title: Storage Backup
page_title: Storage Backup
description: Telerik Report Server Storage Backup
slug: storage-backup
tags: backup,export
published: True
position: 730
---

# Storage Backup

The Report Server storage contains all user assets. Making a regular backup of the Report Server storage is a good practice to avoid eventual data loss. There are several ways to perform a backup.

## Automatic backup

During product upgrade, the .msi installer performs an [automatic storage backup](installation#backup) if the current product version supports this. It is a good practice not to skip this installation step.

## Backup script

Along with the [storage migration tools](migration-tool), the installer deploys a PowerShell script called **rs-backup.ps1** located in the same *Tools\\* subfolder of the installation directory. The  script is a convenient wrapper of the **migrate.exe** tool for the sole purpose of creating a storage backup. This same script is carried with the product installer when performing the automatic backup.
The script has two optional parameters, first being the product installation folder (defaults to *C:\Program Files (x86)\Progress\Telerik Report Server\*) and second being the destination folder of the produced .zip archive (defaults to a *Backup\* subfolder of the given installation folder). The zip functionality requires PowerShell 5 or later, so if an older PS is used, the resulting backup will be a directory containing the migrated storage in the form of a file storage, which you might archive by other means.
## Manual backup
If the installed version of Report Server does not have the necessary tools for guided backup, you can still perform manual backup. Based on the currently configured storage, you need to take appropriate actions: 
- MS SQL Server storage – Back up the respective database
- Redis storage – Back up the respective database 
- File storage – Copy/Archive the respective folder 
The preconfigured storage type and its parameters like connection string or destination folder can be discovered using the Configuration page of the Report Server management application or examining the *Telerik.ReportServer.Web\ReportServerAdmin.config* configuration file located in the product installation folder.
