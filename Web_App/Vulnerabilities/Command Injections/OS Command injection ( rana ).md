Source: https://academy.ranakhalil.com/courses/1491236/lectures/38308201


# General

## What is OS Command Injection:
Attacker is able to execute commands on the host operating system via a vulnerble application. So the attacks are essentially "system commands".

> example: getting a shell through a product param to get the web server to echo "whoami"


# How to Find:

![cfee2c1aa3eeebfafb86094da52d8739.png](../../../_resources/cfee2c1aa3eeebfafb86094da52d8739.png)


There must be two conditions:
- the code will show that there must be a param that allows command execution`cmd` & must also have one that users put in such as the `arg`

> must use function that executes commands > cmd 
> must have "user controllerable" params in the functions > arg


# Types

![7d6192a5f6b352558dc64edc88e04586.png](../../../_resources/7d6192a5f6b352558dc64edc88e04586.png)
1. In-band ( responses from the commands are seen on the web/app )
2. Blind  ( the responses aren't displayed on the app )


# Impact

![7f8163978095410f1a24235eba86701b.png](../../../_resources/7f8163978095410f1a24235eba86701b.png)

# Exploit
## **BLIND**
If it is `in-band` you just concatenate another command to the already exsisting variable/command/string:
> 127.0.0.1 && cat /etc/passwd &


Observe
![23d1c7fce4410029f17060772bb16d27.png](../../../_resources/23d1c7fce4410029f17060772bb16d27.png)

## **IN-BAND**
If you think there it is blind then try to trigger a `time-delay` attack:

> 127.0.0.1 && sleep 10 &
- sleep is for UNIX based systems

> 127.0.0.1 && ping 10 &
- Windows & UNIX 


![9ddc39b5101739108c0a17c29cc38e05.png](../../../_resources/9ddc39b5101739108c0a17c29cc38e05.png)


# PROOF-OF-CONCEPT
source: https://academy.ranakhalil.com/courses/1491236/lectures/38308201


