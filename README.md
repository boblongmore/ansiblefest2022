# Ansiblefest2022
## 1281 - Network Troubleshooting as Code

## Required ansible collections are documented in the execution-environment/requirements.yml file
### ServiceNow ITSM collection
The ITSM module used in this demo is accessible through [Red Hat Automation Hub](https://console.redhat.com/ansible/automation-hub/repo/published/servicenow/itsm "console.redhat.com").

### additional collections required
[Cisco.IOS](https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html "cisco.ios collection")
[Ansible.utils](https://docs.ansible.com/ansible/latest/collections/ansible/utils/index.html "ansible.utils collection")

### Required python packages are documented in the execution-environment/requirements.txt

### Demo Environment
This Demo was tested and developed with ServiceNow Tokyo version and Ansible Automation Platform 2.2.
The network under test was an OSPF point-to-point network with three branch routers all connecting back to one core router. The router configuration was done using the playbooks/configure-cml-rtr.yml playbook. Provisioning of the routers was not part of the demo.



# Authors

- Bob Longmore bob.longmore@wwt.com

