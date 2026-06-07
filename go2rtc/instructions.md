# n8n — Fix Data Folder Permissions

> Restore correct ownership and permissions on the n8n data directory.

---

### Step 1 — Navigate to the stack

> 💡 Run this on your **Dockge LXC** host.

```bash
cd /opt/stacks/n8n/
```

### Step 2 — Reassign ownership to the n8n internal user

The n8n container runs as UID `1000`. This ensures it can read and write its own data.

```bash
chown -R 1000:1000 ./n8n_data
```

### Step 3 — Set directory & file permissions

Grants the owner and group full access while letting others read and execute.

```bash
chmod -R 775 ./n8n_data
```

---

### 🎉 Done

After these three commands, n8n should have full access to `n8n_data/`. Restart the container if it was already running:
