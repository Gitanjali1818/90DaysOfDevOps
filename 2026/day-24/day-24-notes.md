## Day 24 – Advanced Git: Merge, Rebase, Stash & Cherry Pick



## Task 1: Git Merge — Hands-On:

      1- Create a new branch feature-login from main, add a couple of commits to it
        -Make sure your in main
        -git switch main
        -git switch -c feature-login
      2- add a couple of commints in feature-login
         -vim login.txt
           (This file for practice.created nginx script)
         -git add login.txt
         -git commit -m "feat: nginx script is added"
         -vim login.txt
           (Nginx run successfully)
          -git add login.txt
          -git commit -m "chore: added nginx run"
          -git log --oneline
          ## OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-24$ git log --oneline
                     5774157 (HEAD -> feature-login) chore:added nginx run file
                     d90541b feat: added nginx script
                     32d53d2 (master) fet: added first page

       3- Switch back to main and merge feature-login into main
          -git switch master
          -git merge feature-login
          ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-24$ git merge feature-login
                    Updating 32d53d2..5774157
                    Fast-forward
                    login.txt | 2 ++
                    1 file changed, 2 insertions(+)
                    create mode 100644 login.txt
       4- Observe the merge — did Git do a fast-forward merge or a merge commit?
           -yes
          ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-24$ git merge feature-login
                    Updating 32d53d2..5774157
                    Fast-forward
                    login.txt | 2 ++
                    1 file changed, 2 insertions(+)
                    create mode 100644 login.txt

       5- Now create another branch feature-signup, add commits to it — but also add a commit to main before merging
          -git checkout -b feature-signup
          -vim signup.txt
           (this is a signup page)
          -git add .
          -git commit -m "doc: update signup"
          -vim sign.txt
           (signup validation added)
          -git add .
          -git commit -m "doc: validated signup"
          
          ##Add a commit to main BEFORE merging
           -git switch master
           -vim home.txt
             (added home page)
           -git add .
           -git commit -m "doc:added new changes"
           -git log --oneline
           ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-24$ git log --oneline
                     725ea2d (HEAD -> master) doc: added new changes
                     5774157 (feature-login) chore:added nginx run file
                     d90541b feat: added nginx script
                     32d53d2 fet: added first page
           -git merge feature-signup
           ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-24$ git log --oneline
                     2b34c17 (HEAD -> master) Merge branch 'feature-signup'
                     725ea2d doc: added new changes
                     b76d68c (feature-signup) doc: validated signup
                     77427fc doc:update signup
                     5774157 (feature-login) chore:added nginx run file
                     d90541b feat: added nginx script
                     32d53d2 fet: added first page
        
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

       1- Create a branch feature-dashboard from master, add 2-3 commits 
          -git checkout master
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
          -git checkout master
          -vim README.md
            (this is the project info)
          -git add .
          -git commit -m "docs:update the project info"
          -git log --oneline
          ##output: ubuntu@ip-172-31-44-56:~/2026/day-24$ git log --oneline
                    6d74fbf (HEAD -> master) docs: update the project info
                    eb3105b doc: added new changes
                    b76d68c (feature-signup) doc: validated signup
                    77427fc doc:update signup
                    5774157 (feature-login) chore:added nginx run file
                    d90541b feat: added nginx script
                    32d53d2 fet: added first page
          -git switch feature-signup
          -git log --oneline
           ## OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-24$ git log --oneline
                      b76d68c (HEAD -> feature-signup) doc: validated signup
                      77427fc doc:update signup
                      5774157 (feature-login) chore:added nginx run file
                      d90541b feat: added nginx script
                      32d53d2 fet: added first page
          -git rebase feature-dashboard
          -git log --oneline
          ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-24$ git log --oneline
                    10c644c (HEAD -> feature-signup, feature-dashboard) feat: added dashboard API
                    893a10f feat: added dashboard UI
                    2b34c17 Merge branch 'feature-signup'
                    725ea2d doc: added new changes
                    b76d68c doc: validated signup
                    77427fc doc:update signup
                    5774157 (feature-login) chore:added nginx run file
                    d90541b feat: added nginx script
                    32d53d2 fet: added first page
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
      2- Merge it into master using --squash — what happens?
         - git switch master
         - git merge --squash feature-profile
         - git commit -m "feat: add profile feature"
         ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-24$ git log --oneline
                   6d74fbf (HEAD -> master) docs: update the project info
                   eb3105b doc: added new changes
                   b76d68c doc: validated signup
                   77427fc doc:update signup
                   5774157 (feature-login) chore:added nginx run file
                   d90541b feat: added nginx script
                   32d53d2 fet: added first page
                   
       3- Check git log — how many commits were added to master?
         - git log --oneline
         ##OUTPUT: only one commit is added
       4- Now create another branch feature-settings, add a few commits
          - git checkout -b feature-setting
       5- Merge it into master without --squash (regular merge) — compare the history
          - git checkout master
          - git merge feature-setting
          ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-24$ git log --oneline
                    5b41ad0 (HEAD -> master, feature_setting) style: backround
                    35f80a4 fix: dashborad
                    578bf10 feat: setting
                    6d74fbf docs: update the project info
                    eb3105b doc: added new changes
                    b76d68c doc: validated signup
                    77427fc doc:update signup
       6- What does squash merging do?
          - Combines multiple commits into one before merging.
       7- When would you use squash merge vs regular merge?
         - Squash merge: small commits, typo, cleanup commit, cleaner history
         - regural merge: When preserving commit history matters.
       8- What is the trade-off of squashing?
         - Individual commit history is lost.

