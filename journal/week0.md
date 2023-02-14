# Week 0 — Billing and Architecture

## Materials

- [x] Week 0 – Live Streamed Video Session
- [x] Week 0 – Chirag’s Spend Considerations
- [ ] Week 0 – Ashish’s Security Considerations


## Hands-on
Follow Ashish's video, you can setup some best practices below:
- [x] Enable MFA for Root account
- [x] Create an Organization unit

## Homeworks
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

### 5. Create billing alarm
