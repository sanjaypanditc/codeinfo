.. _git:

GIT
============

GIT Basics
----------
``git clone user@gitpath.git``
 * git clone allow you to get all files of git in a directory having name gitpath

``git clone user@gitpath.git  newdoc``
 * git clone allow you to get all files of git in a directory having name newdoc

``git checkout master``
 * git checkout allows you to move between branches and potentially restore tree files.
 * The command git checkout master switches you to the master branch, which is always the best place to start before making changes to your repo.

``git pull origin master``
 * Get the latest updates on the master branch, 
 * A git pull is actually a combination of git fetch, which grabs all the latest  information, and git merge, which merges the two histories together. 
 * Always run git pull origin master before starting work on a repository.

``checkout -b branchname``
 * Create a new branch called “branchname” and move to it.
 * Got an idea for a new feature? Enter git checkout -b new-feature to create a new branch called “new-feature” and open it. 
 * The new branch allows you to work in parallel with your colleagues, keeping your code separate from theirs during the time you’re working on that branch.
 * When you’re ready to share your work, you can push your branch to a remote repo or merge it back into the main branch (usually master).

``git status``
 * Current status of your repository. 
 * Git offers suggestions on what to do, offering commands on how to stage or commit those files.

``git add``
 * The git add command appends a change in the working directory to the staging area. 
 * A change can be either a removal or an addition of a file or directory. This a preparatory step toward committing your changes.
 * The actual actions are already “done,” but this command officially nominates those changes to be committed.
 * You can add the —all option. Entering git add —all stages all changes in the working directory and subdirectories, including removals of directories.

.. Tip::

   git add filename1 filename2

``git commit``
 * The git commit command records changes you make to the local repository.
 * You can also use git commit to delete files, though it’s a somewhat roundabout way of doing so.
 * Git is essentially a tree of commits, where a commit is a change (an addition, deletion, or update).
 * Doing git commit will commit the changes that you have staged with git add. The commit is made on your local repository.
 * It must be pushed to remotes (repositories not on your computer) to be shared.

.. Tip::

  git commit -m "Your message"

``git push``
 * Run the git push command to push your changes to the repository. There are a variety of ways you can tweak this, as you can combine the push command with exceptions.
 * On its own, git push makes changes to the repository and all of its associations.
 * The git push `<remote> <branch>` command will push the changes on `<branch>` from your local repository to `<remote>`, which is usually the repository on a server  
   where you collaborate with your colleagues.
 * By default, the first remote is called "origin." If you’ve made changes in your new-feature branch, you’d do git push origin new-feature to send the changes (commits) of new-feature to the place where you collaborate with your colleagues.

.. Tip::

 git push origin master

 git push origin new-feature
   
``git merge --abort``
 * It will abort merging issue.

Commands
--------

``git reset --hard origin/master``
 * It Keep you local changes and replace it your files with the files uploaded at master branch.

``git config``
 * Use it to view git config settings.

.. code-block:: bash

   git checkout HEAD^
   git checkout -f master

``git merge --abort``
 * To abort the merge if conflict occur

``git reset --hard HEAD~1``
 * To remove last commit changes completely

.. code-block:: bash

  git branch -d branch_name
  git branch -D branch_name

* To delete particular branch:

.. code-block:: rst

   git checkout BRANCH-NAME -- filename
   git checkout origin/BRANCH-NAME -- filename

* To pull specific file from specific branch:

``ssh-keygen -t rsa  -C "emailid"``
 * To generate SSH key for bitbucket:

``git diff develop(FIRST-BRANCH) feature/matches-and-filter(SECOND-BRANCH)  --ajax_mymatch.php(FILE-NAME)``
 * To check the difference between made in the file of two different branch