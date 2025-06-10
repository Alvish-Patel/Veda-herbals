
# How to Place an EC2 Instance into Standby Mode in an AWS Auto Scaling Group

## Using the AWS Management Console

### Step 1: Open the Auto Scaling Groups Console
1. Log in to the [AWS Management Console](https://aws.amazon.com/console/).
2. Navigate to **EC2** > **Auto Scaling Groups** from the left-hand menu.
   
  ![Project Screenshot](https://github.com/Awesome-SRE-Playground/EC2-Auto-Scaling-Group/blob/master/Images/4.png)

### Step 2: Locate Your Auto Scaling Group
1. From the list of ASGs, locate and click on the name of the Auto Scaling Group you want to modify.
2. Under the **Instances** tab, find the instance that you want to move to standby.'   

### Step 3: Place the Instance into Standby
1. Select the instance you wish to put on standby.
2. Click on the **Actions** drop-down menu.
3. Choose **Instance Standby**.
4. Confirm your action in the dialog box.
   - **With decrement**: The desired capacity will be reduced by one.
   - **Without decrement**: ASG retains its desired capacity and may launch a replacement.
  

### Step 4: Verify the Status
1. Once the action is complete, the instance’s status will change to **Standby**.
2. Monitor the ASG details to ensure that the instance has been successfully removed from the active pool.

  ![Project Screenshot](https://github.com/Awesome-SRE-Playground/EC2-Auto-Scaling-Group/blob/master/Images/Screenshot%20from%202025-06-10%2023-21-49.png)

---

## Using the AWS CLI

### Step 1: Identify the Instance and ASG
Ensure you have the **Instance ID** and the **Auto Scaling Group Name**.

### Step 2: Execute the CLI Command
```sh
aws autoscaling enter-standby \
  --instance-ids i-0123456789abcdef0 \
  --auto-scaling-group-name my-asg \
  --should-decrement-desired-capacity
```

### Step 3: Verify the Result
```sh
aws autoscaling describe-auto-scaling-groups --auto-scaling-group-names my-asg
```
Look for the **Standby** state in the instance details.

---
