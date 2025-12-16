# venv - Virtual Environments

A Python virtual environment (often referred to as a `venv`) is a self-contained directory that houses a specific Python installation and a specific set of libraries (packages) for a single project.

Think of it as creating a custom "toolbox" for each project you work on, rather than throwing every tool for every project into one giant, messy pile.

---
1. **Why do we need them? (The Problem)**

Without virtual environments, every Python library you install goes into a Global Python Environment (system-wide). This leads to a major issue known as "Dependency Hell."

The Scenario:

Project A is an old website built using Django 2.0.

Project B is a new website using Django 4.0.

If you install Django 4.0 globally, Project A breaks because it doesn't understand the new code. If you keep Django 2.0, Project B can't run. You cannot have two different versions of the same library in the global environment at the same time.

The Solution: You create a `venv` for Project A (with Django 2.0) and a separate `venv` for Project B (with Django 4.0). They never interact or conflict.

2. **How it Works (Under the Hood)**

When you create a virtual environment, Python creates a folder (usually named `.venv` or `venv`) in your project directory. This folder contains:

A copy (or symlink) of the Python binary: A dedicated `python.exe` or python executable.

A standard library: The basic Python tools.

A site-packages folder: This is where the magic happens. Any library you install while the environment is active gets saved here, not in your computer's main system folders.

Activation Scripts: Scripts that modify your shell's environment variables (specifically `PATH`) to tell your computer: "When I type `python`, look in this specific folder first."

3. **How to Use `venv` (Step-by-Step)**

Here is the standard workflow for using virtual environments in your terminal or command prompt.

*Step 1: Create the Environment*

Navigate to your project folder and run the following command. `venv` is the module name, and the second `venv` is the name of the folder you want to create (you can name it `venv`, `.venv`, `env`, etc.).

```
Bash

# Windows / macOS / Linux
python -m venv venv
```

*Step 2: Activate the Environment*

This step is crucial. It switches your context from "Global" to "Local."

```
Bash

# macOS / Linux:

source venv/bin/activate
```

```
Bash

# Windows:

.\venv\Scripts\activate
```

**Note**: Once activated, you will usually see (`venv`) appear in parenthesis at the start of your command prompt line. This indicates you are now "inside" the environment.

*Step 3: Install Packages*

Now, when you use `pip`, it installs strictly into that folder.

```
Bash

pip install requests pandas
```

*Step 4: Deactivate*

When you are done working on that project, you can leave the environment and return to the global system.

```
Bash

deactivate
```

**4. Best Practices**

Never commit the `venv` folder to GitHub: The folder can be huge (hundreds of MBs). Instead, use a `.gitignore` file to exclude it.

Use `requirements.txt`: Since you aren't uploading the actual libraries to GitHub, you need a list of what libraries are required so others can recreate your environment.

*To create the list:* 

```
Bash

pip freeze > requirements.txt
```

*To install from the list:*

```
Bash

pip install -r requirements.txt
```
---

**Summary Table**

|Feature|Global Environment|Virtual Environment (`venv`)|
|:-|:-|:-|
|Location|System folders (e.g., C:\Python39)|A folder inside your project|
|Sharing|Shared by all projects on PC|Isolated to one specific project|
|Risk|High (updates can break other apps)|Zero (changes only affect this project)|
|Uninstalling|Hard (must hunt down files)|Easy (just delete the `venv` folder)|
