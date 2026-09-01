# User Manual: Creating and Activating a Python Virtual Environment and Installing a Package

## Prerequisites
Before starting this procedure, ensure you have:
- Python installed on your computer (version 3.8 or higher)
- pip (Python package installer) installed (comes with Python by default)
- A terminal/command prompt open on your computer
- An internet connection
- Basic knowledge of navigating folders using command line (cd, dir/ls commands)

---

## Step-by-Step Procedure

### Step 1: Create a project folder
**Action:** Open your terminal and type `mkdir my-python-project` then press Enter.

**Expected Result:** A new folder named "my-python-project" appears in your current directory.

---

### Step 2: Navigate into the project folder
**Action:** Type `cd my-python-project` and press Enter.

**Expected Result:** Your terminal path changes to show you are now inside the "my-python-project" folder.

---

### Step 3: Create the virtual environment
**Action:** Type `python -m venv venv` and press Enter.

**Expected Result:** A new folder named "venv" appears inside your project folder. This contains a complete Python environment separate from your system Python.

**Screenshot Description:** *Include a screenshot showing the terminal after running the `python -m venv venv` command. The screenshot should show the terminal prompt, the command entered, and the newly created "venv" folder appearing when you run `dir` (Windows) or `ls` (Mac/Linux) afterward.*

---

### Step 4: Activate the virtual environment (Windows)
**Action:** Type `venv\Scripts\activate` and press Enter.

**Expected Result:** Your terminal prompt changes to show `(venv)` at the beginning of the line, indicating the virtual environment is active.

---

### Step 5: Activate the virtual environment (Mac/Linux)
**Action:** Type `source venv/bin/activate` and press Enter.

**Expected Result:** Your terminal prompt changes to show `(venv)` at the beginning of the line, indicating the virtual environment is active.

---

### Step 6: Verify the environment is active
**Action:** Type `which python` (Mac/Linux) or `where python` (Windows) and press Enter.

**Expected Result:** The terminal shows the path to the Python interpreter inside your venv folder (e.g., `/project/path/venv/bin/python`), confirming you are using the isolated environment.

---

### Step 7: Check the current installed packages
**Action:** Type `pip list` and press Enter.

**Expected Result:** A short list appears showing only `pip` and `setuptools` as installed packages. This confirms the environment is clean and isolated.

---

### Step 8: Install a package
**Action:** Type `pip install requests` and press Enter.

**Expected Result:** The terminal shows progress bars and messages as it downloads and installs the "requests" library. A success message appears at the end saying "Successfully installed requests-[version]".

---

### Step 9: Verify the package is installed
**Action:** Type `pip list` again and press Enter.

**Expected Result:** The package list now includes "requests" along with its version number, confirming the installation was successful.

---

### Step 10: Test the package
**Action:** Type `python` and press Enter to open the Python interactive shell.

**Expected Result:** Python starts, showing `>>>` prompt with the Python version information.

---

### Step 11: Import the installed package
**Action:** Type `import requests` and press Enter.

**Expected Result:** No error messages appear. This means the package imported successfully.

---

### Step 12: Exit the Python shell
**Action:** Type `exit()` and press Enter.

**Expected Result:** You return to the terminal prompt with `(venv)` still showing at the beginning.

---

### Step 13: Deactivate the virtual environment
**Action:** Type `deactivate` and press Enter.

**Expected Result:** The `(venv)` indicator disappears from your terminal prompt, confirming you have returned to the system Python environment.

---

### Step 14: Verify you are back to the system environment
**Action:** Type `which python` (Mac/Linux) or `where python` (Windows) and press Enter.

**Expected Result:** The path now shows the system Python location, not the venv folder location.

---

## Troubleshooting: "pip is not recognized" or "No module named pip" Error

**Most Common Error:** When running `pip install requests`, you receive an error message like `'pip' is not recognized as an internal or external command` (Windows) or `command not found: pip` (Mac/Linux).

**Solution:** This happens when pip is not installed or not accessible in your PATH. Follow these steps:

1. Check if pip exists by running `python -m pip --version` instead of `pip`
2. If that works, use `python -m pip install requests` as a workaround
3. If it doesn't work, you need to install pip:
   - Download get-pip.py from https://bootstrap.pypa.io/get-pip.py
   - Run `python get-pip.py` in your terminal
   - Verify installation with `python -m pip --version`

**Expected Result:** After following these steps, `python -m pip install requests` succeeds and the package installs correctly.

---

## Quick Reference Card
| Command | Purpose |
|---------|---------|
| `python -m venv venv` | Create virtual environment |
| `venv\Scripts\activate` (Windows) | Activate on Windows |
| `source venv/bin/activate` (Mac/Linux) | Activate on Mac/Linux |
| `pip install package_name` | Install a package |
| `pip list` | See all installed packages |
| `deactivate` | Exit virtual environment |
| `python -m pip` | Use pip if `pip` command fails |
