---
sidebar_position: 4
---

# LP Redemptions

---

## When Can LPs Redeem?

In general, LPs may redeem their $SNEKPOOL LP tokens for the underlying anytime. However, there are certain circumstances where redemptions may be temporarily disabled.

Consider the scenario of a large singular *Market* - think an event like the Superbowl or the World Cup - with a large sum of money riding on the outcome of the match. If LPs could redeem 100% of the time, the protocol could be exploited while the match is occuring. 

For example, consider if the match is a one-sided blowout and there are only 5 minutes remaining in the game and the exploiter knows that the protocol stands to lose a significant sum of money. It is in the exploiter's interest to withdraw their LP in the last minute before before the match is officially over so they do not share in paying out losses to the winning bettors.

Below, we will describe situations when LP redemptions are disabled to avoid the above scenario.

## Market States

To understand redemptions, we must first understand *Market States*. A *Market* can be divided into four distinct states:

1. **Open:** The period before the deadline when all bets are still allowed
2. **Pending:** The period after the deadline when all bets are closed, but before the results of the match are announced.
3. **Closed:** The period after the results of the match are announced, when winning *Tickets* may be claimed.
4. **Expired:** The period after which winning *Tickets* may not be claimable anymore. Winners are given a grace period of three months to claim their winnings. Afterwards, expired *Market* contracts are marked for permanent deletion and all winnings will be forfeited.

The most important case for redemptions are *Markets* that are currently marked as *Pending*.

## Exposure 

The *Exposure* of any given *Market* is defined as the maximum amount the protocol can potentially lose. *Exposure* may be positive (in which case the protocol loses money) or negative (in which case the protocol makes money no matter the outcome). Note that *Exposure* can only be defined for *Open* or *Pending Markets*. Example:

> Suppose the Cleveland Cavaliers vs. Miami Heat Moneyline has the following action:
>
> * Total 20,000 USDC placed on Cleveland Cavaliers at +100 (American odds).
> * Total 100,000 USDC placed on Miami Heat at -150 (American Odds).
>
> Let's calculate the payouts if either side wins.
>
> * If the Cleveland Cavaliers win, the protocol collects 100,000 + 20,000 = 120,000 USDC in revenues from all Tickets and pays out 40,000 USDC to winning tickets, for a net profit of +80,000 USDC
> * If the Miami Heat win, the protocol collects 100,000 + 20,000 = 120,000 USDC in revenues from all Tickets and pays out 166,667 USDC to winning tickets, for a net loss of -46,667 USDC.
>
> Hence, the Exposure for this Market is 46,667 USDC, which would be realized if the Miami Heat win.

## Disabled Redemptions

The *Pending Exposure* for the $SNEKPOOL is defined as the sum of the exposure across all currently *Pending Markets*. This value represents the maximum amount that a malicious LP could potential withdraw last minute to avoid sharing in protocol losses.

The protocol maintains a *MaxPendingExposure* parameter, so that if the current *Pending Exposure* exceeds this amount, all LP from the pool redemptions will be temporarily disabled. However, this is only a temporary measure, and once the offending *Pending Markets* with the highest *Exposure* officially announce their results to become *Closed Markets*, the *Pending Exposure* should drop, and redemptions will once again resume.
