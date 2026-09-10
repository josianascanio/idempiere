# iDempiere 13 ARM Installer

This folder contains the iDempiere 13 provisioning script for the `13-arm` variant using **OpenJDK 17**.

> [!IMPORTANT]
> Run this installer on a server prepared for the `13-arm` variant with root or sudo access.

## Install

```bash
sudo bash -c 'bash <(curl -fsSL https://raw.githubusercontent.com/josianascanio/idempiere/13/13-arm/provision.sh)'
```

## Variant Details

- Target variant: `13-arm`
- Java package: `openjdk-17-jdk-headless`
- PostgreSQL version: PostgreSQL 15
- Web server: optional Nginx installation
- iDempiere server package: the iDempiere 13 server package used by this variant

## Java Configuration

This installer uses OpenJDK 17 and writes this fixed Java path to `idempiereEnv.properties`:

```properties
JAVA_HOME=/usr/lib/jvm/java-17-openjdk-arm64
```

If your operating system installs Java in a different path, update `JAVA_HOME` before running iDempiere in production.

## Local Execution

If you already cloned this repository and are inside this folder, run:

```bash
sudo bash provision.sh
```

## Shared Documentation

For shared requirements, installation flow, troubleshooting, and contributors, see the [main README](../README.md).
