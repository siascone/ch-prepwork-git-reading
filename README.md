# Git and GitHub

## Git

### What is Git?

Git is a Version Control System.

So far, we've been working on small projects with small groups. If we make 
mistakes, it isn't too hard to backtrack. However, as we begin to work on larger 
projects with larger groups, revising and adding code can become a tricky 
endeavor. What if one team member accidentally overwrites important code written 
by another team member? What if two team members try to edit a section of code 
at the same time? Disaster could ensue!

Enter Version Control Systems. Version Control Systems allow us to:

- Keep a log of changes made to a project

- Revert the project back to a previous state if we mess something up

Git also provides us an easier workflow to develop as a team, such as the 
ability to separate our work from others using branches. A branch is like a 
private copy of the main project that can be changed without modifying the 
original. These branches, when complete, may be merged back into the main 
project, bringing with it the accumulation of all the little changes made on it.

### How Git Works

Two important concepts:

1. Git stores data as a series of snapshots.

    - Every time you make a commit, or store your data, Git takes a snapshot of 
    all the changes you've made and stores a reference to that snapshot. We can 
    easily look through previous commits and see what changes were made in each 
    one. This concept of a "stream of snapshots" is what makes Git different 
    from most other Version Control Systems.

2. Git performs most operations locally.

![distributed-centralized][dist-cent]

[dist-cent]: https://git-scm.com/book/en/v2/book/05-distributed-git/images/centralized_workflow.png

Git is distributed but centralized. What does that mean?

While a "main copy" of each repository (aka project) often lives in a remote
location such as Github, each project contributor also keeps a copy of the repo,
along with its version history, locally. When we want to look through past
changes or save new changes to the project, we look to our local repo - no need
to fetch data from the server every time.

Only when we want to push our changes up to the remote "master copy" or grab
other people's changes do we fetch from or push to Github.

For more details on how Git works and how it's different from other Version
Control Systems, check out [this excellent and detailed reading][git-reading].

[git-reading]: https://git-scm.com/book/en/v2/Getting-Started-Git-Basics

### The Three States of Git

So, how do we actually take advantage of Git's version control system? First,
lets learn about the three states of Git.

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

(Note: all of this happens locally. Pushing files to your remote repository is a
separate business.)

### How to Git?

Ok, so how do we actually stage and commit files? 

1. `git init`
    - When you first begin a project, use `git init` to setup the project as a 
    git repository. You should do this before you write any code.

    - First `cd` into your porject's folder then run the command `git init`

    - NOTE: whatever folder you are in when you run `git init` is the folder that 
    will become a git repository. If you happen to `git init` an unintended 
    folder you can always correct this by removing the `.git` file that was 
    was created when you ran `git init`.

    - To remove the `.git` file run the following comand in the folder that you
        no longer want to be a git repositroy.

        - `rm -rf .git`

        - be very careful when using `rm -rf` this is a command that removes 
        removes folders permantely. They don't go the the trash first, they are
        just gone. 

