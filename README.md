## What is CI CD
CI/CD stands for Continuous Integration/Continuous Delivery, is the backbone of the benefits of integrating DevOps methodology. It helps push and deploy more codes faster. At the same time, the team can have instance feedback and make changes if necessary.
## Difference between continuous delivery and continuous deployment 
Deployment goes one step further by applying all stages of the production pipeline to the release where in continuous delivery, its happens in steps manually.
## What is webhook
Webhook in jenkins is a mechanism that automatically trigger the build of a jenkins project in response to a commit pushed to a Git repository

## Steps for jenkins
- create a new ssh key pair called - copy eng130_jenkins_jorge, eng130_jenkins_jorge.pub
### steps

1. create a new CICD pipeline
2. generate a new ssh key pair (ensure to generate it in .ssh folder on localhost)
3. copy file.pub to github repo
4. copy the private key in jenkins
5. create a new job to test the CI
Now your jenkins have connection to your github and can pull and push new code as well as merge them.
## Testing with jenkins
to make testing with jenkins, you make a new job/item. This bring a new page where you can insert instruction. first connect the https of your repo, this will allow jenkins to know where to clone as shown below
<img src="./images/jenkins_item.png" />
After this, you can go to source code management where it acts as VS_code and the repo is in. You also need to make sure that you have your credentials correctly, as shown in "steps for jenkins" above. you can also use <a href="https://github.com/Jorge2091/git_github_setup/tree/main/ssh_setup">This repo</a>
Inside management, you can also have the ability to merge branches to main branch by adding a behaviors below.

## connecting to ec2 with jenkins
The first step is to make sure your security is correctly identified for jenkins IP to ssh, this is also know as port 22.
1. make a new ec2 instance
2. in security group, add ip address of jenkins with correct inside ssh port 22.
3. inside jenkins, add your .pem file using the ssh agent "ssh username with private key" kind.
4. in a shell inside jenkins commands, scp file app to ec2 in aws using `ssh -A -o "StrickHostKeyChecking=no" ubuntu@ec2-ip:/file`
5. copy file inside this ec2 with scp
6. cd to new app
7. npm install
8. npm start & disown (background)
now if you need to stop npm, you need to `ps aux` and shut down npm before redoing these steps.
<img src="./images/jekins_pipeline.png"/>