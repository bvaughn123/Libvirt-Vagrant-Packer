# Nested VM Base Build (awx workflow) 

## Make the Setup VM
Setup Packer, Libvirt, and Vagrant via playbook
- [x] rdp added
- [ ] Remove manual and add task for vagrant install plugin libvirt  
    > Use Plugin (may need to update and test) 
    []()
       
    - Can't find ansible modules for running vagrant via native tasks.
    - [todo] (inprogress) Create a simple plugin for running commands ( install plugin, up, destroy, and package)
    
## Create a testing workflow

AWX Test Workflow using Static Inventory
  > Launch -> Project Synch -> Playbook execute -> success conditional -> example maint. tasks

|![](.Resources/simple_workflow_setup.png)|
|:--:|
| *Simple Workflow* |

```mermaid
  graph TD;
    Launch-->Synch;
    Synch-->Setup;
    Setup-->On_Success;
    Setup-->On_Failure;
    On_Success-->Maint_TL1;
    On_Failure-->Maint_TL2;
```

- [ ] [todo] Make workflow, with test_stuff repo...

Cool bells:

- [ ] Would be cool to have a dynamic inventory using tags via the awx vcenter plugin  
        - [Using VMware vCenter Tags in a Red Hat Ansible Tower Dynamic Inventory](https://www.ansible.com/blog/using-vmware-vcenter-tags-in-a-red-hat-ansible-tower-dynamic-inventory)  

- [ ] Utilization of Surveys in the 

  - [todo] Test Surveys in workflows

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
