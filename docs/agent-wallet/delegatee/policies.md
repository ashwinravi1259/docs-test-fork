# Policy Restrictions

As a delegatee, your tool execution is governed by policies set by the Admin. These policies are immutable rules stored on IPFS that restrict how you can use tools.

## Understanding Your Policies

As a delegatee, you can view the policies applied to a specific Agent Wallet delegated to you by using the [getToolPolicy](https://agent-wallet.vercel.app/classes/agent_wallet_src.Delegatee.html#getToolPolicy) method.

Before executing a tool, you should check if a policy exists for the tool. If a policy exists, you must ensure that your intended parameters comply with the policy. This helps prevent failed transactions due to policy violations. 

## Policy Examples

Policies can restrict various aspects of tool execution. For example, with an ERC-20 sending tool, policies might restrict:

- Maximum amount you can send
- Which addresses you can send to
- Which tokens you can send
