# Infrastructure-Creation

# Instructions

# Step 1. Set up a CircleCI project
Go to https://app.circleci.com/ and set up a new project associated with your Github repository.

# Step 2. Set up Environment variables
To use the AWS CLI in your jobs you'll need the following environment variables to the in Circle CI > Project Settings > environment variables. The value of these variables can be fetched from the AWS IAM user.

If not already, create an AWS IAM user with programmatic access, and it will generate these credentials.
    AWS_ACCESS_KEY_ID
    AWS_DEFAULT_REGION
    AWS_SECRET_ACCESS_KEY

# Step 3. Create the CloudFormation template
Create a simple template - template.yml that will create an EC2 instance and the associated security group. This should be pushed into your git repo.

# Step 4. Create the CircleCI Config file
The ./circleci/config.yml file will have the following sections:
    Create a job in your Circle CI config file named create_infrastructure
Be mindful of copying-pasting the YAML code above. The job code above:
uses amazon/aws-cli docker image that has AWS CLI installed already.
executes the CloudFormation template to create the infrastructure.
Add the create_infrastructure job to the workflows section, and comment out the unrelated jobs.

    Push your local change to the remote Github repo. Your commits will automatically trigger a CircleCI build.