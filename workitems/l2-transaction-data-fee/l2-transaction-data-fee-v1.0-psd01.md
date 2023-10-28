
![EEA Logo](../l2-transaction-data-fee/images/eea-symbol.png)
-------

# Layer 2 Transaction Data Fee Specification Version 1.0
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
Landon Gingerich (lg@matterlabs.dev)\
Daniel Goldman (dgoldman@offchainlabs.com)\
Nikolai Prokhorenko (nikolai.p@metis.io)

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

[L2 Transaction Fee Specification](https://github.com/eea-oasis/L2/blob/main/workitems/l2-transaction-data-fee/l2-transaction-data-fee-v1.0-psd01.md) [Not yet the version from PR 43]


#### Abstract:
The document describes the minimal set of business and technical prerequisites, functional and non-functional requirements for a Layer 2 Transaction Data Fee that when implemented ensures that Layer 2 solutions are transparently and consistently calculating and displaying a Layer 2 Transaction Data Fee.

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

**[l2-transaction-data-fee-v1.0]** _Layer 2 Transaction Data Fee Version 1.0_. Edited by Kelvin Fichter, Andreas Freund, Landon Gingerich,Daniel Goldman, Nikolai Prokhorenko . 27 October 2023. OASIS Standard. https://github.com/eea-oasis/L2/tree/main/workitems/l2-transaction-data-fee/l2-transaction-data-fee-v1.0-psd01.md. Latest stage: https://github.com/eea-oasis/L2/tree/main/workitems/l2-transaction-data-fee/l2-transaction-data-fee-v1.0-psd01.md.

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
[3 Layer 2 Transaction Data Fee Specification](#3-layer-2-transaction-data-fee-specification) \
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

A Layer 2 (L2) Transaction Data Fee is a very large, variable and, therefore, crucial element of the L2 Execution Fee which in turn is typically the largest part of an L2 Transaction Fee. Yet how a Transaction Data Fee is derived varies greatly between L2 platforms, and is not separately displayed to any of the participants in L2 platforms.

Given the above, the need for transparency in a open ecosystem to build trust, and the evolving legal and regulatory landscape around fee transparency and what type of fees can be charged, this document sets out to define an L2 Transaction data Fee and specify requirements around its derivation, transparency and visibility for L2 platforms.


## 1.2 Glossary
###### L2TFSPECGLOS

**Account:**

A unit that is minimally comprised of a unique account identifier, a deterministic ordering parameter, also referred to as a nonce, a balance of a Layer 1, Layer 2 or Sidechain unit of exchange, also referred to as a protocol token. Changes to an account are controlled by a unique cryptographic public and private key pair. There are typically additional account elements referring to instructions and data associated to the account that determine account changes. 

**Base Fee:**

The minimum amount of gas or a Layer 2 gas equivalent unit of compute and storage consumption required to include a transaction on a Layer 2.  

**Blockchain:**

An open, distributed ledger that can record transactions between two parties efficiently and in a verifiable and permanent way.

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

The difference between the Transaction Fee that the Transaction Sender has included in the Transaction when sent to the Layer 2 and the Transaction Fee that has been charged to the Transaction Sender when a Transaction has been finalized on the Layer 2.

**Transaction Data Fee:**
The portion of the Execution fee in a Layer 2 (L2) network or protocol token to be paid by a Transaction Originator or Transaction Sender that is derived from the amount of L2 transaction data stored on the L1.

**L1 Gas Price:**
An L2 Gas price or a price of an L2 gas equivalent unit of compute and storage consumption based on L2 transaction data stored on the L1

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

To specify requirements about a L2 Transaction Data Fee, this document will first:

* Define the meaning of an L2 Transaction Data Fee
* Define requirements requirements on an L2 Transaction Data Fee and its relationships to L2 transaction fee types.

Note, that all definitions can be found in the [Glossary](#12-glossary)

The specification section will define requirements around Transaction Data Fee transparency, estimation, final amount, and how, when and where such a fee is communicated to different roles.

## 2.1 Definition of an L2 Transaction Data Fee
###### L2TFSPECDEF

This document defines an L2 Transaction Data Fee as the portion of the Execution fee in a Layer 2 (L2) network or protocol token to be paid by a Transaction Originator or Transaction Sender that is derived from the amount of L2 transaction data stored on the L1.

This documents follows the definitions of Transaction, Account, State and State Transition in [L2 Transaction Fee Specification](https://github.com/eea-oasis/L2/blob/main/workitems/l2-transaction-fees/l2-transaction-fees-v1.0-psd01.md). [Note: This is not yet the merged version of PR 43]

Note that a Transaction Data Fee has an L1 Gas Price which is defined in the context of this document as an L2 Gas price or a price of an L2 gas equivalent unit of compute and storage consumption based on L2 transaction data stored on the L1.

Note that a Gas price or a price of an L2 gas equivalent unit of compute and storage consumption is typically variable and changes with the level of usage of an L2/L1 network. Note that a gas price is expressed in Giga Wei (GWEI) for EVM-compatible networks, where Wei represents the smallest unit of gas; 1 Wei = 10<sup>-18</sup> Eth in Ethereum's native token.

Furthermore, note that Gas in this document refers to the unit that measures the amount of computational and storage effort required to execute specific operations on an EVM-compatible network.

## 2.2 Definition of L2 Roles relevant to an L2 Transaction Data Fee
###### L2TFSPECDEFROLES

This document follows the role definitions in the [L2 Transaction Fee Specification](https://github.com/eea-oasis/L2/blob/main/workitems/l2-transaction-fees/l2-transaction-fees-v1.0-psd01.md). [Note: This is not yet the merged version of PR 43]

## 2.3 Definition of Transaction Types
###### L2TFSPECDEFTTYPES

This document follows the definitions of transaction types in the [L2 Transaction Fee Specification](https://github.com/eea-oasis/L2/blob/main/workitems/l2-transaction-fees/l2-transaction-fees-v1.0-psd01.md). [Note: This is not yet the merged version of PR 43]

-------

# 3 Layer 2 Transaction Data Fee Specification
###### L2TFSPECSEC

#### **[R1]**
An L2 Transaction Data Fee MUST be indicated to be part of the Execution Fee.

#### **[R2]**
An L2 Transaction Data Fee MUST be displayed separately from the Execution Fee.

#### **[R3]**
An L2 Transaction Data Fee MUST follow the same visibility, verification and transaction requirements as the Execution Fee for all L2 roles as specified in [L2 Transaction Fee Specification](https://github.com/eea-oasis/L2/blob/main/workitems/l2-transaction-data-fee/l2-transaction-data-fee-v1.0-psd01.md).

#### **[R4]**
An L2 Transaction Data fee calculation algorithm or method MUST be published and verifiable.

#### **[R5]**
The L1 Gas Price, the L1 gas cost, and the (estimated) data size of a transaction posted to the L1 as part of an L2 Transaction Data Fee derivation MUST be displayed as part of an L2 Transaction Data Fee.

#### **[R6]**
The L1 Gas Price calculation or method used in an L2 Transaction Data Fee derivation MUST be published and verifiable.

#### **[R7]**
The utilized L1 Gas Price MUST indicate if it was derived based on a calculation or a Gas Price Data Oracle, or a combination of both.

#### **[R8]**
If there is an L2 Transaction Data Fee Refund, it MUST follow the L2 Transaction Fee specification in [R18]() and [R19]()

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

This document defines the conformance levels of an L2 Transaction Data Fee as follows:
* **Level 1:** All MUST requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.
* **Level 2:** All MUST and SHOULD requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.
* **Level 3:** All MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.

#### **[D1]** 
A claim that an L2 Transaction Data Fee conforms to this specification SHOULD describe a testing procedure carried out for each requirement to which conformance is claimed, that justifies the claim with respect to that requirement.

[[D1]](#d1) Testability: Since each of the non-conformance-target requirements in this documents is testable, so must be the totality of the requirements in this document. Therefore, conformance tests for all requirements can exist, and can be described as required in [[D1]](#d1).

#### **[R9]** 
A claim that an L2 Transaction Data Fee conforms to this specification at **Level 2** or higher MUST describe the testing procedure carried out for each requirement at **Level 2** or higher, that justifies the claim to that requirement.

[[R9]](#r9) Testability: Since each of the non-conformance-target requirements in this documents is testable, so must be the totality of the requirements in this document. Therefore, conformance tests for all requirements can exist, be described, be built and implemented and results can be recorded as required in [[R9]](#r9).


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

Kelvin Fichter \
Daniel Goldman \
Landon Gingerich\
Rami Husain\
Nikolai Prokhorenko\
Andreas Freund \
...

 
-------

# Appendix D - Revision History
###### L2TFSPECAPD

Revisions made since the initial stage of this numbered Version of this document have been tracked on [Github](https://github.com/eea-oasis/L2/tree/main/workitems/l2-transaction-data-fee/l2-transaction-data-fee-v1.0-psd01.md).

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
