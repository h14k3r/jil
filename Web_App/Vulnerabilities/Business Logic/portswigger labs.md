# Lab1
I caputured the "add to cart request" with burp.

then i changed the amount from 1k > .99 

sent the request in burp then refreshed it on the app and it changed the price of the item to a dollar and was able to get store credit back in addition to solving the lab

## Rana notes 
Lab #1 - Excessive trust in client-side controls

Target Goal - Exploit logic flaw to buy the Lightweight l33t leather jacket.

Creds - wiener:peter

Analysis:
1. Login as the user*
2. Add an item to the cart*
3. Purchase the item*
4. Confirm that we solved the lab



# Lab2
note: 

she thinks the vuln is when you add the item to cart 
![a300552c6c33435b360311c42c5a2ea4.png](../../../_resources/a300552c6c33435b360311c42c5a2ea4.png)

the difference this time is that the "add price param" is gone. 

![529b3b7f7e9aa0fc2f845ae484a3296c.png](../../../_resources/529b3b7f7e9aa0fc2f845ae484a3296c.png)
- she changed the amount of items in the cart to negative 1



![0799b1ba9155995339910b8a09ba6846.png](../../../_resources/0799b1ba9155995339910b8a09ba6846.png)  
- resulting in negative amount due 
- however it does not accept negative price


![4d419c8322d531d6c9ea2fe37da7f398.png](../../../_resources/4d419c8322d531d6c9ea2fe37da7f398.png)
- what she did here was grab an item that was about 100 then added it to the cart ? then she minues the amount of quantity that would keep subracting the 100 until the price of the item that was 1000 is lowered to 100 


## solved
the way you solve it is by placing a negative amount of produts after adding to different products. 


you want to capture the requst of the product that was 100 dollars until you keep subracting it to something you can afford.

![045036833bbc61ceb8b4bf33d617bd51.png](../../../_resources/045036833bbc61ceb8b4bf33d617bd51.png)



# Lab 3

in real world env. using burp pro
- you would go to `site map` > then select engagement tools and then just fuzz 
![82389a762f83fe8dc3bf871d4bd0a318.png](../../../_resources/82389a762f83fe8dc3bf871d4bd0a318.png)

because it wants us to find the admin panel then what we woulld do is fuzz for hidden dir. 


so she fuzzed it manuall by just `/admin` 

![79a4af991e79ccffb00d37e49e953bd4.png](../../../_resources/79a4af991e79ccffb00d37e49e953bd4.png)

# Lab 4 
back end only checks the last coupon that was added so we can just keep adding a > b > a > b

![45c719d3ee0712271ed08c24d178e488.png](../../../_resources/45c719d3ee0712271ed08c24d178e488.png)

![e804b0d3d32e733ea0e0ea659eaa08b9.png](../../../_resources/e804b0d3d32e733ea0e0ea659eaa08b9.png)


## solved


# Lab 5
The way this was done was basically brute forcing the amount of jackets we can add to the cart.

eventually it got so large that the amount of the total went to negative

![c22babe6cbd9bd29438fd825bcf803d9.png](../../../_resources/c22babe6cbd9bd29438fd825bcf803d9.png)

- note: all we did was continue to send the same request over and over so this means we didn't add any positions to the intruder attack. 

![cf4b66e4f27246067e094debd708b608.png](../../../_resources/cf4b66e4f27246067e094debd708b608.png)
- no positions added


![c039af6da5f2f26d4794014fdd0979ba.png](../../../_resources/c039af6da5f2f26d4794014fdd0979ba.png)

- payload set was put to "null payloads"


Basically what we are doing here is DDoSing the app until we get it to re-act different by setting a negative value. once we get it to do that, then we add a positive value item to the cart until we get it in the positive range and can purchase it.


# Lab 6

Lab #6 Inconsistent handling of exceptional input
