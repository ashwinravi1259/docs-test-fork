# Admin Overview

The admin is the entity that creates and manages the Agent Wallet. They are responsible for:

1. Managing PKPs (Agent Wallets)
2. Managing delegatees
3. Managing tools
4. Setting and managing policies

## Transferring Ownership of the Agent Wallet

To transfer the ownership of the Agent Wallet, you can use the [transferPkpOwnership](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#transferPkpOwnership) method. This will send the PKP NFT to the new Admin's address specified in the execution parameters.

## Creating a New Agent Wallet

To create a new Agent Wallet, you can use the [mintPkp](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#mintPkp) method. This will mint a new PKP NFT to the Admin's wallet address and save it in localStorage. 

## Viewing Owned Agent Wallets

To see the Agent Wallets that the Admin owns, you can use the [getPkps](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getPkps) method. This will return an array of PKP metadata that the Admin owns.

## Viewing Information About an Agent Wallet

To retrieve information about a specific PKP by its token ID, you can use the [getPkpByTokenId](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getPkpByTokenId) method. This will return the metadata for the specified PKP NFT.

## Additional Documentation

For more detailed information about specific admin functionalities, please refer to:

- [Delegatee Management](./delegatees.md) - Learn about adding, removing, and managing delegatees
- [Tool Management](./tools.md) - Learn about registering, permitting, and managing tools
- [Policy Management](./policies.md) - Learn about setting and managing policies for tools and delegatees 