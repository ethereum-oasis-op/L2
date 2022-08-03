
![OASIS Logo](http://docs.oasis-open.org/templates/OASISLogo-v2.0.jpg)
-------

# L2 Token List Version 1.0

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
Andreas Freund (a.freundhaskel@gmail.com) \
Pavel Sinelnikov (pavel.sinelnikov@outlook.com)\

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
The document describes the minimal set of business and technical prerequisites, functional and non-functional requirements for a token list that when implemented ensures that two or more Layer 1, Layer 2, or Sidechains can identify tokens from different Layer 1, Layer 2, or Sidechains.

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

**[l2-token-list-v1.0]** _Token List Specification Version 1.0_. Edited by Kelvin Fichter, Andreas Freund, Pavel Sinelnikov. XX YYYY 2022. OASIS Standard. https://github.com/eea-oasis/L2/tree/main/workitems/tokenlist/l2-token-list-v1.0-psd01.md. Latest stage: https://github.com/eea-oasis/L2/tree/main/workitems/tokenlist/l2-token-list-v1.0-psd01.md.

-------

## Notices
Copyright © OASIS Open 2022. All Rights Reserved.

Distributed under the terms of the OASIS [IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr).

For complete copyright information please see the Notices section in the Appendix.

-------

# Table of Contents
[1 Introduction](#1-introduction) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.1 Overview](#11-overview) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.2 Glossary](#12-glossary) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.3 Typographical Conventions](#13-typographical-conventions) \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.3.1	Requirement Ids](#131-requirement-ids) \
[2 Concepts and Design](#2-Concepts-and-Design) \
[3 Token List Specification](#3-token-list-specification) \
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

The work is an [Ethereum Community Project](https://github.com/ethereum/oasis-open-project), which is managed by [OASIS](https://oasis-open-projects.org/).

## 1.1 Overview

There is a significant challenge around the definition and listing of tokens on Layer 1 (L1), Layer 2 (L2), and Sidechain systems. Note that for simplicity, this document we will collectively refer to L1, L2 and Sidechains systems as chains below since the challenge described below is valid across all such systems:

* Consensus on the "canonical" token on chain B that corresponds to some token on chain A. When one wants to bridge token X from chain A to chain B, one must create some new representation of the token on chain B. It is worth noting that this problem is not limited to L2s -- every chain connected via bridges must deal with the same issue.

Related to the above challenge is the standardization around lists of bridges and their routes across different chains. This will be addressed in a separate document 

Note that both of these issues are fundamental problems for the current multi-chain world.

## 1.2 Glossary

**Blockchain:**

An open, distributed ledger that can record transactions between two parties efficiently and in a verifiable and permanent way.

**Bridge:**

Provides a connection that allows for the transfer of digital tokens or data between two different Layer 1, Layer 2 or Sidechain systems.

**Layer 1:**

A base network, such as Bitcoin, or Ethereum, and its underlying infrastructure that validates and finalizes transactions without the need of another network.

**Layer 2:**

A secondary framework or protocol that is built on top of an existing Layer 1 system in such a way that it inherits the security properties of the Layer 1 system while allowing for a higher transaction throughput that the Layer 1 system.

**Sidechain:**

A secondary blockchain connected to the main blockchain with a two-way peg.

**Two-Way Peg:**

A mechanism by which tokens are transferred between a blockchain and a sidechain and back at a fixed or otherwise deterministic exchange rate.

## 1.3 Typographical Conventions

### 1.3.1 Requirement Ids

A requirement is uniquely identified by a unique ID composed of its requirement level followed by a requirement number, as per convention **[RequirementLevelRequirementNumber]**. 
There are four requirement levels that are coded in requirement ids as per below convention: 

**[R]** - The requirement level for requirements which IDs start with the letter _R_ is to be interpreted as **MUST** as described in [RFC2119](###-RFC2119). \
**[D]** - The requirement level for requirements which IDs start with the letter _D_ is to be interpreted as **SHOULD** as described in RFC2119. \
**[O]** - The requirement level for requirements which IDs start with the letter _O_ is to be interpreted as **MAY** as described in RFC2119. 

Note that requirements are uniquely numbered in ascending order within each requirement level.

Example : It should be read that [R1] is an absolute requirement of the specification whereas [D1] is a recommendation and [O1] is truly optional.


-------

# 2 Concept and Design

For lists of canonical tokens, L2s currently maintain their own customized versions of the Uniswap token list. For example, Arbitrum maintains a [token list](https://bridge.arbitrum.io/token-list-42161.json) with various custom extensions. Optimism also maintains a [custom token list](https://raw.githubusercontent.com/ethereum-optimism/ethereum-optimism.github.io/master/optimism.tokenlist.json), but with different extensions. It should be noted that both of these custom extensions refer to the bridge that these tokens can be carried through. However, these are not the only bridges that the tokens can be carried through, which means that bridges and token lists should be separated. Also note that currently, both Optimism and Arbitrum base "canonicity" on the token name + symbol pair.

An example of an Arbitrum token entry is given below:
```
{
logoURI: "https://assets.coingecko.com/coins/images/13469/thumb/1inch-token.png?1608803028",
chainId: 42161,
address: "0x6314C31A7a1652cE482cffe247E9CB7c3f4BB9aF",
name: "1INCH Token",
symbol: "1INCH",
decimals: 18,
extensions: {
  bridgeInfo: {
    1: {
    tokenAddress: "0x111111111117dc0aa78b770fa6a738034120c302",
    originBridgeAddress: "0x09e9222e96e7b4ae2a407b98d48e330053351eee",
    destBridgeAddress: "0xa3A7B6F88361F48403514059F1F16C8E78d60EeC"
     }
   }
  }
}
```
This standard will build upon the current framework and augment it with concepts from the W3C DID Specification [[1]](#w3c-did) based on the JSON linked data model [[2]](#jsonld) such as resolvable unique resource identifiers (URIs) and JSON-LD schemas which enable easier schema verification using existing tools.

-------

# 3 Token List Specification

The schema for a canonical token list utilizes draft version 7 of https://json-schema.org for consistency purposes with the [W3C CCG](https://w3c-ccg.github.io/) effort. 

#### **[R1]**
The following data elements MUST be present in a canonical token list:
- type
- tokenListId
- name
- createdAt
- updatedAt
- versions
- tokens

Note, that the detailed definition of the data elements in [[R1]](#r1) along with descriptions and examples are given in the schema itself below.

#### **[R2]**
The tokens data element is a composite which MUST minimally contain the following data elements:
- chainId
- chainURI
- tokenId
- tokenType
- address
- tokenName
- tokenSymbol
- decimals
- createdAt
- updatedAt

Note, that the detailed definition of the data elements in [[R2]](#r2) along with descriptions and examples are given in the schema itself below.

#### **[D1]**
All other data elements of the schema SHOULD be included in a representation of a canonical token list.

#### **[CR1]>[D1]**
if the extension data elements is used, the following data elements MUST be present in the schema representation:
- rootChainId
- rootChainURI
- rootAddress

Note, that the detailed definition of the data elements in [[D1]](#d1) and [[CR1]>[D1]](#cr1d1) along with descriptions and examples are given in the schema itself below.

The schema for a canonical token list is given below as follows and can be utilized as a JSON-LD schema if a JSON-LD context file is utilized (see [[1]](#w3c-did) for a concrete example in the context of a standard):

```
{
    "$id": "https://github.com/eea-oasis/l2/schemas/CanonicalTokenList.json",
    "$schema": "https://json-schema.org/draft-07/schema#",
    "$comment": "{\"term\": \"CanonicalTokenList\", \"@id\": \"https://github.com/eea-oasis/l2#CanonicalTokenList\"}",
    "title": "CanonicalTokenList",
    "description": "Canonical Token List",
    "type": "object",
    "required": [
        "type",
        "tokenListId",
        "name",
        "createdAt",
        "updatedAt",
        "versions",
        "tokens"
        ],
        "properties": {
            "@context": {
                "type": "array"
            },
            "type": {
                "oneOf": [
                    {
                        "type": "string"
                    },
                    {
                        "type": "array"
                    }
                ],
                "examples": ["CanonicalTokenList"]
            },
            "tokenListId": {
                "$comment": "{\"term\": \"tokenListId\", \"@id\": \"https://schema.org/identifier\"}",
                "title": "tokenListId",
                "description": "A resolvable URI to the publicly accessible place where this list can be found.",
                "type": "string",
                "examples": ["https://ipfs.io/ipns/k51qzi5uqu5dkkciu33khkzbcmxtyhn376i1e83tya8kuy7z9euedzyr5nhoew"]
            },
            "name": {
                "$comment": "{\"term\": \"name\", \"@id\": \"https://schema.org/name\"}",
                "title": "name",
                "description": "Token List name",
                "type": "string",
                "examples": ["Aggregate Canonical Token List"]
            },
            "logoURI": {
                "$comment": "{\"term\": \"logoURI\", \"@id\": \"https://schema.org/identifier\"}",
                "title": "logoURI",
                "description": "URI or URL of the token list logo",
                "type": "string",
                "examples": ["https://ipfs.io/ipns/k51qzi5uqu5dh5kbbff1ucw3ksphpy3vxx4en4dbtfh90pvw4mzd8nfm5r5fnl"]
            },
            "keywords": {
                "$comment": "{\"term\": \"keywords\", \"@id\": \"https://schema.org/DefinedTerm\"}",
                "title": "keywords",
                "description": "List of key words for the token list",
                "type": "array",
                "examples": [Aggregate Token List]
            },
            "createdAt": {
                "$comment": "{\"term\": \"createdAt\", \"@id\": \"https://schema.org/datePublished\"}",
                "title": "createdAt",
                "description": "Date and time token list was created",
                "type": "string",
                "examples": ["2022-05-08"]
            },
            "updatedAt": {
                "$comment": "{\"term\": \"updatedAt\", \"@id\": \"https://schema.org/dateModified\"}",
                "title": "updatedAt",
                "description": "Date and time token list was updated",
                "type": "string",
                 "examples": ["2022-05-09"]
            },
            "versions": {
                "$comment": "{\"term\": \"versions\", \"@id\": \"https://schema.org/version\"}",
                "title": "versions",
                "description": "Versions of the canonical token list",
                "type": "array",
                 "items": {
                    "type":"object",
                    "required":[
                        "major",
                        "minor",
                        "patch"
                    ],
                    "properties": {
                        "major": {
                            "$comment": "{\"term\": \"major\", \"@id\": \"https://schema.org/Number\"}",
                            "title": "major",
                            "description": "Major Version Number of the Token List",
                            "type": "integer",
                             "examples": [1]
                        },
                        "minor": {
                            "$comment": "{\"term\": \"minor\", \"@id\": \"https://schema.org/Number\"}",
                            "title": "minor",
                            "description": "Minor Version Number of the Token List",
                            "type": "integer",
                             "examples": [1]
                        },
                        "patch": {
                            "$comment": "{\"term\": \"patch\", \"@id\": \"https://schema.org/Number\"}",
                            "title": "patch",
                            "description": "Patch Number of the Token List",
                            "type": "integer",
                             "examples": [1]
                        },
                    }
                }
            },
            "tokens": {
                "title": "Listed Token Entry",
                "description": "Listed Token Entry",
                "type": "array",
                 "items": {
                    "type":"object",
                    "required": [
                        "chainId",
                        "chainURI",
                        "tokenId",
                        "tokenType",
                        "address",
                        "tokenName",
                        "tokenSymbol",
                        "decimals",
                        "createdAt",
                        "updatedAt"
                    ],
                    "properties": {
                        "chainId": {
                            "$comment": "{\"term\": \"chainId\", \"@id\": \"https://schema.org/identifier\"}",
                            "title": "chainId",
                            "description": "The typically used number identifier for the chain on which the token was issued.",
                            "type": "number",
                            "examples": [137]
                        },
                        "chainURI": {
                            "$comment": "{\"term\": \"chainURI\", \"@id\": \"https://schema.org/identifier\"}",
                            "title": "chainURI",
                            "description": "A resolvable URI to the genesis block of the chain on which the token was issued.",
                            "type": "string"
                             "examples": ["https://polygonscan.com/block/0"]
                        },
                        "genesisBlockHash": {
                            "$comment": "{\"term\": \"genesisBlockHash\", \"@id\": \"https://schema.org/sha256\"}",
                            "title": "genesisBlockHash",
                            "description": "The hash of the genesis block of the chain on which the token was issued.",
                            "type": "string",
                            "examples": ["0xa9c28ce2141b56c474f1dc504bee9b01eb1bd7d1a507580d5519d4437a97de1b"]
                        },
                        "tokenIssuerId": {
                            "$comment": "{\"term\": \"tokenIssuerId\", \"@id\": \"https://schema.org/identifier\"}",
                            "title": "tokenIssuerId",
                            "description": "A resolvable URI identifying the token issuer.",
                            "type": "string",
                            "examples": ["0xa9c28ce2141b56c474f1dc504bee9b01eb1bd7d1a507580d5519d4437a97de1b"]
                        },
                        "tokenIssuerName": {
                            "$comment": "{\"term\": \"tokenIssuerName\", \"@id\": \"https://schema.org/name\"}",
                            "title": "tokenIssuerName",
                            "description": "The name oof the token issuer.",
                            "type": "string"
                            "examples": ["Matic"]
                        },
                        "tokenId": {
                            "$comment": "{\"term\": \"tokenId\", \"@id\": \"https://schema.org/identifier\"}",
                            "title": "tokenId",
                            "description": "A resolvable URI to a CanonicalTokenList entry of the token.",
                            "type": "string",
                            "example": ["https://polygonscan.com/address/0x0000000000000000000000000000000000001010"]
                        },
                        "tokenType": {
                            "$comment": "{\"term\": \"tokenType\", \"@id\": \https://schema.org/StructuredValue\"}",
                            "title": "tokenType",
                            "description": "Describes the type of token.",
                            "type": "array"
                            "examples"[["fungible","transferable"]]
                        },
                        "tokenDesc": {
                            "$comment": "{\"term\": \"tokenDesc\", \"@id\": \"https://schema.org/description\"}",
                            "title": "tokenDesc",
                            "description": "Brief description of the token and its functionality.",
                            "type": "string",
                            "examples": ["Protocol Token for the Matic Network"]
                        },
                        "standard": {
                            "$comment": "{\"term\": \"standard\", \"@id\": \"https://schema.org/citation\"}",
                            "title": "standard",
                            "description": "Describes which standard the token adheres to.",
                            "type": "string",
                            "examples": ["ERC20"]
                        },
                        "address": {
                            "$comment": "{\"term\": \"address\", \"@id\": \"https://schema.org/identifier\"}",
                            "title": "address",
                            "description": "Address of the token smart contract.",
                            "type": "string",
                            "examples": ["0x0000000000000000000000000000000000001010"]
                        },
                        "addressType": {
                            "$comment": "{\"term\": \"address\", \"@id\": \"https://schema.org/Intangible\"}",
                            "title": "addressType",
                            "description": "AddressType of the token smart contract.",
                            "type": "string",
                            "examples": ["MaticNameSpace"]
                        },
                        "addressAlg": {
                            "$comment": "{\"term\": \"addressAlg\", \"@id\": \"https://schema.org/algorithm\"}",
                            "title": "addressAlg",
                            "description": "Algorithm used to create the address e.g. CREATE2.",
                            "type": "string",
                            "examples": ["CREATE2"]
                        },
                        "tokenName": {
                            "$comment": "{\"term\": \"tokenName\", \"@id\": \"https://schema.org/name\"}",
                            "title": "tokenName",
                            "description": "Token name.",
                            "type": "string",
                            "examples": ["Matic"]
                        },
                        "tokenSymbol": {
                            "$comment": "{\"term\": \"tokenSymbol\", \"@id\": \"https://schema.org/currency\"}",
                            "title": "tokenSymbol",
                            "description": "Token symbol e.g. ETH.",
                            "type": "string",
                            "examples": ["MATIC"]
                        },
                        "decimals": {
                            "$comment": "{\"term\": \"decimals\", \"@id\": \"https://schema.org/Number\"}",
                            "title": "decimals",
                            "description": "Allowed number of decimals for the listed token.",
                            "type": "integer",
                            "examples": [18]
                        },
                        "tokenLogoURI": {
                            "$comment": "{\"term\": \"tokenLogoURI\", \"@id\": \"https://schema.org/identifier\"}",
                            "title": "tokenLogoURI",
                            "description": "URI or URL of the token logo.",
                            "type": "string"
                            "examples": ["https://polygonscan.com/token/images/matic_32.png"]
                        },
                        "createdAt": {
                            "$comment": "{\"term\": \"createdAt\", \"@id\": \"https://schema.org/datePublished\"}",
                            "title": "createdAt",
                            "description": "Date and time token was created",
                            "type": "string",
                            "examples": ["2020-05-31"]
                        },
                        "updatedAt": {
                            "$comment": "{\"term\": \"updatedAt\", \"@id\": \"https://schema.org/dateModified\"}",
                            "title": "updatedAt",
                            "description": "Date and time token was updated",
                            "type": "string"
                            "examples": ["2020-05-31"]
                        },
                        "extensions": {
                            "title": "extensions",
                            "description": "Extension to the token list entry to specify an origin chain if the token entry refers to another chain other than the origin chain of the token",
                            "type": "array",
                            "items": {
                                "type":"object",
                                "required": [
                                    "rootChainId",
                                    "rootChainURI",
                                    "rootAddress",
                                ],
                                "properties": {
                                    "rootChainId": {
                                        "$comment": "{\"term\": \"rootChainId\", \"@id\": \"https://schema.org/identifier\"}",
                                        "title": "rootChainId",
                                        "description": "The typically used number identifier for the root chain on which the token was originally issued.",
                                        "type": "number",
                                        "examples": [137]
                                    },
                                    "rootChainURI": {
                                        "$comment": "{\"term\": \"rootChainURI\", \"@id\": \"https://schema.org/identifier\"}",
                                        "title": "rootChainURI",
                                        "description": "A resolvable URI to the genesis block of the root chain on which the token was originally issued.",
                                        "type": "string",
                                        "examples": ["https://polygonscan.com/block/0"]
                                    },
                                    "rootAddress": {
                                        "$comment": "{\"term\": \"rootAddress\", \"@id\": \"https://schema.org/identifier\"}",
                                        "title": "rootAddress",
                                        "description": "Root address of the token smart contract.",
                                        "type": "string",
                                        "examples": ["0x0000000000000000000000000000000000001010"]
                                    }
                                }
                            }
                        }
                    }
                }
            }
        },
    "additionalProperties": false,
}
```

-------
# 4 Conformance

This section describes the conformance clauses and tests required to achieve an implementation that is provably conformant with the requirements in this document.

## 4.1 Conformance Targets

This document does not yet define a standardized set of test-fixtures with test inputs for all MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements. 

A standardized set of test-fixtures with test inputs for all MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements is intended to be published with the next version of the standard.

## 4.2 Conformance Levels

This section specifies the conformance levels of this standard. The conformance levels offer implementers several levels of conformance. These can be used to establish competitive differentiation.

This document defines the conformance levels of a BPI as follows:
* **Level 1:** All MUST requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.
* **Level 2:** All MUST and SHOULD requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.
* **Level 3:** All MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.

#### **[D2]** 
A claim that a canonical token list implementation conforms to this specification SHOULD describe the testing procedure used to justify the claim.

#### **[R3]** 
A claim that a canonical token list conforms to this specification at **level 2** or higher MUST describe the testing procedure used to justify the claim.


-------

# Appendix A - References

This appendix contains the normative and non-normative references that are used in this document. 

While any hyperlinks included in this appendix were valid at the time of publication, OASIS cannot guarantee their long-term validity.

## A.1 Normative References

The following documents are referenced in such a way that some or all of their content constitute requirements of this document.

#### **[RFC2119]**
 S. Bradner, Key words for use in RFCs to Indicate Requirement Levels, http://www.ietf.org/rfc/rfc2119.txt, IETF RFC 2119, March 1997.

#### **[JSONLD]** 
JSON-LD 1.1, M. Sporny, D. Longley, G. Kellogg, M. Lanthaler, Pierre-Antoine Champin, N. Lindström, W3C Recommendation, July 2020 , https://www.w3.org/TR/2020/REC-json-ld11-20200716/. Latest version available at https://www.w3.org/TR/json-ld11/. 


## A.2 Non-Normative References

#### **[W3C-DID]** 
Decentralized Identifiers (DIDs) v1.0, M. Sporny, D. Longley, M. Sabadello, D. Reed, O. Steele, C. Allen, W3C Proposed Recommendation, August 2021, https://www.w3.org/TR/2021/PR-did-core-20210803/. Latest version available at https://www.w3.org/TR/did-core/.


# Appendix B - Security Considerations

There are no additional security requirements.

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

Tas Dienes \
Kelvin Fichter \
Andreas Freund \
Daniel Shaw \
Pavel Sinelnikov \
**[please add names here]**
...

 
-------

# Appendix D - Revision History

Revisions made since the initial stage of this numbered Version of this document have been tracked on [Github](https://github.com/eea-oasis/L2/tree/main/workitems/tokenlist/l2-token-list-v1.0-psd01.md).

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
