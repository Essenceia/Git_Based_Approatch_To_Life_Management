# Crypto-1 the RFID cypher for Mifare Classic tags

The security of the Mifare Classic tags partly relied on the secrecy of the cypher 
algorythm used. Unfortunatly this cypher was found out with "modest" effort by a German 
secuirty team spearheaded by Henryk Plotz and accompanied y Karsten Nohl.

## Crypto-1

The Crypto-1 cipher consists of a linear feedback shift register (LFSR) and a filter 
function, f(.),  as shown in Figure 1. During the initialization, the secret 48-bit 
key is loaded into the shift register and the string (ID xor Rb) is shifted into the 
state, where ID is the identifier of the tag, and Rb is a random number chosen by the 
tag. Rb is also sent to the reader as a first challenge in a challenge-response 
protocol in which tag and reader prove knowledge of the secret key. Since in our 
attack, **the attacker only needs to communicate with the reader, the challenge can 
freely be chosen and does not need to be random.**

 

![figure1](figure1.png)

In each clock cycle, the filter function, f(×), computes one bit of key stream from 
20 LFSR bits. The function is composed from 6 instantiations of 3 smaller functions as 
depicted in Figure 2. These functions are statistically biased: if one input bit is 
held constant, then the output is ‘1’ (or ‘0’) more than 50% of the 
time. To compute this bias for a function with n inputs, we test its output 
distribution for all combinations of n-1 of the inputs while keeping the remaining 
input constant. For some of the inputs, the biases are as significant as 10/16 for fc 
and 5/8 for fa and fb. This statistical weakness enables our attack.

 

To find bits of the key, we send challenges to the reader and analyze the first bit of 
key stream sent back by the reader. In these challenges, we hold constant the four 
inputs of one of the fa/b functions while changing some of the other bits in each 
challenge. To generate different challenges in which the chosen bits are constant we 
compute the impact that changes in other bits have on the LFSR feedback, which is 
trivial given knowledge of the LFSR structure and computationally cheap. The key stream 
bits we receive from the reader are biased towards either ‘0’ or ‘1’ 
because fc is statistically biased, which lets us recover the output bit of the fa/b 
block under consideration. Knowing the output bit of the fa/b block we can then test 
for the inputs to the block. This process is repeated for a number of key bits until 
sufficiently many are known for a brute-force attack on the remaining unknown bits to 
become cheap. The number of challenges needed to recover key bits with high probability 
varies for different bits, but generally does not exceed a few dozens.

Using our technique, up to 32 key bits can be recovered, but some of the bits require 
significantly more challenges than others. We found particularly strong biases in 12 of 
the 32 bits that we can recover from the first bit of the key streams. After learning 
these 12 bits, all keys in the remaining 36-bit key space can be tried within 30 
seconds on a single FPGA or within minutes on a typical PC.

Our attack assumes that we can recover the first bit of the key stream. This bit is 
combined with a random bit that is generated on the reader. We have shown previously 
that the random numbers are known to an attacker since they are generated 
deterministically [3]. The attacker needs knowledge of a single key that can, for 
example, be found using a brute-force attack on the entire key space. Once one key is 
known, an attacker can learn enough about a given reader to predict the random numbers 
it will generate, so any number of keys can be recovered using our statistical attack.

Our specific attack can be mitigated by using true random numbers on the reader. This 
does not fix the underlying weaknesses of the cipher, however, and more elaborate 
attacks will emerge. Instead of starting an arms-race around the security of a 
fundamentally flawed cipher, systems should upgrade to more secure cards that use 
publicly scrutinized cryptography.

![figure2](figure2.png)


## Sources

https://www.computerworld.com/article/2537817/how-they-hacked-it--the-mifare-rfid-crack-explained.html
http://www.cs.virginia.edu/~kn5f/Mifare.Cryptanalysis.htm

