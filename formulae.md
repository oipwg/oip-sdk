#####`P : Required Publish Fee, in fiat.`
max ([Pf](https://github.com/dloa/sdk/blob/master/formulae.md#pf---publish-fee-free-artifacts), [Pc](https://github.com/dloa/sdk/blob/master/formulae.md#pc--publish-fee-commercial-artifacts))  
#####`QP : Quantity of Florincoin tokens estimated for Required Publish Fee.`  
[P](https://github.com/dloa/sdk/blob/master/formulae.md#p--required-publish-fee-in-fiat) / [fmdUSD](https://api.alexandria.io/flo-market-data/v1/getAll)	
#####`Pf :	Publish Fee, Free Artifacts.`  
[V](https://github.com/dloa/sdk/blob/master/formulae.md#v--value-of-mined-blocks-in-one-day) * [s](https://github.com/dloa/sdk/blob/master/formulae.md#s--artifacts-total-size-in-blockchain-integer-in-bytes) / [blockchainsize](https://github.com/dloa/sdk/blob/master/formulae.md#blockchainsize--wallet-lookup-function-not-yet-implemented-currently-use-hardcorded-value-of-1065000-integer-in-bytes)	 
#####`Pc : Publish Fee, Commercial Artifacts.`
if ( [C](https://github.com/dloa/sdk/blob/master/formulae.md#c--artifact-cost-defined-as-the-average-between-its-total-minplay-and-its-total-sugbuy-values) < [Cµ](https://github.com/dloa/sdk/blob/master/formulae.md#cµ--mean-average-of-all-artifact-costs-in-entire-library), [C](https://github.com/dloa/sdk/blob/master/formulae.md#c--artifact-cost-defined-as-the-average-between-its-total-minplay-and-its-total-sugbuy-values), (( log ([C](https://github.com/dloa/sdk/blob/master/formulae.md#c--artifact-cost-defined-as-the-average-between-its-total-minplay-and-its-total-sugbuy-values)) - log ([Cµ](https://github.com/dloa/sdk/blob/master/formulae.md#cµ--mean-average-of-all-artifact-costs-in-entire-library)) ) x ( [Cµ](https://github.com/dloa/sdk/blob/master/formulae.md#cµ--mean-average-of-all-artifact-costs-in-entire-library) / [C](https://github.com/dloa/sdk/blob/master/formulae.md#c--artifact-cost-defined-as-the-average-between-its-total-minplay-and-its-total-sugbuy-values) ) x [D](https://github.com/dloa/sdk/blob/master/formulae.md#d--diff-between-an-artifacts-cost-and-mean-avg-artifact-cost-in-the-library) ) + [Cµ](https://github.com/dloa/sdk/blob/master/formulae.md#cµ--mean-average-of-all-artifact-costs-in-entire-library) )	 
#####`V : Value of mined blocks in one day.`  
[BlocksPerDay](https://github.com/dloa/sdk/blob/master/formulae.md#blocksperday--known-variable-integer-currently-2160) * [coinbasereward](https://github.com/dloa/sdk/blob/master/formulae.md#coinbasereward--known-variable-based-on-block-height-integer-currently-25) * [fmdUSD](https://api.alexandria.io/flo-market-data/v1/getAll)	 
#####`s : artifact's total size in blockchain.`  
(integer, in bytes)  
#####`blockchainsize : Wallet lookup function, not yet implemented`  
(integer, in bytes; currently use hardcorded value of 1,065,000)  
#####`BlocksPerDay : The target number of blocks mined per day, according to the blockchain protocol`  
(integer, value = 2160)
#####`coinbasereward : Number of tokens awarded with each found block, looked up based on block height`  
(integer, current value = 25)  
#####`C : artifact "cost", defined as the average between its total minPlay and its total sugBuy values`  
avg ([m](https://github.com/dloa/sdk/blob/master/formulae.md#m--sum-of-all-of-the-minplay-prices-in-a-given-artifact),[b](https://github.com/dloa/sdk/blob/master/formulae.md#b--sum-of-all-of-the-sugbuy-prices-in-a-given-artifact))
#####`m : sum of all of the minPlay prices in a given artifact`
∑ (m₁,m₂, ...)  
#####`b : sum of all of the sugBuy prices in a given artifact`
∑ (b₁,b₂, ...)	 
#####`Cµ : mean average of all artifact "cost"s in entire library`  
avg (C₁,C₂,...)  
#####`D : diff between an artifacts "cost" and mean avg artifact cost in the library`  
[C](https://github.com/dloa/sdk/blob/master/formulae.md#c--artifact-cost-defined-as-the-average-between-its-total-minplay-and-its-total-sugbuy-values) - [Cµ](https://github.com/dloa/sdk/blob/master/formulae.md#cµ--mean-average-of-all-artifact-costs-in-entire-library)  
