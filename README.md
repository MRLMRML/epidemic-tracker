# 🌍 Global Epidemic Tracker

> **CDC is dead, we protect the people.**
>
> **El pueblo unido jamás será vencido.**

[![Live Dashboard](https://img.shields.io/badge/Live-Dashboard-00c9db?style=for-the-badge&logo=googlechrome&logoColor=white)](https://mrlmrml.github.io/epidemic-tracker/)
[![Auto Update](https://github.com/MRLMRML/epidemic-tracker/actions/workflows/update-data.yml/badge.svg)](https://github.com/MRLMRML/epidemic-tracker/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

Real-time global disease outbreak monitoring. WHO Disease Outbreak News + news cross-validation. 53 diseases, 151 countries, 9 languages.

---

## 📊 Current Data

| Metric | Value |
|--------|-------|
| Active Outbreaks | 581 |
| Diseases | 53 |
| Countries | 151 |
| Total Cases | 2,970,802 |
| Total Deaths | 13,677 |
| Auto-Update | Every 6 hours |

---

## 🚀 Local Dashboard Setup

```bash
git clone https://github.com/MRLMRML/epidemic-tracker.git
cd epidemic-tracker
pip install requests

# Fetch latest data
python3 scripts/fetch_data.py --fetch --export-json --export-geojson --no-validate

# Copy to dashboard
cp data/processed/epidemics.json site/data/
cp data/processed/epidemics.geojson site/data/

# Open dashboard
open site/index.html          # macOS
xdg-open site/index.html      # Linux
start site/index.html          # Windows
```

No server needed — single HTML file loads `site/data/epidemics.json`.

---

## 🤖 Agent Integration

Load `SKILL.md` as a skill in any AI agent tool:

| Tool | How |
|------|-----|
| **OpenCode** | `load_skills=["epidemic-tracker"]` |
| **Claude Code** | Reference `SKILL.md` in system prompt |
| **OpenClaw / Hermes** | Include in agent context |

---

## 🏗️ Architecture

```
WHO DON API  ──→  who_don.py   ──┐
WHO GHO API  ──→  who_gho.py   ──┼──→ aggregator.py
OWID CSV     ──→  owid.py      ──┘        ↓
                               news_validator.py
                               (Bing/Google/Reddit)
                                      ↓
                               epidemics.json
                                      ↓
                    ┌────────────────┼────────────────┐
                    ▼                ▼                ▼
             site/index.html   SKILL.md         fetch_data.py
             (Dashboard)       (Agent)           (CLI)
```

---

## 🌐 Dashboard Features

| Feature | Description |
|---------|------------|
| **Hierarchical filters** | Continent→Country, Pathogen Type→Disease |
| **Severity filters** | 极高/高/中等/低/H2H multi-select |
| **Map** | Dark theme, cluster markers, severity colors |
| **Disease cards** | Severity badge, data source tags, confidence level, H2H flag |
| **Disease detail** | 7d/30d/6m trend charts (Chart.js) |
| **News ticker** | Scrolling latest outbreak news |
| **9 languages** | 中文 · English · Español · Русский · العربية · فارسی · Deutsch · Français · Português |

---

## 📡 Data Sources

| Source | What | Method |
|--------|------|--------|
| WHO DON API | Outbreak alerts | REST API |
| WHO GHO | Annual disease stats | REST API |
| OWID | Mpox daily data | CSV |
| Bing/Google/Reddit | Cross-validation | RSS/API |

---

## 🦠 Diseases (53)

Cholera · Ebola · Marburg · Mpox · Dengue · Measles · Influenza · Hantavirus · Yellow Fever · Meningitis · Polio · MERS · Nipah · Rift Valley Fever · West Nile · Lassa · CCHF · Plague · Anthrax · Chikungunya · Diphtheria · Hepatitis E · Rabies · Zika · COVID-19 · Malaria · Avian Influenza · and more.

---

## 📜 License

MIT — The people's data belongs to the people.
