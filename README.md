# Shortly ⚡

A fast, responsive, and secure URL shortener web application built with **Ruby on Rails 7.2**, **React 17**, and **Tailwind CSS**.

Originally created by **[Akhil G Krishnan](https://github.com/akhilgkrishnan)** and forked/modernized by **[Sreedev Rajendran](https://github.com/sreedevrajendran)**.

[![Live Demo](https://img.shields.io/badge/Demo-Shortly_Live-6366f1?style=for-the-badge&logo=render&logoColor=white)](https://shortly-44br.onrender.com)
[![GitHub CI](https://img.shields.io/github/actions/workflow/status/sreedevrajendran/Shortly/ci.yml?branch=main&style=for-the-badge&logo=github)](https://github.com/sreedevrajendran/Shortly/actions)
[![Security Alerts](https://img.shields.io/badge/Dependabot_Alerts-0_Open-brightgreen?style=for-the-badge&logo=github)](https://github.com/sreedevrajendran/Shortly/security/dependabot)
[![Ruby](https://img.shields.io/badge/Ruby-3.2-CC342D?style=for-the-badge&logo=ruby&logoColor=white)](https://www.ruby-lang.org/)
[![Rails](https://img.shields.io/badge/Rails-7.2-CC0000?style=for-the-badge&logo=rubyonrails&logoColor=white)](https://rubyonrails.org/)
[![React](https://img.shields.io/badge/React-17-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org/)
[![Webpack](https://img.shields.io/badge/Webpack-5-8DD6F9?style=for-the-badge&logo=webpack&logoColor=black)](https://webpack.js.org/)

---

## 🌐 Live Demo

Live production deployment on Render:
👉 **[https://shortly-44br.onrender.com](https://shortly-44br.onrender.com)**

---

## 📌 Project Background & Fork Notice

This repository is a modernized fork of the original project by **[akhilgkrishnan](https://github.com/akhilgkrishnan/Shortly)**.

The application has been extensively refactored, upgraded, and secured to bring an unmaintained Rails 6.1 codebase up to modern web standards, resolve all known security vulnerabilities, and provide containerized cloud deployment.

---

## 🛠️ Changes & Enhancements Made (by Sreedev Rajendran)

### 1. 🛡️ Complete Security Overhaul (215 Vulnerabilities Fixed)
- Remediated all **215 GitHub Dependabot security alerts** across Ruby and npm dependencies down to **0 open alerts**.
- Upgraded critical gems to eliminate vulnerabilities in Action View, Action Pack, Rails HTML Sanitizer, Puma, RDoc, and Rack.
- Upgraded `axios` to `1.8.2` and pinned patched releases for transitive packages (`cross-spawn`, `deepmerge`, `braces`, `micromatch`, `minimatch`, `postcss`, `semver`, `yaml`, `lodash`) using Yarn resolutions.

### 2. 🚀 Rails 7.2 & Ruby 3.2 Upgrade
- Upgraded framework from Rails 6.1 to **Rails 7.2.3.2** on **Ruby 3.2**.
- Updated ActiveRecord schemas, modern database configurations, and database driver gems (`sqlite3 ~> 2.9`, `pg ~> 1.7`).

### 3. 📦 Modern Asset Pipeline (Shakapacker 9.7 + Webpack 5)
- Migrated from deprecated `@rails/webpacker 5` (which depended on Webpack 4 and unmaintained Node polyfills) to **Shakapacker 9.7** and **Webpack 5.90+**.
- Removed outdated Node.js legacy OpenSSL flags (`--openssl-legacy-provider`).
- Modernized Babel configuration with standard `@babel/preset-env` and `@babel/preset-react`.
- Updated binstubs (`bin/webpack`, `bin/webpack-dev-server`, `bin/shakapacker`) for compatibility with modern build environments.

### 4. 🔒 Privacy, Session Isolation & Tracking Logic
- **Visitor Isolation:** Restructured `visitor_token` handling to prevent session crosstalk and ensure links remain private to their creator.
- **Strict URL Sanitization:** Hardened URL parsing and auto-prepends missing protocols (`https://`) safely.
- **Unique Click Deduplication:** Implemented secure, HTTP-only cookie tracking to differentiate unique visitors from total clicks over a 24-hour window.
- **QR Code Support:** Integrated instant SVG/PNG QR code preview and download for shortened URLs.

### 5. 🐳 DevOps, CI/CD & Cloud Deployment
- Replaced outdated CircleCI with **GitHub Actions CI** covering database preparation, asset compilation, and automated test execution.
- Added **GitHub CodeQL** static analysis workflow for code scanning.
- Designed a multi-stage **Dockerfile** with non-root security user (`rails:1000`) and Render deployment blueprint (`render.yaml`).

---

## ✨ Features

- **⚡ Instant URL Shortening**: Auto-sanitizes URLs and generates short, clean links.
- **📱 QR Code Generation**: Downloadable QR code previews for every shortened link.
- **📊 Real-Time Analytics**: Tracks **Total Clicks** and **Unique Visitors** (deduplicated over 24 hours).
- **🔒 Visitor Session Isolation**: Links are scoped to your browser session with an optional public links view.
- **📌 Pinning System**: Pin frequent links to the top of the table.
- **🔍 Live Search & Filter**: Instant search across original URLs and generated slugs.
- **🎨 Responsive UI**: Built with Tailwind CSS and Remixicon.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Backend** | Ruby 3.2, Rails 7.2.3.2, Puma 7.2.1 |
| **Frontend** | React 17, React Router, Axios 1.8.2, Tailwind CSS 1.9, Remixicon |
| **Asset Bundler** | Shakapacker 9.7, Webpack 5.112, Babel 7.24 |
| **Databases** | SQLite 2.9 (Development / Test), PostgreSQL (Production) |
| **DevOps & CI** | Docker, GitHub Actions CI, CodeQL SAST, Render |

---

## 🚀 Getting Started Locally

### Option 1: Running with Docker / Podman (Recommended)

```bash
git clone https://github.com/sreedevrajendran/Shortly.git
cd Shortly

docker compose up --build
```
Open **[http://localhost:3000](http://localhost:3000)**.

---

### Option 2: Running Natively

#### Prerequisites
- Ruby 3.2+
- Bundler (`gem install bundler`)
- Node.js 20+ and Yarn (`npm install -g yarn`)
- SQLite3 development packages

#### Setup Steps
```bash
# 1. Install dependencies
bundle install
yarn install

# 2. Setup database
bin/rails db:prepare

# 3. Build assets
bin/webpack

# 4. Start Rails server
bin/rails server
```
Visit **[http://localhost:3000](http://localhost:3000)**.

---

## 🧪 Testing

Run the test suite:
```bash
bin/rails test
```

Test asset precompilation:
```bash
RAILS_ENV=production SECRET_KEY_BASE=dummy bin/rails assets:precompile
```

---

## 👥 Credits & Acknowledgments

- **Original Creator:** [Akhil G Krishnan](https://github.com/akhilgkrishnan) — Original concept and implementation in [akhilgkrishnan/Shortly](https://github.com/akhilgkrishnan/Shortly).
- **Fork Maintainer & Modernization:** [Sreedev Rajendran](https://github.com/sreedevrajendran) — Security vulnerability remediation, Rails 7.2 & Webpack 5 upgrades, visitor isolation, and Docker/CI pipeline.

---

## 📄 License Notice

This repository is forked from the upstream project [akhilgkrishnan/Shortly](https://github.com/akhilgkrishnan/Shortly). Please refer to the upstream repository for original licensing information.
