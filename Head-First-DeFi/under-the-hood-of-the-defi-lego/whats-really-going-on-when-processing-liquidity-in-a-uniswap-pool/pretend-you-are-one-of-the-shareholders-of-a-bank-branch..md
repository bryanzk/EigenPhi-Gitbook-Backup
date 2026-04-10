# Pretend You Are One of the Shareholders of a Bank Branch.

First, take a look at the table below, which contains the information that concerns your interests when you become one of the shareholders of the branch.

<figure><img src="../../.gitbook/assets/1280X1280 (1).PNG" alt=""><figcaption></figcaption></figure>

* You put USD and CAD(Canadian dollars) into the branch. In return, you receive shares of the branch.
* The bank's database has internal data to store how many USD and CAD this branch owns, marked as "Internal USD" and "Internal CAD."
* Meanwhile, to keep your record right, the bank's database also shows how much USD and CAD you have put into the bank, marked as "External USD" and "External CAD."
* The bank branch has the data of the total shares of this branch, marked as "Entire Liquidity Share."
* Your shares of the branch are recorded as "Shareholder's Share."
* Now, when you put your USD and CAD assets into the bank branch as your contribution to the liquidity share of the branch, the amount of your contribution will be reflected as follows:
  * The amount of Internal USD will increase, adding your USD contribution.
  * The amount of Internal CAD will increase, adding your CAD contribution.
  * The amount of External USD is your USD contribution.
  * The amount of External CAD is your CAD contribution.
  * The number of Entire Liquidity Shares will increase, adding your shares based on your USD and CAD contribution.
  * The number of the Shareholder's Shares will increase, adding your shares based on your USD and CAD contributions.
  * All the operations above will generate an "adding" record of the internal bookkeeping for each operation.
* Let's consider what happens when you remove your USD and CAD assets from the bank branch's overall shares. The amount of your removal will be reflected as follows:
  * The amount of Internal USD will decrease, removing your USD contribution.
  * The amount of Internal CAD will decrease, removing your CAD contribution.
  * The amount of External USD is your USD removal.
  * The amount of External CAD is your CAD removal.
  * The number of Entire Liquidity Shares will decrease, removing your shares based on your USD and CAD removals.
  * The number of Shareholder's Shares will be your shares based on your USD and CAD removals.
  * All the operations above will generate a "removing" record of the internal bookkeeping for each operation.
