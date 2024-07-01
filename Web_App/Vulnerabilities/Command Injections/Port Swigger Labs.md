Source: https://academy.ranakhalil.com/courses/enrolled/1491236

# Lab1 ( easy )

## Task
*To solve the lab, execute the "whoami" command to determine the name of the current user*

## Soltuion
The way this was solved was by inputting `1|whoami` in the "storeID" param.

![b1f0db14cc9eb6b69c7d53eaa7b3fe8a.png](../../../_resources/b1f0db14cc9eb6b69c7d53eaa7b3fe8a.png)
- this was a command shell injection


# Lab2 ( easy )
Goal: Get it to sleep for 10sec

Currently have mapped the site to find these:
![1995640ca228621ce10dd8dc2979dfe8.png](../../../_resources/1995640ca228621ce10dd8dc2979dfe8.png)


Noticed that the "feedback/submit" url has a lot of params:
![45672d4f10c240604154d7b0599b8986.png](../../../_resources/45672d4f10c240604154d7b0599b8986.png)


## tried:

- inject a single apostrophy in each injectable but then I remembered this is blind - so we need a time delay

#### Tip: look up cheat sheet for command injections to cause a time delay

## Found the Vuln Param

Payload used: `; sleep 10;`


![dc8c65a667959d10ceaa4eaa66217b99.png](../../../_resources/dc8c65a667959d10ceaa4eaa66217b99.png)
- email was the vulnerabale param
- url encoded the payload
- solved the lab just by getting it to sleep for 10seconds

# Lab3
#### Goal:
- vulnerability is in the "feedback function"
- BLIND
- It suggests to use output redirection to caputre the output from the command
- writeable folder is at `/var/www/images/`

To solve the lab we need to execute the `whoami` command and retrieve the output where we saved it, as stated above

## Attempt ( solo )
- The vuln param is the 'email' > tested this by using this payload `; sleep 10;` > then I URL encoded it

## What I Tried
- I got it to **sleep** for 10 seconds
- however, I couldn't get it to save

#### payloads tried:

`; whoami > /var/www/iamges/whoami.txt;`

`&& whoami > /var/www/images/whoami.txt`

> results: nothing worked
> I keep getting "not saved" error in the response


![dbdeee791129d4ca5443eb2f873dd292.png](../../../_resources/dbdeee791129d4ca5443eb2f873dd292.png)

## Attempt ( Rana )

Payload she used:
> email:test` & sleep 10 #` 

NOTE: there is a space after the 'test' string. What we did is jsut URL encode from the # to the 't'

![f3957a142febbc7609e28c1db6feefab.png](../../../_resources/f3957a142febbc7609e28c1db6feefab.png)
- BEFORE URL encoded

![0081b4de862d396a40a170edfe18cd99.png](../../../_resources/0081b4de862d396a40a170edfe18cd99.png)
- AFTER URL encoded


---
## got it to execute the WHOAMI 
so what we did was use this payload to have it execute the `whoami` command and then save it into a file we created at this dir. `/var/www/images/whoami.txt` 

![8c24949c0fd000b99c16b0dcde4dd2be.png](../../../_resources/8c24949c0fd000b99c16b0dcde4dd2be.png)
- we got a 200 repsonse back

## FUCK THE HELP -->> I DID DAT SHIT MYSELF


#### Payload used: 
>param & whoami > /var/www/images/whoami.txt #
- then I URL encoded that

#### What's happening here?
- `whoami` is a command before the ` > `
- it executes the command then saves the data to the filename we created `whoami.txt`

#### HOW DID WE RETRIEVE IT?
- for some reason we couldn't get it to output by trying to `cat` from the same path

![63ff3dc482727f97ca9893d53eb8c470.png](../../../_resources/63ff3dc482727f97ca9893d53eb8c470.png)
- so it was returning a 200 response but we couldn't do anything else here


#### well?
- What we did is go back to the home page and looked for where the "images" were being rendered from and then we found this:

![dbd7ab6e847e1d04ecdfd5b29231acc2.png](../../../_resources/dbd7ab6e847e1d04ecdfd5b29231acc2.png)
- we changd the param `filename=` and we put in the `whoami.txt` for it to retrieve

## Lab Solved


# Can't Do Because Burp Community Is Fucking BullShit
![4a8c850754954bcd351aa5dd5c17dda7.png](../../../_resources/4a8c850754954bcd351aa5dd5c17dda7.png)

![e218a09e45bdeafade7f625ef214571d.png](../../../_resources/e218a09e45bdeafade7f625ef214571d.png)



Done