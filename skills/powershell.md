# PowerShell

## Status

| Item              | Value       |
| ----------------- | ----------- |
| Level             | Beginner    |
| Started           | August 2026 |
| Last Updated      | August 2026 |
| Actively Learning | Yes         |

---

## Purpose

I use PowerShell as my primary command-line interface on Windows for
filesystem navigation, file management, Git workflows, running Python,
and improving development workflows.

I am gradually moving from basic interactive command-line usage toward
pipelines, scripting, and automation.

---

## Topics Learned

- Filesystem navigation
- Relative and absolute paths
- File and directory management
- File selection with wildcards
- Filtering files and directories
- Recursive directory traversal
- PowerShell aliases
- Tab completion
- Basic PowerShell pipelines
- Moving and renaming files
- Creating files and directories
- Running Python from PowerShell
- PowerShell profile
- Custom navigation functions
- Git integration
- Verifying file operations before modification

---

## Commands I Frequently Use

```powershell
pwd
dir
cd
mkdir
Get-ChildItem
New-Item
Move-Item
Rename-Item
Remove-Item
git status
git pull
git add
git commit
git push
python
```

---

## Filesystem Navigation

### Current directory

```powershell
Get-Location
```

Alias:

```powershell
pwd
```

### List directory contents

```powershell
Get-ChildItem
```

Common aliases:

```powershell
dir
ls
```

### Change directory

```powershell
Set-Location .\path
```

Common alias:

```powershell
cd .\path
```

### Relative paths

`.` represents the current directory:

```powershell
.\file.txt
```

`..` represents the parent directory:

```powershell
cd ..
```

Relative paths are always resolved from the current working directory.

---

## File Selection

### Wildcards

The `*` wildcard can be used to match multiple characters.

Example:

```powershell
Get-ChildItem ".\_inbox\*Fisher*"
```

A more specific pattern can reduce the number of matches:

```powershell
Get-ChildItem ".\_inbox\*Fisher*design*experiments*.pdf"
```

Before modifying files selected with wildcards, inspect the matches first.

```text
find → verify → modify → verify
```

### Tab completion

Partial paths and filenames can be completed with `Tab`.

Example:

```powershell
Get-ChildItem .\_inbox\Fish
```

Press `Tab` to complete or cycle through matching paths.

---

## File Management

### Create a directory

```powershell
New-Item -ItemType Directory .\new-directory
```

Common shortcut:

```powershell
mkdir .\new-directory
```

### Create a file

```powershell
New-Item .\example.md -ItemType File
```

### Move a file

```powershell
Move-Item .\source\file.pdf .\destination\
```

### Move and rename a file

`Move-Item` can move and rename a file in one operation:

```powershell
Move-Item ".\source\original_name.pdf" `
    ".\destination\new_name.pdf"
```

### Rename a file

```powershell
Rename-Item .\old_name.txt new_name.txt
```

### Remove a file

```powershell
Remove-Item .\file.txt
```

Use extra caution when combining `Remove-Item` with wildcards.

---

## Get-ChildItem

`Get-ChildItem` is one of the main commands I use for filesystem operations.

| Command | Description |
| ------- | ----------- |
| `Get-ChildItem` | List directory contents |
| `Get-ChildItem -Force` | Include hidden items |
| `Get-ChildItem -File` | Show only files |
| `Get-ChildItem -Directory` | Show only directories |
| `Get-ChildItem -Recurse` | Traverse subdirectories |
| `Get-ChildItem *.md` | Select Markdown files |
| `Get-ChildItem *keyword*` | Select items containing a keyword |

Common alias:

```powershell
dir
```

---

## Pipelines

The pipeline operator (`|`) passes objects from one PowerShell command to
another.

Example:

```powershell
Get-ChildItem ".\_inbox\*Fisher*.pdf" |
    Move-Item -Destination ".\pdf\non-fiction\mathematics\statistics\ronald_fisher_the_design_of_experiments.pdf"
```

Conceptually:

```text
Get-ChildItem
      ↓
   FileInfo
      ↓
      |
      ↓
 Move-Item
```

Unlike traditional text-oriented shells, PowerShell pipelines pass .NET
objects between commands.

I am currently learning how to use these objects and pipelines more
effectively.

---

## Git Integration

I use Git directly from PowerShell for my development repositories.

Common workflow:

```powershell
git status
git pull
git add .
git commit -m "type: description"
git push
```

I also use:

```powershell
git diff
git log
git branch
git fetch
git merge
git stash
```

---

## Python Integration

Python can be started directly from PowerShell:

```powershell
python
```

Python scripts can be executed with:

```powershell
python script.py
```

The Python interactive interpreter can be exited with:

```python
exit()
```

---

## PowerShell Profile

I use my PowerShell profile to define reusable navigation functions for
frequently used development repositories.

Examples include shortcuts for:

```text
python-crash-course-3e
developer-handbook
developer-portfolio
```

These functions reduce repetitive navigation and can also include commands
such as:

```powershell
git status
```

---

## Practical Workflow

For potentially ambiguous filesystem operations, I use:

```text
1. Find
2. Verify
3. Modify
4. Verify
```

Example:

```powershell
Get-ChildItem ".\_inbox\*Fisher*"
```

After confirming the correct match:

```powershell
Get-ChildItem ".\_inbox\*Fisher*design*experiments*.pdf" |
    Move-Item -Destination ".\pdf\non-fiction\mathematics\statistics\ronald_fisher_the_design_of_experiments.pdf"
```

Then verify:

```powershell
Get-ChildItem ".\pdf\non-fiction\mathematics\statistics\*Fisher*"
```

---

## Projects

PowerShell is currently used in:

- Python Crash Course
- Developer Handbook
- Developer Portfolio
- Local filesystem organization
- Git and GitHub workflows

---

## Currently Learning

- PowerShell pipelines
- PowerShell objects
- Command parameters
- Filesystem automation
- Scripting
- Safer file operations

---

## Future Goals

- Write reusable PowerShell scripts
- Automate repetitive filesystem tasks
- Automate development workflows
- Improve understanding of the PowerShell object pipeline
- Learn variables, loops, and conditionals in PowerShell
- Learn error handling
- Learn functions and parameters
- Learn more advanced filtering and object manipulation
- Build small practical automation scripts