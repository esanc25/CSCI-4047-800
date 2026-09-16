# Data Analytics and Visualization: Course Setup

This guide takes you from a fresh laptop to a working environment for
the course. Follow the steps in order. The first time takes about 15
minutes. You only do the full setup once.

These instructions are written for Windows, since that is what most of
you are using. If you are on a Mac, see the short note at the very end.

## What you will end up with

One conda environment named "analytics" that holds every package this
course uses, connected to VS Code so your notebooks just run.

## Before you start, you need three things

1. Miniconda (installed in Step 1 below)
2. VS Code (you already have this)
3. Two VS Code extensions: Python and Jupyter (Step 2 below)

## Step 1: Install Miniconda

Miniconda gives you "conda," the tool that builds the course
environment. It is a small, clean install.

1. Go to https://docs.conda.io/en/latest/miniconda.html
2. Download the Windows 64-bit installer (the .exe file).
3. Run the installer. Accept the defaults, with these choices:
   - "Install for: Just Me (recommended)". Do not pick All Users, that
     needs admin rights and causes permission problems later.
   - On the Advanced Options screen, LEAVE UNCHECKED the box that says
     "Add Miniconda3 to my PATH environment variable." It is unchecked
     by default and shows a warning. Leave it that way. You do not need
     it, because you will use the Anaconda Prompt (Step 3).
   - Leave every other box at its default and finish.

## Step 2: Add the two VS Code extensions

1. Open VS Code.
2. Open the Extensions panel (Ctrl+Shift+X).
3. Search for "Python" (published by Microsoft) and click Install.
4. Search for "Jupyter" (published by Microsoft) and click Install.

Without these two, VS Code cannot run notebooks or see your
environment, so do not skip this.

## Step 3: Open the Anaconda Prompt

This is the single most important Windows step. Conda commands do NOT
work in the regular Command Prompt or PowerShell. You must use the
Anaconda Prompt.

1. Click the Windows Start menu.
2. Type "Anaconda Prompt".
3. Open the app called "Anaconda Prompt (Miniconda3)".

A black terminal window opens with "(base)" at the start of the line.
That "(base)" tells you conda is working. Run every command in the next
steps inside this window.

## Step 4: Move into the course folder

You need to point the terminal at the folder that contains this course.
The command is "cd" (change directory).

Easiest reliable method:

1. Open File Explorer and find your course folder.
2. Click once on the folder to select it, then hold Shift and
   right-click it, and choose "Copy as path." This copies the full
   path with quotes around it.
3. Back in the Anaconda Prompt, type "cd " (with a space after cd),
   then paste (Ctrl+V), then press Enter.

It will look something like this:

    cd "C:\Users\YourName\Documents\CSCI-4047\data-analytics-course"

The quotes matter. Course folders often sit under paths that contain
spaces, and without the quotes the command fails. "Copy as path" adds
them for you, which is why it is the safe method.

You are in the right place if you can run "dir" and see the file
environment.yml listed.

## Step 5: Build the environment

Run this once:

    conda env create -f environment.yml

Conda reads the file and installs everything into a new environment
named "analytics." This takes a few minutes. Let it finish. You only
ever do this one time.

## Step 6: Confirm it built

    conda activate analytics

The prefix at the start of your line changes from "(base)" to
"(analytics)". That means the environment exists and is active.

## Step 7: Connect it to VS Code

1. In VS Code, open any .ipynb notebook from the course folder.
2. Look at the top-right corner of the notebook for the kernel picker
   (it may say "Select Kernel").
3. Click it, choose "Python Environments," then choose "analytics."

If "analytics" does not appear in the list, close VS Code completely
and reopen it, then try again. VS Code sometimes needs a restart to
notice a brand-new environment.

## Step 8: Final check

In a notebook cell, run:

    import pandas, numpy, sklearn, seaborn, statsmodels, matplotlib
    print("Environment ready")

If it prints "Environment ready" with no error, you are done and set
for the whole semester.

## When the you update the environment

Sometimes a later module needs a new package. When you are told to
re-sync, open the Anaconda Prompt, cd into the course folder (Step 4),
and run:

    conda env update -f environment.yml --prune

## Common problems on Windows

- "'conda' is not recognized" or "conda: command not found"
  You are in the wrong terminal. Close it and open the Anaconda Prompt
  from the Start menu (Step 3). Do not use PowerShell or Command Prompt.

- "cd" says the path cannot be found
  The path probably has spaces and no quotes. Use the "Copy as path"
  method in Step 4 so the quotes are included.

- The "analytics" kernel does not show up in VS Code
  Make sure the Python and Jupyter extensions are installed (Step 2),
  then fully close and reopen VS Code.

- A package says it is missing when you run a cell
  Check the kernel picker in the top-right of the notebook. It must say
  "analytics," not "base" or a plain Python version.

## On a Mac?

The steps are the same, with two differences: download the macOS
Miniconda installer in Step 1, and in Step 3 use the regular Terminal
app instead of the Anaconda Prompt (on Mac, conda works in the normal
terminal once Miniconda is installed).
