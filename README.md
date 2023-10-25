# Sample Node.js application

This repository is a sample Node.js application for Docker's documentation.

1) gh auth login
follow the prompts, choose which account you want to login to, 
you can choose login by web browser or authentication token, be carefull to create such a token to have only these enabled permissions:
The minimum required scopes are 'repo', 'read:org', 'workflow'

2) gh repo create

 What would you like to do?  [Use arrows to move, type to filter]
> Create a new repository on GitHub from scratch
  Create a new repository on GitHub from a template repository
  Push an existing local repository to GitHub
  
  Choose "Create a new repository on GitHub from scratch"
  
1) gh auth login
? You're already logged into github.com. Do you want to re-authenticate? Yes
? What is your preferred protocol for Git operations? HTTPS
? How would you like to authenticate GitHub CLI? Paste an authentication token
Tip: you can generate a Personal Access Token here https://github.com/settings/tokens
The minimum required scopes are 'repo', 'read:org', 'workflow'.
? Paste your authentication token: put-your-token
- gh config set -h github.com git_protocol https
✓ Configured git protocol
✓ Logged in as halilili
2) gh repo create
? What would you like to do? Create a new repository on GitHub from scratch
? Description This repo to be used as an practice for github actions, it is originated from github-action-ci-cd-intro 
? Visibility Public
? Would you like to add a README file? Yes
? Would you like to add a .gitignore? No
? Would you like to add a license? Yes
? Choose a license MIT License
? This will create "your-repo" as a public repository on GitHub. Continue? Yes
✓ Created repository halilili/your-repo on GitHub
? Clone the new repository locally? Yes
Cloning into 'your-repo'...

3) cd your-repo

4) go to the folder, paste all your code

5) 
git add .
git commit -m "adding the files to the repo" 

git remote -v
git push origin main
6) git status
git pull origin main  (to sync between the remote and local repo)



7) Create the Ci.yaml
8) 

git add .
git commit -m "adding the CI workflow to the repo"


some problems happened:
How do I ignore an error on 'git pull' about my local changes would be overwritten by merge?

git reset --hard
git pull

Now, TEst The application:
----------------------------------------

Open a terminal, change directory to the docker-nodejs-sample directory, and run the following command to install the packages.

$ npm install
When the packages have finished installing, run the following command to start the application.

$ node src/index.js
Open a browser and view the application at http://localhost:3000. You should see a simple todo application.

In the terminal, press ctrl+c to stop the application.

Initialize Docker assets: (GO TO THE ref file to check how we can install docker desktop in ubunutu)

docker init
Welcome to the Docker Init CLI!

This utility will walk you through creating the following files with sensible defaults for your project:
  - .dockerignore
  - Dockerfile
  - compose.yaml

Let's get started!

? What application platform does your project use? Node
? What version of Node do you want to use? 18.0.0
? Which package manager do you want to use? npm
? What command do you want to use to start the app: node src/index.js
? What port does your server listen on? 3000

ou should now have the following contents in your docker-nodejs-sample directory.

content_copy
├── docker-nodejs-sample/
│ ├── spec/
│ ├── src/
│ ├── .dockerignore
│ ├── .gitignore
│ ├── compose.yaml
│ ├── Dockerfile
│ ├── package-lock.json
│ ├── package.json
│ └── README.md

Run the application
Inside the docker-nodejs-sample directory, run the following command in a terminal.

$ docker compose up --build
Open a browser and view the application at http://localhost:3000. You should see a simple todo application.

In the terminal, press ctrl+c to stop the application.

Run the application in the background
You can run the application detached from the terminal by adding the -d option. Inside the docker-nodejs-sample directory, run the following command in a terminal.

$ docker compose up --build -d
Open a browser and view the application at http://localhost:3000.

You should see a simple todo application.

In the terminal, run the following command to stop the application.

content_copy
$ docker compose down


