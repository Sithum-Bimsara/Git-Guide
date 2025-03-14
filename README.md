# 📌 Git: The Ultimate Version Control System

## 🔍 What is a Version Control System (VCS)?
A **Version Control System (VCS)** is a tool that helps developers track changes in their code over time, collaborate effectively, and revert to previous versions if needed.

### 📜 Types of Version Control Systems

1. **Centralized Version Control Systems (CVCS)**
   - A single central server holds the entire repository.
   - Developers fetch and commit changes from/to this central repository.
   - Examples:
     - **Subversion (SVN)** 🏛️
     - **Team Foundation Server (TFS)** 💼

![Image](assets/img2.png)


2. **Distributed Version Control Systems (DVCS)**
   - Each developer has a full copy of the repository on their local machine.
   - No dependency on a central server; multiple copies ensure backup and flexibility.
   - Examples:
     - **Git** 🏆
     - **Mercurial** 🚀

![Image](assets/img3.png)

## 🎯 Why is Git So Popular?
Git is widely used due to several key advantages:
- **Free & Open Source** 🆓💻
- **Super Fast** ⚡
- **Scalable** 🔍 (Works for small and large projects)
- **Branching & Merging Capabilities** 🌿🔀

## 🛠️ Different Ways to Use Git
You can interact with Git using different methods:
1. **Command Line Interface (CLI) 🖥️** - The most powerful and flexible way.
2. **Code Editors & IDEs 🏗️** - Built-in Git support in VS Code, IntelliJ, etc.
3. **Graphical User Interfaces (GUI) 🎨** - Visual tools like GitKraken, SourceTree.

### 🏆 Why is Command Line Preferred?
- **More control over Git features** 🎛️
- **GUI tools have limitations** 🚫
- **GUIs are not always available** (e.g., when working on remote servers) 🌍

## 🔍 Checking Your Git Version
To check if Git is installed on your system, run:
```sh
git --version
```

## ⚙️ Git Configuration (Settings)
Before using Git, you need to configure some settings:

### 🔹 Setting User Information
```sh
git config --global user.name "Sithum Bimsara"
git config --global user.email "sithum.22@cse.mrt.ac.lk"
```
These commands set your name and email, which will be used in your commits.

### 🔹 Setting Default Editor
If you prefer to edit Git messages in VS Code:
```sh
git config --global core.editor "code --wait"
```

### 🔹 Viewing Your Configuration
```sh
git config --global -e
```
This will open your global configuration file for editing.

![Image](assets/img1.png)


## 🔍 Levels of Git Configuration
Git settings are applied at different levels:
1. **System Level** 🏢 (Applies to all users on the machine)
2. **Global Level** 🌎 (Applies to all repositories for the current user)
3. **Local Level** 📂 (Applies only to the current repository)

## 📝 Handling Line Endings in Different Operating Systems
## 🔹 What are Line Endings?
Line endings refer to the special characters that indicate the end of a line in a text file. Different operating systems use different conventions:

- **🖥️ Windows:** Uses `\r\n` (Carriage Return + Line Feed)
- **🍎 macOS/Linux:** Uses `\n` (Line Feed only)

These differences can cause issues when sharing files across different operating systems, especially in version control systems like Git.


## 📂 Example: Line Endings Across Different Operating Systems

### **📄 Scenario 1: File Created on Windows**
If you create a file `example.txt` on Windows and write:

```
Hello, World!
This is a test file.
```

Behind the scenes, the file is stored like this (with `\r\n` at the end of each line):

```
Hello, World!\r\n
This is a test file.\r\n
```

### **📄 Scenario 2: File Opened on Linux/macOS**
When the same file is opened on a Linux/macOS system, it may be interpreted differently because Linux expects only `\n` for line endings. If the system doesn’t handle `\r\n` properly, you might see something like:

```
Hello, World!^M
This is a test file.^M
```
(`^M` represents the extra `\r` character.)

This can cause issues in scripts, compilers, or version control.

---

## ⚙️ How Git Handles Line Endings
Git automatically converts line endings based on your system and settings to prevent issues.

### **🛠️ Configuring Git to Handle Line Endings**

#### **🖥️ For Windows Users**
Run the following command to configure Git:
```sh
git config --global core.autocrlf true
```
- ✅ Git will **convert `\n` to `\r\n` when checking out** files.
- ✅ Git will **convert `\r\n` back to `\n` when committing**.

