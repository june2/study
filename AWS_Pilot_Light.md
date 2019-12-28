# Pilot Light

- The term pilot light is often used to describe a DR scenario in which a minimal version of an environment is always running in the cloud. 
- The idea of the pilot light is an analogy that comes from the gas heater.
- In a gas heater, a small flame that’s always on can quickly ignite the entire furnace to heat up a house. 
- This scenario is similar to a backup-and-restore scenario.

- For example, with AWS you can maintain a pilot light by configuring and running the most critical core elements of your system in AWS. When the time comes for recovery, you can rapidly provision a full-scale production environment around the critical core.

![image](https://user-images.githubusercontent.com/5827617/71541149-adbf0900-2997-11ea-8e4e-b6b65d54ae84.png)
