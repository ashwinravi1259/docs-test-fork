# Agent Wallet Overview

The Lit Agent Wallet (LAW) is a powerful tool that enables secure delegation of wallet operations through a system of administrators, delegatees, tools, and policies. It's built on top of [Programmable Key Pairs (PKPs)](../user-wallets/pkps/overview.md) and provides a flexible framework for managed wallet access.

The full repository for the Lit Agent Wallet is available on [GitHub](https://github.com/LIT-Protocol/agent-wallet).

## Core Concepts

### Admin
The Admin is the owner of the Agent Wallet and has full control over its management. They are responsible for:
- Creating and managing PKPs (Agent Wallets)
- Adding and removing delegatees
- Registering and managing tools
- Setting and enforcing policies

### Delegatees
Delegatees are entities that can execute operations on behalf of the Agent Wallet. They:
- Must authenticate using Sign-in With Ethereum (SIWE)
- Can execute tools permitted by the Admin
- Operate within the constraints of policies set by the Admin
- Have access to specific PKPs assigned to them

### Tools
Tools are the building blocks of Agent Wallet functionality, represented by [Lit Actions](../sdk/serverless-signing/overview.md) published on IPFS. They:
- Must be registered by the Admin
- Can be permitted for specific delegatees
- Can be enabled or disabled without removal
- Execute specific operations on behalf of the Agent Wallet

#### Terminology

- **Registered**: When referring to tools from the Admin's perspective (e.g., "registered tools" are tools that have been added to the Agent Wallet by the Admin)
- **Permitted**: When referring to tools from the Delegatee's perspective (e.g., "permitted tools" are tools that a specific delegatee is allowed to execute)

### Policies
Policies are rules that govern how delegatees can use tools. Policies are also represented by [Lit Actions](../sdk/serverless-signing/overview.md) published on IPFS. They are called within the Tool Lit Action to enforce the policies. They:
- Are immutable once published to IPFS
- Can restrict various parameters of tool execution
- Can be enabled or disabled by the Admin
- Apply to specific delegatee-tool combinations

## Security Considerations

1. **Authentication**
   - Delegatees must authenticate using SIWE
   - Admin controls ultimate access

2. **Smart Contract Enforcement**
   - Data such as delegatee addresses, tool and policy CIDs are stored within a [smart contract](https://github.com/LIT-Protocol/agent-wallet/tree/main/packages/aw-contracts) on Lit's [Chronicle Yellowstone](../connecting-to-a-lit-network/lit-blockchains/chronicle-yellowstone.md) blockchain
   - Only the Admin can update the smart contract

3. **Policy Enforcement**
   - Policies are immutable once published
   - Real-time policy checking during execution

4. **Access Control**
   - Granular permissions per delegatee
   - Tool-level access control

## Getting Started

1. [Admin Documentation](./admin/overview.md) - Learn how to set up and configure an Agent Wallet
2. [Delegatee Documentation](./delegatee/overview.md) - Learn how to use an Agent Wallet
3. [Build Your First Agent](./building.md) - Learn how to integrate an Agent Wallet into your own Agent (ElizaOS)
4. [Create New Tools](./new-tool.md) - Understand how to extend functionality with custom tools


