# Delegatee Overview

A delegatee is an entity that can be assigned to manage the Agent Wallet on behalf of the owner. Delegatees can execute tools and interact with the Agent Wallet within the constraints set by the Admin's policies.

## Authentication

As a delegatee, you need to authenticate with the Lit network to execute tools. This is done by:

1. Signing a Sign-in With Ethereum (SIWE) message
2. Generating [Session Signatures](../../../sdk/authentication/session-sigs/intro.md)

This authentication process verifies your identity and ensures secure access to the Agent Wallet's functionality. In the Lit Agent Wallet, this functionality is done under the hood in the [executeTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Delegatee.html#executeTool) method, so you don't need to worry about it.

## Viewing Delegated PKPs

To view the PKPs delegated to you as a delegatee, you can use the [getDelegatedPkps](https://agent-wallet.vercel.app/classes/agent_wallet_src.Delegatee.html#getDelegatedPkps) method. This will return an array of PKPs that you have been delegated access to.

## Additional Documentation

For more detailed information about delegatee functionalities, please refer to:

- [Tool Execution](./tools.md) - Learn about executing tools as a delegatee
- [Policy Restrictions](./policies.md) - Learn about the policies that govern tool execution 