# Tool Management

Tools are the core functionality of the Agent Wallet. They are the actions that can be executed by delegatees on behalf of the Admin. The Admin is responsible for registering tools and managing tool permissions for delegatees.

## Tool Registration and Management

### Registering Tools

Before a tool can be used with an Agent Wallet, it needs to be registered. You can register a new tool using the [registerTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#registerTool) method.

To check if a tool is registered in the system, you can use the [isToolRegistered](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#isToolRegistered) method.

### Managing Tool Permissions

#### Permitting Tools

After adding delegatees to the Agent Wallet, you can permit them to execute tools using the [permitToolForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#permitToolForDelegatee) method.

#### Unpermitting Tools

To unpermit a tool for a specific delegatee, you can use the [unpermitToolForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#unpermitToolForDelegatee) method.

### Enabling and Disabling Tools

Once a tool has been permitted, you can enable and disable tools without removing them from the Agent Wallet's permitted tools using the [enableTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#enableTool) or [disableTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#disableTool) methods.

### Removing Tools

To completely remove a tool from the Agent Wallet, you can use the [removeTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#removeTool) method. This will remove all permissions and policies associated with the tool.

## Tool Information and Status

### Checking Tool Permissions

To check if a specific tool is permitted for a delegatee, you can use the [isToolPermittedForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#isToolPermittedForDelegatee) method.

### Viewing Tool Information

To see if a tool is registered for a delegatee, you can use the [getRegisteredTool](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getRegisteredTool) method. This will return the tool information if it is registered.

To view all tools, you can use the [getRegisteredToolsAndDelegateesForPkp](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getRegisteredToolsAndDelegateesForPkp) method. This will return an array of all tools and their delegatees, organized into:

- `toolsWithPolicies`: Object mapping tool IPFS CIDs to their metadata and delegatee policies
- `toolsWithoutPolicies`: Object mapping tool IPFS CIDs to their metadata without policies
- `toolsUnknownWithPolicies`: Object mapping unknown tool IPFS CIDs to their delegatee policies
- `toolsUnknownWithoutPolicies`: Array of tool CIDs without policies that aren't in the registry 