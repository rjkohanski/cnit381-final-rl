
# __Network Autiomation w/ Ansible ⚙️__
## __Final Project For UW-Stout's CNIT-381 Course__

### About This Project -
We have utilized Ansible to fully automate the configuration and management of a small network topology, which encompasses two routers and one L3 switch. We developed 6 playbooks to apply all required settings, from base configurations and service deployment to complex EIGRP routing and VLAN trunking. Playbooks ensured connectivity checks, configuration of services like NTP, and verification/backup procedures.

### Playbook Descriptions -

*  ```01_verify_connectivity.yml:``` This playbook performs a simple check to ensure that the Ansible control node can successfully connect and authenticate via SSH to all managed network devices.

*  ```02_base_config.yml:``` This playbook applies the essential initial configurations to all devices, including setting hostnames, configuring interface descriptions, and applying login banners.

*  ```03_eigrp_config.yml:``` This playbook configures the EIGRP routing protocol (Autonomous System 100) on both routers, advertises all necessary networks, and creates three loopback interfaces on each.

*  ```04_vlan_config.yml:``` This playbook automates the creation of 2-3 specified VLANs on the switch and correctly configures the trunk port connecting the switch to the router.

*  ```05_services_config.yml:``` This playbook configures network services such as setting the NTP server to time.google.com and configuring a buffered logging size of 16384 on all devices.

* ```06_backup_config.yml:``` This playbook executes a connectivity check and then captures the running configuration of all network devices for backup purposes.

> [!NOTE]  
> This is the topology in use for the final project. 

<img src="https://github.com/rjkohanski/cnit381-final-rl/blob/main/assets/381FinalTopo.png?raw=true" alt="Description" style="padding: 10px; padding-left: 10px; width: 80%;">


### Repository File Structure

* [playbooks/]()
  * [01_verify_connectivity.yml](.)
  * [02_base_config.yml]()
  * [03_eigrp_config.yml]()
  * [04_vlan_config.yml]()
  * [05_services_config.yml]()
  * [06_backup_config.yml]()
* [ansible.cfg]()
* [inventory.ini]()
* [README.md]()

## How Do You Run These Beautiful Playbooks?
> [!WARNING]
> __SSH MUST be enabled and running__ with the specified credentials bellow:
>|Function|Username|Password|
>|-|-|-|
>|Local-Login|cisco|cisco123!|
>|Enable|N/A|cisco123!|

> [!IMPORTANT]
> This How-To assumes you are running a __Debain-based Linux distrubition__ with the __Python Ansible modules & Git already installed.__

1. Clone the Repository and Navigate:
    ```
    git clone https://github.com/rjkohanski/cnit381-final-rl
    cd cnit381-final-rl
    ```
2. Execute a Playbook - Use the ansible-playbook command, specifying the required inventory file (inventory.ini) and the path to the desired playbook.
    ```
    # Example: Run the base configuration playbook
    ansible-playbook -i inventory.ini playbooks/02_base_config.yml
    ```

### Repo Contributors -
|Name|Username|
|-|-|
| Robert Kohanski | rjkohanski |
| Leah Widerski | leahwiderski  |