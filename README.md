<<<<<<< HEAD
test
=======
# DiSCo Streamlit Demo

This repository contains a Streamlit demo for  
**Domain-informed Summarization through Contrast (DiSCo)**.

The demo follows the IUI 2026 demonstration paper:

> **Demonstrating Domain-informed Summarization through Contrast (DiSCo)**  
> Proceedings of the ACM Conference on Intelligent User Interfaces (IUI 2026)

The application compares:
- a **standard (frequency-based) summary** of accommodation reviews, and
- a **DiSCo summary**, which highlights what is *overrepresented* or *underrepresented*
  relative to other accommodations in the same domain.

---

## 📁 Project structure

```text
.
├── app.py                  # Streamlit application
├── requirements.txt
├── data/
│   ├── summaries.csv
│   ├── <domain>_signatures.csv
│   ├── <domain>_freqs.csv
│   └── <domain>_dvr.csv
Each <domain> corresponds to an accommodation domain (e.g., hotels, apartments).
```

## 📊 Expected data files

The application expects all input data to be placed under the `data/` directory.

For each accommodation domain `<domain>`, the following CSV files are required.

---

### `<domain>_signatures.csv`

Domain-level divergence signatures per accommodation.

- **Rows**: accommodations  
- **Columns**:
  - The **first column must be** `accommodation_id`
  - All remaining columns correspond to topic–sentiment elements
- **Values**: numeric divergence scores

---

### `<domain>_freqs.csv`

Topic mention frequencies per accommodation.

**Required columns**:
- `accommodation_id`
- `element`
- `frequency`

---

### `<domain>_dvr.csv`

Global domain reference weights.

**Required columns**:
- `element`
- `global_weight`

---

### `summaries.csv`

Textual summaries displayed in the UI.

**Required columns**:
- `accommodation_id`
- `baseline_summary`
- `expectations_aware_summary`

---

**Notes**

- All `accommodation_id` values are treated as **strings**.
- Only accommodations present in both the domain files and `summaries.csv`
  will be selectable in the application.
- File names must follow the exact naming conventions shown above.

## 🚀 Running the app locally

### 1. Clone the repository
```bash
git clone https://github.com/ScanLab-ossi/DisCo--Demo.git
cd DisCo--Demo
```

### 2. Create a virtual environment (recommended)
```bash
python -m venv .venv
source .venv/bin/activate   # macOS / Linux
# or
.venv\Scripts\activate      # Windows
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Launch Streamlit
```bash
streamlit run app.py
```

The app will open automatically in your browser.

🧠 How to interpret the demo
- **Standard summary**
  Reflects what guests frequently mention within the selected accommodation.

- **DiSCo summary**
  Highlights topics that are:
  - **Overrepresented**: mentioned more than expected compared to the domain
  - **Underrepresented**: mentioned less than expected compared to the domain

Topics are ranked by **absolute divergence magnitude**, so the strongest
deviations from the domain appear first.

📄 Citation
If you use this demo or code, please cite:
```
@inproceedings{disco2026,
  title     = {Demonstrating Domain-informed Summarization through Contrast (DiSCo)},
  booktitle = {Proceedings of the ACM Conference on Intelligent User Interfaces (IUI)},
  year      = {2026}
}
```
>>>>>>> 248ff44 (demo files)
