# Git

## What is Git?

Git is a Version Control System.

So far, you've been working on small projects with sa handful of files. If you
make mistakes, it isn't too hard to backtrack. However, as you begin to work on 
larger projects with larger groups, revising and adding code can become a tricky 
endeavor. What if one team member accidentally overwrites important code written 
by another team member? What if two team members try to edit a section of code 
at the same time? Disaster could ensue!

Enter Version Control Systems. Version Control Systems allow you to:

- Keep a log of changes made to a project

- Revert the project back to a previous state if something gets broken

Git also provides an easier workflow to develop as a team, such as the 
ability to separate one developer's work from another using branches. A branch 
is like a private copy of the main project that can be changed without modifying 
the original. These branches, when complete, may be merged back into the main 
project, bringing with it the accumulation of all the little changes.

## How Git Works

Two important concepts:

1. Git stores data as a series of snapshots.

    - Every time you make a commit, or store your data, Git takes a snapshot of 
    all the changes you've made and stores a reference to that snapshot. You can 
    easily look through previous commits and see what changes were made in each 
    one. This concept of a "stream of snapshots" is what makes Git different 
    from most other Version Control Systems.

2. Git performs most operations locally.

![distributed-centralized][dist-cent]

[dist-cent]: https://git-scm.com/book/en/v2/book/05-distributed-git/images/centralized_workflow.png

Git is distributed but centralized. What does that mean?

While a "main copy" of each repository (aka project) often lives in a remote
location such as Github, each project contributor also keeps a copy of the repo,
along with its version history, locally. When you want to look through past
changes or save new changes to the project, you look to your local repo - no 
need to fetch data from the server every time.

Only when you want to push your changes up to the remote "main copy" or grab
other people's changes do you fetch from or push to Github.

For more details on how Git works and how it's different from other Version
Control Systems, check out [this excellent and detailed reading][git-reading].

[git-reading]: https://git-scm.com/book/en/v2/Getting-Started-Git-Basics

## The Three States of Git

So, how do you actually take advantage of Git's version control system? First,
you'll need to learn about the three states of Git.

![git-stages][git-stages]

[git-stages]: https://git-scm.com/book/en/v2/book/01-introduction/images/areas.png

Files can live in three different states: modified, staged, and committed. A
typical Git workflow goes like this:

1. You make changes in your working directory. Your files are now **modified**.

2. You decide which files you want to add to your next commit and add them to
   the staging area. Your files are now **staged**. Don't want a change to be
   committed? Simple - don't stage that file.

3. You commit all of the files in your staging area and create a snapshot which
   permanently lives in your local Git directory. Your files are now
   **committed**.

Note: all of this happens locally. Pushing files to your remote repository is a
separate business.

## How to Git?

Ok, so how do you actually stage and commit files? 

1. `git init`
    - When you first begin a project, use `git init` to setup the project as a 
      git repository. You should do this before you write any code.

    - First `cd` into your project's folder then run the command `git init`

<!-- Removed the rm -rf .git command. recomended reaching out to a/A support -->
<!-- will there be a general slack/HIR support for students in prep work? -->
    - NOTE: whatever folder you are in when you run `git init` is the folder 
      that will become a git repository. BE CAREFUL to only run `git init` in 
      the folder you want to make a git repository. If you happen to `git init` 
      an unintended folder reach out to the a/A community via slack.

2. `git status`
    - After you have initialized a project as a git repository and start making
      files you can check to see which files you have modified by running 
      `git status`. 

    - `git status` will display a list of files that have been modified since 
      the last commit. If you have not committed anything yet you will see that 
      all of the files you have created are listed.

    ```bash
        ~/aa/ruby-curriculum$ git status
        # On branch master
        # Changes not staged for commit:
        #   (use "git add <file>..." to update what will be committed)
        #   (use "git checkout -- <file>..." to discard changes in working directory)
        #
        #       modified:   README.md
        #       modified:   git.md
        #
        # Untracked files:
        #   (use "git add <file>..." to include in what will be committed)
        #
        #       git-summary.md
        no changes added to commit (use "git add" and/or "git commit -a")
    ```

    - NOTE: git will not track any empty folders. 

3. `git add`
    - Use `git add` to add files you have modified to the git staging area.

    - When you `git add` a file, the next time you commit, this version of the 
      file will be saved in the git repository.
    
    - NOTE: `git add` only adds the changes you have made thus far. This means 
      that when you add a file's changes to staging, if you then make more 
      changes to it and commit without re-`git add`ing, those recent changes 
      will not be committed.

    ```bash
        ~/aa/ruby-curriculum$ git status
        # On branch master
        # Changes not staged for commit:
        #   (use "git add <file>..." to update what will be committed)
        #   (use "git checkout -- <file>..." to discard changes in working directory)
        #
        #       modified:   README.md
        #       modified:   git.md
        #
        # Untracked files:
        #   (use "git add <file>..." to include in what will be committed)
        #
        #       git-summary.md
        no changes added to commit (use "git add" and/or "git commit -a")
        ~/aa/ruby-curriculum$ git add git.md
        ~/aa/ruby-curriculum$ git status
        # On branch master
        # Changes to be committed:
        #   (use "git reset HEAD <file>..." to unstage)
        #
        #       modified:   git.md
        #
        # Changes not staged for commit:
        #   (use "git add <file>..." to update what will be committed)
        #   (use "git checkout -- <file>..." to discard changes in working directory)
        #
        #       modified:   README.md
        #
        # Untracked files:
        #   (use "git add <file>..." to include in what will be committed)
        #
        #       git-summary.md
    ```   

4. `git commit`
    - Use `git commit` to save any modified files that have been staged (i.e. 
      `git add`ed) into the git history. 

    - A commit is a checkpoint that you can return to later if your code gets
      too buggy.

    - Commit frequently. As you add small bits of functionality, write 
      fine-grained commits. Do not wait until you've written half your program 
      to commit.

    - Every time you are about to make a major change to your program, you may 
      want to commit what you have. That way, if you mess up, you can easily 
      undo any major mistakes.

    - You will be hard-pressed to over-commit when starting out. You probably 
      want to commit at least once every 5 minutes. You may commit more often if 
      you add quick-to-write features.

    - `git reset`
        - If you add something you don't want to add, and would like to unstage 
          all staged changes (so that the staged files return to "Changes not 
          staged for commit"), use `git reset`.

    - Check out [this post][chris-beams] by Chris Beams for notes on writing 
      good commit messages.

      [chris-beams]: http://chris.beams.io/posts/git-commit/.
