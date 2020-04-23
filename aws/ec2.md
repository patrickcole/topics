# AWS EC2

- AWS: secure cloud services platform
- 69 zones all around the world
- Amazon Elastic Compute Cloud (EC2)
- provides a "virtual cluster of computers" (A.Reddy - Dev.to)
- "where the compute power lives" (J. Rowe - Freecodecamp.org)
- web service that gives developers the ability to run applications using virtual servers on AWS
- some advantages:
  - scalability
  - easy to maintain
  - flexible
  - reliable
  - secure
  - affordable
  - low learning curve
  - well developed and integrated solution into AWS

- to get started, developers choose what type of instance they wish to use
- memory and network configuration options are available along with a list of operating systems to choose from
- billing is done on hourly bases
- additional services such as Elastic IP aka a static ip address can be added to the ec2 instance
- domain registration can also be applied to an instance via AWS' Route 53

- security groups are essential to get everything configured properly on EC2 instances
- this includes not only SSH access but HTTP traffic on port 80
- these groups are configured explicitly so no surprises exist!

- the concept of using SSH keys or key pairs are crucial to cloud development
- it is recommended to properly name them so each can easily be distinguished from another if you are going to be conducting lots of cloud devlopment (J. Rowe - freecodecamp.org)

- virtual private cloud (VPC)
- thought of as the entire development infrastructure for your aws account

- ec2 instances can be launched from either the web interface or the `aws-cli` package

## Tags

- providing tags will help assist you as you develop your instances and any additional cloud development
- for example, providing a tag for the application name, can be useful to help set it apart from other apps in your vpc
- 

- here's a great [guide](https://dev.to/anudeepreddy/get-started-with-aws-ec2-ejg#creating-your-own-ec2-instance) on getting up and running with AWS EC2

## Sources

- [Get started with AWS EC2](https://dev.to/anudeepreddy/get-started-with-aws-ec2-ejg)
- [How to Spin Up a Remote Server on AWS](https://www.freecodecamp.org/news/getting-started-with-server-administration-on-aws/)
  - the link above doesn't really show how to actually update, it assumes you know how to ssh and make your updates, but the bigger takeaway is it's another great resource for how to spin up EC2 instances
