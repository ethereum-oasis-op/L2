# Meeting Minutes: Technical Specification of General Layer 2 Blockchain Scalability Solutions for EVM-compatible public Blockchains WG

## Meeting Wed, 30 Novt 2022, 7:00 am PT

Attending: Andreas Freund (EF), Daniel Goldman (Offchain Labs), Cody Burns (Accenture), Kartheek Solipuram (E&Y)

Regrets: Ramon Canales (Matter Labs), Kelvin Fichter (Optimism), Weija Zhang (Wanchain, EEA Crosschain Interop Group), Pavel Sinelnikov (Metis), Parth Bhatt, Elena Sinelnikova (Metis), Anav Agrawal (Polygon), Ino Murko (Boba Network), Alan Chiu (Boba Network), Omar Azhar (Matter Labs), Souradeep (Boba Network), Violet (Boba Network), Hanan Beer (EF), Yoav Weiss (EF), Jose Fabrega (Metis), Samrat Kishor (Golden Next Ventures), Dan Shaw (EF), Anais Ofranc (EEA), Tas Dienes (EF), Gabriel Barros (Cartesi)

Scribe: Andreas Freund

Proposed agenda

1. Welcome, and a reminder of the WG meeting rule
2. Selection of scribe
3. Introduction of new participants
4. EEA Crosschain Interoperability WG Presentation on the current status of their efforts on crosschain addressing
5. Review PR: #29 -- EVM-based Address Aliasing, and updates made based on last WG meeting and other feedback
6. Review Open Issues List
7. Select the next work item
8. Open Forum for other items

Meeting notes
1. Kartheek Solipuram (E&Y) joined for the first time
2. After Welcomes, Andreas Freund was selected as scribe
Katheek introduced himself to the group and his interest and work in Layer 2 and Layer 2 bridges as E&Y solution architect
3. EEA Crosschain Interoperability WG did not present as scheduled. Will move presentation to the next meeting on 12/14
4. PR#29 – EVM-based Address Aliasing
    - Andreas: Presented an overview of PR #29 with a focus on the added security considerations
    - Dan: Agreed with proposed language
    - Cody: Asked clarifying questions, in particular on checksum for relativeAddress. Will add comment.
    - Kartheek: Asked clarifying questions on relativAddress structure and security considerations. 
5. Open Issues Review
    - On L2 Interfaces: Karhteek to add some comments based on what he is working on with L2 bridges
    - On L2 Trxn Fees: 
      * Dan and Andreas discussed possible substructures of the priority fee around MEV. 
      * Also discussed trxn ordering in a decentralized sequencer network and how that can be achieved with PoS consensus. Andreas mentioned EigenLayer as a staking mechanism to add L1 protection to L2 sequencer consensus. 
      * Andreas will create PR with draft of definition before next WG meeting
6. Other Business
    - Andeas updated on submission of Canonical Token List spec to PGB and next steps


## Meeting Wed, 16 Novt 2022, 7:00 am PT

Attending: Andreas Freund (EF), Dan Shaw (EF), Anais Ofranc (EEA), Tas Dienes (EF), Gabriel Barros (Cartesi)

Regrets: Daniel Goldman (Offchain Labs),  Ramon Canales (Matter Labs), Kelvin Fichter (Optimism), Daniel Goldman (Offchain Labs), Weija Zhang (Wanchain, EEA Crosschain Interop Group), Pavel Sinelnikov (Metis), Parth Bhatt (MOBI), Elena Sinelnikova (Metis), Anav Agrawal (Polygon), Cody Burns (Accenture), Ino Murko (Boba Network), Alan Chiu (Boba Network), Omar Azhar (Matter Labs), Souradeep (Boba Network), Violet (Boba Network), Hanan Beer (EF), Yoav Weiss (EF), Jose Fabrega (Metis), Samrat Kishor (Golden Next Ventures), 

Scribe: Gabriel Barros

Proposed Agenda:

1. Welcome, and a reminder of the WG meeting rule
2. Selection of scribe
3. Introduction of new participants
4. Report out from Meeting with EEA Cross-chain Interop WG meeting on 11/9
5. Review PR: #29 -- EVM-based Address Aliasing, and updates made based on last WG meeting and other feedback
6. Review Open Issues List
7. Select the next work item
8. Open Forum for other items

Meeting Notes:

