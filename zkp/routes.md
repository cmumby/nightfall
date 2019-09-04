# ZKP Micro-Service Routes 

This is the micro-service that handles the **mint, burn, transfer and shield** processes of the for ERC-20 and ERC-721 tokens in the nightfall enviorment. It also makes use of **[Zokrates](https://zokrates.github.io/)** to handle the zero-knowlege-proof features of the ERC-20 and ERC-721 Sheild Contract commitments. Routes provided by this service are typically accessed via the `api-gateway` micro-service. 

## API Routes
### ERC-20 Fungible Token Routes
#### `POST ft/mint`  

processing: Mints a certain amount of ERC-20 tokens.
-  inputs:
    ```
    {amount, address}
    ```
-  returns:
    ```
    {"statusCode":"data":{"message":}}
    ```
#### `POST ft/burn` 

processing: Burns a certain amount ERC-20 tokens.

-   inputs:
    ```
    {amount, address}
    ```
-  returns:
    ```
    {"statusCode":"data":{"message":}}
    ```
#### `POST ft/transfer`  

processing : Transfers an ERC-20 token between addresses.
-    inputs:
        ```
        {amount, toAddress}
        ```
-   returns:
        ```
        {"statusCode":"data":{"message":}}
        ```
#### `GET ft/address` 

processing : Makes a request for an ERC-20 token from its address.
-    inputs:
        ```
        {address}
        ```
-   returns:
        ```
        {"statusCode":"data":{ftAddress:}}
        ```
#### `GET ft/details` 
processing:  Makes a request for an ERC-20 token's name, symbol and balance.
-    inputs:
        ```
        {address}
        ```
-   returns:
        ```
        {"data":{"balance":"0","ftName":,"ftSymbol":}}
        ```

### ERC-721 NON-Fungible Token Routes
#### `POST nft/mint` 
processing: Mints an ERC-721 token.
-    inputs:
        ```
        {tokenID, tokenURI}
        ```
-   returns:
        ```
       {"statusCode, "data":{"message"}}
        ```
#### `POST nft/burn` 
processing: A Burns an ERC-721 token.
-    inputs:
        ```
        {tokenID}
        ```
-   returns:
        ```
       {"statusCode, "data":{"message"}}
        ```


#### `POST nft/transfer` 
processing: Transfer an ERC-721 token to another account.
-    inputs:
        ```
        {tokenID, to}
        ```
-   returns:
        ```
       {"statusCode, "data":{"message"}}
        ```
#### `GET nft/address` 
procesing: Makes a request for an ERC-721 token from its address.
-    inputs:
        ```
        {address}
        ```
-   returns:
        ```
        {"statusCode":"data":{nftAddress:}}
        ```
#### `GET nft/details` 
processing:  Makes a request for an ERC-721 token's name, symbol and balance.
-    inputs:
        ```
        {address}
        ```
-   returns:
        ```
        {"data":{"balance":"0","nftName":,"nftSymbol":}}
        ```
### ERC-20 Fungible Token Commitment Routes
- `POST coin/mint` : A request to a mint an ERC-20 coin commitment.
- `POST coin/burn` : A request to a mint an ERC-20 coin commitment.
- `POST coin/transfer` : A request to transfer an ERC-20 coin commitment.
- `POST coin/checkCorrectness` : A requets to validate all the paramters needed for a proper coin commitment

### ERC-721 NON-Fungible Token Commitment Routes
- `POST token/mint` : A request to a mint an ERC-721 token.
- `POST token/burn` : A request to a mint an ERC-721 token.
- `POST token/transfer` : A request to transfer an ERC-721 token.
- `POST token/shield` : A request shield a token.