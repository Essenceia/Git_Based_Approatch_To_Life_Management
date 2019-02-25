# 3D stacking 

## Challenges

### IR Drop

IR drop analysis is extremely critical in today s complex design. Now you have to 
calculate IR drop across a large die when you have another 
die on top of that, which has to feed power and ground from the package through the 
bottom die to the top die. The top die IR drop is going to be affected by the IR drop 
of the lower die, so we have to do a **multi-die IR drop analysis**.

> Need for tools to perform a concurrent multi-die IR drop analysis.

#### Definition 

IR drop is the voltage drop in the metal wires consituting the power grid before it 
reaches the VDD pins of the standard cells.

#### Importance

Why do we bother about the voltage? Because the speed of the standard cell (the 
propagation delay) would be directly proportional to the VDD value. Higher VDD would 
mean faster cell, or lower propagation delay.

#### Example 

Now imagine that your SoC has a nominal voltage of 1V, and you closed your setup timing 
assuming the ideal 1V libraries. However, the IR drop of 40mV came into picture after 
you built the power grid, and the voltage is no longer 1V, let's say it is 0.96V. Now, 
with V = 0.96V, the delays of standard cells would be higher and you might see an 
increase in your **setup-time violations**!

Let's look into the factors that could cause this IR drop and how can we mitigate those 
factors, and what should our sign-off corners be to make sure no **failures 
post-silicon**!




## Sources 

https://semiengineering.com/design-for-advanced-packaging/
http://vlsi-soc.blogspot.com/2016/08/ir-drop-analysis.html
