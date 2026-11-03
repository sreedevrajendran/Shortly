# Shortly ⚡

A modern, fast, and secure URL shortener web application developed by **[Sreedev Rajendran](https://github.com/sreedevrajendran)**, built with **Ruby on Rails 7.2**, **React 17**, **Tailwind CSS**, and **Webpack 5 (via Shakapacker)**.

[![Live Demo](https://img.shields.io/badge/Demo-Shortly_Live-6366f1?style=for-the-badge&logo=render&logoColor=white)](https://shortly-44br.onrender.com)
[![GitHub CI](https://img.shields.io/github/actions/workflow/status/sreedevrajendran/Shortly/ci.yml?branch=main&style=for-the-badge&logo=github)](https://github.com/sreedevrajendran/Shortly/actions)
[![Security Alerts](https://img.shields.io/badge/Dependabot_Alerts-0_Open-brightgreen?style=for-the-badge&logo=github)](https://github.com/sreedevrajendran/Shortly/security/dependabot)
[![Ruby](https://img.shields.io/badge/Ruby-3.2-CC342D?style=for-the-badge&logo=ruby&logoColor=white)](https://www.ruby-lang.org/)
[![Rails](https://img.shields.io/badge/Rails-7.2-CC0000?style=for-the-badge&logo=rubyonrails&logoColor=white)](https://rubyonrails.org/)
[![React](https://img.shields.io/badge/React-17-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org/)
[![Webpack](https://img.shields.io/badge/Webpack-5-8DD6F9?style=for-the-badge&logo=webpack&logoColor=black)](https://webpack.js.org/)

---

## 🌐 Live Demo

Visit the live production application deployed on Render:
👉 **[https://shortly-44br.onrender.com](https://shortly-44br.onrender.com)**

---

## 👨‍💻 Developer Overview & Recent Enhancements

Shortly was created and modernized by **Sreedev Rajendran** to provide an ultra-clean, reliable URL shortening service paired with real-time analytics, instant QR code distribution, and strict visitor privacy.

### 🛠️ Key Improvements & Modernization Changes Made

1. **Zero-Vulnerability Security Remediation (215 Advisories Resolved):**
   - Eliminated all **215 GitHub Dependabot security vulnerabilities** across both the Ruby and npm ecosystems down to **0 open alerts**.
   - Upgraded core gems to patch high-severity CVEs in Action View, Action Pack, Rails HTML Sanitizer, Puma, RDoc, and Rack.
   - Upgraded `axios` to `1.8.2` and pinned modern secure releases for transitive packages (`cross-spawn`, `deepmerge`, `braces`, `micromatch`, `minimatch`, `postcss`, `semver`, `yaml`, `lodash`) via Yarn resolutions.

2. **Full Framework Modernization (Rails 7.2 & Ruby 3.2):**
   - Upgraded the application stack from Rails 6.1 to **Rails 7.2.3.2** on **Ruby 3.2**.
   - Modernized ActiveRecord database schemas, database configuration, and native gem drivers (`sqlite3 ~> 2.9`, `pg ~> 1.7`).

3. **Next-Generation Asset Pipeline (Shakapacker 9.7 + Webpack 5):**
   - Replaced the deprecated `@rails/webpacker 5` (which relied on Webpack 4 and unmaintained Node.js polyfills) with **Shakapacker 9.7** and **Webpack 5.90+**.
   - Removed obsolete OpenSSL legacy provider workarounds (`--openssl-legacy-provider`).
   - Cleaned up Babel transpiler configuration with `@babel/preset-env` and `@babel/preset-react`.
   - Added backward-compatible binstubs (`bin/webpack`, `bin/shakapacker`) ensuring smooth local and CI compilation.

4. **Security & Privacy Hardening:**
   - **Visitor Isolation:** Restructured visitor token assignment to prevent session crosstalk and ensure robust multi-tenant link privacy.
   - **Strict URL Sanitization:** Hardened URL format validation to safeguard against invalid URI schemes and malformed inputs.
   - **Unique Click Deduplication:** Implemented secure, HTTP-only cookie-based click tracking to accurately distinguish total clicks from unique visits over a 24-hour window.

5. **CI/CD & DevOps Upgrades:**
   - Integrated **GitHub Actions CI** running automated build, database preparation, asset compilation, and test execution on every commit.
   - Added **GitHub CodeQL Advanced** security workflow for automated static application security testing (SAST).
   - Hardened multi-stage **Dockerfile** with non-root security user (`rails:1000`) and streamlined entrypoint scripts.

---

## ✨ Features

- **⚡ Instant URL Shortening**: Paste any URL, auto-sanitizes missing protocols (auto-prepends `https://`), and generates short, clean links.
- **📱 QR Code Generation**: Instant SVG/PNG QR code preview and download for any shortened link with one click.
- **📊 Real-Time Analytics**: Tracks **Total Clicks** as well as **Unique Visitors** (deduplicated over a 24-hour window using secure HTTP-only cookies).
- **🔒 Visitor Session Isolation**: Permanent cookie token (`visitor_token`) keeps your links private to your browser while supporting a toggle to view all public links.
- **📌 Pinning System**: Pin your most frequently accessed links to the top of your dashboard.
- **🔍 Live Search & Filter**: Real-time client-side search across original URLs and generated slugs.
- **🎨 Modern Responsive UI**: Clean cards, Remixicon badges, high-contrast typography, and smooth transitions built with Tailwind CSS.
- **🐳 Production Ready**: Fully containerized with multi-stage `Dockerfile`, `docker-compose.yml`, and `render.yaml` Blueprint.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Backend** | Ruby 3.2, Rails 7.2.3.2, Puma 7.2.1 |
| **Frontend** | React 17, React Router, Axios 1.8.2, Tailwind CSS 1.9, Remixicon |
| **Asset Pipeline** | Shakapacker 9.7, Webpack 5.112, Babel 7.24 |
| **Databases** | SQLite 2.9 (Development / Test), PostgreSQL (Production) |
| **DevOps & CI** | Docker, Podman, GitHub Actions CI, CodeQL SAST, Render |

---

## 🚀 Getting Started Locally

### Option 1: Running with Docker / Podman (Recommended)

```bash
# Clone the repository
git clone https://github.com/sreedevrajendran/Shortly.git
cd Shortly

# Start with Docker Compose
docker compose up --build
```
Open **[http://localhost:3000](http://localhost:3000)** in your browser.

---

### Option 2: Running Natively

#### Prerequisites
- Ruby 3.2+
- Bundler (`gem install bundler`)
- Node.js 20+ and Yarn (`npm install -g yarn`)
- SQLite3 development headers

#### Setup Steps
```bash
# 1. Install Ruby gems
bundle install

# 2. Install JavaScript dependencies
yarn install

# 3. Setup database and run migrations
bin/rails db:prepare

# 4. Compile frontend assets
bin/webpack
# Alternatively for live rebuilds:
npm run build:dev

# 5. Start Rails server
bin/rails server
```
Visit **[http://localhost:3000](http://localhost:3000)**.

---

## 🧪 Testing & Verification

Run the Rails test suite:
```bash
bin/rails test
```

Precompile assets for production:
```bash
RAILS_ENV=production SECRET_KEY_BASE=dummy bin/rails assets:precompile
```

Check code style:
```bash
bundle exec rubocop
```

---

## 👤 Author

**Sreedev Rajendran**
- GitHub: [@sreedevrajendran](https://github.com/sreedevrajendran)
- Repository: [sreedevrajendran/Shortly](https://github.com/sreedevrajendran/Shortly)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
