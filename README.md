# End to End text-summarizer project

##Workflows

1. Update config.yaml
2. Update params.yaml
3. Update entity
4. Update the configuration manager in src config
5. Update the components
6. Update the pipeline
7. Update the main.py
8. Update the app.py


## How to run?

## How to deploy the application
1. Login to AWS console
2. Create IAM user for deployment
    #with specific access
    1. EC2 access: It is virtual machine
    2. ECR: Elastic Container registry to save your docker image in aws
    
    #Description: About the deployment
    1. Build your docker image of the source code
    2. Push your docker image to ECR
    3. Launch your EC2
    4. Pull your image from ECR in EC2
    5. Launch your docker image in EC2

    #Policy:
    1. AmazonEC2ContainerRegistryFullAccess
    2. AmazonEC2FullAccess

3. Create ECR repo to store/save docker image
    - Save the URI: 051826734134.dkr.ecr.ap-southeast-2.amazonaws.com/omi-text-s
4. Create EC2 machine
5. Open EC2 and install docker in EC2 machine:
    #optional
    sudo apt-get update -y
    sudo apt-get upgrade
    #required
    curl -fsSL https://get.docker.com -o get-docker.sh
    sudo sh get-docker.sh
    sudo usermod -aG docker ubuntu
    newgrp docker

6. Configure EC2 as self-hosted runner:
    settings>actions>runner>new self hosted runner> then run command one by one
    NOTE: After the last press enter to keep the default settings and just mention self-hosted when asked for Enter the name of runner
    and then press enter to keep everything default.
    finally enter the last command ./run.sh to make the connection with your github
    Once connected you will see Listening for jobs
    then you can go to your runner in github and you will see idle status.
    to stop the execution in EC2 just press CTRL+C
7. Setup github secrets:
    AWS_ACCESS_KEY_ID=
    AWS_SECRET_ACCESS_KEY=
    AWS_REGION= us-east-1
    AWS_ECR_LOGIN_URI = demo>>
    ECR_RERPOSITORY_NAME = simple-app