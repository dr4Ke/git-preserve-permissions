git-preserve-permissions
========================

Preserve file permissions within a git repository

Backward compatibility break
----------------------------

Starting with version 1.3, the permissions database file format changes to always include all informations: permissions, owner, group, even if not needed. That way, changing the `user`, `group` and `perms` options should always work as expected. Previous versions are **not** expected to work with this file format.

Installation
============

Copy `git-preserve-permissions` somewhere in your PATH (maybe `~/bin`).

`post-checkout`, `post-merge` and `pre-commit` hooks are provided. You can copy them in your repository directory `.git/hooks`.

Update
======

**Important:** Make sure your permissions are up to date in all your git repositories **before** doing the upgrade.

Proceed as indicated in the Installation section, then update the permissions database file for your repositories with the command ``git preserve-permissions --save``.

Configuration
=============

The following configuration options are available:

 - `preserve-permissions.file`: storage file name (defaults to `.git-preserve-permissions`)
 - `preserve-permissions.user`: true/false to save/restore uid (defaults to false)
 - `preserve-permissions.group`: true/false to save/restore gid (defaults to false)
 - `preserve-permissions.perms`: octal mask to select bits to save/restore (defaults to `0700`)
 - `preserve-permissions.autosave`: true/false to automatically save new permissions on commit (defaults to true)
 - `preserve-permissions.autosavePatch`: true/false to use `git add -p` when autosave is on (defaults to false)

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
