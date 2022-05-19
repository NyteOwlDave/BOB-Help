<link rel="stylesheet" href="./assets/help.css"/>

# Script Folder

This folder is for system admin usage.

# CV Script

In order to speed up conversion of Markdown
files to HTML, I'm using `pandoc`.

This script permits you to convert a single
file or to do a recursive folder search and
convert all files with the `.md` extension
to HTML.

For help, type this at the command line:

```bash
cv --help
```

# Working Folder for CV

The `cv` tool operates using the current working folder as a root node
for the hierarchical search. This means the `cv` script must be invoked
from the folder within which operations are to take place. Generally
this is **not** the folder where the script is stored.

If you've cloned the Git repository and want to convert files in the
`source` folder for the project, you can open a terminal to that
folder and type:

```
../script/cv
```

Since the `script` folder has the same parent as `source`, this will
get the job done.

# Pandoc Installer

The `cv` script relies on the 3rd party file conversion tool named
`pandoc`. This tool needs to be installed before `cv` can work.

Run the `cv-install` script to install `pandoc`. This assumes
a Debian/Ubuntu system.

For other systems, look up installation instructions here:

[pandoc]: <https://pandoc.org/installing.html>

* See: [pandoc][pandoc]

# Fix Permissions

When copying files to/from various media, it's possible for the
security permission settings to be lost. I'm speaking of the read/write
flags (among others).

The `fix-sec` script was written to bulk update `png` files.

As a side effect, the script creates a list of `png` file names
within a text file named `png.list`. Any prior content is
clobbered.

This script operates in the current working folder, so should be
invoked from there. The easiest way to do this is first copy
the script to the folder where it should operate, then open a
terminal for that folder and invoke the script.

---
