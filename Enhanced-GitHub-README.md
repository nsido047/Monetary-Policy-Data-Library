# Monetary Policy Data Library

[![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Data Quality](https://img.shields.io/badge/data-research--grade-success.svg)](docs/data-quality.md)

> **A comprehensive, open-source repository of structured monetary policy data for empirical research in monetary economics, international finance, and asset pricing.**

---

## 📋 Table of Contents

- [Overview](#overview)
- [The Problem](#the-problem)
- [Our Solution](#our-solution)
- [Scope and Coverage](#scope-and-coverage)
- [Data Structure](#data-structure)
- [Getting Started](#getting-started)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [Methodology](#methodology)
- [Data Sources](#data-sources)
- [Citation](#citation)
- [License](#license)
- [Contact](#contact)

---

## 🎯 Overview

The **Monetary Policy Data Library** is a research-grade infrastructure project designed to consolidate, standardize, and document publicly available data on historical monetary policy decisions, central bank balance sheet operations, and unconventional monetary tools from major central banks worldwide.

### Key Features

- ✅ **Centralized Access**: Single repository for cross-country monetary policy data
- ✅ **Standardized Format**: Harmonized data structure across all central banks
- ✅ **Research Validated**: Event timelines verified against peer-reviewed literature
- ✅ **Open Source**: Freely accessible under MIT license
- ✅ **Reproducible**: Full documentation of data sources and compilation methodology
- ✅ **Version Controlled**: Complete history of data updates and revisions

---

## ❗ The Problem

### Current Challenges in Monetary Policy Research

Over the past two decades, central bank operations have undergone dramatic transformation, particularly with the adoption of unconventional monetary policy tools such as:

- **Quantitative Easing (QE)** — Large-scale asset purchase programs
- **Forward Guidance** — Communication about future policy paths
- **Yield Curve Control (YCC)** — Direct targeting of longer-term interest rates
- **Negative Interest Rate Policy (NIRP)** — Policy rates below zero

Despite increased transparency from central banks, researchers face significant obstacles:

#### 1. **Data Fragmentation**
Data are siloed across individual central bank repositories, the Bank for International Settlements (BIS), International Monetary Fund (IMF), and various commercial data aggregators. Limited consolidation efforts exist.

#### 2. **Event Study Inconsistency**
There is little consensus in the literature on which policy announcements merit inclusion in event studies. This leads to:
- Mismatched timelines across research papers (e.g., varying QE announcement dates)
- Inconsistent definitions of "material" policy surprises
- Difficulty replicating existing studies

**Example:** Studies on Federal Reserve QE announcements use varying event sets (Gagnon et al., 2011; Rosa, 2012; Krishnamurthy & Vissing-Jorgensen, 2011; Neely, 2010), making cross-study comparisons challenging.

#### 3. **Manual Data Compilation**
Researchers must manually:
- Trace announcements from PDF releases and institutional websites
- Extract data from disparate formats
- Verify dates and details across multiple sources
- Reconstruct historical balance sheet data

This process can take **days or weeks** for each study, reducing research efficiency and increasing the risk of errors.

---

## 💡 Our Solution

The Monetary Policy Data Library addresses these challenges by providing:

### 1. **Curated Event Datasets**
Pre-compiled datasets of monetary policy announcements validated against peer-reviewed research, including:
- Exact announcement dates and times
- Event descriptions and context
- Associated market reactions (where available)
- Multiple data sources for verification

### 2. **Standardized Data Structure**
Consistent format across all central banks enabling:
- Direct cross-country comparisons
- Seamless integration into econometric models
- Reproducible empirical analysis

### 3. **Open Access Repository**
All data freely available under MIT license:
- No paywalls or subscription fees
- Version-controlled on GitHub
- Regular updates as new data become available
- Community contributions welcome

---

## 🌍 Scope and Coverage

### Initial Focus: Quantitative Easing Announcements

We begin with **QE announcements** as they represent:
- A clearly defined unconventional monetary policy tool
- Central focus of monetary policy research since 2008
- Well-documented historical record with academic consensus
- Cross-country comparability across major central banks

Unlike conventional interest rate decisions (which follow predictable schedules and are readily available), QE announcements occur irregularly and sporadically, making comprehensive datasets particularly valuable.

### Central Banks Covered

| Central Bank | Abbreviation | Coverage Period | Programs Included |
|-------------|--------------|-----------------|-------------------|
| **Federal Reserve (US)** | Fed | 2008–Present | QE1, QE2, Operation Twist, QE3, QE4 |
| **European Central Bank** | ECB | 2014–Present | APP, PSPP, CSPP, PEPP |
| **Bank of England** | BoE | 2009–Present | APF purchases, QT operations |
| **Bank of Japan** | BoJ | 2001–Present | QEP (2001-2006), QQE (2013-present) |

### Future Expansion Plans

- **Additional Central Banks**: Reserve Bank of Australia, Swiss National Bank, Bank of Canada
- **Additional Policy Tools**: Forward guidance statements, interest rate decisions, emergency lending facilities
- **Balance Sheet Data**: Historical SOMA holdings, reserve balances, asset compositions
- **Market Impact Variables**: Intraday yield changes, exchange rate movements, equity market reactions

---

## 📊 Data Structure

### Core Data Elements

For each monetary policy announcement, we collect:

#### Required Fields
- `announcement_date` — Date of announcement (YYYY-MM-DD)
- `announcement_time` — Time of announcement (HH:MM UTC)
- `central_bank` — Issuing central bank
- `policy_tool` — Type of policy (e.g., QE, Forward Guidance)
- `program_name` — Specific program identifier (e.g., QE1, APP)
- `event_type` — Classification (announcement, expansion, taper, conclusion)

#### Optional Fields
- `purchase_amount` — Size of asset purchases (USD billions or local currency)
- `asset_classes` — Securities targeted (Treasuries, MBS, corporate bonds)
- `maturity_target` — Target maturity range
- `policy_statement` — Text of associated statement
- `forward_guidance` — Any forward guidance provided
- `source_document` — URL to official announcement
- `academic_source` — Citation to validating research

#### Market Impact Variables (where available)
- `yield_2y_change` — 2-year Treasury yield change (basis points)
- `yield_10y_change` — 10-year Treasury yield change
- `fx_change` — Exchange rate change vs USD (%)
- `equity_change` — Stock market index change (%)

### Example Data Record

```csv
announcement_date,announcement_time,central_bank,policy_tool,program_name,event_type,purchase_amount,asset_classes,yield_10y_change,source_document,academic_source
2008-11-25,13:15,Federal Reserve,Quantitative Easing,QE1,Initial Announcement,600,"MBS, Agency Debt",-22,https://federalreserve.gov/newsevents/pressreleases/monetary20081125a.htm,"Gagnon et al. (2011), Remache et al. (2011)"
```

---

## 🚀 Getting Started

### Installation

```bash
# Clone the repository
git clone https://github.com/nsido047/Monetary-Policy-Data-Library.git
cd Monetary-Policy-Data-Library

# Install dependencies (if using Python scripts)
pip install -r requirements.txt
```

### Quick Start Example

```python
import pandas as pd

# Load Federal Reserve QE announcements
fed_qe = pd.read_csv('data/federal_reserve/qe_announcements.csv')

# Filter for QE1 events
qe1_events = fed_qe[fed_qe['program_name'] == 'QE1']

# Calculate average yield impact
avg_yield_change = qe1_events['yield_10y_change'].mean()
print(f"Average 10-year yield change: {avg_yield_change} bps")
```

### Data Access

All datasets are available in the `/data` directory organized by central bank:

```
data/
├── federal_reserve/
│   ├── qe_announcements.csv
│   ├── balance_sheet.csv
│   └── metadata.json
├── ecb/
│   ├── app_announcements.csv
│   ├── pepp_announcements.csv
│   └── metadata.json
├── bank_of_england/
│   ├── qe_announcements.csv
│   └── metadata.json
└── bank_of_japan/
    ├── qe_announcements.csv
    └── metadata.json
```

---

## 📖 Documentation

Comprehensive documentation is available in the `/docs` directory:

- **[Data Dictionary](docs/data-dictionary.md)** — Complete field definitions and formats
- **[Methodology](docs/methodology.md)** — Data compilation and validation procedures
- **[Examples](docs/examples/)** — Code examples for common use cases
- **[API Reference](docs/api-reference.md)** — Programmatic access to data
- **[FAQ](docs/faq.md)** — Frequently asked questions

### Tutorials

- [Getting Started with Event Studies](docs/tutorials/event-studies.md)
- [Cross-Country Comparisons](docs/tutorials/cross-country-analysis.md)
- [Time Series Analysis](docs/tutorials/time-series-analysis.md)
- [Replicating Published Research](docs/tutorials/replication-studies.md)

---

## 🤝 Contributing

We welcome contributions from the research community! Ways to contribute:

### Data Contributions
- Verify and validate existing event dates
- Add new central banks or policy tools
- Provide additional market reaction data
- Suggest corrections or improvements

### Code Contributions
- Develop data processing scripts
- Create visualization tools
- Improve documentation
- Add new examples and tutorials

### Research Contributions
- Share your research using this data
- Suggest new data variables
- Provide feedback on data structure

Please see our [Contributing Guide](CONTRIBUTING.md) for detailed instructions.

---

## 🔬 Methodology

### Data Collection Process

#### 1. **Literature Review**
We systematically review peer-reviewed research on monetary policy event studies to identify validated announcement dates. Key sources include:

- Gagnon, J., Raskin, M., Remache, J., & Sack, B. (2011). *The Financial Market Effects of the Federal Reserve's Large-Scale Asset Purchases*
- Krishnamurthy, A., & Vissing-Jorgensen, A. (2011). *The Effects of Quantitative Easing on Interest Rates*
- Rosa, C. (2012). *How "Unconventional" Are Large-Scale Asset Purchases?*
- Neely, C. J. (2010). *The Large-Scale Asset Purchases Had Large International Effects*
- Kapetanios, G., et al. (2012). *Assessing the Economy-Wide Effects of Quantitative Easing*

#### 2. **Primary Source Verification**
All events are cross-referenced with official central bank communications:
- Press releases and announcements
- FOMC/MPC/Governing Council statements
- Meeting minutes and transcripts
- Governor speeches and testimonies

#### 3. **Data Validation**
Multiple validation steps ensure data quality:
- Cross-check dates across at least 3 independent sources
- Verify timing using high-frequency financial market data
- Compare with established event study databases
- Peer review by domain experts

#### 4. **Standardization**
Data harmonized to consistent format:
- UTC timestamps for all events
- Standardized currency units (USD or local currency with exchange rates)
- Consistent classification taxonomy
- Complete metadata and provenance

---

## 📚 Data Sources

### Academic Literature

**Federal Reserve:**
- Gagnon et al. (2011) — LSAP effects and event timeline
- D'Amico & King (2010) — Cross-sectional Treasury analysis
- Bernanke, Reinhart, & Sack (2004) — Supply effects on yields
- Kiley (2018) — QE in the new normal
- Gilchrist et al. (2013) — Credit market effects

**European Central Bank:**
- Eser et al. (2023) — APP impact on sovereign yields
- Altavilla et al. (2019) — Monetary policy surprises
- Busetto et al. (2022) — ECB QE functioning

**Bank of England:**
- Kapetanios et al. (2012) — Economy-wide QE effects
- Joyce et al. (2011) — QE and gilt yields
- Busetto et al. (2022) — BoE QE perspective

**Bank of Japan:**
- Iwata (2013) — Balance sheet expansion in Japan
- Ugai (2007) — Effects of QE policy
- BOJ Working Papers (various) — QE policy analysis

### Official Sources

- [Federal Reserve News & Events](https://www.federalreserve.gov/newsevents.htm)
- [ECB Press Releases](https://www.ecb.europa.eu/press/pr/date/)
- [Bank of England News](https://www.bankofengland.co.uk/news)
- [Bank of Japan Announcements](https://www.boj.or.jp/en/announcements/)
- [BIS Statistics](https://www.bis.org/statistics/)

---

## 📝 Citation

If you use this data in your research, please cite:

### Preferred Citation

```bibtex
@misc{monetary_policy_data_library_2025,
  author = {{Monetary Policy Data Library Contributors}},
  title = {Monetary Policy Data Library: A Comprehensive Repository of Central Bank Policy Data},
  year = {2025},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/nsido047/Monetary-Policy-Data-Library}},
  note = {Accessed: [Date]}
}
```

### Data-Specific Citations

When using specific datasets, also cite the original research sources provided in the `academic_source` field.

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

### Important Notes

- **Data License**: All data compiled from publicly available sources. Original data retain their respective licenses.
- **Research License**: Academic research sources cited remain under their original publication licenses.
- **Code License**: All original code and documentation released under MIT License.

---

## 👥 Project Team

**Principal Investigator:** [Your Name]  
**Institution:** [Your Institution]  
**Contact:** [Your Email]

### Acknowledgments

This project builds on decades of research in monetary economics. We are grateful to:
- Authors of the foundational research cited throughout this repository
- Central banks for their commitment to transparency
- The open-source community for tools and infrastructure
- All contributors to this project

---

## 📞 Contact

- **Issues & Bug Reports:** [GitHub Issues](https://github.com/nsido047/Monetary-Policy-Data-Library/issues)
- **Feature Requests:** [GitHub Discussions](https://github.com/nsido047/Monetary-Policy-Data-Library/discussions)
- **General Inquiries:** [your-email@institution.edu]
- **Twitter:** [@MonetaryDataLib]

---

## 🗺️ Roadmap

### Version 1.0 (Current)
- ✅ Federal Reserve QE announcements (QE1-QE4)
- ✅ Documentation and examples
- ✅ Data validation framework

### Version 1.1 (Q2 2025)
- 🔄 ECB APP and PEPP announcements
- 🔄 Bank of England QE data
- 🔄 Bank of Japan QE/QQE data

### Version 2.0 (Q3 2025)
- ⏳ Additional central banks (RBA, SNB, BoC)
- ⏳ Forward guidance database
- ⏳ Balance sheet time series

### Version 3.0 (Q4 2025)
- ⏳ API for programmatic access
- ⏳ Interactive visualization dashboard
- ⏳ Automated update pipeline

---

## 📊 Repository Statistics

![GitHub stars](https://img.shields.io/github/stars/nsido047/Monetary-Policy-Data-Library?style=social)
![GitHub forks](https://img.shields.io/github/forks/nsido047/Monetary-Policy-Data-Library?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/nsido047/Monetary-Policy-Data-Library?style=social)

**Last Updated:** October 2025  
**Total Events:** 250+  
**Central Banks:** 4  
**Data Coverage:** 2001–Present

---

<p align="center">
  <strong>Made with ❤️ for the monetary economics research community</strong>
</p>

<p align="center">
  <a href="#table-of-contents">Back to Top ↑</a>
</p>
