# Jenkins CI/CD on a 3-tier application && Ansible Configuration Management Dev and UAT servers using Static Assignments

## Ansible Refactoring and Static Assignments (IMPORTS AND ROLES)

In the previous project, I implemented CI/CD and Configuration Managment solution on the Development Servers using Ansible [Ansible_Automate_Project](https://github.com/Micah-Shallom/DevOps_Projects/tree/main/11.ANSIBLE%E2%80%93AUTOMATE_PROJECT_7_TO_10).


### **In this project, I will be extending the functionality of this architecture and introducing configurations for UAT environment.**

![](./img/1.architectureproject12.png)
#

## STEP 1 - Jenkins Job Enhancement
#

Install a plugin on Jenkins-Ansible server called `COPY-ARTIFACTS`.
![](./img/2.copyartifact.png)

On the Jenkins-Ansible server, create a new directory called `ansible-config-artifact` <br/>
```
sudo mkdir /home/ubuntu/ansible-config-artifact
```
Change permission of the directory
```
chmod -R 0777 /home/ubuntu/ansible-config-artifact
```

Create a new Freestyle project and name it `save_artifacts`.

![](./img/3.save_artifacts.png)

This project will be triggered by completion of your existing `ansible` project. Configure it accordingly:

![](./img/4a.saveartifact_setup.png)
![](./img/4b.buildtrigger.png)
![](./img/4c.destinationcop.png)

We configured the number of build to 2. This is useful because whenever the jenkins pipeline runs, it creates a directory for the artifacts and it takes alot of space. By specifying the number of build, we can choose to keep only 2 of the latest builds and discard the rest.

Test your set up by making some change in README.MD file inside your ansible-config-mgt repository (right inside master/main branch).

If both Jenkins jobs have completed one after another – you shall see your files inside /home/ubuntu/ansible-config-artifact directory and it will be updated with every commit to your master branch.

Now your Jenkins pipeline is more neat and clean.
![](./img/5.triggeredansible.png)
#
