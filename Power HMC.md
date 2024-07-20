The Hardware Management Console (HMC) is a hardware appliance that you can use to configure and control one or more managed systems. You can use the HMC to create and manage logical partitions and activate Capacity Upgrade on Demand. Using service applications, the HMC communicates with managed systems to detect, consolidate, and send information to service and support for analysis.

The HMC also provides terminal emulation for the logical partitions on your managed system. You can connect to logical partitions from the HMC itself, or you can set up the HMC so that you can connect to logical partitions remotely through the HMC. HMC terminal emulation provides a dependable connection that you can use if no other terminal device is connected or operational. HMC terminal emulation is useful during initial system setup before you configure your terminal of choice If you use a single HMC to manage a server, and the HMC malfunctions or becomes disconnected from the server firmware, then the server continues to run, but you cannot change the logical partition configuration of the server. If required, you can attach an extra HMC to act as a backup and to provide a redundant path between the server and service and support.

The PowerVM NovaLink architecture enables management of highly scalable cloud deployment by using the PowerVM technology and OpenStack solutions. The architecture provides a direct OpenStack connection to a PowerVM server. The NovaLink partition runs the Linux® operating system and the partition runs on a server that is virtualized by PowerVM. The server is managed by PowerVC or other OpenStack solutions.

For more information, refer to https://www.ibm.com/docs/en/power10/000V-HMC. 

For details on commands provided by HMC, refer to https://www.ibm.com/docs/en/power10/000V-HMC?topic=appliance-hmc-commands

To create a logical partition using HMC CLI, use mksyscfg command and specify name, lpar env. An example would be mksyscfg -r lpar -m system1 -i "name=aix_lpar2,profile_name=prof1,
lpar_env=aixlinux,min_mem=256,desired_mem=1024,max_mem=1024,proc_mode=ded,min_procs=1,desired_procs=1,max_procs=2,sharing_mode=share_idle_procs,auto_start=1,boot_mode=norm,lpar_io_pool_ids=3,\"io_slots=21010003/3/1,21030003//0\",max_virtual_slots=20,\"virtual_fc_adapters=10/client/1//110//1,\"\"11/client/2//111/c0507609a405005a,c0507609a405005b/1\"\"\"". More examples can be seen at https://www.ibm.com/docs/en/power10/000V-HMC?topic=commands-mksyscfg. 

To list HMC version, use lshmc -V command. More examples can be seen at https://www.ibm.com/docs/en/power10/000V-HMC?topic=commands-lshmc

The command `lshmc -h` provides the RAID information and status in power Hardware management console

Using command chhmc, HMC can be configured as DHCP server. Examples at https://www.ibm.com/docs/en/power10/000V-HMC?topic=commands-chhmc

HMC is offered as a Physical Hardware appliance and a Virtual Appliance. Virtual Appliance is supported on VMWare, KVM, Xen Hypervisors. 

HMC also handles service management and handles different SRCs. SRCs like E212E114 which is for high memory usage.



To list systems mamaged by a Power HMC, use lssyscfg command. lssyscg -r sys lists the system details. For more examples, see https://www.ibm.com/docs/en/power10/000V-HMC?topic=commands-lssyscfg

To change system state or lpar state, chsysstate command can be used. chsysstate -r sys -o on -m <managed system> is an example to power on a system. For more examples, see https://www.ibm.com/docs/en/power10/000V-HMC?topic=commands-chsysstate

The ‘lshmcusr -t user’ command will list the HMC users. More details can be found at https://www.ibm.com/docs/en/power10/000V-HMC?topic=commands-lshmcusr

Below are the power HMC information and the command

Display the HMC’s BIOS level:

lshmc -b

Display the preconfigured HMC DHCP server IP addresses, network masks, and ranges:

lshmc -D

Display the settings for the HMC’s Event Manager for Call Home:

lshmc -e

Display HMC hardware information:

lshmc -h

Display the HMC’s IMM settings:

lshmc -i

Display the HMC’s current locale:

lshmc -l

Display all locales supported by the HMC:

lshmc -L

Display the HMC’s network settings:

lshmc -n

Display the HMC’s host name and IP address, and separate the output values with a colon:

lshmc -n -F hostname:ipaddr

Display the HMC’s remote access settings:

