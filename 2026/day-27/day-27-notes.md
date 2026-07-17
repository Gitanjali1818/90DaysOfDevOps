## Day 27 – GitHub Profile Makeover: Build Your Developer Identity

## Task 1: Audit Your Current GitHub Profile:
          1- Visit your own GitHub profile as if you were a stranger — what impression does it give?

          2- Is your profile picture professional?
             - Profile picture looked fine but bio was outdated.
          3- Is your bio filled in? Does it say what you do?   
             - Added a proper bio mentioning DevOps learning.
          4- Are your pinned repos relevant, or are they random forks? 
             - Pinned repositories were random and not related to current learning.
          5- Do your repos have descriptions, or are they blank?  
             - Most repositories didn't have descriptions.
          6- Would a recruiter understand what you've been working on?    
             - Overall profile didn't clearly show what I was working on.

## Task 2: Create Your Profile README:
          1- Create a special repository with the same name as your GitHub username 
             - Repository Name: Gitanjali1818
             - visibility: Public
             ## Clone it:
             - git clone https//:
             -cd username
          2- Add a README.md
             - touch README.md
          3- A short introduction — who you are, what you're learning.
             - vim README.md
               Hello, Myself Gitanjali.
               I am learning DevOps through Train With Shubham Josh Batch.
               And actively compliting 90DayOfDevOps challenge.
           4- What you're currently working on     
               ## Currently working on:
               -90DaysOfDevOps
               -Linux
               -Git & GitHub
               -Shell scripting
               - Python
           5- Skills/tools you know or are learning 
               - Linux
               - Git & GitHub
               -Shell scripting
               -Docker
               -Maven
               -Jenkins
           6- Links to your important repos
              -https://github.com/Gitanjali1818/90DaysOfDevOps/tree/master
           7- How to reach you.
              - ingalegitanjali8@gmail.com
           8- git add .
            - git commit -m "Added self info in README"
            - git push origin main

## Task 3: Organize Your Repositories:
          1- 90 Days of DevOps:
             1- Clear README explaining what the challenge is
                Repo name: 90DaysOfDevOps
                   Daily task and practical exercises completed during the challenge.
             2- Organized folder structure by day
                 ## Folder structed:
                     2026
                     |____day-01
                     |____day-02
                     |____-----
          2- Shell Scripts — a dedicated repo for all your shell scripting work 
             1- Move/copy your scripts from Days 16–21 here
                -mkdir shell-scripts
                -cp ../90-days-of-devops/2026/day-16/*.sh .
                -cp ../90-days-of-devops/2026/day-17/*.sh .
                -cp ../90-days-of-devops/2026/day-18/*.sh .
                   and so on..... upto 21 day
              2- Add a README listing what each script does
                # shell scripts
                  collection of shell scripting practice
                  ##scripts-OUTPUT: ubuntu@ip-172-31-44-56:~/2026/shell-scripts$ ls
                                    README.md             file_check.sh            log_analyzer.sh        safe_script.sh
                                    args_demo.sh          for_loop.sh              log_rotate.sh          sample_logs_generator.sh
                                    backup.sh             functions.sh             loop_control.sh        server_check.sh
                                    check_number.sh       greet.sh                 looping_over_files.sh  strict_demo.sh
                                    count.sh              if_else_server_check.sh  maintance.sh           system_info.sh
                                    countdown.sh          install_packages.sh      passing_arguments.sh   untill_loop.sh
                                    defining_function.sh  local_demo.sh            read.sh                variable.sh
                                    disk_check.sh         local_variable.sh        return_value.sh        while_loop.sh
                    -
          3- Python Scripts — a dedicated repo for your Python projects
             1- Move/copy your scripts from Days 7–15 here
                -Repo name: python script
                -mkdir python-script
                -cp ../90-days-of-devops/2026/day-07/*.py .
                -cp ../90-days-of-devops/2026/day-08/*.py .
                -cp ../90-days-of-devops/2026/day-09/*.py .
                 and so on.... upto 15 day
             2- Add a README listing what each script does
                ##python scripts:
                   practice programs written while learning programs.
                ##Topics:
                   -variable
                   -loop
                   -function
                   -file handling
            4- DevOps Notes — a repo for your learning notes, cheat sheets, and references
               1- Add your shell scripting cheat sheet
                  -Repo name: Devops notes
                  -mkdir linux shell git python   
                  -cp shell-cheatsheet.md Shell/
               2- Add your git-commands.md
                 - cp git-commands.md git/
               3- Organize by topic (Linux, Git, Python, etc.)
                 - yes. In above question it is achieve.
               4- A proper README.md explaining what's inside
                   ##README
                     notes collected during the practice.
                     ##Topic:
                      -linux
                      -shell-script
                      -git
                      -python
               5- A relevant .gitignore
                  -touch gitignore
                  (.env,*.log,*.pyc)
               6- git add .
                  -git commit -m "orgnise the repo"
                  -git push origin main

## Task 4: Pin Your Best Repos:
          1- Go to your GitHub profile and select 4 pinned repositories
             ## 90-days-of-devops
               1-shell-script
               2-python
               3-linux practice
               4-devops notes
           2- Choose repos that best represent your work and learning
           3- Make sure each pinned repo has a description and README

## Task 5: Clean Up:
          1- Delete or archive repos that are empty, abandoned, or irrelevant
          2- Rename any repos with unclear names
          3- Make sure you're not exposing any secrets
          ##usefull commands:
            -git status
            -git log
            -git ls-files
            -git remote -v

## Task 6 – Before & After:
       1- Take a screenshot of your GitHub profile before you started today
       2- Take a screenshot after all your changes
       3- Add both to your day-27-notes.md
       4- Write 3 things you improved and why
        
            

           

           
               
               



    
