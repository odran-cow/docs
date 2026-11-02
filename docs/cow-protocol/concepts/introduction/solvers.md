---
sidebar_position: 2
---

# Solvers

**Solvers** are participants in CoW Protocol that compete to propose settlement solutions for orders expressing users' [trading intents](./intents). A **settlement solution** specifies which eligible orders could be filled and how the required liquidity would be sourced.

In this documentation, *solver* can refer either to a participating operator or to its software. A solver setup typically combines a [solver engine](/cow-protocol/tutorials/arbitrate/solver/solver-engine), which computes solutions, and a [driver](/cow-protocol/tutorials/arbitrate/solver/driver), which connects to the auction infrastructure and handles settlement submissions. These functions may be implemented together or operated separately, including by different parties.

![Solvers](/img/concepts/solvers.png)

## What solvers do

In a [batch auction](./fair-combinatorial-auction), solvers may match compatible orders through a [Coincidence of Wants](../how-it-works/coincidence-of-wants) or use liquidity sources available to them, such as decentralised exchanges.

The [auction mechanism](/cow-protocol/reference/core/auctions) evaluates proposed solutions according to defined competition rules and may select one or more winners. Selected solutions may then be submitted for on-chain settlement, subject to the checks enforced by the [settlement contract](/cow-protocol/reference/contracts/core/settlement).

## Why solver competition matters

Different solvers may propose different ways to use available liquidity and match orders. This competition can create opportunities for more efficient settlement and [price improvement](../benefits/price-improvement), but neither is guaranteed for any particular order.

## Participating as a solver

Anyone can develop a solver, but joining the live competition requires [onboarding and authorisation](/cow-protocol/tutorials/solvers/onboard). Participating solvers may receive [COW rewards](/cow-protocol/reference/core/auctions/rewards) under the applicable reward rules.
