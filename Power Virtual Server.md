IBM® Power® Virtual Server is an IBM Power server offering. You can use the Power Virtual Server to deploy a virtual server, also known as a logical partition (LPAR), in a matter of minutes. You can provision flexible, secure, and scalable compute capacity for Power enterprise workloads both on IBM Power Virtual Server Private Cloud and Power Virtual Server in your data center.

You get fast and flexible management that can be connected to access a stack of enterprise services from IBM – all with pay-as-you-use billing. Using these services you can easily adjust workloads with flexible compute capacity. Power Virtual Server instances can be used across the IBM Cloud platform globally. You can quickly deploy a Power Virtual Server to meet your specific business needs and easily control workload demands. Avoid the large capital expenses or added risk when migrating your essential workloads and get started with Power Virtual Server today! For frequently asked questions about the Power Virtual Server, see FAQ.

Install or update the power-iaas plug-in.
ibmcloud plugin install power-iaas

The power-iaas command-line plug-in uses the region that ibmcloud login targets to determine the Power Virtual Server endpoint. For example, to use the Power Virtual Server endpoint https://cloud.ibm.com you must use the ibmcloud login -a https://cloud.ibm.com command to target the us-east region. If you have a federated account, use the following command:
ibmcloud login -a https://cloud.ibm.com -sso

Run the ibmcloud pi ws ls command to list all of the services under your account. The Cloud Resource Name (CRN) under ID contains your Tenant ID and Cloud Instance ID. The following example shows a typical CRN:
crn:v1:staging:public:power-iaas:us-east:a/abcdefghijklmnopqrstuvwxyzabcdef:121d5ee5-b87d-4a0e-86b8-aaff422135478::

Target your service by entering the following command, ibmcloud pi ws tg <CRN>.
ibmcloud pi ws tg crn:v1:staging:public:power-iaas:us-east:a/abcdefghijklmnopqrstuvwxyzabcdef:121d5ee5-b87d-4a0e-86b8-aaff422135478::

Power Systems Virtual Server CLI requires a valid IAM token authorization before each use. Use the ibmcloud login command to renew authorization if your token expires.



You can find more information on Power Virtual Server at https://cloud.ibm.com/docs/power-iaas