1. No new participants.
2. Merged PR #26 - Canonical Token List Spec Draft : Will be submit for approval by PGB
2. Review PR #29 - EVM-based Address Aliasing
    - Andreas provided an overview from last meeting discussions
    - Gabriel asked clarifying question about 8bytes size limit and human readable chainIDs
    - We need clarification on "no-code at the address for bridged assets" security concern
    - Presentation on the agenda for the next meeting (issue #31 – Crosschain WG x L2 Group) 
3. Review of open issues
    - Call out for interested parties on issue #21
    - Closing issue #20 as dup of #21
    - Gabriel to add Cartesi model as comment to issue #23 - Fee structure
4. Next work item
    - Andreas shared "The State of L2 Bridges" wip document
5. Discussion on the dates of the last meetings of the year and return on 11th of Jan of next year. No meeting Dec 28.
6. Anais brought up the topic of reaching out to other interested groups (such as EVM compatible L1 chains) for the standards created here. 

## Meeting Wed, 2 Novt 2022, 7:00 am PT

Attending: Andreas Freund (EF), Dan Shaw (EF), Daniel Goldman (Offchain Labs), Anais Ofranc (EEA), Tas Dienes (EF), Ramon Canales (Matter Labs), Kelvin Fichter (Optimism),

Regrets: Daniel Goldman (Offchain Labs), Weija Zhang (Wanchain, EEA Crosschain Interop Group), Pavel Sinelnikov (Metis), Parth Bhatt, Elena Sinelnikova (Metis), Anav Agrawal (Polygon), Cody Burns (Accenture), Ino Murko (Boba Network), Alan Chiu (Boba Network), Omar Azhar (Matter Labs), Souradeep (Boba Network), Violet (Boba Network), Hanan Beer (EF), Yoav Weiss (EF), Jose Fabrega (Metis), Samrat Kishor (Golden Next Ventures), Gabriel Barros (Cartesi)

Scribe: Anais Ofranc

Proposed agenda

1. Welcome, and a reminder of the WG meeting rule
2. Selection of scribe
3. Introduction of new participants
4. Review PRs: 
  * #26 -- Canonical Token List Spec Draft (merge after meeting hopefully)
  * #29 -- EVM-based Address Aliasing
5. Review Open Issues List
6. Open Forum for other items

Meeting notes

* New Participants
  - Ramon Canales (Matter Labs), recently joined the ZK Sync team.
* Review PRs: #26 -- Canonical Token List Spec Draft
  - Andreas provided a review of the draft and its purpose
  - All participants agreed it is ready to merge
* Review PRs: #29 -- EVM-based Address Aliasing
  - Andreas provided an overview of the specification and its purpose
  - Ramon asked clarifying questions
  - Kelvin noted tha 8 bytes for encoding should be enough
  - Kelvin suggested that it needs a security section to ensure that addresses for bridged assets are validated to have no code in order to avoid malicious behavior
  - Kelvin agreed to add suggestions on wording for 8 byte limitation and a security section  by the next meeting
* Review of open issues
  - Confirmed L2 report out date for EEA Crosschain WG of 11/9 with Anais
  - Participants agreed that providing a definition of transaction fee terms and general structure would be a good next work item
  - Kelvin agreed to add Optimisim fee structure, definitions and calculations to the fee issue
  - WG briefly discussed remaining open items with agreement that additional low-hanging-fruit interoperability work items should be a focus in 2023
* Meeting adjourned


## Meeting Wed, 19 Oct 2022, 7:00 am PT

Attending: Andreas Freund (EF), Dan Shaw (EF), Gabriel Barros (Cartesi), Daniel Goldman (Offchain Labs), Anais Ofranc (EEA)

Regrets: Tas Dienes (EF), Daniel Goldman (Offchain Labs), Weija Zhang (Wanchain, EEA Crosschain Interop Group), Pavel Sinelnikov (Metis), Parth Bhatt, Elena Sinelnikova (Metis), Anav Agrawal (Polygon), Cody Burns (Accenture), Ino Murko (Boba Network), Alan Chiu (Boba Network), Omar Azhar (Matter Labs), Souradeep (Boba Network), Violet (Boba Network), Hanan Beer (EF), Yoav Weiss (EF), Kelvin Fichter (Optimism), Jose Fabrega (Metis), Samrat Kishor (Golden Next Ventures),

Scribe: Dan Shaw

Agenda
1. Welcome, and a reminder of the WG meeting rule
2. Selection of scribe
3. Introduction of new participants
4. Review PRs: #26 -- Canonical Token List Spec Draft (merge after meeting hopefully) & #29 -- EVM-based Address Aliasing
Review Open Issues List
5. Open Forum for other items

Meeting notes
+ Review PR #29 (address aliasing)
  - Discussed whether we should start this standardization effort with an EIP to get 
  - All EVM-based chains MUST have a chain id to prevent replay attack
  - It was identified that the current max character length for chain IDs is 13, so we need to increase to at least 16 characters
  - Anais noted EIP 3220 https://eips.ethereum.org/EIPS/eip-3220, noting that it would be good to align where we land with the EEA Crosschain Working Groups efforts
  - Decision was made to start with an EIP for Chain IDs
  - Next steps
    * Finalize PR approval
    * Then need at least 2 implementations
OASIS Standardization
    * Anais invited the L2 WG to come join the Crosschain WG and the Crosschain WG to the L2 WG
    * Andreas will represent the group at the Crosschain WG 
+ Issue #23 (transaction fee structure) was reviewed
  - Daniel will add how Arbitrum handles this


## Meeting Wed, 5 Oct 2022, 7:00 am PT

Attending: Andreas Freund (EF/TreeTrunk), Tas Dienes (EF), Dan Shaw (EF), Gabriel Barros (Cartesi), Jose Fabrega (Metis), Samrat Kishor (Golden Next Ventures), Anais Ofranc 

Regrets: Daniel Goldman (Offchain Labs), Weija Zhang (Wanchain, EEA Crosschain Interop Group), Pavel Sinelnikov (Metis), Parth Bhatt, Elena Sinelnikova (Metis), Anav Agrawal (Polygon), Cody Burns (Accenture), Ino Murko (Boba Network), Alan Chiu (Boba Network), Omar Azhar (Matter Labs), Souradeep (Boba Network), Violet (Boba Network), Hanan Beer (EF), Yoav Weiss (EF), Kelvin Fichter (Optimism), 

Scribe: Tas Dienes

Proposed agenda
1. Welcome, and a reminder of the WG meeting rule
2. Selection of scribe
3. Introduction of new participants
4. Review PRs: 
    - #26 -- Canonical Token List Spec Draft
    - #29 -- EVM-based Address Aliasing
5. Review Open Issues List
6. Open Forum for other items

Meeting notes

* Review PR #26 (token list)
  - It’s at the point of final review, ready to merge if no more comments. 
  - Andreas explained the proposed standard
  - Q: where will token lists be hosted? A: each project will have and host its own.  It’s not centralized.
  - Need 2 more approvals
* Review PR #29 (address aliasing)
  - Andreas explained the proposed standard
  - Gabriel pointed out the need for an address order requirement. Andreas said he would add it.
* Issue #23 (transaction fee structure) was reviewed
* Issue #20 (cross chain interop interface) was reviewed
  - Anais mentioned work that the EEA cross chain interop group is working on https://entethalliance.github.io/crosschain-interoperability/draft_crosschain_techspec_messaging.html 

## Meeting Wed, 21 Sep 2022, 7:00 am PT

Attending: Hanan Beer (EF), Tas Dienes (EF), Dan Shaw (EF), Andreas Freund (EF/TreeTrunk), Yoav Weiss (EF), Kelvin Fichter (Optimism), Samrat Kishor (Golden Next Ventures),

Regrets: Daniel Goldman (Offchain Labs), Weija Zhang (Wanchain, EEA Crosschain Interop Group), Pavel Sinelnikov (Metis), Parth Bhatt, Elena Sinelnikova (Metis), Anav Agrawal (Polygon), Cody Burns (Accenture), Ino Murko (Boba Network), Alan Chiu (Boba Network), Omar Azhar (Matter Labs), Souradeep (Boba Network), Violet (Boba Network)

Scribe: Tas Dienes

Proposed agenda
1. Welcome, and a reminder of the WG meeting rules
2. Selection of scribe
3. Introduction of new participants
4. Review PRs: #26 -- Canonical Token List Spec Draft & #29 -- EVM-based Address Aliasing
5. Review Open Issues List
6. Open Forum for other items

Meeting notes
- PR #26 Canonical Token List Spec Draft
  * Andreas presented an overview of the document 
  * Tas will reach out to Offchain Labs for their input***
- PR #29 EVM-based Address Aliasing
  * Andreas and Kelvin discussed the spec
  * In an execution context, you can’t tell if an address is an alias
  * Disallow chainId 0, limit max chainId value
  * Kelvin and Andreas will add details to the PR
- Issue #21 L2 Transaction Interface was discussed
  * Hanan mentioned the problem of bridging tokens to another chain and not having gas on that chain.  Yoav said that account abstraction ERC-4337 should help solve that. There is a potential spec to be developed around this.
- Issue #23 L2 Tx Fee Structure was discussed by Andreas and Yoav
- Andreas will send an email poll about whether to change the October meeting schedule due to Devcon.


## Meeting Wed, 7 September 2022, 7:00 am PT

Attending: Andreas Freund (EF), Tas Dienes (EF), Dan Shaw (EF), Kelvin Fichter (Optimism), Daniel Goldman (Offchain Labs), Sourdeep Das (Boba Network), Samrat Kishor (Golden Next Ventures),

Regrets:  Pavel Sinelnikov (Metis), Parth Bhatt, Elena Sinelnikova (Metis), Anav Agrawal (Polygon), Cody Burns (Accenture), Ino Murko (Boba Network), Alan Chiu (Boba Network), Omar Azhar (Matter Labs), Violet (Boba Network)

Scribe: Dan Shaw

Agenda
1. Welcome, and a reminder of WG meeting rule
2. Selection of scribe
3. Introduction of new participants
4. Review PR #26 -- Canonical Token List Spec Draft https://github.com/eea-oasis/L2/pull/26
5. Review Open Issues List
6. Open Forum for other items

Meeting notes
-  A propoal was made to ensure that the Token List Standard Proposal remain a strict superset of the tokenlist specification
-  Looking for approvals on PR #26 from Cody Burns, Kelvin Fichter, and Kyle Thomas, then we'll do one final round of review and send it off to the PGB for approval
-  Closing [Issue #6]([url](https://github.com/eea-oasis/L2/issues/6)) as completed
-  Closing [Issue #17]([url](https://github.com/eea-oasis/L2/issues/17)) as completed
-  Reviewed [Issue #24]([url](https://github.com/eea-oasis/L2/issues/24))
  - Daniel Goldman proposed integrating [address aliasing]([url](https://developer.offchainlabs.com/arbos/l1-to-l2-messaging#address-aliasing))
-  Reviewed [Issue #20]([url](https://github.com/eea-oasis/L2/issues/20))
  - It was proposed that we add a definition of finality and then categorize by L2

## Meeting Wed, 24 August 2022, 7:00 am PT

Attending: Andreas Freund (EF/TreeTrunk), Tas Dienes (EF), Dan Shaw (EF), Daniel Goldman (Offchain Labs), Weija Zhang (Wanchain, EEA Crosschain Interop Group), Samrat Kishor (Golden Next Ventures),

Regrets:  Pavel Sinelnikov (Metis), Kelvin Fichter (Optimism),  Parth Bhatt, Elena Sinelnikova (Metis), Anav Agrawal (Polygon), Cody Burns (Accenture), Ino Murko (Boba Network), Alan Chiu (Boba Network), Omar Azhar (Matter Labs), Souradeep (Boba Network), Violet (Boba Network)

Scribe: Tas Dienes

Agenda
1. Welcome, and a reminder of WG meeting rule
2. Selection of scribe
3. Introduction of new participants
4. Review PR #26 -- Canonical Token List Spec Draft https://github.com/eea-oasis/L2/pull/26
5. Review Open Issues List
6. Open Forum for other items

Meeting notes
-  Weija Zhang says the crosschain interoperability group previously did some work on token lists and has some interest in the topic.

    * https://medium.com/wanchain-foundation/understanding-wanchain-two-way-bridge-and-direct-bridge-7f6088617734
    * Human readable naming convention: [provider]TOKENSYMBOL@chainname * 
    * E.g. wanETH@wanchain or ethWAN@ethereum, ETH@ethereum
    * It’s a bit long
- Andreas says apps can look up tokenSymbol by tokenId. tokenId may not be human readable.
- Weija: can we recommend a naming convention for UX display of crosschain token symbols?
- Daniel: make it an optional field in the token list?
- Tas: Do we need a separate chainList?  Andreas: maybe
- Weija will propose a change request to add a human readable token symbol to the tokenList
- Andreas: add granularity into description of decimals property
- chainURI could be a DID. Andreas to add explanatory text.
- Andreas will add RFC numbers to URI properties, and EIPs where appropriate 
- Daniel suggested the need for a separate list for bridges 

## Meeting Wed, 10 August 2022, 7:00 am PT

Canceled since both Chair were absent but excused.

## Meeting Wed, 27 July 2022, 7:00 am PT

Attending: Tas Dienes (EF), Dan Shaw (EF), Omar Azhar (Matter Labs), Souradeep (Boba Network), Violet (Boba Network)

Regrets: Andreas Freund (EF/TreeTrunk),  Pavel Sinelnikov (Metis), Kelvin Fichter (Optimism),  Samrat Kishor (Golden Next Ventures), Parth Bhatt, Elena Sinelnikova (Metis), Anav Agrawal (Polygon), Cody Burns (Accenture), Ino Murko (Boba Network), Alan Chiu (Boba Network)

Scribe: Tas Dienes

Proposed agenda:
1. Welcome, and a reminder of WG meeting rules
2. Selection of scribe
3. Introduction of new participants
4. Review the new Token List Spec Draft  PR https://github.com/eea-oasis/L2/pull/26 
5. Open Forum for other items

Meeting notes:
- Andreas was out; Dan Shaw ran the meeting
- TokenList draft spec discussion
  - Omar and Souradeep have looked at it; reviewing further
  - It was posted to ethresear.ch 
  - Micah Zoltu commented that https://tokenlists.org/ already exists, run by Uniswap
  -  ACTION: Ask Kelvin why Optimism isn’t using that
  - ACTION: Tas to contact Optimism and Arbitrum and Metis to review the PR
- Omar asked about Issue #6 and GPACT. Dan pointed him to the EEA Crosschain WG github repo.


## Meeting Wed, 13 July 2022, 7:00 am PT

Attending: Andreas Freund (EF/TreeTrunk), Tas Dienes (EF), Dan Shaw (EF), Pavel Sinelnikov (Metis), Kelvin Fichter (Optimism), Omar Azhar (Matter Labs), Samrat Kishor (Golden Next Ventures), Parth Bhatt

Regrets: Elena Sinelnikova (Metis), Anav Agrawal (Polygon), , Cody Burns (Accenture), Ino Murko (Boba Network), Souradeep (Boba Network), Alan Chiu (Boba Network)

Scribe: Pavel Sinelnikov

Proposed agenda
1. Welcome, and a reminder of WG meeting rule
2. Selection of scribe
3. Introduction of new participants
4. Continue the discussion on the Token List work item with a focus on reaching an agreement on an updated schema.& discuss proposed governance process
5. Open Forum for other items

Meeting notes

Discussion of Issue #22 - https://github.com/eea-oasis/L2/issues/22
  * No objections to https://github.com/eea-oasis/L2/issues/22#issuecomment-1180894487
    -  Intention is to eventually move it to IPFS
  * Getting more complex than what the initial vision was
    - Can make things optional, what is REQUIRED and OPTIONAL
  * Next steps is to write a standards document with what oasis recommends
  * Try to bring in Arbitrum, Loopring, Aztec, Starkware, and Polygon to review the issue 
    - Arbitrum - Tas
    - Starkware, Loopring, and Aztec, and Polygon (mailing list) - Andreas
  * Following standardization process outlined by https://github.com/eea-oasis/baseline-standard/issues/72
  * People might not be familiar with the spec standards, joining the meeting would be the best way to communicate
  * Should a deadline be set on commenting? - no rush


## Meeting Wed, 29 June 2022, 7:00 am PT

Attending: Andreas Freund (EF/TreeTrunk), Tas Dienes (EF), Dan Shaw (EF), Kelvin Fichter (Optimism), Ino Murko (Boba Network), Souradeep (Boba Network), Alan Chiu (Boba Network)

Regrets: Elena Sinelnikova (Metis), Anav Agrawal (Polygon), Pavel Sinelnikov (Metis), Cody Burns (Accenture)

Scribe: Tas Dienes

Proposed agenda:
1. Welcome, and a reminder of WG meeting rules
2. Selection of scribe
3. Introduction of new participants
4. Continue the discussion on the Token List work item with a focus on reaching an agreement on an updated schema.
5. Decide on a date for the AnyTrust presentation by Arbitrum and, subsequently, Metis.
PROPOSAL: Utilize our off weeks for projects to present their current project to the WG including the EEA Crosschain Interop WG 
6. Open Forum for other items

Meeting notes
- Alan, Ino, and Souradeep from Boba Network introduced themselves
- Discussion of Issue #22 - Token list standard  https://github.com/eea-oasis/L2/issues/22	
- Kelvin restated the problem
- Andreas said he added a new token list format proposal which incorporates input from previous comments
- Each chain will maintain their own TokenList, because maintaining one global TokenList is a governance headache.
- Andreas and Kelvin discussed the proposed format and made some changes
- Andreas will add some additional ideas (including TokenId) to the proposal after this meeting
- Tas to work on choosing a date for AnyTrust presentation - favor off weeks from this WG meeting. Andreas made a proposal to offer off weeks for L2 education sessions; approved with no objections. 


## Meeting Wed, 15 June 2022, 7:00 am PT

Attending: Andreas Freund (EF/TreeTrunk), Tas Dienes (EF), Dan Shaw (EF), Kelvin Fichter (Optimism), Anav Agrawal (Polygon), Pavel Sinelnikov (Metis), Cody Burns (Accenture)

Regrets: Elena Sinelnikova (Metis)

Scribe: Pavel Sinelnikov

Proposed agenda
1. Welcome, and a reminder of WG meeting rules 
2. Selection of scribe Introduction of new participants 
3. Status of Arbitrum/Metis presentation on Validium-type Optimistic Rollups -- Tas 
4. First focused discussion and distribution of work items on the most commented issues -- Transaction Fees, Transaction Interfaces, Transaction Interop Interfaces or Token List 
5. Open Forum for other items 

Notes for the meeting

Problem of standardized token lists - here are the tokens and routes
- Token names and symbols should not be used as identifiers
- Governance headaches when implementing a single token list
- Canonical Token List + Bridge Token List
- No bridge is currently working on this
- Need to contact all existing L2s and other chains that are based on Ethereum - just standardizing it under all L2s would give reasons for other chains to adopt the standard
tokenId in a dedicated namespace, similar to a DID
  * DID registry as long as it is compliant with the interface and node for governance - registry does not need to be in a single location
    - Pull in PR
    - Reviewers that review to be compliant with the spec
    - If using an existing namespace, it would not be allowed (e.g. did.microsoft)
    - How namespace conflicts are handled is still under discussion
    - Can have duplicate methods, choice of registry matters
    - Write a test suite to test compliance to make sure that there are no duplicates, essentially governance with more automation
  * PR is merged

Discussion on the creation of a Oracle Aggregation standard - likely more fitting for a different standardization platform

https://github.com/eea-oasis/L2/issues/21 - Testnet creation on the EIP-4844 standard. Need nodes to see if there is support
- Testnet will be created likely within a few months
- Creating a new issue or discussion on the standard


## Meeting Wed, 1 June 2022, 7:00 am PT
Attending: Andreas Freund (EF/TreeTrunk), Tas Dienes (EF), Dan Shaw (EF), Syed Shamayel (Accenture), Niraj Gadgilwar (Accenture), Yuan “Peter” Su (Metis), Samrat Kishor, Cody Burns (Accenture), Sushil Saha (Accenture)

Regrets: Pavel Sinelnikov (Metis), Will Harborne (Deversifi), Konrad (Deversifi), Kelvin Fichter (Optimism), Kyle Thomas (Provide),

Scribe: Tas Dienes

Proposed agenda
1. Welcome, and a reminder of WG meeting rules
2. Selection of scribe
3. Introduction of new participants
4. Discuss the list and contact of new issues and organize workgroups around some or all of them
5. Discuss potential timing and logistics for a presentation by Arbitrum folks on AnyTrust.
6. Open Forum for other items

Notes the meeting

1. If you want to be on the WG’s email list, send an email to general-l2-scalability+subscribe@lists.oasis-open-projects.org
2. Blog post on cross chain asset migration is in the pipeline, almost ready to publish 
3. Discussion of issues https://github.com/eea-oasis/L2/issues
    - Yuan will add some comments and details on #20.  It could be split up into multiple parallel topics.
    - [#21](https://github.com/eea-oasis/L2/issues/21) is for an RPC API
    - [#22](https://github.com/eea-oasis/L2/issues/22) was suggested by Optimism 
    - [#23](https://github.com/eea-oasis/L2/issues/23) (transaction fee structure) has been raised by Optimism and Arbitrum. Metis interested too. 
    - [#24](https://github.com/eea-oasis/L2/issues/24) was brought up by Will Harborne and Andreas Freund.  Cody suggested using soulbound tokens.  Andreas discussed using DIDs. One DID can connect to multiple keys with multiple algos. Yuan expressed interest in working on it.
4. Discussing a presentation about AnyTrust.  Metis also has an L2 that keeps data off of L1 in the happy case; only a Tx hash is written to L1 when cooperating.  Tas to propose some dates/time.


## Meeting Wed, 18 May 2022, 7:00 am PT

Attending: Andreas Freund (EF/TreeTrunk), Tas Dienes (EF), Dan Shaw (EF), Pavel Sinelnikov (Metis), Will Harborne (Deversifi), Konrad (Deversifi), Kelvin Fichter (Optimism), Kyle Thomas (Provide)

Scribe: Dan Shaw

Proposed agenda
* Welcome, and a reminder of WG meeting rules
* Selection of scribe
* Introduction of new participants
* Discuss the list of new work items Tas brought back from Devconnect, plus any other items members want to bring up, decide to focus on 1 - 2 items with the greatest interest and open issues for them.
* Open Forum for other items

Notes from the meeting:

1. Welcome new members: 
 * Kelvin from Optimism - long time L2
 * Conrad, CTO Deversifi - running StarkEx
 * Pavel, Integration Lead at Metis
 * Will, Deversifi - Started on Starkware StarkEx, but now exploring multiple Layer 2s

2. New Work Items discussed in-person at DevConnect
 * Big thank you to Layer Two Amsterdam
 * Will expressed the need for something like IBC which allow roll-ups standard interfaces for ZK
 * Mass migration strategies
 * Tas suggested balancing ambitious projects like standardized interfaces with easier wins like token list
 * Token list
 * Pavel: Looking at EIP 4844 standard for optimistic roll-ups at Layer 2
 * Clarifying question: Do Roll-ups need a modification of EIP 4844?
 * Kyle +1 for interface. Maybe strawman for what the interface would look like. +1 for EIP 4844
 * Conrad cross L2 state changes. Something better than trust notifications.
 * Kelvin standard properly pricing transactions. The fee model, transaction structure, does not work across execution and call data at Layer 2. Standardize transaction format at Layer. Pay this much for execution and that much for call data. Related to EIP 4844.
 * Will asked Is the standard focused on developer experience or is there some other reason for this.
 * Kelvin responded that this would improve developer experience, reduce protocol complexity and overhead, and give a more consistent end user experience.
 * Andreas proposes account experience and wallet considerations at Layer 2. User hub to manage keys and create a portable identity. A generalized account model to provide a better user experience across L2s.
 * Will +1 on wallet proposal

3. Topic: who else should we be reaching out to to work on the projects that were discussed?
 * Aztec
 * Starkware
 * hermez / Jordi
 * Other Polygon folks working on roll-ups

4. Proposals in review

    1. Define L2 Interop Interface standards - engage crosschain working group
    2. Transaction fee - new ethereum transaction type with execution on Layer 2 and what data needs to be published to Layer 1
    3. Token list - mapping contract addresses to the 3-4 character representations. Need chain ID, an address and a code. Simple. No protocol changes. Quick win for standardization.
      * Noted that Multiple representations of the same thing push complexity up significantly
      * Andreas points out that this is like a CUSIP in traditional finance
    4. Standard wallet account representation that work across L2s

5. Delegation of tasks
 * Andreas will take the Wallet issue
 * Will will take the Interop Interface issue
 * Kelvin will take on transaction standard
 * Kelvin will ask Ben at Optimism to create the issue for token list

6. Andreas shared some background context around the Crosschain Interop WG and GPACT

7. Reminder to all new members to add themselves to project Contributor List: https://github.com/eea-oasis/L2/blob/main/CONTRIBUTING.md


## Meeting Wed, 4 May 2022, 7:00 am PT

Attending: Andreas Freund, Tas Dienes, Dan Shaw, David Katz, Samrat Kishor

Scribe: Samrat Kishor

Proposed agenda
1. Welcome, and a reminder of WG meeting rules
2. Selection of scribe
3. Introduction of new participants
4. Report on L2 relevant subjects and feedback on L2 WG launch from Devconnect -- Tas
5. Review of  A DeFi Conundrum: L2s are awesome but they still suck for real financial assets" [(here)](https://docs.google.com/document/d/1RCq9XfH8daEQ_djabRIkXXn0LBYdiNBUV9NiH5lZdT4/edit?usp=sharing) and discussion on content and where to publish
6. Discuss next steps on collaboration with EEA Cross-Chain Interop WG (see new issue on EEA WG Testing Run at the end of Q2 and call for participants) 
7. Open Forum for other items

Notes from the meeting:

Tas: Updates from L2 event at DevConnect Amsterdam:
- The L2 working group announced at DevConnect.
- Most of the major L2 platforms were present.
- General sense in the conversations was that the time is right for talking about standards.
- The group agreed on the fact that we need to follow up with them and explore ways to work together and hence find a way of working in asynchronous/synchronous ways. We could possibly use Slack.

Andreas appealed to the group to review the draft blog post on digital assets with residuals: https://docs.google.com/document/d/1RCq9XfH8daEQ_djabRIkXXn0LBYdiNBUV9NiH5lZdT4/edit?usp=sharing
The group collectively needs to take a look. Comments have been addressed from EEA and post this round of feedback the article will be ready to publish.

Andreas suggested that we need to join forces and have joint communication with the Interop working group. We can explore working with Anais to see if our working group can coordinate on outbound communication.

Andreas suggested that we should reach out to the L2 platforms like Socket and let them know about this working group. We should plan L2<->L2 interop testing their tech.

The group discussed about the user experience for new members and it was concluded that Giithub and Slack is the best place to land new members for this woking group.

A conversation ensued between John W and Andreas F about various growth and outreach strategies for this working group.

## Meeting Wed, 20 Apr 2022, 7:00 am PT

Postponed due to key participants attending DevConnect in Amsterdam.

## Meeting Wed, 6 Apr 2022, 1:30 pm PT

Meeting Assets:
- [Presentation](https://docs.google.com/presentation/d/1s7BiFPsOzkrqfdP52Fa9ryQxhCoQdtn_-eSbTRVd5EM/edit?usp=sharing)
- [Recording](https://us02web.zoom.us/rec/share/i-UqcjVTo9cgyZWwttASutqGgVvAzLZunLSn4PcAwL6vZhbTLthx-oX7BZCQnlL2.rqzVMsM4W_XqPu_-?startTime=1649277362000 (Passcode: ?3=53gNf))

Welcome, and a reminder of WG meeting rules. Selection of scribe: Brittany Mauck

Presentation by the EEA Interoperability WG on GPACT and digital assets with residuals with Q&A: Peter Robinson

Peter Robinson- I sent a link for participants to watch before this meeting. EEA L2 and Crosschain presentation was given. 

Crosschain Protocol Stack. Three separate layers:
- Crosschain Applications- Application code across blockchains. 
- Crosschain Function calls- Enables functions to be executed across blockchains. 
- Crosschain messaging: Enables events generated on one blockchain to be trusted on another blockchain. 

GPACT gives atomicity, multichains, return values, conditional logic, application authentication, gives good developer experience. 
The General Purpose Atomic Crosschain Transaction (GPACT) protocol is a call tree commitment scheme that provides atomic crosschain function calls for an arbitrary function tree. 

Sequence: Start- segment (getPrice)- segment (transfer)- segment (delivery)- segment (shipment)- root (executeTrade)- signaling (transfer)-signaling (delivery).
Execution Process: Start, Segment, Root, Signaling will go into Crosschain control and check whether it trusts the information coming in. Once trusted, you will call out to business function for the entry point function you have previously committed to. 

Andreas Freund- What happens when a contract state changes between commitment to the call tree and execution of the call tree that changes the function outcomes? would that not cause the execution tree failure? 

Peter Robinson- Correct. You can have a situation where the function changes due to state changes and overall transaction will fail. Front running is a well understood issue in blockchain. With crosschain calling, you use the same mitigation for front running. 

Chaals Nevile- Does the synchronicity have a stop rule, so you don't keep hanging forever?

Peter Robinson- You executed the segments in the leaf first, so you’ll hand in the segment from the function you are calling, and it has the return value so no waiting. 

Crosschain Messaging Layer- Only act on Ethereum Events that were emitted by transactions that are in blocks that are final. Finality depends on the chain.

zkRollups with EVM Capability Presentation- Peter looking for feedback on below presentation. 

zkRollup is run by the Operator. If the operator takes transactions and creates a batch, then have zero knowledge proof. Proof can prove you can go to old root hash to new root hash by verifying those transactions and anyone can verify. The user of the rollup will get a transaction receipt. 

zkRollups Operators can be slashed if they: 
- Maliciously sing a transaction receipt and do not include a transaction in the batch. 
- Maliciously sign an incorrect transaction. 

zkRollup Finality
- Immediate? When the zkRollup Operator returns the signed transaction receipt? 
- Once batch proof submitted to blockchain?
- Once blockchain transaction that batch proof was submitted in is final. 

Optimistic Rollups- based on a full proof window. Typically, one week. 

Crosschain Protocol Stack and Rollups
- Like other blockchains, it comes down to how to prove on a target chain that an event was emitted on a source chain and defining “final” for a source chain.

Andreas Freund- Do we then not have the same issues as with bridges if an attacker poses as a validator with a correct signature? 

Peter Robinson- If the attacker steals the zkRollup operator signature key, you are in trouble. If we are on Ethereum 2 for beacon chain and someone steals private keys, you are in trouble. It then comes down to operational security of the system. There are other ways of doing it to. 

Andreas Freund- You are not accepting new blocks until a block has been verified. The user has the escape hash option where they can extract the last valid state of their holding without operator. So, operators can’t steal your funds. You can pull funds out if you don’t like the operator. Even if private key is compromised, you can’t steal funds. 

Peter Robinson- Sounds good. 

Andreas Freund- How do you ensure the issuer doesn’t know that the bond is on the rollup? Not online, just submits the payment. 
Peter Robinson- Per the diagram, the payer calls the contract and it’s up to the people writing the business logic at application level to do the right thing. It’s a matter of solidity contract to do business logic.

Andreas Freund- The bridge contract needs to understand the type of transactions that are happening and then reach out to the bond contract and update the relationship there. That current functionality doesn’t exist.  

Weijia Zhang- Sequence can rearrange transaction which may impact the synchronization of crosschain, correct? 

Andreas Freund- Once committed to the block, that is final. Anything can happen on the L2. 

3.	ADJOURNMENT

This meeting was adjourned on Wednesday, 6 April 2022 at 5:30PM ET. 

**Attendance** 

| Member Company | Name | 
| ----------- | ----------- | 
| Accenture | Cody Burns | 
| Adhara Ltd | Coenie Beyers | 
| Blockdaemon | Fode Toure | 
| Clearmatics | Aiman Baharna | 
| Ethereum Foundation | Andreas Freund | 
| ConsenSys | Angela Potter | 
| ConsenSys AG | Ermyas Abebe | 
| ConsenSys AG | Lucas Saldanha |
| ConsenSys Software R&D | Peter Robinson | 
| Datachain | Susumu Toriumi | 
| EEA | Anais Ofranc | 
| EEA | Brittany Mauck | 
| EEA | Chaals Nevile | 
| EEA | James Harsh | 
| Ethereum Foundation | Dan Shaw | 
| Ethereum Foundation | Tas Dienes | 
| Wanchain | Weijia Zhang |
| Accenture | David Katz|


## Meeting Wed, 23 Mar 2022, 7 am PT

Attending: Andreas Freund, Tas Dienes, Anais Ofranc, Dan Shaw, Kyle Thomas, David Katz, Cody Burns, Samrat Kishor, John Wolpert

Scribe: Tas Dienes

Proposed agenda
1. Welcome, and a reminder of WG meeting rules
2. Selection of scribe
3. Introduction of new participants
4. Introduction and overview of GPACT protocol in preparation of April 6th meeting with Q&A / Discussion of applicability to L2 (Andreas)  
5. Open Forum for other items

Notes
1. No new members today
2. Numerous views but no comments so far on the Eth Magicians& ethresear.ch posts
3. Blog post on the problem of paying residuals for assets that have moved across chains is in progress.  Andreas et al will be meeting with EEA marketing to discuss publicizing it.
4. Anais mentioned this article [https://ethereum-magicians.org/t/outlining-a-standard-interface-for-cross-domain-erc20-transfers/6151. She offered to contact the contributors to see if they are interested in the above mentioned problem.  ACTION: Anais to contact them once a draft of the blog post is ready to share with them.](https://ethereum-magicians.org/t/outlining-a-standard-interface-for-cross-domain-erc20-transfers/6151)
5. Andreas presented on the GPACT protocol.  Peter suggested it could solve the problem of paying residuals for assets that have moved across chains. \
[https://docs.google.com/presentation/d/1KpsBI7lBI8WXk3xkcZ3_tucLmz5AUD12GH-e5q2pGac/edit?usp=sharing](https://docs.google.com/presentation/d/1KpsBI7lBI8WXk3xkcZ3_tucLmz5AUD12GH-e5q2pGac/edit?usp=sharing)
    1. It’s not clear yet how this could work in a privacy preserving system such as zk-zk-rollup
    2. GPACT group is aiming for limited interop testing at the end of Q2 or early Q3 with a few EEA members
6. John Wolpert suggested promoting this WG harder to the L2 projects.  Samrat will reach out to Polygon. Tas will contact Offchain Labs after the blog post can be shared.


## Meeting Wed, 09 Mar 2022, 7 am PT
Attending: Andreas Freund, Tas Dienes, Anais Ofranc, Dan Shaw, Samrat Kishor, Marco Cora

Scribe: Tas Dienes
Proposed agenda
Welcome, and a reminder of WG meeting rules
Selection of scribe
Introduction of new participants
Discuss collaboration between this WG and EEA Interop WG and next steps
Discuss next steps after Eth Magician and Eth Research Posts on our Workitem 1 (Bridging Digital Assets with Residuals) here
Open Forum for other items
Notes
Welcome to new members
There was a discussion between EEA Interop WG (Peter, Weijah) and this WG (Andreas, Anais, Dan).  EEA WGs cannot accept contributions from non-members. Trying to maximize sharing and collaboration across groups. Interop WG aims to start testing in Q2-Q3.  Andreas is planning to meet and discuss further April 6.  Andreas will provide an overview/review of the topic at the next meeting of this WG.
The Eth Magician and Eth Research Posts on our work item about interop for digital assets with residuals is out:
https://ethereum-magicians.org/t/interop-of-digital-assets-with-residuals-l1-l1-l1-l2-l2-l2/8519
https://ethresear.ch/t/interop-of-digital-assets-with-residuals-l1-l1-l1-l2-l2-l2/12156	
Andreas will promote on social media, others encouraged to publicize as well
Andreas will contact EEA marketing about publicizing the topic and collaboration with Interop WG
Andreas will contact Immutable about participating. 
Chair and vice-chair for this WG have been nominated, Chet sent out an email call for objections, which closes at the next meeting March 23.


## Meeting Wed, 23 Feb 2022, 7 am PT

Attending: Tas Dienes, Anais Ofranc, Dan Shaw, Marco Cora, Chaals Neville, Samrat Kishor, Cody Burns 

Scribe: Tas Dienes

Proposed agenda:
* Welcome, and a reminder of WG meeting rules
* Introduction of new participants
* Selection of scribe
* WG Governance
  * Nominations for Chair/Vice-Chair have closed. Discussion of best voting method. PROSPAL: Use e-Ballot administered by OASIS.	
  * Nominations for Maintainer group see Reminder above
* Discuss proposed Eth Magicians and Eth Research Posts on our Workitem 1 (Bridging Digital Assets with Residuals) here based on the posting by Peter Robinson (GPACT protocol) to this work item.
* Open Forum for other items

Notes
* Welcome to new members
* Anais discussed the EEA Crosschain Interoperability WG.  Documents will be made public in the next few weeks.
* Vote for chairs is coming up; will be run as an e-ballot by OASIS.  Reminder to new members to add themselves to the contributor list so they can vote.
* Discuss proposed Eth Magicians and Eth Research Posts on our Workitem 1.  Anais said that the EEA Crosschain Interop WG has already been working on a solution to this problem, and the work in development is expected to be made public in the next week or two. Some information and specs are also public already, including a proposed EIP to identify chains The group is anticipating reaching Interop Testing in Q2.  Further discussion is needed.  We will probably go forward with the post anyway, to raise awareness of the problem and solution(s), but after discussion with the Crosschain Interop WG.
* Noting that many participants here are EEA members so can participate directly in the EEA work. In addition, this group is a good mechanism to provide feedback to EEA, given good IPR policies, an informed group of participants who can provide relevant feedback and assess whether the current proposals meet the needs of L2.
* Meetings will switch to biweekly.  Next is March 9.  Andreas to send an updated invitation.


## Meeting Wed, 16 Feb 2022, 7 am PT

Attending: Dan Shaw, Tas Dienes, Samrat Kishor

Scribe: Tas Dienes

Proposed agenda:
* Welcome, and a reminder of WG meeting rules
* Introduction of new participants
* Selection of scribe
* WG Governance
  * Nominations for Chair/Vice-Chair (to present WG at PGB meetings) see Reminder above
  * Nominations for Maintainer group see Reminder above
* Discussion on meeting times and frequency (PROPOSAL: Biweekly starting after our next meeting)
* Final Review of proposed Eth Magician and Eth Research Posts on our Workitem 1 (Bridging Digital Assets with Residuals) here and publishing schedule.
* Open Forum for other items

Notes
* Reminder about Doodle poll for meeting times https://doodle.com/poll/g64z5hbmsfcfbf57?utm_source=poll&utm_medium=link  
* Reminder about last call for vice-chair of the group. After the meeting, we will ask OASIS to send out a voting ballot to the WG members
* Call for maintainers to nominate themselves
* Andreas is working on Eth Magician and Eth Research Posts on our Workitem 1 (Bridging Digital Assets with Residuals) here
* Meeting schedule will move to biweekly starting in March. Next meeting Feb 23, then March 9.  Agreed by unanimous consent.


## Meeting Wed, 9 Feb 2022, 7 am PT

Attending: Andreas Freund, Tas Dienes, Dan Shaw, Samrat Kishor, Cody Burns, David Katz

Scribe: Dan Shaw 

Proposed agenda:
* Welcome, and a reminder of WG meeting rules
* Introduction of new participants
* Selection of scribe
* WG Governance: Revisit
* Nominations for Chair/Vice-Chair (to present WG at PGB meetings)
* Nominations for Maintainer group
* Review content for Eth Magicians and Eth Research post
* Issue & PR review
* Open Forum

Notes:
* No new participants today
* Andreas Freund has been nominated for Chair.
* Dan Shaw has been nominated for Vice Chair.
* More nominations are welcome.
* Andeas reviewed the planned Ethresearch and EthMagicians posts.
  * L2/Sidechain <-> L1 and L2/Sidechain <-> L2/Sidechain Bridging Digital Assets with Residuals - #6 on L2 WG GitHub
  * Discussion
  * Andreas surmises that the assets described cannot be transferred with integrity
  * Cody asks who can help us solve this?
  * Dan proposes pulling in some finance expertise to inform a technical solution
  * Cody proposes that the technical solution looks like transferring private keys between parties.
  * Like changing the ownership of a bank account
  * Andreas will send out an email to gather another round of feedback with the objective of posting next week.

Meeting adjourned

## Meeting Wed, 2 Feb 2022, 7 am PT

Attending: Andreas Freund, Tas Dienes, Dan Shaw, Samrat Kishor, Kyle Thomas, David Katz, Marco Cora

Scribe: Tas Dienes

Proposed agenda:
* Welcome, and a reminder of WG meeting rules
* Introduction of new participants
* Selection of scribe
* WG Governance: Revisit
* Nominations for Chair/Vice-Chair (to present WG at PGB meetings)
* Nominations for Maintainer group
* Issue and PR review
  * Currently only one Issue: L2/Sidechain <-> L1 and L2/Sidechain <-> L2/Sidechain Bridging Digital Assets with Residuals
* Open Forum for other topics

Notes
* Nominations
  * Dan Shaw nominated himself for chair or vice-chair
  * Samrat and John Wolpert nominated Andreas as chair
  * Andreas nominated Dan Shaw as vice-chair
  * David and Kyle nominated themselves as maintainers
* Andreas to inquire with OASIS about how to conduct the vote
* Discussion of Issue #6 -  L2/Sidechain <-> L1 and L2/Sidechain <-> L2/Sidechain Bridging Digital Assets with Residuals
  * Andreas would like to post on ethresear.ch and ethereum-magicians.org
  * Input from other teams is requested
  * Andreas will start working on a blog post - Marco and Kyle agreed to be co-authors. David wants to dive deeper into the subject matter before committing.


## Meeting Wed, 26th Jan 2022, 7 am PT

Attending: Andreas Freund, Tas Dienes, Dan Shaw, John Wolpert, Samrat Kishor, Cody Burns, David Hatz, Marco Cora (new), Rahul Sethuram (new)

Scribe: Dan Shaw

Proposed agenda:
* Welcome, and a reminder of WG meeting rules
* Introduction of new participants
* Selection of scribe
* Review of new Github repo etc.
* WG Governance
* Nominations for Chair/Vice-Chair (to present WG at PGB meetings)
* Nominations for Maintainer group
* Discuss initially selected work items, and next steps
* Use Cases: Digital Assets with Residuals
* Technical: Precompiles for L1 -> L2 Onboarding
* Requirements: Privacy requirements while maintaining security
* Open Forum for other items

### Notes

Reminder to use Q+ in chat if you have a question.
Vote +1/-1
Rough consensus followed by group.

Marco Cora of Matter Labs, creator of ZKSynk, introduced himself.

Rahul Sethuram, CTO and Co-founder of Connext, bridging L2 and L1s. Invited by Kyle Thomas of Provide.

Andreas introduces WG GitHub, Slack, and Mailing List
* GitHub: https://github.com/eea-oasis/L2 -> add yourself, if you haven’t already
* Slack invite link: https://join.slack.com/t/eeacommunityp-kte2307/shared_invite/zt-120jtrzs2-zOVQ5PJi3cYmt27VlV33NQ
* Mailing group link:  https://lists.oasis-open-projects.org/g/eea-cp-l2
* Mailing group email: eea-cp-l2@lists.oasis-open-projects.org

Minutes will still be mailed out every week after the minutes have been PRed into the WG repo.

Andreas reviewed the WG work items.

Call for nominations for Chair and Vice Chair
* Duties:
   * Prepare agenda
   * Manage Minutes
   * Represents WG at EEA Community Project PGB (Project Governing Board)
     * Meets bi-weekly
     * Chair or Vice-Chair should attend

Call for nominations for Maintainers / Code Owners
Current nominations are Andreas Freund and Kyle Thomas

WG has a Doodle poll to validate best times for meeting. WG is considering alternating meeting times to include a broader group of participants.
* Next week we will stick with 7am PT / 10am PT
* West Coast folks register their bleary votes that 7am is rough

Initial discussion of work items
* Digital assets with residuals L2 to L1 and back
  * Rahul shared how the team explored creating a rebased token to make a normal ERC-20.
  * Cody laid out how an asset with residuals could be abused if the asset were moved off L1 to an L2 and back to L1.
  * Andreas will PR the proposal for the work item to the repo.
  * Andreas asked the group about the scenario when a token owns another token.
* Moving forward these working item will be the primary discussion topic for the group.

Discussion of Baseline Protocol as a potential solution for data moving back and forth from L1 to L2.

John Wolpert proposes creating a WG promotion sub-committee to get the word out.

Meeting adjourned


## Meeting Wed, 19th Jan 2022, 7 am PT

Attending: Andreas Freund, Tas Dienes, Samrat Kishore, Cody Burns, Matthias Geihs, David Katz, Sebastian Stammler, Kyle Thomas

Scribe: Tas Dienes

Proposed agenda:
* Welcome and reminder of the WG rules
* Introduction of new members
* Selection of Scribe
* Update on OASIS WG infrastructure set-up and required steps from the WG e.g. selection of chairs
* Discussion of suggested approach to alternate meeting times
* Discussion on Work Items and selecting at least one work item to begin work

### Notes
New members: Matthias Geihs from Perun, working on state channels with Sebastian Stammler; David Katz from Accenture

Github repo has been set up https://github.com/eea-oasis/general-L2-scalability

Repo name will be changed to “L2”.  

Kyle proposes to be an admin.  Motion approved. 

Contributors will have to add themselves to the readme.md file via a PR
Directories for work items and docs will be created

Andreas and Kyle will be initial maintainers who can approve PRs.  PRs require 2 approvals.

Chair and vice-chair need to be chosen; AF to call for nominations by email.

Doodle poll for new meeting time(s) has been sent out 

Slack will be set up by AF, starting with a business account 

Work item discussion.  We will start with these. AF to create folders.
* “Managing assets with residuals” 
* “Precompiles of most common L2 onboarding or exit functions to reduce L2 gas costs”
* “Layer 2 privacy guarantees that do not compromise on security”


** Meeting Wed, 12th Jan 2022, 7 am PT

Attending: Andreas Freund, Tas Dienes, Dan Shaw, John Wolpert, Samrat Kishore, Alim Karim
Scribe: Tas Dienes

Proposed Agenda:
* Welcome and rules reminder
* Selection of Scribe
* Introduction of new members
* Next steps to set up WG with OASIS (Github, Gitbook etc.)
* Review, prioritize and select the first work items to work on and the first timelines for delivery based on our existing work item list.

### Notes
The project has been approved by PGB!  

Next, request OASIS to create a github repo, and select maintainer(s).  Then add charter and governance docs to the repo, readme.md.
Discussion of the work item list

JW suggests defining what is not an L2 and what is not

JW asks if we need a new “L2IP” standards system or use EIP system. The consensus is that we can probably use EIP system for now.

How to increase attendance:
Consider alternating between two times  
Tas is to create a Doodle poll 

Contact potential participants 1 on 1, mention proposed work items, ask if a different meeting would help

In emails to the group, consider BCCing people who have expressed interest but don’t show up regularly 

## Meeting Wed, 15th Dec 2021, 7 am PT

Attending: Andreas Freund, Tas Dienes, John Wolpert, Bobbin Threadbare (Polygon Miden), Ravikant Agarwal (Polygon)

Scribe: Tas Dienes

### Notes
Governance doc status - resolving comments from Chaals (EEA).  Will be discussed in tomorrow’s EEA Community Project PGB meeting.

Bobbin Threadbare introduction.  

Reviewed work item brainstorming doc.

Next meeting is on January 12th

## Meeting: Wed, 8th Dec, 2021, 7 am PT / 10 am ET / 16:00 BST

Scribe: Tas Dienes

Proposed Agenda:
* Selection of Scribe
* Introduction of new participants
* Meeting Minute Corrections (if required)
* Update from the EEA Community Projects' Project Governance Boards meeting with regard to their feedback a-on Charter and Governance Document (TL/DR: WG is good to go to start working. Just some clarifying minor edits/additions -- will review those during our meeting. Nothing substantial)
Review Workitem Backlog document --   https://docs.google.com/document/d/1AzcuzBNkeQUGJ3EbtaxNHRmq91fSjAspBak26wZjSRo/edit?usp=sharing
 
Attendees: Andreas, Tas, Samrat, Kyle, Dan Shaw, Cody Burns, Alim Karim, Julien Marchand, Kartheek Solipuram

Tas volunteered to scribe

No new participants

Governance doc
https://docs.google.com/document/d/1MNl3jjR5EJF3xM5QSteslklVJUKKEPCP7wHaTxSSK8c/edit?pli=1

Minor edits made to governance doc based on feedback from Dan Burnett.

The WG is also the TSC

We can switch the license from CC0 to Apache 2.0 - but Kartheek is going to check with EY legal about this

Charter doc
https://docs.google.com/document/d/16LZluUzG0RSHpVpYiXVucibv_A7ZWN0GZQvvfW21tiQ/edit?pli=1

Edits made to governance doc based on feedback from Dan Burnet and others.
PGB is expected to vote on these when all comments are resolved. Aim to have them approved by end of the year.

Work items
https://docs.google.com/document/d/1AzcuzBNkeQUGJ3EbtaxNHRmq91fSjAspBak26wZjSRo/edit?pli=1#heading=h.n59e8xyug3dx

Kyle brought up virtualizing a L2 - containerized version of an L2 with a generalized interface. Unified interface application facing API.

Ideas from Vitalik - Tas to add to work item list 
* Standard or recommendation for transitioning from a sidechain to a true L2
* Support the L2 ENS effort, and make sure every dapp that supports ENS also supports it
* L2 state data availability backup 

Kyle will work on item 2b 

Andreas and Alim will work on 4b

NFTs/NFT transfer? NFT royalties cross-chain - Kartheek is interested in working with Andreas on this. Kyle too. 

Next meeting December 15, then January 12.  AF will send cancellations for 3 weeks in between.

## Meeting: Wed, 17th Nov, 2021, 7 am PT / 10 am ET / 16:00 BST

Scribe: Dan Shaw

Attending: Andreas, Tas Dienes, Dan Shaw, Chet Ensign,
Alim Karim,
Karthik Solimpuram,
Samrat Kishor,
Sandeep Nailwal, Polygon (new member),
Samrat Kishor,
Sebastian Stammler,
Steven Goldfeder

Andreas introduces Chet Ensign of OASIS.

Chet is the point of contact with the OASIS staff who is responsible for facilitating participants.

Explains the rules

Find a way to complete the work

OASIS has been involved in Open Source and OPEN Standards since 1993. Ensure IPR. Ensure correct voting procedures.

OASIS is particularly beneficial when the work you’re working on is desired to be an international standard.

Chet notes changes to how folks are building things. Open Source now exceeds Open Standards as a starting point. Provides open source work a path to standards. Most projects want to start as an Open Project. EEA retains the brand, governed by the OASIS process.

EEA Open Projects is the umbrella group for Baseline Protocol, JSON

The project chair reports regularly to the EEA Community Projects project governing board (PGB).

Benefits: Projects get both the EEA stamp of approval and the OASIS stamp of approval. You can determine what goes forward as an OASIS standard. OASIS can steward the standardization process through a number of international standards bodies.

Process for PGB approval: likely within 2 weeks.

Thank you, Chet.

7:25: Sandeep Nailwal representing Polygon introduces himself and provided an overview of Polygon’s offerings, involvement in the ecosystem, and interest in Layer 2.

7:30: Back to the governance review

A suggestion has been made to consider changing the license from CC0 1.0 Universal to Apache 2.0. Apache 2.0 is the default for EEA Community Projects. Chet Ensign noted that CC0 is needed by companies like EY and Accenture (organizations with audit departments).

Sebastian expressed concern that CC0 might deter some contributors from engaging with the project since it is an unknown license.

Chet asks if there were any explicit objects to Apache 2.0 as the license.

Kartheek will check with EY legal to make sure if the project only produces specification text that Apache 2.0 will be OK.

Sebastian expresses concern that solidity interface files might not be adopted if they are using the CC0 license.

No objections were made to the improved definition of the “substantial” participation requirement for working group membership.

Decision-Making Process was reviewed and ratified without objection.

The ratification Process was reviewed and ratified without objection.

Andreas called for final objections. None were made. The governance doc will be submitted with a known open issue for final license selection between CC0 and Apache 2.0, both of which are approved licenses.

From Chat:

Alim: Andreas — re. License — on my side checking with the VMW legal team as well for our participation. Expect to have an answer by next week.

Action Items:
* Kartheek: To check with EY legal to make sure if the project only produces specification text that Apache 2.0 will be OK 
* Alim: To check with the VMW legal team as well for our participation. Expect to have an answer by next week.
* Tas (as PGB member): Submit Charter and Governance doc for approval to EEA - OASIS PGB during next PGB meeting; Status: Submitted awaiting a decision on 1st of December meeting.

## Meeting: Wed, 10th Nov, 2021, 7 am PT / 10 am ET / 16:00 BST

Canceled due to lack of attendance.

## Meeting: Wed, 3rd Nov, 2021, 7 am PT / 10 am ET / 16:00 BST

Participants: Alim (VMWare), Cody (Accenture), Robert (ConsenSys), Julien (ConsenSys), Kyle (Provide), Samrat (Golden Next Ventures), Sebastian (Perun), Tas (Ethereum Foundation), Dan (Ethereum Foundation), Andreas (Ethereum Foundation), 

11/3 Meeting Agenda
* Previous Meeting Notes Corrections (if required)
* Introduction of new participants
* Selection of Scribe
* Continue Review of WG Charter (continuing with Key Stakeholders Section)
* Start WG Governance Draft Review

* Action items from 11/3 WG meeting
* Action item: WG members to review & provide feedback on any headlines/sections missing from governance doc
* Action item: WG members to review details of sections in governance doc
* Action item: Andreas to invite Chad from OASIS to the next meeting to give feedback on charter, governance & license (CC0)

1. Review & Correction of notes from the last meeting
Notes for this meeting will include corrections from Samrat

2. Intro of new members
Kyle, Alim, Julien
3. Selection of Scribe for this meeting
Alim
4. Review of WG Charter

4.1 Stakeholder section

Sponsors definition - intended to be organizational supporters of this WG. Sponsors don't have other commitments other than favorable PR mention.

Sponsors of EEA Community Projects indirectly are sponsors of this initiative - to be added into Stakeholder section

Chains this WG will focus on

Definition: Which chains are we actively writing standards for?
Focus on public blockchains, add specificity by targeting EVM compatible chains so that standards developed are not overly generic

Team members

Keep as a rolling list as orgs join

4.2 WG milestones - 2021

Reviewed milestones in doc

Launch -- done

Charter by mid-Nov -- on track

Success metrics for WG by EO Nov -- on track

Kick off one workstream by EO 2021 --

Goals:

Added goal #6 ("Facilitate interoperability between different applications ...") based on the last WG discussion.

Refine wording to include environment/tooling aspects

List of L2 projects out there?

Published by EEA (authored by Andreas) this week.

L2 beat.

4.3 Budget
N/A at this time

4.4 Constraints

Constraints
WG members are
Proposal: Lean/agile standards development - smaller initiatives with frequent delivery. Example: defining smart contract input/output standards. No objections to this.

Assumptions
EVM-compatible was added as an assumption.
Risks & Dependencies
No changes

Charter doc walkthrough & edits complete

Governance Doc (link):

Doc originated from Baseline governance doc
Action item: WG to provide feedback on any headlines/sections missing from governance doc

Decision: Will run current doc by the OASIS representative on the PGB to get early feedback

License and Patent Policies

Repo to be provided by OASIS free of charge

Once this is an official working group in the EEA, members will have to sign entity (org contribution) and individual CLAs (community contribution)
Code of conduct

Linked to Baseline Code of Conduct. Reviewed pledge & other sections.
WG members to review and agree on the code of conduct linked in Governance Doc. Applies to other sections as well.

License:
Creative Commons License: CC0 - Overview provided by Andreas, key point: all contributors pledge they're not going to sue anyone for the code/IP, it's their IP, give up right to sue anyone that is using this IP within the established context of newly created IP. A commercial product could be built from

Apply to all code created by this group or specific repos? Any contributions/PRs fall under this license.

* Action item: Andreas to invite Chad from OASIS to the next meeting to give feedback on charter, governance & license (CC0)
No objections to this license model

The Working Group:

WG initial members - anyone that signs the charter is eligible to participate and pledges to contribute, bound by governance, etc. WG addition - same process as initial members i.e. signing charters. Non-members can lurk but only members that have signed can contribute & be vote-eligible. Added "and signed charter" to the WG section.

Decision-making process:

The section is lengthy & will require discussion. Skipped for the next session.

Contributors
No comments/changes

Maintainers

Contributions

Ratification

no comments/changes
--------------------------------------------------

## Updated Meeting Minutes: Meeting: Wed, 27th Oct, 2021, 7 am PT / 10 am ET / 16:00 BST

Changes: 
* Corrected Smart's Company Name to Golden Next Ventures
* Added Scribe
 
Scribe: Imran

Participants:
John Wolpert (Consensys), Samer Falah (J.P. Morgan), Imran Bashir (J.P. Morgan),  Andreas Freund (QLC Chain), Tas (Ethereum Foundation), Dan Shaw (Ethereum Foundation), Samrat Kishor (Golden Next Ventures), A.J. Warner (Arbitrum), Sebastian Stammler (Perun), San Safai (Perun), Bruno Maia (Cartesi), Steven Goldfeder (Arbitrum), Kartheek Solipuram (Ernst & Young), Julien Marchand (Consensys), Cody Burns (Accenture)

Introductions:
1. Tas: standards development, risks of the ecosystem, mitigate risks, L2 interoperability
2. Dan Shaw: year and a half, helping enterprises for Mainnet adoption, it turns out that enterprises need L2. focused on enterprise adoption, and expectations from enterprise
3. Sam: This is an interesting topic. We should focus on performance, scalability, and privacy with L2, looking for a Layer 2 solution. Focus on industry standards and ensure scalability. We can engage existing projects too.
4. John Wolpert: chair of baseline protocol / Oasis, baseline protocol is a new standard for coordination under zero-knowledge, have a clear framework to ensure following standards, shouldn’t require things like state machine to do coordination
5. Samrat Kishor: L2 is the next wave of growth, strategy background, baseline community, technical steering committee. regional head of EEA for India
6. Sebastian Stammer  (Perun): academic background, a group doing state channels, from the technical university of Darmstadt
7. AJ Warner: from Arbitrum :
8. Sasan Safai : from Perun,
9. Bruno Maia: from Cartesi, excited to see what this group will bring to standards and interoperability.
10. Steven Goldfeder - optimistic rollup, Arbitrum, CEO Arbitrum , working with different enterprise
11. Kartheek Soluipuram - at EY, solution architecture, baseline protocol. EY scalability and privacy, a family of layer 2 solutions, nightfall, keen on how to standardize
12. Julien Marchand - Consensys - zk-rollups , happy to be here,
13. Robert Drost, (16502792061 - ) R&D effort at Consensys mesh , L1 and L2 protocols, largely around state channels
14. Andreas Freund – active in the blockchain ecosystem, lead author of baseline protocols standards, was at Consensys.  Worked on ZK-rollup, apply learnings from baseline to large ecosystem for scalability, what looks sensible for the enterprise, very excited to be here.
 
Minutes:

Andreas: described meeting rules which were emailed earlier
- Have a transcriber on a rotating basis to take notes, post them in the channel, if the meeting is recorded, notes are automatically recorded
- Scribe required
- Meeting rules described
- Governance emailed
- Rules: everyone to be kind, for the betterment

Cody burns: introduction . . ., from Accenture

Andreas: question to the group, is everyone OK with meeting rules

Andreas: charter of the group. Two ways, quick review, share screen, Q&A session, specific questions, went through the charter. Available at google docs (insert link)

Tas: I like goals, but standards should be mentioned more explicitly.

Samrat: should we include ESG?

Andreas:  probably we can

Bruno: good idea,

Samrat: Blockchains consume a lot of  energy and generate carbon .. Standardize to switch to greener protocols

Sam: I will comment on ESG after but  scalability is the main focus and we should focus on privacy and performance as well … ESG is not our core focus at this point

Bruno: ESG could be the indirect result . . .  I believe that we should align early to  ESG

Samrat: we can add it later if clearer goal in future

Andreas: Leave ESG as an open topic

Tas: Added a suggestion, facilitating interoperability  among different L2s and L1s, and developing appropriate standards

Andreas: ESG should be incorporated now? Poll taken? Some +1s

Cody: intro: Accenture blockchain, metaverse, identity, happy to work on L2

Andreas: read Scope from the google docs document

Samrat: where is this initiative going, would L2 will evolve into Layer 3.

Andreas: go with the flow... We’ll see

Bruno: good question, the difference between L2 and L3, L2 on top of sidechain, it can be named as layer 3

Andreas: recited scope in the charter

John Wolpert: if this group works under EEA, then participants must be members of EEA, otherwise if OASIS then it can be open,  need some money from sponsors, if OASIS route: add some cash, as it’s a community project, if under EEA: grants can be given . .  Emphasized coordination issues when it comes to money and grants.

Andreas: agree with John, however, once something significant is produced. Then donation bucket can be passed around at that time

John: it's serious business .   . .

Andreas: True

John: I’ll rest here

Andreas: Segway, to WG chains

Andreas: proposal for WG chains

Andreas: park that item for next week,  discuss it at next week’s meeting, thank you for a great meeting

Meeting adjourned