## Task 4: Git Stash — Hands-On:
       1- Start making changes to a file but do not commit
       2- Now imagine you need to urgently switch to another branch — try switching. What happens?   
          - git checkout feature-dashborad
          (Sometimes Git blocks switching due to uncommitted changes.)
       3- Use git stash to save your work-in-progress   
          - git stash (Save work)
       4- Switch to another branch, do some work, switch back
          - git checkout feature-login(switch branch)
          - git checkout master (return into master)
       5- Apply your stashed changes using git stash pop
          - git stash pop
       6- Try stashing multiple times and list all stashes
          - git stash push -m "work-1"  
          - git stash list
          ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-24$ git stash list
                    stash@{0}: On feature-dashboard: work-1
                    stash@{1}: WIP on feature-dashboard: 1c4e9d6 style: switch add
       7- Try applying a specific stash from the list
          - git stash apply @{1}
       8- What is the difference between git stash pop and git stash apply?
          - git stash apply: applies stash and keeps it
          - git stash pop: applies stash and removed it
       9- When would you use stash in a real-world workflow?
          - When you're working on one feature and suddenly need to 
            fix an urgent bug without committing unfinished work.

## Task 5: Cherry Picking:
       1- Create a branch feature-hotfix, make 3 commits with different changes
          - git checkout feature-hotfix
          - git commit -m "fix: issue 1"
          - git commit -m "fix: payment bug"
          - git commit -m "fix: issue 3"
          - git log --oneline
       2- Switch to master
          - git switch master
       3- Cherry-pick only the second commit from feature-hotfix onto main
          - git cherry-pick second commit id
          ##OUTPUT: ubuntu@ip-172-31-44-56:~/2026/day-24$ git log --oneline --graph --all
                    * 98035b7 (master) fix: dashborad
       4- Verify with git log that only that one commit was applied
          - git log --oneline --graph --all
       5- What does cherry-pick do?
          - copies the specific commit from another branch and applies to the current branch.
       6- When would you use cherry-pick in a real project?
          - applying a hotfix to a production
          - taking only one useful commit from another branch
          - avoiding merging an entire branch
        7- What can go wrong with cherry-picking?
           - merged conflicts- I faced this issue after using cherry-pick
           - duplicate commits
           - confusing history if overused

## Commands to add to git-commands.md:
        - git merge
        - git merge --squash
        - git rebase main
        - git log --oneline 
        - git stash
        - git stash pop
        - git stash apply
        - git stash list
        - git stash push -m "message"
        - git cherry-pick <commit-hash>
           
          
