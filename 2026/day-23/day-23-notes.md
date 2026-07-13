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
        git  git checkout -b feature-1
        
     3- Switch to feature-1
        git switch feature-1
        ##OUTPUT: Switched to a new branch 'feature-1'

      4- Create a new branch and switch to it in a single command — call it feature-2
          git checkout -b feature-2
          ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-23$ git checkout -b feature-2
                    Switched to a new branch 'feature-2' 

       5- Try using git switch to move between branches — how is it different from git checkout?
                 git checkout                                 git switch
          1- use for branches & files                   used only for branches
          2- multifnction cammand                       single purpose

       6- Make a commit on feature-1 that does not exist on main
          1- Switch to feature-1: git switch feature-1
          2- Create a file: touch feature-1.txt
          3- stage & commit: git add feature-1
                             git commit -m "added feature-1.txt"
          ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-23$ git commit -m "added freature-1.txt"
                    [feature-1 (root-commit) a27ac34] added freature-1.txt
                    1 file changed, 2 insertions(+)
                    create mode 100644 feature-1.txt                

       7- Switch back to master — verify that the commit from feature-1 is not there
           1- swicth to master: git switch master
           2- check log: git log --oneline
           ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-23$ git log --oneline
                     a27ac34 (HEAD -> master, feature-1) added freature-1.txt
                     
       8- Delete a branch you no longer need
           git branch -d feature-2
           ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-23$ git branch -d feature-2
                     Deleted branch feature-2 (was a27ac34).


## Task 3: Push to GitHub
   
       1- Create a new repository on GitHub (do NOT initialize it with a README)
           git remote add origin (git@github.com:Gitanjali1818/devops-git-practice.git)
      
            2- Verify: git remote -v   

       2- Connect your local devops-git-practice repo to the GitHub remote

       3- Push your main branch to GitHub
          git push origin master

       4- Push feature-1 branch to GitHub
           git push origin feature-1

       5- Verify both branches are visible on GitHub
          yes

       6-  What is the difference between origin and upstream?
           Origin: It is your own github repository
           upstream: Original repository from which you forked a project. 
                     Used to keep your fork updated with the original repository.


## Task 4: Pull from GitHub

       1- After editing a file directly on GitHub:
          git pull origin main
          cat index.html

       2- What is the difference between git fetch and git pull?
          Git fetch: Downloads the changes from remote repository
                     does not merge the changes into the current branch
          Git pull: performs git fetch + git merge           
                    Downloads and immediately integrates remote changes into the current branch.


## Task 5: Clone vs Fork
       1- Clone any public repository from GitHub to your local machine
           Practical 

       2- Fork the same repository on GitHub, then clone your fork
          Practical

       3- What is the difference between clone and fork?
                          Clone                                                    fork
          1- creat a local copy of an existing repository         Creat a copy of someone else repository under your github account
          2-             github operation                                       Github feature

        4- When would you clone vs fork?
           1- Clone: -when you have a direct access to the repository
                     - Personal project OR team repository
           2- Fork:  -when contributing to someone else ope source project.
                     -when you do not have a right access of the original repository.

        5- After forking, how do you keep your fork in sync with the original repo?
           1. Add original repository as upstream:
              git remote add main git@github.com:Gitanjali1818/devops-git-practice.git
           2. Fetch updates:
              git fetch main
           3. Merge changes:
              git merge main
                OR
              git pull main  


            
        
                     




          
