# PDFLinuxVM

**PDFLinuxVM** is an experimental project that runs a full Linux operating system inside a PDF file using a lightweight RISC-V emulator written in C and compiled to JavaScript.
[![View Live](https://img.shields.io/badge/View-PDFLinuxVM-blue?logo=google-chrome)](https://pritisingh-09.github.io/PDFLinuxVM/PDFLinuxVM.pdf)

**PDFLinuxVM** is an experimental project that runs a full Linux operating system inside a PDF file using a lightweight RISC-V emulator written in C and compiled to JavaScript.

> 📂 **[Click here to view the live PDF](https://pritisingh-09.github.io/PDFLinuxVM/PDFLinuxVM.pdf)** (works best in Chromium-based browsers)
This PDF-based Linux environment can boot a real Linux kernel directly inside Chromium-based browsers with PDF viewer support for embedded JavaScript.

---

## 💡 Project Overview

PDFs are typically used for static content — but this project takes things further by embedding a RISC-V emulator compiled via Emscripten (asm.js) into a PDF file. The result: an interactive Linux terminal that runs directly in-browser from a PDF.

The interface includes a virtual keyboard and text box for input, while output is rendered using ASCII characters mapped to PDF form fields.

This is a reimagined and educational take on virtual computing within constrained environments like PDFs.

---

## 🚀 Features

- Run a real Linux OS from inside a PDF
- No installations or extensions required
- Fully self-contained emulator
- 32-bit and 64-bit root filesystem support
- Minimalistic UI for interaction (text + keyboard)
- Portable and hackable

---

## 🛠️ Build Instructions

This project must be built on a **Linux system**.

Clone and set up the environment:

```bash

git clone https://github.com/pritisingh-09/PDFLinuxVM.git
cd PDFLinuxVM

python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
./build.sh

If you want to build the 64-bit version, open the build.sh file and change:
BITS="32"
to
BITS="64"
Once built, the output files will be placed in the out/ directory.

To test locally, run:
cd out
python3 -m http.server
Then open http://localhost:8000/linux.pdf in a Chromium browser.
```
Output
All PDF and emulator files are exported to the out/ folder after a successful build. You can share or embed the linux.pdf file wherever needed.

Background
PDFLinuxVM is inspired by the capabilities of JavaScript in PDF viewers. Although most browser-based PDF engines (like Chromium's PDFium) implement a restricted version of Adobe’s JavaScript API, it’s still possible to run logic-heavy code using asm.js compiled C programs.

The Linux boot process is significantly slower in this environment (up to 100x) due to the absence of JIT compilation in browser PDF engines. Still, it’s an impressive demonstration of constrained computing inside document formats.

Credits

Initial inspiration from earlier PDF-based interactive projects- [@ading2210](https://github.com/ading2210/).

Reworked and adapted into PDFLinuxVM by Priti Singh

The RISC-V emulator is forked from [TinyEMU](https://bellard.org/tinyemu/), which was written by [Fabrice Bellard](https://bellard.org/).

License

This repository is licensed under the GNU GPL v3.

PDFLinuxVM - Run Linux inside a PDF file  
Copyright (C) 2025 Priti Singh

This program is free software: you can redistribute it and/or modify  
it under the terms of the GNU General Public License as published by  
the Free Software Foundation, either version 3 of the License, or  
(at your option) any later version.

This program is distributed in the hope that it will be useful,  
but WITHOUT ANY WARRANTY; without even the implied warranty of  
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the  
GNU General Public License for more details.

You should have received a copy of the GNU General Public License  
along with this program. If not, see <https://www.gnu.org/licenses/>.
