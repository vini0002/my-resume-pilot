# Overleaf Integration Guide (Optional)

AI Resume Pilot can automatically sync tailored `.tex` files to an Overleaf project using standard Git, enabling instant online PDF compilation.

---

## 1. Safety & Credential Security First

> [!CAUTION]
> **NEVER hardcode your Overleaf git token into repository files or git remotes pushed to public GitHub!**
> Overleaf git URLs with embedded tokens (`https://git:olp_xxxx@git.overleaf.com/...`) will expose your Overleaf account if committed.

### Safe Setup Options:

### Option A: Standard Git Credentials Cache (Recommended)
Add the remote without credentials in the URL:
```bash
git remote add overleaf https://git.overleaf.com/YOUR_OVERLEAF_PROJECT_ID
```
Configure git to securely cache credentials:
```bash
git config --global credential.helper osxkeychain # on macOS
# or
git config --global credential.helper store # on Linux
```
On your first manual push:
```bash
git push overleaf main
```
Git will prompt you for:
- **Username**: `git`
- **Password**: Your Overleaf Git token (`olp_...`) generated in your Overleaf Account Settings.

---

## 2. Enable Auto-Sync in `config.yaml`

In `config.yaml`, turn on the overleaf sync flag:

```yaml
overleaf_sync:
  enabled: true
  sync_folder: "tech"      # Optional mirror folder
  remote_name: "overleaf"
  branch: "main"
```

Once enabled, whenever the AI finishes tailoring a `.tex` resume or cover letter, it will commit and push to Overleaf automatically.

