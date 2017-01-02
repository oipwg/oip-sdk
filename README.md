##Protocol Introduction   
<a href="https://alexandria.io/browser/#/511c251a4a5b8b9d25631b3f2617eb10412c2771971e202362c4054c878487ad" target="_blank">Watch protocol explanation video.</a>

The **Open Index Protocol** unites a peer-to-peer distribution network (IPFS), a micropayments blockchain (Bitcoin), and a blockchain designed specifically to store messages.  

It’s primary purpose is to establish a fully decentralized **Index** of publish messages describing and facilitating the distribution of original content(**artifacts**). Publishers retain full control of their artifacts, but because it is stored in a blockchain the index is not centrally controled by anyone and is transparent to the community at-large. The individual publish messages describe (1)commerce & tipping preferences, (2)how media files can be found and distributed to end users, (3)cataloguing and descriptive information, (4)meta tags and more. Thru the use of a standardized schema for JSON messages and a simple set of mutually agreed-upon rules for core functions, the following permission-less **jobs** result:  

•[**Retailers**](#retailer-node) of artifacts published in the index

•[**Promoters**](#promoter) of artifacts published to the index  

•[**AutoMiners**](#autominer) contributing proofs-of-work to the mutual protection of the Index of artifacts  

•[**AutoDistributor**](#autodistributor) provide storage and distribution services for the media files published to the index 

•[**Publishers**](#publisher) of original content  to the index  

---  

##Protocol Software  

###Reference "browser" node.js application  
•**Alexandria Browser** - Index browser reference client  |  [Github](https://github.com/dloa/alexandria-browser)   

###Decentralized Full Node
•**Index Blockchain Wallet Daemon** - [Florincoin official site](http://florincoin.org/)  |  [Github](https://github.com/florincoin/florincoin)  |  *(note:[Enable RPC access](https://github.com/dloa/alexandria-docs/blob/master/florincoin-lin64-install.md))*  
•**IPFS Daemon** - [IPFS official site](https://ipfs.io/)  |  [Github](https://github.com/ipfs/go-ipfs)  |  [Prebuilt Installer](https://ipfs.io/docs/install/)  
•**Payment Blockchain Wallet Daemon** - [Bitcoin](https://bitcoin.org/)  |  [Github](https://github.com/bitcoin/bitcoin/)  
•**Decentralized Digital Rights Locker** - [Pockets](http://pockets.tokenly.com/)  |  [Github](https://github.com/tokenly/pockets)  
•**OIP Daemon** - a GoLang daemon for the OIP protocol. Closed repo currently, pending security audit  |  [Request access](mailto:devon@alexandria.io)  

###Retailer node  
a web-hosted front end of some or all of the original content published to the Index  
•[Decentralized Full Node](#decentralized-full-node)  
•**OIP-NPM** - a node.js module built to enable publishing and submitting changes to the OIP index. [Github](https://github.com/dloa/oip-npm)  
•**OIP Daemon** - a GoLang daemon for the OIP protocol. Closed repo currently, pending security audit  |  [Request access](mailto:devon@alexandria.io)  
•**hosted OIP API** - for reading and searching the OIP index. *all artifacts [endpoint](https://api.alexandria.io/alexandria/v2/media/get/all) | search artifacts [endpoint] (https://api.alexandria.io/alexandria/v2/search) & [usage](https://api.alexandria.io/docs/#get-a-specific-artifact)*  
•**Web Interfaces** - [Browser](https://github.com/dloa/alexandria-browser), [Publisher](https://github.com/dloa/publisher-web), [Paywall](https://github.com/dloa/paywall-web) & [TradeBot](https://github.com/dloa/alexandria-tradebot)  
*(paid directly by end users when they pay for a piece of media the retailer put in front of them, mostly using suggestion algorithms within a given front end/marketplace, percent of total sale they get is limited by preferences determined by publishers)*  

###**AutoMiner**  

#####To run a **mining pool**  
•**Pool Interface** - Node.js pool portal [Github](https://github.com/dloa/unified-node-open-mining-portal)  
•**Pool Server** - Node.js stratum pool server [Github](https://github.com/dloa/node-merged-pool)  

#####To check the average **pool_margin** for the past 24 hours of protocol compliant mining pools  
1.  Lookup the current **block** height and store the result as `block` ([hosted API endpoint](https://api.alexandria.io/florincoin/getMiningInfo) | [Github source](https://github.com/oipwg/txcomment-search-api)  
2.  Use the **historian** summary [API POST endpoint](https://api.alexandria.io/alexandria/v1/historian/summary) using:
<code><pre>{
    "min-block":block-2160,
    "max-block":block
}</pre></code>  
3.  The **averages** array will include a field labeled **pool_margin**. If this amount is in the ballpark of your target margin on top of mining costs, you may wish to [become an autominer](#to-become-an-autominer)  

#####**AutoMiner**  
1.  Create an account on miningrigrentals.com  
2.  Make a new “pool profile”  
<code><pre>algo: Scrypt  
 host: api.alexandria.io  
 port: 3032  
 worker: yourflorincoinaddress  
 password: anythingyouwant</pre></code>  
3.  Create a [miningrigrentals API key](https://www.miningrigrentals.com/account/apikey)  
4.  Install and start the **autominer_api** application. [Github](https://github.com/dloa/autominer-api)  
5.  Fund your miningrigrentals.com wallet with some bitcoin, and the autominer-api will automatically start renting rigs if market conditions allow your minimum margin to be met  
*(autominers are paid by publishers for their actual costs plus their requested margin, governed by data-driven market feedback mechanisms, limited by demand for publishing)*  

###**AutoDistributor**  
*(paid by publishers or patrons of content, governed by free floating market prices per MB stored per unit of time and per MB transmitted, limited by caps set per piece of content, since in most cases, a file having any more than ~20 seeders starts to see diminishing returns quickly)*  

###**Promoter**  
*(paid directly by end users when they pay for a piece of media the promoter put in front of them, mostly over social media platforms, percent of total sale they get is limited by preferences determined by publishers)*  

###**Publisher**  
•How to register as a Publisher  
•How to format [publish messages](https://github.com/oipwg/media-protocol#publish-artifact) properly  
•Calculating the required [Publish Fee](https://github.com/oipwg/oip-sdk/blob/master/README.md#publishing-fee-formulae)  
•Calculating the trade value of tokens from AutoMiner nodes  
•Using TradeBot to exchange Bitcoin for Florincoin tokens to use for publishing - Hosted API endpoints for [checking tradable balance](api.alexandria.io/tradebot/flobalance) & [starting a trade](https://api.alexandria.io/tradebot/depositaddress?floaddress=**********************************)  
*(Publishers are paid by end users when they connect with an audience that finds their content valuable, at whatever price they and their market agree upon)*  

---

###JSON standards:  
[multipartData](https://github.com/dloa/media-protocol#multipart-data)  
[publishArtifact](https://github.com/dloa/media-protocol#publish-artifact)  
[editArtifact](https://github.com/dloa/media-protocol#edit-artifact)  
[transferArtifact](https://github.com/dloa/media-protocol#transfer-artifact)  
[deactivateArtifact](https://github.com/dloa/media-protocol#deactivate-artifact)  

###Publishing fee formulae:  
The OIP formula for calculating the **publish fee** is closed-loop and based on inputs found either in the Florincoin blockchain or in the publish message. It is calculated as a function of either (1) commercial value to the Publisher or (2) if it is being offered for free, as a function of its size in the blockchain.  
  
[Publish Fee, Free Artifact](https://github.com/dloa/sdk/blob/master/formulae.md#pf)  
[Publish Fee, Commercial Artifact](https://github.com/dloa/sdk/blob/master/formulae.md#pc)

---

##Captured Value  
![alt text](https://raw.githubusercontent.com/dloa/sdk/master/captured%20value%20stack.png "Value Capture Stack")  
