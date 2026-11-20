# Currency Rate Viewer (v1.0.0 Production Build)

> **StudentLife Hackathon Project #112: Currency Rate Viewer**  
> *Domain: Smart Applications, Financial Tech & APIs*

---

## 📋 Executive Overview

**Currency Rate Viewer** is a modular, production-ready Python software application engineered to fetch live currency exchange rates via APIs (`open.er-api.com`), calculate accurate conversions across 15+ international currencies, maintain robust dual local file persistence (JSON & CSV), provide rich command-line and graphical interfaces, and deliver publication-grade visual analytics reports.

---

## 🌟 Key Production Features

1. **Dual Interface Options**:
   - **Interactive Terminal Console (CLI)**: ANSI-colorized, paginated menu interface.
   - **Desktop GUI (Tkinter)**: Multi-tab desktop application for live conversions, record browsing, and analytics export.
2. **Resilient Rate Engine with Offline Fallback**:
   - Queries live exchange rate APIs with timeout protection.
   - Automatically fails over to an offline mock exchange rate cache if network connectivity drops.
3. **Defensive Input Validation**:
   - Strict 3-letter ISO code validation (USD, EUR, GBP, JPY, AUD, etc.).
   - Type sanitization and non-negative boundary enforcement.
4. **Dual Storage Persistence & Recovery**:
   - Concurrent serialization to JSON (`conversions.json`) and CSV (`conversions.csv`).
   - Corrupted file auto-detection, atomic file writes (`.tmp`), and auto-backup creation.
5. **Record Query & Search Engine**:
   - Filter transaction history by currency pair, date ranges, minimum/maximum USD equivalent thresholds, and keyword notes.
6. **Executive Analytics & Visualization**:
   - Computes total transaction volumes, average conversion sizes, pair distribution histograms, and high-volume alert flags (> $5,000 USD).
   - Generates publication-ready dual-panel plots (`currency_trends.png`) using Matplotlib.
7. **Multi-Format Export Suite**:
   - Exports formatted Markdown reports (`summary_report.md`), HTML summary dashboards (`summary_report.html`), CSV exports, and plain-text audit logs (`audit.log`).
8. **Automated Unit Testing**:
   - Full `unittest` test suite covering models, storage, API failovers, search engine, and analytics calculations.

---

## 📁 Repository Structure

```
currency_rate_viewer_project/
├── currency_rate_viewer/       # Core Application Package
│   ├── __init__.py             # Package Initialization
│   ├── config.py               # Constants, API Endpoints, Mock Rates & Thresholds
│   ├── models.py               # Transaction Dataclass, Schema Validation & CSV/JSON Mappers
│   ├── utils.py                # ANSI Colors, Sanitize Helpers & Input Prompts
│   ├── api.py                  # API Fetcher & Offline Cache Fallback Logic
│   ├── storage.py              # Dual JSON/CSV Storage & Corrupted Backup Recovery
│   ├── engine.py               # Conversion Core & Search Query Engine
│   ├── analytics.py            # Aggregations, Metrics & Matplotlib Visual Charting
│   ├── exporter.py             # Markdown, HTML & Audit Log Exporters
│   ├── cli.py                  # Terminal Menu Dispatcher
│   └── gui.py                  # Tkinter Multi-Tab Desktop Interface
├── tests/                      # Automated Unit Test Suite
│   ├── __init__.py
│   ├── test_models.py          # Validation Tests
│   ├── test_api.py             # API & Cache Tests
│   ├── test_storage.py         # Persistence Tests
│   ├── test_engine.py          # Business Logic Tests
│   └── test_analytics.py       # Metrics Tests
├── data/                       # Seed Datasets
│   └── conversions_seed.csv    # 40-record production seed dataset
├── main.py                     # Entry point (CLI, GUI, Demo, Seed flags)
├── setup.py                    # Standard Packaging Setup
├── requirements.txt            # Dependency Requirements
└── README.md                   # System Documentation
```

---

## 🚀 Installation & Running

### 1. Requirements
- Python 3.10+
- `matplotlib` (Optional for visual plots, standard library fallback included)

### 2. Execution Commands

- **Launch Terminal Interface (CLI)**:
  ```bash
  python3 main.py
  ```

- **Launch Desktop GUI Window (Tkinter)**:
  ```bash
  python3 main.py --gui
  ```

- **Run Automated Hackathon Integration Demo**:
  ```bash
  python3 main.py --demo
  ```

- **Re-Seed Database (40 Sample Records)**:
  ```bash
  python3 main.py --seed
  ```

- **Run Unit Tests**:
  ```bash
  python3 -m unittest discover tests
  ```

---

*Curated for StudentLife Hackathon 2026.*
