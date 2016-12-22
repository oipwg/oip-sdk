###Protocol Introduction  
The **Open Index Protocol** is a decentralized application (DApp) which unites a peer-to-peer distribution network (IPFS), a micropayments blockchain (Bitcoin), and a blockchain designed specifically to store messages.  

It’s primary purpose is to establish a **decentralized media index**, owned by no one collectively and, at the same time, each of it’s publishers individually. Thru the use of an open message schema and a simple set of mutually agreed-upon rules for core functions, the following permission-less **jobs** are created, which anyone can compete to capture value from:  

•**Publishers** of original content (**artifacts**) to the index  
*(paid by end users when they connect with an audience that finds their content valuable, at whatever price they and their market agree upon)*  

•**Miners** contributing proofs-of-work to the mutual protection of the index of artifacts  
*(paid by publishers for their actual costs plus their requested margin, governed by data-driven market feedback mechanisms, limited by demand for publishing)*  

•**Storage and distribution services** for the media files published to the index *(paid by publishers or patrons of content, governed by free floating market prices per MB stored per unit of time and per MB transmitted, limited by caps set per piece of content, since in most cases, a file having any more than ~20 seeders starts to see diminishing returns quickly)*  

•**Promoters** of artifacts published to the index  
*(paid directly by end users when they pay for a piece of media the promoter put in front of them, mostly over social media platforms, percent of total sale they get is limited by preferences determined by publishers)*  

•**Retailers** of artifacts published in the index  
*(paid directly by end users when they pay for a piece of media the retailer put in front of them, mostly using suggestion algorithms within a given front end/marketplace, percent of total sale they get is limited by preferences determined by publishers)*  

##Fully Decentralized Node
•**Index Blockchain Wallet Daemon** - [Florincoin official site](http://florincoin.org/)  |  [Github](https://github.com/florincoin/florincoin)  
*(note:[Enable RPC access](https://github.com/dloa/alexandria-docs/blob/master/florincoin-lin64-install.md))*  
•**IPFS Daemon** [IPFS official site] [Github]

##To be a “retailer” (i.e., to host a front end/marketplace)  
  
2.  Enable RPC access to the florincoin wallet. [Instructions](https://github.com/dloa/alexandria-docs/blob/master/florincoin-lin64-install.md)  
3.  Install OIP-NPM, a node.js module built to enable making changes to the OIP index. [Github](https://github.com/dloa/oip-npm)  
4.  Use our hosted OIPD API endpoint for reading and searching the OIP index.  
[hosted v2/media/get/all endpoint](https://api.alexandria.io/alexandria/v2/media/get/all)  
[hosted v2/search endpoint] (https://api.alexandria.io/alexandria/v2/search)  
[hosted v2/search endpoint usage](https://api.alexandria.io/docs/#get-a-specific-artifact)  
5. Build an interface using all of the above, or start by forking the components of ours. [Browser](https://github.com/dloa/alexandria-browser), [Publisher](https://github.com/dloa/publisher-web), [Paywall](https://github.com/dloa/paywall-web) & [TradeBot](https://github.com/dloa/alexandria-tradebot)  


####JSON standards:  
[multipartData](https://github.com/dloa/media-protocol#multipart-data)  
[publishArtifact](https://github.com/dloa/media-protocol#publish-artifact)  
[editArtifact](https://github.com/dloa/media-protocol#edit-artifact)  
[transferArtifact](https://github.com/dloa/media-protocol#transfer-artifact)  
[deactivateArtifact](https://github.com/dloa/media-protocol#deactivate-artifact)  

####Publishing fee formulae:  
The OIP formula for calculating the **publish fee** is totally closed-loop and depends entirely on information found either in the Florincoin blockchain or in the publish message itself. It is calculated as a function of its commercial value to the Publisher or as a function of its size in the blockchain if it is being offered for free.  
  
[Publish Fee, Free Artifact](https://github.com/dloa/sdk/blob/master/formulae.md#pf)  
[Publish Fee, Commercial Artifact](https://github.com/dloa/sdk/blob/master/formulae.md#pc)

##To check the **pool_margin** for the past 24 hours of a protocol compliant mining pool  
1.  Lookup the current [block](https://api.alexandria.io/florincoin/getMiningInfo) height and store the result as **block**  
2.  Use the **historian** summary [API POST endpoint](https://api.alexandria.io/alexandria/v1/historian/summary) using:
<pre><code>
{
    "min-block":block-2160,
    "max-block":block
}
</code></pre>
3.  The **averages** array will include a field labeled **pool_margin**. If this amount is in the ballpark of your target margin on top of mining costs, you may wish to [become an autominer](https://github.com/dloa/sdk#to-become-an-autominer)  

##To become an AutoMiner:  
1.  Create an account on miningrigrentals.com  
2.  Make a new “pool profile”  
<pre><code>algo: Scrypt  
host: api.alexandria.io  
port: 3032  
worker: yourflorincoinaddress  
password: anythingyouwant</code></pre>  
3.  Create a [miningrigrentals API key](https://www.miningrigrentals.com/account/apikey)  
4.  Install and start the **autominer_api** application. [Github](https://github.com/dloa/autominer-api)  
5.  Fund your miningrigrentals.com wallet with some bitcoin, and the autominer-api will automatically start renting rigs if market conditions allow your minimum margin to be met  


###Captured Value  
![alt text](https://raw.githubusercontent.com/dloa/sdk/master/captured%20value%20stack.png "Value Capture Stack")  