lshmc -r

Display the HMC’s VPD information:

lshmc -v

Display the HMC’s version information:

lshmc -V

Display the HMC’s BMC settings:

lshmc --bmc

Display the firewall settings for the HMC:

lshmc --firewall

Display the network routing information for the HMC:

lshmc --netroute

Display HMC NTP server information:

lshmc --ntpserver

Display the syslog server configuration for the HMC:

lshmc --syslog 

List all HMC users:

lshmcusr

List only the user names and managed resource roles for all HMC users, and separate the output values with a colon:

lshmcusr -F name:resourcerole

List the HMC users hscroot and user1:

lshmcusr --filter names=hscroot,user1

List the HMC users with the task role hmcviewer and the managed resource role mr1:

lshmcusr --filter taskroles=hmcviewer,resourceroles=mr1

List the user-settable default values for HMC user attributes:

lshmcusr -t default 

Power on a managed system and auto start partitions if not a BMC managed system:

chsysstate -m 9406-520*10110CA -r sys -o on

Power on a managed system with a system profile:

chsysstate -m sys1 -r sys -o onsysprof -f mySysProf

Power off a managed system normally:

chsysstate -m sys1 -r sys -o off

Power off a managed system fast:

chsysstate -m sys1 -r sys -o off --immed

Restart a managed system:

chsysstate -m 9406-570*12345678 -r sys -o off --immed
--restart

Rebuild a managed system:

chsysstate -m 9406-570*12345678 -r sys -o rebuild

Recover partition data for a managed system:

chsysstate -m sys1 -r sys -o recover

Initiate service processor failover for a managed system:

chsysstate -m myServer -r sys -o spfailover

Set the keylock position for a managed system:

chsysstate -m sys1 -r sys -o chkey -k manual

Activate IBM i partition p1 using partition profile p1_prof1 and IPL source b:

chsysstate -m sys1 -r lpar -o on -n p1 -f p1_prof1 -i b

Activate partitions p1, p2, and p3 with their current configurations:

chsysstate -m sys1 -r lpar -o on -n p1,p2,p3

Activate and perform a network install of the IBM i partition iLpar:

chsysstate -m mySys -r lpar -o on -n iLpar -f iProf -i d --ip 9.1.2.33
--netmask 255.255.255.0 --gateway 9.1.0.1 --serverip 9.5.12.34
--serverdir /IBMi/611

Shut down the partition with ID 1:

chsysstate -m 9406-570*12345678 -r lpar -o shutdown --id 1

Issue the operating system shutdown command to immediately shut down the partition p1:

chsysstate -m 9406-570*12345678 -r lpar -o osshutdown
-n p1 --immed

Issue the operating system shutdown command to shut down then restart the partition p1:

chsysstate -m 9406-570*12345678 -r lpar -o osshutdown
-n p1 --restart

Immediately restart the partition with ID 1:

chsysstate -m 9406-570*12345678 -r lpar -o shutdown --id 1
--immed --restart

Enable a remote service session for the IBM i partition mylpar:

chsysstate -m sys1 -r lpar -o remotedston -n mylpar

Validate system profile sp1:

chsysstate -m sys1 -r sysprof -n sp1 --test

Validate then activate system profile sp1:

chsysstate -m sys1 -r sysprof -n sp1 -o on --test

Activate system profile mySysProf and continue activating remaining partitions if a partition activation failure occurs:

chsysstate -m 9406-570*12345678 -r sysprof -n mySysProf
-o on --continue

Rebuild a managed frame:

chsysstate -e myFrame -r frame -o rebuild 



Installing the HMC virtual appliance
Last Updated: 2023-04-18

Learn how to install the Hardware Management Console (HMC) virtual appliance.
The HMC virtual appliance can be installed in your existing x86 or POWER® virtualized infrastructure. The HMC virtual appliance supports the following x86 virtualization hypervisors:

    Kernel-based virtual machine (KVM)
    Xen
    VMware

The HMC virtual appliance supports the following POWER virtualization hypervisors:

    PowerVM®

Minimum requirements for running the HMC virtual appliance:

    16 GB of memory

    4 virtual processors

    2 network interfaces (maximum of 4 allowed)
    1 disk drive that contains 500 GB of available disk space

    
