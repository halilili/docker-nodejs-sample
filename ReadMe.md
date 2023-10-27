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



7) Create the file as an example file-name
8) 

git add .
git commit -m "adding the sample-file to the repo"


some problems happened:
How do I ignore an error on 'git pull' about my local changes would be overwritten by merge?

git reset --hard
git pull



Clone the sample application to use with this guide. Open a terminal, change directory to a directory that you want to work in, and run the following command to clone the repository:

$ git clone https://github.com/docker/docker-nodejs-sample



Test the application without Docker (optional)
You can test the application locally without Docker before you continue building and running the application with Docker. This section requires you to have Node.js 18 installed on your machine. Download and install Node.js.

Open a terminal, change directory to the docker-nodejs-sample directory, and run the following command to install the packages.

$ npm install
When the packages have finished installing, run the following command to start the application.

$ node src/index.js
Open a browser and view the application at http://localhost:3000. You should see a simple todo application.

In the terminal, press ctrl+c to stop the application.

Initialize Docker assets
Now that you have an application, you can use docker init to create the necessary Docker assets to containerize your application. Inside the docker-nodejs-sample directory, run the docker init command in a terminal. Refer to the following example to answer the prompts from docker init.

$ docker init
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
You should now have the following contents in your docker-nodejs-sample directory.

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
To learn more about the files that docker init added, see the following:

Dockerfile
.dockerignore
compose.yaml
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

$ docker compose down

In the terminal, run the following command to stop the application.

content_copy
$ docker compose down


Some problems in Build and push Docker to ghcr:

1) Error: buildx failed with: ERROR: failed to solve: failed to push ghcr.io/halilili/docker-nodejs-sample/docker-nodejs-sample:main: unexpected status from POST request to https://ghcr.io/v2/halilili/docker-nodejs-sample/docker-nodejs-sample/blobs/uploads/: 403 Forbidden

In .github/workflows/docker-build-push.yaml
   The solution is to add the permission:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write
