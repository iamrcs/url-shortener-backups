# 📦 URL Shortener Backups

This repository stores **daily database backups** for the [URL Shortener](https://github.com/iamrcs/url-shortener) project.

The application automatically pushes the current database (`urls.db`) to this repo every day at **23:59 UTC** and also restores the database from here on each new deployment.

---

## 🔧 How It Works

* The URL shortener app uses **SQLite** (`urls.db`) locally.
* A helper script (`backup_github.py`) handles syncing:

  * **On Startup** → Pulls the latest `urls.db` from this repo.
  * **Daily at 23:59** → Pushes the updated `urls.db` to this repo.
  * **On Shutdown** → Pushes the latest database as a final backup.

This ensures that your shortened links and stats are **never lost**, even if you redeploy or restart your server.

---

## 📂 Repo Structure

```
url-shortener-backups/
│
├── urls.db            # The SQLite database with all shortened URLs
├── README.md          # Documentation (this file)
└── .gitignore         # Ignores temp files except the DB
```

---

## 🚀 Usage

1. Clone this repo:

   ```bash
   git clone https://github.com/iamrcs/url-shortener-backups.git
   ```

2. On a new deployment, the app will **automatically restore** the database from here.

3. Backups are handled automatically — **no manual action required**.

---

## 🔐 Security Notes

* Do **not** expose this repo publicly if your database contains sensitive data.
* Keep it **private** or enable **GitHub Actions encryption** for sensitive backups.
* Use a **GitHub Personal Access Token (PAT)** in your app (`GITHUB_TOKEN`) to push/pull securely.

---

## 🛠 Related Projects

* Main App: [URL Shortener](https://github.com/iamrcs/url-shortener)
* Backup Automation: Built into the app (`backup_github.py`)

---

💡 With this setup, you can **deploy your URL shortener anywhere**, and your data will always sync back from this GitHub backup repo.
