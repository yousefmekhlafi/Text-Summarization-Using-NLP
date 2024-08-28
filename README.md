# End to end NLP Text Summarization Project

PROJECT STATUS: Functional

# Project scope and goals

1. Learn advanced python OOP concepts by reverse engineering open-source code
2. Get an idea on how NLP transformers work in practice
3. Learning how to deal with text data, and understanding tokenizers  
4. Learn how to make an end-to-end NLP application for processing text data
5. Preparing for AI industry-grade workflows
6. Deep learning practice
7. Practicing CI/CD pipelines through Github actions and cloud deployment



# Project Disclaimers 

The project was done, coded along Krish Naik's YT channel 
YT Link: [https://www.youtube.com/watch?v=-NOIWzjJK-4](https://www.youtube.com/watch?v=p7V4Aa7qEpw&t=2517s)
Project code: [https://github.com/krishnaik06/Text-Summarization-NLP-Project](https://github.com/krishnaik06/Text-Summarization-NLP-Project)

# How to run on your local machine: 

1. Clone my repository (on your local machine)

"git clone https://github.com/yousefmekhlafi/Text-Summarization-Using-NLP"

2. Create a virtual environment on vscode "textS" and activate it

"conda create -n textS python=3.8 -y"
"conda activate textS"

3. install requirements
"pip install -r requirements.txt"

4. Run the app on terminal
"python app.py"

CTRL + click LMB the link provided on terminal and run predictions  


# How to deploy on AWS 

Step 1: Creating IAM user for deployment 

1. go to IAM
2. create user 
3. choose attach policies directly 
4. Add the following policies through the search bar:
AmazonEC2ContainerRegistryFullAccess
AmazonEC2FullAccess
5. next -> create user 


Step 2: Creating Access keys

1. Click on created user  
2. Choose security credintials
3. click create access key
4. choose Command line interface 
5. confirm 
6. download .csv file
7. done


Step 3. Create an ECR (Elastic container registry)

1. Search for ECR
2. create new repository
3. choose a repository name 
4. click on create repository
5. Copy URI and save it somewhere 

ECR Repository URI:
021891609567.dkr.ecr.us-east-1.amazonaws.com/ccancer

Step 4: Create EC2 virtual machine

1. Search for EC2 in AWS search bar
2. click on launch instance
3. choose a name for the the virtual machine
4. choose ubuntu 
5. choose instance type as t2.large (for deep learning models)
6. create new key pair
- choose name
- choose RSA
7. choose:
1. Allow HTTPS traffic from the internet
2. Allow HTTPS traffic from the internet 
8. Change storage to 30 GiB
9. Launch instance
10. connect to instance using default settings

Run the following lines in the CLI

sudo apt-get update -y

sudo apt-get upgrade

#required

curl -fsSL https://get.docker.com -o get-docker.sh

sudo sh get-docker.sh

sudo usermod -aG docker ubuntu

newgrp docker

double check if docker is running on CLI:
docker --version


Step 5. Configuring EC2 as self-hosted runner

1. Go to Github project repostiory settings
2. Go to Actions -> Runners -> New self-hosted runner -> Linux
3. Copy all given commands on Download box and paste into AWS CLI one by one
4. Copy Configure commands -> press enter when prompted to Enter name of group
5. Enter the name of the runner: self-hosted -> press Enter -> press Enter
6. Copy/paste last command 

Step 6. Set up Github secrets: 

1. Click on runners on top of Github page
2. Under settings, go to secrets and variables -> Actions
3. Click on add new repository key
4. Add secrets one by one from previously downloaded CSV file, and AWS pme file

AWS_ACCESS_KEY_ID= "from CSV file"

AWS_SECRET_ACCESS_KEY= "from CSV file"

AWS_REGION = "Same region as your AWS account"

AWS_ECR_LOGIN_URI = "URI link of project's ECR"

ECR_REPOSITORY_NAME = "Name of ECR repo"

Step 7. Running app on cloud

1. Go to instances -> security -> security group -> 
2. Edit inbound rules -> Add rule -> Customer TCP Port range 8080 and 0.0.0.0/0
3. go back to EC2 machine
4. Copy public IP address and access the app

Step 8. Instance termination, ECR deletion, IAM deletion

1. Go to AWS EC2 -> Instance state -> Terminate instance
2. Go to AWS ECR -> Delete docker images from ECRs -> Delete ECR  
3. Go to IAM -> Select user -> Delete user



# Workflow reminder

1. update config.yaml
2. update secrets.yaml (optional)
3. update params.yaml
4. update entities 
5. update config manager
6. update components 
7. update pipeline
8. update main.py
9. update dvc.yaml


# Mlflow testing 

set MLFLOW_TRACKING_URI=https://dagshub.com/yousefmekhlafi/end-to-end-chest-cancer-classification-mlflow-dvc

set MLFLOW_TRACKING_USERNAME=yousefmekhlafi 

set MLFLOW_TRACKING_PASSWORD=d0b4cd5be27b19f397967c9b34dee2aec1d2afb1

