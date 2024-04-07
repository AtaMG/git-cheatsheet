git config
==========

`git config -e [--global]`

Edit the .git/config [or ~/.gitconfig] file in your \$EDITOR.

`git config --global user.name 'Name SecondName'`

Sets your name.

`git config --global user.email 'email@email.com'`

Sets your email.

`git config core.autocrlf true`

this setting tells git to convert the newlines to the system's standard
when checking out files, and to LF newlines when committing in.

`git config --list`

Prints list of all config options.

`git config apply.whitespace nowarn`

To ignore whitespace.


git remotes
===========

`git remote add <remote> <remote_URL>`

Adds a remote repository to your git config.

`git push <repository> +<remote>:<new_remote>`

Replace a <remote> branch with <new_remote>.

`git remote add -t master -m master origin git://example.com/git.git/`

Add a remote and track its master.

`git remote show <remote>`

Show information about the remote server.

`git checkout -b <local branch> <remote>/<remote branch>`

Track a remote branch as a local branch.


git repository getting and creation
===================================

`git init`

Create a new repository in the current dir.

`git clone ssh://user@domain.com/repo.git`

Clone an existing repository to the repo dir.

`git clone ssh://user@domain.com/repo.git <my-repo>`

Clone an existing repository to the <my-repo> dir.

`git clone ssh://user@domain.com/repo.git --branch <my-branch>`
    
Clone an existing repository to the repo dir with checkout <my-branch>
    instead of the remote's HEAD.

`git clone ssh://user@domain.com/repo.git --depth 1`

Clone an existing repository to the repo dir without history, only with the last
    commit.


adding files to the git
=======================

`git add <file1> <file2> ...`

Add <file1>, <file2>, etc... to the project.

`git add <dir>`

Add <dir> to the project.

`git add .`

Add all files besides those included in .gitignore.

`git add -i`

Add modified contents in the working tree interactively to the index.

`git add -A`
    
Add, modify, and remove index entries to match the current working tree.

`git add -u`

Modify or remove index entries to match the current working tree. It adds no new files.


deleting files from the git repository
======================================

`git rm <file1> <file2> ...`

Remove <file1>, <file2>, etc... from the project.

`git rm '\$(git ls-files --deleted)'`

Remove all deleted files from the project.

`git rm --cached <file1> <file2> ...`

Only remove it from the index.

`git rm -r <dir>`

Remove <dir> from the project.


git commit
=============

`git commit <file1> <file2> ... [-m <msg>]`

Commit <file1>, <file2>, etc..., optionally using commit message <msg>.
    otherwise opening your editor to let you type a commit message.

`git commit -a`

Commit all files that have changed since your last commit.

`git commit -v`

Commit verbosely, i.e., includes the diff of the contents being committed in
    the commit message screen.


git branching
=============

`git branch`

List all local branches.

`git branch -r`

List all remote branches.

`git branch -a`
    
List all local and remote branches.

`git branch <branch>`

Create a new branch named <branch>, referencing the same point in history
    as the current branch.

`git branch --track <branch> <remote-branch>`

Create a tracking branch. Will push/pull changes to/from another
    repository.

`git branch --set-upstream <branch> <remote-branch>`

Make an existing branch track a remote branch.

`git branch -d <branch>`

Remove the local branch.

`git branch -r -d <remote-branch>`

Delete a remote tracking branch.

`git checkout <branch>`

Make the current branch - <branch>.

`git checkout -b <new> <start-point>`

Create a new branch <new> referencing <start-point>, and check it out.

`git push :<branch>`

Remove remote <branch> from the current repo.

`git branch -r -d <remote-branch>`

Delete a remote tracking branch.

git merging
===========

git merge <branch> --no-commit
    merge branch <branch> into the current branch, but do not autocommit.

git merge <branch>
    merge <branch> with current branch.

git rebase
==========

git rebase <branch>
    rebase <branch> with current branch

git rebase master <branch>
    rebase branch <branch> into the current branch

git rebase --continue
    restart the rebasing process after having resolved a merge conflict.

git rebase --abort
    alternatively, you can undo the git rebase with option --abort.


updating current repository
===========================

git fetch <remote>
    update the remote-tracking branches for <remote> (defaults to 'origin').
    Does not initiate a merge into the current branch.

git pull
    fetch changes from the server, and merge them into the current branch.

git push
    merge <branch> with current branch.

git push origin <branch>
    update the server with your commits across all branches that are common
    between your local copy and the server.


git stashing
============

git stash
    save your local modifications to a new stash.

git stash save <optional-name>
    save your local modifications to a new stash with <optional-name>.

git stash apply
    restore the changes recorded in the stash on top of the current working
    tree state.

git stash pop
    restore the changes from the most recent stash.

git stash list
    list all current stashes.

git stash drop <stash-name>
    delete the stash with <stash-name>.

git stash clear
    delete all current stashes.


getting info about git repository
=================================

