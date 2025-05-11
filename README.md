# 💍 Wedding App

Application web pour organiser, personnaliser et enrichir notre mariage.
Elle permet de gérer les invités, partager des photos, diffuser les infos pratiques, et bien plus.

---

## ✨ Fonctionnalités prévues

- 🎟️ Gestion des invités (RSVP)
- 📷 Partage sécurisé de photos (via QR code)
- 📄 Informations pratiques (lieu, horaires, hébergements)
- 📊 Tableau de bord privé
- 🔒 Authentification + permissions (admin vs public)

---

## 🧱 Stack technique

| Composant       | Technologie                |
|------------------|----------------------------|
| Frontend        | React + Vite               |
| Backend         | FastAPI + SQLAlchemy       |
| Base de données | PostgreSQL                 |
| Conteneurisation| Docker + Docker Compose    |
| Reverse Proxy   | Nginx                      |
| CI/CD           | GitHub Actions + SSH Deploy|
| Cloud           | Scaleway (VM Ubuntu)       |

---

## 🗂️ Structure du projet

```plaintext
wedding-app/
├── backend/             # API FastAPI
│   ├── app/
│   │   ├── api/         # Routes
│   │   ├── core/        # Config, sécurité
│   │   ├── models/      # Modèles SQLAlchemy
│   │   ├── schemas/     # Pydantic DTOs
│   │   ├── services/    # Logique métier
│   │   └── main.py      # Entrée FastAPI
│   ├── alembic/         # Migrations
│   └── Dockerfile
│
├── frontend/            # Interface React (Vite)
│   ├── src/
│   │   ├── components/
│   │   └── pages/
│   └── Dockerfile
│
├── nginx/               # Reverse proxy + TLS
│   └── default.conf
│
├── .github/workflows/   # CI/CD
├── docker-compose.yml
└── README.md
```

---

## 🚀 Lancer le projet en local

### 1. Cloner le projet

```bash
git clone git@github.com:<TON-PSEUDO>/wedding-app.git
cd wedding-app
```

### 2. Lancer les services avec Docker

```bash
docker compose up --build
```

Assure-toi d’avoir Docker et Docker Compose installés.

### 3. Accéder aux interfaces
- 🌐 Frontend : [http://localhost:5173](http://localhost:5173)
- ⚙️ API (docs Swagger) : [http://localhost:8000/docs](http://localhost:8000/docs)
- 🐘 PostgreSQL : `localhost:5432` (user/pass : `postgres` / `postgres`)

### 4. Appliquer les migrations (si nécessaires)

```bash
docker compose exec backend alembic upgrade head
```

---

## ⚙️ CI/CD
- Déploiement automatique à chaque push sur `main`
- Utilisation de GitHub Actions + clé SSH privée chiffrée
- Connexion au serveur Scaleway
- Build des images Docker et redémarrage des services à distance via `docker compose`

---

## 🔒 Sécurité
- Authentification avec JWT (FastAPI)
- Permissions pour accéder aux différentes parties (admin/public)
- Accès aux photos via QR code temporaire sécurisé
- HTTPS via Nginx + Certbot (TLS Let’s Encrypt)

---

## 📜 Licence

MIT License – © 2025 Yoan Fornari

Voir le fichier LICENSE pour plus de détails.
