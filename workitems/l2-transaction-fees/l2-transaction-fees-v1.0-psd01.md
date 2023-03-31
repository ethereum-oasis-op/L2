
![EEA Logo](../l2-transaction-fees/images/eea-symbol.png)
-------

# Layer 2 Transaction Fee Specification Version 1.0

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

The L2 WG is an open-source initiative with a scope to
- Identify and document the most relevant use cases and business requirements for Layer 2 and other Blockchain Scalability solutions for EVM compatible public blockchains
- Define a technical standard with identification and differentiation of classes of scalability solutions as required that meet both ecosystem and enterprise requirements, with a particular focus on interoperability between Layer 2 solutions for EVM compatible public blockchains
- For EVM compatible public blockchains, identify, document, and devise solution approaches for Layer 2 Blockchain scalability solution specific challenges such as MEV, block (gas) limits, TVL concentration, etc.
- Identify and document characteristics of Layer 2 Blockchain environments for EVM compatible public blockchains that will be key in addressing mainstream and enterprise adoption.

The work is an [EEA Community Project](https://entethalliance.org/eeacommunityprojects/), which is managed by [OASIS](https://oasis-open-projects.org/).

## 1.1 Overview

Layer 2 (L2) Transaction Fees are a crucial element of financing the operations of L2 platforms apart from rewards given to participants for providing economic security guarantees such as validators in consensus protocols. Yet how these transaction fees are derived, to whom they are paid, how and where they are displayed to any of the participants in L2 platforms varies greatly between L2 platforms. 

Given the above, the need for transparency in a open ecosystem to build trust, and the evolving legal and regulatory landscape around fee transparency and what type of fees can be charged, this document sets out to define the different types of L2 transaction fees and then define requirements around transaction fee transparency for L2 platforms.

Note, that fees associated with asset and data bridges between L2 platforms is beyond the scope of this document, as well as between L2 platforms and centralized exchanges.


## 1.2 Glossary

**Account:**

A unit that is minimally comprised of a unique account identifier, a deterministic ordering parameter, also referred to as a nonce, a balance of a Layer 1, Layer 2 or Sidechain unit of exchange, also referred to as a protocol token. Changes to an account are controlled by a unique cryptographic public and private key pair. There are typically additional account elements referring to instructions and data associated to the account that determine account changes. 

**Base Fee:**

The minimum amount of gas or a Layer 2 gas equivalent unit of compute and storage consumption required to include a transaction on a Layer 2.  

**Blockchain:**

An open, distributed ledger that can record transactions between two parties efficiently and in a verifiable and permanent way.

**Bridge:** 

The means for the transfer of information and digital assets between between Layer 2s, Layer 1s, and Sidechains.

**Developer:**

An individual writing computer code for software applications that operate on a Layer 1, Layer 2 or Sidechain.

**Direct Transaction:**
A transaction where the transaction originator is also the transaction sender.

**Execution Fee:**

A fee to be paid by the transaction originator sufficient to cover both the Layer 2 and Layer 1 transaction fees.

An example calculation of such an Execution Fee is:
$$L2\space Gas\space Limit + {L1\space Transaction\space Fee \over L2\space Gas\space Price}$$

**Fee Price:**

A Layer 2 gas price or a price of a Layer 2 gas equivalent unit of compute and storage consumption.

Note that a gas price or a price of a Layer 2 gas equivalent unit of compute and storage consumption is typically variable and changes with the level of usage of a Layer 2 network. Note, that a gas price is expressed in Giga Wei (GWEI) for EVM-compatible networks, where Wei represents the smallest unit of gas; 1 Wei = 10<sup>-18</sup> Eth in Ethereum's native token.

**Gas:**

Refers to the unit that measures the amount of computational and storage effort required to execute specific operations on an EVM-compatible network.

**Intermediary:**

An entity that is the sender of a transaction for which it is not the transaction originator.

**Layer 1:**

A base network, such as Bitcoin, or Ethereum, and its underlying infrastructure that validates and finalizes transactions without the need of another network.

**Layer 2:**

A secondary framework or protocol that is built on top of an existing Layer 1 system in such a way that it inherits the security properties of the Layer 1 system while allowing for a higher transaction throughput that the Layer 1 system.

**Layer 2 Operator:**

An entity responsible for the operation of a Layer 2.

**Maximal Extractable Value:**

Refers to the maximum value that can be extracted from block production in excess of the standard block reward and gas fees by including, excluding, and changing the order of transactions in a block.

**Meta Transaction:**

A transaction where the transaction sender is not the transaction originator, and the transaction fee for the transaction originator is different if the same transaction was a direct transaction.

**Priority Fee:**

To be paid by the transaction originator to a Layer 2 sequencer to obtain a desired slot for its transaction in a new block.

Note that the exact position of a transaction in a new block may be determined by factors such as time-stamp, or minimization of Maximal Extractable Value (MEV) of a block in addition to a Priority Fee.

**Sequencer:**

Collects transactions, publishes them in a batch to the Layer 1 on which the Layer 2 operates, receives transaction fees from the published transactions, pays Layer 2 fees to other Layer 2 protocol participants, and, if required, participates in a consensus algorithm with other sequencers to determine transaction  ordering in a block.

**Sidechain:**

A secondary blockchain connected to the main blockchain with a two-way peg and using its own trust assumptions.

**State:**

The set of all accounts on a Layer 2 that are mapped to one another using a cryptographic data structure.

**State Transition:**

An event that deterministically changes one or more accounts in the set of all accounts that comprise the complete state of a Layer 2.

**Transaction:**

A digitally signed message sent from an Layer 2 account that contains instructions and data that result in a Layer 2 state transition. 

**Transaction Fee:**

The fee in a Layer 2 network or protocol token to be paid by a transaction originator comprised of the sum of a Base Fee, an Execution Fee and a Priority Fee.

**Transaction Originator:**

The account that created a transaction for a Layer 1, Layer 2, or Sidechain.

**Transaction Sender:**

The account that sent a transaction to a Layer 1, Layer 2, or Sidechain.


## 1.3 Typographical Conventions

### 1.3.1 Requirement Ids

A requirement is uniquely identified by a unique ID composed of its requirement level followed by a requirement number, as per convention **[RequirementLevelRequirementNumber]**. 
There are four requirement levels that are coded in requirement ids as per below convention: 

**[R]** - The requirement level for requirements which IDs start with the letter _R_ is to be interpreted as **MUST** as described in [RFC2119](#rfc2119). \
**[D]** - The requirement level for requirements which IDs start with the letter _D_ is to be interpreted as **SHOULD** as described in [RFC2119](#rfc2119). \
**[O]** - The requirement level for requirements which IDs start with the letter _O_ is to be interpreted as **MAY** as described in [RFC2119](#rfc2119). 

Note that requirements are uniquely numbered in ascending order within each requirement level.

Example : It should be read that [R1] is an absolute requirement of the specification whereas [D1] is a recommendation and [O1] is truly optional.

-------

# 2 Concepts and Design

To specify requirements about L2 transaction fees, this document will first:
- Define the meaning of a transaction fee and its components
- Define the roles relevant to transaction fees
- Define transaction types and their relationship to transaction fees

Note, that all definitions can be found in the [Glossary](#12-glossary)

Subsequently, the specification section will define requirements around fee transparency, fee estimation, final fees, and how, when and where fees are communicated to the different roles. The specification will also discuss requirements around responsibilities and accountability of roles towards one another.

## 2.1 Definition of Transaction Fee and its Components

This document defines Transaction Fee as the fee in a Layer 2 network or protocol token to be paid by a transaction originator comprised of the sum of a Base Fee, an Execution Fee and a Priority Fee.

Note that this document defines as Transaction as a digitally signed message sent from an Layer 2 account that contains instructions and data that result in a Layer 2 state transition. Also note that this document defines State and State Transition as follows:
- State: The set of all accounts on a Layer 2 that are mapped to one another using a cryptographic data structure.
- State Transition: An event that deterministically changes one or more accounts in the set of all accounts that comprise the complete state of a Layer 2.

Further note that this document defines Account as a unit that is minimally comprised of a unique account identifier, a deterministic ordering parameter, also referred to as a nonce, a balance of a Layer 1, Layer 2 or Sidechain unit of exchange, also referred to as a protocol token. Changes to an account are controlled by a unique cryptographic public and private key pair. There are typically additional account elements referring to instructions and data associated to the account that determine account changes.

In formula form the Transaction Fee is given as:

**Transaction Fee = Base Fee + Execution Fee + Priority Fee**

The different components are defined as follows:
- **Base Fee:** The minimum amount of Gas or a Layer 2 gas equivalent unit of compute and storage consumption required to include a transaction on a Layer 2.
- **Execution Fee:** A fee to be paid by the transaction originator sufficient to cover both the Layer 2 and Layer 1 transaction fees.
- **Priority Fee:** To be paid by the transaction originator to a Layer 2 sequencer to obtain a desired slot for its transaction in a new block. Note that the exact position of a transaction, a slot, in a new block may be determined by factors such as time-stamp, or minimization of Maximal Extractable Value (MEV) of a block in addition to a Priority Fee. And that MEV is defined as the maximum value that can be extracted from block production in excess of the standard block reward and gas fees by including, excluding, and changing the order of transactions in a block.

Note that a Transaction Fee has a Transaction Fee Price which is defined in the context of this document as a Layer 2 Gas price or a price of a Layer 2 gas equivalent unit of compute and storage consumption.

Note that a Gas price or a price of a Layer 2 gas equivalent unit of compute and storage consumption is typically variable and changes with the level of usage of a Layer 2 network. Note, that a gas price is expressed in Giga Wei (GWEI) for EVM-compatible networks, where Wei represents the smallest unit of gas; 1 Wei = 10<sup>-18</sup> Eth in Ethereum's native token.

Furthermore, note that Gas in this document refers to the unit that measures the amount of computational and storage effort required to execute specific operations on an EVM-compatible network. 

## 2.2 Definition of L2 Roles relevant to Transaction Fees

The following roles are relevant to transaction fees, their calculation and how, when and where they are presented:
- **Transaction Originator:** The account that created a transaction for a Layer 1, Layer 2, or Sidechain.
- **Transaction Sender:** The account that sent a transaction to a Layer 1, Layer 2, or Sidechain.
- **Intermediary:** An entity that is the sender of a transaction for which it is not the transaction originator.
- **Sequencer:** Collects transactions, publishes them in a batch to the Layer 1 on which the Layer 2 operates, receives transaction fees from the published transactions, pays Layer 2 fees to other Layer 2 protocol participants, and, if required, participates in a consensus algorithm with other sequencers to determine transaction  ordering in a block.
- **Layer 2 Operator:** An entity responsible for the operation of a Layer 2.
- **Developer:** An individual writing computer code for software applications that operate on a Layer 1, Layer 2 or Sidechain.

## 2.3 Definition of Transaction Types

There are different types of transactions, and depending on the context transaction fees are paid for differently and by different roles.

There are two types of transactions in the context of this document:
- **Direct Transaction:** A transaction where the transaction originator is also the transaction sender.
- **Meta Transaction:** A transaction where the transaction sender is not the transaction originator, and the transaction fee for the transaction originator is different if the same transaction was a direct transaction.

In the case of a Direct Transaction the Transaction Originator pays for the Transaction Fee based on the Transaction Fee Price the Transaction Originator is maximally willing to pay.

In the case of a Meta Transaction, the Transaction Originator may pay only a portion or no transaction fees at all. Instead, an Intermediary pays all or part of the Transaction Fee. Note that the Intermediary may be the Transaction Sender, or pay the Transaction Sender for the Transaction Fees incurred. Also note that the Transaction Originator may pre-pay Transaction Fees to the Intermediary or the Transaction Sender or both, or submit payment together with the Transaction sent to the Intermediary.

Therefore, the communication of a Transaction Fee and its components is different for different business scenarios. This document will not break down requirements by business scenario but rather by role and if that role is responsible to pay part or all of a Transaction Fee. 

-------

# 3 Layer 2 Transaction Fee Specification

In this section we will formulate requirements in the following areas:
- Transparency
- Visibility
- Roles and Transactions

## 3.1 Transaction Fee Transparency Requirements

#### **[R1]**

A L2 Transaction Fee MUST be comprised as the sum of the Base Fee, the Execution Fee, and the Priority Fee.

[[R1]](#r1) Testability: Mathematical equality equations can be translated into computer code, and any computer code is testable. Therefore, the requirement is testable.

#### **[R2]**

All components of a L2 Transaction Fee MUST NOT be less than zero.

[[R2]](#r2) Testability: Mathematical equality equations can be translated into computer code, and any computer code is testable for specific conditions such as the sum of three elements, or each individual element being less than zero. Therefore, the requirement is testable.

#### **[O1]**

A L2 Transaction Fee or any of its components MAY BE zero.

[[O1]](#o1) Testability: Mathematical equality equations can be translated into computer code, and any computer code is testable for specific conditions such as the sum of three elements, or each individual element being zero. Therefore, the requirement is testable.

#### **[R3]**

The setting and/or calculation of a Base Fee MUST be well documented and verifiable.

[[R3]](#r3) Testability: Documentation about the setting and/or calculation of a Base Fee can be reviewed by individuals, and subsequently compared to computer code that sets and/or calculates a Base Fee. And computer code is always testable. Therefore, the requirement is testable.

#### **[R4]**

The setting and/or calculation of an Execution Fee MUST be well documented and verifiable.

[[R4]](#r4) Testability: Documentation about the setting and/or calculation of an Execution can be reviewed by individuals, and subsequently compared to computer code that sets and/or calculates an Execution Fee. And computer code is always testable. Therefore, the requirement is testable.

#### **[R5]**

The setting of a Priority Fee MUST be well documented and verifiable.

[[R5]](#r5) Testability: Documentation about the setting of a Priority Fee can be reviewed by individuals, and subsequently compared to computer code that sets a Priority Fee. And computer code is always testable. Therefore, the requirement is testable.



## 3.2 Transaction Fee Visibility Requirements


## 3.3 Requirements for Roles and Transactions




-------
# 4 Conformance

This section describes the conformance clauses and tests required to achieve an implementation that is provably conformant with the requirements in this document.

## 4.1 Conformance Targets

This document does not yet define a standardized set of test-fixtures with test inputs for all MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements. 

A standardized set of test-fixtures with test inputs for all MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements is intended to be published with the next version of the standard.

## 4.2 Conformance Levels

This section specifies the conformance levels of this standard. The conformance levels offer implementers several levels of conformance. These can be used to establish competitive differentiation.

This document defines the conformance levels of Layer 2 Transaction Fees as follows:
* **Level 1:** All MUST requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.
* **Level 2:** All MUST and SHOULD requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.
* **Level 3:** All MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.

#### **[DX]** 
A claim that a Layer 2 transaction fee implementation conforms to this specification SHOULD describe the testing procedure used to justify the claim.

#### **[RX]** 
A claim that a Layer 2 transaction fee conforms to this specification at **level 2** or higher MUST describe the testing procedure used to justify the claim.


-------

# Appendix A - References

This appendix contains the normative and non-normative references that are used in this document. 

While any hyperlinks included in this appendix were valid at the time of publication, OASIS cannot guarantee their long-term validity.

## A.1 Normative References

The following documents are referenced in such a way that some or all of their content constitute requirements of this document.

#### **[RFC2119]**
 S. Bradner, Key words for use in RFCs to Indicate Requirement Levels, http://www.ietf.org/rfc/rfc2119.txt, IETF RFC 2119, March 1997.


## A.2 Non-Normative References

TBD


# Appendix B - Security Considerations

TBD

## B.1 Data Privacy

The standard does not set any requirements for compliance to jurisdiction legislation/regulations. It is the responsibility of the implementer to comply with applicable data privacy laws.

## B.2 Production Readiness 

The standard does not set any requirements for the use of specific applications/tools/libraries etc. The implementer should perform due diligence when selecting specific applications/tools/libraries.

<!--

(Note: OASIS strongly recommends that Open Projects consider issues that might affect safety, security, privacy, and/or data protection in implementations of their specification and document them for implementers and adopters. For some purposes, you may find it required, e.g. if you apply for IANA registration.

While it may not be immediately obvious how your specification might make systems vulnerable to attack, most specifications, because they involve communications between systems, message formats, or system settings, open potential channels for exploitation. For example, IETF [[RFC3552](#rfc3552)] lists “eavesdropping, replay, message insertion, deletion, modification, and man-in-the-middle” as well as potential denial of service attacks as threats that must be considered and, if appropriate, addressed in IETF RFCs.

In addition to considering and describing foreseeable risks, this section should include guidance on how implementers and adopters can protect against these risks.

We encourage editors and OP members concerned with this subject to read _Guidelines for Writing RFC Text on Security Considerations_, IETF [[RFC3552](#rfc3552)], for more information.

-->

-------

# Appendix C - Acknowledgments
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

Revisions made since the initial stage of this numbered Version of this document have been tracked on [Github](https://github.com/eea-oasis/L2/tree/main/workitems/l2-transaction-fees/l2-transaction-fees-v1.0-psd01.md).

-------

# Appendix E - Notices

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