#### **🍎 For Linux/macOS Users**
Run the following command:
```sh
git config --global core.autocrlf input
```
- ✅ Git will **convert `\r\n` to `\n` when committing**, but won’t change anything on checkout.


![Image](assets/img4.png)

---

## 🎯 Conclusion
Different line endings can cause issues when switching between operating systems. Git helps by normalizing line endings based on your settings, preventing unnecessary changes in repositories. Configuring Git properly ensures a smooth workflow when working across different environments.



### 🛠️ Configuring Git to Handle Line Endings
- **For Windows:**
  ```sh
  git config --global core.autocrlf true
  ```
  This ensures `\r\n` (Windows format) is converted to `\n` (Unix format) when committing.

- **For macOS/Linux:**
  ```sh
  git config --global core.autocrlf input
  ```
  This keeps line endings unchanged in macOS/Linux but converts `\r\n` to `\n` when committing.

---
💡 Now you're ready to start using Git efficiently! 🚀
# 🚀 Git Workflow Explained

## 🔄 Understanding the Git Workflow
Git follows a structured workflow to track changes efficiently. The process involves three main areas:

1. **Working Directory** 📂 - The area where you modify files.
2. **Staging Area (Index)** 🗂️ - Where changes are added before committing.
3. **Repository** 🏛️ - Where committed changes are permanently stored.

![Image](assets/img5.png)

### 🛠️ Adding and Committing Changes
```sh
git add file1 file2
```
✅ Moves `file1` and `file2` from the working directory to the staging area.

```sh
git commit -m "Initial Commit"
```
✅ Saves the staged files into the repository.

### 🔄 Modifying a File After Committing
If you modify `file1`, the changes remain only in the **working directory**, not in the staging area or repository.
```sh
git add file1
```
✅ Moves the modified `file1` to the staging area.

```sh
git commit -m "Fixed the bug in file1"
```
✅ Saves the modified `file1` to the repository.

### 🗑️ Removing a File
If you delete `file2` from the working directory, it still exists in the staging area.
To remove it from staging:
```sh
git add file2
```
✅ Now `file2` is marked for deletion.

```sh
git commit -m "Removed file2"
```
✅ Permanently removes `file2` from the repository.

---

## 📂 Initializing a Git Repository
To start tracking a project with Git:

```sh
mkdir Moon  # Create a new directory
cd Moon  # Navigate into the directory
git init  # Initialize Git in the directory
```
✅ Output:
```
Initialized empty Git repository in C:/Users/User/Desktop/projects/GIT MOSH/Moon/.git/
```

