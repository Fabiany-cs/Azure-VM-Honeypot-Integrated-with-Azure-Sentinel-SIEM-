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
<img width="1437" alt="Screenshot 2024-04-18 at 9 59 27 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/f40deb84-f4b1-486c-8952-ed3bad1a79f7">
<img width="1437" alt="Screenshot 2024-04-18 at 9 59 33 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/b4dd4b42-8f2b-489c-a822-35d40a588313">
<img width="1437" alt="Screenshot 2024-04-18 at 9 59 33 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/432497a0-a729-4848-a30d-8b0e58c3f18e">
<img width="1437" alt="Screenshot 2024-04-18 at 9 59 53 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/75af6e79-ffce-42c3-bf2f-12731e646c11">

<hr>

  <li><strong>Connecting Log Analytics Workspace to the Honeypot VM</strong>
  <ul>
    <li>Navigate to the Log Analytics Workspace created earlier.</li>
    <li>Scroll down to Virtual Machines and connect the Virtual Machine to the workspace.</li>
    <li>This enables data collection from the VM for monitoring and analysis.</li>
  </ul>
</li>
<img width="1437" alt="Screenshot 2024-04-18 at 10 00 11 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/128295f4-0394-47f3-9040-9caf14510aab">
<img width="1437" alt="Screenshot 2024-04-18 at 10 00 18 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/dc2c8e04-96bb-4d6c-8a7b-76e0d2220b8a">

<hr>

<li><strong>Setting up Sentinel (SIEM)</strong>
  <ul>
    <li>Search for Microsoft Sentinel in the Azure portal.</li>
    <li>Click on Create and select the Log Analytics Workspace.</li>
    <li>Follow the prompts to create Microsoft Sentinel.</li>
  </ul>
</li>
<img width="1437" alt="Screenshot 2024-04-18 at 10 00 42 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/3255bc47-f16d-46d0-8aab-98adf807fcf1">

<hr>

  <li><strong>Logging into the VM via RDP</strong>
  <ul>
    <li>Access the Virtual Machine you created and copy its Public IP Address.</li>
    <li>Open Remote Desktop Connection and connect to the VM using the IP address.</li>
    <li>Follow the prompts to log in with the provided username and password.</li>
    <li>Adjust privacy settings and accept network discoverability prompts.</li>
  </ul>
</li>
<img width="143" alt="Screenshot 2024-04-18 at 10 01 05 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/248c48a4-f23d-4523-894c-899f7ef1c99a">
<img width="763" alt="Screenshot 2024-04-18 at 10 16 44 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/3e868892-14fe-4eae-bac5-7cfb50e31284"

<hr>

<li><strong>GitHub PowerShell Script</strong>
  <ul>
    <li>Visit the provided <a href="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/blob/main/PowerShell%20Log%20Exporter%20(GEO%20IP)" target="_blank">GitHub link</a> and copy the PowerShell Script.</li>
    <li>Open PowerShell ISE, create a new document, and paste the script.</li>
    <li>Save the document on the Desktop with a descriptive name (e.g., Log_Exporter).</li>
  </ul>
</li>
<img width="1437" alt="Screenshot 2024-04-18 at 10 02 07 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/a4340d57-069d-41d2-8283-71613dd4b7b1">

<hr>
  
  <li><strong>API Key for IP Geo Locator</strong>
  <ul>
    <li>In the PowerShell script, navigate to line 1 and copy the link.</li>
    <li>Paste the link into a browser and create a free account to obtain an API Key.</li>
    <li>Copy the API Key and replace the API string in the script.</li>
    <li>Save the script and run it to start logging.</li>
  </ul>
</li>
<img width="1437" alt="Screenshot 2024-04-18 at 10 02 43 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/a05314df-66ea-4940-acae-da0115a6d538">

<hr>

<li><strong>Test Script</strong>
  <ul>
    <li>Open another RDP session and attempt to log into the Virtual Machine with incorrect credentials.</li>
    <li>If the script is working, a purple line will appear in the PowerShell script with the latitude and longitude of the attempted IP address.</li>
  </ul>
</li>
<img width="1437" alt="Screenshot 2024-04-18 at 10 03 11 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/eeb3824f-bc74-4369-b7a2-167424eb8bf8">

<hr>

<li><strong>Disable Windows Defender Firewall</strong>
  <ul>
    <li>Search for Windows Defender Firewall in the Windows search bar.</li>
    <li>Open Windows Defender Firewall Properties.</li>
    <li>Disable the firewall for Domain, Private, and Public profiles.</li>
    <li>This step allows external connections to discover the honeypot VM.</li>
  </ul>
</li>
<img width="1437" alt="Screenshot 2024-04-18 at 11 06 06 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/f23ff863-cc71-468e-b42c-e1aeffd0b174">
<img width="1437" alt="Screenshot 2024-04-18 at 11 06 16 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/c517b639-e18e-4363-8785-6752f2bc52b3">
<img width="1437" alt="Screenshot 2024-04-18 at 11 06 33 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/f1803291-cba1-4366-a8d3-ee8990282990">
<img width="1437" alt="Screenshot 2024-04-18 at 11 06 45 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/f540df7f-b17d-4c8a-9a64-0100d1e47ca5">
<img width="1437" alt="Screenshot 2024-04-18 at 11 06 54 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/5ba2db84-74eb-4e7f-bb6c-10abc27e881c">
<img width="1437" alt="Screenshot 2024-04-18 at 11 07 02 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/3499122e-9f55-4256-9800-c087e70cb5fc">
<img width="1437" alt="Screenshot 2024-04-18 at 11 07 09 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/d72e803c-7583-4d9a-a7fe-141040b3a7dc">

