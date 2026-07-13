## Day 22 – Introduction to Git: Your First Repository

## Task 1: Install and Configure Git:
    1- Verify Git is installed on your machine?
       git --version
       OUTPUT: git version 2.53.0
    2- Set up your Git identity — name and email?
       git config --global user.name "Geet sutar"
       git config --global user.email "geetsutar18@gmail.com"
    3- Verify your configuration?
        git config --list
            OR
        git config user.name
        git config user.email
        ##OUTPUT: user.name=geet sutar
                  user.email=geetsutar@gmail.com

## Task 2: Create Your Git Project:
     1- Create a new folder
         mkdir devops-git-practice
         cd devops-git-practice
     2- Initialize it as a Git repository
         git init
     3- Check the status
          git status
        OUTPUT: On branch master
                No commits yet
                nothing to commit (create/copy files and use "git add" to track)

      4- Explore the hidden .git/
         ls -la
        OUTPUT: 
         ls .git
        OUTPUT:total 12
               drwxrwxr-x 3 ubuntu ubuntu 4096 Jul 11 11:39 .
               drwxrwxr-x 3 ubuntu ubuntu 4096 Jul 11 11:38 ..
               drwxrwxr-x 6 ubuntu ubuntu 4096 Jul 11 11:39 .git

## Task 3: Create Your Git Commands Reference:
      1- Create a file
          touch git-commands.md
      2- Add the Git commands in git-commands.md
          ## Setup & Config:
             - git --version: show installed git version
             - git config --global user.name "geet sutar": configure username
             - git config --global user.email "geetsutar18@gmail.com": configure email
          ## Basic Workflow:
             - git init: initialise the git repo
             - git add git-commands.md: add the file in stage
             - git commit -m "add a git commands for referance": saved the stage file
          ## Viewing Changes:
             - git status: show repo status
             - git log: display commit history
             - git log --oneline: show log in oneline

## Task 4: Stage and Commit:
       1- Stage your file
          - git add git-commands.md
       2- Check what's staged
          - git status
          OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-22/task-2/devops-git-practice$ git status
                  On branch master
                  No commits yet
                  Changes to be committed:
                 (use "git rm --cached <file>..." to unstage)
                 new file:   git-commands.md
                 
       3- Commit with a meaningful message
          - git commit -m "added git commands" 
          ##OUTPUT: [master (root-commit) 0fead7c] added git commands
                    1 file changed, 16 insertions(+)
                    create mode 100644 git-commands.md
       4- View your commit history
          - git log
          OUTPUT: commit 0fead7c700e6742e666320236eabd6e455a01d34 (HEAD -> master)
                  Author: geet sutar <geetsutar@gmail.com>
                  added git commands
                
    
## Task 5: Make More Changes and Build History:
           ##add more commands in git-commands.md
           - git diff: show the changes before staging
           - git show: display commit details
           - git restore git-commands.md: discards changes
           ## second update:
           - git add git-commands.md
           - git commit -m "added more commands"
           ## Third update
           - git rm git-commands.md: delete the file
           - git mv git-commands.md git-comnd.md: move the file 
           - git add .
           - git commit -m "add file management commands"
           -OUTPUT: On branch master
                    nothing to commit, working tree clean
           ## Fourth Update:
           - git branch: show the branch name
           - git checkout dev: switch the branch
           - git add .
           - git commit -m "add branch commands"
           ## View the full history in a compact format
            - git log --oneline
            ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-22/task-2/devops-git-practice$ git log --oneline
                      d793075 (HEAD -> master) added git commands file
                      6178da9 added more commands
                      0fead7c added git commands
             
## Task 6: Understand the Git Workflow:
        1- What is the difference between git add and git commit?
           -git add moves the file into staging area.
           -git commit permanently saves the staged changes in to the repo history.

        2- What does the staging area do? Why doesn't Git just commit directly?
           -The staging area allows us to select which changes should be included in the next commit.
           -Git doesn't commit directly because the staging area gives you control, flexibility, and a clean commit history.

        3- What information does git log show you?
           - git log displays-
             1- commit ID
             2-  Author name
             3- Email
             4- Date & Time
             5- Commit message

         4- What is the .git/ folder and what happens if you delete it?
            -The .git folder contains all repository metadata, objects, branches, and commit history.
            -Deleting the .git folder removes version control and commit history from the project.

         5- What is the difference between a working directory, staging area, and repository?
            - Working directory:
              current file being edited.
            -Staging area:
             temporary place where the changes are prepared for commit.
            -Repository:
             Permanand storage containing all commits and history.  
           

           
             
       
          
             
             
          
        
        
        
       
       
