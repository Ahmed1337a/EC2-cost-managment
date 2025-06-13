# EC2-cost-managment
# Scenario: 
We’re optimizing our AWS storage costs by using a smart Lambda function, triggered on a schedule by Amazon EventBridge. This function regularly checks our EC2 instances and associated snapshots. If it finds a snapshot that isn’t linked to any active EC2 instance, it automatically deletes it. This automated process helps us eliminate unused storage and keep our AWS expenses under control.

   ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/b5dfcd169566815f8cc1186c76fdfec71199a88d/Images/diagram.png)


## Steps :
### Step 1:
1. Log into your AWS Console.
2. Navigate to the EC2 Console.
3. In the Instances section, select 'Instances,' and then click on 'Launch Instance'.
   ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/b5dfcd169566815f8cc1186c76fdfec71199a88d/Images/1.png)
   
4. Next, navigate to the 'Elastic Block Store' section and select 'Volumes'.
   
      ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/b5dfcd169566815f8cc1186c76fdfec71199a88d/Images/2.png)

5. You will notice that a default volume has already been created for us.
6. Next, click on 'Snapshots,' and then click the 'Create Snapshot' button. It will prompt you with a page that looks like this.
   
   ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/b5dfcd169566815f8cc1186c76fdfec71199a88d/Images/3.png)

### Step 2 :
1.Navigate to the IAM Console.
2.Navigate policies section to create a new policy.
3.Select the service as 'EC2
4. In the 'Actions' section, grant permissions for the following actions:
    DescribeInstances, DescribeVolumes, DescribeSnapshots, DeleteSnapshots.
5. create IAM role from that policy

   ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/b5dfcd169566815f8cc1186c76fdfec71199a88d/Images/5.png)
### Step 3:
1. After creating a Snapshot, navigate to the Lambda Console.

2. You will see some options in the user interface, such as 'Create Function'.

3. Click on 'Functions'.

   ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/b5dfcd169566815f8cc1186c76fdfec71199a88d/Images/4.png)
   
4. Select 'Author from Scratch,' then enter the Function name, and choose the latest Python version.

5. Scroll down and click 'Create Function'.

6.After creating the function, scroll down, and you will see something like the image below.

   ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/aa87899f34f39bf610778d48368212e4a5a69f21/Images/13.png)
   
 7. Click on the 'Code' section.

8. Next, clear the existing code and replace it with the 'identify_stale_snapshots.py' code.

9. Click 'Deploy' to save your changes, and then click 'Test.'
    
### Step 4 :

1. You can terminate the EC2 instance to test our Lambda function.

2. Navigate to the EC2 console and then terminate the EC2 instance.

3. Return to the Lambda console to test the code; go to the Lambda Function page.

4. Under the Code section, click 'Test code', it will display an output like this.

5. As expected, our Lambda function deleted the snapshot because it was associated with a volume that couldn't be found.
   
## Additional notes:
We can use CloudWatch to automatically trigger the Lambda function every hour, day, minute, or second. However, this may result in higher costs because our Lambda execution time increases when triggered automatically. Nevertheless, manually triggering this function is a better choice because it allows us to trigger it when needed.

### Steps :

1. Navigate to CloudWatch Console.

2.Navigate to Rules

3.Create Role

   ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/b5dfcd169566815f8cc1186c76fdfec71199a88d/Images/6.png)

4.click Continue in event bridge scheduler

5.Next, on the following page, configure the schedule pattern as follows:

   ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/b5dfcd169566815f8cc1186c76fdfec71199a88d/Images/7.png)
   
6.Scroll Down and then Click Next.

   ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/b5dfcd169566815f8cc1186c76fdfec71199a88d/Images/8.png)

7.Scroll Down and then Click Next.

8. On the next page, choose 'None' for the 'Action after Schedule'
   ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/b5dfcd169566815f8cc1186c76fdfec71199a88d/Images/9.png)

 ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/b5dfcd169566815f8cc1186c76fdfec71199a88d/Images/10.png)
 
   ![image](https://github.com/Ahmed1337a/EC2-cost-managment/blob/b5dfcd169566815f8cc1186c76fdfec71199a88d/Images/11.png)

9.You have successfully created the scheduler, which will trigger the Lambda function every hour.

10. However, please note that this setup will incur some costs since the function is triggered continuously every hour. Alternatively, we can configure it to run on specific days and times as needed.







   

   

   




   

      
      


   
   


   















