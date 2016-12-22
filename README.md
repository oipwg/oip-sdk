###Introduction  
The **Open Index Protocol** is a decentralized application (DApp) which unites a peer-to-peer distribution network (IPFS), a micropayments blockchain (Bitcoin), and a blockchain designed specifically to store messages.  
  
It’s primary purpose is to establish a **decentralized media index**, owned by no one collectively and, at the same time, each of it’s publishers individually. Thru the use of an open message schema and a simple set of mutually agreed-upon rules for core functions, the following permission-less “jobs” are created, which anyone can contribute toward, in exchange for direct financial reward of some sort:  
•**Publishers** of original content (**artifacts**) to the index *(paid by end users when they connect with an audience that finds their content valuable, at whatever price they and their market agree upon)*  
•**Miners** contributing proofs-of-work to the mutual protection of the index of artifacts *(paid by publishers for their actual costs plus their requested margin, governed by data-driven market feedback mechanisms, limited by demand for publishing)*  
•**Storage and distribution services** for the media files published to the index *(paid by publishers or patrons of content, governed by free floating market prices per MB stored per unit of time and per MB transmitted, limited by caps set per piece of content, since in most cases, a file having any more than ~20 seeders starts to see diminishing returns quickly)*  
•**Promoters** of artifacts published to the index *(paid directly by end users when they pay for a piece of media the promoter put in front of them, mostly over social media platforms, percent of total sale they get is limited by preferences determined by publishers)*  
•**Retailers** of artifacts published in the index *(paid directly by end users when they pay for a piece of media the retailer put in front of them, mostly using suggestion algorithms within a given front end/marketplace, percent of total sale they get is limited by preferences determined by publishers)*  

####JSON standards:  
[multipartData](https://github.com/dloa/media-protocol#multipart-data)  
[publishArtifact](https://github.com/dloa/media-protocol#publish-artifact)  
[editArtifact](https://github.com/dloa/media-protocol#edit-artifact)  
[transferArtifact](https://github.com/dloa/media-protocol#transfer-artifact)  
[deactivateArtifact](https://github.com/dloa/media-protocol#deactivate-artifact)  

####Standard formulae
The OIP formula for calculating the **publishing fee** is totally closed-loop and depends entirely on information found either in the Florincoin blockchain or in the publish message itself. It is calculated as a function of its commercial value to the Publisher or as a function of its size in the blockchain if it is being offered for free.
[PublishFreeArtifact](https://github.com/dloa/sdk/blob/master/formulae.md#pf)
[PublishCommercialArtifact](https://github.com/dloa/sdk/blob/master/formulae.md#pc)

##Software Stack to run a hosted web node  


##Software Stack to use as DApp
*described starting with the lowest level*  
1) TCP/IP: Connection between nodes  
2) Florincoin blockchain: Consensus of database contents  
3) OIP Daemon: Parsing of database down to *Index*  
4) Alexandria browser: Reference client to browse *Index*
4) Bitcoin Daemon: Interaction with commercial artifacts within *Index*  
5) IPFS Daemon: Fetching media files referenced by artifacts within *Index*  


##To be a “retailer” (i.e., to host a marketplace)  
Install a florincoin (http://florincoin.org/) wallet on your web server: https://github.com/florincoin/florincoin  
Enable RPC access to the florincoin wallet: https://github.com/dloa/alexandria-docs/blob/master/florincoin-lin64-install.md  
Install OIP-NPM, a node.js module built to enable making changes to the OIP index (register a publisher, publish an artifact, transfer ownership of an artifact, edit an artifact and deactivate an artifact): https://github.com/dloa/oip-npm  
Use our hosted OIPD API endpoint for reading the whole OIP index: https://api.alexandria.io/alexandria/v2/media/get/all  
Use our hosted OIPD API endpoint for searching the whole OIP index by any field: https://api.alexandria.io/alexandria/v2/search (endpoint usage: https://api.alexandria.io/docs/#get-a-specific-artifact)  
Build an interface using all of the above, or start by forking ours: https://github.com/dloa/alexandria-browser (for browsing) & https://github.com/dloa/publisher-web (for publishing) & https://github.com/dloa/paywall-web (paywall)  


##To be a contributor to the proof-of-work mining that protects the index  
Create an account on miningrigrentals.com
Make a new “pool profile”: algo Scrypt host api.alexandria.io port 3032 worker YOURFLORINCOINADDRESS password anythingyouwant
Create a miningrigrentals API key at: https://www.miningrigrentals.com/account/apikey
Install and start the autominer application: https://github.com/dloa/autominer-api
Fund your miningrigrentals.com wallet with some bitcoin, and the autominer-api will automatically start renting rigs if market conditions allow your minimum margin to be met
