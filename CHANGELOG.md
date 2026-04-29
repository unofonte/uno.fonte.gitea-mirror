# Changelog

## 2026-04-30 — Security hardening

- **Removed unconditional `urllib3.disable_warnings()`** — previously called at module load time, suppressing TLS warnings even when SSL verification was enabled.
- **Added interactive confirmation for `--insecure`** — the user must now type `yes` to proceed with disabled TLS verification. Aborts on anything else or on `Ctrl+C`/`EOF`.
- **Removed duplicate `dotenv` loading** — a dead `try/except` block imported `dotenv` and called `load_dotenv()` a second time (the import had already succeeded at module level).
- **Reduced information leakage in error output** — `add_push_mirror()` no longer dumps raw API response bodies to stdout. `process_repo()` now logs only the exception type name instead of the full exception message.
