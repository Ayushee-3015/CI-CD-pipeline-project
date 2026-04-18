# CI/CD Pipeline using Jenkins & Docker on AWS EC2

## Project Overview

### This project demonstrates a complete CI/CD pipeline setup using Jenkins, Docker, and AWS EC2. The pipeline automates code deployment from GitHub to a live application.

## Tech Stack
1.Jenkins

2.Docker

3.Docker

4.AWS EC2

5.Node.js


## Architecture

GitHub → Jenkins → Docker → EC2

## Pipeline Flow

1.Code pushed to GitHub

2.Jenkins pulls latest code

3.Docker image is built

4.Old container is removed

5.New container is deployed


## Live Demo

http://<EC2 IP>:3000

## Screeshots

<img width="1339" height="645" alt="image" src="https://github.com/user-attachments/assets/a0eecf58-c733-41d6-abca-bfedf4e293a7" />


<img width="347" height="191" alt="image" src="https://github.com/user-attachments/assets/e8cdee4b-f0d3-49c2-bfe1-1bfa1bbe401e" />


<img width="1288" height="105" alt="image" src="https://github.com/user-attachments/assets/52b9c9ec-b790-45a6-81a1-bfe75e476404" />


## Build console putput

Started by user Ayushee
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/devops-project
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Clone Code)
[Pipeline] git
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/devops-project/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/Ayushee-3015/CI-CD-pipeline-project # timeout=10
Fetching upstream changes from https://github.com/Ayushee-3015/CI-CD-pipeline-project
 > git --version # timeout=10
 > git --version # 'git version 2.43.0'
 > git fetch --tags --force --progress -- https://github.com/Ayushee-3015/CI-CD-pipeline-project +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision 81ee85ec75d3cf9e9ab6fa0b38c4748259aab8c9 (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 81ee85ec75d3cf9e9ab6fa0b38c4748259aab8c9 # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git branch -D main # timeout=10
 > git checkout -b main 81ee85ec75d3cf9e9ab6fa0b38c4748259aab8c9 # timeout=10
Commit message: "Update README.md"
First time build. Skipping changelog.
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build Docker Image)
[Pipeline] sh
+ docker build -t devops-app .
DEPRECATED: The legacy builder is deprecated and will be removed in a future release.
            Install the buildx component to build images with BuildKit:
            https://docs.docker.com/go/buildx/

Sending build context to Docker daemon  97.79kB

Step 1/7 : FROM node:18
18: Pulling from library/node
1cfd1b2a145f: Already exists
37927ed901b1: Pulling fs layer
3e6b9d1a9511: Pulling fs layer
461077a72fb7: Pulling fs layer
cda7f44f2bdd: Pulling fs layer
79b2f47ad444: Pulling fs layer
e23f099911d6: Pulling fs layer
c6b30c3f1696: Pulling fs layer
3697be50c98b: Pulling fs layer
461077a72fb7: Already exists
cda7f44f2bdd: Already exists
3697be50c98b: Already exists
37927ed901b1: Download complete
37a8114c5a8f: Download complete
3e6b9d1a9511: Download complete
79b2f47ad444: Download complete
c6b30c3f1696: Download complete
e23f099911d6: Download complete
3e6b9d1a9511: Pull complete
37927ed901b1: Pull complete
79b2f47ad444: Pull complete
e23f099911d6: Pull complete
cda7f44f2bdd: Pull complete
c6b30c3f1696: Pull complete
461077a72fb7: Pull complete
3697be50c98b: Pull complete
Digest: sha256:c6ae79e38498325db67193d391e6ec1d224d96c693a8a4d943498556716d3783
Status: Downloaded newer image for node:18
 ---> c6ae79e38498
Step 2/7 : WORKDIR /app
 ---> Running in cfe8a2b8862c
 ---> Removed intermediate container cfe8a2b8862c
 ---> 95f379630086
Step 3/7 : COPY package.json .
 ---> 625852a56fb1
Step 4/7 : RUN npm install
 ---> Running in f9e567ef2128

added 68 packages, and audited 69 packages in 5s

15 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
[91mnpm notice
npm notice New major version of npm available! 10.8.2 -> 11.12.1
npm notice Changelog: https://github.com/npm/cli/releases/tag/v11.12.1
npm notice To update run: npm install -g npm@11.12.1
npm notice
[0m ---> Removed intermediate container f9e567ef2128
 ---> b1c06e9fc567
Step 5/7 : COPY . .
 ---> cd80e9d8826b
Step 6/7 : EXPOSE 3000
 ---> Running in dd4efed5e0d2
 ---> Removed intermediate container dd4efed5e0d2
 ---> 80a5fd4dfc4f
Step 7/7 : CMD ["node", "app.js"]
 ---> Running in e18e33f27150
 ---> Removed intermediate container e18e33f27150
 ---> 36a4a078e1d7
Successfully built 36a4a078e1d7
Successfully tagged devops-app:latest
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Stop Old Container)
[Pipeline] sh
+ docker rm -f devops-container
Error response from daemon: No such container: devops-container
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Run Container)
[Pipeline] sh
+ docker run -d -p 3000:3000 --name devops-container devops-app
feba979b3690a8658f3cd94d48a9747f2ec7b64c8dcefb058d13e83993dc2cf2
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS




## Learnings

1.CI/CD automation

2.Docker containerization

3.Jenkins pipeline setup

4.Cloud deployment (EC2)

