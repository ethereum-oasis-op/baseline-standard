
![OASIS Logo](http://docs.oasis-open.org/templates/OASISLogo-v2.0.jpg)
-------

# Baseline DLT Specification Version 1.0

## Project Specification Working Draft

## 29 April 2021

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
_Baseline DLT Requirements version 1.0_ - https://github.com/ethereum-oasis/baseline/tree/master/docs/specs/dlt


#### Abstract:
The document describes the minimal set of business and technical prerequisites, functional and non-functional requirements for a Distributed Ledger Technology (DLT) network that when utilized ensures that two or more systems of record can synchronize their system state over said DLT securely and privately.

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

**[baseline-dlt-v1.0]**

_Baseline DLT Requiements Version 1.0_. Edited by Anais Ofranc. 29 September 2020. OASIS Project Specification Draft 01. https://docs.oasis-open.org/baseline/baseline-dlt/v1.0/psd01/baseline-dlt-v1.0-psd01.html. Latest stage: https://docs.oasis-open.org/baseline/baseline-dlt/v1.0/baseline-dlt-v1.0.html.

-------

## Notices
Copyright © OASIS Open 2021. All Rights Reserved.

Distributed under the terms of the OASIS [IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr).

For complete copyright information please see the Notices section in the Appendix.

-------

# Table of Contents
[1 Introduction](#1-introduction) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.1 Glossary](#11-glossary) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.2 Typographical Conventions](#12-typographical-conventions) \
[2 Security](#2-Security) \
[3 Privacy](#3-Privacy) \
[4 Scalability](#4-Scalability) \
[5 Interoperability](#5-Interoperability) \
[6 Network](#6-Network)  \
[7 Consensus](#7-Consensus) \
[8 Virtual State Machine](#8-Virtual-State-Machine) \
[9 Data Integrity & Transaction Completeness ](#9-Data-Integrity-&-Transaction-Completeness) \
[10 Integration to External Applications](#10-Integration-to-External-Applications) \
[11 Conformance](#11-conformance) \
&nbsp;&nbsp;&nbsp;&nbsp;[11.1 Conformance Targets](#111-conformance-targets) \
&nbsp;&nbsp;&nbsp;&nbsp;[11.2 Conformance Levels](#112-conformances-levels)\
&nbsp;&nbsp;&nbsp;&nbsp;[11.3 Interoperability](#113-interoperability)\
[Appendix A.        Acknowledgments]()\
[Appendix B.        Revision History]()

-------

# 1 Introduction

Distributed Ledger Technology (DLT) is the foundational enabler of a Baseline Protocol Instance (BPI) with no or limited trust assumptions. The requirements that a DLT must satisfy for it to be used in a BPI as defined in the Baseline Standard fall in the following categories:
1. Security
2. Privacy
3. Scalability
4. Interoperability
5. Network
6. Consensus
7. Virtual State Machine
8. Data Integrity & Transaction Completeness 
9. Integration to External Applications

In the requirements below we will refer to "The DLT" to mean a DLT chosen by the participants to implement a BPI.


## 1.2 Glossary

**Baseline Protocol:**

The Baseline Protocol is a set of methods that enable two or more state machines to achieve and maintain data consistency, and workflow continuity by using a network as a common frame of reference. 

**Byzantine Fault Tolerant(BFT):**

Given a network or system of n components, t of which are dishonest, and assuming only point-to-point channels between all the components, then whenever a component A tries to broadcast a value x such as a block of transactions, the other components are permit-ted to discuss with each other and verify the consistency of A's broadcast, and eventually settle on a common value y. The system is then considered to resist Byzantine faults if a component A can broadcast a value x, and then:
* If A is honest, then all honest components agree on the value x.
* If A is dishonest, all honest components agree on the common value y.

"The Byzantine Generals Problem", Leslie Lamport, Robert E. Shostak, Marshall Pease, ACM Transactions on Programming Languages and Systems, 1982

**Distributed Ledger Technology(DLT):**

Distributed Ledger Technology is a digital system for recording the transaction of assets in which the transactions and their details are recorded in multiple places at the same time. Unlike traditional databases, distributed ledgers have no central data store or administration functionality.

University of Cambridge, Cambridge Judge Business School – Defining DLT, August 2018

**Interoperability:**

The ability of a Party operating Workflows on a baseline-compliant implementation A to instantiate and operate one or more Workflows with one or more Party on a baseline-compliant implementation B without the Party on either implementation A or B having to know anything of the other Party’s implementation.

**Liveness:**
In concurrent computing, liveness refers to a set of properties of concurrent systems, that require a system to make progress, despite its concurrently executing components ("processes") may have to "take turns" in critical sections, parts of the program that cannot be simultaneously run by multiple processes. Liveness guarantees are important properties in operating systems and distributed systems.

Alpern B, Schneider FB (1985) Defining liveness. Inf Proc Lett 21:181-185

**Party:**

A set of Parties participating in the execution of one or more given Workflows. A Workgroup is set up and managed by one Party that invites other Parties to join as workgroup members. 

**Proof of Correctness:**
A Proof of Correctness is a mathematical proof that a computer program or a part thereof will, when executed, yield correct results, i.e. results fulfilling specific requirements. Before proving a program correct, the theorem to be proved must, of course, be formulated. The hypothesis of such a correctness theorem is typically a condition that the relevant program variables must satisfy immediately before the program is executed. This condition is called the precondition. The thesis of the correctness theorem is typically a condition that the relevant program variables must satisfy immediately after execution of the program. This latter condition is called the postcondition. The thesis of a correctness theorem may be a statement that the final values of the program variables are a particular function of their initial values.

"Encyclopedia of Software Engineering",
Print ISBN: 9780471377375| Online ISBN: 9780471028956| DOI: 10.1002/0471028959,
(2002), John Wiley & Sons, Inc.

**Verifiably Secure:**

Verifiable computing that can be described as verifiably secure enables a computer to offload the computation of some function to other perhaps untrusted clients, while maintaining verifiable, and thus secure, results. The other clients evaluate the function and return the result with a proof that the computation of the function was carried out correctly. The proof is not absolute but is dependent on the validity of the security assumptions used in the proof. For example, a blockchain consensus algorithm where the proof of computation is the nonce of a block. Someone inspecting the block can assume with virtual certainty that the results are correct because the number of computational nodes that agreed on the outcome of the same computation is defined as sufficient for the consensus outcome to be secure in the consensus algorithm’s mathematical proof of security. 

Gennaro, Rosario; Gentry, Craig; Parno, Bryan (31 August 2010). Non-Interactive Verifiable Computing: Outsourcing Computation to Untrusted Workers. CRYPTO 2010. doi:10.1007/978-3-642-14623-7_25 

## 1.3 Typographical Conventions

- Naming conventions
- Font colors and styles
- Typographic conventions


-------

# 2. Security

DLT security is one of the most, if not the most important characteristic of a DLT. Therefore, great care has to be taken in its defintion, startting with the utilized cryptographic alogrithms and their implementations. 

**[R1]**	A DLT utilized in a BPI MUST support cryptographic algorithms based on commonly used and security-audited libraries.

The usage of cryptographic libraries that successfully passed the National Institute of Standards and Technology (NIST) Cryptographic Module Verification Program (CMVP) is recommended.

**[R2]**	If the DLT utilized in a BPI utilizes a Peer-to-Peer (P2P) message protocol, the protocol MUST support end-to-end encryption.

**[R3]**	The DLT utilized in a BPI MUST support DLT Node Key Management incl. backup and recovery that adheres to established industry security standards such as the US Federal Information Processing Standard (FIPS) or ISO 27001.

**[R4]**	The DLT utilized in a BPI SHOULD support programmatic economic security assurances.

Note, economic security assurances such as used in Proof-of-Stake consensus algorithms are designed to provide additional security assurances beyond those of cryptography in distributed systems. The security assurances are based on a system of economic incentives and disincentives for distributed system participants with the expressed goal that honest behavior of distributed system participants which enhances system security is in their economic self-interest. This is akin to determining if a cryptographic algorithm is secure or not, and what the level of security of said algorithm is, the security of a system of economic incentives and disincentives must be proven through a game theoretic security analysis.

**[D1]**	The DLT utilized in a BPI SHOULD be compatible with DLT protocol execution in Trusted Execution Environments (TEE)

Note, a TEE is a secure area of a main processor. It guarantees code and data loaded inside to be protected with respect to confidentiality and integrity. A TEE as an isolated execution environment provides security features such as isolated execution, integrity of applications executing with the TEE, along with confidentiality of their assets [[1]](####[1]).

Network attacks typically take the form of Distributed Denial of Service (DDOS) attacks, attacks from groups of malicious DLT nodes performing DLT reorganizations, front running of transactions through transaction injections, and censoring of transactions. This includes game theoretic attacks such as discouragement, extortion, value-extraction, or random oracle attacks.

**[R6]**	The DLT utilized in a BPI MUST support a secure consensus algorithm as explained in Section 8.

Note that secure in this context refers to the security of a consensus algorithm against attacks against its three main characteristics – consistency, availability, and fault tolerance. Therefore, a consensus algorithm is considered secure for a given set of operating assumptions:
* if all nodes produce the same valid output, according to the protocol rules, for the same message broadcast to the network (consistency/safety),
* if all non-faulty participating nodes produce an output indicating the termination, and subsequent restart, of the protocol upon reaching consensus (availability/liveness), and
* if the network exhibits the capability to perform as intended if network nodes fail, either unintentionally or intentionally (fault tolerance).

**[R7]**	A DLT utilized in a BPI MUST have one or more secure-by-construction or Verifiably Secure execution frameworks.

See the glossary for a definition of Verifiably Secure and more details about DLT supported execution frameworks in section 9.

# 3. Privacy
DLTs range in the level of privacy they support. One approach ensures that the contents of a DLT transaction or storage are meaningless to parties not participating in an interaction. Another more stringent approach is to use a DLT that precludes the accessibility of such information to non-participating parties. This standard sets the minimum requirement to the first approach, but the parties can agree to require that the BPI supports the second approach.

**[R8]**	The DLT utilized in a BPI MUST support privacy preservation such that the contents of a DLT transaction or DLT storage does not carry meaning to parties not participating in a DLT based interaction.

**[R9]**	The DLT utilized in a BPI MUST support privacy preservation of transactions and their execution.

**[R10]**	The DLT utilized in a BPI MUST support segregation between public and private state/data.

**[D2]**	The DLT utilized in a BPI SHOULD support a privacy-preserving P2P message protocol.

Privacy-preserving means in this context that at least the content of a message, and ideally, also the sender and recipient, is opaque to all participants of the P2P network except sender and recipient.

**[D3]**	The DLT utilized in a BPI SHOULD support Zero-Knowledge Proof (ZKP) Verification (if not generation) at the protocol level.

Zero-Knowledge Proofs (ZKPs) [[2]](####2) are powerful cryptographic methods by which one party (the prover) can prove to another party (the verifier) that they know a value x -- the password to an online bank account --, without conveying any information apart from the fact that they know the value x -- the password. The essence of zero-knowledge proofs is that it is trivial to prove that one possesses knowledge of certain information by simply revealing it; the challenge is to prove such possession without revealing the information itself or any additional information. When combined with DLTs, ZKPs allow participants to conduct business and exchange assets in the open without revealing anything about the business itself while any outside party can verify that the way business was conducted was in accordance with all applicable business and legal rules for a commercial transaction.

# 4. Scalability
To support the required commercial transaction volume between Baseline Protocol counterparties, the DLT utilized by a BPI should be chosen with these transaction volumes in mind. Especially, since in a public DLT setting there will be, potentially, a significant volume of transactions competing for scarce Block space. 

Since forecasting future transaction volumes is difficult and could rapidly change based on adoption, the considered DLTs should have some form of throughput future-proofing built in. Examples of such techniques include state channels, sidechains, rollup frameworks, state sharding, multiple execution frameworks and parallel process transaction support. This is not mandated in this standard and is considered a question of implementation to be addressed in an agreement by the users of a BPI.

# 4. Interoperability

**[D4]**	The DLT utilized in a BPI SHOULD support secure data sources.

This requirement means that a DLT has a mechanism to securely connect its state through for example a smart contract with a data source which has certain security assurances in such a way that a) the security of the data source is not compromised by the DLT and b) the security assurances of the DLT are not compromised by the secure data source.

**[D5]**	When transactions connect one DLT with another DLT for the purpose of interoperating assets or data across BPIs, and the DLTs use the same DLT Protocol, the DLTs utilized in a BPI SHOULD support asset and data locking techniques to prevent double-spend/usage of assets.

An example of such techniques is a two-phase lock relay bridge. Two-phase locking (2PL) is a concurrency control method that guarantees serializability. The protocol utilizes locks, applied by a DLT transaction to data/assets, which may block other DLT transactions from accessing the same data/assets during the transaction's life. This protocol requires support for DLT transaction receipts signaling DLT transaction lifecycle completeness. This approach requires a relay server (network) between the two DLTs which interacts with the locking/unlocking smart contracts on each of the DLTs. Since both DLTs operate the same DLT protocol the relay server can be a node on both networks which does not introduce further security assumptions.

**[D6]**	When transactions connect one DLT with another DLT for the purpose of interoperating assets or data across BPIs, and the DLTs use different DLT Protocols, the DLTs utilized in a BPI SHOULD support asset and data locking techniques to prevent double-spend/usage of assets.

An example of such techniques are Atomic Swap protocols. An atomic swap is a DLT smart contract technology that enables the exchange of one DLT asset for another without using centralized intermediaries, such as exchanges.

# 6. Network
Network in this context refers to the nodes of a DLT that form the DLT network. A DLT node has several components that impact the network namely its Peer-to-Peer (P2P) message protocol and its consensus algorithm. 

It is important that Peer-to-Peer (P2P) message protocols are used that do not require network nodes which act as message distribution hubs, e.g., leader nodes because network attacks on leader nodes can either cause unwanted network partitions or even network collapse.

**[R11]**	A DLT utilized in a BPI MUST support a P2P message protocol that does not require network leader nodes.

The network requirements on the consensus algorithms are even more stringent than on the P2P protocol. Additional requirements on the consensus algorithm of the DLT are discussed in the next section, section 7.

**[R12]** The DLT utilized in a BPI MUST be Byzantine Fault Tolerant (BFT) [[3]](####[3]).

**[R13]** The DLT utilized in a BPI MUST be able to operate under Weak Synchrony. 

Weak synchrony in this context means, 
1. 	that all messages will eventually reach their intended recipients and 
2. that after a certain, yet unknown, time the network will become synchronous again.

# 7. Consensus
The consensus algorithm is the most important component of a DLT as it ensures the consistency of the network at any given time. Therefore, the requirements on the consensus algorithms are very stringent.

**[R14]**	The DLT utilized in a BPI MUST be able to support more than one BFT consensus algorithm, also known as pluggable consensus.

Note, that deterministic BFT consensus algorithms lead to strong consistency, and, thus, immediate finality. Probabilistic BFT consensus algorithms lead to eventual consistency, and, thus, eventual finality.

**[R15]**	Consensus algorithms employed in the DLT utilized in a BPI MUST have a mathematical proof of security.

A mathematical proof of security is a collection of mathematically provable theorems that make security statements about the three characteristics of a consensus algorithm -- consistency/safety, availability/liveness and fault tolerance and is based on specific operating assumptions of the protocol.

**[D7]**	Consensus algorithms employed in the DLT utilized in a BPI SHOULD include economic security assurances with game theoretic security proofs.

**[D8]**	Consensus algorithms employed in the DLT utilized in a BPI SHOULD require not more than order N messages to reach consensus where N is the number of nodes in the network.

Note that the larger the number of nodes, the higher the level of security. Also, note that performance for certain consensus algorithms degrades quickly as the number of nodes increases because of the number of messages required to exchange between them to achieve consensus can grow very quickly. Therefore, algorithms that scale in the number of nodes without significant performance degradation are preferred. Also, note that network performance such as poor network latency can lead to severe issues such as consensus failure if an algorithm requires the exchange of large numbers of messages to reach consensus.

# 8. Virtual State Machine
DLTs most often utilize a virtual state machine (VSM) for DLT computations of DLT state transitions; a digital computer running on a physical computer. A VSM requires an architecture and execution rules which together define the Execution Framework. 

**[R16]**	The Execution Framework of the DLT utilized in a BPI MUST be deterministic.

All DLT nodes need to arrive at the same result based on the same input and execution instructions, in other words deterministic outcomes. This is only guaranteed if the Execution Framework either does not allow instructions to be executed in parallel, but only strictly sequential, or if the Execution Framework has methods in place that allow the identification and prevention of transactions that would cause DLT state conflicts, if processed in parallel. 

For example, the Buyer, also known as Requester, proposes a commercial state change of the MSA through Order A which is created at time t, and the Seller, also known as the Provider, has just agreed to a suggested discount rate change in the MSA submitted by the Buyer at time t-1 but not yet confirmed by DLT consensus. This means that if the transaction of the Order A is processed in parallel to the discount change the wrong discount might be applied to Order A depending which transaction is executed first.

**[R17]**	The Execution Framework of the DLT utilized in a BPI MUST ensure that state transition computations are either completed or abort in finite time, where what is deemed to be a suitable finite time is determined by the commercially allowable duration of a commercial transaction.

This requirement means that there cannot be infinite computational loops in a distributed computational system with consensus, as this would not allow the DLT network to reach consensus anymore and bring the DLT network itself to a halt. Note also, that when a DLT node is offline, the virtual state machine’s Execution Framework does not perform computations; when a DLT node comes back online, and synchronizes with the state of the DLT network, it only validates the last available state - either a global state or specific to that node. 

**[R18]**	The Execution Framework of the DLT utilized in a BPI MUST support widely used cryptographic operations natively, e.g., hashing, digital signatures, or zero-knowledge proof verification.

**[D9]**	The Execution Framework of the DLT utilized in a BPI SHOULD have a mathematical proof of correctness and security.

**[R19]**	The Execution Framework of the DLT utilized in a BPI MUST be Verifiably Secure. 

# 9. Data Integrity and Transaction Completeness
Data integrity over time, in other words the inability to alter data once it has been committed to the state of the DLT, is one of the key features of typical DLTs.

**[R20]**	If the DLT utilized in a BPI is strongly consistent (as defined in section 7), data committed to the state of the DLT MUST NOT be alterable after the DLT state has been finalized (as defined in section 7).

**[R21]**	If the DLT utilized in a BPI is eventually consistent (as defined in section 7), data committed to the state of the DLT MUST NOT be alterable after the DLT state has been final-ized (as defined in section 7). 

Besides data integrity, the notion of censorshipresistance, or the inability of anyone participant in a DLT to stop any other participant’s transaction to be eventually included in the DLT state, is another key feature of typical DLTs. It conveys the concept of a network without a central authority that can stop things from happening at will. This can be formalized as follows.

**[R22]**	The DLT utilized in a BPI MUST guarantee that a transaction compliant with the DLT protocol rules is eventually included in the state of the DLT, if the security assumptions of the utilized consensus protocol remain valid during transaction processing (see section 6 for details on the security assumptions of consensus algorithms).

The reason why the reference to the consensus algorithm is important is as follows: To guarantee processing of a transaction, one needs only one honest DLT node in the network. However, this is not sufficient to guarantee consensus. Therefore, and to include a submitted transaction in the DLT state, there needs to be an honest majority of DLT nodes to reach consensus on the submitted transaction.

# 10. Integration Capabilities with External Systems 

**[R23]**	The DLT utilized in a BPI MUST be compatible with widely used external authentication services. 

Non-normative examples of such authentication technologies are OAUTH [[4]](####[4]), SAML [[5]](####[5]), [[6]](####[6]), AD/LDAP [[7]](####[7]).

**[R23]**	The DLT utilized in a BPI MUST support roles & access management.

**[R24]**	The DLT utilized in a BPI MUST support policy management.

**[R25]**	The DLT utilized in a BPI MUST support Single-Sign-On (SSO) [[8]](####[8]).

**[R26]**	The DLT utilized in a BPI MUST support Multi-Factor authentication.

**[R27]**	The DLT utilized in a BPI MUST support Hardware Security Modules (HSMs)[[9]](####9).

# 11 Conformance

Describes the conformance clauses and tests required to achieve baseline compliant implementations.

## 11.1 Conformance Targets

Defines entities and implementations subject to conformance.


## 11.2 Conformance Levels

Defines conformance levels and their conformance clauses.

## 11.3 Interoperability

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

## A.1 Normative References

NA

## A.2 Informative References

#### [1] 
ISO/IEC 27033: Information technology — Security techniques — Network security - Parts 1 through 6 published by ISO

#### [2]
[23]	Quisquater, Jean-Jacques; Guillou, Louis C.; Berson, Thomas A. (1990). "How to Ex-plain Zero-Knowledge Protocols to Your Children". Advances in Cryptology – CRYPTO '89: Proceedings. Lecture Notes in Computer Science. 435. pp. 628–631. doi:10.1007/0-387-34805-0_60. ISBN 978-0-387-97317-3.

#### [3]
"The Byzantine Generals Problem", Leslie Lamport, Robert E. Shostak, Marshall Pease, ACM Transactions on Programming Languages and Systems, 1982

#### [4]
Aaron Parecki, (2020), “OAuth 2.0 Simplified”, ISBN-13: 978-1387751518

#### [5]
J. Hughes et al. Profiles for the OASIS Security Assertion Markup Language (SAML) V2.0. OASIS Standard, March 2005. Document identifier: saml-profiles-2.0-os

#### [6]
OpenID Connect Federation 1.0, (2019) 

#### [7]
“Directory System Agent". MSDN Library. Microsoft. (2018). 

#### [8]
"What's the Difference b/w SSO (Single Sign On) & LDAP?". JumpCloud. (2019)

#### [9]
Ramakrishnan, Vignesh; Venugopal, Prasanth; Mukherjee, Tuhin (2015). Proceedings of the International Conference on Information Engineering, Management and Security 2015: ICIEMS 2015. Association of Scientists, Developers and Faculties (ASDF). p. 9. ISBN 9788192974279.

## A.2 Informative References
<!-- 
###### [RFC3552]
Rescorla, E. and B. Korver, "Guidelines for Writing RFC Text on Security Considerations", BCP 72, RFC 3552, DOI 10.17487/RFC3552, July 2003, https://www.rfc-editor.org/info/rfc3552.
-->
-------

# Appendix B. Acknowledgments
<!--
`(Note: A Work Product approved by the OP should include a list of people who participated in the development of the Work Product. This is generally done by collecting the list of names in this appendix. This list should be initially compiled by the Chair, and any Member of the OP may add or remove their names from the list by request. Remove this note before submitting for publication.)`
-->
## B.1 Special Thanks

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
