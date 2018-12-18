## Launching EC2 instances without using a keypair

When launching new EC2 instances in AWS, a keypair is optional. This fork removes the need to generate/use a keypair for the EC2 Plugin to work.
See [JENKINS-5853](https://issues.jenkins-ci.org/browse/JENKINS-5853) for more details.

### Get Started

1. Download [the .hpi file](downloads/ec2-v1.40.hpi) and install it manually 

  ```install plugin
  a. In the Jenkins main page, navigate to Manage Jenkins -> Manage Plugins
  b. Click the Advanced tab
  c. In the Upload Plugin section, click Choose File, and select the downloaded .hpi file
  d. Click Upload
  e. restart Jenkins.
  ```

2. Copy and paste your private key in pem format to the SSH Private Key field. 

  ```ssh private key
  a. In the Jenkins main page, navigate to Manage Jenkins -> Configure System
  b. Scroll down, if not done yet, choose Amazon EC2 from the "Add new cloud" dropdown selections
  c. Copy and paste the SSH private key (PEM formatted) into the SSH Private Key field
  d. Click Save or Apply
  ```

3. (Optional) If the SSH public key is not baked into the AMI you choose to use, we can do that in the User Data field

  ```ssh public key
  e. In the AMIs section, click Advanced button to expand
  f. Use "Remote User" ec2-user as an example, and enter your scripts and append the SSH public key as below:
  #!/bin/bash
  ## append the SSH public key
  cat >> /home/ec2-user/.ssh/authorized_keys << EOF
  ssh-rsa xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
  EOF
  ....
  g. Click Save or Apply
  ```

### Download

[Jenkins EC2 Plugin v1.40-SNAPSHOT](downloads/ec2-v1.40.hpi)
[Jenkins EC2 Plugin v1.42-SNAPSHOT](downloads/ec2-v1.42.hpi)

