# CallTrace Tree

CallTrace Tree is a tool for understanding the behavior of smart contracts and the flow of execution within Tx. It represents the sequence of function calls and their respective outputs, and helps users better understand the Tx on smart contract level.&#x20;

<figure><img src="../../../.gitbook/assets/image (330).png" alt=""><figcaption><p>CallTrace Tree</p></figcaption></figure>



Under CallTrace Tree, we further divide the Tx into two categories: "Nodes with transfer" and "All Nodes"

For "Nodes with transfer", only actions that involve token transfer will be recorded. As users click through each step, the corresponding token flow chart will show on the right.&#x20;

<figure><img src="../../../.gitbook/assets/node transfer.gif" alt=""><figcaption><p>"Nodes with transfer"</p></figcaption></figure>

"All Nodes" records every step in the Tx. Therefore, the token flow chart can go blank as some steps within the Tx do not involve token transfer.&#x20;

<figure><img src="../../../.gitbook/assets/all nodes.gif" alt=""><figcaption><p>"All Nodes"</p></figcaption></figure>

