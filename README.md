# Azure VM Honeypot Integrated with Azure Sentinel (SIEM)
<h2>Description</h2>
<p>This project guides you through the creation of a honeypot environment in Azure, aimed at monitoring and analyzing brute force login attempts. By deploying a Windows 10 Pro Virtual Machine (VM) and integrating it with Azure Sentinel, Microsoft Defender for Cloud, and Log Analytics Workspaces, you'll be able to observe and analyze malicious login attempts in real-time. The project includes setting up logging, custom log creation, and visualization of geographic data using Azure Sentinel workbooks.</p>

<hr>

<h2>Steps</h2>

<ol>
  <li><strong>Create a Resource Group</strong>
    <ul>
      <li>Go to the Azure portal and select Resource Groups.</li>
      <li>Click on Create and follow the prompts:
        <ul>
          <li>Choose your subscription.</li>
          <li>Name your resource group.</li>
          <li>Select a region (e.g., East US).</li>
          <li>Review and Create.</li>
        </ul>
      </li>
      <li>Resource Groups help organize your Azure resources. They allow you to manage all related resources as a single entity and facilitate cleanup once the project is complete.</li>
    </ul>
  </li>
<img width="1437" alt="Screenshot 2024-04-18 at 9 54 32 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/4b71071b-a9ee-4de6-9b06-a65863855d9d">

<hr>
  
  <li><strong>Create a Windows 10 Pro Virtual Machine</strong>
    <ul>
      <li>Navigate to Virtual Machines in the Azure portal.</li>
      <li>Click on Create and follow the steps:
        <ul>
          <li>Choose your subscription and resource group.</li>
          <li>Name the VM and select a region.</li>
          <li>Choose No Infrastructure Redundancy Required for availability options to minimize cost.</li>
          <li>Select the Windows 10 Pro image.</li>
          <li>Choose an appropriate VM size (e.g., Standard_B1s).</li>
          <li>Set up username and password for RDP access.</li>
          <li>Configure networking settings, allowing only RDP (port 3389).</li>
          <li>Review and Create.</li>
        </ul>
      </li>
      <li>Confirm the licensing and review the estimated cost.</li>
      <li>Wait for the VM deployment to complete.</li>
    </ul>
  </li>
<img width="1437" alt="Screenshot 2024-04-18 at 9 55 29 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/fd8d4863-6dd7-4c3e-ba75-3ec28736fa1f">
<img width="1437" alt="Screenshot 2024-04-18 at 9 56 25 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/f6c6ad18-7401-4f86-94b7-5bbf5559217b">
<img width="526" alt="Screenshot 2024-04-18 at 9 56 35 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/ada707f8-92cf-4bae-a34a-d598a8649266">
<img width="1437" alt="Screenshot 2024-04-18 at 9 56 58 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/57a7b2be-6574-4bc3-ab6f-8167f2525b52">
<img width="1437" alt="Screenshot 2024-04-18 at 9 57 30 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/58e29e44-65ac-43c2-9012-ce18b63ebf19">
<img width="1437" alt="Screenshot 2024-04-18 at 9 57 38 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/e5884055-f0da-41a6-9110-64407e02ab91">
<img width="1437" alt="Screenshot 2024-04-18 at 9 57 58 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/b5101169-9725-471b-a39a-c6e3b01acbfa">

<hr>
  
  <li><strong>Set up Log Analytics Workspaces</strong>
    <ul>
      <li>Search for Log Analytics Workspaces in the Azure portal.</li>
      <li>Click on Create and configure the workspace:
        <ul>
          <li>Choose your subscription and resource group.</li>
          <li>Name the workspace (e.g., log-honeypot).</li>
          <li>Review and Create.</li>
        </ul>
      </li>
      <li>Log Analytics Workspaces collect and analyze data from various sources, providing insights into system performance, security, and more.</li>
    </ul>
  </li>
<img width="1437" alt="Screenshot 2024-04-18 at 9 58 53 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/2b776984-abec-4ad1-bd63-1d03bbe1a7ff">


<hr>
  
  <li><strong>Microsoft Defender for Cloud</strong>
  <ul>
    <li>Search for Microsoft Defender for Cloud in the Azure portal.</li>
    <li>Go to Environment Settings and select your Log Analytics Workspace.</li>
    <li>Configure Defender Plans:
      <ul>
        <li>Turn on Servers plan (keep SQL servers settings off).</li>
      </ul>
    </li>
    <li>Configure Data Collection:
      <ul>
        <li>Turn on All Events.</li>
      </ul>
    </li>
    <li>Save the settings.</li>
  </ul>
</li>

<hr>

  <li><strong>Connecting Log Analytics Workspace to the Honeypot VM</strong>
  <ul>
    <li>Navigate to the Log Analytics Workspace created earlier.</li>
    <li>Scroll down to Virtual Machines and connect the Virtual Machine to the workspace.</li>
    <li>This enables data collection from the VM for monitoring and analysis.</li>
  </ul>
