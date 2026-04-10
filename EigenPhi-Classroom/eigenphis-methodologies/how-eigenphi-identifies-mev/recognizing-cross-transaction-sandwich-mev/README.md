# Recognizing Cross-Transaction Sandwich MEV

Cross-transaction structural analysis is an extension of the above intra-transaction analysis approach.

**Processes for Sandwich MEV Identification:**

* Analyze all the trades and liquidity additions in a given block.
* Use the trades identified in step one to search for sandwich pair trades within the block: these are trades in which the from address is the same, they occur in the same liquidity pool, and the trade direction is opposite.
* Once a sandwich trade has been identified, locate the victim transaction between the two sandwich trades: this transaction must have an address different from that of the attacker, occur in the same liquidity pool, and have a trade direction that is the same as the frontrun transaction.
* If a complete set of frontrun, victim, and backrun transactions is identified, we deem the trade to be a sandwich trade.
