# Arbitrage package

The arbitrage package would contain two, sometimes even three arbitrages, i.e., [this one](https://eigenphi.io/ethereum/tx/0x93d331ca38bcb540f13fbb9d47fe1272a11156c536bb212b5a82b8454383fa4c) identified by EigenPhi. Two arbitrages involving 3 tokens among 3 LPs combined together to rake profits in one transaction.

Usually, such action is to save the cost--gas fees--to finish two or more arbitrages. Another reason is to avoid being the victim of [Sandwich MEV](../sandwich-mev.md). To successfully employ a strategy like this, traders would use [flashbots](https://github.com/flashbots/pm), the open-source project that would bundle transactions and send the bundle to the miner without being exposed.&#x20;

In the broad sense, the mentioned arbitrages improve the efficiency of the DeFi market by bridging the price information. On the other hand, [Sandwich MEV](../sandwich-mev.md), also known as front-running, is terrible for the market and harms investors' interests.&#x20;
