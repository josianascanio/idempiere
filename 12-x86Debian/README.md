# iDempiere 12 Debian Installer

This folder contains the iDempiere 12 provisioning script for **Debian 13 (Trixie)** using **Temurin 17**.

> [!IMPORTANT]
> This installer now lives inside the `12` branch under the `12-x86Debian/` folder.
> Use the command below instead of the old branch-based URL.

## Install

```bash
sudo bash -c 'bash <(curl -fsSL https://raw.githubusercontent.com/josianascanio/idempiere/12/12-x86Debian/provision.sh)'
```

## Variant Details

- Target variant: `12-x86Debian`
- Recommended operating system: Debian 13 (Trixie)
- Java package: `temurin-17-jdk`
- Java repository: Adoptium APT repository
- PostgreSQL version: PostgreSQL 15
- Web server: optional Nginx installation
- iDempiere server package: iDempiere 12 daily server package for x86_64

## Java Configuration

This installer uses Temurin 17 instead of `openjdk-17-jdk-headless`.

The script adds the Adoptium repository when Java installation is selected, installs:

```bash
temurin-17-jdk
```

and detects `JAVA_HOME` dynamically from the active `java` binary:

```bash
readlink -f "$(command -v java)"
```

The detected path is written to `idempiereEnv.properties`.

> [!NOTE]
> On Debian 13, `openjdk-17-jdk-headless` may not be available from the default package repositories. This is why this variant uses Temurin 17.

## Additional Dependencies

Compared with the OpenJDK variants, this installer can also install or use:

- `unzip`
- `wget`
- `curl`
- `ca-certificates`
- `lsb-release`
- `apt-transport-https`
- `gpg`

## Local Execution

If you already cloned this repository and are inside this folder, run:

```bash
sudo bash provision.sh
```

## Shared Documentation

For shared requirements, installation flow, troubleshooting, and contributors, see the [main README](../README.md).
