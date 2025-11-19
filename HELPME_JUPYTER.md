# How to Install and Use Jupyter Notebook in VS Code

## Overview

Jupyter Notebook integration in VS Code allows you to write, execute, and visualize Python code in interactive notebook cells. This guide walks you through installation and usage step-by-step.

---

## Part 1: Installation

### Step 1: Ensure Python is Installed

First, verify that Python is installed on your system.

```bash
python3 --version
```

If Python is not installed, download it from [python.org](https://www.python.org/downloads/).

### Step 2: Install Jupyter

Open a terminal and install Jupyter using pip:

```bash
pip install jupyter
```

Or if you're using conda:

```bash
conda install jupyter
```

Verify the installation:

```bash
jupyter --version
```

### Step 3: Install the Jupyter Extension in VS Code

1. Open VS Code
2. Go to the **Extensions** sidebar (click the Extensions icon or press `Cmd+Shift+X`)
3. Search for **"Jupyter"** (by Microsoft)
4. Click **Install** on the official Jupyter extension by Microsoft

Alternatively, you can install from the command line:

```bash
code --install-extension ms-toolsai.jupyter
```

### Step 4: Install Pylance (Optional but Recommended)

For better code intelligence and error checking in notebooks:

1. Search for **"Pylance"** in VS Code Extensions
2. Click **Install**

---

## Part 2: Create Your First Notebook

### Step 1: Create a New Notebook File

1. In VS Code, press `Cmd+Shift+P` to open the Command Palette
2. Type **"Jupyter: Create New Blank Notebook"**
3. Press Enter
4. A new `.ipynb` file will open (or save it with a name like `my_notebook.ipynb`)

**Alternative (faster):**
- Create a new file and name it with the `.ipynb` extension
- VS Code will automatically recognize it as a Jupyter Notebook

### Step 2: Select a Python Kernel

When you open a notebook, VS Code will prompt you to select a kernel (the Python environment to run code in).

1. Click the **Select Kernel** button in the top-right of the notebook
2. Choose one of these options:
   - **Python Environments**: Your system's default Python or virtual environments
   - **Existing Jupyter Server**: If you're running a Jupyter server elsewhere

If no kernel appears, ensure Python and Jupyter are installed (see Part 1).

---

## Part 3: Work with Notebook Cells

### Cell Types & Execution — Detailed Breakdown

This section expands the basics into a practical, step-by-step reference for working with cells in VS Code notebooks.

#### 1. Understanding Cell Types

There are two primary cell types:

- **Code Cells**: Contain executable Python code. Running a code cell executes the code in the selected kernel and displays the output immediately below the cell.
- **Markdown Cells**: Contain formatted text (Markdown). Use them for headings, explanations, lists, links, and inline math.

Quick example:

Code cell:
```python
x = 5
print(x)
```

Markdown cell:
```markdown
# Analysis
This cell explains what the code does.
```

#### 2. Creating Cells

Two common ways to add cells:

- **GUI buttons**: Use the `+ Code` or `+ Markdown` buttons above the current cell to insert a new cell of the chosen type.
- **Command Palette**: Press `Cmd+Shift+P` and run `Jupyter: Insert Cell Below` or `Jupyter: Insert Cell Above`.

Keyboard-focused workflow tip: use the command palette or map a shortcut for faster insertion when iterating quickly.

#### 3. Writing Code in a Code Cell

Write any valid Python code. Keep cells small and focused — one logical step per cell helps debugging and readability.

Example:
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
print("Array:", arr)
print("Sum:", np.sum(arr))
```

Expected output appears below the cell after execution.

#### 4. Executing Cells (Run Modes)

Use the run modes based on what you need:

- **Run current cell**: Click the ▶️ play icon to the left of the cell or press `Ctrl+Enter` — runs only the selected cell.
- **Run and advance**: Press `Shift+Enter` — runs the current cell and moves the cursor to the next cell (creates one if none exists).
- **Run all**: From the Command Palette (`Cmd+Shift+P`) run `Jupyter: Run All Cells` — executes the whole notebook top-to-bottom.
- **Run above / below**: Use the Command Palette to run only cells above or below the current cell when you want a partial execution.

Practical tips:

- Use `Ctrl+Enter` for iterative testing of a single cell.
- Use `Shift+Enter` to step through a notebook like a script.
- Run all after a kernel restart to validate notebook reproducibility.

#### 5. Cell Output and Management

After execution, outputs (text, tables, images, plots) appear below the cell.

Common actions:

- **Clear output**: Click the trash icon on the cell toolbar to clear that cell's output.
- **Clear all outputs**: `Cmd+Shift+P` → `Jupyter: Clear All Outputs`.
- **Scroll large outputs**: Large results are scrollable; expand or collapse them as needed.
- **View errors**: Exceptions show a full stack trace in red — use the traceback to debug.

Output examples:
```
Array: [1 2 3 4 5]
Sum: 15

ZeroDivisionError: division by zero
```

#### 6. Quick Reference Table

| Task | How to do it |
|------|--------------|
| Create a code cell | Click `+ Code` or `Cmd+Shift+P` → "Jupyter: Insert Cell Below" |
| Create a markdown cell | Click `+ Markdown` or use command palette |
| Run current cell | Click ▶️ or press `Ctrl+Enter` |
| Run and move next | Press `Shift+Enter` |
| Run all cells | `Cmd+Shift+P` → "Jupyter: Run All Cells" |
| Clear outputs | Click trash icon or `Jupyter: Clear All Outputs` |

---

## Part 4: Practical Example

Here's a complete example notebook workflow:

### Cell 1 (Markdown)
```markdown
# My First Jupyter Notebook

This notebook demonstrates the Perceptron classifier from our project.
```

### Cell 2 (Code)
```python
import numpy as np
import sys
sys.path.append('/Users/juniorjoseph/Documents/machine-learning/perceptron-api')

from oo_perceptron_api import Perceptron

# Create sample data
np.random.seed(1)
X = np.random.randn(100, 2)
y = np.where(X[:, 0] + X[:, 1] > 0, 1, -1)

print(f"Training data shape: {X.shape}")
print(f"Class distribution: {np.bincount(y)}")
```

### Cell 3 (Code)
```python
# Train the perceptron
ppn = Perceptron(eta=0.01, n_iter=50)
ppn.fit(X, y)

print(f"Final weights: {ppn.w_}")
print(f"Errors per epoch: {ppn.errors_}")
```

### Cell 4 (Code)
```python
# Make predictions
X_test = np.array([[1.0, 1.0], [-1.0, -1.0]])
predictions = ppn.predict(X_test)
print(f"Predictions: {predictions}")
```

---

## Part 5: Common Tasks

### Save Your Notebook

Notebooks are auto-saved, but you can also:
- Press `Cmd+S` to save manually
- Files are saved as `.ipynb` (JSON format with code and outputs)

### Clear All Outputs

1. `Cmd+Shift+P`
2. Type **"Jupyter: Clear All Outputs"**
3. Press Enter

### Restart the Kernel

If variables persist or you want a fresh start:

1. Click the **⟲ Restart** button (top toolbar), or
2. `Cmd+Shift+P` → "Jupyter: Restart Kernel"

### Convert Notebook to Python Script

To save your notebook as a `.py` file:

1. `Cmd+Shift+P`
2. Type **"Jupyter: Export Current Notebook as Python Script"**

### Debugging in Notebooks

- Print variables and outputs to inspect values
- Use `?function_name` to view function documentation
- Use `help(function_name)` for detailed help
- Errors appear in red with full stack traces

---

## Part 6: Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+Enter` | Run current cell |
| `Shift+Enter` | Run current cell and move to next |
| `Cmd+Shift+P` → "Jupyter: Insert Cell Below" | Insert new cell |
| `Cmd+Shift+P` → "Jupyter: Run All Cells" | Run entire notebook |
| `Cmd+K Cmd+C` | Comment/uncomment code |
| `Cmd+/` | Toggle line comment |
| `Cmd+Shift+L` | Format document (if formatter installed) |

---

## Part 7: Troubleshooting

### Issue: "Kernel not found" or "Python not installed"

**Solution:**
```bash
# Check Python is in PATH
which python3

# Reinstall Jupyter
pip install --upgrade jupyter
```

### Issue: Cannot import modules

**Solution:**
- Ensure the module is installed: `pip install module_name`
- Add the module path to your notebook:
  ```python
  import sys
  sys.path.append('/path/to/module')
  ```

### Issue: Notebook runs slowly

**Solution:**
- Restart the kernel: click the **⟲ Restart** button
- Clear outputs: `Cmd+Shift+P` → "Jupyter: Clear All Outputs"
- Close unused notebooks

### Issue: VS Code doesn't recognize `.ipynb` files

**Solution:**
- Reinstall the Jupyter extension
- Reload VS Code: `Cmd+Shift+P` → "Developer: Reload Window"

---

## Part 8: Best Practices

1. **Organize with Markdown**: Use markdown cells to document what each section does
2. **Keep Cells Small**: Break complex logic into multiple cells for easier debugging
3. **Restart Before Running All**: Always restart the kernel before running all cells to ensure clean execution
4. **Version Control**: Add `.ipynb` files to `.gitignore` if you only want to version the `.py` script
5. **Use Relative Imports**: Use absolute paths or `sys.path` for imports to avoid issues
6. **Document Your Code**: Add comments and markdown explanations for clarity

---

## Part 9: Next Steps

- Explore the Jupyter extension settings: `Cmd+,` → Search "Jupyter"
- Install additional Python packages as needed for your projects
- Create notebooks for data exploration, machine learning experiments, or documentation
- Share notebooks with colleagues or save as HTML/PDF

---

## Resources

- [Official Jupyter Documentation](https://jupyter.org/)
- [VS Code Jupyter Extension](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)
- [Jupyter Keyboard Shortcuts](https://jupyter-notebook.readthedocs.io/en/stable/notebook.html#keyboard-shortcuts)
- [NumPy Documentation](https://numpy.org/doc/)

---

## Quick Reference: Common Commands

```bash
# Install Jupyter
pip install jupyter

# Start Jupyter server (optional)
jupyter notebook

# Install a package
pip install package_name

# Check installed packages
pip list
```

---

Happy coding! 🚀
