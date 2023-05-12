# GitHub

GitHub is a web service that integrates git software behind the scenes and
allows you to remotely host projects that are git repositories.

GitHub is also a networking site for developers where you can: 
- Have a profile 
- Publicly list your project repositories
- Market your project and share your code
- Collaborate with other developers on their code

## Local vs. Remote Repositories

- A **local** repo is a git initialized project stored on your machine 
  (i.e. locally)

- A **remote** repo is a git initialized project that has been hosted online 
  using a service like GitHub, Bitbucket, AWS CodeCommit etc.
  - In this course you will be using GitHub for remotely hosting your classwork 
    and projects.

## How to setup a GitHub repo and connect it to a local repo

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
## Pushing and pulling code

- `git push`
    - This is a shorthand command for `git push origin <current_branch>` and it 
      will push any recent changes that you have staged and commited from your 
      local repo to your remote repo on GitHub

    - In the beginning `<current_branch>` will most likely be `main`. As you 
      start making your portfolio projects you will learn more about `branch`es 
      and feature branching workflow

- `git pull`
    - This command will retrieve any changes that your remote repo has and
      **pull** them down to your local repo.
    
    - Once you start pair programming you will use this command quite 
      frequently. For now you will not likely use this command unless you have 
      your repo on multiple computers and are switching back and forth between
      them. 

## Downloading an a/A Project from GitHub to your machine

1. At the bottom of a project page on a/A Open click the `Download Project` 
  button
2. On the resulting GitHub repository click the green `Code` button
3. From the corresponding dropdown menu click the `Download ZIP` option.
4. Navigate to the directory that the zip was downloaded to 
    - This will most likely be the `Downloads` folder in your root directory
5. Unzip the project and open it in VSCode to begin working on the project.

NOTE: You can connect the downloaded project to a GitHub repo of your own by 
following the steps in the above section of 
**How to setup a GitHub repo and connect it to a local repo**


<!-- We could remove the below section for now and provide it as a resource once
the students are in person -->

## Cloning and Collaboration once you are in person.

### `git clone`
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

### Collaboration

To add a collaborator to a GitHub repo:

1. Navigate to the `settings` tab of the repo's dashboard and select 
  `Collaborators` from the left hand menu.

2. Click the green `Add people` button

3. Enter the username or email of the collaborator you would like to add and 
  click `Add <username> to this repository`
  - An email will be sent to your collaborator asking them to accept the 
    invitation.

4. Once a collaboration invitation has been accepted all collaborators can
  `git clone`, `git push` and `git pull`. 