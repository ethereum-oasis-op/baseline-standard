
![OASIS Logo](http://docs.oasis-open.org/templates/OASISLogo-v2.0.jpg)
-------

# Baseline API and Data Model Version 1.0

## Project Specification Draft 01

## 17 September 2021

<!-- URI list start (commented out except during publication by OASIS TC Admin)

#### This stage:
https://docs.oasis-open.org/baseline/baseline-api/v1.0/psd01/baseline-api-v1.0-psd01.md (Authoritative) \
https://docs.oasis-open.org/baseline/baseline-api/v1.0/psd01/baseline-api-v1.0-psd01.html \
https://docs.oasis-open.org/baseline/baseline-api/v1.0/psd01/baseline-api-v1.0-psd01.pdf

#### Previous stage:
N/A

#### Latest stage:
https://docs.oasis-open.org/baseline/baseline-api/v1.0/baseline-api-v1.0.md (Authoritative) \
https://docs.oasis-open.org/baseline/baseline-api/v1.0/baseline-api-v1.0.html \
https://docs.oasis-open.org/baseline/baseline-api/v1.0/baseline-api-v1.0.pdf

URI list end (commented out except during publication by OASIS TC Admin) -->

#### Open Project:
[Baseline, part of the EEA Community Projects](https://www.baseline-protocol.org/)

#### Project Chair:
John Wolpert (john.wolpert@mesh.xyz), [ConsenSys](https://consensys.net/) 

#### Editors:
Kyle Thomas (kyle@provide.services), [Provide Technologies](https://provide.services/), \
Daven Jones (daven@provide.services), [Provide Technologies](https://provide.services/), \
Andreas Freund (a.freundhaskel@gmail.com) \
Anais Ofranc (aofranc@consianimis.com), [Consianimis](https://www.consianimis.com/) 

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
* _Baseline Protocol v0.1_ - https://github.com/ethereum-oasis/baseline/tree/master/**Example:**s/bri-1
* Specifications replaced by this specification (include hyperlink, preferably to HTML format)
 -->

This specification is related to: \
**[baseline-core-v1.0]**
_Baseline Core Specification Version 1.0_. Edited by Andreas Freund and Anais Ofranc. 17 September 2021. OASIS Standard. https://docs.oasis-open.org/baseline/baseline-core/v1.0/psd01/baseline-core-v1.0-psd01.html. Latest stage: https://docs.oasis-open.org/baseline/baseline-core/v1.0/baseline-core-v1.0.html. \
**[baseline-dlt-v1.0]**
_Baseline CCSM Requiements Version 1.0_. Edited by Andreas Freund and Anais Ofranc. 17 September 2021. OASIS Project Specification Draft 01. https://docs.oasis-open.org/baseline/baseline-dlt/v1.0/psd01/baseline-dlt-v1.0-psd01.html. Latest stage: https://docs.oasis-open.org/baseline/baseline-dlt/v1.0/baseline-dlt-v1.0.html.


#### Abstract:

This document describes the Baseline programming interface and expected behaviors of all instances of this interface together with the required programming interface data model.

#### Status:
This document is under active development and implementers are advised against implementing the specification unless they are directly involved with the Baseline TC team.
Comments on this work can be provided by opening issues in the project repository or by sending email to the project’s public comment list baseline@lists.oasis-open-projects.org.


#### Citation format:
When referencing this specification the following citation format should be used:

**[baseline-api-v1.0]**

_Baseline API and Data Model Version 1.0_. Edited by Kyle Thomas, Daven Jones, Andreas Freund and Anais Ofranc. 17 September 2021. OASIS Standard. https://docs.oasis-open.org/baseline/baseline-api/v1.0/psd01/baseline-api-v1.0-psd01.md . Latest stage: https://docs.oasis-open.org/baseline/baseline-api/v1.0/psd01/baseline-api-v1.0-psd01.md .

-------

## Notices
Copyright © OASIS Open 2021. All Rights Reserved.

All capitalized terms in the following text have the meanings assigned to them in the OASIS Intellectual Property Rights Policy (the "OASIS IPR Policy"). The full  [Policy](https://www.oasis-open.org/policies-guidelines/ipr/) may be found at the OASIS website.
This document and translations of it may be copied and furnished to others, and derivative works that comment on or otherwise explain it or assist in its implementation may be prepared, copied, published, and distributed, in whole or in part, without restriction of any kind, provided that the above copyright notice and this section are included on all such copies and derivative works. However, this document itself may not be modified in any way, including by removing the copyright notice or references to OASIS, except as needed for the purpose of developing any document or deliverable produced by an OASIS Technical Committee (in which case the rules applicable to copyrights, as set forth in the OASIS IPR Policy, must be followed) or as required to translate it into languages other than English.

The limited permissions granted above are perpetual and will not be revoked by OASIS or its successors or assigns.

This document and the information contained herein is provided on an "AS IS" basis and OASIS DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE.

OASIS requests that any OASIS Party or any other party that believes it has patent claims that would necessarily be infringed by implementations of this OASIS Committee Specification or OASIS Standard, to notify OASIS TC Administrator and provide an indication of its willingness to grant patent licenses to such patent claims in a manner consistent with the IPR Mode of the OASIS Technical Committee that produced this specification.

OASIS invites any party to contact the OASIS TC Administrator if it is aware of a claim of ownership of any patent claims that would necessarily be infringed by implementations of this specification by a patent holder that is not willing to provide a license to such patent claims in a manner consistent with the IPR Mode of the OASIS Technical Committee that produced this specification. OASIS may include such claims on its website, but disclaims any obligation to do so.

OASIS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this document or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on OASIS' procedures with respect to rights in any document or deliverable produced by an OASIS Technical Committee can be found on the OASIS website. Copies of claims of rights made available for publication and any assurances of licenses to be made available, or the result of an attempt made to obtain a general license or permission for the use of such proprietary rights by implementers or users of this OASIS Committee Specification or OASIS Standard, can be obtained from the OASIS TC Administrator. OASIS makes no representation that any information or list of intellectual property rights will at any time be complete, or that any claims in such list are, in fact, Essential Claims.

The name "OASIS" is a trademark of OASIS, the owner and developer of this specification, and should be used only to refer to the organization and its official outputs. OASIS welcomes reference to, and implementation and use of, specifications, while reserving the right to enforce its marks against misleading uses. Please see https://www.oasis-open.org/policies-guidelines/trademark for above guidance.

-------

# Table of Contents
[1 Introduction](#1-introduction) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.1 Overview](#11-overview) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.2 Glossary](#12-glossary) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.3 Typographical Conventions](#13-typographical-conventions) \
[2 Design and Architecture](#2-design-and-architecture) \
[3 API](#3-api) \
&nbsp;&nbsp;&nbsp;&nbsp;[3.1 Org Management](#31-org-management) \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3.1.1 IRegistry](#311-iregistry) \
&nbsp;&nbsp;&nbsp;&nbsp;[3.2 Messaging](#32-messaging) \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3.2.1 IMessagingService](#321-imessagingservice) \
&nbsp;&nbsp;&nbsp;&nbsp;[3.3 Security](#33-security) \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3.3.1 IVault](#331-ivault) \
&nbsp;&nbsp;&nbsp;&nbsp;[3.4 Agreement Execution](#34-agreement-execution) \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3.4.1 IBaselineRPC](#341-ibaselinerpc) \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3.4.2 IBlockchainService](#342-iblockchainservice) \
&nbsp;&nbsp;&nbsp;&nbsp;[3.5 Privacy](#35-privacy) \
&nbsp;&nbsp;&nbsp;&nbsp;[3.6 Persistence](#36-persistence) \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3.6.1 IPersistenceService](#361-ipersistenceservice) \
&nbsp;&nbsp;&nbsp;&nbsp;[3.7 API Metadata](#37-api-metadata) \
[4 Data Model](#4-data-model) \
&nbsp;&nbsp;&nbsp;&nbsp;[4.1 Org Management](#41-org-management) \
&nbsp;&nbsp;&nbsp;&nbsp;[4.2 Messaging](#42-messaging) \
&nbsp;&nbsp;&nbsp;&nbsp;[4.3 Security](#43-security) \
&nbsp;&nbsp;&nbsp;&nbsp;[4.4 Agreement Execution](#44-agreement-execution) \
&nbsp;&nbsp;&nbsp;&nbsp;[4.5 Privacy](#45-privacy) \
&nbsp;&nbsp;&nbsp;&nbsp;[4.6 Persistence](#46-persistence) \
[5 Security Considerations](#6-security-considerations) \
[6 Conformance](#6-conformance) \
&nbsp;&nbsp;&nbsp;&nbsp;[9.1 API and Data Model Minimal Conformance Level]() \
&nbsp;&nbsp;&nbsp;&nbsp;[9.2 API and Data Model Conformance Level]()\
[Appendix A.        Acknowledgments]()\
[Appendix B.        Revision History]()

-------

# 1 Introduction

The Baseline Protocol is an open-source initiative that combines advances in cryptography, messaging, and consensus-controlled state machines often referred to as blockchains or distributed ledger technology (DLT) to deliver secure and private business processes at low cost -- event ordering, data consistency, and workflow integrity. The Baseline Protocol provides a framework that allows Baseline Protocol Implementations (BPIs) to establish a common (business) frame of reference enabling confidential and complex (business) collaborations between enterprises without moving any sensitive data between traditional Systems of Record. The work is a [Ethereum Community Project](https://github.com/ethereum/oasis-open-project), which is managed by [OASIS](https://oasis-open-projects.org/).

## 1.0 IPR Policy

The Baseline Protocol API Specification is provided under the [RF on Limited Terms](https://www.oasis-open.org/policies-guidelines/ipr/#RF-on-Limited-Mode) Mode of the OASIS IPR Policy, the mode chosen when the Technical Committee was established.

For information on whether any patents have been disclosed that may be essential to implementing this specification, and any offers of patent licensing terms, please refer to the Intellectual Property Rights section of the TC’s web page (https://www.oasis-open.org/committees/legalruleml/ipr.php).

## 1.1 Terminology

The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be interpreted as described in [RFC2119](https://datatracker.ietf.org/doc/html/rfc2119).

## 1.2 Normative References

## 1.4 Glossary

**Anti-Money Laundering:**

Anti-money laundering (AML) refers to a set of laws, regulations, and procedures intended to prevent criminals from disguising illegally obtained funds as legitimate income.  

International Monetary Fund, Reference Guide to Anti-Money Laundering and Combating the Financing of Terrorism Second Edition and Supplement on Special Recommendation IX, 2006

**Baseline Protocol:**

The Baseline Protocol is a set of methods that enable two or more state machines to achieve and maintain data consistency, and workflow continuity by using a network as a common frame of reference. 

**Baseline-Bridge:**

A mechanism for one Workflow to use the proof generated by a different Workflow.
to use a proof generated in a Workflow executed by Workgroup A as input to a Workflow executed by Workgroup B.

**Baseline-Connector:**

An interface connecting and synchronizing a baseline stack and system of record.

**Byzantine Fault Tolerant (BFT):**

Given a network or system of n components, t of which are dishonest, and assuming only point-to-point channels between all the components, then whenever a component A tries to broadcast a value x such as a block of transactions, the other components are permitted to discuss with each other and verify the consistency of A's broadcast, and eventually settle on a common value y. The system is then considered to resist Byzantine faults if a component A can broadcast a value x, and then:
* If A is honest, then all honest components agree on the value x.
* If A is dishonest, all honest components agree on the common value y.

"The Byzantine Generals Problem", Leslie Lamport, Robert E. Shostak, Marshall Pease, ACM Transactions on Programming Languages and Systems, 1982

**Circuit Breaker:**

The ability of a Party to immediately cease all their active Workflows across all of their Workgroups within a Baseline-compliant implementation, and, if required, exit a Baseline-compliant implementation with all their data without any 3rd party being able to prevent the exit.

**Common Frame of Reference:**

A Common Frame of Reference as used in this document refers to achieving and maintaining data consistency between two or more Systems of Record using a consensus-controlled state machine. This enables workflow and data continuity and integrity between two or more counterparties.

**Consensus Controlled State Machine:**

A Consensus Controlled State Machine is a network of replicated, shared, and synchronized digital data spread across multiple sites connected by a peer-to-peer and utilizing a consensus algorithm. There is no central administrator or centralized data storage.

**Electronic Record:**

Information captured through electronic means, and which may or may not have a paper record to back it up.

Bulletin of the American Society for Information Science and Technology, Electron-ic Records Research Working Meeting: A Report from the Archives Community, May 28‐30, 1997.

**Identity:**

The condition of being the same with something described or asserted, per Merriam-Webster Dictionary.

A concretization of the above used in this document: Identity is the combination of one or more unique identifiers with data associated with this/these identifier(s). Identity-associated data consists of signed certificates or credentials such as verifiable credentials and other unsigned, non-verifiable data objects generated by or on behalf of the unique identifier(s).

[Merriam-Webster Dictionary](https://www.merriam-webster.com/dictionary/identity)

**Interoperability:**

The ability of a Party operating Workflows on a baseline-compliant implementation A to instantiate and operate one or more Workflows with one or more Party on a baseline-compliant implementation B without the Party on either implementation A or B having to know anything of the other Party’s implementation.

**Liveness:**

In concurrent computing, liveness refers to a set of properties of concurrent systems, that require a system to make progress, despite its concurrently executing components ("process-es") may have to "take turns" in critical sections, parts of the program that cannot be simultaneously run by multiple processes. Liveness guarantees are important properties in operating systems and distributed systems.

Alpern B, Schneider FB (1985) Defining liveness. Inf Proc Lett 21:181-185

**Master Services Agreement (MSA):**

A legal contract that defines the general terms and conditions governing the entire scope of products commercially exchanged between the parties to the agreement.

**Non-Repudiable:**

Refers to a situation where a statement's author cannot successfully dispute its authorship or the validity of an associated contract. The term is often seen in a legal setting when the authenticity of a signature is being challenged. In such an instance, the authenticity is being "repudiated".

**Party:**

A set of Parties participating in the execution of one or more given Workflows. A Workgroup is set up and managed by one Party that invites other Parties to join as workgroup members. 

**Portability:**

The ability of a Party to migrate and re-baseline its existing Workflows and data from one baseline-compliant implementation to another baseline-compliant implementation without any 3rd party being able to prevent the migration.

**Privacy Assurance Mechanism:**

A way of ensuring the privacy of Workflow data represented on a public Mainnet. - permissionless vs public - to discuss and review.

**Proof of Correctness:**

A Proof of Correctness is a mathematical proof that a computer program or a part thereof will when executed, yield correct results, i.e. results fulfilling specific requirements. Before proving a program correct, the theorem to be proved must, of course, be formulated. The hypothesis of such a correctness theorem is typically a condition that the relevant program variables must satisfy immediately before the program is executed. This condition is called the precondition. The thesis of the correctness theorem is typically a condition that the relevant program variables must satisfy immediately after the execution of the program. This latter condition is called the post-condition. The thesis of a correctness theorem may be a statement that the final values of the program variables are a particular function of their initial values.

"Encyclopedia of Software Engineering",
Print ISBN: 9780471377375| Online ISBN: 9780471028956| DOI: 10.1002/0471028959,
(2002), John Wiley & Sons, Inc.

**System of Record:**

The integrity of the data in data architecture is established by what can be called the “system of record.” The system of record is the one place where the value of data is definitively established. Note that the system of record applies only to detailed granular data. The system of record does not apply to summarized or derived data.

W.H. Inmon, Daniel Linstedt and Mary Levins, "Data Architecture", 2019, Academic Press, ISBN: 978-0-12-816916-2

**Trust Model:**

Collection of entities and processes that Service Providers rely on to help preserve security, safety, and privacy of data and which is predicated on the use of a CCSM implementation.

Marsh S. (1994). "Formalizing Trust as a Computational Concept". Ph.D. thesis, University of Stirling, Department of Computer Science and Mathematics.

**Verifiably Secure:**

Verifiable computing that can be described as verifiably secure enables a computer to offload the computation of some function to other perhaps untrusted clients, while maintaining verifiable, and thus secure results. The other clients evaluate the function and return the result with proof that the computation of the function was carried out correctly. The proof is not absolute but is dependent on the validity of the security assumptions used in the proof. For example, a blockchain consensus algorithm where the proof of computation is the nonce of a block. Someone inspecting the block can assume with virtual certainty that the results are correct because the number of computational nodes that agreed on the outcome of the same computation is defined as sufficient for the consensus outcome to be secure in the consensus algorithm’s mathematical proof of security. 

Gennaro, Rosario; Gentry, Craig; Parno, Bryan (31 August 2010). Non-Interactive Verifiable Computing: Outsourcing Computation to Untrusted Workers. CRYPTO 2010. doi:10.1007/978-3-642-14623-7_25 

**Workflow:**

A process made up of a series of Worksteps between all or a subset of Parties in a given Workgroup.

**Workstep:**

A workstep is characterized by input, the deterministic application of a set of logic rules and data to that input, and the generation of a verifiably deterministic and verifiably correct output.




-------

# 2 Design and Architecture

This section defines the key concepts and architectural principles of the API and Data model(s).


-------

# 3 API

## 3.1 Org Management

Describes interface(s) providing functions to manage workgroups, organizations and users.

### 3.1.1 IRegistry

This interface provides functions to manage workgroups, organizations and users. 

// workgroups

| Requirement ID | Requirement  | 
| :--- | :--- |
| REG1 | #createWorkgroup(params: object): Promise<any>;  <br>description:  <br>interface: <br>**Caveats:**  |
| REG2| #updateWorkgroup(workgroupId: string, params: object): Promise<any>; <br>description:  <br>interface: <br>**Caveats:** |
| REG3| #fetchWorkgroups(params: object): Promise<any>; <br>description:  <br>interface: <br>**Caveats:** |
| REG4| #fetchWorkgroupDetails(workgroupId: string): Promise<any>; <br>description:  <br>interface: <br>**Caveats:** |
| REG5| #fetchWorkgroupOrganizations(workgroupId: string, params: object): Promise<any>;<br>description:  <br>interface: <br>**Caveats:** |
| REG6| #createWorkgroupOrganization(workgroupId: string, params: object): Promise<any>; <br>description:  <br>interface: <br>**Caveats:** |
| REG7| #updateWorkgroupOrganization(workgroupId: string, organizationId: string, params: object): Promise<any>;<br>description:  <br>interface: <br>**Caveats:**  |
| REG8| #fetchWorkgroupInvitations(workgroupId: string, params: object): Promise<any>; <br>description:  <br>interface: <br>**Caveats:** |
| REG9| #fetchWorkgroupUsers(workgroupId: string, params: object): Promise<any>; <br>description:  <br>interface: <br>**Caveats:** |
| REG10| #createWorkgroupUser(workgroupId: string, params: object): Promise<any>; |
| REG11| #updateWorkgroupUser(workgroupId: string, userId: string, params: object): Promise<any>; <br>description:  <br>interface: <br>**Caveats:** |
| REG12| #deleteWorkgroupUser(workgroupId: string, userId: string): Promise<any>; <br>description:  <br>interface: <br>**Caveats:** |


// organizations

| Requirement ID | Requirement  | 
| :--- | :--- |
| REG13| createOrganization(params: object): Promise<any>; |
| REG14| fetchOrganizations(params: object): Promise<any>; |
| REG15| fetchOrganizationDetails(organizationId: string): Promise<any>;|
| REG16| updateOrganization(organizationId: string, params: object): Promise<any>;|


// organization users

| Requirement ID | Requirement  | 
| :--- | :--- |
| REG17| fetchOrganizationInvitations(organizationId: string, params: object): Promise<any>; |
| REG18| fetchOrganizationUsers(organizationId: string, params: object): Promise<any>; |
| REG19| inviteOrganizationUser(organizationId: string, params: object): Promise<any>;|



## 3.2 Messaging

Describes interface(s) providing functions to communicate with counterparties.

### 3.2.1 IMessagingService


## 3.3 Security

Describes interface(s) providing functions to manage vaults and keys and to handle digital signatures.

### 3.3.1 IVault

This interface provides functions to manage vaults and keys.

| Requirement ID | Requirement  | 
| :--- | :--- |
| VAULT1 | createVault(params: object): Promise<any>;  |
| VAULT2| fetchVaults(params: object): Promise<any>;  |
| VAULT3| fetchVaultKeys(vaultId: string, params: object): Promise<any>;|
| VAULT4| createVaultKey(vaultId: string, params: object): Promise<any>; |
| VAULT5| deleteVaultKey(vaultId: string, keyId: string): Promise<any>;|
| VAULT6| encrypt(vaultId: string, keyId: string, payload: string): Promise<any>; |
| VAULT7| decrypt(vaultId: string, keyId: string, payload: string): Promise<any>; |
| VAULT8| signMessage(vaultId: string, keyId: string, msg: string): Promise<any>; |
| VAULT9| verifySignature(vaultId: string, keyId: string, msg: string, sig: string): Promise<any>; |
| VAULT10| fetchVaultSecrets(vaultId: string, params: object): Promise<any>; |
| VAULT11| createVaultSecret(vaultId: string, params: object): Promise<any>; |
| VAULT12| deleteVaultSecret(vaultId: string, secretId: string): Promise<any>; |

## 3.4 Agreement Execution



### 3.4.1 IBaselineRPC

Contains RPC methods that are Remote Calls available by default. The solution ??MUST?? implement all those methods.


| Requirement ID | Requirement  | 
| :--- | :--- |
| BRPC1|**# track**<br>**Description:**  Initializes a merkle tree database for the given Shield contract address and starts tracking new tree events.<br>**jsonrpc:** baseline_track <br>**Caveats:** <br>**Parameters:** <br> - DATA - address of the Shield contract<br>**Returns:**: -<br>**Example:**:|
| BRPC2|**# untrack**<br>**Description:** Removes event listeners for a single Shield contract. <br>**jsonrpc:** baseline_untrack <br>**Caveats:** <br>**Parameters:** <br> - DATA - address of the Shield contract<br>**Returns:**: -<br>**Example:**:|
| BRPC3|**# getTracked**<br>**Description:**  Retrieves a list of the shield contract addresses being tracked and persisted. <br>**jsonrpc:** baseline_getTracked <br>**Caveats:** <br>**Parameters:** -<br>**Returns:**: <br> - Array&lt;DATA&gt; - list of all tracked Shield contracts<br>**Example:**:|
| BRPC4| **# getLeaf** <br>**Description:** Retrieves a single leaf from a tree at the given shield contract address.  <br>**jsonrpc:** baseline_getLeaf <br>**Caveats:**  only works if the contract is tracked, otherwise <br>**Returns:** an error<br>**Parameters:** <br> - DATA - Shield contract address<br> - QUANTITY - leaf index<br>**Returns:**:<br> - MERKLE_TRIE_NODE<br>**Example:**:|
| BRPC5| **# insertLeaf** <br>**Description:** Inserts a single leaf to atree at the given shield contract address.  <br>**jsonrpc:** baseline_insertLeaf <br>**Caveats:**  only works if the contract is tracked, otherwise <br>**Returns:** an error<br>**Parameters:** <br> - DATA - Shield contract address<br> - QUANTITY - leaf index<br>**Returns:**:<br> - MERKLE_TRIE_NODE<br>**Example:**:|
| BRPC6| **# getLeaves** <br>**Description:**  Retrieves multiple leaves from a tree at the given shield contract address. <br>**jsonrpc:** baseline_getLeaves <br>**Caveats:** only works if the contract is tracked, otherwise <br>**Returns:** an error<br>**Parameters:** <br> - DATA - Shield contract address<br> - Array&lt;QUANTITY&gt; - leaf indexes<br>**Returns:**:<br> - Array&lt;MERKLE_TRIE_NODE&gt;<br>**Example:**:|
| BRPC7| **# getRoot** <br>**Description:**  Retrieves the root of a tree at the given shield contract address .<br>**jsonrpc:** baseline_getRoot <br>**Caveats:**  only works if the contract is tracked, otherwise <br>**Returns:** an error<br>**Parameters:**<br> - DATA - Shield contract address<br>**Returns:**:<br> - MERKLE_TRIE_NODE<br>**Example:**:|
| BRPC8| **# getCount** <br>**Description:**  Gets count of a tree at the given 'address'.<br>**jsonrpc:** baseline_getRoot <br>**Caveats:**  only works if the contract is tracked, otherwise <br>**Returns:** an error<br>**Parameters:**<br> - DATA - Shield contract address<br>**Returns:**:<br> - MERKLE_TRIE_NODE<br>**Example:**:|
| BRPC9|**# getSiblings** <br>**Description:**  Retrieves siblings path/proof of the given leaf index. <br>**jsonrpc:** baseline_getSiblings <br>**Caveats:**  only works if the contract is tracked, otherwise<br> **Returns:** an error<br>**Parameters:**<br> - DATA - address of the Shield contract<br> - QUANTITY - leaf index to prove<br>**Returns:**:<br> - Array&lt;MERKLE_TRIE_NODE&gt; - siblings path<br>**Example:**:|
| BRPC10|**# verify** <br>**Description:**  Verifies a sibling path for a given root and leaf at the given shield contract address. .<br>**jsonrpc:** baseline_verify <br>**Caveats:** only works if the contract is tracked, otherwise <br>**Returns:** an error<br>**Parameters:**<br> - DATA - address of the Shield contract<br> - DATA - root node hash<br> - DATA - hash of the leaf node to be verified<br> - Array&lt;DATA&gt; - siblings path/proof<br>**Returns:**:<br> - bool - verification result<br>**Example:**:| 
| BRPC11|**# verifyAndPush**<br>**Description:** .<br>**jsonrpc:** baseline_verify <br>**Caveats:** generates and sends a transaction which only affects the state after being included in a block<br>**Parameters:**<br>- DATA - address of the transaction sender<br>- DATA - address of the Shield contract<br>- Array&lt;DATA&gt; - proof data<br> - Array&lt;DATA&gt; - public inputs<br> - DATA - commitment<br>**Returns:**:<br> - DATA - transaction hash<br>**Example:**:| 
| BRPC12 | **# deploy** <br>**Description:** Deploys a contract with the given 'contract type'. Requires the account to be unlocked. <br>**jsonrpc:** baseline_deploy <br>**Caveats:** Optional and only used for dev/testing<br>**Parameters:**<br> - DATA - address of the deploying transaction sender<br> - string - type of the contract to be deployed<br>**Returns:**: -<br>**Example:**:|
| BRPC13 | **# deployBytecode** <br>**Description:**  Deploys a contract with the given bytecode. Requires the account to be unlocked. <br>**jsonrpc:** baseline_deployBytecode <br>**Caveats:** Optional and only used for dev/testing<br>**Parameters:**<br> - DATA - address of the deploying transaction sender<br> - string - type of the contract to be deployed<br>**Returns:**: -<br>**Example:**:|

### 3.4.2 IBlockchainService 



## 3.5 Privacy

Describes interfaces(s) providing functions to implement and manage private transactions.\
IZKSnarkCircuitProvider\
IZKSnarkCompilationArtifacts

## 3.6 Persistence

Describes interface(s) providing functions to store, query and update data.(sub and unsub ?)\
### 3.6.1 IPersistenceService

## 3.7 API Metadata

Describes the object providing metadata information about the API (example: title, description, terms of service, contact, license,version)

-------

# 4 Data Model

## 4.1 Org Management

| Requirement ID | Requirement  | 
| :--- | :--- |
| ORGM1|**#Workgroup**<br>**id:**  <br>**createdAt:**  <br>**networkId:** <br>**userId:** <br> **name**: <br>**description:**<br>**type:**<br>**config:**<br>**hidden:**|
| ORGM2|**#Organization**<br> {id, createdAt, name, userId, description, metadata}|
| ORGM3|**#User**<br>{id, createdAt, name, firstName, lastName, email, permissions}\|
| ORGM4|**#orgRegistry**<br>|

## 4.1.1 Examples

### 4.1.1.1 Workgroup 



```
Workgroup {
  id: '5bb63fd0-27f8-43f5-8275-14fe2891f14e',
  createdAt: '2020-11-05T14:34:04.3478365Z',
  networkId: '66d44f30-9092-4182-a3c4-bc02736d6ae5',
  userId: 'e021eca9-17cc-4598-a513-c84b05c15270',
  name: 'baseline workgroup',
  description: null,
  type: null,
  config: {
    webhook_secret: 'd6bf3a9f92344ea9b5ee29bd164060a9'
  },
  hidden: false
}
```



### 4.1.1.2  Organization



```
Organization {
  id: '440988f7-8f24-4dd8-bea0-8f103caa2fd5',
  createdAt: '2020-11-05T14:35:26.4838047Z',
  name: 'Bob Corp',
  userId: 'e021eca9-17cc-4598-a513-c84b05c15270',
  description: null,
  metadata: { messaging_endpoint: 'nats://localhost:4224' }
}


```



## 4.2.3 User


```
User {
  id: '',

}
```




## 4.2.4 orgRegistry


## 4.2 Messaging

## 4.2.1 Examples

```
export enum Opcode {
  Baseline = 'BLINE', // workflow-specific
  Join = 'JOIN', // join workgroup
  Ping = 'PING',
  Pong = 'PONG',
  Proof = 'PROOF', // generate proof
  Verify = 'VRFY', // idempotent proof verification
}export enum PayloadType {
  Binary = 0x0,
  Text = 0x1,
}export type Message = {
  opcode: Opcode; // up to 40 bits
  sender: string, // up to 336 bits
  recipient: string; // up to 336 bits
  shield: string; // up to 336 bits
  identifier: string; // up to 288 bits (i.e., UUIDv4 circuit/workflow identifier)
  signature: string; // 512 bits
  type: PayloadType; // 1 bit
  payload: Buffer; // arbitrary length
}

```

## 4.3 Security

| Requirement ID | Requirement  | 
| :--- | :--- |
| SEC1|**#Vault**<br>{id, createAt, name, description}|
| SEC2|**#Key**<br> {id, createAt, vaultId, type, usage, spec, name, description, publicKey}|


Identity/authentication/authorization\
Cryptography - curves, hash functions\
audit

## 4.3.1 Examples
```
Vault {
  id: 'f04e7222-bc86-47a4-a960-3be7e0a06995',
  createdAt: '2020-11-05T14:39:35.088114Z',
  name: 'Alice Corp vault',
  description: 'default organizational keystore'
}

Key {
  id: '89c32eea-d522-4780-84bc-7c29de9f5cf1',
  createdAt: '2020-11-05T14:39:37.7093941Z',
  vaultId: 'f04e7222-bc86-47a4-a960-3be7e0a06995',
  type: 'asymmetric',
  usage: 'sign/verify',
  spec: 'secp256k1',
  name: 'Alice Corp secp256k1 keypair',
  description: 'Alice Corp secp256k1 keypair',
  address: '0x5AE7032d4E3eC2215474988e9831D45C793b2A0f',
  publicKey: '0x049bd97593e08d40d77426d73a1f5ce2dbd184f58e48bee417577dcefcb6eab736dd06128a1eba69695af700bb1fcc5f0baa5e00ef597ebf2a0e2aaf2f8099c73c'
}

```


## 4.4 Agreement Execution

Workflow {}\
Worstep {}


## 4.5 Privacy

## 4.6 Persistence



-------

# 5 Security Considerations



-------

# 6 Conformance



-------

-------

# Appendix A - Acknowledgments
<!--
`(Note: A Work Product approved by the OP should include a list of people who participated in the development of the Work Product. This is generally done by collecting the list of names in this appendix. This list should be initially compiled by the Chair, and any Member of the OP may add or remove their names from the list by request. Remove this note before submitting for publication.)`
-->

The following individuals have participated in the creation of this specification and are gratefully acknowledged.

**Participants**:

Andreas Freund \
Anais Ofranc, Consianimis \
Gage Mondok, Chainlink \
Kyle Thomas, Provide Technologies Inc \
Daven Jones, Provide Technologies Inc \
Mehran Shakeri, SAP \
Alessandro Gasch, SAP \
John Wolpert, ConsenSys \
Sam Stokes, ConsenSys \
Nick Kritikos, ConsenSys
 
-------

# Appendix B. Revision History

Revisions made since the initial stage of this numbered Version of this document may be tracked here.

If revision tracking is handled in another system like github, provide a link to it instead of using this table, if desired.

| Revision | Date | Editor | Changes Made |
| :--- | :--- | :--- | :--- |
| baseline-api-v1.0-psd01 | yyyy-mm-dd | Editor Name | Initial working draft |


