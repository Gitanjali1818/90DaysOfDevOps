## Day 22 – Introduction to Git: Your First Repository

## Task 1: Install and Configure Git:
    1- Verify Git is installed on your machine?
       git --version
    2- Set up your Git identity — name and email?
       git config --global user.name "Geet sutar"
       git config --global user.email "geetsutar18@gmail.com"
    3- Verify your configuration?
        git config --list
            OR
        git config user.name
        git config user.email

## Task 2: Create Your Git Project:
     1- Create a new folder
         mkdir devops-git-practice
         cd devops-git-practice
     2- Initialize it as a Git repository
         git init
     3- Check the status
          git status
        OUTPUT:
     4- Explore the hidden .git/
         ls -la
        OUTPUT: 
         ls .git
        OUTPUT:

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
          OUTPUT:
       3- Commit with a meaningful message
          - git commit -m "add a git commands for refer" 
       4- View your commit history
          - git log
          OUTPUT: 

## Task 5: Make More Changes and Build History:
           ##add more commands in git-commands.md
           - git diff: show the changes before staging
           - git show: display commit details
           - git restore file.txt: discards changes
           ## second update:
           - git add git-commands.md
           - git commit -m "add diff and restore commands"
           ## Third update
           - git rm file.txt: delete the file
           - git mv old.txt new.txt: move the file 
           - git add .
           - git commit -m "add file management commands"
           ## Fourth Update:
           - git branch: show the branch name
           - git checkout dev: switch the branch
           - git add .
           - git commit -m "add branch commands"
           ## View the full history in a compact format
             - git log --oneline

             OUTPUT:

## Task 6: Understand the Git Workflow:
        1- What is the difference between git add and git commit?
           -git add moves the file into staging area.
           -git commit permanently saves the staged changes in to the repo history.

        2- What does the staging area do? Why doesn't Git just commit directly?
           
             
       
          
             
             
          
        
        
        
       
       
