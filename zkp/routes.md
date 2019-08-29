#ZKP Micro-Service Routes 

This is the micro-service that handles the **mint, burn, transfer and shield** processes of the for ERC-20 and ERC-721 tokens in the nightfall enviorment. It also makes use of **[Zokrates](https://zokrates.github.io/)** to handle the zero-knowlege-proof features of the ERC-20 and ERC-721 Sheild Contract commitments. Routes provided by this service are typically accessed via the `api-gateway` micro-service. 

##API Routes
###ERC-20 Fungible Token Routes
- `POST ft/mint` : A request to a mint an ERC-20 token.
- `POST ft/burn` : A request to a burn an ERC-20 token.
- `POST ft/transfer` : A request to a transfer an ERC-20 token.
- `GET ft/address` : A request for an ERC-20 token's address.
- `GET ft/details` : A request for an ERC-20 token's information.

###ERC-721 NON-Fungible Token Routes
- `POST nft/mint` : A request to a mint an ERC-721 token.
- `POST nft/burn` : A request to a mint an ERC-721 token.
- `POST nft/transfer` : A request to transfer an ERC-721 token.
- `GET nft/address` : A request for an ERC-721 token's address.
- `GET nft/details` : A request for an ERC-721 token's information.

###ERC-721 NON-Fungible Token Commitment Routes
- `POST token/mint` : A request to a mint an ERC-721 token.
- `POST token/burn` : A request to a mint an ERC-721 token.
- `POST token/transfer` : A request to transfer an ERC-721 token.
- `POST token/shield` : A request shield a token.

###ERC-20 Fungible Token Commitment Routes
- `POST coin/mint` : A request to a mint an ERC-20 coin commitment.
- `POST coin/burn` : A request to a mint an ERC-20 coin commitment.
- `POST coin/transfer` : A request to transfer an ERC-20 coin commitment.
- `POST coin/checkCorrectness` : A requets to validate all the paramters needed for a proper coin commitment