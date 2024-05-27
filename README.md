# Azure Honeypot with Sentinel

## Objective
1. Build a honeypot environment with a VM on Azure that is discoverable on the internet.
2. Utilize Azure Sentinel to monitor and visualize the failed login attempts on a world map, showing the number of attempts by country.
3. Create alerts and incidents for further analysis.

## Project Structure
- `scripts/` - Contains the PowerShell script for monitoring failed login attempts.
- `queries/` - Contains the KQL queries used in Azure Sentinel.
- `screenshots/` - Contains screenshots of map visualization and alerts configuration.
- `documentation/` - Contains detailed project documentation.

## Steps to Reproduce

1. **Setting Up the Honeypot (VM)**
   - Create a Windows 10 VM on Azure.
   - Change all default administrator account information and use a specific username and password for the VM.
   - Disable the firewall by running `wf.msc` and turning off the public and private profiles.

2. **Running the PowerShell Script**
   - On the honeypot VM, open PowerShell ISE, paste script and save.
   - Register account on https://ipgeolocation.io/ and use your provided API Key in the PS1 script.
   - Run the script and leave it running.
   - Leave the honeypot VM online while running the script for 96 hours.
   - The Geoloction API free version makes 1000 calls per day.

3. **Setting Up Azure Sentinel**
   - Create a Log Analytics workspace.
   - Set up Azure Sentinel and connect it to the workspace.
   - Activate Azure Security Center.
   - Configure data collection rules.

4. **Data Visualization**
   - Create a custom table named `failed_logon_CL` in Azure Sentinel.
   - Write a KQL query to display latitude, longitude, state, country, attempted username, and attempted count.
   - Use the Map visualization feature to display the data on a world map.

5. **Creating Alerts and Incidents**
   - Define alerts in Azure Sentinel for failed login attempts.
   - Configure incidents to investigate and respond to security events.

## Future Enhancements
- Implement stronger security measures post-monitoring, such as enabling firewalls and MFA.
- Explore additional Azure Sentinel features for advanced threat detection and response.
