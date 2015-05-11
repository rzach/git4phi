Git for Philosophers
=

## What is Git?

When software developers work on complex programming projects, they use something called a /revision control system/. A revision control system allows them to keep track of changes in their code -- it stores a history of changes, and allows them to quickly and easily take back ('revert') changes that turn out to break things.  It also makes is easy to collaborate with others: multiple contributors can edit and add code, and the revision control system automatically integrates changes when possible, and alerts contributors to conflicts when it isn't.  Software code is just text, and revision control systems work just as well with LaTeX code, or Markdown text, as they do with Java or Haskell programs.

'Git' is such a revision control system.  It is distributed, which means that the entire history of your code lives not just on a server somewhere, but on your own computer.  Thus, you do not have to be connected to the internet to use Git to make changes, add material, or revert to a previous version.  In order to collaborate with others, it is of course necessary to make code maintained by Git available.  There are a number of websites which provide this service, the most popular ones are [GitHub](http://gthub.com/) and [GitLab](http://gitlab.org/).  Both are free. GitHub is bigger, but GitLab is open source and allows you to have private projects without paying.

You are no doubt familiar with the history function in Word, and with automatic backup services like Dropbox.  Git is a little bit like these, and so it might be useful to compare them as we go along. You can use it as a backup solution, but Git is not an automatic tool. 

## How does Git work?

A collection of files managed by Git are called a 'repository'.  A repository may be a single text document, or an entire collection.  It is essentially a folder (possibly with subfolders) for which Git keeps track of changes to (some of) the files in it.

A particular state of a repository is called a 'revision.'  In contrast to automatic versioning (e.g., track changes in Word, or automatic updates in Dropbox), a Git revision must be explicitly created.  If you have a file on your computer that is tracked by Git, you can make any changes you like to it, but you have to tell Git when you want your changes to "stick," i.e., to count as a new revision.  This is called 'committing.'  When you commit changes in a Git repository, Git creates a new revision of your repository.  A revision may include changes only to a single file, or it may include changes to files, new files added to the repository index, files renamed, moved, or deleted. Each revision is assigned a unique 40-digit hexadecimal "hash" code (often abbreviated to a 10-digit code). When you commit changes to create a new revision, the identity of the committer (i.e., you) as well as a 'commit message' describing the changes is recorded.

One of the differences between Git and, say, Dropbox, is that any new Git revision has to be created manually by committing, while Dropbox just checks if a file has changed on your disk, and makes a new revision whenever that happens.  Another difference is that Git only tracks those files it has been asked to track, while Dropbox tracks every change in every file in the Dropbox folder.  To ask Git to track a file, you 'add' that file to the repository index.
A third difference is that Git works locally until you tell it to save or load changes from the cloud, whereas Dropbox not only records your changes automatically, it also saves those changes to the cloud, and any change in the cloud automatically is mirrored on your own computer without you having to d oanything -- but also without asking you first.

To save the revisions in your Git repository over the internet, your Git repository must be linked with a version of the repository on a server somewhere (e.g., on GitHub or GitLab).  This server repository is called a 'remote'.  Think of it as the cloud copy of your local Dropbox folder.  However, the remote repository is not automatically synced with your local version.  You have to tell Git to copy the changes in your local repository to the remote.  This is called 'pushing' your changes. In the other directions, to incorporate changes to the remote copy into your local repository, you 'pull' changes from the remote.  It's in this case, when the remote repository has been changed (by you, from a different computer, or by a collaborator), that Git is most useful.  If a file is changed in your Dropbox folder at the same time you're editing it on your own computer, Dropbox will make a new copy of the entire file and leave you to figure out if there are conflicting changes and what to do about them.  If you pull changes from a remote Git repository, Git will try very hard to compare your local version with the remote version of each file.  If it is possible to merge changes automatically, Git will do so.  If not -- e.g., when both you and your collaborator have changed the same sentence -- Git will alert you to a conflict that has to be reconciled manually.  In practice, you will find a version of the file with both lines marked; you delete the line you want don't want to keep, save the file, and commit the change to creat a revision that reflects both your and your collaborator's change.

For instance, the [Open Logic Text](https://github.com/OpenLogicProject/OpenLogic) and the [Homotopy Type Theory book](https://github.com/HoTT/HoTT) are two book-size projects that use Git.  The Carnap Edition project also does, but the repository is not public.  


When you have created a repository on github (or gitlab), you can add existing files on your computer to it. In the directory you want to add to the repository:

    git add file-name-to-add
    git commit -m "first commit"
    git remote add origin git@gitlab.com:user-name/repository-name.git
    git push -u origin master
