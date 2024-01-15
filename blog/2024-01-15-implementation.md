---
slug: implementation
title: Design and Implementation of the xsigners Multisig Project for Substrate Blockchains
authors: [gabo, luca] 
tags: [polkadot, smart contracts, discovery, rust, ink!]
---

# Design and Implementation of the xsigners Multisig Project for Substrate Blockchains

## Introduction

In the development of the [**xSigners**](https://xsigners.io) multisig project, tailored for Substrate blockchains containing contracts pallet, our primary objective was to uphold the principles of decentralization while simultaneously striving to minimize operational costs. This document aims to elucidate the various decisions and trade-offs encountered during the project's lifecycle, particularly focusing on aspects such as user experience, on-chain expenses, and contract storage management.

The xsigners multisig solution was conceptualized to enhance security and collaborative decision-making in the management of digital assets and contract interactions on Substrate-based blockchains. By leveraging the ink! smart contract platform, we were able to create a robust and flexible multisig contract. However, this journey was not without its challenges. We had to carefully balance the inherent limitations of blockchain technology, such as storage costs and computational overhead, against the need for a seamless and user-friendly experience.

