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
            
               
