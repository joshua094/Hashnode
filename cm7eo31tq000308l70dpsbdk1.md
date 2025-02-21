---
title: "WTF is Pessimistic Proof? 🤔"
seoTitle: "Understanding Pessimistic Proof"
seoDescription: "Pessimistic proofs boost blockchain security by assuming participant malice, ensuring robust solutions for Ethereum's layer-2 networks"
datePublished: Fri Feb 21 2025 11:07:46 GMT+0000 (Coordinated Universal Time)
cuid: cm7eo31tq000308l70dpsbdk1
slug: wtf-is-pessimistic-proof
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1740135877537/3b9b7df3-dd06-46ca-8518-fd982bfa4100.png
tags: web-development, blockchain, web3, polygon

---

# The Evolution of Blockchain and Aggregated Solutions

Since its inception, blockchain technology has evolved in diverse directions, resulting in a fragmented ecosystem. Despite its potential, only 6.8% of the world's population holds cryptocurrencies, highlighting the technology's limited reach. However, Polygon Technology's concept of aggregated blockchains aims to unify this fragmented ecosystem, offering a promising solution to the current challenges.

# Aggregated Blockchains: A Recap

Introduced by Polygon in early 2024 and discussed in our last [article](https://bandojay.hashnode.dev/architecting-scalability-exploring-agglayers-zk-rollup-aggregation), aggregated blockchains serve as a foundational aspect of AggLayer. This technology aims to deliver the best user experience, unified liquidity, scalability, and customisability. Unlike traditional monolithic and modular blockchains, aggregated blockchains strive to offer a holistic solution without compromising key facets.

Polygon’s AggLayer acts as a unified bridge between layer-1 and layer-2 blockchains, addressing the issue of users traversing multiple blockchains for simple transactions. This fragmentation has led to increased security concerns and reduced scalability, ultimately degrading performance capabilities. By leveraging zero-knowledge proofs (ZKPs) or optimistic proofs, aggregated blockchain solutions register transactions on the main blockchain seamlessly.  

# Challenges with Existing Mechanisms

While zero-knowledge proofs and optimistic proofs currently support aggregated blockchain solutions, they present challenges as more blockchains join the unified bridge. Optimistic proofs, for instance, can take up to seven days for a transaction to become fully integrated into a blockchain, hampering the user experience in a large-scale system.

Zero-knowledge proofs, though effective, may face reduced transaction soundness as the unified bridge interacts with networks with diverse consensus mechanisms. Additionally, without sufficient security backups, a malicious actor from one blockchain could jeopardize the entire aggregated network.

# How Pessimistic Proofs Address These Issues

To overcome the limitations of existing mechanisms, Polygon introduced **pessimistic proofs**, a novel approach designed to enhance the security and reliability of aggregated blockchain solutions. Pessimistic proofs assume that all participants in an aggregated solution are malicious, employing a unique approach to enhance network safety. The key principle is that a participant blockchain cannot withdraw more than its deposited amount in the bridge contract.

The creation of pessimistic proofs involves verifying three critical pieces of information:

1\. Updates are executed correctly on the participant blockchain.

2\. The participant network's internal accounting is accurate.

3\. All participant blockchains conduct their accounting activities correctly.

By checking each participant network for trustworthiness, the unified aggregation layer ensures no attempts are made to withdraw extra from the bridge. If a network fails the check, it can only threaten itself, not the bridge or other networks.

Technically, the unified bridge requires three inputs to generate a pessimistic proof:

1\. The participant blockchain’s local exit tree (indicating withdrawals) up to the previous iteration.

2\. The list of new withdrawals to be included in the current update.

3\. The blockchain’s projected new local exit root.

The mechanism calculates the network’s new exit root from the first two inputs and compares it with the third. If they match, a pessimistic proof is generated, guaranteeing the local exit root is updated correctly. Additionally, the mechanism checks the crypto token balances of participant blockchains before proceeding with a new global exit root. If the withdrawal balance exceeds the deposited balance, the update is invalid, and its state cannot be verified on the layer-1 network.

# Conclusion

Pessimistic proofs represent a pioneering approach to enhancing the safety of aggregated blockchain solutions. As more layer-2 networks build on Ethereum, the need for such provenance mechanisms becomes crucial. While Polygon Technology developed this mechanism to support its AggLayer, its revolutionary appeal is set to capture blockchains worldwide. By adopting pessimistic proofs, blockchain projects, especially those building an L2 on Ethereum, can join a global network with robust security. Connect with our experts now to explore the possibilities and implement pessimistic proofs in your L2 solution with Polygon’s solid infrastructure.