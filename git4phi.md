Git for Philosophers
=

## What is Git?

When software developers work on complex programming projects, they use something called a _revision control system_. A revision control system allows them to keep track of changes in their code -- it stores a history of changes, and allows them to quickly and easily take back ("revert") changes that turn out to break things.  It also makes is easy to collaborate with others: multiple contributors can edit and add code, and the revision control system automatically integrates changes when possible, and alerts contributors to conflicts when it isn't.  Software code is just text, and revision control systems work just as well with LaTeX code, or Markdown text, as they do with Java or Haskell programs.

[_Git_](http://git-scm.com/) is such a revision control system.  It is distributed, which means that the entire history of your code lives not just on a server somewhere, but on your own computer and any other computer that uses the same shared code.  Thus, you do not have to be connected to the internet to use Git to make changes, add material, or revert to a previous version.  In order to collaborate with others, it is of course necessary to make code maintained by Git available over the internet.  There are a number of websites which provide this service, the most popular ones are [GitHub](http://gthub.com/) and [GitLab](http://gitlab.org/).  Both are free. GitHub is bigger, but GitLab is open source and allows you to have private projects without paying.

You are no doubt familiar with the history function in Word, and with automatic backup services like Dropbox.  Git is a little bit like these, and so it might be useful to compare them as we go along. You can use Git as a backup solution, but it is _not_ an automatic tool. 

## How does Git work?

A collection of files managed by Git are called a _repository_.  A repository may be a single text document, or an entire collection.  It is essentially a folder (possibly with subfolders) for which Git keeps track of changes to (some of) the files in it.

A particular state of a repository is called a _revision_.  In contrast to automatic versioning (e.g., track changes in Word, or automatic updates in Dropbox), a Git revision must be explicitly created.  If you have a file on your computer that is tracked by Git, you can make any changes you like to it, but you have to tell Git when you want your changes to "stick," i.e., to count as a new revision.  This is called _committing_.  When you commit changes in a Git repository, Git creates a new revision of your repository.  A revision may include changes only to a single file, or it may include changes to files, new files added to the repository index, files renamed, moved, or deleted. Each revision is assigned a unique 40-digit hexadecimal "hash" code (often abbreviated to a 10-digit code). When you commit changes to create a new revision, the identity of the committer (i.e., you) as well as a _commit message_ describing the changes is recorded.

One of the differences between Git and, say, Dropbox, is that any new Git revision has to be created manually by committing, while Dropbox just checks if a file has changed on your disk, and makes a new revision whenever that happens.  Another difference is that Git only tracks those files it has been asked to track, while Dropbox tracks every change in every file in the Dropbox folder.  To ask Git to track a file, you _add_ that file to the repository index.
A third difference is that Git works locally until you tell it to save or load changes from the cloud, whereas Dropbox not only records your changes automatically, it also saves those changes to the cloud, and any change in the cloud automatically is mirrored on your own computer without you having to do anything -- but also without asking you first!

To save the revisions in your Git repository over the internet, your Git repository must be linked with a version of the repository on a server somewhere (e.g., on GitHub or GitLab).  This server repository is called a _remote_.  Think of it as the cloud copy of your local Dropbox folder.  However, the remote repository is not automatically synced with your local version.  You have to tell Git to copy the changes in your local repository to the remote.  This is called _pushing_ your changes. In the other directions, to incorporate changes to the remote copy into your local repository, you _pull_ changes from the remote.  It's in this case, when the remote repository has been changed (by you, from a different computer, or by a collaborator), that Git is most useful.  If a file is changed in your Dropbox folder at the same time you're editing it on your own computer, Dropbox will make a new copy of the entire file and leave you to figure out if there are conflicting changes and what to do about them.  If you pull changes from a remote Git repository, Git will try very hard to compare your local version with the remote version of each file.  If it is possible to merge changes automatically, Git will do so.  If not -- e.g., when both you and your collaborator have changed the same sentence -- Git will alert you to a conflict that has to be reconciled manually.  In practice, you will find a version of the file with both lines marked; you delete the line you want don't want to keep, save the file, and commit the change to creat a revision that reflects both your and your collaborator's change.

## How do I use Git?

In order to use Git on your computer, you have to install the Git software.  The bare-bones "command line" Git client is available for all operating systems, but there are a fair number of graphical interfaces available as well. The best place to start is on the [Git download page](http://git-scm.com/downloads). For Windows, there is [TortoiseGit](https://code.google.com/p/tortoisegit/), which will make all the Git commands available via the Windows Explorer right-click menu.  If your repositories are or will be hosted on GtHub, you can use GitHub's own graphical tools for Windows and Mac.

Once you have Git and possibly a graphical Git tool installed, you have to set up a repository.  There are two ways to do this.  The first is using the `git init` command: in the folder/directory you want to track using Git, just say `git init`.  Most of the time, however, you want your repository to have a matching remote version on a server.  Then it will be a lot easier to first create the repository on the server and create a local copy of that repository, which will then be linked to the remote.  Creating such a local version of an existing repository is called 'cloning.'

So go to GitHub or GitLab and create a repository.  In both GitHub and GitLab, when you are logged in, there is a little '+' next to your username in the top right corner which lets you add a new repository (GitLab calls them "projects"). Once your repository/project is created, you can clone it to a repository living on your computer using the clone URL at the bottom of the right sidebar in GitHub or at the top of the projct page in GitLab.  There are HTTPS and SSH versions of those URLs.  HTTPS always works, but you will have to give your GitHub/GitLab user ID and password whenever you push or pull.  SSH can be set up to avoid that, so it's preferable, but it is a bit of a hassle to set up on Windows.  

You can of course also use Git to clone repositories not created by you.  For instance, the [Open Logic Text](https://github.com/OpenLogicProject/OpenLogic) is a logic textbook project that uses Git, and you could use the clone URL on its GitHub page to download a copy using Git.  This very document can be cloned from [its GitHub page](https://github.com/rzach/git4phi) as well.  In the same way, you can clone a repository set up by a collaborator for a document you are planning to work on together.  However, only in the latter case will you have permissions to change the repository on the server.  Instead of cloning, e.g., the Open Logic repository directly, you can first ask GitHub to make a copy of it, which you then own.  This is called a _fork_.  A fork of a repository is a snapshot of the original, which you have complete control over.  In particular, you can clone it to your own computer, and push any changes you make back to GitHub or GitLab. Both GitHub and GitLab display a "fork" button in the top right corner of the repository page which allows you to do this. 

Once you have a clone URL, you can create your local version of the repository with the command 

    git clone URL

To track your own work, you'll start with a new, empty repository and clone it.  Suppose you are 'user' on GtHub and have started a repository 'project'.  You make a local version of this repository using

    git clone https://github.com/user/project.git

and this repository will live in the directory/folder 'project' on your local drive.  You can add a new file to that folder, but to have it tracked you also have to add it explicitly to the Git index:

    git add new-file.tex

Now Git knows that new-file.tex should be tracked. To create a new revision of your 'project' repository which records all the changes to your tracked files, say 
    
    git commit -a

The switch "-a" is for "all": Git will 'stage' all changes for all tracked files in the repository.

Then to sync your local hanges to GitHub/GitLab, you say

    git push

## Collaborative Writing with Git

When you have set up a repository for your writing project (say, containing a LaTeX document plus a BibTeX file for references), you can edit the files, commit your changes to generate a new revision, and periodically push your revisions to the remote repository on GitHub or GitLab.  If you are working on the project with someone else, you can give them access to the repository as well. If they have _push access_ they can send their own revisions to the shared repository.

Git keeps track of the state of your own local repository and the remote on GitHub/GitLab.  The command

    git status

will prompt Git to tell you the status of your repository: which branch you are on (typically, this is the _master_ branch, but more about branches later), whether your local version of the repository is up to date with the remote or not, which files have chnages that are waiting to be committed, and which files are untracked.  If you have commits that you have not pushed yet, Git will report something like "Your branch is ahead of 'origin/master' by 1 commit."  The remote repository is usually called _origin_, and the remote branch that corresponds to your local _master_ branch is then called _origin/master_.  It might happen that your branch is _behind_ the remote: if your collaborator has pushed changes to the shared remote, there will be commits on the remote that you don't yet have in your local repository.  Before you can push your changes, you will have to incorporate your collaborators' changes into your own local version of your paper.

This may also happen if you have a document shared on a Dropbox folder.  If your collaborator has edited the file while you were away, you will see the changes automatically.  But if you've had your file open in an editor while your collaborator has made changes -- perhaps even with your laptop asleep! -- Dropbox will realize that there may be a conflict between your version of the document and your collaborator's.  But it won't know what to do.  Rather than overwrite one of your changes, Dropbox will make a copy of the file you're working on simultaneously, and leave you to figure out which version is more up-to-date and how to reconcile the two copies into one.

If your document is under Git control, you will have to remember to pull changes from the shared repository before you see what your co-author has done. By the same toke, you and they have to remember to push new commits to the repository, or there won't be any changes to pull.  In the crucial case where you have both made changes at the same time, however, Git will handle the discrepancies much more gracefully.

In the best case scenario, you and your coauthor have edited the same file, but you haven't edited the same _part_ of the file: say, they added a footnote to the introduction, you have cleaned up a passage in a middle section.  If they have committed their changes and pushed to the shared remote, Git won't let you push your changes.