### 🔍 Viewing Hidden Files
By default, `.git` (Git's hidden directory) is not shown.

#### On Windows:
```sh
dir  # This will not show .git
```
```sh
dir /a  # Shows .git
```

#### On macOS/Linux:
```sh
ls  # This will not show .git
```
```sh
ls -a  # Shows .git
```

### 📂 Opening the `.git` Directory
To explore Git’s internal structure:
```sh
explorer .git  # Windows
open .git  # macOS/Linux
```

---

## 📜 Example Workflow with `git status`
### 📝 Creating and Tracking Files
```sh
echo hello > file1.txt
echo hello > file2.txt
git status
```
🔴 **Output:** (Untracked files in red)
```
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        file1.txt
        file2.txt
```

### ✅ Staging Files
```sh
git add file1.txt file2.txt
git status
```
🟢 **Output:** (Files in green, ready to commit)
```
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   file1.txt
        new file:   file2.txt
```

### 🔄 Modifying a File
```sh
echo world >> file1.txt
git status
```
🔴 **Output:** (File1 modified but not staged in red)
```
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
        modified:   file1.txt
```

### 📝 Committing Changes
```sh
git commit -m "Initial Commit"
```
✅ Stores changes in the repository.

### 📌 Staging and Committing Again
```sh
git add .
git status
```
🟢 **Output:** (File1 modified and staged in green)
```
Changes to be committed:
        modified:   file1.txt
```

```sh
git commit
```
✍️ This command opens a text editor (VS Code, Vim, etc.) to enter a descriptive commit message.

![Image](assets/img5.png)

```
[master cdab869] A short description.
 1 file changed, 1 insertion(+)
```

---
🎉 **Now you understand the full Git workflow!** 🚀

# 🛠️ Git Scenarios and Command Guide

## 🎯 Skipping the Staging Area

### Command:
```bash
echo test >> file1.txt
```

This appends "test" to `file1.txt`.

### Command:
```bash
git commit -a -m "Fix the bug"
```

### Alternative Command:
```bash
git commit -am "Fix the bug"
```

### Result:
```
[master b0a24b1] Fix the bug
 1 file changed, 1 insertion(+)
```

### ✅ What's happening:
The `-a` flag automatically stages and commits all tracked files, skipping the staging area.

---

## 🗑️ Removing Files

### On Windows:
```bash
del file2.txt
```

### On Linux/macOS:
```bash
rm file2.txt
```

### Check Status:
```bash
git status
```

### Output:
```
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    file2.txt
```

### Check Files:
```bash
git ls-files
```

### Output:
```
file1.txt
file2.txt
```

### Stage the Deletion:
```bash
git add file2.txt
```

### Verify Staged Changes:
```bash
git ls-files
```
### Output:
```
file1.txt
```

### Commit the Deletion:
```bash
git commit -m "Remove file2.txt"
```

### ✅ Alternative Approach to delete in one go both working directory and staging area:
```bash
git rm file2.txt
```

### Output:
```
rm 'file2.txt'
```

### Commit:
```bash
git commit -m "Remove file2.txt"
```

### View working directory

```bash
dir
```

### Output:
```
03/14/2025  02:45 PM    <DIR>          .
03/14/2025  02:45 PM    <DIR>          ..
               0 File(s)              0 bytes
               2 Dir(s)   8,479,490,048 bytes free
```

As you can see no files in the working directory.

```bash
git status
```
### Output:

```
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    file1.txt
```
---

## 🔄 Scenario 3: Renaming Files

### On Windows:
```bash
rename file1.txt main.js
```

### On Linux/macOS:
```bash
mv file1.txt main.js
```

### Check Status:
```bash
git status
```

### Output:

```
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    file1.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        main.js
```


### Stage the Changes:
```bash
git add file1.txt main.js
```

### Check status

```bash
git status
```

### Output:

```
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    file1.txt -> main.js
```
Then git will identify this as a file renaming.


### Commit the Changes:
```bash
git commit -m "Refactor code"
```

### ✅ Alternative Approach to directly rename a file both working directory and staging area in one go:
```bash
git mv main.js file1.txt
```

### Check status

```bash
git status
```
### Output:

```
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    main.js -> file1.txt
```

---

## 🛑 Ignoring Files

### Create Directory and File:
```bash
mkdir logs
```
```bash
echo "hello" > logs/dev.log
```

### Check Status:
```bash
git status
```
### Output:

```
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        logs/

nothing added to commit but untracked files present (use "git add" to track)
```


### Add to .gitignore:
```bash
echo logs/ > .gitignore
```

![Image](assets/img6.png)

### Stage and Commit:
```bash
git add .gitignore
```
```bash
git commit -m "Add gitignore"
```

---

## 🚫 Removing an Unwanted Staged File

When we accidently add a unwanted file into staging area, we should have to remove it from staging area too, otherwise if we add that file to .gitignore that files also will be go to staging area, although that file name also included in .gitignore.

### Create a Directory and a File:
```bash
mkdir bin
```
```bash
echo "hello" > bin/app.bin
```

### Add and Commit the File:
```bash
git add .
```
```bash
git commit -m "Add bin"
```

### Add to .gitignore:
```bash
echo bin/ > .gitignore
```

```bash
git commit -m "Include bin directory to .gitignore"
```

### Append "helloworld" to app.bin

```bash
echo hellworld >> bin\app.bin()
```

### View status

```bash
git status
```

### Output:

```
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   bin/app.bin

no changes added to commit (use "git add" and/or "git commit -a")
```
**As you can see the above output our intension was not completed yet, If we want to don't add the changes we make to bin folder to staging area , git is still tracking that folder.**

### View files in staging area

```bash
git ls-files
```

### Output:

```
.gitignore
bin/app.bin
file1.txt
logs/dev.log
```

### Remove that bin directory Staging Area:
```bash
git rm --cached -r bin/
```

### View files in staging area

```bash
git ls-files
```

### Output:

```
.gitignore
file1.txt
logs/dev.log
```

### View status

```bash
git status
```


### Output:

```
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    bin/app.bin
```

### Commit the Removal:
```bash
git commit -m "Remove the bin directory that was accidentally committed"
```

---

🎉 **Now you've mastered these essential Git scenarios!**


