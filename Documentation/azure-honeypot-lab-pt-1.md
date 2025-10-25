Azure Honeypot Lab - Pt. 1

Deploying T-Pot in Azure
In this lab we will deploy T-Pot, an all in one honeypot platform developed by Deutsche Telekom within Microsoft Azure cloud.

But first, let's break down what a honeypot actually is

What is a Honeypot?
A honeypot can be described as a system designed to appear vulnerable and enticing to potential attackers. It allows security professionals to observe and analyze the tactics, techniques, and procedures (TTPs) of cybercriminals without exposing critical data on the actual network.

This lab will demonstrate how to deploy a honeypot in an isolated environment within Azure, minimizing the risk to your internal network.

Understanding T-Pot
T-Pot is a versatile honeypot platform that offers a robust set of features for effective threat detection and analysis. Features include:

Modular Architecture: Enables customization, allowing admins to deploy and manage a tailored selection of honeypot services based on specific threat intelligence and organizational needs

Centralized Management: T-Pot provides a centralized management interface, simplifying the administration and monitoring of multiple honeypot deployments across various environments.

Comprehensive Honey Services: T-Pot integrates a diverse range of honeypot services, including network-based, system-based, and database honeypots, to attract and capture a wide spectrum of cyber threats.

Real-time Threat Intelligence: T-Pot leverages real-time threat intelligence from various sources, including honeypot interactions and external threat feeds, to provide valuable insights into emerging threats and attacker behavior.

Integration Capabilities: T-Pot can be integrated with Security Information and Event Management (SIEM) systems and other security tools, enabling comprehensive threat correlation and incident response.

T-Pot Architecture
So how does T-pot actually work? Below is a simplified illustration of T-Pot's anatomy.

tpot_architecture.png

T-Pot's Foundation: T-Pot is built on a super flexible base called Docker, which runs on top of the Linux Kernel. Think of Docker as a way to package up all the different parts of T-Pot into neat little containers. This makes it super easy to set up and manage.

The Honeypot Army: T-Pot has a whole army of honeypots, like the ones you see in the picture, each one specialized in catching different kinds of hackers.

The Command Center: Now, we need a way to manage all these honeypots, right? That's where the ELK Stack comes in.

Elasticsearch: This is like the brains of the operation, storing all the data collected by the honeypots.

Logstash: This is the data wrangler, organizing and preparing the data for storage.

Kibana: This is your dashboard, giving you a cool visual way to see what's happening on your honeypots and analyze the data.

Accessing T-Pot: You can access T-Pot securely using SSH or HTTPS, this will allow you to monitor and manage your honeypot deployment remotely.

Pre-requisites:
If this is all new to you but not afraid to get your hands dirty, I highly recommend to have a basic understanding of the following to get the most out of this lab:

Network Services
Network Ports
Basic Linux Commands
Honeypot




T-Pot source link: https://github.com/telekom-security/tpotce
Azure Deployment
To follow along with this lab, you'll need an Azure subscription. If you're new to Azure or a student, you might be eligible for free credits.

Important Note: Running a honeypot can incur costs, especially if it's running for an extended period. Make sure to delete after you're done using. Simply visit Resource Group page, select your resource group and you will see the delete option in the pop up window.

Creating Virtual Machine
Let's begin with creating a Virtual Machine

In the Azure Dashboard Portal, click the "Virtual machines" icon or you may search and select it using the search bar

az-vm01

In the Virtual Machines page, click the "Create" button and select "Azure Virtual Machines

az-vm02

Here we will configure the VM, match the input fields with the ones shown in the picture below

For Resource Group, select "Create New" and type in the RG name

Select the Region that Is best for you geographically

Since this is a lab, there won't be a need for redundancy or strict security

az-vm03

For the Authentication Type we will use a password, feel free to make your own or use the following:

Username: labuser Password: Cyberlab123!

We will use the same credentials throughout the lab.

When finished, click "Next"

az-vm04

We will increase the OS disk size to 128gb

click "Next"

Pasted image

This section will create a Virtual Network for our virtual machine.

We can leave the default settings, no changes necessary

From here we can skip the next couple of tags as we won't be needing those features for this lab. click "Review + Create"

Pasted image

Once it has been validated, you may select "Create" to deploy the VM

Pasted image

You'll be redirected here you will see the deployment in progress, give it a few minutes until it has been completed

Pasted image

Pasted image

Making our VM Accessible
Now that we've successfully created our VM, we need to allow it to communicate with the outside world so that it can act as a honeypot.

T-Pot documentation lists specific ports that need to be open for optimal functionality. However, for the purpose of this lab, we'll create a simplified rule that allows all traffic to reach our VM.

Please note: In a real-world scenario, you would never open all ports on a production server. This is a security risk and should only be done in controlled lab environments.

