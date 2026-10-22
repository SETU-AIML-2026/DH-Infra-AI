# Lecture 6 notebook: run the data pipeline demo (in Google Colab or on your own computer)

**Data Handling and Infrastructure for AI | MSc | SETU**

This folder contains a Jupyter notebook, **`Lecture6_Pipeline_Demo_student.ipynb`**, that takes you through the Lecture 6 demo **step by step**. You run a real data pipeline, read its code, test it, break it on purpose, and use it on real Dublin Bikes data.

> **It costs nothing.** You run it in **Google Colab** (free, in your browser, nothing to install) or on your own computer. You do not need a Google Cloud project, credits, or a credit card. (The Google Cloud version is the lab, which comes after.)

**Time:** about 90 to 120 minutes for everything, plus about 5 minutes the first time for the setup in Colab (10 to 20 on your own computer). If you are short of time, do Parts 0 to 5 first: they use only a small sample and need no downloads.

---

## 1. What you will learn

By the end you will be able to:

* explain, in your own words, what a **data pipeline** is and what its parts do;
* read the code of a small Apache Beam pipeline and say what each piece is for;
* run **automatic tests** on a pipeline and understand why they matter;
* read a pipeline's **counters** like a test report, and explain why `rows_read = good rows + bad rows` should always be true;
* explain what a **quarantine** is, and why bad rows are kept with a reason instead of being dropped or crashing the job;
* check a pipeline's result with a **second, independent method** (a reconciliation);
* notice that a published description of a dataset can be **wrong**, and what to do about it.

## 1a. Quick start in Google Colab (recommended)

**Google Colab** is a free service from Google that runs notebooks in your browser. You need only a **Google account**. There is nothing to install: this is the quickest way to start, and it is how the labs are done.

### Open the notebook in Colab (choose one)
* **Option A: one click.** [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AbNeil/lecture6_demo/blob/main/lecture6_notebooks/Lecture6_Pipeline_Demo_student.ipynb) This opens the notebook straight from GitHub. (If it says "not found", use Option B.) Colab may warn that the notebook was not written by Google: choose **Run anyway**.
* **Option B: upload the file.** Go to <https://colab.research.google.com>, sign in, choose **File > Upload notebook**, and select `Lecture6_Pipeline_Demo_student.ipynb` (your tutor will give you the file).

### Then
1. **Run the first code cell, "Part 0a".** Click in the cell and press **Shift + Enter**. It downloads the demo code from GitHub and installs Apache Beam. It takes **about a minute**. You should see "Downloading the code from GitHub ... Done." and "Installed."
   * If Colab then asks you to **restart the runtime**, choose **Runtime > Restart session**, then run the Part 0a cell again.
2. **Run the "Part 0" cell.** You should see the folder `/content/lecture6_demo/lecture6_demo` and four version numbers.
3. **Carry on from Part 1,** one cell at a time, in order.

### Things to know about Colab
* **Colab gives you a temporary computer.** If you are idle for a long time, or close the tab, it is **reset**, and everything you created in it is **lost**, including the downloaded data. Nothing is broken: just run the cells again from **Part 0a**.
* **Save your answers.** Use **File > Save a copy in Drive**, or **File > Download > Download .ipynb**, so that your written answers are not lost.
* **Menus have different names from Jupyter:** *Runtime > Restart session* (restart), *Runtime > Run before* (run everything above this cell), *Runtime > Interrupt execution* (stop a cell that never ends).
* **No Google Cloud project, no credits and no GitHub login are needed.** The code repository is public.
* **Colab's computer is shared and not very fast.** The real-data run (Part 6) should still finish in about a minute or two.
* The sections below about a virtual environment, `jupyter lab` and terminals (section 4) are **only for people who run the notebook on their own computer**. In Colab you can ignore them.

---

## 2. What you need on your own computer (not needed in Colab)

| You need | Details |
|---|---|
| A computer | Mac, Windows or Linux. About **1 GB of free disk space** (the libraries are a few hundred MB and the real data is about 130 MB) |
| Python | **Python 3.10, 3.11 or 3.12** (the demo was tested with 3.11 and 3.12). Check yours with `python3 --version` (Mac/Linux) or `py --version` (Windows) |
| Internet | To install the libraries (a few hundred MB) and, in Part 6, to download the real data (about 130 MB) |
| A web browser | Jupyter opens in your browser |
| `git` (optional) | To download the code with one command. Without it you can download a ZIP file instead |

