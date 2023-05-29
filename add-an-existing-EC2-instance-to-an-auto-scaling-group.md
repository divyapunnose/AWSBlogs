# How to add an existing EC2 instance to an autoscaling group
The following steps has to be followed to add an existing EC2 instace to an autoscaling group.

### Create the AMI of the existing instance.
Go to Instances >> Choose the instance >> Actions >> Image and Templates >> Create Image.

 
### 2) Create a Launch Configuration
From AWS Management Console >> AutoScaling Group >> Launch Configuration.
Create the Launch Configuration using the previously created AMI of the instance. This AMI will be present under the MyAMI option while creating the Launch Configuration.
 
3) Create the Auto Scaling Group
Goto Auto Scaling >> Auto Scaling Groups >> Create Auto Scaling Group.
Here, we are using Launch Configuration to create the Auto Scaling Group. So, 	click on the "Switch to Launch Configiration option and choose the lauch configuration we have created.
  
Choose the VPC and the required Availability Zones and subnets. We are using default VPC here. Make sure that the VPC and the Availability Zone are the same as that of the instance which is to be added in the Auto Scaling Group.
An important section in this configuration is the "Group size" option "Configure group size and scaling policies" section.
Desired capacity: Represents the initial capacity of the Auto Scaling group at the time of creation. An Auto Scaling group attempts to maintain the desired capacity. It starts by launching the number of instances that are specified for the desired capacity, and maintains this number of instances as long as there are no scaling policies or scheduled actions attached to the Auto Scaling group.
Minimum capacity: Represents the minimum group size. When scaling policies are set, an Auto Scaling group cannot decrease its desired capacity lower than the minimum size limit.
Maximum capacity: Represents the maximum group size. When scaling policies are set, an Auto Scaling group cannot increase its desired capacity higher than the maximum size limit.
In our case, we set the following values for the Group size
Desired capacity: 0
Minimum capacity: 0
Maximum capacity : 1
Setting this value will create an Auto Scaling Group without any instances in it.
 
4) Now we can go ahead and add the existing EC2 instance to the Auto Scaling Group. 
Go to EC2 section >> Instances >> Select the instance >> Attach to Auto Scaling group >> Select the mentioned Auto Scaling group.
Once this is done, the EC2 instance will be a part of the ASG. Now will you see that the value of Desired capacity of the ASG is 1 since an instance has been added to it. 
 
You can see the details  of the Auto Scaling Group and the instances from by going to the ASG.

 
The detailed logs regarding the activities of the ASG can be found from the Activity Tab
 




