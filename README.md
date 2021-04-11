# AWS Infrastructure as Code Networking Architecture
Udacity Cloud DevOps Engineer Nanodegree Program - Challenge AWS IaC Networking Architecture

## Project Overview
You have been tasked with creating the required Infrastructure-as-code scripts for a new cloud environment in AWS. The Lead Solutions Architect for the project sends you the following diagram.

## Architecture
![Architecture](https://video.udacity-data.com/topher/2021/February/602bb312_screenshot-2021-02-16-at-5.24.30-pm/screenshot-2021-02-16-at-5.24.30-pm.png)

## ToDo
Write a CloudFormation script that:

  - Creates a VPC
    - It will accept the IP Range -also known as CIDR block- from an input parameter
  - Creates and attaches an Internet Gateway to the VPC
  - Creates Two Subnets within the VPC with Name Tags to call them “Public” and “Private”
    - These will also need input parameters for their ranges, just like the VPC.
  - The Subnet called “Public” needs to have a NAT Gateway deployed in it
    - This will require you to allocate an Elastic IP that you can then use to assign it to the NAT Gateway.
  - The Public Subnet needs to have the MapPublicIpOnLaunch property set to true. Use this reference for help.
  - The Private Subnet needs to have the MapPublicIpOnLaunch property set to false.
  - Both subnets need to be /24 in size.
    - If you need assistance with IP math, you can use a subnet calculator such as this one.
  - You will need 2 Routing Tables, one named Public and the other one Private
  - Assign the Public and Private Subnets to their corresponding Routing table
  - Create a Route in the Public Route Table to send default traffic ( 0.0.0.0/0 ) to the Internet Gateway you created
  - Create a Route in the Private Route Table to send default traffic ( 0.0.0.0/0 ) to the NAT Gateway
  - Finally, once you execute this CloudFormation script, you should be able to delete it and create it again, over and over in a predictable and repeatable manner, this is the true verification of working Infrastructure-as-Code

## Setup

Create stack
```sh
aws cloudformation create-stack --stack-name udacity-challenge --template-body file://iac.yml --parameters file://parameters.json
```

Update stack
```sh
aws cloudformation update-stack --stack-name udacity-challenge --template-body file://iac.yml --parameters file://parameters.json
```
