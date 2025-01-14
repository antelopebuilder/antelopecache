# antelope{cache}: A sovereign RAM mining protocol for Antelope Chains

\-lc  
www.antelopecache.com

**Abstract:** A sovereign mining protocol for Antelope Chains that utilizes Antelope’s bona fide native resource RAM, akin to Bitcoin’s utilization of physical hardware; fostering an open market where participants compete to earn market share. This is achieved by virtue of: RAM Caching,  trustless governance through weighted permission logic enabling inline modification of Application Binary Interface ( ABI ) and WebAssembly ( WASM ) by its stakeholders, and a token with exceptionally limited supply pegged to RAM named CACHE.

**1\.  Introduction** 

Antelope Chains are a digital diorama of real world finance and nation governance. In its current state, these chains carry politized governance enabling a select few the ability to adjust network policies including those which affect the cost of resources that enable trade and the inflationary nature of its native core tokens ( *EOS, WAX, TLOS; etc* ). These circumstances have uniquely positioned Antelope Chains to adopt a contract that can attract renewed interest and alternate investment opportunities. Any reference to \`eosio\` will represent the respective chain in which \`antelopcache\` is deployed *( account/contract referenced as* \`antelopcache\` *).*  
Outside of physical hardware and the regenerative nature of CPU/NET, RAM governed by Block Producers (BP’s) and a Bancor Algorithm¹, is the primary cost for any Antelope Chain participant. Early contracts capitalized on the speculative potential of emerging RAM markets, however, these attempts were thwarted by exceptional inflationary policies. RAM is a depreciative commodity with real world capital amortization, its utilization influences price action and serves as a catalyst for renewed/continued network growth.  
Antelope Chains carry powerful customizable authorities for accounts/contracts which may include control over: funds & ABI/WASM alteration; however, existing solutions carry varied degrees of centralized risk. Common approaches for semi-mutable contracts or distributed governance include: permissions split among keys/accounts; temporary immutability ², allowing accounts/contracts to lock permissions for a period of time; total immutability via permission nullification \`eosio.null\`, making ABI/WASM updates impossible; and the \`eosio.code\` permission for inline actions, resource restricted on select chains unless actioned by a privileged account.  
Antelope Chain users have limited stores of value. The primary medium of exchange and common denominator in Antelope markets are its native core tokens, all of which share the same inflationary fiat nature that blockchain enthusiasts seek to escape. Meanwhile, the most popularly traded Antelope based tokens carry exorbitant supplies which require exorbitant volume to motivate the volatility sought in an already niche market.   
We propose a mining contract for Antelope Chains that utilizes RAM as a resource to mine tokens, a trustless sovereign permission structure to promote distributed governance, and a dynamic inflationary token “CACHE” with an exceptionally limited supply appropriate for its environment.  
**2\. RAM Caching**

A blend of Proof of Stake and Proof of Storage, *“RAM Caching”* is an Antelope Chain specific protocol, transforming  RAM into a resource that when purchased and reserved grants mining participants the privilege to earn market share of a new token CACHE by weight of  RAM owned aka “Cached”.  
After registration as a cacheminer, any native core tokens deposited into the \`antelopcache\` contract with memo: *“increase\_bytes”* are converted into RAM and held in an \`antelopcache\` managed account \`cachereserve\`; each byte representing the direct mining/voting weight for each cacheminer. Any account may action \`antelopcache::mineblock\` immediately after each scheduled block subsidy to log block details onto the \`antelopcache::tokensubsidy\` table. Cacheminers are then able to reserve their portion of the block reward via the \`antelopcache::claim\` action  in the form of shares, followed by  the \`antelopcache::redeem\` action to emancipate their shares to transactable CACHE; mining weight adjustments are possible only after iterating through the latest subsidy from the \`antelopcache::tokensubsidy\` table. \`antelopcache\` is a RAM custodian with dynamically shifting power, requiring an unconventional governance logic.

**3\.  Sovereign Contract** 

\`antelopcache\` carries the singular permission \`antelopcache@eosio.code\` and is governed exclusively by the mining weight of its participants who can vote to change contract ABI & WASM via inline actions to privileged account \`eosio.msig\`.  
Given all checks and criteria are met, cacheminers are able to link any pre-proposed \`eosio::setabi\`and \`eosio::setcode\` actions pertaining to \`antelopcache\` from the \`eosio.msig::proposal\` table for vote on the \`antelopcache: proposals\` table. Each active cacheminer is entitled to a singular vote equivalent to its total mining weight through proposal expiration. If ‘x’ proposal gathers the required \`percentage of voting consensus\` for ‘y’ blocks,  the proposal may then be realized via the \`antelopcache::propreview\` subsequently actioning \`eosio.msig::approve\` and \`eosio.msig::exec\`.  Undoubtedly, it is possible for any account with sufficient voting weight to link, approve, and execute a malicious proposal, as such this contract requires a token that stimulates competition to enhance contract security through weighted distribution.

**4\.  Inflation** 

\`antelopcache\` carries a dynamic inflationary schedule to incentivize and protect cacheminers. 1,048,574.0000 CACHE  of the supply is mined via RAM Caching beginning with the initial block reward of 26.2144 CACHE,  halved every 20,000 blocks, each lasting 3600 seconds over the course of 20 eras.  An equivalent supply of 1,048,574.0000 CACHE is issued at Genesis and burned over the life of the contract to mitigate any potential RAM depreciation and counteract BP’s *Connector Weight* ³ adjustments which would adversely affect RAM prices, and by extension, the returns for any antelope{cache} participant.  Approximately 10% or 116,508.0000 CACHE of total possible supply is issued to the developer at contract bios, the chart below depicts  the mining schedule disregarding developer & burn supply allocations.

| Reward Era | CACHE/Block | Starting CACHE | CACHE Added | Ending CACHE | \# of Blocks | Blocktime (*seconds*) |
| ----: | ----: | ----: | ----: | ----: | ----: | ----: |
| 1 | 26.2144 | 0.0000 | 524,288.0000 | 524,288.0000 | 20,000 | 3600 |
| 2 | 13.1072 | 524,288.0000 | 262,144.0000 | 786,432.0000 | 20,000 | 3600 |
| 3 | 6.5536 | 786,432.0000 | 131,072.0000 | 917,504.0000 | 20,000 | 3600 |
| 4 | 3.2768 | 917,504.0000 | 65,536.0000 | 983,040.0000 | 20,000 | 3600 |
| 5 | 1.6384 | 983,040.0000 | 32,768.0000 | 1,015,808.0000 | 20,000 | 3600 |
| 6 | 0.8192 | 1,015,808.0000 | 16,384.0000 | 1,032,192.0000 | 20,000 | 3600 |
| 7 | 0.4096 | 1,032,192.0000 | 8,192.0000 | 1,040,384.0000 | 20,000 | 3600 |
| 8 | 0.2048 | 1,040,384.0000 | 4,096.0000 | 1,044,480.0000 | 20,000 | 3600 |
| 9 | 0.1024 | 1,044,480.0000 | 2,048.0000 | 1,046,528.0000 | 20,000 | 3600 |
| 10 | 0.0512 | 1,046,528.0000 | 1,024.0000 | 1,047,552.0000 | 20,000 | 3600 |
| 11 | 0.0256 | 1,047,552.0000 | 512.0000 | 1,048,064.0000 | 20,000 | 3600 |
| 12 | 0.0128 | 1,048,064.0000 | 256.0000 | 1,048,320.0000 | 20,000 | 3600 |
| 13 | 0.0064 | 1,048,320.0000 | 128.0000 | 1,048,448.0000 | 20,000 | 3600 |
| 14 | 0.0032 | 1,048,448.0000 | 64.0000 | 1,048,512.0000 | 20,000 | 3600 |
| 15 | 0.0016 | 1,048,512.0000 | 32.0000 | 1,048,544.0000 | 20,000 | 3600 |
| 16 | 0.0008 | 1,048,544.0000 | 16.0000 | 1,048,560.0000 | 20,000 | 3600 |
| 17 | 0.0004 | 1,048,560.0000 | 8.0000 | 1,048,568.0000 | 20,000 | 3600 |
| 18 | 0.0002 | 1,048,568.0000 | 4.0000 | 1,048,572.0000 | 20,000 | 3600 |
| 19 | 0.0001 | 1,048,572.0000 | 2.0000 | **1,048,574.0000** | 20,000 | 3600 |

During the \`antelopcache::mineblock\` action, CACHE  is burned proportional to the difference in the last recorded RAM price, if RAM price increased then no burn occurs, if RAM price decreases then CACHE is burned; otherwise CACHE is burned a constant rate of 10.6400 CACHE per block. Adjustments to \`eosio::global\` table or \`eosio::global2\` table  will change the rate of burn, such that if ‘new\_ram\_per\_block’ doubles to 2048 bytes per block, \`antelopcache\` burns 200% more CACHE, and conversely, if \`new\_ram\_per\_block\` drops to 512 bytes per block then \`antelopcache\` burns 50% less CACHE.  Lastly, in observation of resource management, only the latest 1024 block rewards are provisionally logged onto the \`antelopcache::tokensubsidy\` table, where cacheminers will regularly erase the earliest subsidy record on a first in first out basis regardless of claim status, meaning that any unclaimed CACHE subsidies will be considered lost.

 **5\. Conclusions**

We have laid out the framework of a unique mining contract for Antelope Chains. A sovereign contract governed only by the mining weight of its participants who stake  Antelope’s native resource RAM via RAM Caching to earn market share of a new token with exceptionally limited supply and dynamic tokenomics appropriately named: CACHE.

**6\. Forward Looking Statement**

Antelope Chain protocols are exceptionally malleable and are subject to change by its BP’s⁴. That being said, among other things, this contract was built with the intention of renting RAM by extension of  bytes held in reserve; an opportunity recently made possible on other contracts and configurable if so desired by antelope{cache} participants.

**References**

1\.  Bloxchanger. “Eosio-Lock, a Free Open Source Service Provides Temporary Immutability to               
       Eos Smart Contracts.” *Medium*, Medium, 27 Aug. 2019,    
       medium.com/@bloxchanger/eosio-lock-a-free-open-source-service-provides-temporary-  
       immutability-to-eos-smart-contracts-1c5e0ddf03e4.   
2\.  “Mine Eos Ram with RUTM.” *EOS Go* News, www.eosgo.io/news/mine-eos-ram-with-rutm/  
3\.  Larimer, Daniel. “Eosio Ram Market and Bancor Algorithm.” *Medium*, Medium, 4 July 2018,                             
      bytemaster.medium.com/eosio-ram-market-bancor-algorithm-b8e8d4e20c73.   
4\.  By EOS Network Foundation. “EOS RAM Evolution: Unlocking New Capabilities.”           
      Https://Eosnetwork.Com/Blog/Eos-Ram-Evolution/, 19 Mar. 2024,    
      [https://eosnetwork.com/blog/eos-ram-evolution/](https://eosnetwork.com/blog/eos-ram-evolution/).

*To my family and loved ones, for their unwavering support.*  
*This project is as much yours as it is mine.*
