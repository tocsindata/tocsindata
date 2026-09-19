# READ THIS FIRST — Mandatory Software Supply-Chain Policy

Humans and AI agents must use pinned, reviewed, reproducible versions. Production installs from committed lockfiles or explicit versions only, never `latest`. Ordinary releases must be at least four days old; major upgrades always require human review. Urgent security exceptions require a recorded reason, reviewer, tests, and rollback.

For npm, use supported Node.js with npm 12+, declare exact `packageManager`/`engines`, run `npm ci`, commit `package-lock.json`, and require this `.npmrc`:
```ini
engine-strict=true
strict-npmrc=true
ignore-scripts=true
min-release-age=4
save-exact=true
package-lock=true
audit=true
fund=false
```
Keep lifecycle hooks disabled by default. Never globally enable scripts for one package or use force, legacy-peer-deps, broad script enabling, or forced audit fixes without approval.

For Composer, use committed `composer.lock`; production runs `composer install --no-dev --no-interaction --no-plugins --no-scripts --prefer-dist --optimize-autoloader`. Disable plugins by default and never run `composer update` in production.

For Python, Ruby, Rust, Go, PowerShell, Homebrew, Chocolatey, Winget, Snap, Flatpak, containers, and vendor installers: pin versions, commit lockfiles, disable hooks where possible, verify ownership/provenance/signatures/checksums/release notes/transitive changes, and deploy reviewed artifacts only. Never pipe remote content into a shell; download, verify, inspect, then execute.

APT/DNF/YUM lack a dependable universal age rule. Permit automatic security updates only from approved official origins; simulate and review ordinary upgrades; prohibit unapproved repositories/keys and OS upgrades inside application deployment scripts. Kernel, database, PHP, web server, SSH, firewall, and control-panel changes require backups, a maintenance window, testing, and rollback. Never bypass authentication, TLS, signatures, or checksums.

cPanel production uses STABLE or LTS, not EDGE/CURRENT. Do not routinely force updates. Review `/etc/cpupdate.conf`, stage where possible, back up, and schedule maintenance.

Pin GitHub Actions to immutable commit SHAs, use minimum permissions and frozen lockfiles, never auto-merge dependency updates, require tests/scans/human review, reject unexpected installers/registries/scripts/binaries, and protect secrets.

Record component, old/new versions, source, release age, provenance, hooks, dependency changes, checks, tests, backup, rollback, reviewer, result, and exceptions. AI agents cannot approve their own exceptions and must report hook risk, pinning, four-day status, tests, rollback, and required human approval. Stricter repository rules prevail.