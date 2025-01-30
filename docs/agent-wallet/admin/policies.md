# Policy Management

Policies are a set of rules specific to each delegatee that restrict their parameters for executing tools. Policies are published to IPFS to ensure that they are immutable and cannot be changed once published, however the Admin can always remove or change the policy by publishing a new policy to IPFS.

For example, for the ERC-20 sending tool, we can restrict the delegatee from:

- Sending more than a specific amount
- The recipients of the ERC-20 tokens
- The ERC-20 tokens that can be sent

## Setting Tool Policies

After a tool has been permitted, the Admin can set a policy for when the delegatee attempts to execute the tool.

To set a tool policy, you can use the [setToolPolicyForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#setToolPolicyForDelegatee) method.

### Removing Tool Policies

To remove a tool policy, you can use the [removeToolPolicyForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#removeToolPolicyForDelegatee) method.

## Enabling and Disabling Policies

Once a tool policy has been set for a delegatee, the Admin can enable and disable the policy without removing the policy from the Agent Wallet's policies.

To enable or disable a policy, you can use the [enableToolPolicyForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#enableToolPolicyForDelegatee) or [disableToolPolicyForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#disableToolPolicyForDelegatee) methods.

## Policy Parameters

To set specific parameters for a tool policy, you can use the [setToolPolicyParametersForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#setToolPolicyParametersForDelegatee) method.

To remove specific policy parameters for a delegatee, you can use the [removeToolPolicyParametersForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#removeToolPolicyParametersForDelegatee) method.

## Policy Retrieval

To get the complete policy configuration for a tool and delegatee, you can use the [getToolPolicyForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getToolPolicyForDelegatee) method.

To retrieve a specific policy parameter for a delegatee, you can use the [getToolPolicyParameterForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getToolPolicyParameterForDelegatee) method.

To see the policies that are set for a delegatee, you can use the [getToolPolicyParametersForDelegatee](https://agent-wallet.vercel.app/classes/agent_wallet_src.Admin.html#getToolPolicyParametersForDelegatee) method. This will resolve to return an array of policy parameter values. 