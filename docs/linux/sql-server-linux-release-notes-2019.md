---
title: Release notes for SQL Server 2019 on Linux
description: This article contains the release notes and supported features for SQL Server 2019 running on Linux. Release notes are included for the most recent release and several previous releases.
author: rwestMSFT
ms.author: randolphwest
ms.reviewer: vanto
ms.date: 05/16/2022
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
---
# Release notes for SQL Server 2019 on Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md)]

The following release notes apply to [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] running on Linux. This article is broken into sections for each release. Each release has a link to a support article describing the CU changes as well as links to the Linux package downloads.

> [!TIP]
> To learn about new Linux features in [!INCLUDE [sssql19-md](../includes/sssql19-md.md)], see [What's new in SQL Server 2019](../sql-server/what-s-new-in-sql-server-2019.md?preserve-view=true&view=sql-server-ver15#sql-server-on-linux).

## Supported platforms

[!INCLUDE [linux-supported-platforms-2019](../includes/linux-supported-platforms-2019.md)]

## Tools

Most existing client tools that target SQL Server can seamlessly target SQL Server running on Linux. Some tools might have a specific version requirement to work well with Linux. For a full list of SQL Server tools, see [SQL Tools and Utilities for SQL Server](../tools/overview-sql-tools.md).

## Release history

The following table lists the release history for [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] releases.

| Release                   | Version       | Release date |
|---------------------------|---------------|--------------|
| [CU16](#cu16)             | 15.0.4223.1   | 2022-05-16   |
| [CU15](#cu15)             | 15.0.4198.2   | 2022-01-27   |
| [CU14](#cu14)             | 15.0.4188.2   | 2021-11-22   |
| [CU13](#cu13)             | 15.0.4178.1   | 2021-10-05   |
| [CU12](#cu12)             | 15.0.4153.1   | 2021-08-04   |
| [CU11](#cu11)             | 15.0.4138.2   | 2021-06-10   |
| [CU10](#cu10)             | 15.0.4123.1   | 2021-04-06   |
| [CU9](#cu9)               | 15.0.4102.2   | 2021-02-10   |
| [CU8-GDR](#cu8-GDR)       | 15.0.4083.2   | 2021-01-12   |
| [CU8](#cu8)               | 15.0.4073.23  | 2020-10-07   |
| [CU7 (Removed)](https://support.microsoft.com/help/4570012)     | 15.0.4063.15  | 2020-09-02   |
| [CU6](#cu6)               | 15.0.4053.23  | 2020-08-04   |
| [CU5](#cu5)               | 15.0.4043.16  | 2020-06-22   |
| [CU4](#cu4)               | 15.0.4033.1   | 2020-03-31   |
| [CU3](#cu3)               | 15.0.4023.6   | 2020-03-12   |
| [CU2](#cu2)               | 15.0.4013.40  | 2020-02-13   |
| [CU1](#cu1)               | 15.0.4003.23  | 2020-01-07   |
| [GA](#ga)                 | 15.0.2000.5   | 2019-11-04   |

## <a id="cuinstall"></a> How to install updates

If you have configured the CU repository (`mssql-server-2019`), then you will get the latest CU of SQL Server packages when you perform new installations. If you require Docker container images, see official images for [Microsoft SQL Server on Linux for Docker Engine](https://hub.docker.com/r/microsoft/mssql-server/). For more information about repository configuration, see [Configure repositories for SQL Server on Linux](sql-server-linux-change-repo.md).

If you are updating existing SQL Server packages, run the appropriate update command for each package to get the latest CU. For specific update instructions for each package, see the following installation guides:

- [Install SQL Server package](sql-server-linux-setup.md#upgrade)
- [Install Full-text Search package](sql-server-linux-setup-full-text-search.md)
- [Install SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Install SQL Server 2019 Machine Learning Services R and Python support on Linux](sql-server-linux-setup-machine-learning.md)
- [Install PolyBase package](../relational-databases/polybase/polybase-linux-setup.md)
- [Enable SQL Server Agent](sql-server-linux-setup-sql-agent.md)

## <a id="cu16"></a> CU16 (May 2022)

This is the Cumulative Update 16 (CU16) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4223.1. For information about the fixes and improvements, see <https://support.microsoft.com/help/5011644>.

> [!IMPORTANT]  
> TDE-compressed backups that are made by using [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] CU 16 and later cannot be restored to previous CU versions of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. For more information, see [FIX: Error 3241 occurs during executing RESTORE LOG or RESTORE DATABASE](https://support.microsoft.com/help/5014298).
>
> Transparent Data Encryption (TDE)-compressed backups that are made by using previous CU versions of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] can still be restored by using [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] CU 16 and later versions.

> [!WARNING]  
> The **adutil** tool has been removed from [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] on Linux for CU 16, and will be reintroduced in a future Cumulative Update. However, you can still [install **adutil** manually](sql-server-linux-ad-auth-adutil-introduction.md#installing-adutil).

### Package details

For manual or offline package installations, you can download the RPM and Debian packages for the latest supported distributions, with the information in the following table.

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4223.1-2 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4223.1-2.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4223.1-2.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4223.1-2.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4223.1-2.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4223.1-2.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4223.1-2.x86_64.rpm)|
| **SLES v15 RPM packages**<br /><br />(Get [SLES v12 RPM packages](https://packages.microsoft.com/sles/12/mssql-server-2019/)) | 15.0.4223.1-2 | [Database Engine RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-15.0.4223.1-2.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-ha-15.0.4223.1-2.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-fts-15.0.4223.1-2.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-extensibility-15.0.4223.1-2.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-extensibility-java-15.0.4223.1-2.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-polybase-15.0.4223.1-2.x86_64.rpm)|
| **Ubuntu 20.04 Debian packages**<br /><br />(Get [Ubuntu 18.04 Debian packages](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/)) | 15.0.4223.1-2 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4223.1-2_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4223.1-2_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4223.1-2_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4223.1-2_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4223.1-2_amd64.deb)</br>[PolyBase Debian Package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4223.1-2_amd64.deb)|

## <a id="cu15"></a> CU15 (January 2022)

This is the Cumulative Update 15 (CU15) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4198.2. This update adds improvements in capturing memory dumps on unexpected crashes in [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] on Linux. For information about the fixes and improvements, see <https://support.microsoft.com/help/5008996>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4198.2-10 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4198.2-10.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4198.2-10.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4198.2-10.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4198.2-10.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4198.2-10.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4198.2-10.x86_64.rpm)|
| **SLES v15 RPM packages**<br /><br />(Get [SLES v12 RPM packages](https://packages.microsoft.com/sles/12/mssql-server-2019/)) | 15.0.4198.2-10 | [Database Engine RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-15.0.4198.2-10.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-ha-15.0.4198.2-10.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-fts-15.0.4198.2-10.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-extensibility-15.0.4198.2-10.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-extensibility-java-15.0.4198.2-10.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-polybase-15.0.4198.2-10.x86_64.rpm)|
| **Ubuntu 20.04 Debian packages**<br /><br />(Get [Ubuntu 18.04 Debian packages](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/)) | 15.0.4198.2-10 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4198.2-10_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4198.2-10_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4198.2-10_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4198.2-10_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4198.2-10_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4198.2-10_amd64.deb)|

## <a id="cu14"></a> CU14 (November 2021)

This is the Cumulative Update 14 (CU14) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4188.2. For information about the fixes and improvements, see <https://support.microsoft.com/help/5007182>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

> [!NOTE]  
> **SLES v15** is now supported on [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] starting with CU14. The offline package installation links for SLES are pointing to SLES 15 packages. If you are looking for SLES 12 packages, refer to the download path <https://packages.microsoft.com/sles/12/mssql-server-2019/>

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4188.2-3 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4188.2-3.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4188.2-3.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4188.2-3.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4188.2-3.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4188.2-3.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4188.2-3.x86_64.rpm)|
| **SLES v15 RPM packages**<br /><br />(Get [SLES v12 RPM packages](https://packages.microsoft.com/sles/12/mssql-server-2019/)) | 15.0.4188.2-3 | [Database Engine RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-15.0.4188.2-3.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-ha-15.0.4188.2-3.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-fts-15.0.4188.2-3.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-extensibility-15.0.4188.2-3.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-extensibility-java-15.0.4188.2-3.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/15/mssql-server-2019/mssql-server-polybase-15.0.4188.2-3.x86_64.rpm)|
| **Ubuntu 20.04 Debian packages**<br /><br />(Get [Ubuntu 18.04 Debian packages](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/)) | 15.0.4188.2-3 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4188.2-3_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4188.2-3_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4188.2-3_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4188.2-3_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4188.2-3_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4188.2-3_amd64.deb)|

## <a id="cu13"></a> CU13 (October 2021)

This is the Cumulative Update 13 (CU13) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4178.1. For information about the fixes and improvements, see <https://support.microsoft.com/help/5005679>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4178.1-3 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4178.1-3.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4178.1-3.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4178.1-3.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4178.1-3.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4178.1-3.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4178.1-3.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4178.1-3 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4178.1-3.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4178.1-3.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4178.1-3.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4178.1-3.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4178.1-3.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4178.1-3.x86_64.rpm)|
| **Ubuntu 20.04 Debian packages**<br /><br />(Get [Ubuntu 18.04 Debian packages](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/)) | 15.0.4178.1-3 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4178.1-3_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4178.1-3_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4178.1-3_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4178.1-3_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4178.1-3_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4178.1-3_amd64.deb)|

## <a id="cu12"></a> CU12 (August 2021)

This is the Cumulative Update 12 (CU12) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4153.1. For information about the fixes and improvements, see <https://support.microsoft.com/help/5004524>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4153.1-6 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4153.1-6.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4153.1-6.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4153.1-6.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4153.1-6.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4153.1-6.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4153.1-6.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4153.1-6 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4153.1-6.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4153.1-6.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4153.1-6.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4153.1-6.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4153.1-6.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4153.1-6.x86_64.rpm)|
| **Ubuntu 20.04 Debian packages**<br /><br />(Get [Ubuntu 18.04 Debian packages](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/)) | 15.0.4153.1-6 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4153.1-6_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4153.1-6_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4153.1-6_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4153.1-6_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4153.1-6_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4153.1-6_amd64.deb)|

## <a id="cu11"></a> CU11 (June 2021)

This is the Cumulative Update 11 (CU11) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4138.2. For information about the fixes and improvements, see <https://support.microsoft.com/help/5003249>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4138.2-1 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4138.2-1.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4138.2-1.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4138.2-1.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4138.2-1.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4138.2-1.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4138.2-1.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4138.2-1 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4138.2-1.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4138.2-1.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4138.2-1.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4138.2-1.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4138.2-1.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4138.2-1.x86_64.rpm)|
| **Ubuntu 20.04 Debian packages**<br /><br />(Get [Ubuntu 18.04 Debian packages](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/)) | 15.0.4138.2-1 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4138.2-1_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4138.2-1_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4138.2-1_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4138.2-1_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4138.2-1_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4138.2-1_amd64.deb)|

## <a id="cu10"></a> CU10 (April 2021)

This is the Cumulative Update 10 (CU10) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4123.1. For information about the fixes and improvements, see <https://support.microsoft.com/help/5001090>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

> [!NOTE]  
> **Ubuntu 20.04** is now supported on [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] starting with CU10. The offline package installation links for Ubuntu are pointing to Ubuntu 20.04 packages. If you are looking for Ubuntu 18.04 packages, refer to the download path <https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/>

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4123.1-5 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4123.1-5.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4123.1-5.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4123.1-5.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4123.1-5.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4123.1-5.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4123.1-5.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4123.1-5 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4123.1-5.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4123.1-5.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4123.1-5.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4123.1-5.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4123.1-5.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4123.1-5.x86_64.rpm)|
| **Ubuntu 20.04 Debian packages**<br /><br />(Get [Ubuntu 18.04 Debian packages](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/)) | 15.0.4123.1-5 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4123.1-5_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4123.1-5_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4123.1-5_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4123.1-5_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4123.1-5_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/20.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4123.1-5_amd64.deb)|

## <a id="cu9"></a> CU9 (February 2021)

This is the Cumulative Update 9 (CU9) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4102.2. For information about the fixes and improvements, see <https://support.microsoft.com/help/5000642>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4102.2-4 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4102.2-4.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4102.2-4.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4102.2-4.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4102.2-4.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4102.2-4.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4102.2-4.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4102.2-4 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4102.2-4.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4102.2-4.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4102.2-4.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4102.2-4.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4102.2-4.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4102.2-4.x86_64.rpm)|
| **Ubuntu 18.04 Debian packages**<br /><br />(Get [Ubuntu 16.04 Debian packages](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/)) | 15.0.4102.2-4 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4102.2-4_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4102.2-4_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4102.2-4_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4102.2-4_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4102.2-4_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4102.2-4_amd64.deb)|

## <a id="cu8-GDR"></a> CU8-GDR (January 2021)

This is the Cumulative Update 8-GDR (CU8-GDR) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4083.2. For information about the fixes and improvements, see <https://support.microsoft.com/help/4577194>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4083.2-15 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4083.2-15.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4083.2-15.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4083.2-15.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4083.2-15.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4083.2-15.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4083.2-15.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4083.2-15 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4083.2-15.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4083.2-15.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4083.2-15.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4083.2-15.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4083.2-15.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4083.2-15.x86_64.rpm)|
| **Ubuntu 18.04 Debian packages**<br /><br />(Get [Ubuntu 16.04 Debian packages](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/)) | 15.0.4083.2-15 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4083.2-15_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4083.2-15_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4083.2-15_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4083.2-15_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4083.2-15_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4083.2-15_amd64.deb)|

## <a id="cu8"></a> CU8 (September 2020)

This is the Cumulative Update 8 (CU8) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4073.23. For information about the fixes and improvements, see <https://support.microsoft.com/help/4577194>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4073.23-4 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4073.23-4.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4073.23-4.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4073.23-4.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4073.23-4.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4073.23-4.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4073.23-4.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4073.23-4 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4073.23-4.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4073.23-4.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4073.23-4.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4073.23-4.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4073.23-4.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4073.23-4.x86_64.rpm)|
| **Ubuntu 18.04 Debian packages**<br /><br />(Get [Ubuntu 16.04 Debian packages](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/)) | 15.0.4073.23-4 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4073.23-4_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4073.23-4_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4073.23-4_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4073.23-4_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4073.23-4_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4073.23-4_amd64.deb)|

## <a id="cu6"></a> CU6 (July 2020)

This is the Cumulative Update 6 (CU6) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4053.23. For information about the fixes and improvements, see <https://support.microsoft.com/help/4563110>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4053.23-2 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4053.23-2.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4053.23-2.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4053.23-2.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4053.23-2.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4053.23-2.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4053.23-2.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4053.23-2 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4053.23-2.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4053.23-2.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4053.23-2.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4053.23-2.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4053.23-2.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4053.23-2.x86_64.rpm)|
| **Ubuntu 18.04 Debian packages**<br /><br />(Get [Ubuntu 16.04 Debian packages](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/)) | 15.0.4053.23-2 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4053.23-2_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4053.23-2_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4053.23-2_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4053.23-2_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4053.23-2_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4053.23-2_amd64.deb)|

## <a id="cu5"></a> CU5 (June 2020)

This is the Cumulative Update 5 (CU5) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4043.16. For information about the fixes and improvements, see <https://support.microsoft.com/help/4552255>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4043.16-4 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4043.16-4.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4043.16-4.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4043.16-4.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4043.16-4.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4043.16-4.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4043.16-4.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4043.16-4 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4043.16-4.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4043.16-4.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4043.16-4.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4043.16-4.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4043.16-4.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4043.16-4.x86_64.rpm)|
| **Ubuntu 18.04 Debian packages**<br /><br />(Get [Ubuntu 16.04 Debian packages](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/)) | 15.0.4043.16-4 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4043.16-4_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4043.16-4_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4043.16-4_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4043.16-4_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4043.16-4_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4043.16-4_amd64.deb)|

## <a id="cu4"></a> CU4 (April 2020)

This is the Cumulative Update 4 (CU4) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4033.1. For information about the fixes and improvements, see <https://support.microsoft.com/help/4548597>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4033.1-2 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4033.1-2.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4033.1-2.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4033.1-2.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4033.1-2.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4033.1-2.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4033.1-2.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4033.1-2 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4033.1-2.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4033.1-2.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4033.1-2.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4033.1-2.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4033.1-2.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4033.1-2.x86_64.rpm)|
| **Ubuntu 18.04 Debian packages**<br /><br />(Get [Ubuntu 16.04 Debian packages](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/)) | 15.0.4033.1-2 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4033.1-2_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4033.1-2_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4033.1-2_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4033.1-2_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4033.1-2_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4033.1-2_amd64.deb)|

## <a id="cu3"></a> CU3 (March 2020)

This is the Cumulative Update 3 (CU3) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4023.6. For information about the fixes and improvements, see <https://support.microsoft.com/help/4538853>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

> [!NOTE]  
> **Ubuntu 18.04** is now supported on [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] starting with CU3. The offline package installation links for Ubuntu are pointing to Ubuntu 18.04 packages. If you are looking for Ubuntu 16.04 packages, refer to the download path <https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/>

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4023.6-2 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4023.6-2.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4023.6-2.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4023.6-2.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4023.6-2.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4023.6-2.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4023.6-2.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4023.6-2 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4023.6-2.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4023.6-2.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4023.6-2.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4023.6-2.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4023.6-2.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4023.6-2.x86_64.rpm)|
| **Ubuntu 18.04 Debian packages**<br /><br />(Get [Ubuntu 16.04 Debian packages](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/)) | 15.0.4023.6-2 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4023.6-2_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4023.6-2_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4023.6-2_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4023.6-2_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4023.6-2_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/18.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4023.6-2_amd64.deb)|

## <a id="cu2"></a> CU2 (February 2020)

This is the Cumulative Update 2 (CU2) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4013.40. For information about the fixes and improvements, see <https://support.microsoft.com/help/4536075>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4013.40-8 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4013.40-8.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4013.40-8.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4013.40-8.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4013.40-8.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4013.40-8.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4013.40-8.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4013.40-8 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4013.40-8.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4013.40-8.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4013.40-8.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4013.40-8.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4013.40-8.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4013.40-8.x86_64.rpm)|
| **Ubuntu 16.04 Debian packages** | 15.0.4013.40-8 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4013.40-8_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4013.40-8_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4013.40-8_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4013.40-8_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4013.40-8_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4013.40-8_amd64.deb)|

## <a id="cu1"></a> CU1 (January 2020)

This is the Cumulative Update 1 (CU1) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.4003.23. For information about the fixes and improvements in this release, see <https://support.microsoft.com/en-us/help/4527376>.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

> [!NOTE]  
> Starting with CU1, the offline package installation links for Red Hat are pointing to RHEL 8 packages. If you are looking for RHEL 7 packages, refer to the download path <https://packages.microsoft.com/rhel/7/mssql-server-2019/>

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 8.x RPM packages**<br /><br />(Get [RHEL 7.x RPM packages](https://packages.microsoft.com/rhel/7/mssql-server-2019/)) | 15.0.4003.23-3 | [Database Engine RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4003.23-3.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4003.23-3.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4003.23-3.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4003.23-3.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4003.23-3.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4003.23-3.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.4003.23-3 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4003.23-3.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4003.23-3.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4003.23-3.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4003.23-3.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4003.23-3.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4003.23-3.x86_64.rpm)|
| **Ubuntu 16.04 Debian packages** | 15.0.4003.23-3 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4003.23-3_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4003.23-3_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4003.23-3_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4003.23-3_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4003.23-3_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4003.23-3_amd64.deb)|

## <a id="ga"></a> GA (November 2019)

This is the General Availability (GA) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)]. The SQL Server Database Engine version for this release is 15.0.2000.5.

### Package details

For manual or offline package installations, you can download the RPM and Debian packages with the information in the following table:

| Package | Package version | Downloads |
|-----|-----|-----|
| **RHEL 7.x RPM packages** | 15.0.2000.5-5 | [Database Engine RPM package](https://packages.microsoft.com/rhel/7/mssql-server-2019/mssql-server-15.0.2000.5-5.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/rhel/7/mssql-server-2019/mssql-server-ha-15.0.2000.5-5.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/rhel/7/mssql-server-2019/mssql-server-fts-15.0.2000.5-5.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/rhel/7/mssql-server-2019/mssql-server-extensibility-15.0.2000.5-5.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/rhel/7/mssql-server-2019/mssql-server-extensibility-java-15.0.2000.5-5.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/rhel/7/mssql-server-2019/mssql-server-polybase-15.0.2000.5-5.x86_64.rpm)|
| **SLES v12 RPM packages** | 15.0.2000.5-5 | [Database Engine RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.2000.5-5.x86_64.rpm)</br>[High Availability RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.2000.5-5.x86_64.rpm)</br>[Full-Text Search RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.2000.5-5.x86_64.rpm)</br>[Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.2000.5-5.x86_64.rpm)</br>[Java Extensibility RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.2000.5-5.x86_64.rpm)</br>[PolyBase RPM package](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.2000.5-5.x86_64.rpm)|
| **Ubuntu 16.04 Debian packages** | 15.0.2000.5-5 | [Database Engine Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.2000.5-5_amd64.deb)</br>[High Availability Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.2000.5-5_amd64.deb)</br>[Full-Text Search Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.2000.5-5_amd64.deb)</br>[Extensibility Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.2000.5-5_amd64.deb)</br>[Java Extensibility Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.2000.5-5_amd64.deb)</br>[PolyBase Debian package](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.2000.5-5_amd64.deb)|

## Known issues

The following sections describe known issues with the General Availability (GA) release of [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] on Linux.

### General

- The length of the hostname where [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is installed needs to be 15 characters or less.

    - **Resolution**: Change the name in /etc/hostname to something 15 characters long or less.

- Manually setting the system time backwards in time will cause [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to stop updating the internal system time within [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

  - **Resolution**: Restart [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

- Only single instance installations are supported.

  - **Resolution**: If you want to have more than one instance on a given host, consider using VMs or Docker containers.

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager can't connect to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Linux.

- The default language of the **sa** login is English.

  - **Resolution**: Change the language of the **sa** login with the **ALTER LOGIN** statement.

- OLEDB provider logs the following warning: `Failed to verify the Authenticode signature of 'C:\binn\msoledbsql.dll'. Signature verification of SQL Server DLLs will be skipped. Genuine copies of SQL Server are signed. Failure to verify the Authenticode signature might indicate that this is not an authentic release of SQL Server. Install a genuine copy of SQL Server or contact customer support.`

  - **Resolution**: No action is required. The OLEDB provider is signed using SHA256. SQL Server Database engine doesn't validate the signed .dll correctly.

### Databases

- The `master` database can't be moved with the mssql-conf utility. Other system databases can be moved with mssql-conf.

- When restoring a database that was backed up on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Windows, you must use the **WITH MOVE** clause in the Transact-SQL statement.

- Certain algorithms (cipher suites) for Transport Layer Security (TLS) do not work properly with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Linux. This results in connection failures when attempting to connect to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], as well as problems establishing connections between replicas in high availability groups.

  - **Resolution**: Modify the **mssql.conf** configuration script for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Linux to disable problematic cipher suites, by doing the following:

  1. Add the following to /var/opt/mssql/mssql.conf.

     ```ini
     [network]
     tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
     ```

     > [!NOTE]  
     > In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.

  1. Restart [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with the following command.

     ```bash
     sudo systemctl restart mssql-server
     ```

- [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] databases on Windows that use In-memory OLTP cannot be restored on [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] on Linux. To restore a [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] database that uses in-memory OLTP, first upgrade the databases to [!INCLUDE[sssql15-md](../includes/sssql16-md.md)], SQL Server 2017, or [!INCLUDE [sssql19-md](../includes/sssql19-md.md)] on Windows before moving them to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Linux via backup/restore or detach/attach.

- User permission **ADMINISTER BULK OPERATIONS** is not supported on Linux at this time.

### Networking

Features that involve outbound TCP connections from the `sqlservr` process, such as linked servers, PolyBase, or Availability Groups, might not work if both the following conditions are met:

1. The target server is specified as a hostname and not an IP address.

1. The source instance has IPv6 disabled in the kernel. To verify if your system has IPv6 enabled in the kernel, all the following tests must pass:

   - `cat /proc/cmdline` will print the boot cmdline of the current kernel. The output must not contain `ipv6.disable=1`.
   - The /proc/sys/net/ipv6/ directory must exist.
   - A C program that calls `socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` should succeed - the syscall must return an fd != -1 and not fail with EAFNOSUPPORT.

The exact error depends on the feature. For linked servers, this manifests as a login timeout error. For Availability Groups, the `ALTER AVAILABILITY GROUP JOIN` DDL on the secondary will fail after 5 minutes with a download configuration timeout error.

To work around this issue, do one of the following:

1. Use IPs instead of hostnames to specify the target of the TCP connection.

1. Enable IPv6 in the kernel by removing `ipv6.disable=1` from the boot cmdline. The way to do this depends on the Linux distribution and the bootloader, such as grub. If you do want IPv6 to be disabled, you can still disable it by setting `net.ipv6.conf.all.disable_ipv6 = 1` in the `sysctl` configuration (for example, `/etc/sysctl.conf`). This will still prevent the system's network adapter from getting an IPv6 address, but allow the `sqlservr` features to work.

#### Network File System (NFS)

If you use **Network File System (NFS)** remote shares in production, note the following support requirements:

- Use NFS version **4.2 or higher**. Older versions of NFS do not support required features, such as `fallocate` and sparse file creation, common to modern file systems.
- Locate only the **/var/opt/mssql** directories on the NFS mount. Other files, such as the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] system binaries, are not supported.
- Ensure that NFS clients use the `nolock` option when mounting the remote share.

### Localization

- If your locale is not English (en_us) during setup, you must use UTF-8 encoding in your bash session/terminal. If you use ASCII encoding, you might see an error similar to the following:

  ```output
  UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
  ```

  If you can't use UTF-8 encoding, run setup using the MSSQL_LCID environment variable to specify your language choice.

  ```bash
  sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
  ```

- When running mssql-conf setup, and performing a non-English installation of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], incorrect extended characters are displayed after the localized text, "Configuring SQL Server...". Or, for non-Latin based installations, the sentence might be missing completely. The missing sentence should display the following localized string: "The licensing PID was successfully processed. The new edition is [\<Name\> edition]". This string is output for information purposes only, and the next [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Cumulative Update will address this for all languages. This doesn't affect the successful installation of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in any way.

#### Full-Text Search

- Not all filters are available with this release, including filters for Office documents. For a list of supported filters, see [Install SQL Server Full-Text Search on Linux](sql-server-linux-setup-full-text-search.md#filters).

### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- The **mssql-server-is** package is not supported on SUSE in this release. It's currently supported on Ubuntu and on Red Hat Enterprise Linux (RHEL).

- With [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on Linux CTP 2.1 Refresh and later, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages can use ODBC connections on Linux. This functionality has been tested with the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the MySQL ODBC drivers, but is also expected to work with any Unicode ODBC driver that observes the ODBC specification. At design time, you can provide either a DSN or a connection string to connect to the ODBC data; you can also use Windows authentication. For more info, see the [blog post announcing ODBC support on Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- The following features aren't supported in this release when you run SSIS packages on Linux:
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Catalog database
  - Scheduled package execution by SQL Agent
  - Windows Authentication
  - Third-party components
  - Change Data Capture (CDC)
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Scale Out
  - Azure Feature Pack for SSIS
  - Hadoop and HDFS support
  - Microsoft Connector for SAP BW

For a list of built-in SSIS components that are not currently supported, or that are supported with limitations, see [Limitations and known issues for SSIS on Linux](sql-server-linux-ssis-known-issues.md#components).

For more info about SSIS on Linux, see the following articles:

- [Blog post announcing SSIS support for Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
- [Install SQL Server Integration Services (SSIS) on Linux](sql-server-linux-setup-ssis.md)
- [Extract, transform, and load data on Linux with SSIS](sql-server-linux-migrate-ssis.md)

### <a id="ssms"></a> SQL Server Management Studio (SSMS)

The following limitations apply to [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] on Windows connected to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Linux.

- Maintenance plans aren't supported.

- Management Data Warehouse (MDW) and the data collector in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] aren't supported.

- [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] UI components that have Windows Authentication or Windows event log options don't work with Linux. You can still use these features with other options, such as SQL logins.

- Number of log files to retain can't be modified.

## Next steps

To get started, see the following quickstarts:

- [Install on Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Install on SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Install on Ubuntu](quickstart-install-connect-ubuntu.md)
- [Run on Docker](quickstart-install-connect-ubuntu.md)
- [Provision a SQL VM in Azure](/azure/azure-sql/virtual-machines/linux/sql-vm-create-portal-quickstart?toc=/sql/toc/toc.json)
- [Run & Connect - Cloud](quickstart-install-connect-clouds.md)

For answers to frequently asked questions, see the [SQL Server on Linux FAQ](sql-server-linux-faq.yml).