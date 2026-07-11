# Setting Up Anaconda Python with Positron IDE

**Source:** Gemini in Google search on 2026-07-11.

This guide walks you through installing **Anaconda** to manage your Python
environments and configuring **Positron** as your interactive data science IDE.

---

## Prerequisites

Before beginning, ensure your system meets the basic requirements for both
tools. No prior installation of Python is required.

---

## Step 1: Install Anaconda

Anaconda provides the Python language, data science packages, and the `conda`
environment manager.

1. Go to the official [Anaconda Downloads](https://anaconda.com) page.
2. Download the installer matching your operating system (**Windows**,
   **macOS**, or **Linux**).
3. Run the installer and follow the prompts:
   - **Windows**: It is generally recommended to leave **"Add Anaconda3 to my
     PATH environment variable"** unchecked unless you have a specific reason to
     enable it. Use the Anaconda Navigator or Anaconda Prompt instead.
   - **macOS/Linux**: Allow the installer to run `conda init` at the end of the
     setup.
4. Open your terminal (**Anaconda Prompt** on Windows, or your standard
   **Terminal** on macOS/Linux) and verify the installation:
   ```bash
   conda --version
   ```

---

## Step 2: Create a Dedicated Conda Environment

It is best practice to create an isolated environment for your data science
projects rather than installing packages into the base environment.

1. Open your terminal or Anaconda Prompt.
2. Create a new environment named `data-env` running Python 3.11 (or your
   preferred version):
   ```bash
   conda create --name data-env python=3.11 -y
   ```
3. Activate your new environment:
   ```bash
   conda activate data-env
   ```
4. Install essential data science libraries and the kernel gateway package
   (`ipykernel`), which allows IDEs to interact with this environment:
   ```bash
   conda install pandas numpy matplotlib ipykernel -y
   ```

---

## Step 3: Install Positron

Positron is a lightweight, data-centric IDE built by Posit.

1. Navigate to the [Positron Releases](https://github.com) page on GitHub.
2. Download the latest stable release for your architecture (e.g., `.exe` for
   Windows, `.dmg` for macOS).
3. Install and launch the application.

---

## Step 4: Connect Anaconda to Positron

Positron features automatic environment discovery and will actively scan your
system for Conda environments.

1. Launch **Positron**.
2. Look at the **Status Bar** in the bottom-right corner of the window. You will
   see a language indicator button (it may say `No Interpreter` or show a
   default system Python).
3. Click on the **Python Interpreter** indicator button to open the command
   palette.
4. Select your newly created environment from the list. It will typically be
   formatted like:
   `Python 3.11.x (data-env) - ~/.conda/envs/data-env/bin/python`
5. Open a new Python file (`Ctrl+N` or `Cmd+N`), save it as `test.py`, and write
   a quick script to verify the connection:
   ```python
   import pandas as pd
   print("Pandas loaded successfully!")
   ```
6. Click the **Run** button or press `Shift+Enter` to execute the code in the
   interactive Positron Console.

---

## Troubleshooting

### Positron Cannot Find the Conda Environment

If your environment does not appear in the interpreter list:

- Ensure you installed `ipykernel` inside that specific Conda environment.
- Restart Positron to force a fresh scan of your system paths.
- Manually point to the interpreter by selecting **"Find Interpreter..."** from
  the selection menu and navigating directly to the folder path where your
  environment executable resides.
