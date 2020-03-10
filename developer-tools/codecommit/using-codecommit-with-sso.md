
##  AWS CodeCommit with git-remote-codecommit clone step for Windows. 

We need to setup git-remote-codecommit to connect CodeCommit Using a root account, federated access, or temporary credentials .Follwing  Steps are helping you to setup  git-remote-codecommit.   
      
### Step 1: Install Prerequisites for git-remote-codecommit

Note!
 we need must install **Python Version 3** or Later and its package manager pip , git-remote-codecommit requires **pip version 9.0.3** or later.
Install Python 
    1. Download and Install latest python. [Download Python](https://www.python.org/downloads/) . Ensure that the Install launcher for  
       all users (recommended) and the Add Python 3.7 to PATH checkboxes at the bottom are checked .
       
 To Verify python Installition Type the Below Command 
 ```python
  Python --version 
  ```
 Once you’ve confirmed that Python is correctly installed, you can proceed with installing Pip.      
 
 
Installing Pip

    1. Download and install Pip . [Download Pip](https://pip.pypa.io/en/stable/installing/#do-i-need-to-install-pip)


Download **get-pip.py** to a folder on your computer.
Open a command prompt and navigate to the folder containing **get-pip.py.**
Run the following command:

  ```python
 python get-pip.py
 ```
 
Pip is now installed!

To check your version of pip, open a terminal or command line and run the following command:

 ```python
 pip --version
 ```
 
###  Step 2: Install git-remote-codecommit
Follow these steps to install git-remote-codecommit.
To install git-remote-codecommit At the terminal or command line, run the following command:

```python
 pip install git-remote-codecommit
 ```
Below is the message of sucess installtion :

```
Successfully built git-remote-codecommit
```

### Step 3: Set Up the Credential Helper
Open a command prompt and use Followig Command  that  enables the Git credential helper to send the path to repositories:

```
 git config --global credential.helper "!aws codecommit credential-helper $@"

 git config --global credential.UseHttpPath true
```

above  Commannd writes the following to the .gitconfig file:
```
[credential]    
    helper = !aws codecommit credential-helper $@ 
    UseHttpPath = true
```
 
 
### Step 4 :- To install and configure the AWS CLI

Download  and install the AWS CLI[Download AWS Cli ](https://s3.amazonaws.com/aws-cli/AWSCLI64PY3.msi).  CodeCommit works only with **AWS CLI versions 1.7.38** and later. 

To determine which version of the AWS CLI you have installed, run the follwing Command 
```
aws --version 
```

### Step 5 :- Configure AWS CLI with your SSO Credential 

We need to bookmark our sso signup link . Example is  following  below .
       
 **https://my-sso-portal.awsapps.com/start**

Copy paste the link in your browser and select your account .Then select your account, it will give you two option management Console and programmatic  access . Here we need to click on programmatic access . again it will give you two options like MAC/Linux and windows . Here we need to select windows,  because we are using windows . copy environment credential and paste it in CMD 

### Step 6: Connect to the CodeCommit Console and Clone the Repository

Open the CodeCommit console at **https://console.aws.amazon.com/codesuite/codecommit/home.**
```
 git clone https://git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo
```
