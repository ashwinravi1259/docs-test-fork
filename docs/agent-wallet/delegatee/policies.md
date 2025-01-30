# Policy Restrictions

As a delegatee, your tool execution is governed by policies set by the Admin. These policies are immutable rules stored on IPFS that restrict how you can use tools.

## Understanding Your Policies

You can view the policies that apply to you using several methods:

1. Get all policy parameters with [getToolPolicyParametersForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getToolPolicyParametersForDelegatee)
2. Get a specific policy with [getToolPolicyForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getToolPolicyForDelegatee)
3. Get a specific policy parameter with [getToolPolicyParameterForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getToolPolicyParameterForDelegatee)

## Policy Examples

Policies can restrict various aspects of tool execution. For example, with an ERC-20 sending tool, policies might restrict:

- Maximum amount you can send
- Which addresses you can send to
- Which tokens you can send

## Policy Status

Before executing a tool, you should check if:

1. A policy exists for the tool
2. The policy is currently enabled
3. Your intended parameters comply with the policy

This helps prevent failed transactions due to policy violations. 