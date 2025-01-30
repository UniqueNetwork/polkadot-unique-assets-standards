# Polkadot Unique Assets Standards

## Abstract

This repository describes several standards for the Polkadot ecosystem's Unique Assets, which are NFT-like objects of any nature and purpose.
The standards define a Unique Asset, how it can be identified throughout the ecosystem, how it can be inspected on any chain, and how it can be modified in a standard way.

## Motivation

The Polkadot ecosystem has the crucial advantage of interoperability between its participants in a secure and decentralized manner.
Specialized blockchains (the parachains) participate in the shared Polkadot consensus while maintaining their sovereignty. This way, each parachain isn't restricted to what service it provides and how it should be built, which opens more possibilities for innovation.

This also leads to fragmentation in the implementation of similar ideas. The different implementations have their strengths, and having them is a good thing. But the fragmentation of the API and understanding of similar notions is also causing friction to build the products for the end-users.
This is what happened with the Unique Assets (NFTs, CoreTime regions, and other unique objects like exchange pools) in the ecosystem.

To overcome this, the standards are needed. The interactions between chains are standardized via XCM. It already provides a common language for expressing NFT transfers, and the approved [Fellowship RFC 125 "XCM Asset Metadata"](https://polkadot-fellows.github.io/RFCs/approved/0125-xcm-asset-metadata.html) paves the way for data communication between chains. With these tools, parachains are capable of interacting with each other. Unfortunately, this doesn't cover the client side.

This repository's documents aim to solve the "standards problem" for the client side. It defines what a Unique Asset can be and what generic APIs should be exposed by a compliant parachain.

The standards are designed in such a way as to not impose any artificial limitations on the underlying Unique Asset implementations on a given parachain.

## Unique Asset Definition

A Unique Asset is any unique object existing on-chain. The nature of such an asset should be defined purely by what it can do.

For instance, Unique Assets can be represented by:
- regular NFTs
- NFT collections
- fungible collections
- CoreTime regions
- exchange pools

All the objects above can be uniquely identified and have some data attached. These properties are attributed to all Unique Assets. 

All Unique Assets have a privileged set of operations that can only be done by a special user. This user is considered an asset owner. The owner can be a user account or a chain's system account (like Treasury).

The common properties of Unique Assets form the main parts of the standards, which are mandatory for all compliant parachains.

- The Unique Assets must have a standard identification. See the [Identification Standard](./src/identification.md).
- The Unique Assets' attached data must be inspectable by a client. See the [Inspection Standard](./src/inspection.md).
- The Unique Assets can be modified. The modification operations are subject to authorization and may be rejected by the given chain according to its internal rules. See the [Modification Standard](./src/modification/README.md).
The Modification Standard describes the mandatory operations like changing the asset's owner or data. Also, it esteblishes the way of adding standard extensions that can be optionally supported by parachains. 
