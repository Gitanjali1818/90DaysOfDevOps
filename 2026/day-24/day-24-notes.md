## Day 24 – Advanced Git: Merge, Rebase, Stash & Cherry Pick



## Task 1: Git Merge — Hands-On:

      1- Create a new branch feature-login from main, add a couple of commits to it
        -Make sure your in main
        -git switch main
        -git switch -c feature-login
      2- add a couple of commints in feature-login
         -vim login.txt
           (This file for devops practice.created nginx script)
         -git add login.txt
         -git commit -m "feat: nginx script is added"
         -vim login.txt
           (Nginx run successfully)
          -git add login.txt
          -git commit -m "chore: added nginx run"
          -git log --oneline

       3- Switch back to main and merge feature-login into main
          -git switch main
          -git merge feature-login

       4- Observe the merge — did Git do a fast-forward merge or a merge commit?
          OUTPUT:

       5- Now create another branch feature-signup, add commits to it — but also add a commit to main before merging
          -git checkout -c feature-signup
          -vim signup.txt
           (this is a signup page)
          -git add .
          -git commit -m "doc: update signup"
          -vim sign.txt
           (signup validation added)
          -git add .
          -git commit -m "doc: validated signup"
          
          ##Add a commit to main BEFORE merging
           -git switch main
           -vim home.txt
             (added home page)
           -git add .
           -git commit -m "doc:added new changes"
           -git log --oneline
           -git merge feature-signup
           ##OUTPUT:
        
        6- What is a fast-forward merge?
           -Main has no new changes, so Git just moves the branch pointer forward.
           -example: You create feature-login, make some commits, and main stays unchanged. 
                    When you merge, Git just moves main forward. 
        7- When does Git create a merge commit instead?
           -Both branches have changes, so Git creates a new commit to combine them.
           -Example: You create feature-signup, make some commits, and meanwhile someone adds a commit to main. 
                     When you merge, Git creates a merge commit to combine both sets of changes. 
        8- What is a merge conflict? 
           -Same code is changed differently in two branches, and Git needs your help to decide which change to keep.
           -Example: In featur-login you change welcome user in same file
                     In feature-signup you change welcome new user in same file


## Task 2: Git Rebase — Hands-On:

       1- Create a branch feature-dashboard from main, add 2-3 commits 
          -git chechkout main
          -git checkout -b feature-dashboard
          -vim dashboard.txt
           (create dashboard UI)
          -git add .
          -git commit -m "feat: added dashboard UI"
          -vim dashboard.txt
            (it is a dashboard API)
          -git add .
          -git commit -m "feat: added dashboard API"
       2- While on main, add a new commit (so main moves ahead) 
          -git checkout main
          -vim README.md
            (this is the project info)
          -git add .
          -git commit -m "docs:update the project info"
          -git checkout main
          -git rebase main
          -git log --oneline
        3- What does rebase actually do to your commits?
           -It moves your commits on top of the latest changes from another branch to keep history clean.
        4- How is the history different from a merge?
           -Merge keeps branch history and creates a merge commit, while rebase creates a straight, clean history.
        5- Why should you never rebase commits that have been pushed and shared with others?
           -Because it changes commit history and can cause conflicts for other developers.
        6- When would you use rebase vs merge?
           Rebase:
           - To keep the commit history linear and easy to read.
           - To update your branch with the latest changes from main.
           - When the commits haven't been shared with others yet.
           Merge:
           - When multiple developers are working on branches.
           - When the branch has already been pushed and shared with others.
           - When preserving branch history is important.
           ** Use rebase to keep history clean, and use merge when working with 
              shared branches and preserving branch history is important.


## Task 3: Squash Commit vs Merge Commit:

      1- Create a branch feature-profile, add 4-5 small commits (typo fix, formatting, etc.)
         - git checkout -m feature-profile
         - git commit -m "fix: typo"
         - git commit -m "style: formatting"
         - git commit -m "feat: profile image"
         - git commit -m "fix: validation"
         
              

   
