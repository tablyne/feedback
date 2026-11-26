# Security policy

## Reporting a vulnerability

Please **do not open a public issue or discussion** for a security problem. Email
**[support@tablyne.com](mailto:support@tablyne.com)** (the contact in
[tablyne.com/.well-known/security.txt](https://tablyne.com/.well-known/security.txt)) with:

- the Tablyne version (Help → About Tablyne) and your operating system,
- what you found and the steps to reproduce it,
- the impact you expect (for example: code execution, leaking a saved connection password, a write that skips the review before Apply).

Do not send real passwords, connection strings, cloud keys or data from your databases; a minimal example is enough.

We aim to acknowledge a report within a few days, tell you what we decided, and credit you in the release notes
if you want. Please give us reasonable time to ship a fix before you disclose the problem publicly.

## Supported versions

Only the latest release, available at [tablyne.com/download](https://tablyne.com/download/), receives security
fixes. Every release is a beta. Tablyne checks for updates itself (Help → Check for updates…), and in-app updates
are signed and verified.

## Scope

Tablyne itself (the desktop app for Windows, macOS and Linux, its installers, the apt and dnf repository at
tablyne.com/repo) and tablyne.com. Problems in the databases and services Tablyne connects to belong with their
own maintainers.
