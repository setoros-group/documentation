---
sidebar_position: 2
---

# Oddsmaking

---

## Raw Data Feeds

Lucky Snake takes a pragmatic approach to setting odds. Rather than set its own baseline odds, Lucky Snake sources raw data feeds from various betting *Markets* from established sportsbooks such as *Pinnacle Sports*, *Barstool*, *FanDuel*, *BetMGM*, *WynnBet*, and others. 

## Implied Probabilities

The raw data feeds are aggregated and standardized into *Implied Probabilities*. You can learn more about the various ways to express odds, including *Implied Probabilities* [here](https://www.investopedia.com/articles/dictionary/042215/understand-math-behind-betting-odds-gambling.asp).

Generally, sportsbooks include something called a *Vig* into their odds, which is a spread or commission on the odds and is usually how sportsbooks make money. TO extract the true *Implied Probability* each sports book is implicitly pricing, it is important to strip away the *Vig* to obtain each book's individual *De-Vigged Implied Probabilities*. Here is an example to work out the math:

> Suppose an example moneyline bet of New England Patriots -200 vs New York Jets +170 (American odds). First we need to convert American odds to Implied Probabilities. Note the math is slightly different for favorites versus underdogs:
>
> * New England Patriots (Favorite): 200 / ( 200 + 100) * 100 = 66.67%
> * New York Jets (Underdog): 100 / ( 170 + 100) * 100 = 37.04%
>
> Notice that the sum of the Implied Probabilities for both sides add up to 103.7%, which is greater than 100%. This implies a vig of 3.7%. We need to remove the vig by normalizing the probabilities:
>
> * New England Patriots (Favorite): 66.67% / (66.67% + 37.04%) = 64.29%
> * New York Jets (Underdog): 37.04% / ( 66.67% + 37.04%) = 35.71%
>
> The De-Vigged Implied Probabilities now sum up to exactly 100%. It can be physically interpreted as the sports book implying a 64.29% chance that the New England Patriots will win, versus a 35.71% chance that the New York Jets will win.

## Lucky Snake Odds

Once the individual *De-Vigged Implied Probabilities* for each sports book have been obtained, Lucky Snake takes a weighted average blend of all the sources to obtain its own theoretical mid odds. A directional *Skew* in favor of one side or the other in the *Market* is then added onto the mid odds. The *Skew* is based on the existing bets made by users on the protocol. If all bettors favor one side of a *Market* on Lucky Snake, the protocol will *Skew* the odds in favor of the other side to incentivize users to balance the risk on the protocol. Finally, Lucky Snake adds its own *Vig*, set by smart contract parameter, to either side of the *Market* to obtain the final odds that users can execute against on the platform.

## Data Feed Oracle

To maintain pragmatic transparency, data regarding odds such as the raw *Implied Probabilities* for each individual sports book, as well as the end-user *Implied Probabilities* for Lucky Snake, are pushed periodically onto an oracle smart contract on the blockchain, both at standard intervals and also when the line moves by a minimum significant margin. 

These odds data are recorded on the blockchain to ensure the protocol is pricing odds accurately and fairly. However, it is important to note that currently Lucky Snake uses a *private* oracle to publish these odds. Longer-term decentralization calls for the protocol to use a decentralized oracle such as Chainlink to obtain raw data feeds. This is a feature currently on the roadmap that the protocol will transition to over time.
