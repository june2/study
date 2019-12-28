# AWS Glacier

-  Amazon Glacier is an extremely low-cost storage service that provides secure, durable, and flexible storage for data backup and archival. Amazon Glacier is designed to store data that is infrequently accessed. Amazon Glacier enables customers to offload the administrative burdens of operating and scaling storage to AWS so that they don’t have to worry about capacity planning, hardware provisioning, data replication, hardware failure detection and repair, or time-consuming hardware migrations.

- It is advisable to transition the standard data to infrequent access first then transition it to Amazon Glacier. You can specify in the lifecycle rule the time it will sit in standard tier and infrequent access. You can also delete the objects after a certain amount of time.


![image](https://user-images.githubusercontent.com/5827617/71541108-0f32a800-2997-11ea-88e0-d4d402cefde0.png)




- In transitioning S3 standard to Glacier you need to tell S3 which objects are to be archived to the new Glacier storage option, and under what conditions. 
- You do this by setting up a lifecycle rule using the following elements:
   - A prefix to specify which objects in the bucket are subject to the policy.
   - A relative or absolute time specifier and a time period for transitioning objects to Glacier. The time periods are interpreted with respect to the object’s creation date. They can be relative (migrate items that are older than a certain number of days) or absolute (migrate items on a specific date)
   - An object age at which the object will be deleted from S3. This is measured from the original PUT of the object into the service, and the clock is not reset by a transition to Glacier.
