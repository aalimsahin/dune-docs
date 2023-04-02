[View code on GitHub](https://dune.com/docs/data-tables/community/flashbots/liquidations.md)

# Liquidations

The `liquidations` section of the Dune Docs project focuses on providing details related to executed liquidations. The `flashbots.liquidations` table contains information about liquidations executed using the MEV strategy. The table includes details such as the time of record creation, transaction hash, trace pattern related to the position of the transaction in the chain of all transactions related to the MEV trade, underlying token address of the debt to pay, amount received from the liquidation, protocol name, address of the liquidated user, address of the liquidator user, address of the received asset, block number, amount of purchased debt, and timestamp of the latest update of the file.

The purpose of this guide is to provide a detailed explanation of the `flashbots.liquidations` table and its columns. The guide also includes a link to query examples for liquidations by protocol. This information is useful for developers who want to understand how liquidations work and how to access the data related to executed liquidations.

An example of a query that can be run using the `flashbots.liquidations` table is the `Liquidations by Protocol` query, which can be found at [https://dune.com/queries/625715/1166880](https://dune.com/queries/625715/1166880). This query provides information about liquidations executed by protocol, including the protocol name, number of liquidations, total received amount, and average received amount.

Overall, the `liquidations` section of the Dune Docs project provides valuable information for developers who want to understand how liquidations work and how to access the data related to executed liquidations using the MEV strategy.
## Questions: 
 1. What is the purpose of the `flashbots.liquidations` table in the context of blockchain and how is it related to MEV (Miner Extractable Value)? 
- The `flashbots.liquidations` table contains details related to executed liquidations, which is another MEV strategy. It is related to MEV because it involves extracting value from transactions before they are included in a block.

2. Can you provide more information on the `trace_address` column and how it relates to the position of the transaction in the chain of all transactions related to the MEV trade? 
- The `trace_address` column contains a trace pattern related to the position of the transaction in the chain of all transactions related to the MEV trade. This can be useful for analyzing the flow of transactions and identifying potential bottlenecks or inefficiencies.

3. Are there any limitations or considerations to keep in mind when using the `debt_purchase_amount` column for analysis? 
- It may be important to consider the specific context and protocol being used when analyzing the `debt_purchase_amount` column, as the amount of purchased debt may vary depending on the protocol and other factors. Additionally, it may be useful to compare this column to other relevant metrics to gain a more complete understanding of the data.