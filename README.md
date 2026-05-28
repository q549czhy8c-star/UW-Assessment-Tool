# UW Assessment Tool

A standalone, browser-based underwriting (UW) assessment assistant for insurance case review, requirement checking, affordability analysis, and case-summary drafting.

## Public Link

- **Public app URL:** https://<your-github-username>.github.io/UW-Assessment-Tool/
- If the deployment is hosted somewhere else, update the URL above to the active public `index.html` location.

## Current Version

- **Application version:** `v2.9.0`
- **Version date:** 16 Apr 2026
- The version is shown in the browser title and in the app header. The in-app update log is available from the **Update Log** control.

## What This Tool Does

The tool consolidates day-to-day UW assessment workflows into one single-page web app. It is designed to reduce manual checking, keep related case data synchronized across tabs, and generate reusable UW text for case handling.

### 1. Policy Information Input

The **保單資料輸入** tab is the main data-entry workspace. It captures and persists case information such as:

- Basic application data, application type, signing dates, policyholder/insured information, and age handling.
- Product and policy details, including plan, premium mode, sum assured, other insurance coverage, and total-sum-assured logic.
- Financial Questionnaire inputs, including purpose of insurance, Source of Fund (SoF), Source of Wealth (SoW), premium source, income/assets, retirement details, target saving, and surrender value inputs.
- Premium Financing fields, including loan amount, loan rate, tenor, repayment amount, IFS-PF, customer authorization, workflow reminder, and pending-message triggers when documents are missing.
- Special-case indicators such as Trust, High Risk, Jumbo, NiceActimize, broker-related requirements, PS reinstatement, and Business Insurance.

Data entered here is reused by the affordability page, case summary, business-insurance checks, and export/import functions.

### 2. PS Reinstatement

The **PS reinstatement** tab appears when PS reinstatement is enabled in Policy Info. It supports reinstatement-focused data capture, including current/revised plan values and position-related information needed for reinstatement handling.

### 3. Business Insurance Requirement Checking

The **Business Insurance** tab appears when Business Insurance is selected in Policy Info and a business purpose is selected in the Financial Questionnaire. It checks requirement status for business cases such as:

- Key person insurance.
- Partnership / shareholder protection.
- Business loan protection.
- Employee benefit use cases.

It uses the policy plan, total sum assured, ownership percentage, company market value, annual remuneration, company gross/net profit, loan amount, BIQ completion, and loan-agreement status to show PASS/MISSING requirement rows.

### 4. Affordability Calculator

The **負擔能力計算** tab supports income, asset, and combined affordability approaches. Key functions include:

- Importing policy data from Policy Info.
- Handling multiple policies, Applying / Existing / Pending statuses, Regular Pay / Single Pay / Prepay logic, and Premium Financing cases.
- Applying SoF-driven reminders when the selected affordability approach does not match the SoF category.
- Calculating income sufficiency, asset sufficiency, pre-retirement and post-retirement affordability, total annual premiums, and asset requirements.
- Including other insurance coverage and plan multipliers where relevant.
- Supporting print-friendly affordability output.

### 5. Case Summary Generator

The **Case Summary** tab converts the captured case data into structured UW comments and copy-ready text. It summarizes:

- Case basics, parties, plan and premium details.
- FNA / affordability conclusion and supporting figures.
- Source of Fund / Source of Wealth rationale.
- Trust, AML, high-risk, jumbo, HNW, Premium Financing, NiceActimize, Commission Spreading, and other special-case wording.
- Issue UN / pending messages generated from missing or inconsistent requirements.

The tab includes copy controls so underwriters can quickly reuse the generated wording.

### 6. UN Screen / Text Splitter

The **UN Screen** tab formats pending and FYI text into screen-friendly line blocks. It supports:

- Bulk paste parsing.
- Pending / FYI / custom prefixes.
- Optional numbering removal.
- Configurable line length and row limits.
- Auto-sorting pending items before FYI/custom items.

### 7. Pending Message Sample Library

The **Pending message sample** tab provides a searchable library of pending and FYI message templates. It is intended for quick lookup and copy of common UW pending messages.

### 8. Exclusion Code Lookup

The **Exclusion Code** tab provides searchable exclusion-code reference data for UW handling.

### 9. Occupation Rating Manual

The **Occupation Rating** tab provides an occupation-rating reference table with keyword search across:

- Industry.
- Chinese job title.
- English job title.
- Life / CI / WP rating values.

### 10. Salary Benchmark Dashboard

