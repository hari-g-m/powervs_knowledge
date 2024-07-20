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


