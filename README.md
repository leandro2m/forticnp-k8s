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
</ul>
