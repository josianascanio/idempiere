# iDempiere 12 x86 Installer

This folder contains the iDempiere 12 provisioning script for **AMD64 / x86_64** servers using **OpenJDK 17**.

> [!IMPORTANT]
> This installer now lives inside the `12` branch under the `12-x86/` folder.
> Use the command below instead of the old branch-based URL.

## Install

```bash
sudo bash -c 'bash <(curl -fsSL https://raw.githubusercontent.com/josianascanio/idempiere/12/12-x86/provision.sh)'
```

## Variant Details

- Target variant: `12-x86`
- Java package: `openjdk-17-jdk-headless`
- PostgreSQL version: PostgreSQL 15
- Web server: optional Nginx installation
- iDempiere server package: iDempiere 12 daily server package for x86_64

## Java Configuration

This installer uses OpenJDK 17 and writes this fixed Java path to `idempiereEnv.properties`:

```properties
JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
```

If your operating system installs Java in a different path, update `JAVA_HOME` before running iDempiere in production.

## Local Execution

If you already cloned this repository and are inside this folder, run:

```bash
sudo bash provision.sh
```

## Shared Documentation

For shared requirements, installation flow, troubleshooting, and contributors, see the [main README](../README.md).
