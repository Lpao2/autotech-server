# Security and publication review

## Before publishing the private project

- Revoke and replace every GitHub personal access token present in source or commit history.
- Rotate qBittorrent, Sonarr, Radarr, Jellyfin, and other service credentials.
- Remove `keys.txt`, `.env`, databases, logs, backups, caches, cookies, and session files.
- Remove license/customer data and references to private license repositories.
- Remove editor swap files and generated runtime data.
- Scan the complete Git history, not only the current working tree.

Recommended local checks:

```bash
git grep -nEi 'token|secret|password|passwd|api[_-]?key|authorization|bearer'
git log -p --all -- . ':!*.png' ':!*.jpg'
```

Tools such as Gitleaks or GitHub secret scanning can provide an additional check, but they do not replace credential rotation after exposure.

## Runtime recommendations

- Bind management APIs to localhost or a trusted private interface.
- Put remote access behind a VPN or authenticated reverse proxy.
- Do not use hard-coded default passwords.
- Use least-privilege tokens and environment-based secret injection.
- Back up persistent configuration before upgrades.
- Avoid unconditional deletion of storage paths during installation.
