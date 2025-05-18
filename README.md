# CourseForge API

Back‑end service for **CourseForge** – a self‑hosted e‑learning platform where courses are structured as *course → section → lesson* and each lesson is delivered primarily as video.

---

## ✨ Key features

* **Video‑centric learning** – each lesson points to a protected video file and optional supplementary materials.
* **Section quizzes** – configurable tests unlock the next section only after the learner passes.
* **Progress tracking** – per‑user completion stats and resume‑from‑last‑time timestamps.
* **Escrow certificates** – signed issuer JSON for completed courses.
* **Role‑based access** – admins, instructors and students with JWT auth.
* **REST + Swagger** – automatic OpenAPI docs generated from Nest JS decorators.

---

## 🛠 Tech stack

| Layer            | Tech / Package                              |
| ---------------- | ------------------------------------------- |
| Framework        | **Nest JS 10** (`@nestjs/*`)|
| Database         | MongoDB 6, Mongoose ODM                     |
| Caching          | Redis 7 (optional)                          |
| Storage          | S3‑compatible (AWS S3 / MinIO)              |
| Auth             | JWT Bearer tokens                           |
| Validation       | `class‑validator` / `class‑transformer`     |
| Dev & tooling    | pnpm, TypeScript, ESLint, Prettier, Husky   |
| CI               | GitHub Actions → lint → test → build        |

---

## 🚀 Quick start

```bash
# clone & install deps
git clone https://github.com/kurkul608/digital-producer-back.git
cd digital-producer-back
pnpm install

# start MongoDB in Docker (optional helper)
docker compose up -d mongo

# run migrations / seed demo data
pnpm seed

# start dev server with hot‑reload
pnpm start:dev
```

The API listens on **http://localhost:4000** (port configurable).

---

## 🔑 Environment variables

Copy template and fill in secrets:

```bash
cp .env.example .env.local
```

---

## 📂 Folder structure (trimmed)

```
src/
 ├─ modules/
 │   ├─ course/
 │   ├─ section/
 │   ├─ lesson/
 │   ├─ quiz/
 │   └─ auth/
 ├─ common/           # pipes, guards, filters
 ├─ configs/          # configuration providers
 └─ main.ts           # bootstrap
prisma/               # if you migrate to Prisma later
```

---

## 🧪 Scripts

| Command            | Action                                 |
| ------------------ | -------------------------------------- |
| `pnpm start:dev`   | Nest‑CLI watch mode                    |
| `pnpm build`       | Compile to `dist/`                     |
| `pnpm start`       | Start compiled build                   |
| `pnpm test`        | Jest unit tests                        |
| `pnpm lint`        | ESLint                                 |
| `pnpm seed`        | Load demo course + user credentials    |

---

## 🚧 Roadmap

- [ ] Replace Mongoose with Prisma MongoDB connector
- [ ] Add HLS transcoding pipeline for large videos
- [ ] WebSocket live‑progress updates
- [ ] OAuth2 provider (Google, GitHub)

---

## 🤝 Contributing

1. Fork → `git checkout -b feat/amazing`
2. `pnpm install && pnpm lint && pnpm test`
3. Commit using Conventional Commits.
4. Open a PR describing what and why.

---

## 📝 License

Distributed under the MIT License – see **LICENSE** for details.
