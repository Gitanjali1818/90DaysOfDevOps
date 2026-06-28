## Day 26 – GitHub CLI: Manage GitHub from Your Terminal


## Task 1: Install and Authenticate:
          1- Install the GitHub CLI on your machine
             1-winget install GitHub.cli
             2- gh --version
          2- Authenticate with your GitHub account
             1- gh auth login
                Select: GitHub.com
                        HTTPS
                        Login with browser
                        Authorize GitHub CLI
           3- Verify you're logged in and check which account is active
              1- git auth status
           4- What authentication methods does gh support?
               1- Browser based OAuth authentication
               2- Personal access token
               3-GitHub enterprises authentication

## Task 2: Working with Repositories:
          1- Create a new GitHub repo directly from the terminal — make it public with a README
             - gh repo create day-26-gh-demo --public --clone --add-readme
          2- Clone a repo using gh instead of git clone
             - gh repo clone day-26-gh-demo
          3- View details of one of your repos from the terminal
             - gh repo view
          4- List all your repositories
            - gh repo list
          5- Open a repo in your browser directly from the terminal
            - gh repo view --web
          6- Delete the test repo you created 
            - gh repo delete day-26-gh-demo --yes

## Task 3: Issues
          1- Create an issue on one of your repos from the terminal — give it a title, body, and a label
              gh issue create \
            --title "Update README with GitHub CLI commands" \
            --body "Need to document commonly used GitHub CLI commands for future reference." \
            --label documentation
          2- List all open issues on that repo
             - gh issue list
          3- View a specific issue by its number
             - gh issue view 3
          4- Close an issue from the terminal
             - gh issue close 3
          5- How could you use gh issue in a script or automation?   
             - Automatically create issues when a deployment fails
             - Create bug reports from monitoring tools.
             - Generate weekly maintenance issues.
             - Close resolved issues after successful CI/CD runs

## Task 4: Pull Requests:
           1- Create a branch, make a change, push it, and create a pull request entirely from the terminal
             - git checkout -b update-readme
             - vim README.md (This is ths github CLI command)
             - git add .
             - git commit -m "added gh cli command"
             - git push -u origin update-readme
             - gh pr create --fill
          2- List all open PRs on a repo   
             - gh pr list
          3- View the details of your PR — check its status, reviewers, and checks
             - gh pr view 5
             OUTPUT
          4- Merge your PR from the terminal
            - gh pr merge -5 --merge
          5- What merge methods does gh pr merge support?
            - --merge → Creates a merge commit.
            - --squash → Combines all commits into one.
            - --rebase → Rebases commits before merging.
          6- How would you review someone else's PR using gh?
            - gh pr view : view the pr
            - gh pr diff: check change the file
            - gh pr review
            - gh pr review --approve : approve 

## Task 5: GitHub Actions & Workflows (Preview):
          1- List the workflow runs on any public repo that uses GitHub Actions
             - gh run list --repo cli/cli
             OUTPUT:
          2- View the status of a specific workflow run
            - gh run view <run id> --repo cli/cli
            OUTPUT:
          3- How could gh run and gh workflow be useful in a CI/CD pipeline?  
             1- monitor workflow exicution without opening github
             2- check whether builts or deployments completed successfully
             3- view logs when workflow is fails
             4- re-run failed workflow exicution
             5- trigger workflows from the terminal


## Task 6: Useful gh Tricks:
           1- gh api user: GitHub account information in JSON format.
                                    output:
           2- gh gist: - echo "GitHub CLI Practice" > notes.txt 
                       - Creating a Gist from the terminal is quick and useful when sharing notes
                       - gh gist create notes.txt
           3- gh release: -gh release create v1.0.0 
                          -The command asked for release details because my repository didn't have a release yet. 
           4- gh alias: - gh alias set prs "pr status"
                        - Aliases help save time when using the same commands repeatedly.
                        - gh prs 
           5- gh search repos: -gh search repos docker
                              -I searched for Docker repositories.

## Commands Added to git-commands.md:
                commands                               Description
           1- gh auth login                     authentication guthub cli
           2- gh repo clone                     clone repo
           3- gh repo create                    create repo
           4- gh issue create                   creats issue
           5- gh issue list                     view list
           6- gh issue view                     view issue
           7- gh issue close                    close issue
           8- gh pr create                      create pull request
           9- gh pr view                        view pull request
           10- gh pr list                       list pull request
           11- gh pr merge                      merge pull request 
           12- gh run list                      list workfloe run
           13- gh run view                      view workflow run
           14- gh workflow list                 list workflows
           15- gh api                           call Github REST API
           16- gh gist create                   create Github Gist
           17- gh release create                create release 
           18- gh alies set                     create command aliases
           19- gh search repos                  search GitHub repositories

           
                        

             
             
            
