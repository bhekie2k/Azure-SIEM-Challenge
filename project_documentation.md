# Project Documentation: Setting Up a Honeypot to Monitor and Visualize Failed Login Attempts Using Azure Sentinel

## Objective
The objective of this project is to build a honeypot environment with a virtual machine (VM) on Azure that is discoverable on the internet with the firewall disabled. The honeypot will utilize Azure Sentinel to monitor and visualize the failed login attempts on a world map, showing the number of attempts by country. Additionally, alerts and incidents will be created for further analysis.

## Step-by-Step Process

1. **Setting Up the Honeypot (VM)**
   - **Create a VM:**
     - Create a Windows 10 VM on Azure.
     - Use a specific username and password for the VM (avoid using default credentials to enhance security).
   - **Disable Firewall:**
     - Access the firewall settings by running `wf.msc` on the VM.
     - Disable the public and private profiles to ensure the VM is fully discoverable on the internet, making it an attractive target for potential attackers.

2. **Running the PowerShell Script**
   - **Script Details:**
     - Develop a PowerShell script to monitor and log failed login attempts.
     - The script should capture the following information:
       - Latitude and longitude of the IP addresses attempting to brute force the VM.
       - Attempted username.
       - IP address.
       - Timestamp of the attempted login.
   - **Geolocation API Integration:**
     - Use an API to convert the latitude and longitude into country and state information.
     - Set the script to run continuously for 96 hours, with the API making 1000 calls per day.

3. **Setting Up Azure Sentinel**
   - **Log Analytics Workspace:**
     - Create a Log Analytics workspace in Azure.
   - **Configure Azure Sentinel:**
     - Set up Azure Sentinel and connect it to the Log Analytics workspace.
     - Activate Azure Security Center and configure data collection rules to collect common security events from the Windows 10 VM.

4. **Data Visualization**
   - **Creating a Custom Table:**
     - Create a custom table named `failed_logon_CL` in Azure Sentinel to store the collected data.
   - **KQL Query for Data Analysis:**
     - Write a Kusto Query Language (KQL) query to display the following information:
       - Latitude.
       - Longitude.
       - State.
       - Country.
       - Attempted username.
       - Attempted count.
   - **Map Visualization:**
     - Use the Map visualization feature in Azure Sentinel to display a world map.
     - The map should show the locations of all attempted hacks, indicating the country and state of origin.

5. **Creating Alerts and Incidents**
   - **Define Alerts:**
     - Set up alerts in Azure Sentinel to notify when certain thresholds of failed login attempts are met.
   - **Incident Management:**
     - Configure incidents in Azure Sentinel to investigate and respond to significant security events.

## Conclusion
This honeypot environment demonstrates the ability to use Microsoft Azure resources and Azure Sentinel to monitor and visualize failed login attempts on a globally accessible VM. By setting up alerts and incidents, it also showcases the capability to respond to security threats in real-time. This project highlights essential skills for a Cloud Security Engineer in managing and securing cloud infrastructure.

## Attachments
- PowerShell Script for Monitoring Failed Login Attempts.
- Sample KQL Queries Used in Azure Sentinel.
- Screenshots of Map Visualization and Alerts Configuration.

## Future Enhancements
- Implement more robust security measures after the monitoring period, such as enabling firewalls and using multi-factor authentication (MFA).
- Explore additional Azure Sentinel features for more advanced threat detection and response.
