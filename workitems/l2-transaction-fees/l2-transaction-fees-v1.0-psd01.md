
![EEA Logo](../l2-transaction-fees/images/eea-symbol.png)
-------

# Layer 2 Transaction Fee Specification Version 1.0
###### L2TFSPEC

## Project Specification Draft

<!-- URI list start (commented out except during publication by OASIS TC Admin)

#### This stage:
https://docs.oasis-open.org/baseline/baseline-core/v1.0/psd01/baseline-core-v1.0-psd01.md (Authoritative) \
https://docs.oasis-open.org/baseline/baseline-core/v1.0/psd01/baseline-core-v1.0-psd01.html \
https://docs.oasis-open.org/baseline/baseline-core/v1.0/psd01/baseline-core-v1.0-psd01.pdf

#### Previous stage:
N/A

#### Latest stage:
https://docs.oasis-open.org/baseline/baseline-core/v1.0/baseline-core-v1.0.md (Authoritative) \
https://docs.oasis-open.org/baseline/baseline-core/v1.0/baseline-core-v1.0.html \
https://docs.oasis-open.org/baseline/baseline-core/v1.0/baseline-core-v1.0.pdf

URI list end (commented out except during publication by OASIS TC Admin) -->

#### Open Project:
[Layer 2 Working Group](https://github.com/eea-oasis/L2), an initiative of [EEA Community Projects](https://entethalliance.org/eeacommunityprojects/)

#### Project Chair:
Dan Shaw (daniel.shaw@ethereum.org), [Ethereum Foundation](https://ethereum.org), Andreas Freund (a.freundhaskel@gmail.com), [Ethereum Foundation](https://ethereum.org)  

#### Editors:
Kelvin Fichter (kelvin@optimism.io)\
Andreas Freund (a.freundhaskel@gmail.com)\
Daniel Goldman (dgoldman@offchainlabs.com)\

<!--
#### Additional artifacts:
This prose specification is one component of a Work Product that also includes:
* XML schemas: (list file names or directory name)
* Other parts (list titles and/or file names)
* `(Note: Any normative computer language definitions that are part of the Work Product, such as XML instances, schemas and Java(TM) code, including fragments of such, must be (a) well formed and valid, (b) provided in separate plain text files, (c) referenced from the Work Product; and (d) where any definition in these separate files disagrees with the definition found in the specification, the definition in the separate file prevails. Remove this note before submitting for publication.)`
 -->

#### Related work:

<!--
This specification replaces or supersedes:
* _Baseline Protocol Version 1.0_ - 
* Specifications replaced by this specification (include hyperlink, preferably to HTML format)
 -->

NA


#### Abstract:
The document describes the minimal set of business and technical prerequisites, functional and non-functional requirements for Layer 2 Transaction Fees that when implemented ensures that Layer 2 solutions are transparently and consistently calculating and displaying transaction fees.

#### Status:
This document is under active development and implementers are advised against implementing the specification unless they are directly involved with L2 WG.

<!--
was last revised or approved by Baseline, part of the Ethereum OASIS Open Project, on the above date. The level of approval is also listed above. Check the "Latest stage" location noted above for possible later revisions of this document. Any other numbered Versions and other technical work produced by the Open Project (OP) are listed at [TBD].
-->

Comments on this work can be provided by opening issues in the project repository.

#### Keywords:
The keywords "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [[RFC2119](#rfc2119)] when, and only when, they appear in all capitals, as shown here.

#### Citation format:
When referencing this specification the following citation format should be used:

**[l2-transaction-fees-v1.0]** _Layer 2 Transaction Fees Version 1.0_. Edited by Kelvin Fichter, Andreas Freund, Daniel Goldman. 22 February 2023. OASIS Standard. https://github.com/eea-oasis/L2/tree/main/workitems/l2-transaction-fees/l2-transaction-fees-v1.0-psd01.md. Latest stage: https://github.com/eea-oasis/L2/tree/main/workitems/l2-transaction-fees/l2-transaction-fees-v1.0-psd01.md.

-------

## Notices
Copyright © OASIS Open 2023. All Rights Reserved.

Distributed under the terms of the OASIS [IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr).

For complete copyright information please see the Notices section in the Appendix.

-------

# Table of Contents
[1 Introduction](#1-introduction) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.1 Overview](#11-overview) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.2 Glossary](#12-glossary) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.3 Typographical Conventions](#13-typographical-conventions) \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.3.1	Requirement Ids](#131-requirement-ids) \
[2 Concepts and Design](#2-concepts-and-design) \
[3 Layer 2 Transaction Fees Specification](#3-layer-2-transaction-fees-specification) \
[4 Conformance](#4-conformance) \
&nbsp;&nbsp;&nbsp;&nbsp;[4.1 Conformance Targets](#41-conformance-targets) \
&nbsp;&nbsp;&nbsp;&nbsp;[4.2 Conformance Levels](#42-conformance-levels)\
[Appendix A - References](#appendix-a---references)\
&nbsp;&nbsp;&nbsp;&nbsp;[A.1 Normative References](#a1-normative-references) \
&nbsp;&nbsp;&nbsp;&nbsp;[A.2 Non-Normative References](#a2-non-normative-references) \
[Appendix B - Security Considerations](#appendix-b---security-considerations) \
&nbsp;&nbsp;&nbsp;&nbsp;[B.1 Data Privacy](#b1-data-privacy) \
&nbsp;&nbsp;&nbsp;&nbsp;[B.2 Production Readiness](#b2-production-readiness) \
[Appendix C - Acknowledgments](#appendix-c---acknowledgments)\
[Appendix D - Revision History](#appendix-d---revision-history)\
[Appendix E - Notices](#appendix-e---notices)

 

-------
# 1 Introduction
###### L2TFSPECINTRO

The L2 WG is an open-source initiative with a scope to
- Identify and document the most relevant use cases and business requirements for Layer 2 and other Blockchain Scalability solutions for EVM compatible public blockchains
- Define a technical standard with identification and differentiation of classes of scalability solutions as required that meet both ecosystem and enterprise requirements, with a particular focus on interoperability between Layer 2 solutions for EVM compatible public blockchains
- For EVM compatible public blockchains, identify, document, and devise solution approaches for Layer 2 Blockchain scalability solution specific challenges such as MEV, block (gas) limits, TVL concentration, etc.
- Identify and document characteristics of Layer 2 Blockchain environments for EVM compatible public blockchains that will be key in addressing mainstream and enterprise adoption.

The work is an [EEA Community Project](https://entethalliance.org/eeacommunityprojects/), which is managed by [OASIS](https://oasis-open-projects.org/).

## 1.1 Overview
###### L2TFSPECOVERV

Layer 2 (L2) Transaction Fees are a crucial element of financing the operations of L2 platforms apart from rewards given to participants for providing economic security guarantees such as validators in consensus protocols. Yet how these transaction fees are derived, to whom they are paid, how and where they are displayed to any of the participants in L2 platforms varies greatly between L2 platforms. 

Given the above, the need for transparency in a open ecosystem to build trust, and the evolving legal and regulatory landscape around fee transparency and what type of fees can be charged, this document sets out to define the different types of L2 transaction fees and then define requirements around transaction fee transparency for L2 platforms.

Note, that fees associated with asset and data bridges between L2 platforms as well as between L2 platforms and centralized exchanges are beyond the scope of this document.


## 1.2 Glossary
###### L2TFSPECGLOS

**Account:**

A unit that is minimally comprised of a unique account identifier, a deterministic ordering parameter, also referred to as a nonce, a balance of a Layer 1, Layer 2 or Sidechain unit of exchange, also referred to as a protocol token. Changes to an account are controlled by a unique cryptographic public and private key pair. There are typically additional account elements referring to instructions and data associated to the account that determine account changes. 

**Base Fee:**

The minimum amount of gas or a Layer 2 gas equivalent unit of compute and storage consumption required to include a transaction on a Layer 2.  

**Blockchain:**

An open, distributed ledger that can record transactions between two parties efficiently and in a verifiable and permanent way.

**Bridge:** 

The means for the transfer of information and digital assets between Layer 2s, Layer 1s, and Sidechains.

**Developer:**

An individual writing computer code for software applications that operate on a Layer 1, Layer 2 or Sidechain.

**Direct Transaction:**

A transaction where the Transaction Originator is also the Transaction Sender.

**Execution Fee:**

A fee to be paid by the Transaction Originator or Transaction Sender sufficient to cover both the Layer 2 and Layer 1 transaction fees excluding a Base Fee, or a Priority Fee.

An example calculation of such an Execution Fee is:
$$L2\space Gas\space Limit + {L1\space Transaction\space Fee \over L2\space Gas\space Price}$$

**Fee Price:**

A Layer 2 gas price or a price of a Layer 2 gas equivalent unit of compute and storage consumption.

Note that a gas price or a price of a Layer 2 gas equivalent unit of compute and storage consumption is typically variable and changes with the level of usage of a Layer 2 network. Note, that a gas price is expressed in Giga Wei (GWEI) for EVM-compatible networks, where Wei represents the smallest unit of gas; 1 Wei = 10<sup>-18</sup> Eth in Ethereum's native token.

**Gas:**

Refers to the unit that measures the amount of computational and storage effort required to execute specific operations on an EVM-compatible network.

**Intermediary:**

An entity that is the sender of a transaction for which it is not the Transaction Originator.

**Layer 1:**

A base network, such as Bitcoin, or Ethereum, and its underlying infrastructure that validates and finalizes transactions without the need of another network.

**Layer 2:**

A secondary framework or protocol that is built on top of an existing Layer 1 system in such a way that it inherits the security properties of the Layer 1 system while allowing for a higher transaction throughput than the Layer 1 system.

**Layer 2 Operator:**

An entity responsible for the development and/or operation of a Layer 2 network or single Layer 2 network node, except for entities that only provide access to a Layer 2.

**Layer 2 Block:**

A Layer 2 data object stored on a Layer 1 and typically comprised of a set of Layer 2 Transactions or their compressed representations and/or a cryptographic representation of the Layer 2 State after applying the set of Layer 2 Transactions to the Layer 2 state. This Layer 2 data object is also cryptographically linked to the previous Layer 2 Block where the cryptographic link is derived using only the previous Layer 2 Block's data.

**Layer 2 Operating Condition:** 

A combination of the current volume of L2 transactions waiting to be processed on an L2 and all the transactions currently being processed on an L2.

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

The fee in a Layer 2 network or protocol token to be paid by a transaction Originator or Transaction Sender comprised of the sum of a Base Fee, an Execution Fee and a Priority Fee.

**Transaction Fee Refund:**

The difference between the Transaction Fee that the Transaction Sender has included in the Transaction when sent to the Layer 2 and the Transaction Fee that has been charged to the Transaction Sender when a Transaction has been finalized on the Layer 2

**Transaction Originator:**

The account that created a transaction for a Layer 1, Layer 2, or Sidechain.

**Transaction Sender:**

The account that sent a transaction to a Layer 1, Layer 2, or Sidechain.


## 1.3 Typographical Conventions
###### L2TFSPECTYPO

### 1.3.1 Requirement Ids
###### L2TFSPECREQIDS

A requirement is uniquely identified by a unique ID composed of its requirement level followed by a requirement number, as per convention **[RequirementLevelRequirementNumber]**. 
There are four requirement levels that are coded in requirement ids as per below convention: 

**[R]** - The requirement level for requirements which IDs start with the letter _R_ is to be interpreted as **MUST** as described in [RFC2119](#rfc2119). \
**[D]** - The requirement level for requirements which IDs start with the letter _D_ is to be interpreted as **SHOULD** as described in [RFC2119](#rfc2119). \
**[O]** - The requirement level for requirements which IDs start with the letter _O_ is to be interpreted as **MAY** as described in [RFC2119](#rfc2119). 

Note that requirements are uniquely numbered in ascending order within each requirement level.

Example : It should be read that [R1] is an absolute requirement of the specification whereas [D1] is a recommendation and [O1] is truly optional.

-------

# 2 Concepts and Design
###### L2TFSPECCONCEPT

To specify requirements about L2 transaction fees, this document will first:

* Define the meaning of a transaction fee and its components
* Define the roles relevant to transaction fees
* Define transaction types and their relationship to transaction fees

Note, that all definitions can be found in the [Glossary](#12-glossary)

Subsequently, the specification section will define requirements around fee transparency, fee estimation, final fees, and how, when and where fees are communicated to the different roles. The specification will also discuss requirements around responsibilities and accountability of roles towards one another.

## 2.1 Definition of Transaction Fee and its Components
###### L2TFSPECDEF

This document defines Transaction Fee as the fee in a Layer 2 (L2) network or protocol token to be paid by a Transaction Originator or Transaction Sender comprised of the sum of a Base Fee, an Execution Fee and a Priority Fee.

Note that this document defines as Transaction as a digitally signed message sent from an L2 account that contains instructions and data that result in an L2 state transition. Also note that this document defines State and State Transition as follows:

* State: The set of all accounts on an L2 that are mapped to one another using a cryptographic data structure.
* State Transition: An event that deterministically changes one or more accounts in the set of all accounts that comprise the complete state of an L2.

Further note that this document defines Account as a unit that is minimally comprised of a unique account identifier, a deterministic ordering parameter, also referred to as a nonce, a balance of a Layer 1, Layer 2 or Sidechain unit of exchange, also referred to as a protocol token. Changes to an account are controlled by a unique cryptographic public and private key pair. There are typically additional account elements referring to instructions and data associated to the account that determine account changes.

In formula form the Transaction Fee is given as:

**Transaction Fee = Base Fee + Execution Fee + Priority Fee**

The different components are defined as follows:

* **Base Fee:** The minimum amount of Gas or an L2 gas equivalent unit of compute and storage consumption required to include a transaction on an L2.
* **Execution Fee:** A fee to be paid by the Transaction Originator or Transaction Sender sufficient to cover both the Layer 2 and Layer 1 transaction fees excluding a Base Fee, or a Priority Fee.
* **Priority Fee:** Paid by the Transaction Originator or Transaction Sender to obtain a desired slot for its transaction in a new block. Note that the exact position of a transaction, a slot, in a new block may be determined by factors such as time-stamp, or minimization of Maximal Extractable Value (MEV) of a block in addition to a Priority Fee. And that MEV is defined as the maximum value that can be extracted from block production in excess of the standard block reward and gas fees by including, excluding, and changing the order of transactions in a block.

Note that a Transaction Fee has a Transaction Fee Price which is defined in the context of this document as an L2 Gas price or a price of an L2 gas equivalent unit of compute and storage consumption.

Note that a Gas price or a price of an L2 gas equivalent unit of compute and storage consumption is typically variable and changes with the level of usage of an L2 network. Note that a gas price is expressed in Giga Wei (GWEI) for EVM-compatible networks, where Wei represents the smallest unit of gas; 1 Wei = 10<sup>-18</sup> Eth in Ethereum's native token.

Furthermore, note that Gas in this document refers to the unit that measures the amount of computational and storage effort required to execute specific operations on an EVM-compatible network. 

## 2.2 Definition of L2 Roles relevant to Transaction Fees
###### L2TFSPECDEFROLES

The following roles are relevant to transaction fees, their calculation and how, when and where they are presented:

* **Transaction Originator:** The account that created a transaction for a Layer 1, L2, or Sidechain.
* **Transaction Sender:** The account that sent a transaction to a Layer 1, L2, or Sidechain.
* **Intermediary:** An entity that is the sender of a transaction for which it is not the Transaction Originator.
* **Sequencer:** Collects transactions, publishes them in a batch to the Layer 1 on which the L2 operates, receives transaction fees from the published transactions, pays L2 fees to other L2 protocol participants, and, if required, participates in a consensus algorithm with other sequencers to determine transaction  ordering in a block.
* **L2 Operator:** An entity responsible for the operation of an L2.
* **Developer:** An individual writing computer code for software applications that operate on a Layer 1, L2 or Sidechain.

## 2.3 Definition of Transaction Types
###### L2TFSPECDEFTTYPES

There are different types of transactions, and depending on the context transaction fees are paid for differently and by different roles.

There are two types of transactions in the context of this document:

* **Direct Transaction:** A transaction where the Transaction Originator is also the Transaction Sender.
* **Meta Transaction:** A transaction where the Transaction Sender is not the Transaction Originator, and the transaction fee for the Transaction Originator is different if the same transaction was a direct transaction.

In the case of a Direct Transaction the Transaction Originator pays for the Transaction Fee based on the Transaction Fee Price the Transaction Originator is maximally willing to pay.

In the case of a Meta Transaction, the Transaction Originator may pay only a portion or no transaction fees at all. Instead, an Intermediary pays all or part of the Transaction Fee. Note that the Intermediary may be the Transaction Sender, or pay the Transaction Sender for the Transaction Fees incurred. Also note that the Transaction Originator may pre-pay Transaction Fees to the Intermediary or the Transaction Sender or both, or submit payment together with the Transaction sent to the Intermediary.

Therefore, the communication of a Transaction Fee and its components is different for different business scenarios. This document will not break down requirements by business scenario but rather by role and if that role is responsible to pay part or all of a Transaction Fee. 

-------

# 3 Layer 2 Transaction Fee Specification
###### L2TFSPECSEC

In this section we will formulate requirements in the following areas:

* Transparency
* Visibility and Roles
* Transactions

## 3.1 Layer 2 Transaction Fee Transparency Requirements
###### L2TFSPECTFREQS

#### **[R1]**

An L2 Transaction Fee MUST be comprised as the sum of a Base Fee, an Execution Fee, and a Priority Fee.

[[R1]](#r1) Testability: Mathematical equality equations can be tested as the sum of the equations elements equaling a desired output. The test is passed if the sum of the elements as inputs is equal to the desired output. If the sum of the equations element do not equal the  desired output the test fails.

#### **[R2]**

All components of an L2 Transaction Fee MUST NOT be less than zero.

[[R2]](#r2) Testability: Mathematical equality or inequality equations can be expressed as testable conditions. A passing test condition is that each individual element of a transaction fee is equal to or larger than zero. A failing test condition is that one or more transaction fee elements is less than zero.

#### **[O1]**

An L2 Transaction Fee or any of its components MAY BE zero.

[[O1]](#o1) Testability: Mathematical equality equations can be expressed as testable conditions. A test for [[R2]](#r2) also tests this optional requirement since zero values are allowed in tests for [[R2]](#r2).

#### **[R3]**

The setting and/or calculation of a Base Fee MUST be well documented and verifiable.

[[R3]](#r3) Testability: 

Preconditions:

* The L2 must have a defined Base Fee.
* There must be documentation available for the current Base Fee.
* An L2 instance is up and running.

Test Steps:

1. Verify that there is a documented process for setting and/or calculating the Base Fee.
2. Verify that the documentation includes the value, specific formula or calculation used to determine the Base Fee.
3. Verify that the documentation includes any relevant assumptions or dependencies that are used in the calculation.
4. Verify that the documentation is up-to-date and accurate, and that it matches the current Base Fee being charged.
5. Attempt to independently calculate the Base Fee using the information provided in the documentation.
6. Verify that the calculated Base Fee matches the currently charged Base Fee.

Test Passing Criteria:

* The documented process for setting and/or calculating the Base Fee must be clear and unambiguous.
* The documentation must include the specific value, formula or calculation used to determine the Base Fee, as well as any relevant assumptions or dependencies.
* The documentation must be up-to-date and accurate.
* The calculated Base Fee must match the currently charged Base Fee.

#### **[R4]**

The setting and/or calculation of an Execution Fee MUST be well documented and verifiable.

[[R4]](#r4) Testability: 

Preconditions:

* The L2 must have a defined Execution Fee.
* There must be documentation available for the current Execution Fee.
* An L2 instance is up and running.

Test Steps:

1. Verify that there is a documented process for setting and/or calculating the Execution Fee.
2. Verify that the documentation includes the value, specific formula or calculation used to determine the Execution Fee.
3. Verify that the documentation includes any relevant assumptions or dependencies that are used in the calculation.
4. Verify that the documentation is up-to-date and accurate, and that it matches the current Execution Fee being charged.
5. Attempt to independently calculate the Execution Fee using the information provided in the documentation.
6. Verify that the calculated Execution Fee matches the currently charged Execution Fee.

Test Passing Criteria:

* The documented process for setting and/or calculating the Execution Fee must be clear and unambiguous.
* The documentation must include the specific value, formula or calculation used to determine the Execution Fee, as well as any relevant assumptions or dependencies.
* The documentation must be up-to-date and accurate.
* The calculated Execution Fee must match the currently charged Execution Fee.

#### **[R5]**

The setting of a Priority Fee MUST be well documented and verifiable.

[[R5]](#r5) Testability: 

Preconditions:

* The L2 must have a defined Base Fee and Execution Fee.
* There must be documentation available for the current Priority Fee.
* An L2 system must be up and running.
* An L2 user is configured.

Test Steps:

1. Verify that there is a documented process for setting the Priority Fee by the L2 user.
2. Verify that the documentation includes the specific factors or criteria used to determine and set the Priority Fee.
3. Verify that the documentation includes any relevant assumptions or dependencies that are used in the determination and setting of the Priority Fee.
4. Verify that the documentation is up-to-date and accurate.
5. An L2 user sets a priority fee for a transaction.
6. Verify that the set Priority Fee is correctly added to the Base Fee and Execution Fee to calculate the Transaction Fee.
7. Verify that the calculated Transaction Fee matches the currently charged Transaction Fee for the set Priority Fee.

Test Passing Criteria:

* The documented process for setting the Priority Fee by the L2 user must be clear and unambiguous.
* The documentation must include the specific factors or criteria used to determine the Priority Fee, as well as any relevant assumptions or dependencies.
* The documentation must be up-to-date and accurate.
* The set Priority Fee must be correctly added to the Base Fee and Execution Fee to calculate the Transaction Fee.
* The calculated Transaction Fee must match the currently charged Transaction Fee for the set Priority Fee.

#### **[R6]**

An L2 MUST provide a capability to estimate a Transaction Fee based on a given Transaction and the current Operating Conditions of the L2.

Note that L2 Operating Conditions refer to a combination of the current volume of L2 transactions waiting to be processed on an L2 and all the transactions currently being processed on an L2.

[[R6]](#r6) Testability: 

Preconditions:

* An L2 system is up and running.
* The L2 must have a defined process for estimating a Transaction Fee based on varying Operating Conditions.
* Operating Conditions must be measurable for the L2, including:
    * The current number of transactions waiting to be processed on the L2.
    * The current number of transactions currently being processed on the L2.
    * The current available L2 resources (e.g. CPU, memory, network bandwidth).
* The L2 must be configured to adjust the Transaction Fee estimation based on varying Operating Conditions.
* Different sets of test Transactions with varying levels of complexity and number of transactions must be available.

Test Steps:

1. Verify that the L2 can provide a Transaction Fee estimate.
2. Submit a simple test Transaction to the L2 after the first set of test transactions has been submitted to the L2.
3. Record the estimated Transaction Fee provided by the L2.
4. Verify that the estimated Transaction Fee is within an acceptable range of the actual Transaction Fee charged after the L2 transaction has been finalized on the L1.
5. Increase the number of transactions waiting to be processed on the L2 by submitting another test data set with more transactions and submit a complex test Transaction.
6. Record the estimated Transaction Fee provided by the L2.
7. Verify that the estimated Transaction Fee has increased in response to the increase in the number of transactions waiting to be processed and currently being processed.
8. Verify that the estimated Transaction Fee has increased in response to the increase in the number of transactions currently being processed and waiting to be processed.
9. Repeat the test with different test Transactions of varying complexity to ensure that the Transaction Fee estimation process is accurately responsive to changes in Operating Conditions and transaction complexity.

Test Passing Criteria:

* The L2 must provide a Transaction Fee estimate in response to a test transaction.
* The estimation process must take into account the current Operating Conditions of the L2.
* The estimated Transaction Fee must be within an acceptable range of the actual Transaction Fee charged.
* The Transaction Fee estimation process must be accurately responsive to changes in Operating Conditions, with higher Operating Conditions leading to higher estimated Transaction Fees.

#### **[R7]**

An L2 MUST record and provide access to the Transaction Fee that the Transaction Sender has included in the Transaction when a Transaction has been sent to the L2.

[[R7]](#r7) Testability:

Preconditions:

* An L2 system is up and running.
* The L2 must have a defined process for recording and storing the Transaction Fee included by the Transaction Sender.
* A test Transaction must be available with a known Transaction Fee included by the Transaction Sender.

Test Steps:

1. Submit the test Transaction to the L2.
2. Verify that the L2 has recorded the Transaction Fee included by the Transaction Sender.
3. Retrieve the recorded Transaction Fee from the L2.
4. Compare the retrieved Transaction Fee with the known Transaction Fee included by the Transaction Sender.
5. Verify that the recorded Transaction Fee matches the known Transaction Fee included by the Transaction Sender.

Test Passing Criteria:

* The L2 must have recorded the Transaction Fee included by the Transaction Sender.
* The recorded Transaction Fee must be accessible by the user.
* The recorded Transaction Fee must match the known Transaction Fee included by the Transaction Sender.

#### **[R8]**

An L2 MUST record and provide access to the Transaction Fee that has been charged to the Transaction Sender when a Transaction has been processed by the L2.

[[R8]](#r8) Testability: 

Preconditions:

* An L2 system is up and running.
* The L2 must have a defined process for calculating and recording the Transaction Fee charged to the Transaction Sender.
* A test Transaction must be available with a known Transaction Fee charged to the Transaction Sender.

Test Steps:

1. Submit the test Transaction to the L2.
2. Wait for the Transaction to be processed by the L2, and the L2 return a message to the Transaction Sender with the processing result of the test transaction including the transaction fee.
3. Retrieve the Transaction Fee charged to the Transaction Sender from the L2 message.
4. Compare the retrieved Transaction Fee with the known Transaction Fee submitted by the Transaction Sender.
5. Verify that the recorded Transaction Fee matches or is less than the known Transaction Fee submitted by the Transaction Sender.

Test Passing Criteria:

* The L2 must have calculated and recorded the Transaction Fee charged to the Transaction Sender.
* The recorded Transaction Fee must be accessible by the Transaction Sender.
* The recorded Transaction Fee must match or is less than the Transaction Fee submitted by the Transaction Sender.

#### **[R9]**

An L2 MUST record and provide access to the Transaction Fee that has been charged to the Transaction Sender when a Transaction has been finalized on theL2.

Transaction finality in the context of this document is defined as the condition when a transaction can no longer be reverted on an L2. Note that the finality condition will vary by L2, and that L2 finality requirements are outside of the scope of this document.

[[R9]](#r9) Testability: 

Preconditions:

* The L2 must have a defined process for calculating and recording the Transaction Fee charged to the Transaction Sender.
* An L2 system is up and running.
* A test Transaction must be available with a known, estimated Transaction Fee to be charged to the Transaction Sender.
* The test environment must have finalized the test Transaction on the L2 according to the L2 finality conditions.

Test Steps:

1. Retrieve the Transaction ID for the test Transaction.
2. Retrieve the Transaction Fee charged to the Transaction Sender from the L2.
3. Compare the retrieved Transaction Fee with the known, estimated Transaction Fee to be charged to the Transaction Sender.
4. Verify that the recorded Transaction Fee matches or is less than the known Transaction Fee to be charged to the Transaction Sender.

Test Passing Criteria:

* The L2 must have calculated and recorded the Transaction Fee charged to the Transaction Sender.
* The recorded and finalized Transaction Fee must be accessible by the user.
* The recorded Transaction Fee must match or be less than the known, estimated Transaction Fee to be charged to the Transaction Sender.


#### **[R10]**

If there is a Transaction Fee Refund, an L2 implementation MUST record and provide access to the Transaction Fee Refund when a Transaction has been finalized on the L2.

A Transaction Fee Refund in the context of this document is defined as the difference between the Transaction Fee that the Transaction Sender has included in the Transaction sent to the L2 and the Transaction Fee that has been charged to the Transaction Sender when a Transaction has been finalized on the L2.

[[R10]](#r10) Testability: 

Preconditions:

* The L2 must have a defined process for calculating and recording the Transaction Fee charged to the Transaction Sender and the Transaction Fee Refund.
* An L2 system is up and running.
* A test Transaction must be available with a known Transaction Fee estimate to be charged to the Transaction Sender.
* The test environment must have finalized the test Transaction on the L2 based on its finality conditions.

Test Steps:

1. Retrieve the Transaction ID for the finalized test Transaction.
2. Retrieve the Transaction Fee charged to the Transaction Sender from the L2.
3. Calculate the Transaction Fee Refund as the difference between the Transaction Fee that the Transaction Sender included in the Transaction and the Transaction Fee charged to the Transaction Sender when the Transaction was finalized.
4. Compare the balance of the users' account protocol token balance minus the estimate Transaction Fee with the balance of the users' account protocol token balance minus the Transaction Fee of the finalized test transaction.
5. Verify that the Transaction Fee Refund from step 3. equals the comparison value in step 4.

Test Passing Criteria:

* The L2 must have calculated the Transaction Fee Refund.
* The Transaction Fee Refund must be accessible by the user.
* The Transaction Fee Refund must match the comparison result of step 4.

#### **[R11]**

An L2 MUST provide continuous access to the Transaction Fee, the Transaction Fee components, and Transaction Fee Refund, if applicable, of all Transaction finalized on the L2.

[[R11]](#r11) Testability: 

Preconditions:

* A test L2 is up and running.
* The L2 must have a defined process for submitting and finalizing Transactions.
* There is a set of test L2 transactions.

Test Steps:

1. Submit a set of Transactions to the L2.
2. Wait for the L2 to finalize the Transactions using transaction confirmation notifications as finalization confirmations.
3. Query the L2 for a Transaction ID from the set of finalized test transactions.
4. For a given Transaction ID, retrieve the Transaction ID, Transaction Fee, Transaction Fee components (Base Fee, Execution Fee, and Priority Fee), and Transaction Fee Refund (if applicable).
5. Verify that the retrieved Transaction Fee, Transaction Fee components, and Transaction Fee Refund (if applicable) match the values recorded in the transaction confirmations.
6. Repeat steps 3. through 5. for each Transaction ID in the set of test transactions at random time intervals during the test for the entire test transaction set.

Test Passing Criteria:

* Steps 3. through 5. are successfully completed for every transaction in the test transaction set, otherwise the test fails.


#### **[R12]**

An L2 MUST provide a capability that delivers a current Fee Price that a Transaction Fee calculation by the Transactions Sender or Transaction Originator can be based on. 

[[R12]](#r12) Testability:  

Preconditions:

* A test L2 is running and operational
* The L2 has a current Fee Price available
* A Transaction Sender or Transaction Originator is ready to send a transaction on the L2

Test steps:

1. Retrieve the current Fee Price from the L2.
2. Calculate a Transaction Fee based on the Fee Price obtained in step 1.
3. Send a transaction to the L2 with the calculated Transaction Fee.
4. Retrieve the Transaction Fee recorded by the L2 for the transaction sent in step 3.
5. Verify that the Transaction Fee recorded by the L2 matches the calculated Transaction Fee in step 2.

Test Passing criteria:

* The current Fee Price is successfully retrieved from the L2 in step 1.
* The calculated Transaction Fee matches the Transaction Fee recorded by the L2 in step 5.


## 3.2 Layer 2 Transaction Fee Visibility Requirements

In this section, this document discusses the visibility requirements for different L2 Transaction Types and Roles.

#### **[R13]**

A Transaction Originator, a Transaction Sender and a Developer MUST be able to view an estimated Transaction Fee and its components before an L2 Transaction is submitted.

[[R13]](#r13) Testability: 

Preconditions:

* An L2 instance is set up and running.
* A Transaction Originator, a Transaction Sender, and a Developer have access to the L2 and can interact with it.
* The L2 provides a capability to estimate Transaction Fees based on current operating conditions and other relevant factors.

Test Steps:

1. The Transaction Originator, the Transaction Sender, and the Developer navigate to the L2 interface and initiate the process of creating a new transaction.
2. The L2 interface displays the estimated Transaction Fee and its components (Base Fee, Execution Fee, and Priority Fee) to the Transaction Originator, the Transaction Sender, and the Developer.
3. The Transaction Originator, the Transaction Sender, and the Developer proceed to submit the Transaction to the L2.

Test Passing Criteria:

* The L2 interface displays the estimated Transaction Fee and its components accurately.
* The Transaction Originator, the Transaction Sender, and the Developer are able to review and verify the estimated Transaction Fee and its components before submitting the Transaction.

#### **[R14]**

A Transaction Originator, a Transaction Sender and a Developer MUST be able to view a Transaction Fee and its components after an L2 Direct Transaction has been processed on the L2.

[[R14]](#r14) Testability: 

Preconditions:

* An L2 instance is operational and available for use.
* The Transaction Originator, Transaction Sender, and Developer have access to the L2 and can view Transaction information.
* At least one Direct Transaction has been submitted and processed on the L2.
* The L2 has a defined method to notify L2 users that an L2 transaction has been processed.

Test Steps:

1. Transaction Sender or Developer submit a Direct Transaction to the L2.
2. The L2 processes the Direct Transaction and charges a Transaction Fee.
3. The Transaction Originator, Transaction Sender, or Developer accesses the L2 to view the Transaction Fee and its components after a Direct Transaction has been processed on the L2 using the Transaction ID from the transaction processing confirmation notification from the L2.
4. The Transaction Originator, Transaction Sender, or Developer verifies that they can see the Transaction Fee and its components, including the Base Fee, Execution Fee, Priority Fee.
5. The Transaction Originator, Transaction Sender, or Developer verifies that the Transaction Fee and its components displayed on the L2 match or is less than the Transaction Fee and its components displayed to them before submitting the Direct Transaction.
6. The Transaction Originator, Transaction Sender, or Developer verifies that the Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components charged to the Transaction Sender's account.

Test Passing Criteria: The test passes if,

* The Transaction Originator, Transaction Sender, or Developer can access the Transaction Fee and its components on the L2 after a Direct Transaction has been processed.
* The Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components displayed to the Transaction Originator, Transaction Sender, or Developer before submitting the Direct Transaction.
* The Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components charged to the Transaction Sender's account.


#### **[R15]**

An Intermediary and a Developer MUST be able to view a Transaction Fee and its components after an L2 Meta Transaction has been processed on the L2.

[[R15]](#r15) Testability: 

Preconditions:

* An L2 instance is operational and accepting transactions.
* The Intermediary and Developer have access to the L2.
* The Intermediary and Developer have a Meta Transaction ready to submit to the L2.
* The L2 has a defined method to notify L2 users that an L2 transaction has been processed.

Test Steps:

1. The Intermediary and Developer submit a Meta Transaction to the L2.
2. The L2 processes the Meta Transaction and charges a Transaction Fee.
3. The Intermediary and Developer access the Transaction and the Transaction Fee and its components for the processed Meta Transaction using the Transaction ID from the transaction processing confirmation notification from the L2.
4. The Intermediary and Developer verify that they can see the Transaction Fee and its components, including the Base Fee, Execution Fee, Priority Fee.
5. The Intermediary and Developer verify that the Transaction Fee and its components displayed on the L2 match or is less than the Transaction Fee and its components displayed to them before submitting the Meta Transaction.
6. The Intermediary and Developer verify that the Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components charged to the Transaction Sender's account.

Test Passing Criteria: The test passes if,

* The Intermediary and Developer can access the Transaction Fee and its components on the L2 after a Meta Transaction has been processed.
* The Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components displayed to the Transaction Originator, Transaction Sender, or Developer before submitting the Meta Transaction.
* The Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components charged to the Transaction Sender's account.

#### **[R16]**

A Transaction Originator, a Transaction Sender and a Developer MUST be able to view a Transaction Fee and its components after an L2 Direct Transaction has been finalized on the L2.

[[R16]](#r16) Testability: 

Preconditions:

* An L2 instance is operational and available for use.
* The Transaction Originator, Transaction Sender, and Developer have access to the L2 and can view Transaction information.
* At least one Direct Transaction has been submitted, processed and finalized on the L2.
* The L2 has a defined method to notify L2 users that an L2 transaction has been finalized.

Test Steps:

1. The Transaction Originator, Transaction Sender, or Developer accesses the L2 to view the Transaction Fee and its components after a Direct Transaction has been finalized on the L2 using the Transaction ID from the transaction finalization confirmation notification from the L2.
2. The Transaction Originator, Transaction Sender, or Developer verifies that they can see the Transaction Fee and its components, including the Base Fee, Execution Fee, Priority Fee.
3. The Transaction Originator, Transaction Sender, or Developer verifies that the Transaction Fee and its components displayed on the L2 match or is less than the Transaction Fee and its components displayed to them before submitting the Direct Transaction.
4. The Transaction Originator, Transaction Sender, or Developer verifies that the Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components charged to the Transaction Sender's account.

Test Passing Criteria: The test passes if,

* The Transaction Originator, Transaction Sender, or Developer can access the Transaction Fee and its components on the L2 after a Direct Transaction has been finalized.
* The Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components displayed to the Transaction Originator, Transaction Sender, or Developer before submitting the Direct Transaction.
* The Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components charged to the Transaction Sender's account.

#### **[R17]**

An Intermediary and a Developer MUST be able to view a Transaction Fee and its components after an L2 Meta Transaction has been finalized on the L2.

[[R17]](#r17) Testability: 

Preconditions:

* An L2 instance is operational and accepting transactions.
* The Intermediary and Developer have access to the L2.
* The Intermediary and Developer have a Meta Transaction ready to submit to the L2.
* The L2 has a defined method to notify L2 users that an L2 transaction has been finalized.

Test Steps:

1. The Intermediary and Developer submit a Meta Transaction to the L2.
2. The L2 processes, and finalizes the Meta Transaction and charges a Transaction Fee.
3. The Intermediary and Developer access the Transaction and the Transaction Fee and its components for the processed Meta Transaction using the Transaction ID from the transaction finalization confirmation notification from the L2.
4. The Intermediary and Developer verify that they can see the Transaction Fee and its components, including the Base Fee, Execution Fee, Priority Fee.
5. The Intermediary and Developer verify that the Transaction Fee and its components displayed on the L2 match or is less than the Transaction Fee and its components displayed to them before submitting the Meta Transaction.
6. The Intermediary and Developer verify that the Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components charged to the Transaction Sender's account.

Test Passing Criteria: The test passes if,

* The Intermediary and Developer can access the Transaction Fee and its components on the L2 after a Meta Transaction has been finalized.
* The Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components displayed to the Transaction Originator, Transaction Sender, or Developer before submitting the Meta Transaction.
* The Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components charged to the Transaction Sender's account.


#### **[R18]**

If there is a Transaction Fee Refund, a Transaction Originator, a Transaction Sender and a Developer MUST be able to view a Transaction Fee Refund after an L2 Direct Transaction has been finalized on the L2.

[[R18]](#r18) Testability: 

Preconditions:

* An L2 instance is operational and available for use.
* The Transaction Originator, Transaction Sender, and Developer have access to the L2 and can view Transaction information.
* At least one Direct Transaction has been submitted, processed and finalized on the L2.
* The L2 has a defined method to notify L2 users that an L2 transaction has been finalized.

Test Steps:

1. The Transaction Originator, Transaction Sender, or Developer accesses the L2 to view the Transaction Fee and its components after a Direct Transaction has been finalized on the L2 using the Transaction ID from the transaction finalization confirmation notification from the L2.
2. The Transaction Originator, Transaction Sender, or Developer verifies that they can see the Transaction Fee and its components, including the Base Fee, Execution Fee, Priority Fee.
3. The Transaction Originator, Transaction Sender, or Developer verifies that the Transaction Fee and its components displayed on the L2 is equal to or less than the Transaction Fee and its components displayed to the Transaction Originator, Transaction Sender, or Developer before submitting the Direct Transaction.
4. The Transaction Originator, Transaction Sender, or Developer verifies that the Transaction Fee and its components displayed on the L2 match the Transaction Fee and its components charged to the Transaction Sender's account.

Test Passing Criteria: The test passes if,

* The Transaction Originator, Transaction Sender, or Developer can access the Transaction Fee and its components on the L2 after a Direct Transaction has been finalized.
* The Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components displayed to the Transaction Originator, Transaction Sender, or Developer before submitting the Direct Transaction.
* The Transaction Fee and its components displayed on the L2 match or are less than the Transaction Fee and its components charged to the Transaction Sender's account, if applicable.

#### **[R19]**

If there is a Transaction Fee Refund, an Intermediary and a Developer MUST be able to view a Transaction Fee Refund after an L2 Meta Transaction has been finalized on the L2.

[[R19]](#r19) Testability: 

Preconditions:

* An L2 instance is operational and accepting transactions.
* The Intermediary and Developer have access to the L2.
* The Intermediary and Developer have a Meta Transaction ready to submit to the L2.
* The L2 has a defined method to notify L2 users that an L2 transaction has been finalized.

Test Steps:

1. The Intermediary and Developer submit a Meta Transaction to the L2.
2. The L2 processes, and finalizes the Meta Transaction and charges a Transaction Fee.
3. The Intermediary and Developer access the Transaction and the Transaction Fee and its components for the processed Meta Transaction using the Transaction ID from the transaction finalization confirmation notification from the L2.
4. The Intermediary and Developer verify that they can see the Transaction Fee and its components, including the Base Fee, Execution Fee, Priority Fee.
5. The Intermediary and Developer verify that the Transaction Fee and its components displayed on the L2 is less than the Transaction Fee and its components displayed to them before submitting the Meta Transaction.
6. The Intermediary and Developer verify that the Transaction Fee and its components displayed on the L2 match the Transaction Fee and its components charged to the Transaction Sender's account.

Test Passing Criteria: The test passes if,

* The Intermediary and Developer can access the Transaction Fee and its components on the L2 after a Meta Transaction has been finalized.
* The Transaction Fee and its components displayed on the L2 are less than the Transaction Fee and its components displayed to the Intermediary and Develope before submitting the Meta Transaction.
* The Transaction Fee and its components displayed on the L2 match the Transaction Fee and its components charged to the Transaction Sender's account.

#### **[R20]**

An L2 MUST provide an Intermediary with a capability to display the Transaction Fee and its components of an L2 Meta Transaction after it has been processed on the L2 to 3rd parties.

[[R20]](#r20) Testability: 

Preconditions:

* A L2 instance is operational and accessible.
* There is at least one Intermediary operating on the L2.
* At least one L2 Meta Transaction has been submitted and processed on the L2.
* The Intermediary can access the Transaction with its Transaction Fee and its Fee components.
* The L2 is accessible by any 3rd party.

Test Steps:

1. The Intermediary logs into their account on the L2.
2. The Intermediary selects the L2 Meta Transaction they wish to view the Transaction Fee and its components for using the Transaction ID from the transaction processing confirmation notification from the L2.
3. The L2 displays the Transaction Fee and its components of the selected L2 Meta Transaction to the Intermediary.
4. The Intermediary verifies that the displayed Transaction Fee and its components match or are less than the submitted Transaction Fee and its components.
5. The Intermediary attempts to display the Transaction Fee and its components of the selected L2 Meta Transaction to a 3rd party.
6. The 3rd party verifies that the displayed Transaction Fee and its components match the Transaction Fee and its components for the Transaction ID of the Meta Transaction when accessed directly on the L2 using the Transaction ID.

Test Passing Criteria:

* The Intermediary is able to view the Transaction Fee and its components of the selected L2 Meta Transaction.
* The displayed Transaction Fee and its components are accurate and match the actual Transaction Fee and its components of the selected L2 Meta Transaction.
* The Intermediary is able to display the Transaction Fee and its components of the selected L2 Meta Transaction to a 3rd party.
* The displayed Transaction Fee and its components match the actual Transaction Fee and its components of the selected L2 Meta Transaction as verified by the 3rd party.

#### **[R21]**

If there is a Transaction Fee Refund, an L2 MUST provide an Intermediary with a capability to display the Transaction Fee Refund of an L2 Meta Transaction to a 3rd party after it has been finalized on the L2.

[[R21]](#r21) Testability:  

Preconditions:

* An L2 instance is deployed and running.
* An Intermediary is operating on the L2 and has the necessary permissions to view Transaction Fee Refunds.
* A set of L2 Meta Transactions has been submitted and processed on the L2, resulting in at least one Transaction Fee Refund.

Test steps:

1. The Intermediary sends a request to the L2 to display the Transaction Fee Refund of a specific L2 Meta Transaction using the Transaction ID from the L2's transaction finalization confirmation notification.
2. The L2 receives the request and verifies that the Intermediary has the necessary permissions to view Transaction Fee Refunds.
3. The L2 retrieves the Transaction Fee Refund information for the requested L2 Meta Transaction.
4. The L2 sends the Transaction Fee Refund information to the Intermediary.
5. The Intermediary receives the Transaction Fee Refund information.
6. The Intermediary verifies that the Transaction Fee Refund information matches the expected values based on the difference in the L2 Meta Transaction Transaction Fee between the submitted and finalized L2 Meta Transaction.
7. The Intermediary displays the Transaction Fee Refund information to the requesting 3rd party.
8. The requesting 3rd party verifies that the displayed Transaction Fee and its components match the Transaction Fee and its components for the Transaction ID of the Meta Transaction when accessed directly on the L2 using the Transaction ID.

Test Passing criteria:

* The Intermediary is able to successfully retrieve and display the Transaction Fee Refund information for the requested L2 Meta Transaction.
* The displayed Transaction Fee Refund information matches the expected values based on the L2 Meta Transaction.

#### **[R22]**

A Transaction Originator, a Transaction Sender and a Developer MUST be able to view a current Fee Price that a Transaction Fee calculation by the Transactions Sender or Transaction Originator can be based on. 

[[R22]](#r22) Testability: 

Preconditions:

* An L2 instance is live and operational.
* The Transaction Originator, Transaction Sender, and Developer have access to the L2.
* The Fee Price calculation is based on the current Operating Condition of the L2.
* A Fee Price Emulator that can accurately calculate a Fee Price based on current Operating Conditions on the L2. 

Test steps:

1. The Transaction Originator, Transaction Sender, or Developer access the current Fee Price from the L2.
2. The L2 responds to the request by providing the current Fee Price.
3. The Transaction Originator, Transaction Sender, or Developer verifies that the Fee Price provided by the L2 network matches the Fee Price estimate using the Fee Price Emulator.

Test Passing criteria:

* The current Fee Price is successfully retrieved from the L2.
* The Fee Price provided by the L2 matches the Fee Price estimate using the Fee Price Emulator.

## 3.3 Transaction Fee Requirements for Layer 2 Transactions

In this section, the documents details Transaction Fee requirements for an L2 Transaction and its processing. 


#### **[R23]**

Every L2 Transaction MUST contain a Transaction Fee and its components.

[[R23]](#r23) Testability: 

Preconditions:

* An L2 instance is set up and functional.
* There is a user account on the L2 with the necessary permissions to submit a transaction.
* There is a sufficient balance of funds available in the user's account to cover the transaction fee.

Test Steps:

1. Log in to the user account on the L2.
2. Create a new L2 transaction.
3. Verify that the transaction contains a transaction fee and its components.
4. Submit the transaction.
5. Wait for the transaction to be processed and finalized on the L2.
6. Retrieve the details of the processed and finalized transaction using using the Transaction ID from the transaction finalization confirmation notification from the L2.
7. Verify that the transaction fee and its components are still present and accurate.

Test Passing Criteria:

* The L2 transaction contains a transaction fee and its components.
* The transaction fee and its components remain present and accurate after the transaction is processed and finalized on the L2.

#### **[R24]**

Every L2 Block MUST contain one or more L2 account addresses to which the accumulated Transaction Fees in said L2 Block are transferred either whole or in proportion based on the specification of the L2 protocol.

[[R24]](#r24) Testability: 

Preconditions:

* The L2 protocol and its specifications have been implemented and tested.
* An L2 instance is set up and functional.
* A set of L2 transactions have been created and finalized on the L2.

Test steps:

1. Verify that every L2 block has one or more L2 account 
addresses specified to receive the accumulated Transaction Fees.
2. Verify that the accumulated Transaction Fees from each L2 transaction in the block have been transferred to the specified L2 account address(es).
3. Verify that the transfer of the accumulated Transaction Fees is done either whole or in proportion to the account 
addresses specified to receive the accumulated Transaction Fees in the L2 Block.

Test Passing criteria:

* Step 1, 2, and 3 must pass for all L2 blocks that have been finalized on the L2 that contain the test L2 transactions.

#### **[R25]**

If one or more L2 Transactions are reverted before they are finalized on the L2's Layer 1, the Transaction Fees in the affected Transactions MUST not be charged to the Transaction Senders.

Note, that it is not important why an L2 Transaction has been reverted before it is finalized.

[[R25]](#r25) Testability:  

Preconditions:

* An L2 instance is set up and functional.
* There are at least two valid L2 Transactions that have not been finalized on the L2's Layer 1.
* Each L2 Transaction has a valid Transaction Sender.
* The L2 Transactions have Transaction Fees associated with them.
* The L2 protocol supports the reversion of Transactions before they are finalized on Layer 1.

Test Steps:

1. Verify that the initial balances of the Transaction Senders are recorded.
2. Submit the L2 Transactions to the L2.
3. Verify that the L2 Transactions are valid and the Transaction Fees are calculated correctly.
4. Attempt to revert one of the L2 Transactions before it is finalized on the L2's Layer 1.
5. Verify that the reverted L2 Transaction's Transaction Fees are not charged to the Transaction Sender.
6. Finalize the remaining L2 Transactions on the L2's Layer 1.
7. Verify that the Transaction Fees are charged to the Transaction Senders for the finalized L2 Transactions.
8. Verify that the balances of the Transaction Senders have been updated accordingly.

Test Passing Criteria:

* The balances of the Transaction Senders are updated correctly after the L2 Transactions are finalized.
* The Transaction Fees for the finalized L2 Transactions are charged to the corresponding Transaction Senders.
* The Transaction Fees for the reverted L2 Transactions are not charged to the corresponding Transaction Senders.

#### **[D1]**

If an L2 Meta Transaction is reverted before it is finalized on the processing L2's Layer 1 and the Transaction Originator has been charged the Transaction Fee by the Intermediary, the Transaction Fee in the reverted Meta Transaction SHOULD be refunded to the Transaction Originator by the Intermediary.

[[D1]](#d1) Testability: 

Preconditions:

* An L2 instance is set up and available for testing.
* A set of L2 Meta Transactions has been submitted by the Transaction Sender and processed on the L2.
* Some of the L2 Meta Transactions have been reverted before being finalized on the L2's Layer 1.

Test steps:

1. Submit a set of L2 Meta Transactions to the L2.
2. Verify that the Transaction Sender and Developer can view the estimated Transaction Fees and their components before submitting the L2 Meta Transactions.
3. Verify that the Intermediary can view and record the Transaction Fees and their components after the L2 Meta Transactions have been processed on the L2.
5. Revert some of the L2 Meta Transactions before they are finalized on the L2's Layer 1.
6. The Intermediary returns the recorded Transaction Fees for the reverted Meta Transactions from the Transaction Sender Account or the account of the Intermediary to the account of the Transaction Originator. 
7. Verify that the Transaction Originator received the Transaction Fee Refund and it has the right value.

Test passing criteria:

* The Intermediary, Transaction Sender and Developer can view the estimated Transaction Fees and their components before submitting the L2 Meta Transactions.
* The Intermediary can view the Transaction Fees and their components after the L2 Meta Transactions have been processed on the L2.
* The Intermediary returns the right amount of Transaction Fees as a refund to the Transaction Originator when L2 Meta Transactions are reverted.

-------
# 4 Conformance

###### L2TFSPECCONF

This section describes the conformance clauses and tests required to achieve an implementation that is provably conformant with the requirements in this document.

## 4.1 Conformance Targets

###### L2TFSPECCONFT

This document does not yet define a standardized set of test-fixtures with test inputs for all MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements. 

A standardized set of test-fixtures with test inputs for all MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements is intended to be published with the next version of the standard.

## 4.2 Conformance Levels

###### L2TFSPECCONFL

This section specifies the conformance levels of this standard. The conformance levels offer implementers several levels of conformance. These can be used to establish competitive differentiation.

This document defines the conformance levels of L2 Transaction Fees as follows:
* **Level 1:** All MUST requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.
* **Level 2:** All MUST and SHOULD requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.
* **Level 3:** All MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.

#### **[D2]** 
A claim that a Transaction Fee conforms to this specification SHOULD describe a testing procedure carried out for each requirement to which conformance is claimed, that justifies the claim with respect to that requirement.

[[D2]](#d2) Testability: Since each of the non-conformance-target requirements in this documents is testable, so must be the totality of the requirements in this document. Therefore, conformance tests for all requirements can exist, and can be described as required in [[D2]](#d2).

#### **[R26]** 
A claim that a Transaction Fee conforms to this specification at **Level 2** or higher MUST describe the testing procedure carried out for each requirement at **Level 2** or higher, that justifies the claim to that requirement.

[[R26]](#r26) Testability: Since each of the non-conformance-target requirements in this documents is testable, so must be the totality of the requirements in this document. Therefore, conformance tests for all requirements can exist, be described, be built and implemented and results can be recorded as required in [[R26]](#r26).


-------

# Appendix A - References
###### L2TFSPECAPA

This appendix contains the normative and non-normative references that are used in this document. 

While any hyperlinks included in this appendix were valid at the time of publication, OASIS cannot guarantee their long-term validity.

## A.1 Normative References
###### L2TFSPECAPREFNORM

The following documents are referenced in such a way that some or all of their content constitute requirements of this document.

#### **[RFC2119]**
 S. Bradner, Key words for use in RFCs to Indicate Requirement Levels, http://www.ietf.org/rfc/rfc2119.txt, IETF RFC 2119, March 1997.


## A.2 Non-Normative References
###### L2TFSPECAPREFNONNORM

#### **[W3C-String-Meta]**

Strings on the Web: Language and Direction Metadata, R. Ishida, A. Phillips, August 2022,
https://www.w3.org/TR/string-meta/


# Appendix B - Security Considerations
###### L2TFSPECAPBSEC

There are no additional security requirements.

It should be noted that any Layer 2 should have completed a security audit by a reputable security auditor and resolved all security issues before going to production.

## B.1 Data Privacy
###### L2TFSPECAPBDP

The standard does not set any requirements for compliance to jurisdiction legislation/regulations. It is the responsibility of the implementer to comply with applicable data privacy laws.

## B.2 Production Readiness 
###### L2TFSPECAPBPR

The standard does not set any requirements for the use of specific applications/tools/libraries etc. The implementer should perform due diligence when selecting specific applications/tools/libraries.

## B.3 Internationalization and Localization Reference
###### L2TFSPECAPBINT

The standard encourages implementers to follow the [W3C "Strings on the Web: Language and Direction Metadata" best practices guide](#w3c-string-meta) for identifying language and base direction for strings used on the Web wherever appropriate. 

<!--

(Note: OASIS strongly recommends that Open Projects consider issues that might affect safety, security, privacy, and/or data protection in implementations of their specification and document them for implementers and adopters. For some purposes, you may find it required, e.g. if you apply for IANA registration.

While it may not be immediately obvious how your specification might make systems vulnerable to attack, most specifications, because they involve communications between systems, message formats, or system settings, open potential channels for exploitation. For example, IETF [[RFC3552](#rfc3552)] lists “eavesdropping, replay, message insertion, deletion, modification, and man-in-the-middle” as well as potential denial of service attacks as threats that must be considered and, if appropriate, addressed in IETF RFCs.

In addition to considering and describing foreseeable risks, this section should include guidance on how implementers and adopters can protect against these risks.

We encourage editors and OP members concerned with this subject to read _Guidelines for Writing RFC Text on Security Considerations_, IETF [[RFC3552](#rfc3552)], for more information.

-->

-------

# Appendix C - Acknowledgments
###### L2TFSPECAPC
<!--
`(Note: A Work Product approved by the OP should include a list of people who participated in the development of the Work Product. This is generally done by collecting the list of names in this appendix. This list should be initially compiled by the Chair, and any Member of the OP may add or remove their names from the list by request. Remove this note before submitting for publication.)`
-->

The following individuals have participated in the creation of this specification and are gratefully acknowledged.

**Participants**:

Daniel Goldman \
Kelvin Fichter \
Andreas Freund \
...

 
-------

# Appendix D - Revision History
###### L2TFSPECAPD

Revisions made since the initial stage of this numbered Version of this document have been tracked on [Github](https://github.com/eea-oasis/L2/tree/main/workitems/l2-transaction-fees/l2-transaction-fees-v1.0-psd01.md).

-------

# Appendix E - Notices
###### L2TFSPECAPBE

Copyright © OASIS Open 2022. All Rights Reserved.

All capitalized terms in the following text have the meanings assigned to them in the OASIS Intellectual Property Rights Policy (the "OASIS IPR Policy"). The full [Policy](https://www.oasis-open.org/policies-guidelines/ipr) may be found at the OASIS website.

This specification is published under the [CC0 1.0 Universal (CC0 1.0)](http://creativecommons.org/publicdomain/zero/1.0/) license. Portions of this specification are also provided under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

All contributions made to this project have been made under the [OASIS Contributor License Agreement (CLA)](https://www.oasis-open.org/policies-guidelines/open-projects-process#individual-cla-exhibit).

For information on whether any patents have been disclosed that may be essential to implementing this specification, and any offers of patent licensing terms, please refer to the [Open Projects IPR Statements](https://github.com/oasis-open-projects/administration/blob/master/IPR_STATEMENTS.md) page.

This document and translations of it may be copied and furnished to others, and derivative works that comment on or otherwise explain it or assist in its implementation may be prepared, copied, published, and distributed, in whole or in part, without restrictions of any kind, provided that the above copyright notice and this section are included on all such copies and derivative works. However, this document itself may not be modified in any way, including by removing the copyright notice or references to OASIS, except as needed for the purpose of developing any document or deliverable produced by an OASIS Open Project (in which case the rules applicable to copyrights, as set forth in the OASIS IPR Policy, must be followed) or as required to translate it into languages other than English.

The limited permissions granted above are perpetual and will not be revoked by OASIS or its successors or assigns.

This document and the information contained herein is provided on an "AS IS" basis and OASIS DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE. OASIS AND ITS MEMBERS WILL NOT BE LIABLE FOR ANY DIRECT, INDIRECT, SPECIAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF ANY USE OF THIS DOCUMENT OR ANY PART THEREOF.

As stated in the OASIS IPR Policy, the following three paragraphs in brackets apply to OASIS Standards Final Deliverable documents (Project Specifications, OASIS Standards, or Approved Errata).

\[OASIS requests that any OASIS Party or any other party that believes it has patent claims that would necessarily be infringed by implementations of this OASIS Standards Final Deliverable, to notify OASIS TC Administrator and provide an indication of its willingness to grant patent licenses to such patent claims in a manner consistent with the IPR Mode of the OASIS Open Project that produced this deliverable.\]

\[OASIS invites any party to contact the OASIS TC Administrator if it is aware of a claim of ownership of any patent claims that would necessarily be infringed by implementations of this OASIS Standards Final Deliverable by a patent holder that is not willing to provide a license to such patent claims in a manner consistent with the IPR Mode of the OASIS Open Project that produced this OASIS Standards Final Deliverable. OASIS may include such claims on its website but disclaims any obligation to do so.\]

\[OASIS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this OASIS Standards Final Deliverable or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on OASIS' procedures with respect to rights in any document or deliverable produced by an OASIS Open Project can be found on the OASIS website. Copies of claims of rights made available for publication and any assurances of licenses to be made available, or the result of an attempt made to obtain a general license or permission for the use of such proprietary rights by implementers or users of this OASIS Standards Final Deliverable, can be obtained from the OASIS TC Administrator. OASIS makes no representation that any information or list of intellectual property rights will at any time be complete, or that any claims in such list are, in fact, Essential Claims.\]

The name "OASIS" is a trademark of [OASIS](https://www.oasis-open.org/), the owner and developer of this specification, and should be used only to refer to the organization and its official outputs. OASIS welcomes reference to, and implementation, and use of, specifications, while reserving the right to enforce its marks against misleading uses. Please see https://www.oasis-open.org/policies-guidelines/trademark for the above guidance.

![OASIS Logo](http://docs.oasis-open.org/templates/OASISLogo-v2.0.jpg)
-------
