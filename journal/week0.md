# Week 0 — Billing and Architecture

## Materials

- [x] Week 0 – Live Streamed Video Session
- [x] Week 0 – Chirag’s Spend Considerations
- [x] Week 0 – Ashish’s Security Considerations


## Hands-on
Follow Ashish's video, you can setup some best practices below:
- [x] Enable MFA for Root account
- [x] Create an Organization unit

## Homeworks
### 3. Create Admin user
- Go to IAM > Users > Create user
  - Choose [Enable console access], you should use console often.
  - Keep default for anything else
- Add user to a group
  - If you do not have a group yet, create one. Click [Create group]
  - Give it a name like `Administrator`
  - Add `AdministratorAccess` IAM policy to created group.
- Save your credential information at some where safe.
- Try to login into the console using that credential information
  - When first create, you will need to change your password (this setting can be enable/disable when you create the user)

### 4. Using AWS Cloud Shell
- Click on this icon to go to Cloud shell
![](img/week0_20230215054252.png)
- A warning like this will popped up to show that you do not have authorized for this service
  > Unable to start the environment. You don't have required permissions. Ask your IAM administrator for access to AWS CloudShell. System error: User: arn:aws:iam::*****:user/***** is not authorized to perform: cloudshell:CreateEnvironment on resource: arn:aws:cloudshell:us-east-1:*****:*
- Go to IAM > User groups > [Your user group]
- Add permission to your [User group] or user: `AWSCloudShellFullAccess`
  - I think that's not best practice to give *FullAccess anywhere, everytime but in this Cloud Bootcamp, we will use a lots of AWS Cloud shell, so just for future proof, add `AWSCloudShellFullAccess`
- Typing some command line to know your shell is working
  - When first create, the environment will show you a welcome popup.
  - In case you do not know how to use AWS CLI, [this reference](https://docs.aws.amazon.com/cli/latest/) from AWS will help.
    - Ex: aws s3 ls

### 5. Generate AWS credentials
- Go to IAM > Users > [Your user] > `Security credentals` tab > Create access key
- I create this key to access from my local code, so I choose `Local code`
- Set a tag
  ![](img/week0_20230216051657.png)
- Your scecret access key is only showed one, so you should **Download** it to .csv for later needs. If you loose this file, just go to IAM and create a new one.
  ![](img/week0_20230216051848.png)


### 6. Install AWS CLI
- Install AWS CLI on my local computer (MacOS)
```
curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
sudo installer -pkg AWSCLIV2.pkg -target /
```
- Check the AWS version
```
aws --version
aws-cli/2.9.23 Python/3.9.11 Darwin/22.3.0 exe/x86_64 prompt/off
```
- Go ahead, and configure my aws credential profile for this bootcamp (using the Access key and Secret access key retrieved at 5.). Set the --profile will help you switch between profile easier.
```
aws configure --profile bootcamp
AWS Access Key ID [None]: AIDAWIRQ******
AWS Secret Access Key [None]: tJBNH*******
Default region name [None]: ap-northeast-1
Default output format [None]: json
```

- Install AWS Toolkit extension for VSCode. This extension is offical from AWS
  ![](img/week0_20230216052343.png)
- After installing, click on the AWS label in the bottom of VSCode, you will see a Switch Connection popup asking you which profile to connect to.
  ![](img/week0_20230216052652.png)

### 7. Create a budget, billing Alarm alerts
- Go to your account (top right menu) > Billing Dashboard > Budgets
- Click `Create budget` button
- Choose Using a template
- Create 2 budgets for this bootcamp
  - one Zero spend budget, to inform that any service still running.
  - one Monthly cost budget to set my spending limitation. Mine is $100
![](img/week0_20230215063944.png)
- Create 1 custom budget for experimence
  - Choose [Customize] > [Usage budget]
  - Choost Create alert when using > 80% of the threshold
  - Ex: you set the usage budget is 2000 Hours for EC2 service, then 80% mean 1600 Hours
![](img/week0_20230215064936.png)


