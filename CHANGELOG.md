# Changelog

All notable changes to Tablyne, newest first. Every release is a beta. Downloads and checksums: [Releases](https://github.com/tablyne/feedback/releases) or <https://tablyne.com/download/>.

## 1.5.2 — 2026-11-26

Tablyne v1.5.2 (beta). A cleaner object tree and sidebar, the same in every database.

### Object tree

- The vertical guide lines are gone. Indentation shows the hierarchy.
- Counts and actions sit at the right edge of each row. The ⋯ menu takes their place on hover, keyboard focus or selection, so no row keeps empty space for it. Right-click and Shift+F10 still open the menu.

### Sidebar

- Database icons are drawn cleaner and at the same size, with a new PostgreSQL elephant.
- The database picker and the filter have a thin, subtle border that gets stronger on hover. The active connection shows the selection tone and a thin accent line.

### Structure tab

- Columns, Foreign keys, Indexes and the other views use the same tabs as the rest of the app: no box around the active one, and one style for counts. In narrow windows, inactive tabs show only the icon and the count, with the name in the tooltip.

### Console

- "Loading draft…" no longer flashes when you open the console.

## 1.5.1 — 2026-11-25

Tablyne v1.5.1 (beta). Safe mode no longer gets in the way, and an open transaction is always visible in the console.

### Safe mode

- New connections start with No confirmation, in every database and environment. Existing connections keep the level they have.
- The confirmation dialog has "Don't confirm again on this connection". Tick it to save No confirmation and run. To undo it, open Edit connection › Safe mode.
- Changing only the safe mode no longer reconnects. Your tabs keep their database, schema and open transactions.
- Typing the connection name in production is asked only when the connection's level asks for confirmation. Trino and Redshift follow the same level.
- The database's own confirmations still apply at every level: the system keyspace in CQL, Replace on import and grid DELETE in production.

### Console

- An open transaction always shows in the status bar under the editor, with how long it has been open, Commit and Rollback. It stays readable in narrow windows and split panes.
- The cursor position moves to the More menu when the status bar is too narrow, so the transaction state keeps its place.

## 1.5.0 — 2026-11-25

Tablyne v1.5.0 (beta). A lighter, more consistent interface across every database, menus that follow your operating system, and Linux packages you can install and update with apt or dnf.

### Look and feel

- A lighter design. Lines and outlines are 1 px, and the focus ring is a thin line in the brand color.
- One type scale for the whole app. Titles are the only bold text. Controls, menus and the object tree use the same size everywhere.
- Grids look the same in every database. Data, Structure, Indexes and the other grids share the same header, row height and checkbox.
- Key columns carry the same marker in every grid: PK for the primary key, SK for the DynamoDB sort key, and CK for Cassandra clustering columns. Copy with headers gives the plain column name.

### Console

- Run and the other actions sit above the editor, with Run on the left. Below the editor, a thin status bar shows the transaction and the run details.
- Drag the divider between the editor and the result to resize them.

### Tables and the object tree

- Data and Structure are tabs at the top of the table tab. The footer fits in one line, and the grid options are in one menu.
- The column editor in Structure uses the same grid as Data.
- Each object in the tree takes one line, with a ⋯ menu for its actions. Pinning is in that menu. Every database shows the same menu, in the same order.
- The Ask AI panel is compact and looks the same in all seven places where it opens.
- Activity is the same view in every database that has it.

### Connections

- When Test fails, the connection form shows the reason in the same box for every database. PostgreSQL and Redshift add Diagnose. Long error messages scroll inside the box.

### Menus

- On macOS, Tablyne uses the native menu bar. On Linux, the window has the system title bar. Windows is unchanged.

### Linux

- New: an apt and dnf repository at tablyne.com/repo, signed with GPG. The download page has the commands to add it. They check the key fingerprint before trusting it. After that, apt upgrade and dnf upgrade bring new versions.
- The .rpm is signed with the same key. The .deb and .rpm now declare the system libraries they need, so apt and dnf install them.
- The packages include AppStream data and a valid desktop entry, so software centers list Tablyne with its name, icon and description.

### Privacy

- Telemetry is now on by default, except in the EU, EEA, UK and Switzerland. It sends usage counters, errors and crashes with a pseudonymous ID. It never sends queries, data or credentials. Turn it off in Settings › Security and privacy.

### Fixes

- The JSON preview on hover stays anchored to its cell.
- Status labels in the object tree are no longer in capital letters.
- The trial counter counts calendar days to the end date.

## 1.4.0 — 2026-11-23

Tablyne v1.4.0 — a new console, the same table tab and object tree in every database, and clearer connection errors.

### Console

- The console has one strip right under the editor, the same in every database that has a console. Run, Cancel, Format, AI and the other controls sit there, and nothing covers your code.
- A new Queries menu holds Save, Open file, Saved and Recent in one searchable list. Run has a ▾ with Run all.
- PostgreSQL now uses the same console as the other SQL databases, so every improvement reaches all of them. Pinned results now work in all SQL consoles too.

### Tables

- The table tab looks and works the same in every database. Data and Structure are two views you switch at the bottom of the tab.
- The object tree has one icon for each kind of object and the same section names in every database. Row actions are easier to hit, and nothing was removed.
- In MySQL and MariaDB, the many actions of a database moved from its row to a ⋯ menu.

### Look

- Fewer outlines. Buttons, panels and bars rest without a frame and show hover and pressed states by tone. Outlines stay on form fields and wherever they are needed to read the limit.
- The selected tab or view has a clear 2 px underline.

### DynamoDB

- Switching a table to provisioned mode sends the read and write capacity of the table and of each index.
- AWS errors arrive in plain words, with the original text under "Technical details", also in the PartiQL console.
- Bulk delete, edit and script runs now stay open when something fails and show how many items were already written. The grid reloads when anything was saved.
- Table groups show their count, and long names are shortened in the middle.

### Connections

- When a PostgreSQL connection fails, Tablyne says why: no response, name not found, refused, TLS problem, wrong credentials or dropped. The message has Diagnose, Try again and Edit connection.
- Passwords and tokens are masked in error messages, logs and diagnostics.

### Fixes

- The entity list in the Builder no longer squeezes the entity name when keys are long.

## 1.3.4 — 2026-11-21

Tablyne v1.3.4 — calmer production signals, PartiQL like the SQL consoles, and a connection rail you can reorder.

### Production connections

- A quiet "production" pill next to the connection name, and a slim notice only where you can write — consoles, editable grids, import, item editor, restore and structure editors: "Production · <connection> — changes ask for confirmation". No more red lines or tinted editors.
- Read-only production connections say so; with safe mode off, the notice says changes may apply without confirmation.

### DynamoDB PartiQL

- In a table, PartiQL is a compact filter bar with Run (⌘↵) and "Open in console", like the SQL filter of other databases.
- The PartiQL console looks and works like the SQL consoles: status line, Output panel, results and errors in their own tabs. Writes show their target and outcome in Output.
- DynamoDB writes, and the previews and reads that prepare them (such as a copy's source table), now use one snapshot of your AWS credentials for both the account check and the requests. If it expires mid-operation, the write stops instead of renewing credentials. Browsing and read-only queries keep using your profile's credentials as before.

### Connections

- Drag the connection icons on the left to reorder them (or Alt+↑/↓). The same order is used by the hub, the connection switcher and Ctrl/⌘+1–9.

### App

- The toolbar above every database tree fits on one line: filter, Refresh, + (now a menu when there is more than one thing to create), Activity and "More actions" with each database's tools grouped by name.
- Help › Check for updates… (also in the command palette) checks right away instead of only at launch.
- On macOS, scrollbars no longer cover buttons and fields at the right edge of panels (for example, Settings › Appearance).

### Privacy

- The v1.3.3 notes called usage statistics anonymous. They are pseudonymous: a random install id that changes every month, never linked to your license or email, and only sent if you opt in.

## 1.3.3 — 2026-11-19

Tablyne v1.3.3 — DynamoDB local and cloud endpoints are never mixed, and clearer trial insights.

### DynamoDB

- With LOCAL on, every command of the connection uses the local endpoint: reads, PartiQL, writes, batches, imports and copies. Before, reads used the local endpoint while writes and PartiQL used the saved one.
- Write confirmations name the endpoint that will receive the change, and switching LOCAL/cloud after the preview refuses the write.
- In split view, each tab reads with its own connection's account and endpoint.
- Backups are created through the connection's own endpoint.

### Usage statistics (only with your consent)

- Anonymous trial steps (trial started, first connection, active days, trial ended, buy and export clicks) help us improve the trial. No names, ids or device data are sent.

## 1.3.2 — 2026-11-19

Tablyne v1.3.2 — one console button everywhere, mixed tabs, clearer production and connection status, and the same value previews in every database.

### Consoles and tabs

- A console button in the connection bar, in the same place for every database, named after its language: SQL, PartiQL, Mongo Shell, CQL, T-SQL or Redis CLI. "+" and Ctrl+T still work.
- Tabs can be grouped by connection (default) or all together. Together, every tab shows its connection name and colour, and switching tab switches the connection.
- "Collapse all" in the sidebar tree of every database (Ctrl/⌘+Alt+−).

### Connection status

- TLS is shown as a quiet lock state (verified, encrypted, not encrypted) instead of a constant warning; it turns amber only for production connections at risk.
- Production is clearer: a PRODUCTION badge in the connection bar, a red top line on its tabs and a subtle tint in the editor.
- The unexplained square on connection icons is gone; open tabs are listed in the tooltip.

### Value previews

- Hovering a value shows the same preview in every database: JSON (including JSON stored as text, e.g. DynamoDB strings), arrays and sets, long text, binary, time zones and epoch numbers.
- DynamoDB shows maps, lists and sets as plain JSON when reading; copying and exporting keep the exact types.

## 1.3.1 — 2026-11-18

Tablyne v1.3.1 — a 14-day free trial of everything, plans you can manage, and a consistent workspace across databases.

### Trial and license

- Every new device gets a 14-day free trial with every feature, starting at the first launch. No card.
- The trial is shown in the title bar with the days left, and reminders arrive at 7, 3 and 1 day. It works up to 24 hours offline.
- After the trial, Tablyne needs a license. Without one, the License screen and the export of your saved connections and queries keep working; nothing is deleted.
- Pro is a one-time purchase. License (Help › License) shows your plan, the license on this device, receipts and billing.
- The e-mail with your key has a link that opens Tablyne and fills the key for you.

### Team and devices

- Invites and devices show the e-mail, an alias you choose and the computer name, instead of an id. You can rename your devices.

### Workspace

- DynamoDB: "+" opens a PartiQL console like the SQL consoles of other databases; "Open in console" turns the current search into PartiQL; the Search/PartiQL switch stays visible; the page size now applies to PartiQL.
- "Query (SELECT …)" in the table menu of every database with a console.
- Hovering a JSON, nested, time-zone or epoch value shows the same preview in every database.
- Editing a cell shows "Editing — Enter confirms · Esc cancels" instead of an empty bar.

### Fixes

- Usage statistics (only with your consent) arrive complete and correct; the event viewer was removed from the menu.

## 1.3.0 — 2026-11-18

Tablyne v1.3.0 — Pro trial, plans you can manage, and identifiable devices.

### Plans and license

- Free stays free: the editor, the grid, review before apply and copying between connections.
- Pro features: DynamoDB on AWS, pg_dump / pg_restore, file import and schema diff.
- The first time you use a Pro feature you can start a 14-day Pro trial, with no card. The trial needs to be online to start and to keep running; if the check-in fails, the app pauses the Pro features and offers "Try again".
- License (Help › License) shows your plan, the trial days left and the license on this device. A lifetime key now shows as "Pro (perpetual license)".
- "Receipts and billing" opens the payment portal to update the card, see receipts or cancel.
- The e-mail with your key has a link that opens Tablyne and fills the key for you.

### Team and devices

- Invites and devices show the e-mail, an alias you choose ("Ana's laptop") and the computer name, instead of an id.
- You can rename your devices. The computer name is sent only with license calls, never with usage statistics, and it is visible only to the account owner, the member and Tablyne support.

### Fixes

- Usage statistics (only with your consent) arrive complete and correct; the event viewer was removed from the menu.

## 1.2.1 — 2026-11-17

Tablyne v1.2.1 — fixes for the first public beta.

### Install and updates

- macOS: the app no longer opens as "damaged". The whole bundle is now signed (ad hoc) and every release checks the signature inside the .dmg before it is published. macOS still asks you to confirm the first launch once (System Settings › Privacy & Security › Open Anyway).
- The app no longer registers itself as the default opener for data files it cannot open yet.
- Linux packages describe Tablyne as a multi-database client.
- Each release now publishes a SHA256SUMS file next to the installers.

### License and plan

- License (Help › License) and About now show your current plan, whether a trial applies and the license on this device.
- When a license is refused, the panel says why (revoked, refunded, device removed, seat suspended) and what to do, instead of asking you to check your connection.
- At the device limit you can free one of the key's devices from the new machine and activate there.
- "Lost your key?" sends it again to the e-mail of the purchase.
- A key pasted with line breaks or spaces is accepted.

### Fixes

- Moving the mouse to another menu while a menu is open now switches menus.
- Third-party licenses and release notes are rendered as formatted text.
- After a conflict, a successful apply clears the "nothing was applied" warning.

## 1.2.0 — 2026-11-15

Tablyne v1.2.0 — one native client for your whole data stack, not just DynamoDB.

### New databases

- Relational: SQL Server, plus Supabase, CockroachDB, YugabyteDB, TiDB, StarRocks and Apache Doris through their Postgres/MySQL protocols.
- Cloud warehouses: Snowflake, BigQuery, Redshift, Athena and Trino.
- Document, key-value and wide-column: MongoDB, Azure Cosmos DB, Redis and Cassandra / ScyllaDB (Keyspaces and Astra included).
- ClickHouse.

### What's new

### Grid and editing

- The same spreadsheet-style grid across engines: edit cells, review the generated statement or command, then apply with Ctrl+S.
- Find a value across a table or collection from the regular search bar, including MongoDB and Cosmos DB.
- Copy rows to another connection where the engine allows it. Where it doesn't, the action is disabled and says why.
- Tree, table and JSON views for results in MongoDB and Cosmos DB.
- Redis: create a key from the "New key" dialog (string, hash, list, set, sorted set or stream, with an optional TTL). You review the exact commands before they run, and an existing key is never overwritten.

### Query console

- Consoles with syntax highlighting, autocomplete, EXPLAIN plans and engine-specific dialects.
- An AI assistant available in every console, set up in one step, with your own API key or a local model through Ollama, which needs no key.
- A built-in MCP server lets your AI tools reach selected connections, with per-connection access, a separate revocable token for each AI client and an activity log.

### Schema and design

- Table designers and DDL review for the new engines, including choosing where a new MySQL/MariaDB column goes.
- Schema compare with a sync script for MySQL/MariaDB.
- Interactive ER diagrams with a minimap, keyboard navigation and table comments.
- Browse programmability objects (SQL Server, CQL types and functions) with read-only definitions.

### Import, export and backup

- Export and import for tables and collections, with progress in the job center.
- PostgreSQL exports read each table in one consistent snapshot, and a multi-table export reads all tables from the same moment, without holding a table's lock after that table is written.
- CSV import and export for Cassandra tables, with TTL-aware Redis export and import.
- Backup and restore screens for MySQL and SQLite.
- Import connections from DBeaver, DataGrip, pgAdmin and Azure Data Studio.

### Connections and security

- SSH tunnels (and AWS SSM) across more engines.
- Kerberos for MongoDB, Trino and SQL Server; browser sign-in (OIDC) for MongoDB; AWS IAM authentication for MySQL/MariaDB on RDS and Aurora.
- Step-by-step connection diagnosis for MongoDB: DNS, SSH, TCP, TLS and authentication.
- App lock with an access code and automatic locking.

### Safety

- Connections marked as production ask for confirmation before imports and destructive commands.
- Read-only connections are clearly marked, and the badge shows how to fix it.
- Cost guard for BigQuery queries before they run.
- Writes to Supabase-managed schemas need an explicitly confirmed target.
- CSV and Excel exports protect against formula injection by default, for every database: text a spreadsheet would run as a formula (`=`, `+`, `-`, `@`) is neutralized, while numbers like `-1` stay numbers. Turn it off in the export dialog when you need the raw value (the console's `\copy … TO` starts with it off, like psql).

### Interface

- Pinned databases in the catalog trees and a pending-changes bar that shows what will be saved.

### System requirements

- macOS: requires macOS 12 (Monterey) or later. Separate downloads for Apple Silicon and Intel.
- Windows 10 or 11 (x64).
- Linux x64 AppImage: glibc 2.35 or later (Ubuntu 22.04, Debian 12, Fedora 36 or newer).

### Breaking changes

- macOS 11 (Big Sur) is no longer supported: Tablyne 1.2.0 requires macOS 12 or later (the bundled PostgreSQL tools need it).
- Exports: the old saved export preference `csv.escapeFormulas: false` is ignored. Formula protection is now one option, on by default for .csv and .xlsx; turn it off per export if you need the raw value.
- SQLite: `REGEXP` now works only in queries (grid, console, export). Views, triggers, CHECK constraints, indexes and generated columns that call `REGEXP` stop working ("unsafe use of regexp()"), because the function is registered by Tablyne and must not become part of the file's schema.
- SQLite: for numbers, `REGEXP` matches against the same text as `CAST(x AS TEXT)`.
- PostgreSQL export: the table filter ("where…") now always runs in a read-only transaction, also without a raw `WHERE`. A filter that calls `nextval()` or a function that writes is refused by the server.

### Known limits

- PostgreSQL export: the transaction that holds the export's snapshot keeps the cleanup horizon (`xmin`) for the whole export, so `VACUUM` cannot remove row versions that changed after it started. An export that runs for hours on a cluster with heavy writes can accumulate bloat.
- Copy to another connection is not available for Cassandra/ScyllaDB or Cosmos DB.
- Some write actions are disabled with an explanation where the database has no equivalent (for example, transactions or Duplicate on Redis variants without COPY).
- CockroachDB: browsing, grid edits, the console, ER diagrams and data export work. Structure changes (DDL), dump, restore, import and manual transactions are not available. The connection bar lists the limits.
- ClickHouse: the grid does not write to tables without a UUID (Ordinary or Lazy databases). Tablyne refuses the write and sends nothing. Use a table in an Atomic or Replicated database.
- Cassandra, ScyllaDB, Amazon Keyspaces and Astra: the grid refuses to edit a cell that reads as NULL and sends nothing (an empty collection also reads as NULL). Edit that cell from the console.
- Initialization SQL accepts only session commands: SET, RESET and SET ROLE on PostgreSQL; SET on MySQL and SQL Server.

## 1.0.1 — 2026-06-25

### New

- **Item Editor v2** — inferred columns, colour-coded keys, rich JSON editing, an entity picker, type pills, and quick-add field chips.
- **Export / Import config** — back up your themes, labels, saved queries, AI providers and preferences to JSON, and restore them with a per-row diff.
- **Windows standalone** — a no-install portable `.exe` alongside the regular installer.

### Improved

- Item Editor: modified-state is now visible on every tab, a ←/→ field navigator, a prominent add-field action, autofocus on new fields, and clearer save / undo hints.
- Grid: `Cmd/Ctrl+I` adds a new row, with clearer inline edit feedback.

### Fixed

- Item Editor: key-order stability, blank-key data loss, stable field ids, PK-prefix round-trip, and rename metadata.
- Correct app / bundle name capitalisation.

## 1.0.0 — 2026-06-23

Meet Tablyne — DynamoDB, finally enjoyable.

A small, fast, native app that turns DynamoDB from a console-clicking chore into a modern workflow.

### What's in v1.0.0

- Every AWS account, region and SSO profile in one window.
- Browse and edit tables in a fast, spreadsheet-style grid.
- Search with a visual builder — or full PartiQL with autocomplete.
- Describe what you want in plain English; Tablyne writes the query.
- Model your schema with entities, relationships and access patterns. Export the IaC.
- Migrate indexes safely, with a live, guided backfill.
- Bulk-edit with a dry-run preview — nothing changes until you say so.
- Restore from snapshots or point-in-time into a new table.
- A live stream of your data, kept open while you work.
- See costs the way you'll pay them — provisioned vs on-demand, per entity.
- Multi-tab workspace, command palette, history, code generation, JS REPL.
- Beautiful themes (and a custom theme editor), in pt / en / es.
