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
         - 
