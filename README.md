<p align="center">
  <img src="assets/logo.png" width="96" height="96" alt="Tablyne" />
</p>

<h1 align="center">Tablyne</h1>

<p align="center"><strong>A desktop database client for Windows, macOS and Linux.</strong><br/>
PostgreSQL, MySQL, SQL Server, MongoDB, Redis, DynamoDB and more, in one native app built in Rust.</p>

<p align="center">
  <a href="https://tablyne.com">Website</a> ·
  <a href="https://tablyne.com/download/">Download</a> ·
  <a href="https://github.com/tablyne/feedback/releases">Releases</a> ·
  <a href="CHANGELOG.md">Changelog</a> ·
  <a href="https://github.com/tablyne/feedback/issues/new/choose">Report a bug</a> ·
  <a href="https://github.com/tablyne/feedback/discussions">Ideas &amp; questions</a>
</p>

---

## 👋 This is the Tablyne community tracker

> **Tablyne is in beta.** Every release is a beta. Apple code signing and notarization are in progress, and the Windows installers are not yet signed with a Microsoft certificate, so macOS and Windows ask you to confirm the first launch once. In-app updates are already signed and verified.

Tablyne itself is closed-source. **This repo is the public home for release notes, installers, bug reports and ideas.**

Tablyne is a desktop database GUI: connect, browse tables and collections, edit data in a grid where your edits wait in review until you press Apply, and run queries in the console. Supported databases:

| Relational | NoSQL and key-value | Analytics and warehouses |
| --- | --- | --- |
| PostgreSQL | MongoDB | Amazon Athena |
| MySQL / MariaDB | Redis / Valkey | ClickHouse |
| SQLite | Amazon DynamoDB | Snowflake |
| SQL Server | Azure Cosmos DB | Google BigQuery |
| | Apache Cassandra / ScyllaDB | Amazon Redshift |
| | | Trino / Presto |

Also through the Postgres and MySQL protocols: Supabase, CockroachDB, YugabyteDB, TiDB, StarRocks and Apache Doris. The full, current list is on [tablyne.com/databases](https://tablyne.com/databases/).

## 📦 Download

- **[tablyne.com/download](https://tablyne.com/download/)** is the official download page: a 14-day trial with every feature, no card and no account. After that, Pro is a perpetual license paid once, with no subscription. See [pricing](https://tablyne.com/pricing/).
- **[Releases](https://github.com/tablyne/feedback/releases)**, from 1.5.0 on, carry the same installers as the site, byte for byte, and the same `SHA256SUMS`: a `.dmg` for Apple Silicon and one for Intel, `-setup.exe` and `.msi` for Windows, `.AppImage`, `.deb` and `.rpm` for Linux (x64). Older releases have the notes only.
- Once installed, Tablyne updates itself: **Help → Check for updates…**.

| System | Requirement |
| --- | --- |
| Windows | Windows 10 or 11, x64 |
| macOS | macOS 12 Monterey or later, Apple Silicon or Intel |
| Linux | x64, glibc 2.35 or later (Ubuntu 22.04, Debian 12, Fedora 36 or newer). No ARM64 build yet |

First launch: on macOS, open Tablyne once, then **System Settings → Privacy & Security → Open Anyway**. On Windows, on "Windows protected your PC", click **More info → Run anyway**. Full steps: [installation guide](https://tablyne.com/docs/installation/).

### Package managers

**macOS, Homebrew**

```bash
brew install --cask tablyne/tap/tablyne
```

The cask installs the same `.dmg` as the site. Tablyne is not notarized yet, so macOS asks you to confirm the first launch once (Privacy & Security → Open Anyway). Tap: [tablyne/homebrew-tap](https://github.com/tablyne/homebrew-tap).

<!-- winget
**Windows, winget**

```powershell
winget install Tablyne.Tablyne
```

The package is the per-machine `.msi`; Windows asks for administrator permission.
-->

**Linux, apt and dnf.** A signed repository at `tablyne.com/repo`: after you add it, `apt upgrade` and `dnf upgrade` bring new versions. The commands are on the [download page](https://tablyne.com/download/#linux) and in the [installation guide](https://tablyne.com/docs/installation/#installing-on-linux). They check the key fingerprint before trusting it.

### Verify the Linux repository key

The repository key (`https://tablyne.com/repo/tablyne.asc`) has this fingerprint:

```
6EB6 F06E BD90 4D13 BDB6  DED1 0C8D 6B84 D7CE 90C5
```

### Verify a download

Every release publishes a `SHA256SUMS` file next to the installers, on the site and in [Releases](https://github.com/tablyne/feedback/releases). Download it to the folder of the installer, then:

```bash
# Linux
sha256sum -c --ignore-missing SHA256SUMS

# macOS (use the name of the file you downloaded)
grep Tablyne_<version>_aarch64.dmg SHA256SUMS | shasum -a 256 -c
```

```powershell
# Windows, PowerShell (use the name of the file you downloaded)
$f = "Tablyne_<version>_x64-setup.exe"
(Get-FileHash $f).Hash -eq ((Select-String -Path SHA256SUMS -Pattern " $f$").Line -split " ")[0]
```

Linux and macOS must print `OK` for your file; Windows must print `True`. Anything else means the file is not the one we published: download it again.

## 🚀 What's new

See the [CHANGELOG](CHANGELOG.md), the [Releases](https://github.com/tablyne/feedback/releases) or the [changelog on the site](https://tablyne.com/changelog/).

## 🐞 Report a bug

[**→ Open a bug report**](https://github.com/tablyne/feedback/issues/new/choose). The form asks for your Tablyne version (Help → About Tablyne), your operating system and the steps to reproduce. Search [existing issues](https://github.com/tablyne/feedback/issues) first, and 👍 the ones you care about: it helps us prioritize.

> ⚠️ **Never paste secrets**: passwords, connection strings, cloud keys, tokens or real data. Mask anything sensitive.

## 💡 Ideas and questions

Use [**Discussions**](https://github.com/tablyne/feedback/discussions): feature ideas, a database you'd like Tablyne to support, how-to questions and general feedback. Tell us the problem you're trying to solve. Please search before posting; a bug belongs in [Issues](https://github.com/tablyne/feedback/issues).

For **account, billing or private** matters, email **[support@tablyne.com](mailto:support@tablyne.com)** instead (your Paddle receipt has billing and invoice links).

## 🔒 Security

Please report a vulnerability by email, not in a public issue. See the [security policy](SECURITY.md).

---

<p align="center"><sub>© Tablyne · <a href="https://tablyne.com/privacy/">Privacy</a> · <a href="https://tablyne.com/terms/">Terms</a> · <a href="SECURITY.md">Security</a></sub></p>
