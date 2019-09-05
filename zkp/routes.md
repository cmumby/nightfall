# ZKP Micro-Service Routes 

This is the micro-service that handles the **mint, burn, transfer and shield** processes of the for ERC-20 and ERC-721 tokens in the nightfall enviorment. It also makes use of **[Zokrates](https://zokrates.github.io/)** to handle the zero-knowlege-proof features of the ERC-20 and ERC-721 Sheild Contract commitments. Routes provided by this service are typically accessed via the `api-gateway` micro-service. 

## API Routes
### ERC-20 Fungible Token Routes
#### `POST ft/mint`  

processing: Mints a certain amount of ERC-20 tokens.
-  inputs:
    ```
    { amount, address }
    ```
-  returns:
    ```
    {"statusCode":"data":{"message":}}
    ```
#### `POST ft/burn` 

processing: Burns a certain amount ERC-20 tokens.

-   inputs:
    ```
    { amount, address }
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
        { address }
        ```
-   returns:
        ```
        {"statusCode":"data":{ftAddress:}}
        ```
#### `GET ft/details` 
processing:  Makes a request for an ERC-20 token's name, symbol and balance.
-    inputs:
        ```
        { address }
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
        { tokenID, tokenURI }
        ```
-   returns:
        ```
       {"statusCode, "data":{"message"}}
        ```
#### `POST nft/burn` 
processing: A Burns an ERC-721 token.
-    inputs:
        ```
        { tokenID }
        ```
-   returns:
        ```
       {"statusCode, "data":{"message"}}
        ```


#### `POST nft/transfer` 
processing: Transfer an ERC-721 token to another account.
-    inputs:
        ```
        { tokenID, to }
        ```
-   returns:
        ```
       {"statusCode, "data":{"message"}}
        ```
#### `GET nft/address` 
procesing: Makes a request for an ERC-721 token from its address.
-    inputs:
        ```
        { address }
        ```
-   returns:
        ```
        {"statusCode":"data":{nftAddress:}}
        ```
#### `GET nft/details` 
processing:  Makes a request for an ERC-721 token's name, symbol and balance.
-    inputs:
        ```
        { address }
        ```
-   returns:
        ```
        {"data":{"balance","nftName":,"nftSymbol":}}
        ```
### ERC-20 Fungible Token Commitment Routes
#### `POST coin/mint` 
processing: Mints an ERC-20 coin commitment.
-  inputs:
    ```
    { A, pk_A } 
-  returns:
    ```
    {"statusCode","data":{"coin","coin_index","S_A","action_type"}}
    ```
#### `POST coin/burn` 
processing: Burns an ERC-20 coin commitment.
-  inputs:
    ```
    { A, sk_A, S_A, z_A, z_A_index, payTo } 
-  returns:
    ```
    {"statusCode","data":{"z_C","z_C_index"}}
    ```
#### `POST coin/transfer` 
processing: Transfers an ERC-20 coin commitment between two accounts.
-  inputs:
    ```
    { C, D, E, F, pk_B, S_C, S_D, sk_A, z_C, z_C_index, z_D, z_D_index } 
-  returns:
    ```
   {
      z_E,
      z_E_index,
      z_F,
      z_F_index,
      txObj,
      S_E,
      S_F,
    }
    ```

#### `POST coin/checkCorrectness` 
processing: Validates the accuracy of the ERC-20 commitment. 
-  inputs:
    ```
    { E, pk, S_E, z_E, z_E_index }
    ```
-  returns:
    ```
    { results }
    ```
#### `POST coin/sheild`
processing: sheilds the private data of an ERC-20 token committment with the help of zokrates. 
-  inputs:
    ```
    { coinShield }
    ```
-  returns:
    ```
    {
      message: 'CoinShield Address Set.',
    }
    ```

#### `GET coin/sheild`
processing: Gets the address of the shielded values of an of an ERC-20 token committment. 
-  inputs:
    ```
    { address } // from request headers
    ```
-  returns:
    ```
    { name, sheildAddress }
    ```
#### `DELETE coin/sheild`
processing: Deletes a shield for a ERC-20 committment. 
-  inputs:
    ```
    { address } // from request headers
    ```
-  returns:
    ```
    {
      message: 'CoinShield Address Unset.',
    }
    ```

### ERC-721 NON-Fungible Token Commitment Routes
#### `POST token/mint`
processing: Mints an ERC-721 coin commitment.
-  inputs:
    ```
    { A, pk_A } 
-  returns:
    ```
    {"statusCode","data":{
      z_A,
      z_A_index,
      S_A,
    }}
    ```
#### `POST token/burn`
processing: Burns an ERC-721 coin commitment.
-  inputs:
    ```
    { A, S_A, Sk_A, z_A, z_A_index, payTo } 
-  returns:
    ```
    {"statusCode","data":{"z_A"}
    ```
#### `POST token/transfer`
processing: Transfers an ERC-20 coin commitment between two accounts.
-  inputs:
    ```
    { C, D, E, F, pk_B, S_C, S_D, sk_A, z_C, z_C_index, z_D, z_D_index } 
-  returns:
    ```
   {
      z_B,
      z_B_index,
      txObj,
      S_B,
    }
    ```
#### `POST token/checkCorrectness` 
processing: Validates the accuracy of the ERC-721 commitment. 
-  inputs:
    ```
    { A, pk, S_A, z_A, z_A_index }
    ```
-  returns:
    ```
    { results }
    ```
#### `POST token/shield`
processing: sheilds the private data of an ERC-721 token committment with the help of zokrates. 
-  inputs:
    ```
    { tokenShield }
    ```
-  returns:
    ```
    {
      message: 'TokenShield Address Set.',
    }
    ```
#### `GET token/shield`
processing: Gets the address of the shielded values of an of an ERC-721 token committment. 
-  inputs:
    ```
    { address } // from request headers
    ```
-  returns:
    ```
    { name, sheildAddress }
    ```
#### `DELETE token/shield`
processing: Deletes a shield for a ERC-721 committment. 
-  inputs:
    ```
    { address } // from request headers
    ```
-  returns:
    ```
    {
      message: 'CoinShield Address Unset.',
    }
    ```