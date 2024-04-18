# SIEM-Home-Lab

## Objective

The Detection Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to ingest and analyze logs within a Security Information and Event Management (SIEM) system, security events on the Kali VM, configure an agent to forward data to the SIEM, and query and analyze the logs within the SIEM. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

### Skills Learned

- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Configure the Elastic Agent on the Linux VM to collect and forward logs to the SIEM.
- Generate security events on the Kali VM.
-  Query for security events in the Elastic SIEM.
- Create a Dashboard to visualize security events.
- Create alerts for security events.

### Tools Used

- Security Information and Event Management (SIEM) system for log ingestion and analysis.
- VirtualBox or VMware
- Kali Linux
  
## STEPS

Task 1: Set up an Elastic Account
To start, we need to create a free account for Elastic Cloud. Follow these steps:
- Sign up for a free trial on Elastic Cloud at https://cloud.elastic.co/registration
- Once you have an account, log in to the Elastic Cloud console at https://cloud.elastic.co
- Click on "Start your free trial" and proceed to create a deployment with Elasticsearch as the deployment type.
- Choose a region and deployment size, then click "Create Deployment" and wait for the configuration to complete.
- Once the deployment is ready, click "continue."
 ![1a](https://github.com/8ball24/SIEM-Home-Lab/assets/162763700/7113e1e4-63bb-4d92-b6ae-365d24932fa3)


Task 2: Setting up the Linux VM
Next, let's set up the Linux VM. Here's what you need to do:
- Download the Kali Linux VM from the official Kali website at https://www.kali.org/get-kali/#kali-virtual-machines
- Create a new VM with the Kali VM file in your preferred virtualization platform, such as VirtualBox or VMware.
- Start the VM and follow the on-screen prompts to install Kali.
- Once the installation is complete, log in to the Kali VM using the credentials "kali" for both the username and password.
 ![1b](https://github.com/8ball24/SIEM-Home-Lab/assets/162763700/ef98b702-44e3-487c-8c31-0f17b900caa1)

Task 3: Setting up the Agent to Collect Logs
Now, let's configure the Elastic Agent on the Linux VM to collect and forward logs to the SIEM. Follow these steps:
- Log in to your Elastic SIEM instance and navigate to the Integrations page by clicking on the Kibana main menu bar at the top left, then selecting "Integrations" at the bottom.
- Search for "Elastic Defend," click on it to open the integration page, and then click on "Install Elastic Defend" to follow the instructions provided on the integration page to install the agent on your Kali VM.
 ![1c](https://github.com/8ball24/SIEM-Home-Lab/assets/162763700/943a8447-12e1-4a9a-8c2d-594ec6911dae)

- Ensure "Linux" is selected, copy the command, and paste it into the Kali terminal.
 ![Screenshot (8)](https://github.com/8ball24/SIEM-Home-Lab/assets/162763700/e9d3ca51-6e39-42ac-889a-155dbe02b480)

- Once the agent is installed, verify its status using the command: `sudo systemctl status elastic-agent.service`
 ![1e](https://github.com/8ball24/SIEM-Home-Lab/assets/162763700/ad80a48d-6824-490b-ae5f-95ffc6e22877)
![1f](https://github.com/8ball24/SIEM-Home-Lab/assets/162763700/1c16bbae-8e9f-43ff-b853-f3d857ccdc78)

 
If you encounter any errors, ensure that your Kali VM is connected to the internet before proceeding.

Task 4: Generating Security Events on the Kali VM
To verify the agent's functionality, let's generate security-related events on the Kali VM using Nmap. Here's how:
- Install Nmap on the Linux VM if not already installed: `sudo apt-get install nmap`
- Run an Nmap scan on the Kali machine: `sudo nmap <vm-ip>`
- This scan will generate security events such as the detection of open ports and services running on those ports.
 ![1g](https://github.com/8ball24/SIEM-Home-Lab/assets/162763700/ce729255-65f5-40bf-b446-43e3bd762147)

Task 5: Querying for Security Events in the Elastic SIEM
With data forwarded from the Kali VM to the SIEM, we can now query and analyze logs. Follow these steps:
- Inside your Elastic Deployment, navigate to the "Logs" tab under "Observability" to view the logs from the Kali VM.
- Enter a search query in the search bar to filter the logs, for example, `event.action: "nmap_scan"` or `process.args: "sudo"`.
- Click "Search" to execute the query. Note that it may take some time for events to populate in the SIEM.
 ![1h](https://github.com/8ball24/SIEM-Home-Lab/assets/162763700/1b27c9aa-1b22-4e0c-809d-baa12faff009)

Task 6: Create a Dashboard to Visualize the Events
Utilize the SIEM app's visualizations and dashboards to analyze logs. Here's how to create a simple dashboard:
- Navigate to the Elastic web portal at https://cloud.elastic.co/
- Click on "Dashboards" under "Analytics," then "Create dashboard."
- Add a new visualization to the dashboard, selecting "Area" or "Line" as the visualization type.
- Configure the visualization with appropriate metrics and save it.
 
![1j](https://github.com/8ball24/SIEM-Home-Lab/assets/162763700/2ac25fb2-a562-417a-9487-d8eba709b92d)

Task 7: Create an Alert
Create alerts in the SIEM to detect security incidents. Follow these steps to create an alert for Nmap scans:
- Click on "Alerts" under "Security," then "Manage rules."
- Create a new rule, select "Custom query," and set the conditions for the rule.
- Give your rule a name and description, set the severity level, and configure the actions to be taken when the rule is triggered.
- Click "Create and enable rule" to create the alert.

## Conclusion:
Embarking on the Home SIEM Lab project has been an illuminating journey, deepening my understanding of cybersecurity through hands-on experience. From setting up a free Elastic account to crafting custom alerts, each task has been a stepping stone towards mastering SIEM concepts and fortifying defensive strategies. Through this endeavor, I've not only honed technical skills in log analysis and attack pattern recognition but also cultivated critical thinking and problem-solving abilities essential in the realm of cybersecurity. Armed with this newfound knowledge, I'm ready to contribute meaningfully to safeguarding digital ecosystems against evolving threats.

