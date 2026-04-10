# UW Assessment Tool

A standalone, browser-based underwriting (UW) assessment assistant packaged as a single HTML file.

## Overview

This repository contains a self-contained web app in `index.html` that helps users work through underwriting and financial-assessment workflows. It is built with:

- **React 18 (UMD build)**
- **Tailwind CSS (CDN)**
- **Babel Standalone**

No build step or package installation is required.

## Repository Structure

- `index.html` — Entire application UI and logic (single-file app).

## Getting Started

### Option 1: Open directly in a browser

1. Clone or download this repository.
2. Open `index.html` in a modern browser.

### Option 2: Serve locally (recommended)

Serving locally avoids certain browser security restrictions for some features.

```bash
python3 -m http.server 8000
```

Then open:

- `http://localhost:8000`

## Key Characteristics

- Single-page tabbed interface for UW-related workflows.
- Built-in calculators and rule-driven helper logic.
- Uses predefined options/constants for assessment scenarios and requirements.
- Designed for quick updates by editing one file.

## Versioning

The current in-page title indicates application version:

- `UW assessment tool (v2.8.635)`

## Notes

- This project currently has no formal automated test suite.
- If you want maintainable long-term development, consider splitting the code into modular React components and adding a build/test toolchain.
