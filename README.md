
# Ansible Management of RHoMIS Components

This repository contains scripts needed to setup, update, test, and deploy the components developed for the RHoMIS 2.0 platform.

## Setup

Installation of ansible was done using [this guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)



### Domain

* Pick a domain name for both your staging site, and your production site. Setup the domain name, and add the named servers of your VPS provider.
...

### VPS Setup

* Ubuntu 20.04
* Swap file
* Open ports
* Link to domain

* This can be automated via ansible, however the scripts to do this depend on your cloud service provider. We have tried to keep these installation instructions independent of providers

### Installation



## Requirements:

* python >= 3.6
* boto3 >= 1.15.0
* botocore >= 1.18.0
* aws-cli >= 2.4.6



## Creating a domain

1. Find a domain provider, in my case I used NameCheap. 
2. Go to your lightsail console, create a new DNS zone, and add the new domain.
3. Look for the "Name Servers" in your DNS zone, and add these to your domain provider.

## Creating `vars.yml` file

* Create the `vars.yml` by copying the `vars_template.yml` file and renaming it to `vars`.
* Go through each of the variables, and rename the appropriately based on the domain you have set up, the type of instance you would like, the region/zone.

## Creating `inventory` file

* You will need to manage the hosts that you create and ensure you can connect to them. 

## Managing the instance

* Each of the blocks in the main playbook `manageLightsailInstance.yml` can be run using the command:

`ansible-playbook -v manageLightsailInstance.yml --tags TAGNAME`

* To create an instance, replace `TAGNAME` with `create`.
* To delete an instance, replace `TAGNAME` with `delete`.


# Deployment

* After the VPS is created, 


# Useful Links

* See [here](https://docs.ansible.com/ansible/latest/user_guide/sample_setup.html#sample-setup) for a full sample ansible setup

* Handling ansible secrets [here](https://stackoverflow.com/questions/30209062/ansible-how-to-encrypt-some-variables-in-an-inventory-file-in-a-separate-vault)

* See [here](https://medium.com/@dustindavignon/getting-started-with-ansible-ef5d13111cb1) for a tutorial on getting started with Ansible and AWS lightsail.

* Good [explanation](https://www.middlewareinventory.com/blog/ansible-playbook-example/) of ansible playbook

* See [here](https://docs.ansible.com/ansible/latest/collections/community/aws/lightsail_module.html) for documentation on how to provision an instance.

* See [here](https://www.digitalocean.com/community/tutorials/how-to-set-up-ansible-inventories) for a guide on Ansible inventories

* See this [tutorial](https://linuxbuz.com/linuxhowto/install-letsencrypt-ssl-ansible) for managing ssl certificates with ansible

* CI [tutorial](https://dev.to/knowbee/how-to-setup-continuous-deployment-of-a-website-on-a-vps-using-github-actions-54im)
* Manage git credentials with git credential manager. And vscode git credential manager. See [here](https://stackoverflow.com/questions/46645843/where-to-store-my-git-personal-access-token), [here](https://docs.github.com/en/actions/security-guides/automatic-token-authentication),