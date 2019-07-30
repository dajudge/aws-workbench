The AWS workbench is set of scripts that makes it trivial to get started with AWS CLI development.
# Prerequesites
1. Works with Linux (tested with Ubuntu)
2. Have docker installed (you are a developer, right?)
3. Checkout this project somewhere under your home directory (you're not working as root, are you?)

# Usage
In order to get started quickly, simply follow these instructions:
## Configure the AWS workbench
```
# Create the config file from the provided sample
user@host:~/devel/project$ cp .config.sample .config

# Fill the missing information in .config (don't worry, it's in .gitignore)
user@host:~/devel/project$ vi .config

user@host:~/devel/project$
```

## Build the workbench docker image
This step is optional as it's also being executed silently when you start the workbench in the 
next step, but it'll take a while and you might want to know what's happening...
```
user@host:~/devel/project$ docker build .workbench
Sending build context to Docker daemon  1.337kB
Step 1/6 : FROM ubuntu:bionic
...
Successfully built deadbeef1234
user@host:~/devel/project$
```
## Enter the development workbench
```
user@host:~/devel/project$ ./workbench 
You are now inside the development workbench.
user@host:~/devel/project$  
```

##  Confirm things are working
```
user@host:~/devel/project$ aws sts get-caller-identity --profile $DEVELOPER_PROFILE_NAME
{
    "UserId": "AAAAAARRRRRROOOOOOMMM:botocore-session-1234567890",
    "Account": "123456789012",
    "Arn": "arn:aws:sts::123456789012:assumed-role/someRole/botocore-session-1234567890"
}
user@host:~/devel/project$
``` 