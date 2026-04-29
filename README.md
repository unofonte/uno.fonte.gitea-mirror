original source [**sudden-che/gitea-mirror**](https://github.com/sudden-che/gitea-mirror)

[README-RU](README-RU.md)

---

# Gitea Push Mirror Automation

A Python script for automating Push Mirror replication of repositories between two Gitea instances.

## 🔧 Features

- Fetches **all available repositories** for a user: personal, organizational, private.
- Creates missing repositories on the target Gitea.
- Sets up Push Mirror with `sync_on_commit`.
- Skips repositories if mirrors are already configured.
- Supports `--dry-run` and `--insecure` modes.
- Works via the REST API, using `Authorization: token ...` headers.

---

## 🚀 Getting Started

1. Install dependencies:

```bash
pip install -r requirements.txt
```

1. Copy `.env` file:

```bash
cp .env.example .env
```

or create `.env` file:

```bash
# .env
#SRC_GITEA_URL=https://source-gitea.tld
SRC_GITEA_URL=http://localhost:3000   # or https if you have SSL locally
SRC_GITEA_TOKEN=TOKEN_GITEA_SOURCE

DEST_GITEA_URL=https://destination-gitea.tld
DEST_GITEA_TOKEN=TOKEN_GITEA_DESTINATION
DEST_GITEA_USER=your-user
```

3. Run the script:

```bash
python mirror_script.py --insecure           # ignore SSL errors
python mirror_script.py --dry-run            # simulate actions, no changes
python mirror_script.py --dry-run --insecure
```

---

## Script Behavior

- Checks whether each repository exists on the target.
- Creates the repository if it doesn't exist.
- Does not re-add an existing push mirror.
- Outputs diagnostic messages on authorization errors.
