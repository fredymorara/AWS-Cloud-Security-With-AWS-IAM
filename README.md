<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** Fredrick Momanyi  
**Email:** momanyifredm@gmail.com

---

![Image](http://learn.nextwork.org/determined_lavender_smart_antelope/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate Cloud Security with AWS Identinty and Access Management (IAM) service. I'm doing this project to learn how to control who is authorized and authenticated to use your AWS cloud resources.

### Tools and concepts

Services I used were Amazon EC2 and IAM Key concepts I learnt include settings up EC2 Instances, creating IAM Policies, Creating AWS account alias, Creating IAM users and user groups and then testing created policies with and without IAM policy simulator.

### Project reflection

This project took me approximately two hours and forty five minutes. The most challenging part was navigating aws and geting to know where what you are looking foris located and then how to configure each step of the way, understanding why we are configuring something with specific parameters. It was most rewarding to finally see my users can access through the account alias and also the policies I created were implemented correctly.

---

## Tags

### What I did in this step

In this step, I will launch two new EC2 instances because we need computing power to handle traffic to websites.

### Understanding tags

Tags are like labels we give AWS resouces for organization so that its easy to identify them uusing the tags for use.

### My tag configuration

The tag I’ve used on my EC2 instances is called Env to represent the enviroment we are currently in. The value I’ve assigned for my instances are production and deployment for when we are in the development enviroment we will use the development EC2 instance and when we get into production we will use the production EC2 instance. I also have the initial Name tag that help you know what EC2 instance you are running.

![Image](http://learn.nextwork.org/determined_lavender_smart_antelope/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

### What I did in this step

In this step, I will create an AWS IAM policy to give access to the EC2 instance for development I created above because I am practicing by assuming I am giving an intern access to AWS EC2 resources but can't have break production of end user services.

### Understanding IAM policies

IAM Policies are rules on whom can do what with your AWS resources. It is about giving permisions to users, groups or roles on what the can or can't do on those resources and when do they come in effect.

### The policy I set up

For this project, I’ve set up a policy using JSON policy editor although you can also setup using a visual editor.

### Policy effect

I’ve created a policy that allows some actions (like starting, stopping, and describing EC2 instances) for instances tagged with "Env = development" while denying the ability to create or delete tags for all instances.

### Understanding Effect, Action, and Resource

The Effect, Action, and Resource attributes of a JSON policy means: 
The Effect attribute defines whether the policy statement results in an explicit permission (Allow) or an explicit prohibition (Deny). 
The Action attribute specifies the API operations that are being allowed or denied. It describes the specific task a user or service can perform, such as reading from a database, launching a virtual machine, or uploading a file. 
The Resource attribute, ‍Which resources does this policy apply to? specifies the resource, object or set of objects to which the Action applies. 

---

## My JSON Policy

![Image](http://learn.nextwork.org/determined_lavender_smart_antelope/uploads/aws-security-iam_1c864649)

---

## Account Alias

### What I did in this step

In this step, I will simplify user login into AWS by using an Account alias because it simplifies login.


### Understanding account aliases

An account alias is essentially a friendly, memorable name for your AWS account. Instead of using a long, numerical account ID to sign in to the AWS Management Console, you can use this alias.

### Setting up my account alias

Creating an account alias took me. like a minute. Now, my new AWS console sign-in URL is https://nextwork-alias-freddy-morara.signin.aws.amazon.com/console.

![Image](http://learn.nextwork.org/determined_lavender_smart_antelope/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### What I did in this step

In this step, I will setup am IAM group for interns so that i can manage their permissions from one place as a collective.

### Understanding user groups

IAM user groups are the collections/folders of users for easier user management.

### Attaching policies to user groups

I attached the policy I created to this user group, which means all user in that group will have the policy applied to them even though i did not do it manually for each an every one.

### Understanding IAM users

IAM users are identities within AWS that represent a person or application. They have specific permissions attached to them, defining what actions they can perform on AWS resources. This allows for fine-grained control over who can access what in your AWS account.

---

## Logging in as an IAM User

### Sharing sign-in details

The first way is to email is to email them the sign instructions and the second is to download a CSV file of their sign in credentials and share it with them.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed some of my dashboard panels were already revoking me access. This was because the interns account did not have access to the resources those panels represented.

![Image](http://learn.nextwork.org/determined_lavender_smart_antelope/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

### What I did in this step

In this step, I will test my interns IAM user access because i need to ensure all confugarations are ok and needed access is granted and no extra access if given.

### Testing policy actions

I tested my JSON IAM policy by trying to stop both the production and development EC2 instances as an intern account and the production failed with development being a succes as the policy was enforcing the level of access of the intern to only development resources.

### Stopping the production instance

When I tried to stop the production instance it failed with an error pessage popping up. This was because the intern account I created does  not have access to any resource tagged "production".

![Image](http://learn.nextwork.org/determined_lavender_smart_antelope/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

Next, when I tried to stop the development instance it was a success. 

![Image](http://learn.nextwork.org/determined_lavender_smart_antelope/uploads/aws-security-iam_1811801c)

---

## IAM Policy Simulator

To extend my project, I'm going to learn how to test IAM policies using a Policy simulator. I'm doing this because testing on actual resources could interfere with them thus being disruptive to other people using them.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is a special IAM tool used to validate policies without affecting your actual AWS resources. It's useful for when you do not want to test on resources being shared by other user which if you make change it might affect.

### How I used the simulator

I set up a simulation for testing the development group policy i set earlier. The results were succesfull although I had to adjust one of the test settings for the EC2 service when testing its action to stopInstances so that i could test development resources.

![Image](http://learn.nextwork.org/determined_lavender_smart_antelope/uploads/aws-security-iam_069d8a621)

---

---
