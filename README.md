<h1>Created a web-server on AWS EC2 instance using Terraform and user data</h1>


<h2>Description</h2>
I detail all the steps required to create a bare-bone web server on AWS EC2. I discuss from creating the VPC, subnets, internet gateway, security group, and EC2 instances to finally automating the process via Terraform and user data.
<br />


<h2>Environments Used </h2>

- <b>AWS EC2</b>
- <b>Terraform</b> 

<h2>Walk-through:</h2>

<p align="center">
Step 1: Create the network components: <br/>
<img src="https://i.imgur.com/0pGJSbk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Step 2: Create a security group:  <br/>
<img src="https://i.imgur.com/obitj2n.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
Since this was a proof of concept and since I did not require HTTPS traffic, I did not bother to create more than what was necessary. 
<br />
<br />
Step 3: Create the user data file <br/>
<img src="https://i.imgur.com/wUw1inz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Step 4: Create an AWS EC2 instance with a user data file  <br/>
<img src="https://i.imgur.com/kx1zrzJ.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<br />
<br />
With all the above code, I ran the usual Terraform commands of terraform apply (after initializing the repository). And after Terraform provisioned the resources, I received the message below. That is due to the specification in the output block (in the output.tf file):  <br/>
<img src="https://i.imgur.com/SMZ1mVl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Since I did not install a certificate on the EC2 instances, HTTPS was not going to work, and I tried the HTTP URL, which was HTTP://$(the public DNS provided in the output) And this is what I saw for all the three public DNS addresses: <br/>
<img src="https://i.imgur.com/zmoLvvz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/81CWREt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/KqhdCz2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The “Not secure” right before the public DNS name denotes that this is an HTTP URL.  <br/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
