---
slug: implementation
title: Design and Implementation of the **xSigners** Multisig Project for Substrate Blockchains
authors: [gabo, luca] 
tags: [polkadot, smart contracts, discovery, rust, ink!]
---

# Design and Implementation of the **xSigners** Multisig Project for Substrate Blockchains

## Introduction

In the development of the [****xSigners****](https://**xSigners**.io) multisig project, tailored for Substrate blockchains containing contracts pallet, our primary objective was to uphold the principles of decentralization while simultaneously striving to minimize operational costs. This document aims to elucidate the various decisions and trade-offs encountered during the project's lifecycle, particularly focusing on aspects such as user experience, on-chain expenses, and contract storage management.

The **xSigners** multisig solution was conceptualized to enhance security and collaborative decision-making in the management of digital assets and contract interactions on Substrate-based blockchains. By leveraging the ink! smart contract platform, we were able to create a robust and flexible multisig contract. However, this journey was not without its challenges. We had to carefully balance the inherent limitations of blockchain technology, such as storage costs and computational overhead, against the need for a seamless and user-friendly experience.

## Integration of Subsquid in the ****xSigners**** Multisig Project

In addressing the challenges of user experience and on-chain data management in the **xSigners** multisig project, we turned to Subsquid, an innovative indexing and storage engine for blockchain data. Subsquid's integration plays a crucial role in streamlining the flow of information within our application. By harnessing its ability to aggregate and archive on-chain data, we have significantly enhanced the way users interact with our multisig solution. This integration allows for a more consolidated and efficient presentation of data, crucial for decision-making in a multisig environment.

One of the key benefits brought by Subsquid is its GraphQL API, which facilitates easy and flexible queries. This feature enables the application to efficiently extract and present vital information such as events, balances, and other contract-related metadata. The result is a substantial reduction in the user experience (UX) friction that was previously a challenge. Users are no longer burdened with the manual task of sharing individual contract addresses and details. Instead, the Subsquid processor efficiently collates this information and provides it through a unified gateway, simplifying user interactions with the multisig contract. 

## Understanding Subsquid: An Overview

Subsquid serves as a powerful indexing and storage engine for blockchain data, a critical component in modern blockchain applications. Its primary function is to efficiently process, aggregate, and archive data from blockchain networks. This capability is essential for applications that require quick and easy access to a big array of on-chain information. Subsquid achieves this through its advanced data processing capabilities, which transform raw blockchain data into a more accessible and usable format.

The core advantage of using Subsquid in blockchain projects, such as the **xSigners** multisig, lies in its ability to provide a more streamlined and user-friendly data interaction experience. With its GraphQL API, Subsquid allows for sophisticated and customizable data queries. This means that applications can offer their users a more intuitive and responsive interface, with the ability to access a wide range of data points without the complexities and limitations of direct on-chain data retrieval. This approach not only enhances the user experience but also contributes to the overall efficiency and effectiveness of the application.

Building upon the integration of Subsquid in the **xSigners** multisig project, a significant advantage emerges in the form of accessing historical data. With Subsquid's indexing capabilities, users can effortlessly view older transactions without the need to delve into dated blockchain snapshots. This feature is particularly beneficial in a multisig context, where tracking the history of transactions and contract interactions is crucial for transparency and auditability. By providing a streamlined method to access this historical data, Subsquid enhances the user experience, making it simpler and more efficient to review past activities and decisions made within the multisig contract.

Despite the convenience and efficiency offered by Subsquid, it is crucial to emphasize that decentralized data integrity remains at the forefront of our priorities. The core functionality of the underlying contract palette and its state transitions continue to operate in a backendless, decentralized paradigm. This means that while Subsquid acts as an efficient access layer, providing a user-friendly interface for data retrieval and interaction, it does not have the capability to alter any on-chain settlements. The immutable nature of blockchain ensures that all contract interactions and settlements remain tamper-proof and transparent, upholding the trust and security inherent in decentralized systems.

## All core logic on-chain

The architectural decision to keep all core logic on-chain in the **xSigners** multisig project opens up a realm of possibilities for community engagement and innovation. By maintaining the contract logic on the blockchain, we ensure that the system is not only transparent and secure but also accessible for external developers. This approach allows anyone in the community to create their own frontends or interfaces to interact with the contracts. Such openness fosters a collaborative ecosystem where developers can contribute to the project's growth, experiment with new user interfaces, or even build specialized tools tailored to specific needs, all while interacting with the same underlying, reliable smart contract logic.

This design choice has already borne fruit in several instances. For example, we have seen developers create customized dashboard interfaces that cater to specific user groups, such as enterprise clients requiring more detailed reporting features. Another notable development is the creation of mobile applications that provide on-the-go access to multisig functionalities, making it more convenient for users to manage their contracts from anywhere. These examples underscore the versatility and adaptability of the **xSigners** multisig project, demonstrating how keeping the logic on-chain can spur innovation and enhance user experience through community-driven development.

## Facing some event handling issues

Before delving into the proposed enhancements for the next version of the **xSigners** multisig project, it is important to address a key challenge encountered in the current implementation: the ambiguity of certain emitted events from the blockchain. While blockchain events are crucial for tracking and responding to contract interactions, they sometimes lack the clarity and specificity needed for effective application logic. This issue is particularly evident in the context of our project's reliance on Openbrush, a library for developing ink! smart contracts. Notably, Openbrush does not emit events, as highlighted in their documentation Openbrush Contracts. This limitation necessitates additional post-processing of on-chain data to accurately interpret and utilize these events within our application.

To address this, the next version of the **xSigners** multisig project will incorporate a more robust mechanism for post-processing blockchain events. This enhancement aims to extract clearer and more actionable insights from on-chain activities, ensuring that the application can respond accurately and efficiently to contract states and changes. By refining our approach to handling and interpreting blockchain events, we can overcome the limitations posed by the current ambiguity and lack of event emissions in some contract interactions. This improvement is not only crucial for maintaining the integrity and functionality of the multisig system but also sets the stage for the more advanced backend integration features proposed in the following notes.

## Notes for Next Version: Backend Integration for Signature Management

- **Backend-Driven Signature Collection**: Implement a backend system that allows users to send their signatures to a centralized service. This approach would streamline the process of gathering signatures for multisig transactions, especially in scenarios where multiple confirmations are required.

- **Threshold-Based Transaction Execution**: The backend would monitor the number of affirmative signatures collected. Once the predefined threshold is reached, indicating sufficient consensus among the parties involved, the backend would then automatically prepare for the next step of executing the transaction.

- **Bulk Transaction Posting**: Instead of posting each signature to the blockchain individually, the backend could aggregate all the required signatures and post them in bulk. This would result in a single transaction being sent to the blockchain, representing the collective approval of the multisig participants.

- **Cost and Efficiency Optimization**: By consolidating multiple signatures into a single transaction, this method would significantly reduce the number of transactions required on the blockchain. This not only optimizes the cost associated with transaction fees but also enhances the efficiency of the process.

- **Security Considerations**: While this approach adds convenience, it's crucial to assess and implement robust security measures within the backend to safeguard the signature collection and transaction execution process.

- **User Experience Improvement**: This backend integration aims to simplify the user experience, making the process of multisig approvals more seamless and less time-consuming for the users.


## Conclusion

In conclusion, the journey of developing the **xSigners** multisig project for Substrate blockchains has been both challenging and enlightening. We navigated through the complexities of maintaining decentralization, optimizing costs, and enhancing user experience, all while adhering to the stringent requirements of newest technology. The integration of Subsquid addressed significant challenges related to data accessibility and user interface, demonstrating the power of combining on-chain logic with off-chain data processing. Furthermore, our commitment to keeping all core logic on-chain has opened avenues for community-driven innovation, allowing others to build diverse and customized frontends.

As we look towards the future, the proposed enhancements in signature management and event processing signify our ongoing commitment to evolving and improving the **xSigners** multisig project. By considering the integration of a backend system for more efficient signature collection and transaction execution, along with refining our approach to blockchain event interpretation, we aim to further streamline the multisig process. These advancements will not only enhance the user experience but also maintain the integrity and security that are paramount in blockchain applications.

The **xSigners** multisig project stands as a testament to the potential of collaborative development in the blockchain space. It showcases how innovative solutions can emerge from the challenges of working within a decentralized framework, and how these solutions can lead to more efficient, user-friendly, and secure blockchain applications. As we continue to develop and refine our MVP, we remain dedicated to pushing the boundaries of what is possible in the realm of blockchain technology, always with an eye towards the needs and experiences of our users. Our journey thus far has been a blend of technical innovation and practical problem-solving, and we are excited about the future possibilities this project holds. The lessons learned and the successes achieved serve as a foundation for not only our team but also for the broader blockchain community, inspiring further exploration and development in this dynamic field.

 By continuously adapting and improving, we aim to contribute to a more secure, efficient, and user-centric blockchain ecosystem. We look forward to the continued support and collaboration from the community as we embark on the next phase of this exciting journey.