You do **not** need to know Apache Beam, pandas or Jupyter beforehand. The notebook explains what you need as you go.

## 3. What is in the repository

```
lecture6_demo/                     <- the repository (this name appears twice after you clone it)
├── README.md                      <- overview of everything
├── lecture6_demo/                 <- the demo code: the pipeline, its tests, and the scripts
├── lab6_student/                  <- Lab 6 (Google Cloud), later
└── lecture6_notebooks/            <- THIS FOLDER
    ├── README.md                  <- this file
    ├── requirements.txt           <- the libraries to install
    └── Lecture6_Pipeline_Demo_student.ipynb   <- the notebook
```

The notebook finds the demo code in the sibling folder `../lecture6_demo`, so **keep the folders next to each other** and open the notebook from inside `lecture6_notebooks`.

---

## 4. Alternative: set up on your own computer, step by step

**Skip this whole section if you use Colab.** Do this **once**. Take your time: most problems later come from skipping a step here.

### Step 4.1: get the code

**Option A: with git** (recommended). Open a terminal (see 4.2) and run:

```bash
git clone https://github.com/AbNeil/lecture6_demo
cd lecture6_demo
```

**Option B: without git.** Open <https://github.com/AbNeil/lecture6_demo>, click the green **Code** button, choose **Download ZIP**, and unzip it. You will get a folder; open a terminal inside it.

**Option C: from a ZIP file given by your tutor.** Unzip it. If the unzipped folder contains both `lecture6_notebooks` and `lecture6_demo`, you are ready; open a terminal in that folder.

In all cases, the folder you are in must **contain** the two folders `lecture6_demo` and `lecture6_notebooks`. Check with `ls` (Mac/Linux) or `dir` (Windows).

### Step 4.2: open a terminal
* **Mac:** press Cmd + Space, type `Terminal`, press Enter.
* **Windows:** press the Windows key, type `PowerShell`, press Enter. (If you use Anaconda, use **Anaconda Prompt** instead.)
* **Linux:** open your terminal program.

To move into a folder, type `cd` followed by the folder's path. A trick: type `cd ` (with a space), then **drag the folder from your file browser into the terminal window**, and press Enter.

### Step 4.3: create a virtual environment
A **virtual environment** is a private box for this project's Python libraries, so that they do not interfere with anything else on your computer. In the folder from step 4.1:

**Mac / Linux**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

**Windows (PowerShell)**
```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
```
*If PowerShell says "running scripts is disabled", run `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`, answer `Y`, and try again. Or use the Command Prompt (`cmd`) and run `.venv\Scripts\activate.bat`.*

When it works, your prompt starts with **`(.venv)`**. **Every time you open a new terminal, you must activate it again** (the second command).

> **Using Anaconda?** Create an environment with `conda create -n lecture6 python=3.11` and `conda activate lecture6`, then continue with step 4.4 (use `pip install` as shown).

### Step 4.4: install the libraries
```bash
cd lecture6_notebooks
pip install -r requirements.txt
```
This installs Apache Beam, pandas, pytest, matplotlib and JupyterLab. **It takes a few minutes** and prints a lot of text. That is normal. It is finished when you get your prompt back without a red `ERROR`.

### Step 4.5: start Jupyter and open the notebook
```bash
jupyter lab
```
Your browser opens (if it does not, copy the address starting `http://localhost:8888/` that appears in the terminal into your browser). In the file list on the left, **double-click `Lecture6_Pipeline_Demo_student.ipynb`**. If asked to choose a kernel, choose **Python 3 (ipykernel)**.

**Leave the terminal window open** while you work: closing it stops Jupyter. To stop Jupyter at the end, press Ctrl + C in the terminal and confirm.

**Using Visual Studio Code instead?** Open the repository folder, install the **Python** and **Jupyter** extensions, open the notebook, click **Select Kernel** (top right) and choose the one named `.venv`.

### Step 4.6: check that it works
Run the first code cell (Part 0). You should see a folder path ending in `lecture6_demo` and four version numbers. If you do, you are ready. If not, see the troubleshooting section below.

---

## 5. How to work through the notebook

* **Run a cell:** click in it and press **Shift + Enter**. Run the cells **in order**.
* **Blanks:** `___` in a code cell means "put your answer here". Until you do, you will get a red `NameError` or `SyntaxError`. That is expected.
* **Checks:** after most tasks a check cell prints **`PASS`** or **`CHECK AGAIN`**. They check numbers, not understanding, so read the explanations too.
* **Hints:** click *Hint* to open it. Try for a couple of minutes first.
* **Written answers:** double-click the cell, write one or two sentences, press Shift + Enter. Nothing is handed in.
* **If you get lost:** Kernel > Restart Kernel, then Run > **Run All Above Selected Cell**.
* **Save often:** Ctrl + S (Cmd + S on a Mac).

