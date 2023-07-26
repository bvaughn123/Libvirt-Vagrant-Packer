# Nested VM Base Build (awx workflow) 

## Make the Setup VM
Setup Packer, Libvirt, and Vagrant via playbook
- [x] rdp added
- [ ] Remove manual and add task for vagrant install plugin libvirt 
       
    - Can't find ansible modules for running vagrant via native tasks.
    - [todo] (inprogress) Create a simple plugin for running commands ( install plugin, up, destroy, and package)
    
## Create a testing workflow

AWX Test Workflow using Static Inventory
  > Launch -> Project Synch -> Playbook execute -> success conditional -> example maint. tasks

  ```mermaid
  Workflow;
    Launch Template-->Synch Repo;
    Synch Repo-->Setup Tools;
    Setup tools-->On Success;
    Setup tools-->On Failure;
    On Success-->Maint. Tasks1;
    On Failure-->Maint. Tasks2;
  ```

|![](.Resources/simple_workflow_setup.png)|
|:--:|
| *Simple Workflow* |

Cool bells:

- [ ] Would be cool to have a dynamic inventory using tags via the awx vcenter plugin  
        - [Using VMware vCenter Tags in a Red Hat Ansible Tower Dynamic Inventory](https://www.ansible.com/blog/using-vmware-vcenter-tags-in-a-red-hat-ansible-tower-dynamic-inventory)  

- [ ] Utilization of Surveys in the jobs, though unsure how it ineracts with workflows...

  - Currently using hardcoded inventory in awx

##  Base Testing tasks 

| Workflow Job  | Plays: | :Tasks: | :Hosts: |
|-----------------|---------|---------|---------|
| 1/1 | 1 | 20 | 1 | 

> Stdout
```
    ok: [rocky_test]
    TASK [Check if the basic packages have already installed] **********************
    TASK [Update yum cache] ********************************************************
    TASK [Install required packages] ***********************************************
    TASK [Enable epel repo] ********************************************************
    TASK [Upgrade all packages] ****************************************************
    TASK [Check if xrdp is installed] **********************************************
    TASK [Install xrdp] ************************************************************
    TASK [Check if tigervnc-server is installed] ***********************************
    TASK [Install tigervnc-server] *************************************************
    TASK [Add File for Check] ******************************************************
    TASK [hashicorp : Configure hashicorp repo] ************************************
    TASK [hashicorp : Install packer and vagrant] **********************************
    TASK [Install required packages] ***********************************************
```
