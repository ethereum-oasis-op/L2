# Working Group Standards Glossary of Terms

The goal of this glossary of terms is to provide a repository of definitions of common terms in the layer 2 ecosystem, and that are used in this working groups standards. 


**Account:**

A unit that is minimally comprised of a unique account identifier, a deterministic ordering parameter, also referred to as a nonce, a balance of a Layer 1, Layer 2 or Sidechain unit of exchange, also referred to as a protocol token. Changes to an account are controlled by a unique cryptographic public and private key pair. There are typically additional account elements referring to instructions and data associated to the account that determine account changes. 

**Address Aliasing**

Refers to a method by which an address is associated with another (destination) address.

**Blockchain:**

An open, distributed ledger that can record transactions between two parties efficiently and in a verifiable and permanent way.

**Bridge:**

Provides a connection that allows for the transfer of digital tokens or data between two different Layer 1, Layer 2 or Sidechain systems.

**Developer:**

An individual writing computer code for software applications that operate on a Layer 1, Layer 2 or Sidechain.

**Direct Transaction:**

A transaction where the Transaction Originator is also the Transaction Sender.

**Data Fee:**

A fee to be paid by the Transaction Originator or Transaction Sender sufficient to cover the Layer 1 transaction fees, and any other transaction data fees related to non-Layer 1 data storage, and excluding a Priority Fee and an Execution Fee.

**Execution Fee:**

A fee to be paid by the Transaction Originator or Transaction Sender sufficient to cover the Layer 2 transaction fees excluding a Priority Fee and a Data Fee.

**Externally Owned Account (EOA)**

An Ethereum address that is controlled by a cryptographic private key.

**Fee Price:**

A Layer 2 gas price or a price of a Layer 2 gas equivalent unit of compute and storage consumption.

Note that a gas price or a price of a Layer 2 gas equivalent unit of compute and storage consumption is typically variable and changes with the level of usage of a Layer 2 network. Note, that a gas price is expressed in Giga Wei (GWEI) for EVM-compatible networks, where Wei represents the smallest unit of gas; 1 Wei = 10<sup>-18</sup> Eth in Ethereum's native token.

**Gas:**

Refers to the unit that measures the amount of computational and storage effort required to execute specific operations on an EVM-compatible network.

**Intermediary:**

An entity that is the sender of a transaction for which it is not the Transaction Originator.

**Layer 1:**

A base blockchain network, such as Bitcoin, or Ethereum, and its underlying infrastructure that validates and finalizes transactions without the need of another blockchain network.

**Layer 2:**

A secondary framework or protocol that is built on top of an existing Layer 1 system in such a way that it inherits the security properties of the Layer 1 system while allowing for a higher transaction throughput than the Layer 1 system.

**Layer 2 Operator:**

An entity responsible for the development and/or operation of a Layer 2 network or single Layer 2 network node, except for entities that only provide access to a Layer 2.

**Layer 2 Block:**

A Layer 2 data object stored on a Layer 1 and typically comprised of a set of Layer 2 Transactions or their compressed representations and/or a cryptographic representation of the Layer 2 State after applying the set of Layer 2 Transactions to the Layer 2 state. This Layer 2 data object is also cryptographically linked to the previous Layer 2 Block where the cryptographic link is derived using only the previous Layer 2 Block's data.

**Layer 2 Operating Condition:** 

A combination of the current volume of L2 transactions waiting to be processed on an L2 and all the transactions currently being processed on an L2.

**Layer 3:**

A tertiary framework or protocol that is built on top of an existing Layer 2 system in such a way that it inherits the security properties of the Layer 2 system while allowing for an improvement of a Layer 2 characteristic such as higher transaction throughput than the Layer 2 system or transaction privacy.

**Maximal Extractable Value:**

Refers to the maximum value that can be extracted from block production in excess of the standard block reward and gas fees by including, excluding, and changing the order of transactions in a block.

**Meta Transaction:**

A transaction where the Transaction Sender is not the Transaction Originator, and the transaction fee for the Transaction Originator is different if the same transaction was a direct transaction.

**Priority Fee:**

Paid by the Transaction Originator or Transaction Sender to obtain a desired slot for its transaction in a new block.

Note that the exact position of a transaction in a new block may be determined by factors such as time-stamp, or minimization of Maximal Extractable Value (MEV) of a block in addition to a Priority Fee.

**Sequencer:**

Collects L2 transactions, publishes them in a batch to the Layer 1 on which the Layer 2 operates, and, if required, participates in a consensus algorithm with other sequencers to determine transaction ordering in a Layer 2 block. It may collect transaction fees from the published transactions, pay Layer 2 fees to other Layer 2 protocol participants, or distribute transaction fees to 3rd parties as designated.

**Sidechain:**

A secondary blockchain connected to the main blockchain with a two-way peg and using its own trust assumptions.

**State:**

The set of all accounts on a Layer 2 that are mapped to one another using a cryptographic data structure.

**State Transition:**

An event that deterministically changes one or more accounts in the set of all accounts that comprise the complete state of a Layer 2.

**Transaction:**

A digitally signed message sent from a Layer 2 account that contains instructions and data that result in a Layer 2 state transition. 

**Transaction Fee:**

The fee in a Layer 2 network or protocol token to be paid by a transaction Originator or Transaction Sender comprised of the sum of an Execution Fee, a Data Fee and a Priority Fee.

**Transaction Fee Refund:**

The difference between the Transaction Fee that the Transaction Sender has included in the Transaction when sent to the Layer 2 and the Transaction Fee that has been charged to the Transaction Sender when a Transaction has been finalized on the Layer 2

**Transaction Originator:**

The account that created a transaction for a Layer 1, Layer 2, or Sidechain.

**Transaction Sender:**

The account that sent a transaction to a Layer 1, Layer 2, or Sidechain.

**Two-Way Peg:**

A mechanism by which tokens are transferred between a blockchain and a sidechain and back at a fixed or otherwise deterministic exchange rate.

An interesting forum for ecosystem term discussions and descriptions of topics can be found [here](https://l2beat.com/faq).