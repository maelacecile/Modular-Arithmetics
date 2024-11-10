ThreePassProtocol
Three-Pass Protocol Solution
Problem Statement
Alice and Bob use Shamir's Three-Pass Protocol to securely exchange a message without sharing keys directly. Given a series of messages exchanged and certain parameters, our task is to determine the secret message sent by Alice to Bob.

Parameters and Observed Messages
Prime (p): 
𝑝
=
91246234312872996521
p=91246234312872996521
Messages Observed:
𝐴
→
𝐵
:
28815377349986238948
A→B:28815377349986238948
𝐵
→
𝐴
:
32022638409929718780
B→A:32022638409929718780
𝐴
→
𝐵
:
14438564975518228697
A→B:14438564975518228697
Additional Information:
We have 
(
𝑎
⋅
𝑏
)
m
o
d
 
 
(
𝑝
−
1
)
=
52989123124449843069
(a⋅b)mod(p−1)=52989123124449843069
The goal is to use this information to reconstruct the original message 
𝑚
m that Alice sent.

Approach
Using modular arithmetic and the given values:

We calculate the modular inverse of 
𝑎
a and 
𝑏
b modulo 
𝑝
−
1
p−1.
Using the Three-Pass Protocol, we can solve for 
𝑚
m by isolating the terms in the message exchanges.
Code