Navigate to the virtual machines page, and select TPOT-VM-01

Look for the Networking blade on the left side panel, then select "Network Settings"

Take note of your VM's Public IP address, we will use this to connect to our VM

You may need to scroll down a bit to view the Network Security Group. This is a fundamental security perimeter that controls network traffic to or from our VM.

Click "Create port rule" button on the right side and select "Inbound port rule"

Pasted image

As previously mentioned, we are allowing anyone from the outside to communicate with our Honeypot through any port

Match the input fields, be sure to type the proper port range

Click "add" when finished

Pasted image

Testing Connection
Now that we have created the new inbound rule, let's test the connection!

Lets open up Windows terminal

Search for terminal

Pasted image

I'm using Powershell, but you can use command prompt as well

we will test our connection using ssh, command is as follows:

ssh labuser@<your vm's public ip address>

Pasted image

You will be prompted for the password: Cyberlab123!

Pasted image

And we have a connection! Your directory path should have changed to "labuser@TPOT-VM-01:~$"

Pasted image

Installing T-Pot
Before we install T-Pot lets make sure our VM is up to date

Run command: sudo apt update && sudo apt upgrade -y

Pasted image

Once the update finishes, run the following command:

sudo apt install git

We will need this in order to clone the T-Pot codebase

Pasted image

we'll then grab the T-Pot codebase directly from GitHub. To do this, run the following command:

git clone https://github.com/telekom-security/tpotce

This will clone the T-PotCE repo onto your system

Pasted image

Pasted image

After the cloning is complete, let's verify that the T-Pot repository has been downloaded correctly. Use the following command to list the files and directories in your current working directory

ls

You should see a newly created directory named "tpotce." To enter this directory, use the following command:

Cd tpotce/

Now, list the contents of this directory again using the ls command. You should see various files and subdirectories related to the T-Pot installation

Pasted image

If you recall the T-Pot Architecture illustration, honeypots and related services should be inside the docker directory. Let's see what is included in the standard version

Run command: cd docker/ followed by the ls command

You should now be able to view them. Feel free to search what each one does.

Pasted image

Now let's go back a file to tpotce/ . Simply type cd .. To go back one directory.

To install T-Pot we need to run the installation, run:

./install.sh --type-user

select Y for "yes"

Pasted image

You will then be prompted to select the T-Pot type

We will be using the T-Pot Standard version for that type in "h" as the option

Pasted image

you will be prompted to create a username and password, use the same credentials.

Pasted image

Installation is now completed. You will be prompted to reboot the machine. Run the following command

sudo reboot

Pasted image

Allow the machine time to reboot

Accessing Web Interface
After a few minutes, open up your web browser and type in your VM's public IP address ending with the port number ":64297"

https://<publicipaddress>:64297

It will show as non secured, depending on your browser you may select "advanced" or "proceed to.."

Pasted image

You will be prompted to sign-in, use the same credentials

Pasted image

You have successfully logged in to the T-Pot web interface.

To allow the honeypots to start capturing traffic and potentially detect some initial attacks, it is recommended to wait for a couple of hours after deployment. You might even observe some attack activity within the first hour.

You'll notice that you are welcomed with a couple of options, let's review them

Pasted image

Attack Map: Visualizes network activity and attack traffic captured by the honeypots. Displays connections, identifies attack sources and destinations, and helps track attack progression.

Pasted image

CyberChef: A versatile tool for data analysis and manipulation. Encodes/decodes data, analyzes network traffic, extracts information from encrypted data, and visualizes data in various formats.

Pasted image

Elasticvue: A user-friendly interface for interacting with Elasticsearch. Simplifies querying, analyzing, and managing data stored in Elasticsearch.

NOTE: You will need to first "Add an Elasticsearch cluster" and then click "Connect". You may need to enter credentials used in T-pot login

Pasted image

Kibana: The primary data visualization and exploration tool. Creates dashboards, charts, and graphs to analyze attack trends, identify patterns, and gain insights into attacker behavior. Offers advanced search and alerting capabilities.

Pasted image

SpiderFoot: An open-source intelligence (OSINT) gathering tool. Collects information about individuals, organizations, and domains from public sources to enrich threat intelligence and understand the context of observed attacks.

Pasted image

Conclusion
Congratulations! You've successfully deployed your first honeypot in Azure using the T-Pot platform. Through this lab, you've gained a foundational understanding of honeypots, including their purpose, functionality, and architecture.

In the next part of this series, we'll dive deeper into the tools and capabilities of T-Pot. We'll explore each honeypot service in detail, analyze the types of attacks we're seeing, and gain valuable insights into the tactics, techniques, and procedures (TTPs) of cybercriminals.
