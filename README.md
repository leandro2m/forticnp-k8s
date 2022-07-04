<h1>Workshop FortiCNP - EKS Use Case </h1>

<h3>About</h3>
<p>
The main purpose of this project is to create an EKS cluster with a flaw application to explore some vulnerabilities and see how FortiCNP can support you during your cloud security operation. 
</p>
<p><strong> FortiCNP </strong> is a new Fortinet Cloud Native Protection product that is designed to help you address today’s cloud security needs by integrating with Cloud Native Security services as well as Fortinet Security Fabric products.</p>

<h3>Resources</h3>
<p>The following  resources will be deployed into your AWS account:</p>


<strong>VPC</strong>
* 1 x VPC
* 4 x Subnets. 2 Publics and 2 Privates
* 2 x Route Tables
* 1 x Nat Gateway
* 1 x IGW

<strong>EKS Cluster</strong>
* 1 EKS Cluster with a single WorkerNode

<strong> IAM </strong>
* IAM User for EKS Cluster management

<strong> Bastion EC2 Instance </strong>
* 1x EC2 Instance for EKS cluster api access/management


<h3>Use Case</h3>

<p>In this use case, we will discuss the risks of the AWS Instance Metadata service in AWS Elastic Kubernetes Service (EKS) clusters. We will demonstrate that deploying a flaw application with misconfiguration of AWS resources such as IAM policies can have disastrous consequences in the AWS account.</p>
<p><a href=https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html> Instance Metadata service </a> is an AWS API listening on a link-local IP address, 169.254.169.254. It is only accessible from EC2 instances and allows to retrieve many information about them.</p>

<h3>Deploy AWS Resources</h3>
<p>Follow the deployment process below to deploy EKS cluster in your AWS Account </p>
<ul>
<li>1. Deploy the cloudformation template Activate_AWSQS_extentation.yaml</li>
<li>2. Deploy the cloudformation template EKS.yaml</li>
It will take around 20 minutes to complete.
</ul>

<h3>Deploy Application</h3>
<p>Follow the  process below to deploy a flaw application on top of EKS</p>
<ul>
<li>1. Connect to an EC2 Bastion host created. If you have Key Pair you can use it to connect through SSH. If not, use Connect button available in the console</li>
<li>2. Open the folder forticnp-k8s/application available in the root path.</li>
<li>3. Deploy the application with the following command.
kubectl create -f deployment_k8s_attack.yaml
</li>
<li>4. Deploy the service to expose the application with the following command.
kubectl create -f service_k8s_attack.yaml
</li>
</ul>

<h3>Accessing the Instance Metadata service from a compromised pod</h3>
<ul>
<li>1. Open the application URL. Get the URL with the command below.
<p> kubectl get svc service-k8s-attack</p>
<img src='/get_service.PNG'>
</li>
<li>2. Launch http://your_url_service:8080.
<img src='/home_page.PNG'>


</li>
<li>3. You can explore Instance Metadata. Copy and paste the command below in the form that will return informations about the EKS WorkerNode
curl http://169.254.169.254/meta-data/iam/
</li>
</ul>