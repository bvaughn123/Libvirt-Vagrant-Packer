# Playbook 
> Install for packer vagrant and libvirtd


- [x] Remove virtualbox, use libvirt 


| :information: | Setup of Base Testing VM |
|---------------|:------------------------|

##  Base Testing VM Setup 

| :Workflow Job:  | :Plays: | :Tasks: | :Hosts: |
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
