###Protocol Introduction  
The **Open Index Protocol** is a decentralized application (DApp) which unites a peer-to-peer distribution network (IPFS), a micropayments blockchain (Bitcoin), and a blockchain designed specifically to store messages.  

It’s primary purpose is to establish a fully decentralized **Index** of publish messages describing and facilitating the distribution of original content(**artifacts**), owned by no one collectively and, at the same time, each of it’s **publishers** individually. The individual publish messages are able to describe commerce & tipping preferences, how media files can be found and distributed to end users, in addition to cataloguing and descriptive information, meta tags and more. Thru the use of a standardized schema for JSON messages and a simple set of mutually agreed-upon rules for core functions, the following permission-less **jobs** result, which anyone can compete to capture value from:  

•**Retailers** of artifacts published in the index

•**Promoters** of artifacts published to the index  

•**AutoMiners** contributing proofs-of-work to the mutual protection of the Index of artifacts  

•**AutoDistributor** provide storage and distribution services for the media files published to the index 

•**Publishers** of original content  to the index  

---  

###Protocol Software  

####Reference "browser" node.js application  
•**Alexandria Browser** - Index browser reference client  |  [Github](https://github.com/dloa/alexandria-browser)   

####Decentralized Full Node
•**Index Blockchain Wallet Daemon** - [Florincoin official site](http://florincoin.org/)  |  [Github](https://github.com/florincoin/florincoin)  |  *(note:[Enable RPC access](https://github.com/dloa/alexandria-docs/blob/master/florincoin-lin64-install.md))*  
•**IPFS Daemon** - [IPFS official site](https://ipfs.io/)  |  [Github](https://github.com/ipfs/go-ipfs)  |  [Prebuilt Installer](https://ipfs.io/docs/install/)  
•**Payment Blockchain Wallet Daemon** - [Bitcoin](https://bitcoin.org/)  |  [Github](https://github.com/bitcoin/bitcoin/)  
•**Decentralized Digital Rights Locker** - [Pockets](http://pockets.tokenly.com/)  |  [Github](https://github.com/tokenly/pockets)  
•**OIP Daemon** - a GoLang daemon for the OIP protocol. Closed repo currently, pending security audit  |  [Request access](mailto:devon@alexandria.io)  

####“Retailer” node  
a web-hosted front end of some or all of the original content published to the Index  
*(paid directly by end users when they pay for a piece of media the retailer put in front of them, mostly using suggestion algorithms within a given front end/marketplace, percent of total sale they get is limited by preferences determined by publishers)*  
•[Decentralized Full Node](#decentralized-full-node)  
•**OIP-NPM** - a node.js module built to enable publishing and submitting changes to the OIP index. [Github](https://github.com/dloa/oip-npm)  
•**OIP Daemon** - a GoLang daemon for the OIP protocol. Closed repo currently, pending security audit  |  [Request access](mailto:devon@alexandria.io)  
•**hosted OIP API** - for reading and searching the OIP index. *all artifacts [endpoint](https://api.alexandria.io/alexandria/v2/media/get/all) | search artifacts [endpoint] (https://api.alexandria.io/alexandria/v2/search) & [usage](https://api.alexandria.io/docs/#get-a-specific-artifact)*  
•**Web Interfaces** - [Browser](https://github.com/dloa/alexandria-browser), [Publisher](https://github.com/dloa/publisher-web), [Paywall](https://github.com/dloa/paywall-web) & [TradeBot](https://github.com/dloa/alexandria-tradebot)  

####**AutoMiner**  
*(paid by publishers for their actual costs plus their requested margin, governed by data-driven market feedback mechanisms, limited by demand for publishing)*  

#####To run a Pool node  
•**Pool Interface** - Node.js pool portal [Github](https://github.com/dloa/unified-node-open-mining-portal)  
•**Pool Server** - Node.js stratum pool server [Github](https://github.com/dloa/node-merged-pool)  

#####To check the average **pool_margin** for the past 24 hours of protocol compliant mining pools  
1.  Lookup the current [block](https://api.alexandria.io/florincoin/getMiningInfo) height and store the result as **block**  
2.  Use the **historian** summary [API POST endpoint](https://api.alexandria.io/alexandria/v1/historian/summary) using:
<code><pre>{
    "min-block":block-2160,
    "max-block":block
}</pre></code>  
3.  The **averages** array will include a field labeled **pool_margin**. If this amount is in the ballpark of your target margin on top of mining costs, you may wish to [become an autominer](#to-become-an-autominer)  

#####To become an AutoMiner:  
1.  Create an account on miningrigrentals.com  
2.  Make a new “pool profile”  
<code><pre> algo: Scrypt  
 host: api.alexandria.io  
 port: 3032  
 worker: yourflorincoinaddress  
 password: anythingyouwant</pre></code>  
3.  Create a [miningrigrentals API key](https://www.miningrigrentals.com/account/apikey)  
4.  Install and start the **autominer_api** application. [Github](https://github.com/dloa/autominer-api)  
5.  Fund your miningrigrentals.com wallet with some bitcoin, and the autominer-api will automatically start renting rigs if market conditions allow your minimum margin to be met  

####To become an **AutoDistributor**  
*(paid by publishers or patrons of content, governed by free floating market prices per MB stored per unit of time and per MB transmitted, limited by caps set per piece of content, since in most cases, a file having any more than ~20 seeders starts to see diminishing returns quickly)*  

####To become a **Promoter**  
*(paid directly by end users when they pay for a piece of media the promoter put in front of them, mostly over social media platforms, percent of total sale they get is limited by preferences determined by publishers)*  

####To become a **Publisher**  
*(Publishers are paid by end users when they connect with an audience that finds their content valuable, at whatever price they and their market agree upon)* 

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

###Captured Value  
![alt text](https://raw.githubusercontent.com/dloa/sdk/master/captured%20value%20stack.png "Value Capture Stack")  
