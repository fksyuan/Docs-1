### 3. Privacy Token

PlatONE provides the zero-knowledge proof tool and paillier homomorphic encryption algorithm lib for users to implement their privacy token, which could hide the user's balance and the amount in the transaction process. In order to protect the privacy of users while guaranteeing the security of the assets in the token contract, users need to use the offline tool to generate the key pair of the homomorphic encryption algorithm and the zero knowledge proof in the transaction process.

The functions of  privacy token mainly includes token issuance (initialization), user registration (upload his own public key to the token contract) and transfers. The above process requires both the offline tool and the online contract operations.

- Token issuance

  When the token contract is deployed, the contract owner is required to pre-use nizkpail (offline tool) to generate its own account public key, and pre-allocate all tokens (cipher text) .

- User registration

  The new user needs to generate a public-private key pair of the homomorphic encryption algorithm in advance. Since the contract does not provide an explicit registration interface, the transfer of the privacy token holder to the new user could be regarded as the registration operation of the new user. The initial state of the new user is the transaction amount (in cipher text form) of the transfer.

- Transfer

  The transfer requires a zero-knowledge proof of the transaction generated by the sender's offline. The proof is used as the input to the transaction for contract verification. The token contract will update the account status of both parties after verifying the validity of the proof by using  the homomorphic addition and subtraction operation.
  