2. `git status`
    - After you have initialized a project as a git repository and start making
      files you can check to see which files you have modified by running 
      `git status`. 

    - `git status` will display a list of files that have been modified since 
      the last commit. If you have not commited anything yet you will see that 
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
      file will be saved in the git repoistory.
    
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
    - Use `git commit` to save any modified files that habe been staged (i.e. 
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
      want to commit at least once every 5min. You may commit more often if you 
      add quick-to-write features.

    - `git reset`
        - If you add something you don't want to add, and would like to unstage 
          all staged changes (so that the staged files return to "Changes not 
          staged for commit"), use `git reset`.

    - Check out [this post][chris-beams] by Chris Beams for notes on writting 
      good commit messages.

      [chris-beams]: http://chris.beams.io/posts/git-commit/.

## GitHub

GitHub is a web service that integrates git software behind the sceens and
allows you to remotely host porjects that are git repositories.

GitHub is also a networking site for developers where you can: 
- Have a profile 
- Publically list your project repositories
- Market yor project and share your code
- Collaborate with other developers on their code

### Local vs. Remote Repositories

- A **local** repo is a git initialized project stored on your machine 
  (i.e. locally)

- A **remote** repo is a git initialized project that has been hosted online 
  using a service like GitHub, Bitbucket, AWS CodeCommit etc.
  - In this course you will be using GitHub for remotely hosting your classwork 
    and projects.

### How to setup a GitHub repo and connect it to a local repo

1. Navigate to the **Repositories** page on your GitHub dashboard and click the 
  green `New` button.

![new-repo](https://aa-ch-lecture-assets.s3.us-west-1.amazonaws.com/git-github/new-git-repo.png)

2. Create a new repository
    - Fill out `Repository name *` with the name of your project
    - Leave the rest of the options with their default selections
    - Click the green `Create repository` button at the bottom

3. Connect a local repo to your new GitHub repository
    - After clicking `Create repository` GitHub will provide a couple options to
      connect a local repo to your new GitHub repo. 

    - In most cases you will have already started your project on your machine 
      and you should use the commands listed under **...or push an existing repository from teh command line**

    ```bash
        git remote add origin https://github.com/siascone/testest.git
        git branch -M main
        git push -u origin main
    ```

    - If you have created your GitHub repo before creating a local repo GitHub
      provides the following instructions to be run inside of a local project
      folder to setup and connect to GitHub.
    
    ```bash
        echo "# testest" >> README.md
        git init
        git add README.md
        git commit -m "first commit"
        git branch -M main
        git remote add origin https://github.com/siascone/testest.git
        git push -u origin main
    ```
### Pushing and pulling code

- `git push`
    - This is a short hand command for `git push origin <current_branch>` and it 
      will push any recent changes that you have staged and commited from your 
      local repo to your remote repo on GitHub

    - In the begining `<current_branch>` will most likely be `main`. As you 
      start making your portfolio projects you will learn more about `branch`es 
      and feature branching workflow

- `git pull`
    - This command will retreive any changes that your remote repo has and
      **pull** them down to your local repo.
    
    - Once you start pair programming you will use this command quite 
      frequently. For now you will not likely use this command unless you have 
      your repo on multiple computers and are switching back and forth between
      them. 

### Cloning and Collaboration 

#### `git clone`
If you would like to pull down a GitHub repo that you don't have on your local 
machine, navigate the the remote repo on GitHub use the following steps to clone 
the repo

1. On the `code` tab of the repo's dashboard click the green `<> Code` 
    button

![code-btn](https://aa-ch-lecture-assets.s3.us-west-1.amazonaws.com/git-github/code-btn.png)

2. On the resulting dropdown under the `Local` tab copy the `HTTPS` url

![clone-dropdown](https://aa-ch-lecture-assets.s3.us-west-1.amazonaws.com/git-github/clone-dropdown.png)

3. On your computer open up a terminal and `cd` to the location you would 
    like to store the repo you are cloning and run the command 
    `git clone <https://url_you_copied_from_github>`

4. `cd` into the newly cloned repo and start coding!

#### Collaboration

To add a collaborator to a GitHub repo:

1. Navigate to the `settings` tab of the repo's dashboard and select 
  `Collaborators` from the lefthand menu.

2. Click the green `Add people` button

3. Enter the username or email of the collaborator you would like to add and 
  click `Add <username> to this repository`
  - An email will be sent to your collaborator asking them to accept the 
    invitation.

4. Once a collaboration invitaiton has been accepted all collaborators can
  `git clone`, `git push` and `git pull`. 

### Useful Git Commands and Vocabulary

#### Local Vocabulary

- `untracked`
    - Any newly introduced file not logged in a previous commit
    - When you create a new .git directory, all files are `untracked`
- `unstaged`
    - Any files that have been previously committed but the contents of which 
      have changed in the working directory
- `staged`
    - Files added to staging area
    - Files awaiting commit
- `commit`
    - Files that have been committed to the .git directory

#### Local Commands

- `git init`
    - Creates local .git repository
- `git status`
    - Displays current changes from the last commit
- `git log`
    - Displays a list of commits
- `git add <file_name>`
    - Adds specified file from working directory to the staging area
    - The file will change from `unstaged` or `untracked` to `staged`
- `git add .`
    - Adds all files from the current directory and all child directories to the 
      staging area
- `git add -A` 
    - Adds all files in the entire working tree to the staging area
- `git commit -m <msg>`
    - Moves files in staging area to .git directory
    - Creates a commit 
    - Always include a descriptive message
        - Start with a verb
        - Use the imperative mood
        - _NO_ emoji 
        - No ending punctuation


### Remote Vocabulary

- `origin`
    - The Default remote repo name on your local machine
    - You can name this whatever you want; the convention to use `origin`
- `remote`
    - A url that points to an online git repository
    - When you run `git push` or `git pull` an HTTP request to this `remote` url 
      is made to either **push** data up or **pull** data down.

#### Remote Commands

- `git remote`
    - Lists remotes attached to your local repo (i.e origin)
- `git remote add <remote_name> <remote-url>`
    - Connects a remote repo to your local repo
- `git push <remote> <branch-name>`
    - Moves updates from the .git directory on your local repo to a remote repo
- `git push -u <remote> <branch-name>`
    - Sets the upstream branch of a `remote` so that you can push data up to a 
      specified branch on of a specified remote repo.
    - Don't worry too much about branching just yet. You'll learn more when you
      start working on your portfolio projects.
- `git clone <remote-url>`
    - Copies the specified remote repo to a local machine
    - Sets local main branch to track remote main branch
- `git pull <remote> <branch>`
    - Fetches and merges a remote branch into current working directory
