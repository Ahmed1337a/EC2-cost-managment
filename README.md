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

   















