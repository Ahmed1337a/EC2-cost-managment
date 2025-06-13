# EC2-cost-managment
# Scenario: 
We’re optimizing our AWS storage costs by using a smart Lambda function, triggered on a schedule by Amazon EventBridge. This function regularly checks our EC2 instances and associated snapshots. If it finds a snapshot that isn’t linked to any active EC2 instance, it automatically deletes it. This automated process helps us eliminate unused storage and keep our AWS expenses under control.

## Steps :
### Step 1:
1. Log into your AWS Console.<br>
2. Navigate to the EC2 Console.<br>
3. In the Instances section, select 'Instances,' and then click on 'Launch Instance'.<br>









