---
icon:
  type: material-symbols:science
  color: "#15866C"
---

# Lab 1:

## Statistical Foundations and pandas for EDA


## Recommended environment: Google Colab

A GPU is not required.

## Install the required libraries

Run the installation cell at the beginning of the notebook:

```python
%pip install -q pandas numpy scipy matplotlib seaborn statsmodels
```

If Colab requests a restart, select **Runtime → Restart session**, then continue from the import cell.

## Libraries used

| Library | Purpose |
|---|---|
| `pandas` | Loading, inspecting, grouping and summarising tabular data |
| `numpy` | Numerical arrays and mathematical operations |
| `scipy` | Probability distributions and statistical tests |
| `matplotlib` | Base plotting and figure control |
| `seaborn` | Statistical visualisation |
| `statsmodels` | Statistical diagnostics and additional modelling utilities |

## Verify the environment

```python
import sys
import numpy as np
import pandas as pd
import scipy
import matplotlib
import seaborn as sns
import statsmodels

print("Python:", sys.version.split()[0])
print("NumPy:", np.__version__)
print("pandas:", pd.__version__)
print("SciPy:", scipy.__version__)
print("Matplotlib:", matplotlib.__version__)
print("Seaborn:", sns.__version__)
print("statsmodels:", statsmodels.__version__)
```

All imports should complete without an error. Exact version numbers may change as Colab updates.

## Dataset

The notebook uses the Titanic dataset:

<https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv>

The expected source shape is:

```text
891 rows × 12 columns
```

The notebook requires internet access when it downloads the dataset. If the download fails, download the CSV through a browser and upload it using the Colab Files panel.

## Local Jupyter alternative

Python 3.11 or 3.12 is recommended.

Create and activate a virtual environment:

```bash
python -m venv .venv
```

**Windows PowerShell**

```powershell
.venv\Scripts\Activate.ps1
```

**macOS or Linux**

```bash
source .venv/bin/activate
```

Install Jupyter and the Lab 1 libraries:

```bash
python -m pip install --upgrade pip
python -m pip install jupyterlab ipykernel pandas numpy scipy matplotlib seaborn statsmodels
```

Register the kernel:

```bash
python -m ipykernel install --user --name dh-lab1 --display-name "Python (DH Lab 1)"
```

Start JupyterLab:

```bash
jupyter lab
```

Select **Python (DH Lab 1)** as the notebook kernel.

## Working procedure

1. Run the installation and import cells.
2. Confirm that the Titanic dataset contains 891 rows.
3. Run cells in order because later analyses depend on earlier variables.
4. Complete each student task before running its checking cell.
5. Interpret statistical results in context rather than reporting only a p-value.
6. Save figures and written answers in the notebook.
7. Restart the runtime and run the completed notebook from top to bottom before submission.

## Common problems

### `ModuleNotFoundError`

Rerun the installation cell and restart the session if requested. In local Jupyter, confirm the active interpreter:

```python
import sys
print(sys.executable)
```

### A statistical test returns `nan`

Check for missing values, empty groups, constant variables or inappropriate data types. Do not remove missing values without documenting the rule.

### A plot does not appear

Rerun the plotting imports. In local Jupyter, add:

```python
%matplotlib inline
```
