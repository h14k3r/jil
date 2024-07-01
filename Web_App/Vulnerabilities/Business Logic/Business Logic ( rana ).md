# General

It is a flaw in the design on the web/app that allows an attacker to "utilize" to get the app to behave in a way that it was not intended too

 ![cb75c1f8f6f896a5e07ee4ad6a3fd1a1.png](../../../_resources/cb75c1f8f6f896a5e07ee4ad6a3fd1a1.png)
 
 Example:
- view senesitive data
- comprimse the account


## Examples of Bussiness Logic flaws
---
#### Example 1

![c4bc4bd5d91792c155d82be5cc687442.png](../../../_resources/c4bc4bd5d91792c155d82be5cc687442.png)

The code below shows the function that creates the businesss logic vulnerability. 

![961ac495acbf209c9263da40cd108d02.png](../../../_resources/961ac495acbf209c9263da40cd108d02.png)

- if exsisting password is "null / empty" then it assumes that you are an administrator
- This is because only the Admin interface does not have an "exsisting" password option ( for example, think of an AD scenerio where you're resetting a password )

### Remediation:
- this should be retrieved from the session token ( to determine user or admin )
- NOT: the client-side parameters 

## Exploit:

A user can edit another user's password by simply not supplying an exsisting password -->> meaning leaving that field blank


# Example 2
This example is about an application that you can place orders on, for example like Amazon:

![a2a711c13f6ecd847dfc772d15f9c6af.png](../../../_resources/a2a711c13f6ecd847dfc772d15f9c6af.png)
- she said that the devs made it where the functions are set up where the steps have to be followed in that order
- however, "That's not how 'requests work"

## Exploit
The bypass here is that in burp we can intercept it and skip the "enter payment" part and go straight into the "devlivery information"


![3ee3b2a4e632f109c32a99588065f8b3.png](../../../_resources/3ee3b2a4e632f109c32a99588065f8b3.png)

# Example 3
App that allows users to transfer from 1 bank to another bank ( like zelle )

![b1ce04e34ab3a656f86023ff8eb572a5.png](../../../_resources/b1ce04e34ab3a656f86023ff8eb572a5.png)
- the devs were told to make sure that they can't transfer more than 10k 

## Exploit

![be7044070b8264e0e9caad3e5f92dc4b.png](../../../_resources/be7044070b8264e0e9caad3e5f92dc4b.png)
- user puts in a negative number they can bypass the filter


# Example 4
![abc195e08cf489c8713a453a5eec5616.png](../../../_resources/abc195e08cf489c8713a453a5eec5616.png)


![af31b10da607cdd15f29a7c720687f6e.png](../../../_resources/af31b10da607cdd15f29a7c720687f6e.png)


# How to Find & Exploit 

1. Map the web/app > make note of each & every compontent & how it operates
2. Try to guess the "assumptions" that the developers / architects made during the design phase

So basically we disrupt "Business Flow" by not following the rules set by the devs -->> or intended rules.

For example, shoping web/app's have certain steps:
1. info
2. pay
3. deliever

What would happen if we tried to skip step #2 


