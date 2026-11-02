---
sidebar_position: 3
---

# Fair Combinatorial Batch Auction

CoW Protocol groups eligible orders expressing users' [trading intents](./intents) into off-chain batch auctions. [Solvers](./solvers) propose settlement solutions (also called **bids**) that may cover orders on one token pair or combine orders across different pairs. The auction evaluates these proposals and may select more than one winning solution.

![The Auctions](/img/concepts/batch-auctions.png)

## How the auction works

The auction is **combinatorial** because it considers combinations of proposed solutions, rather than requiring a single solver to settle the entire batch.

It is **fair** according to a defined, score-based test. For each *directed token pair* (the same sell token and buy token, in the same direction) with an available single-pair proposal, the auction establishes a reference score from the highest-scoring such proposal. A proposal combining different directed pairs is filtered out if its score on any pair falls below the corresponding reference, where one exists.

The auction ranks eligible solutions by [competition score](/cow-protocol/reference/core/auctions/the-problem) and selects compatible winners according to its [selection rules](/cow-protocol/reference/core/auctions/competition-rules). Higher-scoring solutions are considered first, up to a configured maximum number of winners. The score reflects proposed trading outcomes and applicable protocol fees. The fairness test does not guarantee a particular price for every order or the best price available across all markets.

## Why the auction matters

Considering orders together can create opportunities to match compatible orders directly through a [Coincidence of Wants](../how-it-works/coincidence-of-wants), use different liquidity sources, and reduce some settlement costs.

Solutions are also subject to [uniform directional clearing-price rules](/cow-protocol/reference/core/auctions/competition-rules#off-chain-protocol), with defined exceptions. These rules apply within each solution, and winner selection prevents different winning solutions from covering the same directed token pair. Together with other features of CoW Protocol, they can help [mitigate certain forms of MEV](../benefits/mev-protection), but do not eliminate all MEV risks.

The scoring, fairness, and uniform-pricing requirements are part of the off-chain competition rules. They are distinct from the user's order constraints enforced by the settlement contract. For details, see the [auction mechanism](/cow-protocol/reference/core/auctions) and [solver competition rules](/cow-protocol/reference/core/auctions/competition-rules).