<hr>

<li><strong>Log Analysis</strong>
  <ul>
    <li>Access the log file generated by the PowerShell script.</li>
    <li>Analyze the log file to observe attempted login events.</li>
  </ul>
</li>
<img width="1437" alt="Screenshot 2024-04-18 at 10 03 44 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/4a1e4f20-481e-423c-99d5-ed144b683847">
<img width="1437" alt="Screenshot 2024-04-18 at 10 03 52 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/8554d61b-4a3b-4afa-a67c-748fe1f79c0f">
<img width="1437" alt="Screenshot 2024-04-18 at 10 04 09 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/13bcb5ba-a02a-4a24-ab89-546a3a1f9c35">

<hr>

<li><strong>Create Custom Log</strong>
  <ul>
    <li>Return to the Azure portal and navigate to Log Analytics Workspaces.</li>
    <li>Select your workspace and go to Tables &gt; Create &gt; New Custom Log (MMA-Based).</li>
    <li>Upload the sample log data from the VM to create a custom log in Azure.</li>
    <li>Specify the collection path (e.g., C:\ProgramData\failed_rdp.log) and create the custom log.</li>
  </ul>
</li>
<img width="1437" alt="Screenshot 2024-04-18 at 10 04 47 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/d0dd417c-247e-417c-af77-bab337b51687">
<img width="1322" alt="Screenshot 2024-04-18 at 10 07 06 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/4df7d596-a5c9-4641-ba6d-9e46a2d9eabf">

<hr>

  <li><strong>View Logs</strong>
  <ul>
    <li>Navigate to Log Analytics Workspaces &gt; Select your workspace &gt; Logs.</li>
    <li>Search for the custom log you created (e.g., FAILED_RDP_WITH_GEO).</li>
    <li>Wait for logs to generate (may take 20-40 minutes) and run the query again if needed.</li>
  </ul>
</li>
<img width="1437" alt="Screenshot 2024-04-18 at 10 07 42 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/1591e3a1-9a8a-4c94-8b9e-795576a793b4">
<img width="1437" alt="Screenshot 2024-04-18 at 10 07 48 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/3dd3d5b9-3846-45fc-876c-7437bf920906">
<img width="1437" alt="Screenshot 2024-04-18 at 10 08 12 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/1865217d-44c9-401f-98e4-5ef0b32d338f">
<img width="1437" alt="Screenshot 2024-04-18 at 10 08 27 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/3d078039-2cca-432a-baa3-cf05e7981ac9">
<img width="1437" alt="Screenshot 2024-04-18 at 10 08 34 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/fdac3c75-bcbe-42f1-bf5a-a3ac4e01b5a6">
<img width="1437" alt="Screenshot 2024-04-18 at 10 09 58 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/12480f64-8ed8-453e-950e-4f28cd54ef0a">

<hr>

<li><strong>Extracting Custom Fields</strong>
  <ul>
    <li>After logs generate, examine the RawData field in the logs.</li>
    <li>Create custom fields to filter the raw data for analysis.</li>
    <li>Copy and paste the <a href="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/blob/main/Extract%20Log%20Query" target="_blank">query</a> to extract custom fields such as username, timestamp, latitude, longitude, and more.</li>
  </ul>
</li>
<img width="1437" alt="Screenshot 2024-04-18 at 10 11 13 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/97d13a7b-315d-4823-929f-d0d23e472ef7">

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
<img width="1437" alt="Screenshot 2024-04-18 at 10 12 00 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/3c14994c-0bed-4297-a388-9582c6e7082d">
<img width="1437" alt="Screenshot 2024-04-18 at 10 12 29 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/cccad58c-7ad0-436f-a37e-82a2baa3d15e">
<img width="1437" alt="Screenshot 2024-04-18 at 10 12 40 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/b6e3a5e3-74e6-4de5-b07c-db0e368a6480">
<img width="1437" alt="Screenshot 2024-04-18 at 10 12 58 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/ce6b2784-3ca8-40fd-bd92-397ba86fc17f">
<img width="1437" alt="Screenshot 2024-04-18 at 10 13 22 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/65d36da4-b092-4550-b92c-5f9ffa4a9a58">
<img width="1437" alt="Screenshot 2024-04-18 at 10 13 54 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/cb265d24-a6f8-4390-9705-1f6f9b79f3c8">

<hr>

<li><strong>Monitor Attacks</strong>
  <ul>
    <li>Leave the VM running to monitor and analyze brute force login attempts. The longer the better. Below is a screenshot from Josh Madakors and as you can see the longer you leave the honeypot the more attempts will be made from around the world.</li>
    <li>Observe Azure Sentinel for alerts and visualizations of attempted logins on the map.</li>
  </ul>
</li>
<img width="1437" alt="Screenshot 2024-04-18 at 11 15 45 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/a1cf81a2-08cc-49fb-a252-5061eec2b36f">

<hr>

<li><strong>Cleanup</strong>
  <ul>
    <li>Upon completing the project, delete the resource group to avoid additional charges.</li>
    <li>Navigate to the resource group in the Azure portal and select Delete.</li>
    <li>Confirm the deletion to clean up all resources associated with the project.</li>
  </ul>
</li>
<img width="1437" alt="Screenshot 2024-04-18 at 11 07 56 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/5dc452ff-c045-453f-b4d5-e8c3b4052f9f">
<img width="1437" alt="Screenshot 2024-04-18 at 11 08 13 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/0c110f67-2cdd-4e57-9f58-48236f5c5614">
<img width="1437" alt="Screenshot 2024-04-18 at 11 08 17 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/2404d032-77a7-462c-a1ee-75265bafa928">

</ol>
