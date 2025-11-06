# Image Encryption GUI (Tkinter + NumPy + Pillow)

A lightweight desktop tool that lets you encrypt and decrypt images using two reversible methods:

- **XOR** — Apply a byte-wise XOR with an integer key (0–255) across every pixel channel.
- **Pixel Swap** — Swap pixels in 2×2 diagonal pairs; applying the same swap again restores the original image.

This project was developed as part of an internship at **SkillCraft Technology** to explore image processing fundamentals and practical GUI development with Tkinter.

---

## Features

- File browser for selecting images (`.jpg`, `.jpeg`, `.png`, `.bmp`)
- Method selection: `xor` or `swap`
- Key-based XOR encryption (user-supplied integer 0–255)
- Reversible operations: the same operation reverses the effect (use the same key for XOR)
- Success and error dialogs with saved output path
- Output files saved next to the original with a descriptive suffix

---

## Why this is educational

- Demonstrates how pixel data is represented and manipulated in memory.
- Shows how simple bitwise operations (XOR) affect image channels.
- Introduces reversible pixel-level permutation (swap) and the idea of invertible transforms.
- Reinforces fundamentals useful in cybersecurity, image forensics, and algorithm design.

**Important:** These methods are *teaching tools* and **are not secure** for protecting sensitive data. Do not use them to secure confidential information.

---

## How encryption and decryption work

### XOR
XOR is its own inverse. If `C = P ^ K` (where `P` is the plain image pixel byte, `K` is the key), then applying XOR with the same key to `C` recovers the original: `P = C ^ K`. Use the same integer key (0–255) for encryption and decryption.

### Pixel Swap
The implemented swap operation exchanges each pixel at `(i, j)` with the pixel at `(i+1, j+1)` inside non-overlapping 2×2 blocks. Swapping the same pairs a second time restores the image. Thus, the swap function is symmetric — applying it twice returns to the original.

---

## Installation & run (Linux / Windows / macOS)

```bash
# clone repo
git clone https://github.com/<your-username>/image-encryption-gui.git
cd image-encryption-gui

# create & activate virtual environment (optional but recommended)
python3 -m venv .venv
# Linux / macOS
source .venv/bin/activate
# Windows (PowerShell)
.venv\Scripts\Activate.ps1

# install dependencies
pip install -r requirements.txt

# run
python app.py
