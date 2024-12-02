# Layer 2 Transaction Fee API Specification Version 1.0
###### L2TFAPISPEC

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
[Layer 2 Working Group](https://github.com/eea-oasis/L2), an initiative of Ethereum Community Projects managed by OASIS.
#### Project Chair:
Dan Shaw (daniel.shaw@ethereum.org), [Ethereum Foundation](https://ethereum.org), Andreas Freund (a.freundhaskel@gmail.com), [Ethereum Foundation](https://ethereum.org)  

#### Editors:
Kelvin Fichter (kelvin@optimism.io)\
Andreas Freund (a.freundhaskel@gmail.com)\
Derek Lee (dlee@offchainlabs.com)\
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
[L2 Transaction Fee Specification](https://github.com/eea-oasis/L2/blob/main/workitems/l2-transaction-fees/l2-transaction-fees-v1.0-psd01.md).


#### Abstract:
The document describes the minimal set of technical prerequisites, functional and non-functional requirements for a Layer 2 Transaction Fee API that when implemented ensures that Layer 2 solutions are transparently and consistently displaying standardized transaction fees to consumers of those fees such as wallets, data oracles, developers, and end users in a standardized manner.

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

**[l2-transaction-fees-api-v1.0]** _Layer 2 Transaction Fee API Version 1.0_. Edited by Kelvin Fichter, Andreas Freund, Daniel Goldman, Landon Gengrich. March 2024. OASIS Standard. https://github.com/eea-oasis/L2/tree/main/workitems/l2-transaction-fee-API/l2transactionfeeapispec-v1.0.md. Latest stage: https://github.com/eea-oasis/L2/tree/main/workitems/l2-transaction-fee-API/l2transactionfeeapispec-v1.0.md.

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
[3 Layer 2 Transaction Fee API Specification](#3-layer-2-transaction-fees-specification) \
&nbsp;&nbsp;&nbsp;&nbsp;[3.1 Layer 2 Transaction Fee API Data Schema ](#31-layer-2-transaction-fee-api-data-schema) \
&nbsp;&nbsp;&nbsp;&nbsp;[3.2 Layer 2 Transaction Fee Transparency Requirements](#32-layer-2-transaction-fee-transparency-requirements) \
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

The work is an Ethereum Community Project which is managed by [OASIS](https://oasis-open-projects.org/).

## 1.1 Overview
###### L2TFSPECOVERV

Layer 2 (L2) Transaction Fees are a crucial element of financing the operations of L2 platforms apart from rewards given to participants for providing economic security guarantees such as validators in consensus protocols. Yet how these transaction fees are derived, to whom they are paid, how and where they are displayed to any of the participants in L2 platforms varies greatly between L2 platforms. 

Given the above, the need for transparency in a open ecosystem to build trust, and the evolving legal and regulatory landscape around fee transparency and what type of fees can be charged, this document sets out to define an Application Programmable Interface (API) based on existing [L2 Transaction Fees Specification](https://github.com/eea-oasis/L2/tree/main/workitems/l2-transaction-fees/l2-transaction-fees-v1.0-psd01.md) to allow ecosystem participants .

Note, that APIs for fees associated with asset and data bridges between L2 platforms as well as between L2 platforms and centralized exchanges are beyond the scope of this document. Further note, while this API is in scope for an entity submitting EIP-2771-type transactions, or EIP-4337-type transactions to a Layer 2, often called a Relayer, the API is out of scope for the entity submitting EIP-2771-type or EIP-4337-type transaction requests to a Relayer.Furthermore, L2 client-specific fees are also out of scope


## 1.2 Glossary
###### L2TFSPECGLOS

**Account:**

A unit that is minimally comprised of a unique account identifier, a deterministic ordering parameter, also referred to as a nonce, a balance of a Layer 1, Layer 2 or Sidechain unit of exchange, also referred to as a protocol token. Changes to an account are controlled by a unique cryptographic public and private key pair. There are typically additional account elements referring to instructions and data associated to the account that determine account changes. 

**Blob Gas:**

A separate L1 gas fee and fee market, separate from the L1 gas fee for non-blob transactions introduced with EIP-1559  It is specifically designed for transactions that include blobs of data. These blobs are chunks of data introduced with the Ethereum Dencun upgrade under EIP-4844 to improve scalability, particularly for Layer 2 solutions.

**Blockchain:**

An open, distributed ledger that can record transactions between two parties efficiently and in a verifiable and permanent way.

**Developer:**

An individual writing computer code for software applications that operate on a Layer 1, Layer 2 or Sidechain.

**Data Fee:**

A fee to be paid by the Transaction Originator or Transaction Sender sufficient to cover the Layer 1 transaction fees, and any other transaction data fees related to non-Layer 1 data storage, and excluding a Priority Fee and an Execution Fee.

**Execution Fee:**

A fee to be paid by the Transaction Originator or Transaction Sender sufficient to cover the Layer 2 transaction fees excluding a Priority Fee and a Data Fee.

**Fee Price:**

A Layer 2 gas price or a price of a Layer 2 gas equivalent unit of compute and storage consumption.

Note that a gas price or a price of a Layer 2 gas equivalent unit of compute and storage consumption is typically variable and changes with the level of usage of a Layer 2 network. Note, that a gas price is expressed in Giga Wei (GWEI) for EVM-compatible networks, where Wei represents the smallest unit of gas; 1 Wei = 10<sup>-18</sup> Eth in Ethereum's native token.

**Gas:**

Refers to the unit that measures the amount of computational and storage effort required to execute specific operations on an EVM-compatible network.


**Layer 1:**

A base network, such as Bitcoin, or Ethereum, and its underlying infrastructure that validates and finalizes transactions without the need of another network.

**Layer 2:**

A secondary framework or protocol that is built on top of an existing Layer 1 system in such a way that it inherits the security properties of the Layer 1 system while allowing for a higher transaction throughput than the Layer 1 system.

**Priority Fee:**

Paid by the Transaction Originator or Transaction Sender to obtain a desired slot for its transaction in a new block.

Note that the exact position of a transaction in a new block may be determined by factors such as time-stamp, or minimization of Maximal Extractable Value (MEV) of a block in addition to a Priority Fee.

**Relayer:**

An entity receiving EIP-2771-type and EIP-4337-type transaction requests, bundling them into one or more L2 transactions, and submitting those transaction to an L2 on behalf of the requesters.

Note, that Relayers are typically organized into their own Relayer network.

**Transaction:**

A digitally signed message sent from a Layer 2 account that contains instructions and data that result in a Layer 2 state transition. 

**Transaction Fee:**

The fee in a Layer 2 network or protocol token to be paid by a transaction Originator or Transaction Sender comprised of the sum of an Execution Fee, a Data Fee and a Priority Fee.

**Transaction Status:**

The current stage of a Layer 2 transaction in its lifecycle from initial submission on the L2 to finalization on the L1.

Note that the lifecycle stages can vary between different L2 types.


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

The L2 Transaction Fee API specification is written in OpenAPI 3.0.0 format. It describes two endpoints related to Layer 2 (L2) transaction fees in a L2 network.

1. **POST /l2transactionfeeestimate**: This endpoint is used to provide an estimated L2 transaction fee based on a proposed L2 transaction. The request body requires a JSON object with properties such as `transactionCall`, `transactionPriority`, `currency`, and `chainId`. The `transactionCall` object includes details about the transaction such as the sender's address (`from`), the recipient's address (`to`), the gas provided for the transaction execution (`gas`), the gas price (`gasPrice`), the value sent with the transaction (`value`), and the input data (`input`). The response includes the estimated transaction fee broken down into `executionFee`, `dataFee`, `priorityFee`, and the total fee (`totalL2TranactionFee`).

2. **GET /l2transactionfee**: This endpoint retrieves the L2 transaction fee of a submitted transaction based on a transaction hash. The request body requires a JSON object with properties such as `transactionHash`, `currency`, and `chainId`. The response includes the transaction status (`transactionStatus`), the total transaction fee (`totalL2TranactionFee`), and the breakdown of the fee into `executionFee`, `dataFee`, and `priorityFee`.

Both endpoints return a typical HTTP `200` status code for successful requests, with the response body containing detailed information about the transaction fees. And typical HTTP error codes.

The fees are broken down into `executionFee` (the cost of executing the transaction), `dataFee` (the cost of the data to be anchored on an L1 and, possibly, Data Availability solution), and `priorityFee` (the cost based on the priority of the transaction). Each fee is further broken down into the value in the requested currency (`value_currency`), the value in gas units (`value_gas`), and the gas price (`l2GasPrice` for execution fee, `l1GasPrice` for data fee, and `l2PriorityGasPrice` for priority fee). The method, description, and source of the gas price derivation are also included.

# 3 Layer 2 Transaction Fee API Specification
###### L2TFSPECSEC

The specification of the L2 Transaction Fee API has two sections:

- Layer 2 Transaction Fee API Data Schema
- Layer 2 Transaction Fee Transparency Requirements

## 3.1 Layer 2 Transaction Fee API Data Schema
###### L2TFSPECTFDATASCHEMA

The [OpenAPI3.0.0 Data Schema](#open-api-3) for the L2 Transaction Fee APIs is given as follows:

```
openapi: 3.0.0
info:
  title: Layer 2 Transaction Fees APIs
  version: 1.0.0
paths:
  /l2transactionfeeestimate:
    post:
      summary: Calculate an estimated L2 transaction fee based on a proposed transaction
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              required:
                - transactionCall
                - chainId
              properties:
                transactionCall:
                  type: object
                  required:
                    - from
                    - input
                    - value
                  properties:
                    from:
                      type: string
                      description: The address the transaction is sent from.
                      example: "0x1234567890abcdef1234567890abcdef12345678"
                    to:
                      type: string
                      description: The address the transaction is directed to.
                      example: "0x9876543210fedcba9876543210fedcba98765432"
                    gas:
                      type: integer
                      description: The gas provided for the transaction execution.
                      example: 21000
                    gasPrice:
                      type: integer
                      description: The gasPrice used for each paid gas.
                      example: 1000000000
                    value:
                      type: integer
                      description: The value sent with this transaction.
                      example: 1000000000000000000
                    input:
                      type: string
                      description: Hash of the method signature (1st 4 bytes) and encoded parameters as a byte array. See example of setAddress(0xabcdef1234567890abcdef1234567890abcdef12)
                      example: "e30081a0000000000000000000000000abcdef1234567890abcdef1234567890abcdef12"
                transactionPriority:
                  type: string
                  enum: [high, medium, low]
                  default: Null
                  description: The priority of the transaction. Defaults to 'Null' if not specified, and allows the application provider to return an array of priority fees based on L2 specific definition of a priority such as high, medium, or low.
                  example: "high"
                currency:
                  type: string
                  enum: [GigaWei, ETH, Native Token, Fiat Currency]
                  default: Null
                  description: The currency in which the fees should be expressed. Defaults to 'Null' if not specified setting the currency to the gas unit of account in the respective L2 such as GigaWei.
                  example: "ETH"
                chainId:
                  type: number
                  description: The unique identifier of the blockchain network where the transaction is intended to be processed.
                  example: 1
      responses:
        '200':
          description: Transaction fee calculated successfully
          content:
            application/json:
              schema:
                type: object
                required:
                  - executionFee
                  - dataFee
                  - priorityFee
                  - totalL2TransactionFee
                properties:
                  totalL2TransactionFee:
                    type: object
                    required:
                      - value_currency
                      - value_gas
                    properties:
                      value_currency:
                        type: number
                        example: 0.00054
                      value_gas:
                        type: number
                        example: 27000
                    description: Total estimated transaction fee based on the submitted transaction, as the sum of execution, data and priority fee expressed in the requested currency and estimated gas units.
                  executionFee:
                    type: object
                    required:
                      - value_currency
                      - value_gas
                      - l2GasPrice
                    properties:
                      value_currency:
                        type: number
                        example: 0.00042
                      value_gas:
                        type: number
                        example: 21000
                      l2GasPrice:
                        type: number
                        example: 20
                        description: The Layer 2 gas price, expressed in GigaWei. 
                      l2GasPriceDerivationMethod:
                        type: string
                        description: The method used to derive the L2 gas price.
                      l2GasPriceDerivationMethodDescription:
                        type: string
                        description: Description of the L2 gas price derivation method.
                      l2GasPriceDerivationMethodSource:
                        type: string
                        format: uri
                        description: The source of information for the L2 gas price derivation method. 
                    description: Estimated execution fee based on the transaction, expressed in the requested currency and estimated gas units.
                  dataFee:
                    type: object
                    required:
                      - value_currency
                      - value_gas
                      - l1GasPrice
                    properties:
                      value_currency:
                        type: number
                        example: 0.00002
                      value_gas:
                        type: number
                        example: 1000
                    l1GasPrice:
                      type: number
                      example: 100
                      description: The Layer 1 gas price, expressed in GigaWei. The gas price is either the gas price for L1 data or for L1 blob data, whichever price is cheaper.
                    l1GasPriceDerivationMethod:
                        type: string
                        description: The method used to derive the L1 gas price.
                    l1GasPriceDerivationMethodDescription:
                      type: string
                      description: Description of the L1 gas price derivation method.
                    l1GasPriceDerivationMethodSource:
                      type: string
                      format: uri
                      description: The source of information for the L1 gas price derivation method.  
                    description: Estimated data fee based on the transaction, expressed in the requested currency and estimated gas units.
                  priorityFee:
                    type: array
                    items:
                      type: object
                      required:
                        - priority
                        - value_currency
                        - value_gas
                        - l2PriorityGasPrice
                      properties:
                        priority:
                          type: string
                          example: high
                        value_currency:
                          type: number
                          example: 0.0001
                        value_gas:
                          type: number
                          example: 5000
                        l2PriorityGasPrice:
                          type: number
                          example: 20
                          description: The Layer 2 gas price, expressed in GigaWei.
                        l2PriorityGasPriceDerivationMethod:
                          type: string
                          description: The method used to derive the L2 priority gas price.
                        l2PriorityGasPriceDerivationMethodDescription:
                          type: string
                          description: Description of the L2 priority gas price derivation method.
                        l2PriorityGasPriceDerivationMethodSource:
                          type: string
                          format: uri
                          description: The source of information for the L2 priority gas price derivation method.
                      description: Suggested priority fee based on transaction priority, expressed in the requested currency and estimated gas units.
  /l2transactionfee:
    get:
      summary: Get the L2 transaction fee based on a transaction hash
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              required:
                - transactionHash
                - chainId
              properties:
                transactionHash:
                      type: string
                      description: The hash of an L2 transaction
                      example: "0x1234567890abcdef1234567890abcdef12345678"
                currency:
                  type: string
                  enum: [GigaWei, ETH, Native Token, Fiat Currency]
                  default: Null
                  description: The currency in which the fees should be expressed. Defaults to 'Null' if not specified setting the currency to the gas unit of account in the respective L2 such as GigaWei.
                  example: "ETH"
                chainId:
                  type: number
                  description: The unique identifier of the blockchain network where the transaction is intended to be processed.
                  example: 1
      responses:
        '200':
          description: L2 Transaction fee successfully retrieved
          content:
            application/json:
              schema:
                type: object
                required:
                  - transactionStatus
                  - totalL2TransactionFee
                  - executionFee
                  - dataFee
                  - priorityFee
                properties:
                 transactionStatus:
                    type: string
                    example: Confirmed  
                    description: The processing status of a submitted transaction specific to each L2.
                 totalL2TransactionFee:
                    type: object
                    required:
                      - value_currency
                      - value_gas
                    properties:
                      value_currency:
                        type: number
                        example: 0.00054
                      value_gas:
                        type: number
                        example: 27000
                    description: Total transaction fee based on the submitted transaction hash, as the sum of execution, data, and priority fee expressed in the requested currency and estimated gas units.
                  executionFee:
                    type: object
                    required:
                      - value_currency
                      - value_gas
                      - l2GasPrice
                    properties:
                      value_currency:
                        type: number
                        example: 0.00042
                      value_gas:
                        type: number
                        example: 21000
                      l2GasPrice:
                        type: number
                        example: 20
                        description: The Layer 2 gas price, expressed in GigaWei. 
                      l2GasPriceDerivationMethod:
                        type: string
                        description: The method used to derive the L2 gas price.
                      l2GasPriceDerivationMethodDescription:
                        type: string
                        description: Description of the L2 gas price derivation method.
                      l2GasPriceDerivationMethodSource:
                        type: string
                        format: uri
                        description: The source of information for the L2 gas price derivation method. 
                    description: The execution fee charged, expressed in the requested currency and estimated gas units.
                  dataFee:
                    type: object
                    required:
                      - value_currency
                      - value_gas
                      - l1GasPrice
                    properties:
                      value_currency:
                        type: number
                        example: 0.00002
                      value_gas:
                        type: number
                        example: 1000
                    l1GasPrice:
                      type: number
                      example: 100
                      description: The Layer 1 gas price, expressed in GigaWei. The gas price is either the gas price for L1 data or for L1 blob data, whichever price is cheaper.
                    l1GasPriceDerivationMethod:
                        type: string
                        description: The method used to derive the L1 gas price.
                    l1GasPriceDerivationMethodDescription:
                      type: string
                      description: Description of the L1 gas price derivation method.
                    l1GasPriceDerivationMethodSource:
                      type: string
                      format: uri
                      description: The source of information for the L1 gas price derivation method.  
                    description: Data fee charged, expressed in the requested currency and estimated gas units.
                  priorityFee:
                    type: object
                    required:
                      - priority
                      - value_currency
                      - value_gas
                      - l2PriorityGasPrice
                    properties:
                      priority:
                        type: string
                        example: High
                      value_currency:
                        type: number
                        example: 0.0001
                      value_gas:
                        type: number
                        example: 5000
                      l2PriorityGasPrice:
                        type: number
                        example: 20
                        description: The Layer 2 gas price, expressed in GigaWei.
                      l2PriorityGasPriceDerivationMethod:
                        type: string
                        description: The method used to derive the L2 priority gas price.
                      l2PriorityGasPriceDerivationMethodDescription:
                        type: string
                        description: Description of the L2 priority gas price derivation method.
                      l2PriorityGasPriceDerivationMethodSource:
                        type: string
                        format: uri
                        description: The source of information for the L2 priority gas price derivation method.     
                    description: Priority Fee charged, expressed in the requested currency and estimated gas units.
```

## 3.2 Layer 2 Transaction Fee Transparency Requirements
###### L2TFSPECTFAPIREQS

#### **[R1]** 

The `/l2transactionfeeestimate` and `/l2transactionfee` API endpoints MUST have a request body, and return a response body with an HTTP code.

[[R1]](#r1) Testability: 

**Test Preconditions:**
1. L2 stack API endpoints `/l2transactionfeeestimate` and `/l2transactionfee` are accessible.
2. The L2 stack is deployed and operational.
3. Proper authentication credentials, if required, are available.

**Test Steps:**
1. Send a request to the `/l2transactionfeeestimate` endpoint with a valid request body containing transaction details.
2. Verify that the endpoint returns a response body with an appropriate HTTP status code.
3. Inspect the response body to ensure it contains the expected data related to transaction fee estimation.
4. Repeat steps 1-3 for the `/l2transactionfee` endpoint.

**Passing Criteria:**
1. The `/l2transactionfeeestimate` endpoint returns a response body with an HTTP status code, and the response body contains the expected data for transaction fee estimation.
2. The `/l2transactionfee` endpoint returns a response body with an HTTP status code, and the response body contains the expected data for transaction fee retrieval.

### POST /l2transactionfeeestimate

#### **[R2]** 

**Request Parameters:**

The L2 Transaction Fee Estimation API request body has the following requirements:
- `chainId`: MUST be a positive integer and a valid, publicly accessible and verifiable 'chainId'.

For the `transactionCall` obbject 
  - `from`: MUST be a valid blockchain address.
  - `to`: MUST be a valid blockchain address.
  - `gas`: MUST be a positive integer.
  - `gasPrice`: MUST be a positive integer.
  - `value`: MUST be a non-negative numeric value.
  - `input`: MUST be a valid hexadecimal string.
- `transactionPriority`: MUST be one of a set of priority levels as defined by the L2 that provides the API implementation.
- `currency`: MUST be a valid currency code of either GigaWei or ETH, or as defined by the L2 that provides the API implementation.

[[R2]](#r2) Testability:

**Test Preconditions:**
1. Access to the L2 Transaction Fee Estimation API endpoint.
2. Proper authentication credentials, if required, are available.

**Test Steps:**
1. Prepare a request body with the following fields:
   - `chainId`: A positive integer representing a valid, publicly accessible, and verifiable 'chainId'.
   - `transactionCall` object containing:
     - `from`: A valid blockchain address.
     - `to`: A valid blockchain address.
     - `gas`: A positive integer representing gas.
     - `gasPrice`: A non-negative integer representing gas price.
     - `value`: A non-negative numeric value.
     - `input`: A valid hexadecimal string.
   - `transactionPriority`: One of the priority levels defined by the L2.
   - `currency`: A valid currency code representing either GigaWei or ETH.

**Passing Criteria:**
1. The request body is correctly structured with all required fields.
2. The `chainId` field is a positive integer and points to a valid, publicly accessible, and verifiable 'chainId'.
3. The `transactionCall` object fields (`from`, `to`, `gas`, `gasPrice`, `value`, `input`) conform to their respective requirements.
4. The `transactionPriority` field matches one of the priority levels defined by the L2.
5. The `currency` field is a valid currency code representing either GigaWei or ETH, or as defined by the L2.

#### **[R3]** 

**Response Parameters:**

The L2 Transaction Fee Estimation API response body parameters have the following requirements:
- `totalL2TransactionFee`:
  - `value_currency`: MUST be a non-negative numeric value.
  - `value_gas`: MUST be a non-negative numeric value.
- `executionFee`:
  - `value_currency`: MUST be a non-negative numeric value.
  - `value_gas`: MUST be a non-negative numeric value.
  - `l2GasPrice`: MUST be a non-negative numeric value.
  - `l2GasPriceDerivationMethod`: MUST be a non-empty string.
  - `l2GasPriceDerivationMethodDescription`: MUST be a non-empty string.
  - `l2GasPriceDerivationMethodSource`: MUST be a non-empty string formatted as URI.
- `dataFee`:
  - `value_currency`: MUST be a non-negative numeric value.
  - `value_gas`: MUST be a non-negative numeric value.
  - `l1GasPrice`: MUST be a non-negative numeric value.
  - `l1GasPriceDerivationMethod`: MUST be a non-empty string.
  - `l1GasPriceDerivationMethodDescription`: MUST be a non-empty string.
  - `l1GasPriceDerivationMethodSource`: MUST be a non-empty string formatted as URI.
- `priorityFee` MUST be an array and each object in the array has the following requirements:
    - `priority`: MUST be a non-empty string.
    - `value_currency`: MUST be a non-negative numeric value.
    - `value_gas`: MUST be a non-negative numeric value.
    - `l2PriorityGasPrice`: MUST be a non-negative numeric value.
    - `l2PriorityGasPriceDerivationMethod`: MUST be a non-empty string.
    - `l2PriorityGasPriceDerivationMethodDescription`: MUST be a non-empty string.
    - `l2PriorityGasPriceDerivationMethodSource`: MUST be a non-empty string formatted as URI.

[[R3]](#r3) Testability:

**Test Preconditions:**
1. Access to the L2 Transaction Fee Estimation API endpoint.
2. A valid request with appropriate parameters sent to the API.

**Test Steps:**
1. Receive the API response containing parameters:
   - `totalL2TransactionFee` object with:
     - `value_currency`: A non-negative numeric value.
     - `value_gas`: A non-negative numeric value.
   - `executionFee` object with:
     - `value_currency`: A non-negative numeric value.
     - `value_gas`: A non-negative numeric value.
     - `l2GasPrice`: A non-negative numeric value.
     - `l2GasPriceDerivationMethod`: A non-empty string.
     - `l2GasPriceDerivationMethodDescription`: A non-empty string.
     - `l2GasPriceDerivationMethodSource`: A non-empty string formatted as URI.
   - `dataFee` object with:
     - `value_currency`: A non-negative numeric value.
     - `value_gas`: A non-negative numeric value.
     - `l1GasPrice`: A non-negative numeric value.
     - `l1GasPriceDerivationMethod`: A non-empty string.
     - `l1GasPriceDerivationMethodDescription`: A non-empty string.
     - `l1GasPriceDerivationMethodSource`: A non-empty string formatted as URI.
   - `priorityFee` array with each object containing:
     - `priority`: A non-empty string.
     - `value_currency`: A non-negative numeric value.
     - `value_gas`: A non-negative numeric value.
     - `l2PriorityGasPrice`: A non-negative numeric value.
     - `l2PriorityGasPriceDerivationMethod`: A non-empty string.
     - `l2PriorityGasPriceDerivationMethodDescription`: A non-empty string.
     - `l2PriorityGasPriceDerivationMethodSource`: A non-empty string formatted as URI.

**Passing Criteria:**
1. Each parameter in the API response meets the specified requirements.
2. All numeric values are non-negative.
3. All strings are non-empty.
4. URI strings are properly formatted.
5. The `priorityFee` array contains objects with all required fields.

### GET /l2transactionfee

#### **[R4]**

**Request Parameters:**

The L2 Transaction Fee API request body has the following requirements:
- `transactionHash`: MUST be a non-empty hexadecimal string.
- `currency`: MUST be a valid currency code of either GigaWei or ETH, or as defined by the L2 that provides the API implementation.
- `chainId`: MUST be a positive integer and a valid, publicly accessible and verifiable 'chainId'.

[[R4]](#r4) Testability:

**Test Preconditions:**
1. Access to the L2 Transaction Fee API endpoint.
2. A valid request with appropriate parameters sent to the API.

**Test Steps:**
1. Send a request to the L2 Transaction Fee API endpoint with a request body containing:
   - `transactionHash`: A non-empty hexadecimal string.
   - `currency`: A valid currency code (e.g., GigaWei or ETH) or as defined by the L2.
   - `chainId`: A positive integer representing a valid, publicly accessible and verifiable 'chainId'.

**Passing Criteria:**
1. The API request is successfully processed.
2. The request body contains the specified parameters.
3. `transactionHash` is a non-empty hexadecimal string.
4. `currency` is a valid currency code.
5. `chainId` is a positive integer and represents a valid, publicly accessible, and verifiable 'chainId'.

**Response Parameters:**

#### **[R5]**

The L2 Transaction Fee API response body has the following requirements:

- `transactionStatus`: MUST be a string. Note, give that there is no standardization on L2 Transaction statuses, the displayed string values will depend on the specific L2 client transaction status implementation.
- `totalL2TransactionFee`:
  - `value_currency`: MUST be a non-negative numeric value.
  - `value_gas`: MUST be a non-negative numeric value.
- `executionFee`:
  - `value_currency`: MUST be a non-negative numeric value.
  - `value_gas`: MUST be a non-negative numeric value.
  - `l2GasPrice`: MUST be a non-negative numeric value.
  - `l2GasPriceDerivationMethod`: MUST be a non-empty string.
  - `l2GasPriceDerivationMethodDescription`: MUST be a non-empty string.
  - `l2GasPriceDerivationMethodSource`: MUST be a non-empty string formatted as URI.
- `dataFee`:
  - `value_currency`: MUST be a non-negative numeric value.
  - `value_gas`: MUST be a non-negative numeric value.
  - `l1GasPrice`: MUST be a non-negative numeric value.
  - `l1GasPriceDerivationMethod`: MUST be a non-empty string.
  - `l1GasPriceDerivationMethodDescription`: MUST be a non-empty string.
  - `l1GasPriceDerivationMethodSource`: MUST be a non-empty string formatted as URI.
- `priorityFee`:
  - `value_currency`: MUST be a non-negative numeric value.
  - `value_gas`: MUST be a non-negative numeric value.
  - `l2PriorityGasPrice`: MUST be a non-negative numeric value.
  - `l2PriorityGasPriceDerivationMethod`: MUST be a non-empty string.
  - `l2PriorityGasPriceDerivationMethodDescription`: MUST be a non-empty string.
  - `l2PriorityGasPriceDerivationMethodSource`: MUST be a non-empty string formatted as URI.

[[R5]](#r5) Testability:

**Test Preconditions:**
1. Sent a valid request to the L2 Transaction Fee API endpoint.
2. Received a response from the API.

**Test Steps:**
1. Parse the response body received from the L2 Transaction Fee API.
2. Verify that the following fields exist and meet the specified requirements:
   - `transactionStatus`: Must be one of "confirmed", "pending", or "failed".
   - `totalL2TransactionFee`:
     - `value_currency`: Must be a non-negative numeric value.
     - `value_gas`: Must be a non-negative numeric value.
   - `executionFee`:
     - `value_currency`: Must be a non-negative numeric value.
     - `value_gas`: Must be a non-negative numeric value.
     - `l2GasPrice`: Must be a non-negative numeric value.
     - `l2GasPriceDerivationMethod`: Must be a non-empty string.
     - `l2GasPriceDerivationMethodDescription`: Must be a non-empty string.
     - `l2GasPriceDerivationMethodSource`: Must be a non-empty string formatted as URI.
   - `dataFee`:
     - `value_currency`: Must be a non-negative numeric value.
     - `value_gas`: Must be a non-negative numeric value.
     - `l1GasPrice`: Must be a non-negative numeric value.
     - `l1GasPriceDerivationMethod`: Must be a non-empty string.
     - `l1GasPriceDerivationMethodDescription`: Must be a non-empty string.
     - `l1GasPriceDerivationMethodSource`: Must be a non-empty string formatted as URI.
   - `priorityFee`:
     - `value_currency`: Must be a non-negative numeric value.
     - `value_gas`: Must be a non-negative numeric value.
     - `l2PriorityGasPrice`: Must be a non-negative numeric value.
     - `l2PriorityGasPriceDerivationMethod`: Must be a non-empty string.
     - `l2PriorityGasPriceDerivationMethodDescription`: Must be a non-empty string.
     - `l2PriorityGasPriceDerivationMethodSource`: Must be a non-empty string formatted as URI.

**Passing Criteria:**
1. The API response is successfully received.
2. All required fields exist in the response body.
3. The values of each field meet the specified requirements.

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

This document defines the conformance levels of L2 Transaction Fee API as follows:
* **Level 1:** All MUST requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.
* **Level 2:** All MUST and SHOULD requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.
* **Level 3:** All MUST, SHOULD, and MAY requirements with conditional MUST or SHOULD requirements are fulfilled by a specific implementation as proven by a test report that proves in an easily understandable manner the implementation's conformance with each requirement based on implementation-specific test-fixtures with implementation-specific test-fixture inputs.

#### **[D1]** 
A claim that an L2 Transaction Fee API conforms to this specification SHOULD describe a testing procedure carried out for each requirement to which conformance is claimed, that justifies the claim with respect to that requirement.

[[D1]](#d1) Testability: Since each of the conformance target requirements in this documents is testable, so must be the totality of the requirements in this document. Therefore, conformance tests for all requirements can exist, and can be described as required in [[D1]](#d1).

#### **[R6]** 
A claim that an L2 Transaction Fee API conforms to this specification at **Level 2** or higher MUST describe the testing procedure carried out for each requirement at **Level 2** or higher, that justifies the claim to that requirement.

[[R6]](#r6) Testability: Since each of the non-conformance-target requirements in this documents is testable, so must be the totality of the requirements in this document. Therefore, conformance tests for all requirements can exist, be described, be built and implemented and results can be recorded as required in [[R6]](#r6).

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

#### **[OPEN-API-3]**
Darrel Miller, Jeremy Whitlock, Marsh Gardiner, Mike Ralphson, Ron Ratovsky, https://spec.openapis.org/oas/v3.0.0.html


## A.2 Non-Normative References
###### L2TFSPECAPREFNONNORM

#### **[W3C-String-Meta]**

Strings on the Web: Language and Direction Metadata, R. Ishida, A. Phillips, August 2022,
https://www.w3.org/TR/string-meta/


# Appendix B - Security Considerations
###### L2TFSPECAPBSEC

There are no additional security requirements. However, each implementer is encouraged to utilize current API endpoint security best practices such as OAUTH2 endpoint protection, software firewalls, and (Distributed) Denial of Service (DDOS) attack mitigation.  

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

Landong Gengrich\
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