
![OASIS Logo](http://docs.oasis-open.org/templates/OASISLogo-v2.0.jpg)
-------

# Baseline Core Version 1.0

## Project Specification Working Draft

## 29 September 2020

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
[Baseline, part of the Ethereum OASIS Open Project](https://www.baseline-protocol.org/)

#### Project Chair:
John Wolpert (john.wolpert@mesh.xyz), [ConsenSys](https://consensys.net/) 

#### Editors:
Anais Ofranc (aofranc@consianimis.com), [Consianimis](https://www.consianimis.com/) \
Andreas Freund (a.freundhaskel@gmail.com) \
Brian Chamberlain (brian.chamberlain@consensys.net), [ConsenSys](https://consensys.net/) \
Charles ‘Chaals’ Nevile (charles.nevile@consensys.net), [ConsenSys](https://entethalliance.org/) \
Daniel Norkin (daniel.norkin@envisionblockchain.com), [Envision Blockchain](https://envisionblockchain.com/)

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

This specification is related to: \
_Baseline API and Data Model version 1.0_ - https://github.com/ethereum-oasis/baseline/tree/master/docs/specs/api


#### Abstract:
This document describes the minimal set of business and technical prerequisites, functional and non-functional requirements, together with a reference architecture that when implemented ensures that two or more systems of record can synchronize their system state over a permissionless public Distributed Ledger Technology (DLT) network.

#### Status:
This document is under active development and implementers are advised against implementing the specification unless they are directly involved with the Baseline TC team.

<!--
was last revised or approved by Baseline, part of the Ethereum OASIS Open Project, on the above date. The level of approval is also listed above. Check the "Latest stage" location noted above for possible later revisions of this document. Any other numbered Versions and other technical work produced by the Open Project (OP) are listed at [TBD].
-->

Comments on this work can be provided by opening issues in the project repository or by sending email to the project’s public comment list baseline@lists.oasis-open-projects.org.


#### Key words:
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 [[RFC2119](#rfc2119)] and [[RFC8174](#rfc8174)] when, and only when, they appear in all capitals, as shown here.

#### Citation format:
When referencing this specification the following citation format should be used:

**[baseline-core-v1.0]**

_Baseline Core Version 1.0_. Edited by Anais Ofranc. 29 September 2020. OASIS Project Specification Draft 01. https://docs.oasis-open.org/baseline/baseline-core/v1.0/psd01/baseline-core-v1.0-psd01.html. Latest stage: https://docs.oasis-open.org/baseline/baseline-core/v1.0/baseline-core-v1.0.html.

-------

## Notices
Copyright © OASIS Open 2020. All Rights Reserved.

Distributed under the terms of the OASIS [IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr).

For complete copyright information please see the Notices section in the Appendix.

-------

# Table of Contents
[1 Introduction](#1-introduction) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.1 Overview](#11-overview) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.2 Glossary](#12-glossary) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.3 Typographical Conventions](#13-typographical-conventions) \
[2 Design and Architecture](#2-design-and-architecture) \
[3 API and Data Model](#3-api-and-data-model) \
[4 Communication](#4-communication) \
&nbsp;&nbsp;&nbsp;&nbsp;[4.1 Authentication and Authorization](#41-authentication-and-authorization) \
&nbsp;&nbsp;&nbsp;&nbsp;[4.2 Message Delivery](#42-message-delivery) \
&nbsp;&nbsp;&nbsp;&nbsp;[4.3 Performance](#43-performance) \
[5  Privacy and Confidentiality](#5-privacy-and-confidentiality) \
&nbsp;&nbsp;&nbsp;&nbsp;[5.1 Privacy](#51-privacy) \
&nbsp;&nbsp;&nbsp;&nbsp;[5.2 Confidentiality](#52-confidentiality) \
[6 Agreement Execution](#6-agreement-execution)  \
&nbsp;&nbsp;&nbsp;&nbsp;[6.1 Business Logic Development](#61-business-logic-development) \
&nbsp;&nbsp;&nbsp;&nbsp;[6.2 Business Logic Execution](#62-business-logic-execution) \
&nbsp;&nbsp;&nbsp;&nbsp;[6.3 Performance](#63-performance) \
[7 Governance](#7-governance) \
&nbsp;&nbsp;&nbsp;&nbsp;[7.1 Governance Model](#71-governance-model) \
[8 Security Considerations](#8-security-considerations) \
&nbsp;&nbsp;&nbsp;&nbsp;[8.1 Data Privacy](#81-data-privacy) \
&nbsp;&nbsp;&nbsp;&nbsp;[8.2 Production readiness](#82-production-readiness) \
[9 Conformance](#9-conformance) \
&nbsp;&nbsp;&nbsp;&nbsp;[9.1 Conformance Targets](#91-conformance-targets) \
&nbsp;&nbsp;&nbsp;&nbsp;[9.2 Conformance Levels](#92-conformances-levels)\
&nbsp;&nbsp;&nbsp;&nbsp;[9.3 Interoperability](#93-interoperability)\
[Appendix A.        Acknowledgments]()\
[Appendix B.        Revision History]()

 

-------

# 1 Introduction


## 1.1 Overview


## 1.2 Glossary

**Baseline Protocol:**

The Baseline Protocol is a set of methods that enable two or more state machines to achieve and maintain data consistency, and workflow continuity by using a network as a common frame of reference. 

**Baseline-bridge:**

A mechanism for one Workflow to use the proof generated by a different Workflow.
to use a proof generated in a Workflow executed by Workgroup A as input to a Workflow executed by Workgroup B.

**Baseline-connector:**

Proposed: An interface connecting and synchronizing a baseline stack and system of record.

**Byzantine Fault Tolerant(BFT):**

Given a network or system of n components, t of which are dishonest, and assuming only point-to-point channels between all the com-ponents, then whenever a component A tries to broadcast a value x such as a block of transactions, the other components are permit-ted to discuss with each other and verify the consistency of A's broadcast, and eventually settle on a common value y. The system is then considered to resist Byzantine faults if a component A can broadcast a value x, and then:
* If A is honest, then all honest compo-nents agree on the value x.
* If A is dishonest, all honest components agree on the common value y.

"The Byzantine Generals Problem", Leslie Lamport, Robert E. Shostak, Marshall Pease, ACM Transactions on Programming Languages and Systems, 1982

**Circuit Breaker:**

The ability of a Party to immediately cease all their active Workflows across all of their Workgroups within a Baseline-compliant implementation, and, if required, exit a Baseline-compliant implementation with all their data without any 3rd party being able to prevent the exit.

**Common frame of reference:**

Proposed: Baselining is a methodology for achieving and maintaining data consistency between two or more state machines  using a network as a common frame of reference. It enables workflow continuity between two or more Parties.

**Distributed Ledger Technology(DLT):**

Distributed Ledger Technology is a digital system for recording the transaction of assets in which the transactions and their details are recorded in multiple places at the same time. Unlike traditional databases, distributed ledg-ers have no central data store or administra-tion functionality.

University of Cambridge, Cambridge Judge Business School – Defining DLT, August 2018

**Interoperability:**

The ability of a Party operating Workflows on a baseline-compliant implementation A to instantiate and operate one or more Workflows with one or more Party on a baseline-compliant implementation B without the Party on either implementation A or B having to know anything of the other Party’s implementation.

**Liveness:**
In concurrent computing, liveness refers to a set of properties of concurrent systems, that require a system to make progress, despite its concurrently executing components ("process-es") may have to "take turns" in critical sec-tions, parts of the program that cannot be sim-ultaneously run by multiple processes. Liveness guarantees are important properties in operating systems and distributed systems.

Alpern B, Schneider FB (1985) Defining liveness. Inf Proc Lett 21:181-185

**Master Services Agreement (MSA):**
A legal contract that defines the general terms and conditions governing the entire scope of products commercially exchanged between the parties to the agreement.

**Non-Repudiable:**
Refers to a situation where a statement's au-thor cannot successfully dispute its authorship or the validity of an associated contract. The term is often seen in a legal setting when the authenticity of a signature is being challenged. In such an instance, the authenticity is being "repudiated".

**Party:**

A set of Parties participating in the execution of one or more given Workflows. A Workgroup is set up and managed by one Party that invites other Parties to join as workgroup members. 

**Portability:**

The ability of a Party to migrate and re-baseline its existing Workflows and data from one baseline-compliant implementation to another baseline-compliant implementation without any 3rd party being able to prevent the migration.

**Privacy Assurance Mechanism:**

A way of ensuring the privacy of Workflow data represented on a public Mainnet. - permissionless vs public - to discuss and review.

**System of Record:**

The integrity of the data in data architecture is established by what can be called the “system of record.” The system of record is the one place where the value of data is definitively established. Note that the system of record applies only to detailed granular data. The system of record does not apply to summa-rized or derived data.

W.H. Inmon, Daniel Linstedt and Mary Levins, "Data Architecture", 2019, Academic Press, ISBN: 978-0-12-816916-2

**Trust Model:**

Collection of entities and processes that Ser-vice Providers rely on to help preserve securi-ty, safety, and privacy of data and which is predicated on the use of a DLT implementa-tion.

Marsh S. (1994). "Formalizing Trust as a Computational Concept". PhD thesis, University of Stirling, Department of Computer Science and Mathematics.

**Verifiably Secure:**

Verifiable computing that can be described as verifiably secure enables a computer to of-fload the computation of some function to other perhaps untrusted clients, while main-taining verifiable, and thus secure, results. The other clients evaluate the function and return the result with a proof that the compu-tation of the function was carried out correct-ly. The proof is not absolute but is dependent on the validity of the security assumptions used in the proof. For example, a blockchain consensus algorithm where the proof of com-putation is the nonce of a block. Someone in-specting the block can assume with virtual certainty that the results are correct because the number of computational nodes that agreed on the outcome of the same computa-tion is defined as sufficient for the consensus outcome to be secure in the consensus algo-rithm’s mathematical proof of security. 

Gennaro, Rosario; Gentry, Craig; Parno, Bryan (31 August 2010). Non-Interactive Verifiable Computing: Outsourcing Computation to Untrusted Workers. CRYPTO 2010. doi:10.1007/978-3-642-14623-7_25 

**Workflow:**

A process made up of a series of Worksteps between all or a subset of Parties in a given Workgroup.

**Workstep:**

A workstep is characterized by an input, the deterministic application of a set of logic rules and data to that input, and the generation of a verifiably deterministic and verifiably correct output.

## 1.3 Typographical Conventions

- Naming conventions
- Font colors and styles
- Typographic conventions


-------

# 2 Design and Architecture

This section provides definitions, key concepts, and overviews of the components of a Baseline Protocol Implementation compliant with the requirements of this document. 

## 2.1 Agreement
An agreement is a manifestation of mutual assent by two or more parties to one another see [Cornell Law School](https://www.law.cornell.edu/wex/agreement). An Agreement between two or more Counterparties allows for transactions between them dealing with, for example, commercial items such as products. An Agreement governs and defines all transactions between counterparties.

**[R1]**	Transacting counterparties  MUST have a corresponding agreement.

## 2.2	State Object
A State Object is an item which can be exchanged between counterparties to an agreement, whose state the counterparties have agreed on and which is defined in an agreement. In the context of this standard, a State Object is assumed to be a document derived from an agreement and representing a specific state of either an asset, a product offering or a service offering transacted between counterparties.

Examples include but are not limited to a
* Quote
* Order
* Invoice
referencing for example:
* Digital Services
* Physical Products
* Financial Assets
 
## 2.3 Transacting Counterparties
A transaction counterparty, or simply counterparty, that requests one or more State Objects from another counterparty is the Requester with respect to the State Object.  The Requester can also be the final recipient of one or more State Objects.

A counterparty that provides one or more State Object to another counterparty is the Provider with respect to the provided State Objects. The Provider is accountable to the Requester for all the State Objects it provides to the Requester. 

A Requester may request State Objects from multiple Providers and in the context of a supply chain of State Objects, a Provider of one State Object may also play the role of a Requester of other State Objects.

## 2.4 Commercially and Legally Binding Documents
Prior to establishing a business and operational environment, Requester(s) and Provider(s) (“the parties”) sign agreements that commercially and legally bind the parties. 

Such documents may be presented as a combination of one or more of the following: Master Services Agreement, Specific Terms and Conditions and an Order.

**[R2]**	The parties to a Commercial Agreement MUST sign commercially and legally binding documents with each other.

### 2.4.1	Contract

This section details the prerequisites required to be fulfilled by a legal contract between the parties within the context of this document, and defines the general terms and conditions in the legal contract governing commercial transactions between these parties. 

A contract will typically govern all commercial transactions and includes, but is not limited to, sections defining the Governing Law, the Legal Jurisdic-tion, Indemnity, Liability, Force Majeure, Charges and Taxes, Term, Obligations, definitions of commercially relevant elements such as locations, equipment, and products, as well as any other terms and conditions that apply to the entire scope of commercial and legal relations between the parties. Other legal documents, such as an order, typically reference the contract for its general terms and conditions and might contain more specific terms and conditions, such as rates and discounts and other commercial information, relevant for the specific context of the legal document. These specific terms and conditions can expand or override the original contract, and are intentionally not specified in the original contract. The contract is the legal document from which specific commercial documents, such as a Quote or an Order, are derived.

**[R3]**	There MUST be a legally binding contract, however simple and temporary, before a commercial transaction — such as an order — between parties takes place. 

For example, the contract and the order can be combined into a single document for the purposes of a single transaction. However, there must be a legal framework in place to provide context for monies that are exchanged and settled. The functional part of the contract forms the basis of a Baseline Protocol Implementation (BPI) defined in section 2.6. The requirements below are to be understood solely within the context of this document. They are not meant to be generalized beyond this context.

**[D1]**   The contract SHOULD be in an electronic form.

**[D2]**   The functional terms of the contract SHOULD be represented on a BPI between the counterparties.

**[D3]**	 The contract SHOULD be an MSA between the contract parties. 

An MSA is preferable since it allows a proliferation of contract based BPI (commercial) workflows and work staps between the parties reducing complexity and potential errors.

**[CR1]< [D3]** 	There MUST be only one MSA between a contract parties covering commercial transactions for a given set of products, services or assets to disambiguate which terms cover which part of a commercial relationship between parties.

Specific Terms and Conditions (“Specific T&Cs”) defines the terms and conditions governing a specific product, service or asset or set thereof offered and delivered by Provider(s) to Requester(s).

**[D4]**	Each specific product, service or asset or set thereof offered and delivered by Provider(s) to Requester(s) SHOULD have its own Specific T&C document.

This would allow the fine graining and consistent application of commercial State Object specific business rules and data.

### 2.4.2	Commercial Documents 

Commercial Documents, a category of commercial State Objects, refer to the state of a specific product/service/asset or set thereof, which may or may not be modified from an original offering to meet the Requester requirements and includes operational and commercial details. A commercial document is an abstract construct representing mutual commitments based on a legally binding contract.

**[R4]**	A commercial State Object to be transacted on MUST be based on a specific commercial document.

**[R5]**  A commercial document MUST be derived from a legally binding contract.

**[R6]**	A commercial document MUST be represented as an electronic record.

**[R7]**  A commercial document MUST be represented on a BPI between the counterparties.

**[R8]**	A commercial document MUST be authorized by legal representatives of the parties, or their legal delegates.

**[D4]**	The definition of a commercial document authorization SHOULD be stated in the legal contract underlying the commercial document.

Authorizations for commercial transactions are a foundational element in the context of this document, as they are in paper based agreements. Therefore, any legal authorization agreements relevant to the commercial agreement between commercial counterparties, and thus to commercial transactions between them, are important to be represented in a BPI to ensure mitigating the risk of unauthorized signatures.

**[R9]**	The representatives and their authorized delegates who can perform commercial document authorizations SHOULD be explicitly listed or inferred from the stated legal delegation rules of the counterparties in the contract underlying any commercial document. 

**[R10]**	A commercial document MUST be non-repudiable.

Note that while non-repudiation in the physical world is most often tied to a physical signature of an individual on a legal document, in the digital world a digital signature over a digital legal document such as an Order or an Invoice belonging to a known and verifiable digital identity of a counterparty serves the same purpose.

Example
A Buyer and Seller may agree that a signed Order requires a signed original paper copy, or a digitally signed electronic Order Form, in addition to an Order being digitally signed and recorded within a BPI.

## 2.5 Distributed Ledger Technology (DLT)

A distributed ledger (also called a shared ledger or Distributed Ledger Technology or DLT) is a consensus of replicated, shared, and synchronized digital data spread across multiple sites. There is no central administrator or centralized data storage. 

A DLT is the foundational enabler of a BPI with no or limited trust assumptions.

A peer-to-peer network is required as well as a consensus algorithm to ensure replication across nodes is undertaken [put reference here]

For specificity, the popular word "Blockchain" is a particular form of DLT design.

## 2.6 Baseline Protocol Instance

Baseline Protocol Instances (BPIs) are logical constructs shared between (commercial) counterparties of Requesters and Providers and implemented on a Distributed Ledger. They are used to either validate, or reconcile, commercial transactions between Requesters and Providers related to all (commercial) State Objects transacted between them. The nature of bi- or multi-lateral transactions is such that two or more parties may (commercially) transact to/from each other interchangeably. 

Abstractly, a BPI consists of
* the private messaging between legal Contract Counterparties about the state, or the requested or finalized state changes, of the commercial State Objects between them.
* the representation of a (commercial) contract and commercial documents and their business rules and data as distinct workflows and worksteps between Contract Counterparties organized into workgroups based on the stipulations of the (commercial) contract.
* the deterministic processing and finalization of state change requests based on commercial documents between the Contract Counterparties as stipulated by the (commercial) contract.
* the preservation of privacy of all Contract Counterparties and their (commercial) data from other 3rd parties.

BPIs are strongly dependent on the security and privacy capabilities of the DLT used to implement a BPI.

**[R11]**	A BPI MUST be implemented on a DLT.

Security and Privacy requirements of a BPI are key and are strongly dependent on the security and privacy assurances of the DLT on which the BPI is implemented can provide. BPIs need to take great care to avoid the following two situations:

1. Weaken the security assurances of the underlying DLT by increasing the DLT attack surface. Such an expansion of the attack surface can occur through, for example, concentration of value-at-risk in one or more BPIs above the value used to economically secure the underlying DLT. This situation would provide an economic incentive to attack, and subvert, the underlying DLT to extract the value in one or more BPIs.
2. Increase the existing attack surface of a DLT such that the security assurances of the BPI become significantly weaker than the underlying DLT. An example of such a situation can occur when a commercial State Object such as a Financing contract or an Order in BPI A is dependent on a commercial State Object such as an invoice as collateral in BPI B, and when BPI B has weaker transaction finality assurances than either BPI A or the underlying DLT. In that scenario, the commercial State Object in BPI A cannot provably rely on the invoice as collateral in BPI B since the invoice might be reverted, and it would then no longer be a suitable collateral.
	
Hence, we enumerate the following requirements below:

**[R12]**	A BPI MUST have the same security assurances as the DLT used to implement it.

**[R13]**	(Commercial) State changes of a BPI MUST be verifiable on the DLT used to implement it.

Verifiable in this context means that a 3rd party can verify, via a cryptographic proof on the DLT, that a transaction changed the state of a (commercial) State Object in the BPI correctly, based on agreed upon business rules - for example changing the Order status from open to completed.

**[R14]**	A BPI SHOULD have the same Liveness properties as the DLT used to implement it.

Liveness means that if a DLT does not require (commercial) counterparties to constantly monitor its state to ensure that the state of the DLT is correct, then the BPI should not require a constant observation of its state either.

**[R15]**	A BPI MUST be censorship resistant.

Censorship resistant means that a (commercial) counterparty can terminate a commercial transaction at any time without another counterparty, or any Node of the DLT used to implement the BPI, being able to stop the termination of the commercial transaction.

**[R16]**	A BPI MUST be able to provide privacy of the (commercial) conterparties' data with respect to any party outside of the BPI.

 
## 2.7 High-Level Functional Requirements

This section describes the prerequisites and high-level general operational framework requirements 
* Functional Requirements on commercial counterparties
* DLT-based Lifecycle Processes

### 2.7.1	Functional Requirements on commercial counterparties 

This section states the commercial and operational functionalities required from commercial counterparties.

**[R17]**	Commercial Counterparties MUST have the ability to meet all required legal, compliance and business reporting requirements. 

This comprises, e.g., fraud or tax audit requirements based on commercial transactions on a BPI.

**[R18]**	Commercial Counterparties MUST support the Reference Architecture defined in this section.

**[R19]**	Commercial Counterparties MUST use the Baseline Protocol APIs to transact on a commercial State Object.

An ability of a Requester to request products, services or assets, in other words commercial State Objects, through an instance of the Baseline Protocl's APIs does not necessarily imply the ability to provide products, services and assets through an instance of the Baseline Protocol APIs and vice versa.

It is important for (commercial) counterparties to know the level of conformity other (commercial) counterparties have with the Baseline Protocl Standard.

**[R18]**	Counterparties MUST publish their level of conformity (self-declaration or certification) with the Baseline Protocol standard in a publicly accessible manner.

### 2.7.2	DLT-based Lifecycle Processes

Commercial Counterparties must comply efficiently and effectively with requirements of regulatory frameworks, e.g., Office of Foreign Assets Control ("OFAC") of the US Department of the Treasury when employing new operational and commercial frameworks as laid out in this standard.

**[R19]**	If required to meet particular third party requirements, (e.g., privacy or regu-latory frameworks in different jurisdictions), a commercial counterparty MUST record a pseudonymous map of the supply chain that is required to fulfill the provisioning of a requests commercial State Object (products, services or assets) transacted on a BPI.

Requesters are only aware of the identity and commercial data of their Provider(s), but not of the other participants in the supply chain. However, Requesters can cryptographically verify that a given set of claims by Providers about the supply chain are true, for example, that all supply chain participants are not located in an embargo country.

Therefore, a pseudonymous map of a supply chain is a cryptographically connected and verifiable list of proofs about the relationships of participants and integrity of supply chain events that does not disclose identifying details of Providers and their commercial data.

This allows enforcement of conformance with regulations, additional legal and technical requirements without disclosure of confidential information.

## 2.8 Baseline Protocol Reference Architecture 

This section describes the components of the Baseline Reference Architecture 
* (Commercial) State Synchornization
* DLTs and BPI/DLT Abstraction Layers
* External Applications
* Baseline Protocol Stack Detailed Reference Architecture Layers and Componants

### 2.8.1 (Commercial) State Synchornization

A BPI can be used  as a common frame of reference for business processes that can be used in a complementary way to existing System-of-Record integrations.

#### Illustrative High-Level Example

A Master Services Agreement (MSA) between a Requester (Buyer) and a Provider (Seller) is implemented on a BPI and contains billing terms, pricing, discounts, and Seller information such as billing address etc. Once established and agreed upon by Buyer and Seller, the BPI provides state synchronization between Buyer and Seller since the ERP systems for Buyer and Seller can now refer to mutually agreed upon data as a common frame of reference. Based on this mutually agreed upon state in the MSA, the Buyer creates an Order in the business workflow based on the MSA and a cryptographic proof (in zero knowledge) that confirms not only the correct application of business logic but also correct application of commercial data in the Order creation. This proof is submitted together with the Order through the BPI and then validated by the Seller without having to utilize its own System of Record for validation using the BPI. If the proof is validated, the Seller accepts the proposed state change by generating its own cryptographic proof confirming its acceptance of the state change. The Seller then updates the state of the business workflow in the BPI and sends the new proof to the Buyer. 

The figure below visually demonstrates high-level Buyer and Seller Order generation and acceptance assuming that a MSA between Buyer and Seller already exists and is recorded on a BPI, and that the commercial state has been synchronized up to this workstep in the commercial business workflow.

<figure>
  <img
  src="./images/Baseline-Fig1-Illustrative-Example.png"
  >
  <figcaption>Figure 1: Illustrative Example of how the commercial state between Buyer and Seller is synchronized and an Order created.</figcaption>
</figure>

Without a BPI, both Buyer and Seller must assume that the MSA between them and all its values are correctly represented in the other party’s respective Systems-of-Record. If an order is created based upon the MSA but does not comply with the MSA, it will likely result in extensive manual interactions between Seller and Buyer at one stage or another to re-solve the problem to their mutual satisfaction.  

**[R20]**	The (commercial) counterparties MUST agree on the business process rules which are represented in the business workflows and worksteps in the BPI. 

**[R21]** 	The (commercial) counterparties MUST validate the correctness of a (commercial) State Object based on a commercial state change against the transaction business logic in the applicable BPI workflow and workstep.

**[R22]** 	The (commercial) counterparties MUST generate a proof of correctness of a (commercial) State Object based on a commercial state change that can be validated against the BPI transaction business logic.

**[R23]** 	Any new (commercial) state between counterparties MUST be recorded on the BPI between them.

**[R24]** 	Any counterparty having received a proof of correctness of a (commercial) state change MUST be able to validate that proof of correctness aginst the BPI between the counterparties.

**[R25]** 	A (commercial) counterparty MUST include a verifiable proof of correctness of the (commercial) State Object generated by the commercial state change in the BPI Messages between the transacting counterparties.

### 2.8.2 DLTs and BPI/DLT Abstraction Layers

<figure>
  <img
  src="./images/Baseline-Fig2-DLT-BPI-Abstractions.png"
  >
  <figcaption>Figure 2: DLT and BPI Abstraction Architecture</figcaption>
</figure>

To maintain modularity in the reference architecture, we introduce the concept of DLT and BPI Abstraction. A DLT or BPI Abstraction expressed through a DLT Abstraction Layer, constitutes technology applications which wrap capabilities of DLTs and BPIs such that these capabilities can be exposed to applications above the DLT or BPI Abstraction Layers in a manner that minimizes the dependency of these application on the details of a DLT and BPI – Figure 2. 

The Client DLT API as an external BPI API is implementation specific and will not be discussed further.

**[R26]**	DLTs used in the implementation of a BPI MUST support bilateral and multi-lateral digital representations of legal contracts.

**[R27]**	A DLT or BPI Abstraction Layer used in a BPI MUST support more than one DLT instance.

**[R28]** A DLT or BPI Abstraction Layer used in a BPI MUST support more than one DLT type.

This approach avoids lengthy discussions about which DLT protocol to utilize for a BPI, simplifying the decision making process considerably if most common DLTs are incorporated.

Note that irrespective of whether one is in a public or private DLT scenario, the settings of a protocol such as block time, consensus model, type of execution framework etc. needs to be agreed upon by operating entities in some fashion either informally such as in Ethereum or formally such as in the Trade Finance consortium Komgo. 

The agreement on the governance entity, its rules, and its method of achieving interval syn-chronization consensus, as well as the definition of acceptable governance structures and their rules is beyond the scope of this document.

**[R29]**	The (commercial) counterparties MUST agree on the BPI.

### 2.8.3	External Applications

**[R30]**	Application/s providing commercial transaction functionality such as billing to (commercial) counterparties, and re, therefore, external with respect to the BPI, MUST be independent of any BPI.

Note, that this requirement is motivated by reducing the dependency of counterparty internal systems on the BPI and vice versa. 

### 2.8.4	Baseline Protocol Stack Detailed Reference Architecture Layers and Componants

<figure>
  <img
  src="./images/High-Level-Baseline-Architecture.png"
  >
  <figcaption>Figure 3: Detailed Baseline Reference Architecture Layers and Components</figcaption>
</figure>

A Baseline Protocol Stack Reference Architecture as depicted above in Figure 3 is comprised of the following layers:
* **Baseline Protocol (BPI) Abstraction Layer**: This layer enables accessing all externally available BPI functions through APIs as defined in the Baseline Protcol API Standards document 
* **Middleware Layer**: This layer manages all counterparties to an agreement and its associated workflows and worksteps with business rules and business data as well as all counterparrty delegates. In addition, it manages all messaging between counterparties to an agreement and instantiation of processing layers based on newly created or updated agreements and their workflows, worksteps, business rules and business data.  
* **Processing Layer**: Manages, properly sequences and deterministiaclly processes and finalizes in a privacy-preserving, cryptographically verifiable manner all state change requests from counterparties to all agreements represented in the BPI.  
* **DLT Abstraction Layer**: This layer enables accessing all required BPI functions implemented on one or more DLTs through APIs as defined in the Baseline Protcol API Standards document. 
* **DLT Layer**: This layer manages, properly sequences and deterministiaclly processes in a privacy-preserving, cryptographically verifiable manner all transactions from the Processing Layer as well as either deterministcally or probabilistically finalizes on the DLT all DLT state transitions based on said transactions.

Below we list and define the components of each layer. The detailed requirements for each component will be discussed in later sections of this document.

* **BPI Abstraction layer**
    * **API Gateway**: An API gateway which exposes all required functionality to the counterparties to an agreement and enforces all necessary authentication and authorization of API calls as well as properly directs the API calls within the Baseline Protocol Stack
    * **Application**: The application logic which manages the pre-processing and routing of all API requests, as well as the enforcement of authentication and authoorization protocols and rules.
* **Middleware Layer**
    * **Workflows**: A Business Process Management engine that allows for the definition, management and instantiation of workflows and worksteps and associated buiness rules and data based on (commercial) agreements between counterparties
    * **Identity/Accounts/Workgroups**: A capability that allows for the identification and management of counterparties and their delegates as well as members of workflows and worksteps organizaed in workgroups which are derived from the counterparties to an agreement. 
    * **Messaging**: A mesaging capability that allows the exchange of secure and privacy-preserving messages between counterparties to an agreement to communicate and coordinate agreement on proposed (commercial) state changes. 
* **Processing Layer**
    * **Transaction Pool**: one or more transaction pools which hold, properly sequence, preprocess and batch for processing by the Virtual State Machine all requested state change transactions of a BPI.
    * **Virtual State Machine**: one or more Virtual State Machines which deterministically processes and finalizes in a privacy-preserving, cryptographically verifiable manner all state change request transactions.
    * **Storage**: A storage system for the cryptographically linked current and historical state of all (commercial) agreements in a BPI.
* **DLT Abstraction Layer** 
    * **API Gateway**: An API gateway which enables accessing all required BPI functions implemented on one or more DLTs, and properly directs the requests within the DLT Abstraction layer to the proper DLT API application logic
    * **Application**: The DLT API application logic which manages the pre-processing, as well as the proper usage of the underlying DLT and BPI authentication and authorization.
*  **DLT Layer** is comprised of
    * Messaging: A mesaging capability that allows the exchange of messages between DLT nodes that comprise either received transactions or a new proposed DLT state.
    * Transaction Pool: A transaction pool holds, properly sequences, pre-processes and batches for processing by the DLT Virtual State Machine all submitted DLT transactions.
    * Virtual State Machine: A Virtual State Machine deterministically cally processes in a cryptographically verifiable manner all submitted transactions for DLT state changes.
    * Storage: A storage system for the cryptographically linked current and historical state of all DLT State Objects.


# 3 API and Data Model


-------

# 4 Communication

This section describes the logical architecture (presented as two abstract services - Authentication & Authorization and Message Delivery) that allows parties to send and receive messages securely.

## 4.1 Authentication and Authorization

Describes the requirements for the Authentication service responsible for establishing and maintaining the connection between verified parties.

| Requirement ID | Requirement  | 
| :--- | :--- |
| COM1 | something MUST something |
| COM2 | something SHOULD something |

## 4.2 Message Delivery

Describes the requirements for the Delivery service responsible for exchanging messages between verified parties.

| Requirement ID|Requirement  |
| :--- | :--- |
| COM3 | MUST implement IMessagingService interface to interact with verified parties. |
| COM4 | MUST implement pub-sub pattern. |
| COM5 | MUST implement XYZ Protocol Messages (types, formats, queues, inbound, outbound). |
| COM6 | Automated message validation |
| COM7 | Messaging Endpoints - SHOULD be distinct from system of record. |

## 4.3 Performance

Describes the performance requirements for the Communication component.

| Requirement ID|Requirement  |
| :--- | :--- |
| COM8 | Durable messaging  |
| COM9 | Persistent messaging|
| COM10 | Latency  |
| COM11 | Fault-tolerance |
| COM12 | Scalability |


-------

# 5 Privacy and Confidentiality

This section describes mechanisms to ensure counterparties confidentiality and shielded private transactions.

## 5.1 Privacy
Describes mechanisms ensuring that only information relevant to the transaction and pre-agreed by verified parties is used to its purpose.

| Requirement ID|Requirement  |
| :--- | :--- |
| PRICON1 | something MUST something  |
| PRICON2 | something SHOULD something |


## 5.2 Confidentiality

Describes the mechanisms ensuring that other parties (i.e parties outside of transaction) are prevented from accessing data that they are not authorized to access.

| Requirement ID|Requirement  |
| :--- | :--- |
| PRICON3 | something MUST something  |
| PRICON4 | something SHOULD something |

-------

# 6 Agreement Execution

## 6.1 Business Logic Development

Describes the requirements for the development of business rules that define what and how workflows are executed.

| Requirement ID|Requirement  |
| :--- | :--- |
| AGEXEC1 | IBaselineRPC  |
| AGEXEC2| Shared agreement: up to each workgroup to agree on business logic  |
| AGEXEC3| Shielding: up up to each workgroup to determine a suitable shielding mechanism. |

## 6.2 Business Logic Execution

Describes the mechanisms supporting the execution of the agreed business logic.


| Requirement ID|Requirement  |
| :--- | :--- |
| AGEXEC4 | Workflows, worksteps - business rules chaining and sequenced execution |
| AGEXEC5| Deterministic result - given a set of arguments and a state of the ledger, execution of business logic must produce the same result. |
| AGEXEC6| Event-driven |
| AGEXEC7| On-chain/ DTL execution mode|

## 6.3 Performance

Describes the performance requirements for the Agreement Execution component.

| Requirement ID|Requirement  |
| :--- | :--- |
| AGEXEC8 | Processing/Finality time  |
| AGEXEC9| Execution/Process monitoring |

-------

# 7 Governance
Describes the required functionalities to implement governance processes at every functional layer of the Baseline specification.


## 7.1 Governance Model

| Requirement ID|Requirement  |
| :--- | :--- |
| GOV1 | Change Control - requirements for introducing change in a controlled and coordinated manner for each functional layer. |
| GOV2| Execution/Process monitoring |


## 7.2 Audit

Describes the requirements for audit activities. 


| Requirement ID|Requirement  |
| :--- | :--- |
| GOV3 |Internal audit |
| GOV4| External audit  |


## 7.3 Monitoring & Reporting

Describes the requirements for monitoring and reporting on operations for each functional layer.

| Requirement ID|Requirement  |
| :--- | :--- |
| GOV5 | something MUST something  |
| GOV6| something SHOULD something |

-------

# 8 Security Considerations


Describes security topics that should be important in Baseline implementations but that are NOT requirements. 

## 8.1 Data Privacy

Provides a list of considerations related to data privacy.

The standard does not set any requirements for compliance to jurisdiction legislation/regulations, responsibility of the implementer to comply to applicable data privacy laws.

## 8.2 Production Readiness

Provides a list of considerations related to the use of underlying protocols/applications/tools etc. 

The standard does not set any requirements for the use of specific applications/tools/libraries etc.
Examples included in standard to be non-normative.
The implementer should perform due diligence when selecting tools, libraries etc.



<!--

(Note: OASIS strongly recommends that Open Projects consider issues that might affect safety, security, privacy, and/or data protection in implementations of their specification and document them for implementers and adopters. For some purposes, you may find it required, e.g. if you apply for IANA registration.

While it may not be immediately obvious how your specification might make systems vulnerable to attack, most specifications, because they involve communications between systems, message formats, or system settings, open potential channels for exploit. For example, IETF [[RFC3552](#rfc3552)] lists “eavesdropping, replay, message insertion, deletion, modification, and man-in-the-middle” as well as potential denial of service attacks as threats that must be considered and, if appropriate, addressed in IETF RFCs.

In addition to considering and describing foreseeable risks, this section should include guidance on how implementers and adopters can protect against these risks.

We encourage editors and OP members concerned with this subject to read _Guidelines for Writing RFC Text on Security Considerations_, IETF [[RFC3552](#rfc3552)], for more information.

-->

-------

# 9 Conformance


Describes the conformance clauses and tests required to achieve baseline compliant implementations.

## 9.1 Conformance Targets

Defines entities and implementations subject to conformance.


## 9.2 Conformance Levels

Defines conformance levels and their conformance clauses.

## 9.3 Interoperability

<!--

(Note: The [OASIS TC Process](https://www.oasis-open.org/policies-guidelines/tc-process#wpComponentsConfClause) requires that a specification approved by the OP for public review, or for publication at the Project Specification or OASIS Standard level must include a separate section, listing a set of numbered conformance clauses, to which any implementation of the specification must adhere in order to claim conformance to the specification (or any optional portion thereof). This is done by listing the conformance clauses here.

For the definition of "conformance clause," see [OASIS Defined Terms](https://www.oasis-open.org/policies-guidelines/oasis-defined-terms-2017-05-26#dConformanceClause).

See "Guidelines to Writing Conformance Clauses":  
http://docs.oasis-open.org/templates/TCHandbook/ConformanceGuidelines.html.

Remove this note before submitting for publication.)

-->

-------

# Appendix A. References

This appendix contains the normative and informative references that are used in this document. Any normative work cited in the body of the text as needed to implement the work product must be listed in the Normative References section below. Each reference to a separate document or artifact in this work must be listed here and must be identified as either a Normative or an Informative Reference. Normative references are specific (identified by date of publication and/or edition number or version number) and Informative references are either specific or non-specific.

While any hyperlinks included in this appendix were valid at the time of publication, OASIS cannot guarantee their long-term validity.

(Note - Reference sources:

For references to IETF RFCs, use the approved citation formats at:  
http://docs.oasis-open.org/templates/ietf-rfc-list/ietf-rfc-list.html.

For references to W3C Recommendations, use the approved citation formats at:  
http://docs.oasis-open.org/templates/w3c-recommendations-list/w3c-recommendations-list.html.

Remove this note before submitting for publication.)


## A.1 Normative References

The following documents are referenced in such a way that some or all of their content constitutes requirements of this document.
<!-- 
###### [OpenC2-HTTPS-v1.0]
_Specification for Transfer of OpenC2 Messages via HTTPS Version 1.0_. Edited by David Lemire. Latest stage: http://docs.oasis-open.org/openc2/open-impl-https/v1.0/open-impl-https-v1.0.html
###### [OpenC2-SLPF-v1.0]
_Open Command and Control (OpenC2) Profile for Stateless Packet Filtering Version 1.0_. Edited by Joe Brule, Duncan Sparrell, and Alex Everett. Latest stage: http://docs.oasis-open.org/openc2/oc2slpf/v1.0/oc2slpf-v1.0.html
###### [RFC2119]
Bradner, S., "Key words for use in RFCs to Indicate Requirement Levels", BCP 14, RFC 2119, DOI 10.17487/RFC2119, March 1997, http://www.rfc-editor.org/info/rfc2119.
###### [RFC8174]
Leiba, B., "Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words", BCP 14, RFC 8174, DOI 10.17487/RFC8174, May 2017, http://www.rfc-editor.org/info/rfc8174. 
-->

## A.2 Informative References
<!-- 
###### [RFC3552]
Rescorla, E. and B. Korver, "Guidelines for Writing RFC Text on Security Considerations", BCP 72, RFC 3552, DOI 10.17487/RFC3552, July 2003, https://www.rfc-editor.org/info/rfc3552.
-->
-------

# Appendix B. ABC


-------

# Appendix C. Acknowledgments
<!--
`(Note: A Work Product approved by the OP should include a list of people who participated in the development of the Work Product. This is generally done by collecting the list of names in this appendix. This list should be initially compiled by the Chair, and any Member of the OP may add or remove their names from the list by request. Remove this note before submitting for publication.)`
-->
## C.1 Special Thanks

<!-- This is an optional subsection to call out contributions from OP members. If a OP wants to thank non-OP members then they should avoid using the term "contribution" and instead thank them for their "expertise" or "assistance". -->

Substantial contributions to this document from the following individuals are gratefully acknowledged:

Participant Name, Affiliation or "Individual Member"

## C.2 Participants

<!-- An OP can determine who they list here. It is common practice for OPs to list everyone that was part of the OP during the creation of the document, but this is ultimately an OP decision on who they want to list and not list. -->

The following individuals have participated in the creation of this specification and are gratefully acknowledged:

**Project-name OP Members:**

| First Name | Last Name | Company |
| :--- | :--- | :--- |
x | x | Something Networks
x | x | Company B
x | x | Mini Micro
x | x | Big Networks

-------

# Appendix D. Revision History

Revisions made since the initial stage of this numbered Version of this document may be tracked here.

If revision tracking is handled in another system like github, provide a link to it instead of using this table, if desired.

| Revision | Date | Editor | Changes Made |
| :--- | :--- | :--- | :--- |
| baseline-core-v1.0-psd01 | 2020-09-29 | Anais Ofranc | Initial working draft |

-------
<!--
# Appendix E. Example Appendix with subsections

## E.1 Subsection title

### E.1.1 Sub-subsection
-->
-------

# Appendix F. Notices

<!-- This required section should not be altered, except to modify the license information in the second paragraph -->


Copyright © OASIS Open 2020. All Rights Reserved.

All capitalized terms in the following text have the meanings assigned to them in the OASIS Intellectual Property Rights Policy (the "OASIS IPR Policy"). The full [Policy](https://www.oasis-open.org/policies-guidelines/ipr) may be found at the OASIS website.

This specification is published under the [CC0 1.0 Universal (CC0 1.0)](http://creativecommons.org/publicdomain/zero/1.0/) license. Portions of this specification are also provided under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

All contributions made to this project have been made under the [OASIS Contributor License Agreement (CLA)](https://www.oasis-open.org/policies-guidelines/open-projects-process#individual-cla-exhibit).

For information on whether any patents have been disclosed that may be essential to implementing this specification, and any offers of patent licensing terms, please refer to the [Open Projects IPR Statements](https://github.com/oasis-open-projects/administration/blob/master/IPR_STATEMENTS.md) page.

This document and translations of it may be copied and furnished to others, and derivative works that comment on or otherwise explain it or assist in its implementation may be prepared, copied, published, and distributed, in whole or in part, without restriction of any kind, provided that the above copyright notice and this section are included on all such copies and derivative works. However, this document itself may not be modified in any way, including by removing the copyright notice or references to OASIS, except as needed for the purpose of developing any document or deliverable produced by an OASIS Open Project (in which case the rules applicable to copyrights, as set forth in the OASIS IPR Policy, must be followed) or as required to translate it into languages other than English.

The limited permissions granted above are perpetual and will not be revoked by OASIS or its successors or assigns.

This document and the information contained herein is provided on an "AS IS" basis and OASIS DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE. OASIS AND ITS MEMBERS WILL NOT BE LIABLE FOR ANY DIRECT, INDIRECT, SPECIAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF ANY USE OF THIS DOCUMENT OR ANY PART THEREOF.

As stated in the OASIS IPR Policy, the following three paragraphs in brackets apply to OASIS Standards Final Deliverable documents (Project Specifications, OASIS Standards, or Approved Errata).

\[OASIS requests that any OASIS Party or any other party that believes it has patent claims that would necessarily be infringed by implementations of this OASIS Standards Final Deliverable, to notify OASIS TC Administrator and provide an indication of its willingness to grant patent licenses to such patent claims in a manner consistent with the IPR Mode of the OASIS Open Project that produced this deliverable.\]

\[OASIS invites any party to contact the OASIS TC Administrator if it is aware of a claim of ownership of any patent claims that would necessarily be infringed by implementations of this OASIS Standards Final Deliverable by a patent holder that is not willing to provide a license to such patent claims in a manner consistent with the IPR Mode of the OASIS Open Project that produced this OASIS Standards Final Deliverable. OASIS may include such claims on its website, but disclaims any obligation to do so.\]

\[OASIS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this OASIS Standards Final Deliverable or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on OASIS' procedures with respect to rights in any document or deliverable produced by an OASIS Open Project can be found on the OASIS website. Copies of claims of rights made available for publication and any assurances of licenses to be made available, or the result of an attempt made to obtain a general license or permission for the use of such proprietary rights by implementers or users of this OASIS Standards Final Deliverable, can be obtained from the OASIS TC Administrator. OASIS makes no representation that any information or list of intellectual property rights will at any time be complete, or that any claims in such list are, in fact, Essential Claims.\]

The name "OASIS" is a trademark of [OASIS](https://www.oasis-open.org/), the owner and developer of this specification, and should be used only to refer to the organization and its official outputs. OASIS welcomes reference to, and implementation and use of, specifications, while reserving the right to enforce its marks against misleading uses. Please see https://www.oasis-open.org/policies-guidelines/trademark for above guidance.
