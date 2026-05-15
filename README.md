# iDempiere 12 Provisioning Scripts

This repository provides guided provisioning scripts for installing **iDempiere 12** with PostgreSQL 15, Java 17, and an automatically generated runtime environment.

Choose the installer folder that matches your server architecture and operating system.

## Contributors

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/josianascanio">
        <img src="https://github.com/josianascanio.png" width="80" alt="Josian Ascanio" />
        <br />
        <sub><b>Josian Ascanio</b></sub>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/Carl0gonzalez">
        <img src="https://github.com/Carl0gonzalez.png" width="80" alt="Carlo Gonzalez" />
        <br />
        <sub><b>Carlo Gonzalez</b></sub>
      </a>
    </td>
  </tr>
</table>

> [!NOTE]
> Each installer has its own folder with a dedicated `provision.sh` script and variant-specific documentation.

## Available Installers

| Variant | Architecture | Operating system | Java | Details |
| --- | --- | --- | --- | --- |
| `12-x86` | AMD64 / x86_64 | Debian or Ubuntu-compatible systems | OpenJDK 17 | [README](12-x86/README.md) |
| `12-arm` | ARM variant | Debian or Ubuntu-compatible systems | OpenJDK 17 | [README](12-arm/README.md) |
| `12-x86Debian` | AMD64 / x86_64 | Debian 13 (Trixie) | Temurin 17 | [README](12-x86Debian/README.md) |

## Quick Install

Choose the installer that matches your target environment and run the matching command as `root` or with `sudo`.

### 12-x86

```bash
sudo bash -c 'bash <(curl -fsSL https://raw.githubusercontent.com/josianascanio/idempiere/12/12-x86/provision.sh)'
```

### 12-arm

```bash
sudo bash -c 'bash <(curl -fsSL https://raw.githubusercontent.com/josianascanio/idempiere/12/12-arm/provision.sh)'
```

### 12-x86Debian

```bash
sudo bash -c 'bash <(curl -fsSL https://raw.githubusercontent.com/josianascanio/idempiere/12/12-x86Debian/provision.sh)'
```

## What The Installers Do

All installers automate the main steps needed to prepare an iDempiere 12 server:

- Ask for environment parameters through a `whiptail` interface.
- Configure the environment name, base port, installation folder, PostgreSQL host, and `adempiere` database password.
- Optionally install required dependencies.
- Optionally add the official PostgreSQL repository.
- Install or configure Java 17 according to the selected variant.
- Optionally install PostgreSQL 15 and Nginx.
- Download the iDempiere 12 server package.
- Create `idempiereEnv.properties`.
- Run the silent setup, database import, database sync, and database signing scripts.
- Create the `idempiere` system user when needed.
- Create SSH keys for the `idempiere` user.
- Create, enable, and restart a system service for iDempiere.

## General Requirements

- Debian or Ubuntu-compatible server using `apt`.
- `root` access or a user with `sudo` permissions.
- Internet access to download packages, GPG keys, and the iDempiere server package.
- 2 CPU or more recommended.
- 4 GB RAM minimum recommended.
- 20 GB free disk space or more recommended.

> [!NOTE]
> The Debian 13 variant uses Temurin 17 because the traditional OpenJDK package may not be available in that environment.

## Shared Installation Flow

1. Select the folder that matches your target installer.
2. Run the installer command for that folder.
3. Complete the interactive prompts.
4. Review the summary before continuing.
5. Wait for dependency installation and iDempiere setup to complete.
6. Verify that the generated service is running.

## Expected Installation Layout

The installers create an iDempiere home directory using this structure:

```bash
/opt/<folder>/<port>_<environment>
```

Example:

```bash
/opt/sas/80_idempiere
```

The generated service name follows the same `<port>_<environment>` pattern:

```bash
80_idempiere
```

## Service Check

After installation, verify the generated service with:

```bash
systemctl status <service>
```

Example:

```bash
systemctl status 80_idempiere
```

## Troubleshooting

### The service does not start

Check the service status and logs:

```bash
systemctl status <service>
journalctl -u <service> -xe
```

### PostgreSQL does not connect

Verify the configured host, `pg_hba.conf`, user password, and PostgreSQL service status.

### Java is not found

Confirm that the Java package required by the selected variant is installed and available in `PATH`:

```bash
java -version
```

## Variant Documentation

Each folder contains a short README with only the details that differ for that installer:

- [12-x86](12-x86/README.md)
- [12-arm](12-arm/README.md)
- [12-x86Debian](12-x86Debian/README.md)
