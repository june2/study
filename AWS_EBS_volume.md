# AWS EBS
- An Amazon EBS volume is a durable, block-level storage device that you can attach to a single EC2 instance. 
- You can use EBS volumes as primary storage for data that requires frequent updates, such as the system drive for an instance or storage for a database application. 
- You can also use them for throughput-intensive applications that perform continuous disk scans. EBS volumes persist independently from the running life of an EC2 instance.

- list of important information about EBS Volumes:
   - When you create an EBS volume in an Availability Zone, it is automatically replicated within that zone to prevent data loss due to a failure of any single hardware component.
   - An EBS volume can only be attached to one EC2 instance at a time.
   - After you create a volume, you can attach it to any EC2 instance in the same Availability Zone
   - An EBS volume is off-instance storage that can persist independently from the life of an instance. You can specify not to terminate the EBS volume when you terminate the EC2 instance during instance creation.
   - EBS volumes support live configuration changes while in production which means that you can modify the volume type, volume size, and IOPS capacity without service interruptions.
   - Amazon EBS encryption uses 256-bit Advanced Encryption Standard algorithms (AES-256)
   - EBS Volumes offer 99.999% SLA.
