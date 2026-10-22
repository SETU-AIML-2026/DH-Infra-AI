# Lecture 6 notebook: getting started (5 minutes)

**Data Handling and Infrastructure for AI | MSc**

You will run a real data pipeline in a notebook, read its code, test it, and do two exercises. It runs in **Google Colab**: free, in your browser, **nothing to install**. It costs nothing and you do **not** need a Google Cloud project or credits.

**You need:** a Google account, a web browser, and about 90 to 120 minutes (you can stop after Part 5 if you are short of time).

---

## Step 1: open the notebook in Colab (choose one)

* **Option A: a link.** Click this link:
  <https://colab.research.google.com/github/AbNeil/lecture6_demo/blob/main/lecture6_notebooks/Lecture6_Pipeline_Demo_student.ipynb>
  If Colab says the notebook was not written by Google, choose **Run anyway**.
* **Option B: upload the file.** Go to <https://colab.research.google.com>, sign in, choose **File > Upload notebook**, and pick `Lecture6_Pipeline_Demo_student.ipynb` (the file is on your course page).

## Step 2: run the first code cell ("Part 0a")

Click inside the first code cell and press **Shift + Enter**. It downloads the demo code and installs the library it needs. **It takes about a minute.**

You should see: `Downloading the code from GitHub ... Done.` and then `Installed.`

> If Colab asks you to **restart the runtime**, choose **Runtime > Restart session**, then run the Part 0a cell again.

## Step 3: run the "Part 0" cell

You should see a folder ending in `lecture6_demo` and four version numbers. If you do, everything is ready.

## Step 4: work through the notebook, top to bottom

* Run each cell with **Shift + Enter**, **in order**. Wait until the `[*]` (or spinning circle) has gone before the next cell.
* `___` (three underscores) is a **blank for you to fill in**. A red error before you fill it in is normal.
* After most tasks, a check prints **`PASS`** or **`CHECK AGAIN`**.
* Click **Hint** to open a hint. Try for two minutes first.
* In the cells headed **Your answer**, double-click, write one or two sentences, then Shift + Enter.
* Nothing is handed in.

## Step 5: save your work

Colab gives you a **temporary computer**. If you are idle for a long time or close the tab, it is **reset and everything is lost** (including the downloaded data).

* To keep your answers: **File > Save a copy in Drive**, or **File > Download > .ipynb**.
* If it is reset: just run the cells again from **Part 0a**. Nothing is broken.

---

## If something goes wrong

| What you see | What to do |
|---|---|
| `ModuleNotFoundError: No module named 'apache_beam'` | Run the **Part 0a** cell. If Colab asks to restart, do **Runtime > Restart session**, then run Part 0a and Part 0 again |
| `fatal: unable to access 'https://github.com/...'` | Wait a minute and run Part 0a again |
| `I cannot find bike_pipeline.py` | Run the **Part 0a** cell first |
| A red `NameError` on a cell with `___` | You have not filled in the blank yet: that is expected |
| `WARNING:root:apitools not found` | Harmless: ignore it |
| A cell seems to run forever | **Runtime > Interrupt execution**, then run it again |
| Everything disappeared | Colab reset your session: run from Part 0a again |

**Still stuck?** Do **Runtime > Restart session**, then run the **Part 0a** cell and the **Part 0** cell again. This fixes most problems.

## More detail

The full instructions (including running it on your own computer) are in the README for this notebook, here: <https://github.com/AbNeil/lecture6_demo/tree/main/lecture6_notebooks>

*The data is published by Dublin City Council under the licence CC BY 4.0 (<https://data.smartdublin.ie/dataset/dublinbikes-api>).*