The **Salary Benchmark** tab embeds the bundled salary benchmark dashboard from `salary-benchmark-dashboard-single.html`. It gives salary reference data and links to source references for benchmark checking.

### 11. Master Broker List

The **Master Broker List** tab provides a searchable broker reference table, grouping broker names with RM and support assignments.

### 12. Case Data Management

The app uses browser `localStorage` for persistence. It supports:

- Autosaving key form state in the browser.
- Exporting case data to JSON.
- Importing JSON case data.
- Maintaining recent saved cases in browser storage.
- Resetting stored case data when starting a new case.

## Technical Overview

This is a single-file React application with no build step:

- `index.html` contains the main UI, constants, logic, tab components, local persistence, update log, export/import flow, and rendering entry point.
- `salary-benchmark-dashboard-single.html` contains the embedded salary benchmark dashboard used by the Salary Benchmark tab.
- `README.md` documents usage, versioning, and functionality.

External browser CDN dependencies:

- React 18 UMD build.
- ReactDOM 18 UMD build.
- Tailwind CSS CDN.
- Babel Standalone.

Because the app loads these dependencies from CDNs, an internet connection is required unless the dependencies are bundled locally in a future version.

## Getting Started

### Option 1: Use the Public Link

Open the public app URL in a modern browser:

```text
https://<your-github-username>.github.io/UW-Assessment-Tool/
```

### Option 2: Open Locally

1. Clone or download this repository.
2. Open `index.html` directly in Chrome, Edge, Safari, or another modern browser.

### Option 3: Serve Locally

Serving locally is recommended when testing import/export behavior or browser storage behavior.

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

## Versioning Policy

The app keeps an in-code `CURRENT_VERSION` and `versionHistory` list.

Suggested versioning convention:

- **Major version** (`v3.0.0`) — large workflow additions, major rule changes, or structural redesign.
- **Minor version** (`v2.10.0`) — new tabs, new modules, new calculation logic, or meaningful workflow enhancements.
- **Patch version** (`v2.9.1`) — wording changes, small rule updates, data updates, bug fixes, and UI refinements.

When updating the app:

1. Update the `<title>` version in `index.html`.
2. Update `CURRENT_VERSION` in `index.html`.
3. Add a new entry to `versionHistory` with version, date, update type, and changes.
4. Update this README if the user-facing workflow or public link changes.

## Change Log

### v2.9.0 — 16 Apr 2026 — Major Update

- Added the **Business Insurance** checkbox in Policy Info.
- Added a conditional **Business Insurance** tab after Policy Info when enabled.
- Added business-insurance requirement checking based on policy inputs and business-purpose Financial Questionnaire selections.
- Added business-specific fields such as ownership percentage, company market value, annual remuneration, company profits, loan amount, BIQ completion, and loan-agreement status.
- Added local persistence for Business Insurance inputs and reset cleanup.

### v2.8.635 — 01 Apr 2026 — Patch Update

- Added Premium Financing dropdowns for IFS-PF and Customer Letter of Authorization.
- Added automatic pending UN messages when Premium Financing document dropdowns are set to `No`.
- Removed one IFS-PF dropdown wording option and moved the O2O reminder into the general Premium Financing reminder area.
- Added the Premium Financing workflow hyperlink/reminder.

### v2.8.634 — 01 Apr 2026 — Patch Update

- Updated Case Summary FNA wording for non-Premium-Financing cases when assets are required before or after retirement.

### v2.8.633 — 27 Mar 2026 — Patch Update

- Updated Reasonable Target Protection Range checking to use `1 USD = 8 HKD` for sum-assured conversion.

### v2.8.632 — 23 Mar 2026 — Patch Update

- Simplified Source of Fund labels by removing bracketed explanations.
- Updated SoF wording to Income, Investment Income, and Retirement Fund.

### v2.8.631 — 19 Mar 2026 — Patch Update

- Updated SoF and SoW option wording.
- Updated FNA suitability Part 2 Q2 mapping.
- Added per-row plan selection for Other Insurance Coverage and automatic medical/financial multipliers.
- Added affordability approach mismatch warning based on Policy Info SoF.
- Added temporary reminder for new FNA requirements from 31 Mar 2026.

Older entries are maintained inside the in-app **Update Log**.

## Maintenance Notes

- The project currently has no automated test suite or package manager configuration.
- Most changes are made directly in `index.html`; keep updates small and document them in `versionHistory`.
- Be careful when changing constants or wording because many case-summary, affordability, and pending-message outputs depend on exact text matches.
- If the tool grows further, consider splitting the single HTML file into modular React components and adding a build/test toolchain.
