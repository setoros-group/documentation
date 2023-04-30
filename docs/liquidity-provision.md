---
sidebar_position: 3
title: Liquidity Provision
---

<head>
    <title>Setoros Protocol</title>
    <meta name="title" property="og:title" content="Setoros Protocol" />
    <meta name="description" content="Documentation | Intro" />
    <meta name="description" property="og:description" content="Documentation | Intro" />
    <meta name="image" property="og:image" content="https://i.imgur.com/7dbH48C.png" />
    <meta name="twitter:title" content="Setoros Protocol" />
    <meta name="twitter:description" content="Documentation | Intro" />
    <meta name="twitter:image" content="https://i.imgur.com/7dbH48C.png"/>
    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:site" content="@setoros" />
</head>

---

## History of Decentralized Sportsbetting Protocols

Many decentralized sportsbetting protocols have attempted to decentralize the *House*, with various implementations such as allowing users to set their own odds (back and lay bets), or creating liquidity pools for various betting Markets, among others. However, these protocols have so far all largely failed to achieve mainstream success for one primary reason: **LOW LIQUIDITY**.

## Local vs Global Liquidity Pools

The sportsbetting protocols with a *Decentralized House* as described above have historically implemented it via *Local Liquidity Pools*. This means that for every *Betting Market*, there must be a separate liquidity pool to fund it. So for example, if there are three *Betting Markets* (Example: LA Lakers vs LA Clippers, Brooklyn Nets vs New York Knicks, Detroit Pistons vs Chicago Bulls), that would be three separate pools. Moreover, if the protocol wanted to support three different currencies (Example: USDC, ETH, BTC), that would mean a total of 3x3 = 9 separate liquidity pools. This is severely wasteful of LP funds and does not scale: For 100 betting markets and 3 different currencies, that would be 300 different pools!

Setoros takes a small shift in mindset to create a fundamentally different approach to liquidity provision that solves the *low liquidity problem* using *Global Liquidity Pools*. Enter the **TOROPOOL** LP token.

## $TOROPOOL LP tokens

The $TOROPOOL LP token acts a central treasury for all open *Betting Markets*, denominated in a single underlying currency. For example, the **TOROPOOL-USDC** token allows LPs to deposit USDC in order to mint a proportional amount of new **TOROPOOL-USDC** tokens. All USDC-denominated *Betting Markets* use the funds locked inside the **TOROPOOL-USDC** contract to pay out its winners. Conversely, all profits from losing bettors flow back into the **TOROPOOL-USDC** contract. Here is an example to make this more concrete:

> Suppose the **TOROPOOL-USDC** Token currently has 1,000,000 USDC locked inside. Suppose also there is currently one open Betting Market, Los Angeles Lakers vs. Boston Celtics Moneyline, with the following action:
>
> * Total 100,000 USDC placed on Los Angeles Lakers at +100 (American odds).
> * Total 125,000 USDC placed on Boston Celtics at -150 (American odds).
>
> Lets calculate the total payout to winning bets vs the total collected from losing bets for each team win outcome.
>
> * If Los Angeles Lakers win: Total Payout to winners: 100,000 USDC, total collected from losers: 125,000 USDC
> * If Boston Celtics win: Total Payout to winners: 83,333 USDC, total collected from losers: 100,000 USDC
>
> Hence, the net House PnL for each team win outcome is:
>
> * If Los Anageles Lakers win: +25,000 USDC
> * If Boston Celtics win: + 16,667 USDC
>
> If the Boston Celtics win, the TOROPOOL-USDC contract must transfer 83,333 USDC to the Los Anageles Lakers vs Boston Celtics Market in order to pay out all the winners. However, the TOROPOOL-USDC contract also receives 100,000 USDC from the Market to account for all the losing bets. Hence, the TOROPOOL-USDC USDC balance increases by net +16,667 USDC.
>
> Suppose that prior to the game results, the TOROPOOL-USDC token currently has 1,000,000 USDC total value locked, and that User A had deposited 100,000 USDC to own 10% of the TOROPOOL-USDC tokens. They may redeem their LP tokens anytime prior to the game for the original 100,000 USDC. After the game results in a Boston Celtics win, there is now 1,016,667 USDC total value locked inside the TOROPOOL-USDC token. Since User A owns 10% of the LP tokens, he can now redeem them for 101,667 USDC, a net profit of 1,667 USDC for them.
 
In this way, the TOROPOOL-USDC token serves as a global liquidity pool for all betting Markets denominated in USDC. Similarly, the protocol can also support bets denominated in ETH or BTC via an analogous TOROPOOL-ETH token or TOROPOOL-BTC token. Even with 100 open Betting Markets, the SNEK model only needs 3 liquidity pools to support them all - a far more sustainable *Decentralized House* model with deep liquidity for bettors.
