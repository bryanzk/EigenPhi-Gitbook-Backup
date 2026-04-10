# Recognizing Atomic Arbitrage MEV Transactions

Since transactions can be highly complex and involve infinite unknown patterns, relying solely on specific transaction pattern matching is inadequate to identify new MEV patterns. To detect Arbitrage in transactions, we need a universal abstraction for transactions.To achieve this, we have established the following principles for recognition.

1. We define a transaction as a collection of asset transfers.
2. Then, we evaluate the outcomes of these transfers using a set of rules to determine if an MEV has occurred.
3. We break down a transaction into Transfers and Trades.
4. Our algorithm merges Transfers to form a Transfer Table.
5. Next, we use the Transfer Table to merge the rows with the same address and generate a Combined Transfer Table.

<figure><img src="../../../.gitbook/assets/water_gitbook3 (3).png" alt=""><figcaption><p>Principles for Recognition</p></figcaption></figure>

Our rule of thumb is: if the token balance of the nearest point to the "from" or "to" address of the transaction within a **strongly connected component** is positive, we regard this transaction as Arbitrage.

To help you better understand it, next, we will present a detailed process and an example to illustrate our algorithm based on the **Token Flow** graph generated in our **EigenTx** tool.
