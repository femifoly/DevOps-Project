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
----
**Click on Services, Compute then select EC2**
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC2.jpg)
---
**Scroll down, click Lauch Instances and name your new instance**
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC21.jpg)
---
![](https://github.com/femifoly/DevOps-Project/blob/main/Project%20Images/EC22.jpg)
---
**Ububtu Server 22.04, t2.micro family type is selected to run on the instance**
