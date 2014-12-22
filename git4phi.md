Git for Philosophers
=

When software developers work on complex programming projects, they use something called a /revision control system/. A revision control system allows them to keep track of changes in their code -- if functions as a history of changes, and allows them to quickly and easily take back ('revert') changes that turn out to break things.  It also makes is easy to collaborate with others: multiple contributors can edit and add code, and the revision control system automatically integrates changes when possible, and alerts contributors to conflicts when it isn't.  

When you have created a repository on github (or gitlab), you can add existing files on your computer to it. In the directory you want to add to the repository:

    git add file-name-to-add
    git commit -m "first commit"
    git remote add origin git@gitlab.com:user-name/repository-name.git
    git push -u origin master
