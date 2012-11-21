git-preserve-permissions
========================

Preserve file permissions within a git repository

Installation
============

Create a `commands` directory in your `.git` directory and copy the `git-preserve-permissions-*` files in it.

`post-checkout` and `pre-commit` hooks are provided. You can copy them in your repository directory `.git/hooks`.

The file `git-aliases` contains aliases for these git commands. Include them in your git configuration file (`.git/config`)

Usage
=====

Save your permissions
---------------------
Use git preserve-permissions-save to save permissions in a file named `.permissions.save`.

Commit this file to the current branch. It will be useful upon branch checkouts.

Do it for each branch where you need to save permissions.

Check your permissions
----------------------
Use git preserve-permissions-check to check whether permissions have change. This is done each time you do a commit, by the pre-commit hook.

Restore your permissions
------------------------
Use git preserve-permissions-restore to restore previous permissions. This is done each time you do a checkout, by the post-checkout hook.

License
=======

This project is published under GPLv3+

Reports
=======

Any bug, suggestion, report is welcome.
