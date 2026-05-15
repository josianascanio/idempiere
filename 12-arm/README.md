# iDempiere 12 ARM Installer

This folder contains the iDempiere 12 provisioning script for the `12-arm` variant using **OpenJDK 17**.

> [!IMPORTANT]
> Run this installer on a server prepared for the `12-arm` variant with root or sudo access.

## Install

```bash
sudo bash -c 'bash <(curl -fsSL https://raw.githubusercontent.com/josianascanio/idempiere/12/12-arm/provision.sh)'
```

## Variant Details

- Target variant: `12-arm`
- Java package: `openjdk-17-jdk-headless`
- PostgreSQL version: PostgreSQL 15
- Web server: optional Nginx installation
- iDempiere server package: the iDempiere 12 server package used by this variant

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
