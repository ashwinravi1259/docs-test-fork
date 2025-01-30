# Tool Management

Tools are the core functionality of the Agent Wallet. They are the building blocks that allow delegatees to execute actions on behalf of the Admin. The Admin is responsible for registering tools and managing tool permissions for delegatees.

## Tool Registration

Before a tool can be used with an Agent Wallet, it needs to be registered. You can register a new tool using the [registerTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#registerTool) method.

To check if a tool is registered in the system, you can use the [isToolRegistered](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#isToolRegistered) method.

## Permitting Tools

After the Admin has added delegatees to the Agent Wallet, they can permit the delegatees to execute tools. 

To permit a tool for a specific delegatee, you can use the [permitToolForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#permitToolForDelegatee) method.

### Unpermitting Tools

To unpermit a tool for a specific delegatee, you can use the [unpermitToolForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#unpermitToolForDelegatee) method.

## Enabling and Disabling Tools

Once a tool has been permitted, the Admin has the ability to enable and disable tools without removing the tool from the Agent Wallet's permitted tools.

To enable or disable a tool, you can use the [enableTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#enableTool) or [disableTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#disableTool) methods.

## Tool Permissions

To check if a specific tool is permitted for a delegatee, you can use the [isToolPermittedForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#isToolPermittedForDelegatee) method.

## Removing Tools

To completely remove a tool from the Agent Wallet, you can use the [removeTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#removeTool) method. This will remove all permissions and policies associated with the tool.

## Tool Information

To see if a tool is registered (permitted) for a delegatee, you can use the [getRegisteredTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getRegisteredTool) method. This will return the tool information if it is registered.

If you would like to see all tools, you can use the [getRegisteredToolsAndDelegateesForPkps](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getRegisteredToolsAndDelegateesForPkps) method. This will return an array of all tools and the delegatees that have access to them, organized into:

- `toolsWithPolicies`: Object mapping tool IPFS CIDs to their metadata and delegatee policies
- `toolsWithoutPolicies`: Object mapping tool IPFS CIDs to their metadata without policies
- `toolsUnknownWithPolicies`: Object mapping unknown tool IPFS CIDs to their delegatee policies
- `toolsUnknownWithoutPolicies`: Array of tool CIDs without policies that aren't in the registry 