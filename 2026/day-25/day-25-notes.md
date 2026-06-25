## Day 25 – Git Reset vs Revert & Branching Strategies

## Task 1: Git Reset — Hands-On:

      1- Make 3 commits in your practice repo (commit A, B, C)
         - vim file.txt
            (commit A)
         - git add .
         - git commit -m "A"
         - git commit -m "B"
         - git commit -m "C"
      2- Use git reset --soft to go back one commit — what happens to the changes?
         - git reset --soft - Commit C disappears from history.
      3- Re-commit, then use git reset --mixed to go back one commit — what happens now?
         - git commit -m "add c again"
         - git reset --mixed - commit removed again
      4- Re-commit, then use git reset --hard to go back one commit — what happens this time?
         - git commit -m "add c for reset"
         - git reset --hard - delete all data and tree is clean (c- completly gone)
      5- What is the difference between --soft, --mixed, and --hard?
         - --soft: removed the commits but keep changes staged.
         - --mixed: removed the commits and unstaged changes.
         - --hard: removed the commits and delete all changes.
      6- Which one is destructive and why?
         - git reset --hard is distructive because its permantly removes changes from 
           both the staging area and working directory.
      7- When would you use each one?
         - --soft: 1- to rewrite commit message
                   2- to squash multipla commit into one
         - --mixed:1- to modify file before recommiting
                   2- most commonly used reset mode
         - --hard: 1- to discard unwanted local work completely
                   2- to return the repository to a clean state
      8- Should you ever use git reset on commits that are already pushed?
         - Generally NO. - git reset rewrites commit history
         - If other developers have pulled those commits, resetting and force-pushing can create conflicts and confusion.
         - For pushed/shared commits: git revert <commit id>
         - because it preserve the history and safe for collaboration.

## Task 2: Git Revert — Hands-On:

       1- Make 3 commits (commit X, Y, Z)
          - vim file.txt (commit X)
          - git add .
          - git commit -m "added X"
          -vim file.txt (commit Y)
          - git add .
          - git commit -m "added Y"
          - vim file.txt (commit Z)
          - git add .
          - git commit -m "added Z"
          - git log --oneline
       2- Revert commit Y (the middle one) — what happens?
         - git revert <2nd commit id>
         - git log --oneline
         OUTPUT:
       3- Check git log — is commit Y still in the history?
          - YES
          - git log --oneline
          OUTPUT:
       4- How is git revert different from git reset?
          git revert: - create a new history that undoes new changes.
                      - keep history intact
          git reset:  - move branch pointer backward
                      - can removes the commit from history 
        5- Why is revert considered safer than reset for shared branches?
           - Because no history is rewritten
        6- When would you use revert vs reset?
           - Use revert: - shared branche
                         - push commits
                         - team project
           - Use reset: - local branches
                        - before pushing
                        - cleaning commit history
           
