---
sidebar_position: 1
---

# Intents

An **intent** describes the trading outcome a user is willing to accept, rather than a specific route for executing a swap. In CoW Protocol, users typically express an intent through an **order** that specifies the tokens and amounts to trade, together with conditions such as a limit price and an expiration time.

For example, a user might authorise selling 1 WETH for **at least 2,000 USDC** before a specified deadline. This defines an acceptable outcome; it does not guarantee that the order will be settled.

## Why intents matter

By specifying an acceptable trading outcome rather than a fixed execution route, users allow [solvers](./solvers) to explore different ways of settling their orders within the authorised constraints.

In CoW Protocol, this flexibility enables solvers to compete using different liquidity sources and allows [batch auctions](./fair-combinatorial-auction) to create opportunities for matching compatible orders through a [Coincidence of Wants](../how-it-works/coincidence-of-wants). These mechanisms can contribute to [price improvement](../benefits/price-improvement) and more efficient settlement.

## From authorisation to settlement

Users typically authorise orders by signing their parameters off-chain. The protocol also supports [smart-contract signatures and on-chain pre-signing](/cow-protocol/reference/core/signing-schemes). Authorising an order does not itself execute a swap or transfer tokens. A settlement can occur only if the applicable order authorisation and on-chain constraints are satisfied.

For the next steps, see [How intents are formed](../how-it-works/how-intents-are-formed) and [Flow of an order](../how-it-works/flow-of-an-order).