git log
    show recent commits, most recent on top. Useful options:
    --color       with color
    --graph       with an ASCII-art commit graph on the left
    --decorate    with branch and tag names on appropriate commits
    --stat        with stats (files changed, insertions, and deletions)
    -p            with full diffs
    --author=foo  only by a certain author
    --after='MMM DD YYYY' ex. ('un 20 2008') only commits after a certain date
    --before='MMM DD YYYY' only commits that occur before a certain date
    --merge       only the commits involved in the current merge conflicts

git status
    show files added to the staging area, files with changes, and untracked
    files.

git status -uno
    show files added to the staging area, files with changes, but no untracked
    files.

git diff
    show a diff of the changes made since your last commit.

git diff <rev>^ <rev>
    show a diff between rev and rev's ancestor, without commit info. Similar
    to 'git show <rev>', but this also includes commit info.

git log <ref1>..<ref2>
    show commits between the <ref1> and <ref2>.

git log number
    show last number commits.

git log --oneline --decorate --all --graph
    text-based graphical representation of the commit history on the left
    hand side of the output.

git log --all --grep='Some commit text'
    search the log (across all branches) for the given commit text.

git show <rev>
    show the changeset (diff) of a commit specified by <rev>.

git show --name-only <rev>
    show only the names of the files that changed, no diff information.

git ls-files
    list all files in the index and under version control.

git ls-files -m
    list modified files in the index and under version control.

git ls-files -m -o --exclude-standard
    list modified files, untracked files, excluding files in the standard ignored lists.


git patching
============

git format-patch HEAD^
    generate the last commit as a patch that can be applied on another
    clone (or branch) using 'git am'.

git format-patch <rev>^..<rev>
    generate a patch for a single commit.

git am <patch file>
    apply the patch file generated by format-patch.

git diff --no-prefix > patchfile
    generate a patch file that can be applied using patch: patch -p0 <
    patchfile.


git debugging
=============

git blame <file>
    show who authored each line in <file>.

git blame <file> <rev>
    show who authored each line in <file> as of <rev>.

git grep -e <regexp> <my_other_branch> -- '*.erl'
    search for our regexp in erlang files from <my-another-branch>.

git grep --cached -e <regexp>
    search files registered in the index, rather than the working tree.

git log -G <regexp>
    search for commits whose changes include your regexp.
	
	
git email
=========

git send-email -1
    send last commit from the current branch.

git send-email -1 <rev>
    send commit with hash - <rev>.

git send-email configuration:
    git config --global sendemail.smtpencryption tls
    git config --global sendemail.smtpserver mail.smtp.com
    git config --global sendemail.smtpuser user@email.com
    git config --global sendemail.smtpserverport 587
    git config --global sendemail.smtppass password
    git config sendemail.to patch@lists.org


git tags
========

git tag -l
    list all tags defined in the repository.

git co <tag_name>
    checkout the code for a particular tag.

git tag -a -m 'Tagging release 1.0' v1.0
    create tag with message.

git tag -d <tag>
    remove local tag <tag>.

git push origin --tags
    push local tags to the remote server.

git push origin :refs/tags/<tag>
    remove tag <tag> from remote server.


git reseting
============

git reset HEAD <file1> <file2> ...
    remove the specified files from the next commit.


git conflicts fixing
====================

git mergetool
    work through conflicted files by opening them in your mergetool.


git reverting
=============

git revert <rev>
    reverse commit specified by <rev> and commit the result..

git checkout <file>
    re-checkout <file>, overwriting any local changes.

git checkout -- <file>
    undo last changes in unstaged <file>.

git checkout .
    recheckout all files.


fixing mistakes
===============

git reset --hard
    abandon everything since your last commit.

git reset --soft HEAD^
    undo your last commit, but keep the changes in the staging area for
    editing.

git commit --amend
    redo previous commit, including changes you've staged in the meantime.


git submodules
==============

git submodule add <remote_repository> <path/to/submodule>
    add the given repository at the given path.

git submodule update [--init]
    update the registered submodules (clone missing submodules, and checkout
    the commit specified by the super-repo).

removing submodules:
    1. Delete the relevant line from the .gitmodules file
    2. Delete the relevant section from .git/config
    3. Run git rm --cached path_to_submodule
    4. Commit and delete the now untracked submodule files

Updating git submodule
    cd <path to submodule>
    git pull
    cd <path to toplevel>
    git commit -m 'update submodule version'
    recheckout all files


archive your git repository
===========================

git archive -l
    show all available archive formats.

git archive -o <output> <branch>
    create an archive named <output> that contains the contents of <branch>.
    the output format is inferred by the extension of <output>.


clean your git repository
=========================

git clean -f -d
    deletes untracked files and directories (similar to hg purge).

git clean -f -d -x
    deletes untracked files, ignored files and directories (similar to hg purge --all).

git clean -f -X
    deletes ignored files but leaves untracked files untouched.
