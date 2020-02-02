# EC2 lifecycle instance states: 
 - pending : The instance is preparing to enter the running state. An instance enters the pending state when it launches for the first time, or when it is restarted after being in the stopped state.

 - running : The instance is running and ready for use.

 - stopping : The instance is preparing to be stopped. Take note that you will not billed if it is preparing to stop however, you will still be billed if it is just preparing to hibernate.

 - stopped : The instance is shut down and cannot be used. The instance can be restarted at any time.

 - shutting-down : The instance is preparing to be terminated.

 - terminated : The instance has been permanently deleted and cannot be restarted. Take note that Reserved Instances that applied to terminated instances are still billed until the end of their term according to their payment option.
 
 ![image](https://user-images.githubusercontent.com/5827617/73608951-18550b80-460c-11ea-84c9-0ffd70ecd32b.png)
