# hitc-checkov
HITC Demo of using Checkov to scan IaC

## EXERCISE

In an Ubuntu Linux terminal, run the following commands to install our dependencies:

```
sudo apt update
sudo apt install -y git tree docker.io

```

Next, clone down the repository that we will be scanning with Checkov:

```
git clone https://github.com/Resistor52/tf-vm_in3csps.git

```

Run the following command to see the layout of the `tf-vm_in3csps` project:

```
tree tf-vm_in3csps/

```

Take a moment to look at the various files.

Next lets pull down the docker image of checkov

```
sudo docker pull bridgecrew/checkov

```

Run the help command for checkov:

```
sudo docker run --tty --volume /home/ubuntu/tf-vm_in3csps:/tf --workdir /tf bridgecrew/checkov -h

```

Lets take a look at all of the checks that checkov can perform:

```
sudo docker run --tty --volume /home/ubuntu/tf-vm_in3csps:/tf --workdir /tf bridgecrew/checkov --list

```

Now for the fun part, time to have Checkov run the scan on our Terraform code:

```
sudo docker run --tty --volume /home/ubuntu/tf-vm_in3csps:/tf --workdir /tf bridgecrew/checkov -d /tf

```

## CONCLUSION

Very cool! This repository had some basic Terraform code to deploy a VM in AWS, Azure, and GCP. When we ran Checkov on this code base, we see a variety of issues with each module that should be fixed before this code is deployed.
