# Setup Steps for HTTPS Connections to AWS CodeCommit Repositories on Windows with the AWS CLI Credential Helper.

Before you can connect to AWS CodeCommit for the first time, you must complete the initial configuration steps . Here we are using CodeCommit root account, federated access, or temporary credentials, you can use the credential helper that is included in the AWS CLI.

   ## Step 1: install and configure the AWS CLI  : - 

   On your local machine, download and install the AWS CLI. This is a prerequisite for interacting with CodeCommit from the command line.CodeCommit works only with **AWS CLI versions 1.7.38** and later. As a best practice, install or upgrade the AWS CLI to the latest version available. To determine which version of the AWS CLI you have installed, run the **aws --version command**.

   ## Step 2: Install Git
   
To work with files, commits, and other information in CodeCommit repositories, you must install Git on your local machine. CodeCommit supports **Git versions 1.7.9** and later. We recommend using a recent version of Git.To install Git, we recommend websites such as Git for Windows. If you use this link to install Git, you can accept all of the installation default settings except for the following:
When prompted during the Adjusting your PATH environment step, choose the option to use Git from the command line.

(Optional) If you intend to use HTTPS with the credential helper that is included in the AWS CLI instead of configuring Git credentials for CodeCommit, on the Configuring extra options page, make sure the **Disable Git Credential Manager option** . The Git Credential Manager is only compatible with CodeCommit if IAM users configure Git credentials

## Step 3: Set Up the Credential Helper

The AWS CLI includes a Git credential helper you can use with CodeCommit. The Git credential helper requires an AWS credential profile, which stores a copy of an IAM user's AWS access key ID and AWS secret access key (along with a default AWS Region name and default output format). The Git credential helper uses this information to automatically authenticate with CodeCommit so you don't need to enter this information every time you use Git to interact with CodeCommit.

Open a command prompt and use Git to run **git config**, specifying the use of the Git credential helper with the AWS credential profile, which enables the Git credential helper to send the path to repositories:


> **git config --global credential.helper "!aws codecommit credential-helper $@"**

> **git config --global credential.UseHttpPath true**



The Git credential helper writes the following to the .gitconfig file:

**[credential]    
    helper = !aws codecommit credential-helper $@ 
    UseHttpPath = true**  

## Step 4: Configure AWS CLI With your SSO Credential 

We need to bookmark our sso signup link .  following  below  Example is just example link .
       
 **https://my-sso-portal.awsapps.com/start**

Copy paste the link in your browser and select your account .Then select your account it will give you two option management Console and programmatic  access . Here we need to click on programmatic access . agin it will give you two options like MAC/Linux and windows .Here we need to select windows,  because we are using windows . copy environment credential and paste it on CMD 

## Step 5: Connect to the CodeCommit Console and Clone the Repository

If an administrator has already sent you the name and connection details for the CodeCommit repository, you can skip this step and clone the repository directly.

Open the CodeCommit console at **https://console.aws.amazon.com/codesuite/codecommit/home.**

In the region selector, choose the AWS Region where the repository was created. Repositories are specific to an AWS Region.Find the repository you want to connect to from the list and choose it. Choose Clone URL, and then choose the protocol you want to use when cloning or connecting to the repository. This copies the clone URL.

**git clone https://git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo**


---
___

# Setup Steps for HTTPS Connections to AWS CodeCommit with git-remote-codecommit

If you want to connect to CodeCommit using a root account, federated access, or temporary credentials, you should set up access using git-remote-codecommit. This utility provides a simple method for pushing and pulling code from CodeCommit repositories by extending 
Git. It is the recommended method for supporting connections made with federated access, identity providers, and temporary credentials.  Instead of creating an IAM user, you can use existing identities from AWS Directory Service, your enterprise user directory, or a web identity provider. These are known as federated users. AWS assigns a role to a federated user when access is requested through an identity provider. For more information about federated users
   

You can also use git-remote-codecommit with an IAM user. Unlike other HTTPS connection methods, git-remote-codecommit does not require setting up Git credentials for the user Some IDEs do not support the clone URL format used by git-remote-codecommit. You might have to manually clone repositories to your local computer before you can work with them in your preferred IDE
      
## Step 1: Install Prerequisites for git-remote-codecommit

Before you can use git-remote-codecommit, you must install some prerequisites on your local computer. These include:Python **(version 3 or later)** and its package manager, pip, if they are not already installed. To download and install the latest version of Python, visit the Python website.When you install Python on Windows, make sure that you choose the option to add Python to the path.git-remote-codecommit requires **pip version 9.0.3** or later. 

Installing Pip

Once you’ve confirmed that Python is correctly installed, you can proceed with installing Pip.

Download **get-pip.py** to a folder on your computer.
Open a command prompt and navigate to the folder containing **get-pip.py.**
Run the following command:
> python get-pip.py

Pip is now installed!

To check your version of pip, open a terminal or command line and run the following command:

> pip --version
 
## Step 2: Install git-remote-codecommit
Follow these steps to install git-remote-codecommit.
To install git-remote-codecommit At the terminal or command line, run the following command:

> pip install git-remote-codecommit

Monitor the installation process until you see a success message similar to the following:
Successfully built git-remote-codecommit

 ## Step 3: Set Up the Credential Helper

The AWS CLI includes a Git credential helper you can use with CodeCommit. The Git credential helper requires an AWS credential profile, which stores a copy of an IAM user's AWS access key ID and AWS secret access key (along with a default AWS Region name and default output format). The Git credential helper uses this information to automatically authenticate with CodeCommit so you don't need to enter this information every time you use Git to interact with CodeCommit.

Open a command prompt and use Git to run **git config**, specifying the use of the Git credential helper with the AWS credential profile, which enables the Git credential helper to send the path to repositories:


> git config --global credential.helper "!aws codecommit credential-helper $@"

> git config --global credential.UseHttpPath true


The Git credential helper writes the following to the .gitconfig file:

**[credential]    
    helper = !aws codecommit credential-helper $@ 
    UseHttpPath = true**  
 
## Step 4 :- To install and configure the AWS CLI

On your local machine, download and install the AWS CLI. This is a prerequisite for interacting with CodeCommit from the command line. CodeCommit works only with **AWS CLI versions 1.7.38** and later. As a best practice, install or upgrade the AWS CLI to the latest version available. To determine which version of the AWS CLI you have installed, run the aws --version command.
 
## Step 5 :- Configure AWS CLI With your SSO Credential 

We need to bookmark our sso signup link . Example is  following  below .
       
 **https://my-sso-portal.awsapps.com/start**

Copy paste the link in your browser and select your account .Then select your account it will give you two option management Console and programmatic  access . Here we need to click on programmatic access . agin it will give you two options like MAC/Linux and windows . Here we need to select windows,  because we are using windows . copy environment credential and paste it on CMD 

## Step 6: Connect to the CodeCommit Console and Clone the Repository

If an administrator has already sent you the name and connection details for the CodeCommit repository, you can skip this step and clone the repository directly.

Open the CodeCommit console at **https://console.aws.amazon.com/codesuite/codecommit/home.**

In the region selector, choose the AWS Region where the repository was created. Repositories are specific to an AWS Region.Find the repository you want to connect to from the list and choose it. Choose Clone URL, and then choose the protocol you want to use when cloning or connecting to the repository. This copies the clone URL.

> git clone https://git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo
