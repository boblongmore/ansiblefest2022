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

![Demo Network](/images/DemoNetwork.png)


The AAP environment used in this Demo consists of one Ansible Automation Controller, Three Exec Nodes, One DB, and One Private Automation Hub. The Automation Hub is used as a private repo for the Execution Environment images.

![Demo AAP2](/images/DemoAAP.png)

<details>
  <summary>Setting up AAP and ServiceNow communication</summary>

1. Create Authentication
   1. Record Redirect URI of your servicenow instance. The redirect will be this format ``` {{https://yourinstance}}.service-now.com/oauth_redirect.do ```
   2. In the Ansible Automation Controller (AAC) go to Administration > Applications and add a new application. Give it a name and input the redirect URI. The authorization grant type should be 'Authorization Code' and the Client type should be 'confidential.' This will generate a client ID and client secret. Save these tokens for later use.
   3. In ServiceNow go to System OAth > Application Registry
   4. Click the New button to create a new Third-Party OAuth provider, input your client ID and client secret you generated in AAC. The default grant type should be 'Authorization Code.'
   5. For authorization URL the value will be ``` {{https://your_aac_address}}/api/o/authorize/ ``` and the token URL will be ``` {{https://your_aac_address}}/api/o/token/ ``` Right click on the gray bar at the top and select save.
   6. Click on the 'OAuth Entity Scopes' tab. Click where it says 'Insert a New Row.' Under Name enter 'Writing Scope' and for OAuth Scope input 'write.' Click update.

2. Create REST Message
   1. In AAP find the API endpoint of the template of workflow you wish to launch (ex. ``` https://{{your_aac_address}}/api/v2/workflow_job_templates/14/launch/ ```.)
   2. Go to System Web Services > Outbound > REST Messages, click on NEW to create a Rest Message
   3. Enter the API Endpoint in the Endpoint field
   4. Authentication type should be OAuth and associate the previously created OAuth profile
   5. Click the link that says 'Get OAuth Token.' This should retrieve the OAuth token from your AAC.
   6. Once you have the OAuth token, you are ready to create the rest message. Under HTTP methods, click on New.
   7. The method type should be 'post,' and the API endpoint should be the same as entered previously.
   8. Under the 'Authentication' tab, select 'OAuth 2.0' and select the previously created OAuth profile
   9. Click on the 'HTTP Request' tab and under 'HTTP Headers' click on 'Insert a new row...' The Name should be 'Content-Type' and the values should be 'application/json'

These are the steps to setup communication between ServiceNow and AAP using OAuth. Additionally, if you wanted to pass variables to AAP, you would do that in the HTTP Method screen. In this example I am setting HTTP Query Parameters with the Content ```{"extra_vars": { "incident_id": "${incident_id}" } } ```. I then set the variable substition with 'incident_id.' This allows the workflow to pass the incident ID to AAP when it sends this REST message. There is also a link in this form for 'Preview Script Usage.' You can use this script in settin up the ServiceNow workflow in workflow editor.

</details>

# Authors

- Bob Longmore bob.longmore@wwt.com
