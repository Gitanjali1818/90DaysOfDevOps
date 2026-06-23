## Day 23 – Git Branching & Working with GitHub

## Task 1: Understanding Branches
  
     1- What is a branch in Git?
        A branch is an independent line of development in Git. 
        It allows developers to work on features, bug fixes, or experiments 
        separately without affecting the main code.

     2- Why do we use branches instead of committing everything to main?
        Branches help isolate changes, prevent breaking the main codebase, 
        allow multiple developers to work simultaneously, and make feature development easier to manage.

     3- What is HEAD in Git?
        HEAD is a pointer that refers to the current branch and the latest commit you are working on.
 
     4- What happens to your files when you switch branches?
         Files that exist only in one branch appear or disappear accordingly.


## Task 2: Branching Commands — Hands-On:
   
     1- List all branches in your repo
        git branch - 

     2- Create a new branch called feature-1
        git branch feature-1

     3- Switch to feature-1
        git switch feature-1

      4- Create a new branch and switch to it in a single command — call it feature-2
          git checkout -b feature-2

       5- Try using git switch to move between branches — how is it different from git checkout?
                 git checkout                                 git switch
          1- use for branches & files                   used only for branches
          2- multifnction cammand                       single purpose

       6- Make a commit on feature-1 that does not exist on main
          1- Switch to feature-1: git switch feature-1
          2- Create a file: touch feature-1.txt
          3- stage & commit: git add feature-1
                             git commit -m "added feature-1 file"

       7- Switch back to main — verify that the commit from feature-1 is not there
           1- swicth to main: git switch main
           2- check log: git log --oneline

       8- Delete a branch you no longer need
           git branch -d feature-2


## Task 3: Push to GitHub
   
      1- Create a new repository on GitHub (do NOT initialize it with a README)
          git remote add origin (https://github.com/<username>/devops-git-practice.git)
      
          2- Verify: git remote -v   

       2- Push your main branch to GitHub   
