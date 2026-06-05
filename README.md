# TTS-REPORTS-V1.0-MVP-RELEASE

# TTS Reports V1.0 Stable Build

**TTS Reports V1.0 MVP** is a local web-based reporting app designed to help Metrel aPAT and ES Manager users import project data, review an asset register, preview reports, and export cleaner customer-ready PDF reports.

This build is intended as a stable MVP for internal testing, controlled customer testing, and early workflow validation.

---

## Purpose

Users often experience difficulty generating clear reports from existing Metrel reporting workflows such as PATLink PC and ES Manager. TTS Reports provides a simpler reporting workflow:

1. Import a supported project file.
2. Review the imported Asset Register.
3. Preview the report.
4. Export a customer-ready PDF.

The app is designed to support contractors, compliance testers, and support teams who need a faster way to turn Metrel project exports into usable reports.

---

## Current Build

**Build name:** TTS Reports V1.0 Stable Build - Version Label  
**Version label shown in app:** TTS Reports V1.0 MVP  
**App type:** Local Flask web app  
**Primary output:** PDF reports  
**Status:** MVP / stable test build

---

## Key Features

### Local Web App

- Runs locally on the user's computer.
- Opens in a browser at `http://127.0.0.1:5000`.
- No cloud account required for this V1.0 MVP build.

### Multi-format Import

Supported project file types:

| File Type | Source |
|---|---|
| `.pdf` | Project report exported directly from the Metrel aPAT Android Application |
| `.padfx` | Project export from the Metrel aPAT Android Application |
| `.apx` | Project export / MESM file from the Metrel aPAT Android Application |
| `.padfx` | Saved project file from a project imported into the Metrel ES Manager Software |
| `.xlsx` | Exported project spreadsheet from the Metrel ES Manager Software |

### Asset Register Dashboard

- Displays imported asset data in a dashboard.
- Includes summary cards/statistics.
- Supports dashboard search.
- Supports status filtering.
- Supports location filtering.
- Includes a **Tested By** column where tester/operator data is available.
- Clicking an asset opens the asset details in a modal popup.

### Asset Details Modal

- Opens when a user selects an asset.
- Can be closed using:
  - the close button
  - clicking outside the modal
  - pressing `Esc`

### Table View and Tree View

The Asset Register Dashboard includes two view modes:

- **Table View** — standard asset register table.
- **Tree View** — assets grouped by location.

Tree View features:

- Groups assets directly by location.
- Expand and collapse individual locations.
- **Expand all** option.
- **Collapse all** option.
- Clicking an asset opens the asset detail modal.

### Reports Page

Reports are generated only from the **Reports** page.

Available report types:

- **Basic Report**
- **PRO Report**
- **Upcoming Retest Report**
- **Advanced / Audit Report**

### Report Preview

- Users can preview a report before exporting.
- Preview opens inside the app.
- Users can export the PDF from the preview.
- Direct PDF generation is still available.

### PDF Export

- Generates customer-ready PDF reports.
- Reports can be downloaded through the browser.
- Reports may also be saved in the app's `output` folder depending on the workflow.

### Simplified Settings

The Settings page has been simplified for V1.0.

Current Settings tabs:

- **Business**
- **Report Defaults**
- **Report Template Defaults**
- **Sign-off**

Removed from V1.0 visible settings:

- Branding
- Retest settings
- Import settings
- PDF settings
- Privacy settings
- Advanced/developer settings

### Help Page

The app includes a built-in Help page with a Quick Set-up Guide covering:

- Starting the app
- Importing files
- Supported file types
- Reviewing the Asset Register
- Using Table View and Tree View
- Using the asset modal
- Completing settings
- Previewing reports
- Exporting reports
- Troubleshooting

### Version Label

The app includes a small footer-style version label:

```text
TTS Reports
V1.0 MVP
```

---

## Recommended Folder Structure

After extracting the build, the project folder should look similar to this:

```text
TTS_REPORTS_V1_0/
│
├── app.py
├── cli.py
├── report_core.py
├── requirements.txt
├── build_windows.bat
│
├── templates/
│   └── index.html
│
├── static/
│   └── style.css
│
├── samples/
│   └── sample project files
│
├── uploads/
│   └── temporary imported files
│
└── output/
    └── generated PDF reports
```

The `uploads` and `output` folders may be created automatically if they do not already exist.

---

## Requirements

- Windows 10 or later recommended
- Python 3.11 or newer recommended
- Google Chrome, Microsoft Edge, or another modern browser

Python packages:

- Flask
- ReportLab
- PyMuPDF
- PyInstaller, only required if building a Windows executable

---

## Installation

### 1. Install Python

Download Python from:

```text
https://www.python.org/downloads/
```

During installation, tick:

```text
Add Python to PATH
```

Check Python is installed:

```bat
python --version
```

---

### 2. Extract the Build

