# What Were the Sandwich Searchers Capable of Yesterday?

This part illustrates the overall Sandwich MEV capabilities in the market using percentile distribution metrics.&#x20;

![](<../../.gitbook/assets/image (15).png>)

It might be a bit confusing at first look. So let’s start with the table below to understand the concept:

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F07dc8231-76c3-4411-bb37-11e5891000ea_762x182.png)

The table shows that the lowest 50% of transactions’ profit is mostly less than 2.66 USD; the 90% of transactions’ profit is mostly less than 92.91 USD; about 95% is less than 222.88 USD, and the highest profit is 33,074.98 USD.

Here is the table that exhibits the Total Sandwich MEV Volume/Profit/Cost/Revenue Distribution:

![](<../../.gitbook/assets/image (10).png>)

The first 4 rows of the table should now be more apparent. However, it’s important to remember that **the same column’s data in no way belongs to the same transaction.**&#x20;

We calculate the volume, profit, cost, revenue, and ROI distribution rankings separately. For example, a transaction’s cost is $42, ranking 50th. But its profit could be $20, more than the 50th profit, $1, and less than the 90th profit, $43, and vice versa.&#x20;

The ROI in the 5th row is also calculated independent of the data in the same column. It also shows the overall ROI distribution. So, therefore, the best ROI is 139897.7%, and the 95th one is 274.0%, etc.

With the knowledge of the data in the table, let’s examine the line charts again.&#x20;

In order to make the data more understandable, the chart's vertical axis is scaled in logarithms.&#x20;

The first one exhibits the **Volume** percentile distribution of the overall Sandwich MEV V.S. profit>1K USD Sandwiches V.S. MEV-Bot Sandwiches marked on Etherescan.

![](<../../.gitbook/assets/image (3).png>)

Please be noted that there are 3 vertical axes matching different lines.&#x20;

* Yellow axis on the right side and the yellow lines: Data of all the MEVs.
* Green axis on the left side and the green lines: Data of MEVs with over $1K profit
* Purple axis on the right side and purple line: Data of MEV-bot transactions.&#x20;

These 3 vertical axes have different scales to accommodate all the data points.

The figure above shows that at the 100th percentile, profit>$1K transaction's volume is the same as the Total, but larger than MEV-Bot.&#x20;

Move your cursor to a different percentile, and you can see other data points.

All the data can be found in the tables below, which are categorized in different dimensions to examine the other aspects of the data.&#x20;

**Remember that the same percentile’s data does not necessarily belong to the same transaction, except for the 100th one.**
