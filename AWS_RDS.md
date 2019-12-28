# Failover
- In Amazon RDS, failover is automatically handled so that you can resume database operations as quickly as possible without administrative intervention in the event that your primary database instance went down.
- When failing over, Amazon RDS simply flips the canonical name record (CNAME) for your DB instance to point at the standby, which is in turn promoted to become the new primary. 

![image](https://user-images.githubusercontent.com/5827617/71541165-10180980-2998-11ea-9ea4-494f1ff0d348.png)

--- 

# Multi-AZ deployments VS Read Replicas

![image](https://user-images.githubusercontent.com/5827617/71459722-21241780-27ec-11ea-9a03-d4a553da0974.png)
