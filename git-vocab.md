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