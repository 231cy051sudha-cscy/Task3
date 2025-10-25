# Task3
IN my  windows 7  using virtual machine through implementing kali linux operating system to perform the Perform a Basic Vulnerability Scan .
First we update the kali linux and upgrade it 
linux command : 
1. sudo apt update && sudo apt upgrade
2. sudo apt install gvm -y
This installs GVM and its dependencies, including the scanner, manager, and web interface.
3. sudo gvm-setup
set Up GVM - Run the automatic setup script to configure databases, users:
4. gvm-check-setup
It should say your installation is OK. If not, rerun sudo gvm-setup
5. sudo gvm-start
This launches the web interface and background processes.
6. Set Up Scan Target as Your Local Machine IP or Localhost
Access the GVM web interface:
7. Open a browser in your Kali VM (Firefox) and go to https://127.0.0.1:9392.
8. Create a Scan Target for Your Windows Host (10.125.165.33)
A "target" defines what system(s) you want to scan. We will  create one specifically for your Windows host.
Steps:
Navigate to Targets:
In the left sidebar, click Configuration > Targets
Or use the top menu: Configuration > Targets
You will  see a list of existing targets (likely empty) and a New Target button (star icon) in the top-left.
Create New Target:
Click the star icon (New Target) or + button
Fill in the target configuration:
1. Name: Windows Host Scan (or any descriptive name)
2. Comment: Scanning Windows PC at 10.125.165.33 (optional)
3. Hosts: Enter 10.125.165.33 (your Windows host IP)
4. Port List: Select "All TCP and UDP" from the dropdown (comprehensive scan)

Allow Simultaneous Scans: Check this box (allows multiple scans if needed)
Alive Tests: Select "Ping Hosts" (verifies the target is reachable)
Max Hosts: Leave as 10 (default, fine for single host)
Max Checks: Leave as 4 (default)
Advanced Settings :
Scroll down to Snmp Credentials and Login Credentials sections
For basic scan: Leave empty (unauthenticated scan)
For authenticated scan (more accurate, requires Windows setup):
SMB Credentials: Add Windows username/password for deeper scanning

Save the Target:
Click Save at the bottom
Your target "Windows Host Scan" should now appear in the targets list

Test Target Connectivity:
From Kali terminal, verify you can reach the Windows host:
ping 10.125.165.33
If ping fails:
Check Windows Firewall: Allow ICMP (or temporarily disable firewall)

Create and Configure a Scan Task
A "task" defines how and when to scan the target using specific vulnerability tests.
Steps:

Navigate to Tasks:

Left sidebar: Scans > Tasks
Or top menu: Scans > Tasks


Create New Task:

Click the wand icon (New Task) or + button
Configure the task:

Name: Windows Host Full Vulnerability Scan
Comment: Full scan of Windows PC for vulnerabilities (optional)
Target: Select "Windows Host Scan" from the dropdown
Scanners: Should auto-select "OpenVAS Default"
Scan Config: Choose "Full and fast"

This tests thousands of vulnerabilities (NVTs) comprehensively
Alternatives: "Base" (quick overview), "Full and very deep" (thorough but slow)

Alert: Leave default or create notifications (optional)
Schedule: Leave as "Run once" for now
Preferences: Leave default for basic scan

Save the Task:
Click Save
Your task appears in the tasks list.

4. Start the Vulnerability Scan
