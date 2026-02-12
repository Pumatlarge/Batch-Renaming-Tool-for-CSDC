# PDF-Batch-Renaming-Tool-for-CSDC-China-Securities-Depository-and-Clearing-Corporation

---

## 📘 Technical Documentation: PDF Batch Renaming Tool

**Development and Packaging Guide for PDF Batch Renaming Tool**

### I. Project Background

When processing Security Holding Change Information PDFs exported from the **CSDC (China Securities Depository and Clearing Corporation)** system, the following requirements must be met:

* **Batch processing:** Efficiently read multiple PDF files.
* **Data Extraction:** Identify and extract:
1. Securities Sub-account Number
2. Holder Name


* **Standardized Naming:** Automatically generate filenames based on extracted data.
* **Data Integrity:** Preserve original files and output to a dedicated sub-folder.
* **Ease of Use:** Support drag-and-drop functionality for offline execution.

### II. Functional Requirements

#### 1. Input Methods

The tool supports:

* Dragging and dropping single/multiple PDFs.
* Dragging and dropping single/multiple folders.
* Mixed drag-and-drop (files and folders combined).
* Double-clicking the executable to manually select a folder via a popup window.

#### 2. Naming Convention

New Filename = `Securities Sub-account Number-Holder Name.pdf`

> **Example:** `A290546372-李大强.pdf`

#### 3. Output Rules

* **Non-destructive:** Does not modify the original files.
* **Directory Structure:** Creates a sub-folder named `Renamed_Output` in the source directory.
* **Duplicate Handling:** Automatically appends a suffix if a file exists:
* `A290546372-李大强.pdf`
* `A290546372-李大强(2).pdf`



#### 4. Log Generation

Automatically generates a `Renaming_Log.csv` containing:

* `Original Filename` | `Output Filename`

### III. Technical Stack

* **Python 3.13**
* **pdfplumber:** For PDF text parsing.
* **shutil:** For file copying operations.
* **PyInstaller:** For converting the script into a standalone EXE.

### IV. Core Logic Implementation

* **Field Extraction (Regex):**
`m1 = re.search(r"证券子账户号码\s*：\s*([A-Za-z0-9]+)", text)`
`m2 = re.search(r"持有人名称\s*：\s*(\S+)", text)`
* **File Operation:**
Uses `shutil.copy2(src_path, dst_path)` to ensure original files are preserved along with their original timestamps.

### V. Packaging Process (EXE)

#### 1. Create a Clean Virtual Environment (Highly Recommended)

```bash
python -m venv packenv
.\packenv\Scripts\activate
pip install -U pip
pip install pyinstaller pdfplumber

```

#### 2. Packaging Command

```bash
pyinstaller --onefile --console --clean --noconfirm rename_pdf_drag.py -n PDF_Renaming_Tool

```

#### 3. Output

The final executable is located in: `dist\PDF_Renaming_Tool.exe`

### VI. Troubleshooting

| Issue | Cause | Solution |
| --- | --- | --- |
| **Drag & Drop fails** | Running as Administrator | Do **not** run as Admin; drag files directly onto the EXE icon. |
| **PKG phase stuck** | Global environment contains large libs (e.g., torch, pandas) | Use a clean **venv** for packaging. |
| **Empty "dist" folder** | Antivirus interference or incomplete build | Disable antivirus temporarily and check terminal logs. |

### VII. Directory Structure Example

```text
Source Directory/
├── Original_Files.pdf
├── Renamed_Output/
│   ├── A290546372-李大强.pdf
│   └── Renaming_Log.csv

```

### VIII. Security & Compliance

* **Local Execution:** The tool runs entirely offline.
* **Privacy:** No data is uploaded or transmitted over the network.
* **Suitability:** Designed for processing sensitive securities registration documents within internal networks.

---
