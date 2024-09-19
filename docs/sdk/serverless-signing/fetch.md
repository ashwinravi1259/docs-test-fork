import FeedbackComponent from "@site/src/pages/feedback.md";

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Signing within a Lit Action using EIP-191

## Overview

Unlike traditional smart contract ecosystems, Lit Actions can natively talk to the external world. This is useful for things like fetching data from the web, or sending API requests to other services.

The Lit Action below will get the current temperature from the [National Weather Service](https://www.weather.gov/) API, and ONLY sign a txn if the temperature is forecast to be **above 60 degrees F**. Since you can put this HTTP request and logic that uses the response directly in your Lit Action, you don't have to worry about using a 3rd party oracle to pull data in.

## Prerequisites

- Basic understanding of [PKPs](../../../user-wallets/pkps/overview)
- Basic understanding of [Lit Actions](../serverless-signing/quick-start)

## Complete Code Example

The complete code example is available in the [Lit Developer Guides Code Repository](https://github.com/LIT-Protocol/developer-guides-code/tree/master/lit-action-using-fetch). There you can find a Node.js and browser implementation of this example code.

### Example Lit Action

The return value of `ethPersonalSignMessageEcdsa` (the `sigShare` variable in this example) is set to a boolean value of `true` if the signature was successfully generated, and `false` otherwise. The Lit Action will also return the complete signature as an object under the `sigName` key.

```jsx
const _litActionCode = async () => {
  try {
    const url = "https://api.weather.gov/gridpoints/TOP/31,80/forecast";
    const resp = await fetch(url).then((response) => response.json());
    const temp = resp.properties.periods[0].temperature;
    console.log("Current temperature from the API:", temp);

    if (temp < 60) {
      Lit.Actions.setResponse({ response: "It's too cold to sign the message!" });
      return;
    }

    const sigShare = await LitActions.signEcdsa({ toSign, publicKey, sigName });
    Lit.Actions.setResponse({ response: sigShare });
  } catch (error) {
    Lit.Actions.setResponse({ response: error.message });
  }
};

export const litActionCode = `(${_litActionCode.toString()})();`;
```

## Important Considerations
You can also use fetch() inside a Lit Action to write data, but you **must be careful**. The HTTP request will be run N times where N is the number of Lit Nodes.

Some operations give the same result no matter how many times you repeat them, while others don't. For example:

SQL Insert: Running it 10 times creates 10 rows - the result changes each time.
SQL Update: Running it 10 times only changes the row once - repeating doesn't affect the outcome.

When using fetch() to write data, it's best if the server operation is the second type. This way, if the request accidentally repeats (due to network issues or user actions), it won't cause unwanted duplicates or changes.

## Summary
This guide demonstrates how to sign an EIP-191 message using Lit Actions.

If you'd like to learn more about Lit Actions, check out the [Lit Actions SDK](https://actions-docs.litprotocol.com/), or our [Advanced Topics](https://developer.litprotocol.com/category/advanced-topics-1) section on Lit Actions.

<FeedbackComponent/>
