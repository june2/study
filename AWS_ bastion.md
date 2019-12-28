# AWS Bastion
 - A bastion host is a special purpose computer on a network specifically designed and configured to withstand attacks. 
 - If you have a bastion host in AWS, it is basically just an EC2 instance. 
 - It should be in a public subnet with either a public or Elastic IP address with sufficient RDP or SSH access defined in the security group. 
 - Users log on to the bastion host via SSH or RDP and then use that session to manage other hosts in the private subnets. 
 
 ![image](https://user-images.githubusercontent.com/5827617/71541050-6e43ed00-2996-11ea-80cb-8acee2e4c28a.png)