Extract the project zip to a simple folder, for example:

```text
C:\PROJECTS\TTS REPORTS V1.0
```

---

### 3. Open Command Prompt

Navigate to the extracted project folder:

```bat
cd "C:\PROJECTS\TTS REPORTS V1.0"
```

---

### 4. Create a Virtual Environment

```bat
python -m venv .venv
```

Activate it:

```bat
.venv\Scripts\activate
```

You should see:

```text
(.venv)
```

at the start of the Command Prompt line.

---

### 5. Install Dependencies

```bat
python -m pip install --upgrade pip
pip install -r requirements.txt
```

If `pyinstaller` is not included in `requirements.txt` and you want to build an executable, install it separately:

```bat
pip install pyinstaller
```

---

## Running the App

From the project folder, run:

```bat
python app.py
```

You should see:

```text
Running on http://127.0.0.1:5000
```

Open your browser and go to:

```text
http://127.0.0.1:5000
```

---

## Basic Workflow

1. Start the app.
2. Import a supported project file.
3. Review the imported assets on the Asset Register Dashboard.
4. Use Table View or Tree View to inspect the data.
5. Click an asset to view its details in a modal.
6. Complete or confirm relevant settings.
7. Go to the Reports page.
8. Select the report type.
9. Preview the report.
10. Export the PDF.

---

## Report Types

### Basic Report

A simpler customer-facing report with a richer title page and a simpler report body.

Includes:

- customer/site details
- contractor details
- generated date
- test standard
- report basis
- testing start/end information
- next inspection date
- operator/tester
- asset count summary
- results summary
- notes section
- sign-off area

### PRO Report

A more detailed report with fuller report information and detailed result tables.

### Upcoming Retest Report

A forward-looking report for assets due for retesting.

### Advanced / Audit Report

A more detailed reporting mode for historical, date range, or audit-style review.

---

## Building a Windows Executable

Use a clean virtual environment before building. This avoids PyInstaller scanning unrelated packages from the global Python environment.

Recommended build sequence:

```bat
cd "C:\PROJECTS\TTS REPORTS V1.0"

python -m venv .venv

.venv\Scripts\activate

python -m pip install --upgrade pip

pip install -r requirements.txt

pip install pyinstaller

build_windows.bat
```

The executable should be created in:

```text
dist\
```

Example:

```text
dist\TTSProReportGenerator.exe
```

Run the executable, then open:

```text
http://127.0.0.1:5000
```

---

## Troubleshooting

### Python is not recognised

Python may not be installed or may not have been added to PATH.

Reinstall Python and select:

```text
Add Python to PATH
```

---

### App does not open in browser

Make sure the app is running in Command Prompt.

Look for:

```text
Running on http://127.0.0.1:5000
```

Then manually open:

```text
http://127.0.0.1:5000
```

---

### Port 5000 is already in use

Close other local Flask/Python apps or restart Command Prompt.

---

### Report does not download

Check:

- the browser Downloads folder
- the app `output` folder
- the Command Prompt window for errors

---

### PDF import does not work

The PDF must contain selectable text. Scanned/image-only PDFs are not supported by this MVP build because OCR is not included.

---

### Windows build takes a long time

Use a clean virtual environment before running `build_windows.bat`.

If PyInstaller scans unrelated packages like Torch, SciPy, or Pandas, it may take a long time or appear stuck. A clean `.venv` keeps the build smaller and faster.

---

## MVP Scope

This build is intended to validate the core product idea:

```text
Can users import Metrel project data, review the asset register, preview reports, and export a cleaner PDF report faster than using the existing reporting workflow?
```

This V1.0 build is suitable for:

- internal testing
- staff demonstration
- limited customer testing
- workflow validation
- collecting feedback before cloud/SaaS development

This build is not yet intended as a full cloud SaaS product.

---

## Future Expansion Ideas

Possible future features include:

- hosted web app version
- user accounts
- cloud storage
- customer database
- site/location management
- saved project history
- report history
- branded report themes
- logo upload
- multiple report templates
- failed asset report
- improved retest report
- retest reminder system
- CSV/XLSX export
- bulk report generation
- email-ready report summaries
- customer portal
- TTS admin portal
- product/consumables marketing section
- AI-assisted report checking
- AI help assistant
- export guides with screenshots or video

---

## Important Notes

This project is an MVP and should be tested with multiple real-world files before broader release.

Recommended test files:

- aPAT PDF export
- aPAT `.padfx`
- aPAT `.apx`
- ES Manager `.padfx`
- ES Manager `.xlsx`

Before relying on generated reports commercially, confirm that imported asset data, test results, dates, standards, and customer details match the original source project.

---

## License / Internal Use

Add your preferred licence or internal-use notice here.

Example:

```text
Copyright © Test and Tag Supplies.
Internal MVP build. Not for public distribution without approval.
```
