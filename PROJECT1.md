# <ins>WEB STACK IMPLEMENTATION IN AWS</ins> 
## Linux, Apache, MySQL, PHP - LAMP STACK
Welcome to my first project! In this project, I will be exploring the use of technology stack to create different solutions possible to deploy our applications, websites etc. A technology stack is a set of frameworks and tools used to develop a software product. They are specifically chosen to work together in creating a well-functioning software.
The fuctionality of the Stack is hereby listed as:

| STACK | FUNCTION |
| - | - |
| Linux | Operating Sysytem |
| Apache| Web Server |
| MySQL | Database |
| PHP | Programing Language |

---
Before I get into the fundamentals, I created an AWS account and also created a IAM User for the account. It is best practice to access the AWS account as a user rather than accessing it as a root user. 


![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/iamuser1.jpg)


![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/iamuser.jpg)

AWS service for hosting a virtual machine is the Elastic Compute Cloud (ECS). I am going to create an EC2 instance to host our VM which will run Ubuntu (Linux 
Distribution). Before proceeding with the creation of an EC2 instance, Select the desired and closest region to you. the following are the factors to consider before deciding the AWS region to choose:

* Latency and proximity

* Security and regulatory compliance

* Service Level Agreements (SLA)

And finally, the most important is the **Cost**

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/region.jpg)
---

**Click on Services, Compute then select EC2.**

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC2.jpg)
---

**Scroll down, click Lauch Instances and name your new instance.**

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC21.jpg)
---

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC22.jpg)
---

**Ubuntu Server 22.04, t2.micro family type is selected to run on the instance.**

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC23.jpg)
---

**Next, a key pair is created to enable secure connection to the instance. The private key (.pem) should be saved securely to prevent unauthorized access to the server.**

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC24.jpg)
---

Next, I configured the network setting by creating a new segurity group that will act as firewall to control traffic in and out of our instance. For me to be be able to access the instance from my windows computer and from the internet, I need to enable SSHport 22 and HTTP port 80. To do this, I created inbound rules for the ports. Because my computer runs on Windows, I will need to download and install an ssh client to establish conectivity with the instance. For this project, I will install Mobarxterm.
**Note** - EC2 has created a default Virtual Private Cloud (VPC) where the instance server is situated which means both public and private IPs have been authomatically generated for the instance. I will leave the root storage setting as default for the purpose of this project. We can go ahead and launch the new instance!

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/sg.jpg)
---
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/sg1.jpg)
---

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/instance.jpg)
---

![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/instance1.jpg)

