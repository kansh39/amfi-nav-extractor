# AMFI NAV Extractor

This project extracts **Scheme Name** and **Net Asset Value (NAV)** from the [AMFI NAVAll.txt](https://www.amfiindia.com/spages/NAVAll.txt) file and saves the output in TSV format. An optional step converts the data into JSON format for easier use in APIs or structured applications.

---

## 📁 Files Included

- `NAVAll.txt` – Original downloaded data from AMFI (optional)
- `scheme_nav.tsv` – Extracted Scheme Name and NAV as tab-separated values
- `scheme_nav.json` – (Optional) JSON version of the data
- `nav_extraction_colab.ipynb` – Google Colab notebook with full workflow
- `extract_nav.sh` – (Optional) Shell script for local execution

---

## 🚀 How It Works

### ▶️ Google Colab Instructions
1. Open `nav_extraction_colab.ipynb` in [Google Colab](https://colab.research.google.com).
2. Run the notebook to:
   - Download `NAVAll.txt`
   - Extract Scheme Name and NAV using `awk`
   - Save result as `scheme_nav.tsv`
   - (Optional) Convert to `scheme_nav.json`

---

## 💻 Shell Script (for Linux/Mac)

If you prefer using a shell script locally:

```bash
#!/bin/bash

# Download NAVAll.txt from AMFI
curl -s https://www.amfiindia.com/spages/NAVAll.txt -o NAVAll.txt

# Extract Scheme Name and NAV using awk
awk -F ';' 'NR > 1 && NF >= 5 { print $4 "\t" $5 }' NAVAll.txt > scheme_nav.tsv

echo "Saved to scheme_nav.tsv"
