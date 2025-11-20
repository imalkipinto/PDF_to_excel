# PDF_to_excel
convert tabular data in pdfs to excel or csv formats 

requirements

pandas>=1.5
tabula-py>=2.4.0
camelot-py[cv]>=0.10.1
pdfplumber>=0.7.6
openpyxl>=3.0

# Optional / system requirements (not installable via pip):
# - Java Runtime (for tabula-py)
# - Ghostscript (for camelot on Windows)


# PDF → CSV / Excel table extractor

This repository contains `convert.py`, a script to extract tables from PDF files and export them to CSV files or an Excel workbook.

Quick notes
- The script tries these extractors in this order: `tabula-py`, `camelot`, `pdfplumber` (falls back if earlier backend is not available).
- Large PDFs (600–700 pages) may take a long time to process. Use the `--pages` option to process in chunks.

Prerequisites (Windows)
- Python 3.8+
- Install Python packages: `pip install -r requirements.txt`.
- If you want the best results with `tabula-py`, install a Java runtime (JRE/JDK) and ensure `java` is on `PATH`.
- If you want to use `camelot`, install Ghostscript for Windows and add it to `PATH`.

Usage
```
python convert.py input.pdf --outdir Results/tables --format csv
python convert.py input.pdf --outdir Results/tables --format excel --pages 1-50
```

Tips for large PDFs
- Process the PDF in page ranges: `--pages 1-100`, then `101-200`, etc., to avoid long single runs and allow parallelization.
- If many tables have varying columns, CSV output will create one file per table, while Excel output writes each table as a separate sheet.

If you want, I can try a small extraction on a single-page sample PDF or add an optional `--chunk-size` driver to process large files in batches.

