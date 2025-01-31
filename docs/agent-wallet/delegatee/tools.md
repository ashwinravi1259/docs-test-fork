# Tool Execution

As a delegatee, you can execute tools that have been permitted to you by the Admin. Tool execution is subject to any policies that the Admin has set.

## Executing Tools

To execute a tool on behalf of the Admin, you can use the [executeTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Delegatee.html#executeTool) method. This method requires:

1. The tool's IPFS CID
2. The parameters required by the tool
3. Valid session signatures for authentication

## Viewing Available Tools

You can view the tools that have been permitted to you by using the [getPermittedToolsForPkp](https://agent-wallet.vercel.app/classes/agent_wallet_src.Delegatee.html#getPermittedToolsForPkp) method. This will show you:

- Tools you have access to with their associated policies
- Tools you have access to without policies
- Any unknown tools that have policies set

