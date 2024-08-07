# Layer 2 Transaction Status Specification Version 1.0
###### L2TSSPEC

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
[Layer 2 Working Group](https://github.com/ethereum-oasis-op/L2), an initiative of Ethereum Community Projects managed by OASIS.
#### Project Chair:
Andreas Freund (a.freundhaskel@gmail.com), [Ethereum Foundation](https://ethereum.org)  

#### Editors:
Kelvin Fichter (kelvin@optimism.io)\
Andreas Freund (a.freundhaskel@gmail.com)\
Landon Gengrich (lg@matterlabs.dev)\

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

This specification utilizes the definitions and requirements of the
L2 Transaction Fee API Specification [TODO: Add Link once PR is merged!]


#### Abstract:
The document describes the minimal set of technical prerequisites, functional and non-functional requirements for Layer 2 Transaction Statuses that when implemented ensures that Layer 2 solutions are transparently and consistently displaying standardized L2 transaction statuses to end user, and developers such as wallet providers and L2 client teams.

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

**[l2-transaction-statuses-v1.0]** _Layer 2 Transaction Statuses Version 1.0_. Edited by Kelvin Fichter, Andreas Freund, Landon Gengrich. August 2024. OASIS Standard. https://github.com/ethereum-oasis-op/L2/tree/main/workitems/l2-transaction-statuses/l2-transaction-statuses-v1.0-psd01.md. Latest stage: https://github.com/ethereum-oasis-op/L2/tree/main/workitems/l2-transaction-statuses/l2-transaction-statuses-v1.0-psd01.md.

-------

## Notices
Copyright © OASIS Open 2024. All Rights Reserved.

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
[3 Layer 2 Transaction Statuses Specification](#3-layer-2-transaction-statuses-specification) \
&nbsp;&nbsp;&nbsp;&nbsp;[3.1 Layer 2 Transaction Statuses Definitions](#31-layer-2-transaction-statuses-definitions) \
&nbsp;&nbsp;&nbsp;&nbsp;[3.2 Layer 2 Transaction Statuses Requirements](#32-layer-2-transaction-statuses-requirements) \
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
###### L2TSSPECINTRO

The L2 WG is an open-source initiative with a scope to
- Identify and document the most relevant use cases and business requirements for Layer 2 and other Blockchain Scalability solutions for EVM compatible public blockchains
- Define a technical standard with identification and differentiation of classes of scalability solutions as required that meet both ecosystem and enterprise requirements, with a particular focus on interoperability between Layer 2 solutions for EVM compatible public blockchains
- For EVM compatible public blockchains, identify, document, and devise solution approaches for Layer 2 Blockchain scalability solution specific challenges such as MEV, block (gas) limits, TVL concentration, etc.
- Identify and document characteristics of Layer 2 Blockchain environments for EVM compatible public blockchains that will be key in addressing mainstream and enterprise adoption.

The work is an Ethereum Community Project which is managed by [OASIS](https://oasis-open-projects.org/).

## 1.1 Overview
###### L2TSSPECOVERV

Several recent discussions in the Ethereum Ecosystem, in particular in the RollCall Group managing [RIPs](https://github.com/ethereum/RIPs), showed that a lack of standards around the processing status of an L2 transaction is confusing not only for users and developers working on block explorers, wallets, smart contracts, or chain analytics but also for L2 client teams themselves trying to understand what different statuses of different L2 clients mean, and what trust assumptions have been made for each status. Besides confusion, there are real security risks, especially for L2 bridges based on the processing status of an L2 transaction (finalized on an L2 but not on an L1 vs finalized on an L2 and on an L1).

This topic of discussion also arose in the [L2 Standards WG](https://github.com/ethereum-oasis-op/L2) when discussing the [L2 Transaction Fee API specification](**TODO: add Github link once PR is merged**).

This standard is addressing confusion around L2 Transaction Statuses, and defines a set of universal L2 Transaction Statuses, with status codes, and their trust assumptions, for the lifecycle of an L2 Transaction.

Note, that this standard does not prevent additional, non-duplicative L2 transaction statuses to be defined based on the details of an L2 client. For example, an Optimistic L2 has additional intermediate transaction statuses having to do with the challenge period compared to Zero-Knowledge based L2s.


## 1.2 Glossary
###### L2TSSPECGLOS

**Developer:**

An individual writing computer code for software applications that operate on a Layer 1, Layer 2 or Sidechain.

**Layer 1:**

A base network, such as Bitcoin, or Ethereum, and its underlying infrastructure that validates and finalizes transactions without the need of another network.

**Layer 2:**

A secondary framework or protocol that is built on top of an existing Layer 1 system in such a way that it inherits the security properties of the Layer 1 system while allowing for a higher transaction throughput than the Layer 1 system.

**Transaction:**

A digitally signed message sent from a Layer 2 account that contains instructions and data that result in a Layer 2 state transition. 

**Transaction Status:**

The current stage of a Layer 2 transaction in its lifecycle from initial submission on the L2 to finalization on the L1.

Note that the lifecycle stages can vary between different L2 types.


## 1.3 Typographical Conventions
###### L2TSSPECTYPO

### 1.3.1 Requirement Ids
###### L2TSSPECREQIDS

A requirement is uniquely identified by a unique ID composed of its requirement level followed by a requirement number, as per convention **[RequirementLevelRequirementNumber]**. 
There are four requirement levels that are coded in requirement ids as per below convention: 

**[R]** - The requirement level for requirements which IDs start with the letter _R_ is to be interpreted as **MUST** as described in [RFC2119](#rfc2119). \
**[D]** - The requirement level for requirements which IDs start with the letter _D_ is to be interpreted as **SHOULD** as described in [RFC2119](#rfc2119). \
**[O]** - The requirement level for requirements which IDs start with the letter _O_ is to be interpreted as **MAY** as described in [RFC2119](#rfc2119). 

Note that requirements are uniquely numbered in ascending order within each requirement level.

Example : It should be read that [R1] is an absolute requirement of the specification whereas [D1] is a recommendation and [O1] is truly optional.

-------

# 2 Concepts and Design
###### L2TSSPECCONCEPT

The L2 Transaction Statuses specification is define an L2 Transaction Status as having:

- A common name denoted by an alpha numeric string
- A status code denoted by an alpha numeric string similar to HTTP status codes
- A Trust Assumption that specifies the security assumptions made and subsequent security guarantees of an L2 Transaction Status

# 3 Layer 2 Transaction Statuses Specification
###### L2TSSPECSEC

The specification of the L2 Transaction Status Specification has two sections:

- Layer 2 Transaction Statuses Definitions
- Layer 2 Transaction Statuses Requirements

## 3.1 Layer 2 Transaction Statuses Definitions
###### L2TFSPECTFDATASCHEMA

The minimal set of transaction statuses is defined as follows:

1. **L2 Pending**
    - **Definition**: An L2 transaction submitted to an L2, and waiting to be processed by a sequencer
    - **Trust Assumption**: No inclusion guarantee on the L2
    - **Transaction Status Code**: `L2TS00100`
2. **L2 Replaced**
    - **Definition**: An L2 transaction that was "Pending" was replaced by another L2 transaction.
    - **Trust Assumption**: Same as L2 Pending
    - **Transaction Status Code**: `L2TS00200`
3. **L2 Dropped**
    - **Definition**: An L2 transaction that was removed from the L2 processing queue
    - **Trust Assumption**: NA
    - **Transaction Status Code**: `L2TS00300`
4. **L2 Confirmed** 
    - **Definition**: An L2 transaction processed by a sequencer and assigned an order in a proposed L2 block by the sequencer by applying an L2 client-specific L2 transaction ordering protocol
    - **Trust Assumption**: The L2 transaction order guarantee is based on the security guarantee of the ordering protocol. Inclusion in finalized L2 and L1 blocks is not guaranteed
    - **Transaction Status Code**: `L2TS00400`
5. **L2 Included, L1 Pending**
    - **Definition**: An L2 transaction included in an L2 block but not yet submitted to the L1 
    - **Trust Assumption**: The L2 inclusion guarantee is dependent on the submission guarantee of the L2 block to the L1 and L1 Finalization
    - **Transaction Status Code**: `L2TS00500`
6. **L2 Included, L1 Included**
    - **Definition**: An L2 transaction included in an L2 block submitted to the L1 
    - **Trust Assumption**: The L2 inclusion guarantee is dependent on L1 finalization
    - **Transaction Status Code**: `L2TS00600`
7. **L2 Finalized, L1 Finalized** 
    - **Definition**: An L2 transaction included in a L2 block that has been included in a finalized L1 transaction. 
    - **Trust Assumption**: The L2 transaction finalization guarantee is equivalent to an L1 transaction finalization guarantee in a finalized L1 block.
    - **Transaction Status Code**: `L2TS00600`


## 3.2 Layer 2 Transaction Fee Transparency Requirements
###### L2TSSPECTFAPIREQS

#### **[R1]** 

The Transaction Status Code MUST be an alphanumeric string of no more than 32 characters with the four leading characters being `L2TS`.

[[R1]](#r1) Testability: 

**Test Preconditions:**
...

**Test Steps:**
...

**Passing Criteria:**
...


# 4 Conformance

###### L2TSSPECCONF

This section describes the conformance clauses and tests required to achieve an implementation that is provably conformant with the requirements in this document.

## 4.1 Conformance Targets

###### L2TSSPECCONFT

This document does not yet define a standardized set of test-fixtures with test inputs for all MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements. 

A standardized set of test-fixtures with test inputs for all MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements is intended to be published with the next version of the standard.

## 4.2 Conformance Levels
###### L2TSSPECCONFL

This section specifies the conformance levels of this standard. The conformance levels offer implementers several levels of conformance. These can be used to establish competitive differentiation.

This document defines the conformance levels of L2 Transaction Fee API as follows:
* **Level 1:** All MUST requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.
* **Level 2:** All MUST and SHOULD requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.
* **Level 3:** All MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.

#### **[D1]** 
A claim that an L2 Transaction Fee API conforms to this specification SHOULD describe a testing procedure carried out for each requirement to which conformance is claimed, that justifies the claim with respect to that requirement.

[[D1]](#d1) Testability: Since each of the conformance target requirements in this documents is testable, so must be the totality of the requirements in this document. Therefore, conformance tests for all requirements can exist, and can be described as required in [[D1]](#d1).

#### **[R2]** 
A claim that an L2 Transaction Fee API conforms to this specification at **Level 2** or higher MUST describe the testing procedure carried out for each requirement at **Level 2** or higher, that justifies the claim to that requirement.

[[R2]](#r2) Testability: Since each of the non-conformance-target requirements in this documents is testable, so must be the totality of the requirements in this document. Therefore, conformance tests for all requirements can exist, be described, be built and implemented and results can be recorded as required in [[R6]](#r6).

-------

# Appendix A - References
###### L2TSSPECAPA

This appendix contains the normative and non-normative references that are used in this document. 

While any hyperlinks included in this appendix were valid at the time of publication, OASIS cannot guarantee their long-term validity.

## A.1 Normative References
###### L2TSSPECAPREFNORM

The following documents are referenced in such a way that some or all of their content constitute requirements of this document.

#### **[RFC2119]**
 S. Bradner, Key words for use in RFCs to Indicate Requirement Levels, http://www.ietf.org/rfc/rfc2119.txt, IETF RFC 2119, March 1997.


## A.2 Non-Normative References
###### L2TSSPECAPREFNONNORM

#### **[W3C-String-Meta]**

Strings on the Web: Language and Direction Metadata, R. Ishida, A. Phillips, August 2022,
https://www.w3.org/TR/string-meta/


# Appendix B - Security Considerations
###### L2TSSPECAPBSEC

There are no additional security requirements.

## B.1 Data Privacy
###### L2TSSPECAPBDP

The standard does not set any requirements for compliance to jurisdiction legislation/regulations. It is the responsibility of the implementer to comply with applicable data privacy laws.

## B.2 Production Readiness 
###### L2TSSPECAPBPR

The standard does not set any requirements for the use of specific applications/tools/libraries etc. The implementer should perform due diligence when selecting specific applications/tools/libraries.

## B.3 Internationalization and Localization Reference
###### L2TSSPECAPBINT

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

Landon Gengrich\
Kelvin Fichter \
Andreas Freund \
...

 
-------

# Appendix D - Revision History
###### L2TFSPECAPD

Revisions made since the initial stage of this numbered Version of this document have been tracked on [Github](https://github.com/eea-oasis/L2/tree/main/workitems/l2-transaction-statuses).

-------

# Appendix E - Notices
###### L2TSSPECAPBE

Copyright © OASIS Open 2024. All Rights Reserved.

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