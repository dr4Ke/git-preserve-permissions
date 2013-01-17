git-preserve-permissions
========================

Preserve file permissions within a git repository

Installation
============

Copy `git-preserve-permissions` somewhere in your PATH (maybe `~/bin`).

`post-checkout` and `pre-commit` hooks are provided. You can copy them in your repository directory `.git/hooks`.

Configuration
=============

The following configuration options are available:

 - `preserve-permissions.file`: storage file name (defaults to `.git-preserve-permissions`)
 - `preserve-permissions.user`: true/false to save/restore uid (defaults to false)
 - `preserve-permissions.group`: true/false to save/restore gid (defaults to false)
 - `preserve-permissions.perms`: octal mask to select bits to save/restore (defaults to `0700`)
 - `preserve-permissions.autosave`: true/false to automatically save new permissions on commit (defaults to false)
 - `preserve-permissions.autosavePatch`: true/false to use `git add -p` when autosave is on (defaults to true)

Use the following command to set them:

    git config <option> <value>

Use the following command to unset them:

    git config --unset <option>

Usage
=====

Save your permissions
---------------------
Use `git preserve-permissions --save` to save permissions in a file named `.git-preserve-permissions`.

Commit this file to the current branch. It will be useful upon branch checkouts.

Do it for each branch where you need to save permissions.

Check your permissions
----------------------
Use `git preserve-permissions --check` to check whether permissions have change. This is done each time you do a commit, by the pre-commit hook.

Restore your permissions
------------------------
Use `git preserve-permissions --restore` to restore previous permissions. This is done each time you do a checkout, by the post-checkout hook.

License
=======

This project is published under GPLv3+

Reports
=======

Any bug, suggestion, report is welcome.