## 6. What each part does

| Part | What you do | What you should see |
|---|---|---|
| **0a. Colab setup** | (Colab only) Downloads the demo code from GitHub and installs Apache Beam | "Installed." |
| **0. Setup check** | Finds the demo code and checks the libraries | A folder path and four version numbers |
| **1. Read the code** | Prints each piece of the pipeline, with an explanation, and three small tasks | Three `PASS` lines |
| **2. Tests** | Runs the 5 automatic tests | `5 passed` |
| **3. Sample data** | Creates a small made-up sample (3 files, some deliberately bad rows) and looks inside | 189 lines in total, so 186 data rows |
| **4. Run the sample** | Runs the pipeline locally and reads its counters | `rows_read 186`, `good_rows 182`, `bad_rows 4` and the 4 rejection reasons |
| **5. Exercise 1** | **You** write a CSV with deliberately bad rows, predict the counters, then check | Your prediction matches the real counters |
| **6. Real data** | Downloads real Dublin Bikes data, runs the pipeline, checks it with a second method | About a million rows read, none rejected, two methods agree |
| **7. Exercise 2** | **You** investigate the real results with pandas | Six stations with no name |
| **8. Wrap-up** | Summary, clean-up and glossary | |

### The two exercises

**Exercise 1: break it on purpose (Part 5).** The pipeline has rules about what a good row is. You write a small file containing one row that breaks each rule (a negative number of bikes, an empty station id, an unreadable time, a word instead of a number), one row that is odd but allowed (more bikes than the capacity), and one for an unknown station. **Before running anything you predict** the counters (`rows_read`, `good_rows`, `bad_rows`, `over_capacity`, `unknown_station`). Then you run it and compare. *The aim: understand the rules well enough to predict what happens.* Tip: the over-capacity row is *not* rejected, and `unknown_station` counts hourly **results**, not rows.

**Exercise 2: investigate the real results (Part 7).** In Part 6 a counter called `unknown_station` shows a large number. Using pandas on the pipeline's output you find **which stations** have no name, **when** they appear, and you write down why this might have happened and what you would ask the data owner. *The aim: see that a counter that fires on real data points to a real data problem.*

### About the real data (Part 6)
* The data is published by **Dublin City Council** under the licence **CC BY 4.0** (you may use it with credit): <https://data.smartdublin.ie/dataset/dublinbikes-api>.
* You download **two monthly files** (June 2024 and February 2026) and a station list: about **130 MB** in total.
* **Slow connection or no internet in the lab?** Ask your tutor for the files. They must end up in `lecture6_demo/data/raw/` (two CSV files) and `lecture6_demo/data/ref/dublin.csv`.
* If you want to skip the real data for now, set `RUN_REAL = False` in the Part 6 cell. Everything real then skips itself.
* The numbers in the notebook (such as 1,052,292 rows) are for the files as they were when the lecture was written. If the council updates a file, your numbers may differ a little: tell your tutor, and do not worry.

---

## 7. Troubleshooting

Find your message in the left column.

