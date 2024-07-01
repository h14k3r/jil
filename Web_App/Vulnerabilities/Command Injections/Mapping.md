# Blackbox
Map the application by having burp listening silently while picking up all the requests you're making as you're moving through the web/app


- Make not of all input vectors that might talk to the backend
- Understand the Application Functions
-  Figure out the Logic of the application

 
## **Looking for Command Injections**
![5541be7639456d3689011861dee6a761.png](../../../_resources/5541be7639456d3689011861dee6a761.png)

Note each time there is a instance where there is a "client side input" that talks to the back-end.


## STEPS
1. Note all the user input fields that might be talking to the backend.
2. FUZZ the application 


[Command_Injections_Module_Cheat_Sheet.pdf](../../../_resources/Command_Injections_Module_Cheat_Sheet.pdf)



## BLIND
If you think there is a blind Command Injection try triggering a **TIME-DELAY** attack by using either `ping` or `sleep` attacks


![5c01e570c420e819a1f4c4697f844a10.png](../../../_resources/5c01e570c420e819a1f4c4697f844a10.png)


# WhiteBox
![2b8fac4bc7ada7e3be1ad3f54679237f.png](../../../_resources/2b8fac4bc7ada7e3be1ad3f54679237f.png)


