# 🌍 Global Epidemic Tracker

> **CDC is dead, we protect the people.**
>
> **"El pueblo unido jamás será vencido"**

[![Live Dashboard](https://img.shields.io/badge/Live-Dashboard-brightgreen?style=for-the-badge&logo=googlechrome&logoColor=white)](https://mrlmrml.github.io/epidemic-tracker/)
[![Auto Update](https://github.com/MRLMRML/epidemic-tracker/actions/workflows/update-data.yml/badge.svg)](https://github.com/MRLMRML/epidemic-tracker/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

---

An open-source, real-time global epidemic monitoring system. We aggregate outbreak data from WHO Disease Outbreak News, cross-validate against independent news outlets, and present it in a multilingual interactive dashboard that anyone can use.

When institutions fail, the people must protect themselves.

## 🖥️ Dashboard

**[→ mrlmrml.github.io/epidemic-tracker](https://mrlmrml.github.io/epidemic-tracker/)**

- Interactive world map with cluster markers and severity coloring
- Multilingual: 中文 · English · Español · Русский · العربية · فارسی · Deutsch · Français · Português
- Risk alerts for dangerous outbreaks with H2H transmission warnings
- Disease search with hover tooltips for quick info
- Auto-updated every 6 hours via GitHub Actions
- News cross-validation indicators (✓ Verified / ? Unverified)

## 🔧 How It Works

```
   WHO Disease Outbreak News API
              ↓
      Data Collection (all diseases)
              ↓
      News Cross-Validation
      (Bing News · Google News · Reddit)
              ↓
      Risk Analysis & Severity Classification
              ↓
      JSON/GeoJSON Export → GitHub Pages
              ↓
      Interactive Dashboard (auto-refresh)
```

### Run Locally

```bash
pip install requests

# Full pipeline
python3 scripts/fetch_data.py --fetch --validate --summary

# Filter by disease
python3 scripts/fetch_data.py --fetch --disease cholera --summary

# Export for dashboard
python3 scripts/fetch_data.py --fetch --validate --export-json --export-geojson
```

## 🤖 Agent Integration

This project ships a `SKILL.md` for AI agent frameworks. Load it as a skill to enable natural-language epidemic queries.

```
User: "What cholera outbreaks are active right now?"
Agent: [loads skill] → [runs pipeline] → [presents data with sources]
```

## 📡 Data Sources & Validation

| Source | Role | Method |
|--------|------|--------|
| **WHO Disease Outbreak News** | Primary outbreak data | REST API, event-driven |
| **Bing News** | Cross-validation | RSS search |
| **Google News** | Cross-validation | RSS search |
| **Reddit** | Community signal | API search |

Every outbreak is scored and validated: if 2+ independent news sources corroborate the WHO report, it's marked ✓ Verified.

## 🦠 Diseases Tracked

Cholera · Ebola · Marburg · Mpox · Dengue · Measles · Influenza · Hantavirus · Yellow Fever · Meningitis · Polio · MERS · Nipah · Rift Valley Fever · West Nile · Lassa Fever · CCHF · Plague · Anthrax · Chikungunya · Diphtheria · Hepatitis E · COVID-19 · Rabies · Zika · and more.

## 📁 Structure

```
├── SKILL.md                          # AI agent skill
├── scripts/fetch_data.py             # Data pipeline CLI
├── src/
│   ├── collectors/who_don.py         # WHO DON API collector
│   ├── collectors/aggregator.py      # Aggregation + risk analysis
│   └── validation/news_validator.py  # News cross-validation
├── site/
│   ├── index.html                    # Dashboard (single-file)
│   └── data/                         # Live data (JSON/GeoJSON)
└── .github/workflows/                # Auto-update cron (6h)
```

## 🤝 Contributing

- Add a new data source collector
- Improve disease name translations
- Fix data extraction accuracy
- Improve dashboard UI/UX

## 📜 License

MIT — Use it, fork it, deploy it. The people's data belongs to the people.
