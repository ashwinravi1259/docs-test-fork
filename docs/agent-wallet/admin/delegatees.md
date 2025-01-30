# Delegatee Management

A delegatee is an entity that can be assigned to manage the Agent Wallet on behalf of the owner. The Admin can add, remove, and manage delegatees for their Agent Wallet.

## How Delegatees Work

Assigning delegatees requires the Admin to know the Ethereum address of the delegatee, since the delegatee will be expected to authenticate with the Lit network within the [executeTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Delegatee.html#executeTool) method. 

To authenticate with the Lit network and to have the delegatee verify their identity, they are expected to sign a Sign-in With Ethereum (SIWE) message and generate [Session Signatures](../../../sdk/authentication/session-sigs/intro.md).

## Adding Delegatees

To add a delegatee to an Agent Wallet ([PKP](../../../user-wallets/pkps/overview.md)), you can use the [addDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#addDelegatee) method.

## Removing Delegatees

To remove a delegatee from an Agent Wallet, you can use the [removeDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#removeDelegatee) method.

## Viewing Delegatees

You can view the delegatees that are assigned to an Agent Wallet by using the [getDelegatees](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getDelegatees) method. This will return an array of delegatee addresses that are assigned to the Agent Wallet.

## Checking Delegatee Status

To check if a specific address is a delegatee of the Agent Wallet, you can use the [isDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#isDelegatee) method. 