</li>

<hr>

<li><strong>Setting up Sentinel (SIEM)</strong>
  <ul>
    <li>Search for Microsoft Sentinel in the Azure portal.</li>
    <li>Click on Create and select the Log Analytics Workspace.</li>
    <li>Follow the prompts to create Microsoft Sentinel.</li>
  </ul>
</li>

<hr>

  <li><strong>Logging into the VM via RDP</strong>
  <ul>
    <li>Access the Virtual Machine you created and copy its Public IP Address.</li>
    <li>Open Remote Desktop Connection and connect to the VM using the IP address.</li>
    <li>Follow the prompts to log in with the provided username and password.</li>
    <li>Adjust privacy settings and accept network discoverability prompts.</li>
  </ul>
</li>

<hr>

<li><strong>GitHub PowerShell Script</strong>
  <ul>
    <li>Visit the provided <a href="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/blob/main/PowerShell%20Log%20Exporter%20(GEO%20IP)" target="_blank">GitHub link</a> and copy the PowerShell Script.</li>
    <li>Open PowerShell ISE, create a new document, and paste the script.</li>
    <li>Save the document on the Desktop with a descriptive name (e.g., Log_Exporter).</li>
  </ul>
</li>

<hr>
  
  <li><strong>API Key for IP Geo Locator</strong>
  <ul>
    <li>In the PowerShell script, navigate to line 1 and copy the link.</li>
    <li>Paste the link into a browser and create a free account to obtain an API Key.</li>
    <li>Copy the API Key and replace the API string in the script.</li>
    <li>Save the script and run it to start logging.</li>
  </ul>
</li>

<hr>

<li><strong>Test Script</strong>
  <ul>
    <li>Open another RDP session and attempt to log into the Virtual Machine with incorrect credentials.</li>
    <li>If the script is working, a purple line will appear in the PowerShell script with the latitude and longitude of the attempted IP address.</li>
  </ul>
</li>

<hr>

<li><strong>Log Analysis</strong>
  <ul>
    <li>Access the log file generated by the PowerShell script.</li>
    <li>Analyze the log file to observe attempted login events.</li>
  </ul>
</li>

<hr>

<li><strong>Create Custom Log</strong>
  <ul>
    <li>Return to the Azure portal and navigate to Log Analytics Workspaces.</li>
    <li>Select your workspace and go to Tables &gt; Create &gt; New Custom Log (MMA-Based).</li>
    <li>Upload the sample log data from the VM to create a custom log in Azure.</li>
    <li>Specify the collection path (e.g., C:\ProgramData\failed_rdp.log) and create the custom log.</li>
  </ul>
</li>

<hr>

  <li><strong>View Logs</strong>
  <ul>
    <li>Navigate to Log Analytics Workspaces &gt; Select your workspace &gt; Logs.</li>
    <li>Search for the custom log you created (e.g., FAILED_RDP_WITH_GEO).</li>
    <li>Wait for logs to generate (may take 20-40 minutes) and run the query again if needed.</li>
  </ul>
</li>

<hr>

<li><strong>Extracting Custom Fields</strong>
  <ul>
    <li>After logs generate, examine the RawData field in the logs.</li>
    <li>Create custom fields to filter the raw data for analysis.</li>
    <li>Copy and paste the <a href="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/blob/main/Extract%20Log%20Query" target="_blank">query</a> to extract custom fields such as username, timestamp, latitude, longitude, and more.</li>
  </ul>
</li>

<hr>

<li><strong>Sentinel Setup</strong>
  <ul>
    <li>Search for Microsoft Sentinel in the Azure portal.</li>
    <li>Select your custom Log Analytics Workspace.</li>
    <li>Configure Microsoft Sentinel to visualize and analyze the log data.</li>
    <li>Add a workbook and customize queries to include custom fields.</li>
    <li>Visualize the data on a map for geographic analysis.</li>
  </ul>
</li>

<hr>

<li><strong>Disable Windows Defender Firewall</strong>
  <ul>
    <li>Search for Windows Defender Firewall in the Windows search bar.</li>
    <li>Open Windows Defender Firewall Properties.</li>
    <li>Disable the firewall for Domain, Private, and Public profiles.</li>
    <li>This step allows external connections to discover the honeypot VM.</li>
  </ul>
</li>

<hr>

<li><strong>Monitor Attacks</strong>
  <ul>
    <li>Leave the VM running to monitor and analyze brute force login attempts.</li>
    <li>Observe Azure Sentinel for alerts and visualizations of attempted logins on the map.</li>
  </ul>
</li>

<hr>

<li><strong>Cleanup</strong>
  <ul>
    <li>Upon completing the project, delete the resource group to avoid additional charges.</li>
    <li>Navigate to the resource group in the Azure portal and select Delete.</li>
    <li>Confirm the deletion to clean up all resources associated with the project.</li>
  </ul>
</li>
</ol>
