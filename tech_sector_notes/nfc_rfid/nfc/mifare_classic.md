# MIFARE Classic family 

Build by NXP, compilant to parts 1 to 3 of the ISO/IEC 14443 type A. Uses a 
**propietary security protocol** for authentification and ciphering.

The mifare classic chip has a memory for 1-4K divided into sectors composed of 16 bits 
datablocks. Every last data block of a sector is called a **sector tailers**. Each 
sector is 
protected by two different keys called A and B. Each key can be programmed to allow 
operations such as reading, writing, increasing value blocks, etc.

It uses an NXP proprietary security protocol **Crypto-1** for authentication and 
ciphering. ( broken )

### Sector 0 

This sector contains special data, the first 4 bytes contaon the unique indentifier of 
the card UID followed by a 1 byte bit count check ( BCC ). The reste of this sector is 
used to store manefacturer data. 

This block is read only.

### Data acces

The command set of mifar Classic is small. Most commands are related to a datablock 
and 
require the reader to be authenticated for its containing sector. The access conditions 
are checked every time a command is executed to determine whether it is allowed or not. 
A block of data might be configured to be read only. 
Another example of a restriction 
might be a value block which can only be decremented.

#### Read and Write

The read and write 
commands read or write one data block. This is either a data block or a value block. 
The 
write command can be used to format a data block as value block or just store arbitrary 
data. 

#### Decrement, Increment, Restore and Transfer

These commands are only al-lowed on data 
blocks that are formatted as value blocks. The increment and decre-mentcommands will 
increment or decrement a value block with a given value andplace the result in a memory 
register. There store command loads a value into the memory register without any 
change. 
Finally the memory register is transferred inthe same block or transferred to another 
block by the transfer command.


#### Authentication Protocol

Mifare Classic makes use of a mutual three pass au-thentication 
protocol that is based on ISO 9798-2 accordingto the mifare docu-mentation [8]. 
However, 
it turned out that this is not completely true [2]. In thispaper we only use the first 
initial nonce that is send by the card. The reader sends a request for sector 
authentication and the card will respondwith a 32-bit nonceNC.Then, the reader sends 
back an 8-byte answer to that nonce which also contains a reader random NR. This answer 
is the first encrypted message after the start of the authentication procedure. 
Finally, 
the card sends a 4-byteresponse. As far as our attack is concerned this description 
captures all the necessary information.

## Key management 

The cards memory is divided into sectors, each protected by two cryptographic 
keys.Proper key managementis a subject in its own right. Roughly speaking, there are 
two possibilities:

- All cards and all card readers used for a some application have 
the same keys for authentication. This is common when cards are used for access 
control.
- Each **card has its own cryptographic keys**. To check the keys of a card, the 
cardreader should then : first determine which card it is talking to and then look up 

or calculate the associated key(s). This is called key diversification. 


## Sources

https://en.wikipedia.org/wiki/MIFARE
http://www.cs.ru.nl/~flaviog/publications/Security_Flaw_in_MIFARE_Classic.pdf
http://www.cs.ru.nl/~flaviog/publications/Attack.MIFARE.pdf
