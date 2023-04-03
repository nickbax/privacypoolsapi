# privacypoolsapi
This repo contains [proposed API endpoints](https://nickbax.github.io/privacypoolsapi/ "proposed API endpoints") used by entities in the privacypools ecosystem. 

There are 4 entities in the ecosystem: 
- **Users**: seek to maximize their anonymity set and minimize hassle due to tainted anonymity sets.
- **Blockchain analysis companies**: analyze blockchain transactions using combination of open- and closed-source tools to identify illicit funds.
- **List Curation DAO**: Aggregate lists of illicit funds from multiple sources and curate Merkle trees which enable users to prove source of funds is licit.
- **VASPs**: Value-added service providers such as cryptocurrency exchanges which need to comply with OFAC and money laundering regulations. 

A diagram showing the typical user flow and interplay between ecosystem members is available[ here](https://miro.com/app/board/uXjVMY60aSE=/?share_link_id=407558010902 " here"). 
1. Users deposit to the privacy pool smart contract. 
2.  Various blockchain analysis companies analyze the transaction and determine whether it is "flagged".
3. ListDAOs periodically request listed of recently flagged transactions via the blockchain analysis companies' 'Retrieve multiple signed transactions by block' API endpoint. Flagged transactions are used to build 'inclusion' merkle trees, which include all unflagged transactions, and 'exclusion' merkle trees which can be used for "proof-of-innocence". 
4. ListDAOs publish their Merkle roots on-chain as well as via an API endpoint. 
5. When a user makes a withdrawal, they provide a proof showing that their transaction did not come from a flagged deposit.  Alternatively, they can withdraw despite being flagged or find an alternative Merkle tree which does not flag their transaction. 
6. If funds are deposited to a regulated VASP, the VASP can compare data from the listDAO and blockchain analysis company to prove that the funds did not come from a flagged source. 
7. Law enforcement and regulators benefit from a reduced anonymity set and search space for illicit funds. 

The proposed scheme here is deliberately bare bones. 
