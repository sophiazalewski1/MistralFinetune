# MistralFinetune
--------------------
## Setup
### Creating an AWS Instance
- Log into AWS and create a ```p2.xlarge``` instance using the EC2 Dashboard
- When prompted, create a new <b>ssh key</b> and save this on your local machine
- Make sure the instance is set to <b>"running"</b> before attemtping to ssh though VSCode
### SSH Through VSCode
- To ssh into your created AWS instnace through VS Code, make sure you have the <b>remote explorer</b> installed
- In the remote explorer tab, press the <b>"+"</b> button to add a new remote host
- When prompted, ssh via the command
```bash
ssh -i absolute_path_to_your_key ec2-user@ec2-<numbers_here>.compute-1.amazonaws.com
```
- Make sure you press <b>'add to config'</b> and also connect to the instance, you are now connected!
### Connect to Github Remotely
- In the VS code terminal, once you are connected to your AWS instance, generate a <b>new SSH key</b> on your remote machine using the following command
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
- Start the SSh agent in the background, and add your <b>SSH private key</b> to the ssh-agent
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```
- Display the contents of your ssh key using the <b>"cat"</b> command below. By default, the public key file is named <b>id_rsa.pub</b> and is located in the <b>~/.ssh directory</b> (unless you've saved it under a different name or location). You can then manually select and copy the text from the terminal window (starting with <b>ssh-rsa</b> and ending with <b>your email or comment</b> at the end)
```bash
cat ~/.ssh/id_rsa.pub
```
- Once you have your SSh public key copied, you can add it to your <b>GitHub</b> account by navigating to <b>settings -> ssh keys -> new ssh key</b>
- Make sure to give your key <b>"write"</b> access so you can push to the github
- After connecting your ssh key, run the command
```bash
git clone https://github.com/sophiazalewski1/MistralFinetune.git
```
- If git is not installed, look up the instructions on how to install git via your current linux distribution. For my system (CentOS 7 and below), this seemed to work:
```bash
sudo yum update -y
sudo yum install git -y
```