| What you see | What it means and what to do |
|---|---|
| **In Colab:** `ModuleNotFoundError: No module named 'apache_beam'` | Run the **Part 0a** cell. If Colab asks to restart, do **Runtime > Restart session**, then run Part 0a and Part 0 again |
| **In Colab:** `fatal: unable to access 'https://github.com/...'` | Colab cannot reach GitHub right now. Wait a minute and run the Part 0a cell again. If it keeps failing, tell your tutor |
| **In Colab:** everything I made has disappeared | Colab reset your temporary computer (idle for a long time, or the tab was closed). Run the cells again from Part 0a. To keep your answers next time, save a copy (File > Save a copy in Drive) |
| `ModuleNotFoundError: No module named 'apache_beam'` (or `pandas`, `matplotlib`, `pytest`) **on your own computer, in the notebook** | The notebook is using a different Python from the one you installed into. In JupyterLab: **Kernel > Change Kernel** and choose the kernel with `.venv` in its name. If it is not listed: stop Jupyter (Ctrl + C), activate the environment (step 4.3), run `jupyter lab` from the `lecture6_notebooks` folder again |
| The same error **in the terminal** while installing | Your environment is not active. Look for `(.venv)` at the start of the prompt; if it is missing, activate it (step 4.3) and run the install again |
| `I cannot find bike_pipeline.py` | **In Colab:** run the Part 0a cell first. **On your own computer:** the notebook is not in the right place. It must be in `lecture6_notebooks`, next to the `lecture6_demo` folder. Check with `ls` / `dir` in the folder that contains both |
| `pip install` fails with a long red error | Check `python3 --version`: Apache Beam needs a supported Python (3.10 to 3.12 were tested). Newer versions may not work yet. On Windows, Apache Beam can be harder to install: if it fails, tell your tutor (an alternative is Windows Subsystem for Linux, or doing the work in Cloud Shell) |
| `Activate.ps1 cannot be loaded because running scripts is disabled` (Windows) | Run `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`, answer `Y`, try again. Or use `cmd` and `.venv\Scripts\activate.bat` |
| `jupyter: command not found` | The installation did not finish, or the environment is not active. Activate it and run `pip install -r requirements.txt` again |
| The browser did not open | Copy the address that starts with `http://localhost:8888/` from the terminal into your browser |
| A line starting `WARNING:root:apitools not found` | Harmless: it only says that Google's cloud libraries are not installed, and this notebook does not use them. Ignore it |
| A cell shows `[*]` (or a spinning circle in Colab) and nothing happens | It is still working. The first import of Apache Beam, and the real-data run, can take a while. If more than 5 minutes: Kernel > Interrupt Kernel |
| `NameError` or `SyntaxError` on a cell with `___` | You have not filled in the blanks yet. That is expected |
| `NameError: name 'display' is not defined` | You are running the code outside Jupyter (for example in a plain Python window). Use the notebook |
| The tests fail (Part 2) | Read the last lines of the output. If you edited `bike_pipeline.py`, restore the original from the repository |
| `CERTIFICATE_VERIFY_FAILED` during the download (common on a Mac) | Python cannot check the website's certificate. Run the download with `curl` instead: in a new code cell type `code, out = run(["bash", "get_data_local.sh"])` and run it (on your own computer you can also run `./get_data_local.sh` in a terminal; if it says "Permission denied", run `chmod +x *.sh` first), then continue the notebook |
| `HTTP Error 404` or a timeout during the download | The link may have changed or the site may be busy. Try again in a minute, or ask your tutor |
| A check says `CHECK AGAIN` | Look at your answer, and the explanation above it. If a check about the *real data* fails and you cannot see why, your files may differ from the lecture's: ask your tutor |
| Everything is slow | The real-data run reads about a million rows. A recent laptop takes under a minute; an older one takes longer. Close other programs |
| You want to start over | Kernel > Restart Kernel, then Run > Run All Above Selected Cell. To also remove the files the notebook created, use the clean-up cell in Part 8 |

## 8. Frequently asked questions

**Do I need a Google Cloud account for this?** No. Colab needs only a normal Google account, and the notebook uses no Google Cloud project and no credits. The lab uses Google Cloud later.

**Do I hand anything in?** No. The checks and your written answers are for you.

**Do I need Google Colab?** No, but it is the easiest way and how the labs are done: see section 1a. You can also run the notebook on your own computer (section 4).

**Why Apache Beam for such a small job?** A million rows could also be handled with pandas alone, and for a job this size that would be simpler. Beam is used here because the same pipeline can run on a large cloud system (Google Cloud Dataflow) for much bigger data, which is what you will do in the lab. (The reconciliation in Part 6 actually uses pandas as the second method.)

**What if my numbers are slightly different from the notebook's?** For the sample data they must match exactly. For the real data, they may differ a little if the council has updated its files.

**Is the data free to use?** Yes, under the licence CC BY 4.0, with credit to Dublin City Council.

## 9. Testing note

The notebook was run from start to end by its authors for Parts 0 to 5 (the sample data), in a Linux environment. The **Colab setup was tested by simulation**: in a clean environment with no Apache Beam and no code, the Part 0a cell downloaded the repository and installed Beam, and the whole notebook then ran. It has **not** yet been run inside the real Colab service, and the real-data steps use the same commands that were run on real data on a Mac. It has not been tested on Windows. If something unexpected happens, tell your tutor.

## 10. After this notebook

Next comes **Lab 6**, in the `lab6_student` folder of the repository: you will extend this pipeline, prove your changes with tests, and run it on **Google Cloud Dataflow**.
