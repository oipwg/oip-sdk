#####`P`  
*Required Publish Fee, in fiat.*
max ([Pf](#pf), [Pc](#pc))  
#####`QP`  
*Quantity of Florincoin tokens estimated for Required Publish Fee.*  
[P](#p) / [fmdUSD](https://api.alexandria.io/flo-market-data/v1/getAll)	
#####`Pf`  
*Publish Fee, Free Artifacts.*  
[V](#v) * [s](#s) / [blockchainsize](#blockchainsize)	 
#####`Pc`  
*Publish Fee, Commercial Artifacts.*
if ( [C](#c) < [Cµ](#cµ), [C](#c), (( log ([C](#c)) - log ([Cµ](#cµ)) ) x ( [Cµ](#cµ) / [C](#c) ) x [D](#d) ) + [Cµ](#cµ) )	 
#####`V`  
*Value of mined blocks in one day.*  
[BlocksPerDay](#blocksperday) * [coinbasereward](#coinbasereward) * [fmdUSD](https://api.alexandria.io/flo-market-data/v1/getAll)	 
#####`s`  
*artifact's total size in blockchain.*  
(integer, in bytes)  
#####`blockchainsize`  
*Wallet lookup function, not yet implemented*  
(integer, in bytes; currently use hardcorded value of 1,065,000)  
#####`BlocksPerDay`  
*The target number of blocks mined per day, according to the blockchain protocol*  
(integer, value = 2160)
#####`coinbasereward`  
*Number of tokens awarded with each found block, looked up based on block height*  
(integer, current value = 25)  
#####`C`  
*artifact "cost", defined as the average between its total minPlay and its total sugBuy values*  
avg ([m](#m),[b](#b))
#####`m`  
*sum of all of the minPlay prices in a given artifact*
∑ (m₁,m₂, ...)  
#####`b`  
sum of all of the sugBuy prices in a given artifact
∑ (b₁,b₂, ...)	 
#####`Cµ`  
*mean average of all artifact "cost"s in entire library*  
avg (C₁,C₂,...)  
#####`D`  
*diff between an artifacts "cost" and mean avg artifact cost in the library*  
[C](#c) - [Cµ](#cµ)  
