

# Lab 5: Getting started

**Exploratory Data Analysis with pandas, NumPy and scikit-learn**
Data Handling and Infrastructure for AI | MSc | 2-hour lab

> [!NOTE]
> **Read this first.** The lab is ten short tasks. Most of the code is already written: you fill in a few blanks, and a check cell tells you whether your number is right.
>
> If something goes wrong, do not worry: almost every problem has a simple fix, and they are all in [section 5](#5-what-to-do-when-something-goes-wrong) and [section 6](#6-quick-tips-for-each-task).

## Contents

1. [What you need](#1-what-you-need)
2. [Open the notebook in Google Colab](#2-open-the-notebook-in-google-colab)
3. [How to run the notebook](#3-how-to-run-the-notebook)
4. [How each task works](#4-how-each-task-works)
5. [What to do when something goes wrong](#5-what-to-do-when-something-goes-wrong)
6. [Quick tips for each task](#6-quick-tips-for-each-task)
7. [How to ask for help](#7-how-to-ask-for-help)
8. [Before you leave](#8-before-you-leave)
9. [Plan for the lab](#9-plan-for-the-lab)

---

## 1. What you need

- A web browser (Chrome, Edge, Firefox or Safari) and a Google account. You do not need to install anything.
- The notebook file `Lab5_EDA.ipynb` 

---

## 2. Open the notebook in Google Colab

**Quickest way (from GitHub):** click the button below.

[Open Lab 5 in Google Colab](https://colab.research.google.com/github/SETU-AIML-2026/DH-Infra-AI/blob/main/topic-03-sprint-2-weeks-4-6/unit-4-week-5-lab/notebook-1-week-5-eda/Lab5_EDA.ipynb)


**Other ways to open it:**

1. Go to [colab.research.google.com](https://colab.research.google.com) and sign in with your Google account.
2. In the window that opens, choose the **GitHub** tab and paste the repository address, **or** choose **Upload** and select `Lab5_EDA.ipynb`. (If the window does not appear: **File > Upload notebook**.)
3. Alternatively, upload the file to Google Drive, right-click it and choose **Open with > Google Colaboratory**.
4. Wait a few seconds. You should see the title **Lab 5: Exploratory Data Analysis...** and the plan table.
5. **Immediately** choose **File > Save a copy in Drive**, so that your work is saved under your own account. (Changes you make are not saved to the repository, so without your own copy your work is lost when the session ends.)

---

## 3. How to run the notebook

A notebook is made of **cells**. Text cells explain; code cells contain Python that you run.

| To do this | Do this |
|---|---|
| **Run one code cell** | Click the cell, then press the play button on its left, or press `Shift + Enter` (runs and moves on) or `Ctrl + Enter` (runs and stays). |
| **Run the cells above this one** | **Runtime > Run before**. Use this if you get an error saying something is "not defined". |
| **Edit a text cell** (written answers) | Double-click it, type, then press `Shift + Enter` to close it. |
| **Insert or delete a cell** | Hover between cells and click **+ Code**; to delete, use the bin icon at the top right of the cell. |
| **Undo** | `Ctrl + Z` (`Cmd + Z` on a Mac). |
| **Stop a cell that is running** | **Runtime > Interrupt execution**. |
| **Start again cleanly** | **Runtime > Restart session**, then run the Setup cells and the cells you need. |

The first time you run a cell, Colab connects to a computer in the cloud. This can take 10 to 20 seconds: wait for the cell to finish (the play button stops spinning).

> [!IMPORTANT]
> **Golden rule: run cells in order, from top to bottom.** Each cell uses results from the cells above it. If you skip one, later cells will say that something is "not defined".

---

## 4. How each task works

Every task has the same shape, so after Task 1 you will know what to expect.

- **A short explanation** and the lecture slide numbers where you saw the pattern.
- **A code cell with blanks.** A blank looks like `___` (three underscores). Replace each one with your answer. Until you do, you will see a red error: `NameError: name '___' is not defined`. This is expected, not a mistake.
- **A hint** (click "Hint" to open it). Try for two minutes first.
- **A check cell.** `PASS` means your number is right. `CHECK AGAIN` means re-read your blanks. A pass tells you the number is right, not that your explanation is.
- **Sometimes a short written answer** (one or two sentences, in your own words). The reasoning matters more than the code.

**Example of a blank**

Before:

```python
"Survived is 0 or 1":      ___,
```

After (the pattern is on slide 12):

```python
"Survived is 0 or 1":      set(frame["Survived"]) <= {0, 1},
```

---

## 5. What to do when something goes wrong

### Step 1: read the error from the bottom

Python errors are long, but the useful part is the **last line**. Read the last line first; it names the problem. Then look for the arrow (`---->`) that shows which line caused it.

```text
NameError                          Traceback (most recent call last)
/tmp/ipython-input-12.py in <cell line: 0>()
      3     "Survived is 0 or 1": ___,
----> 4     "Pclass is 1, 2 or 3": ___,
NameError: name '___' is not defined          <-- read this line first
```

| Error name | What it usually means |
|---|---|
| `NameError` | Python does not know that name. Either a blank (`___`) is still there, you misspelled a variable, or you did not run an earlier cell (use **Runtime > Run before**). |
| `KeyError` | A column name is misspelled. Names are case-sensitive: `"Pclass"` is not `"pclass"`. |
| `SyntaxError` | A typo in the code: a missing quote, bracket or comma. Look at the line with the arrow and the line just above it. |
| `TypeError` | The wrong kind of thing was used, for example a list where a number was expected, or a missing argument. |
| `ValueError` | The right kind of thing but a wrong value or shape, for example an array of the wrong length. |
| `AttributeError` | You used `.something` that does not exist for that object. Check the spelling: `.isna()`, `.mean()`, `.to_numpy()`. |

### Step 2: look up your problem

| What you see | Why it happens | What to do |
|---|---|---|
| `NameError: name '___' is not defined` | A blank is not filled in yet. | Replace `___` with your answer. This error is normal until you do. |
| `NameError: name 'df'` (or `'X_train'`, `'model'`, ...) `is not defined` | An earlier cell was not run, or the session restarted. | **Runtime > Run before** (on the cell with the error), then run it again. Cells with unfilled blanks above will show errors: fill them in. |
| `URLError`, `HTTPError`, or "Could not download" when loading the data | The network is blocking GitHub, or the internet dropped. | Upload `titanic.csv`: click the **folder icon** on the left, then the **upload icon**, and choose the file. Re-run the load cell (it falls back to `titanic.csv` automatically). |
| `CHECK AGAIN` | Your number is different from the expected one. | Re-read the blanks. Open the hint. Compare with the slide. Check quotes, brackets and the right data (`X_train`, not `X`). |
| Your number is slightly different from a neighbour's or the slide's | A different `random_state`, rounding, or a different split. | Use the exact values the task gives (for example `test_size=0.2`, `random_state=42`). The checks allow small rounding differences. |
| Red or pink text starting with `FutureWarning` or `UserWarning` | A warning, not an error. | Ignore it. The cell worked. |
| A cell has been running for a long time | Task 8 is the slowest. | Task 8 takes 5 to 15 seconds. If any cell runs for more than a minute, use **Runtime > Interrupt execution** and re-run it once. |
| The plot does not appear | The cell was interrupted, or has an error above the plot. | Run the cell again and read the last line of any error. |
| "Session crashed", "Runtime disconnected", or all your variables are gone | Colab disconnects after being idle, or memory ran out. | Click **Reconnect**. Then **Runtime > Restart session**, run the Setup cells, and use **Runtime > Run before** to get back to your task. |
| You deleted or broke a cell that was provided | Easy to do by accident. | Press `Ctrl + Z` straight away. Otherwise copy your blanks somewhere, re-open a fresh copy of the notebook and paste them back. |
| dtype shows `str` in one place and `object` in another | Different versions of pandas. | Ignore it. The two behave the same here. |
| A text cell shows symbols like `$$` or `\frac` | A formula that did not render. | Ignore it. It is only the formula. |
| You cannot sign in to Google | Some institutional accounts block Colab. | Use a personal Google account, or ask your lecturer for help. |

---

## 6. Quick tips for each task

| Task | Things that often trip people up |
|---|---|
| **1** | Use curly brackets `{ }` for the set of allowed values. Copy the pattern from slide 12 and only change the column and the values. |
| **2** | Use `.isna()` and then `.mean() * 100`, rounded to 1 decimal place. The two blanks in `assign()` are True/False columns (for Age and for Cabin). |
| **3** | The fence is Q3 + 1.5 x (Q3 - Q1): subtract the quartiles. For the share, divide by *all* first-class passengers (216), not by 891. |
| **4** | Use `dropna()` before sorting. The ranks start at 1, so the last ECDF value is exactly 1. |
| **5** | Cramér's V needs brackets: `np.sqrt(chi2 / (n * k))`. The method name goes in quotes: `method="wilson"`. |
| **6** | `"size"` and `"mean"` need quotes. The overall rate is total admitted divided by total applied, not the average of the department rates. |
| **7** | Give `train_test_split` the features `X` (not the whole `df`). Use the *training* numbers for the test rows. Use `np.nanmean` and `np.nanstd` with `axis=0`. |
| **8** | It takes 5 to 15 seconds. Run it once and wait. The checks only need the leaky score to be well above 0.5 and the pipeline score to be near 0.5. |
| **9** | Strategies and options need quotes: `"median"`, `"most_frequent"`, `"ignore"`. Fit on `X_train` and `y_train`; score on `X_test` and `y_test`. |
| **10** | Pass the whole `model` and the raw `X` and `y` to `cross_val_score`, not a transformed matrix. In your own finding row, include a number, an action and a limitation. |

---

## 7. How to ask for help

1. Read the last line of the error and try the table above.
2. Ask your fellow students/colleagues. Explaining where you are stuck often finds the problem.
3. Drop a text in Slack. Tell us which task you are on and show the last two or three lines of the error.

It is fine to ask. Nobody is expected to finish with every blank perfect: the goal is to understand each step.

---

## 8. Before you leave

1. Check that the cells you have done show `PASS` (or ask about the ones that do not).
2. Use **File > Save a copy in Drive** if you have not already. To keep a copy on your computer: **File > Download > Download .ipynb**.
3. That is all. **There is nothing to hand in and no homework from this lab.**

**Colab not available?** You can run the notebook on your own computer with Jupyter. Install the packages once with:

```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn statsmodels jupyter
```

then start Jupyter (`jupyter notebook`) and open the same file. Ask your lecturer if you need help.

---
