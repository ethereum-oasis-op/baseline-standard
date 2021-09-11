
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
&nbsp;&nbsp;&nbsp;&nbsp;[1.0 IPR Policy](#10-ipr-policy) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.1 Terminology](#11-terminology) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.2 Normative References](#12-normative-references) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.3 Non-Normative References](#13-non-normative-references) \
&nbsp;&nbsp;&nbsp;&nbsp;[1.4 Typographical Conventions](#14-typographical-conventions) \
[2 API Overview](#2-design-and-architecture) \
[3 Baseline](#3-api) \
&nbsp;&nbsp;&nbsp;&nbsp;[3.1 Create Objects](#31-create-objects) \
[4 CCSM](#4-ccsm) \
[5 Privacy](#5-privacy) \
[6 Registry](#6-registry) \
[7 Vault](#7-vault) \
[8 Schemas](#8-schemas) \
[9 Conformance](#9-conformance) \
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
## 1.3 Non-Normative References
## 1.4 Typographical Conventions

-------

# 2 API Overview

This section defines the key concepts and architectural principles of the API and Data model(s).


-------

# 3 Baseline


| URL | Methods  |  Resource Type | 
| :--- | :--- | :--- |
| {api-root}/objects/ | Post, Put | objects |
| {api-root}/states/ | Get | states |
| {api-root}/workflows/ | Get, Post| workflows |
| {api-root}/workflows/{id} | Get| |
| {api-root}/workflows/{id}/worksteps | Get, Post| |
| {api-root}/workflows/{id}/worksteps/{workstep_id} | Get| |
| {api-root}/workgroups/ | Get, Post |  |
| {api-root}/workgroups/{id} | Get, Put|  |
| {api-root}/workgroups/{id}/users | Get, Post |  |

## 3.1 Create Objects


```
  /objects:
    post:
      deprecated: false
      description: 'Creates a Baseline object using the parameters provided in the request body'
      operationId: createBaselineObject
      parameters: []
      requestBody:
        content:
          application/json:
            example:
              workflowinstance_id: af96a1bb-0c6d-4b6d-9b18-801d1db07a9d
              opcode: BLINE
              payload:
                proof: '8d8f7498db7aee910428c737d8427ac4add98353f981ca70db07697a091d8c23972b55b0b20fc0eebc1ac6c2ae427d783291c7fcb2e3f7417d279fea78ce1eac2d2293e53579abbef4960a1e290bd023e2999d8ff423d01080d449ce5d14ca89c94e277e8e0bb14fb91a0b71129920ae4411e77685287611f4d2aaf66b8fc5dc'
                type: general_consistency
                witness: {}
              type: general_consistency
            schema:
              $ref: '#/components/schemas/Object'
        required: true
      responses:
        '201':
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Object'
          description: The request was successful and a new object was created.
        '401':
          $ref: '#/components/responses/Unauthorized'
        '403':
          $ref: '#/components/responses/Forbidden'
        '404':
          $ref: '#/components/responses/NotFound'
        '429':
          $ref: '#/components/responses/TooManyRequests'
        '500':
          $ref: '#/components/responses/InternalServerError'
        '503':
          $ref: '#/components/responses/ServiceUnavailable'
```

## 3.2 Create Objects

## 3.3
## 3.4
## 3.5
## 3.6
## 3.7
## 3.8
## 3.9
## 3.10
## 3.11
## 3.12
## 3.13
## 3.14
## 3.15
## 3.16


-------

# 4 CCSM

| URL | Methods  |  Resource Type | 
| :--- | :--- | :--- |
| {api-root}/bpisubjectaccounts | Get, Post|  |
| {api-root}/bpisubjectaccounts/{account_id} | Get |  |
| {api-root}/contracts/ | Get, Post| workflows |
| {api-root}/contracts/{id}| Get |  |
| {api-root}/contracts/{id}/execute| Post |  |
| {api-root}/networks| Get,Post |  |
| {api-root}/networks/{id}| Put|  |
| {api-root}/networks/{id}/status| Get |  |
| {api-root}/transactions| Get, Post |  |
| {api-root}/transactions/{id}| Get |  |
| {api-root}/wallets| Get, Post |  |
| {api-root}/wallets/{id}/accounts| Get |  |

## 4.1
## 4.2
## 4.3
## 4.4
## 4.5
## 4.6
## 4.7
## 4.8
## 4.9
## 4.10
## 4.11
## 4.12
## 4.13
## 4.14
## 4.15
## 4.16



-------

# 5 Privacy

| URL | Methods  |  Resource Type | 
| :--- | :--- | :--- |
| {api-root}/provers/ | Get, Post |  |
| {api-root}/provers/{id} | Get | |
| {api-root}/provers/{id}/notes/{index}| Get | |
| {api-root}/provers/{id}/nullifiers/{index} | Get |  |
| {api-root}/provers/{id}/prove | Psot | |
| {api-root}/provers/{id}/verify | Post |  |

## 5.1 
## 5.2 
## 5.3 
## 5.4 
## 5.5 
## 5.6 
## 5.7 

-------

# 6 Registry

| URL | Methods  |  Resource Type | 
| :--- | :--- | :--- |
| {api-root}/organizations/ | Get, Post| organizations |
| {api-root}/organizations/{id} | Get, Put |  |
| {api-root}/workgroups/ | Get, Post| workgroups |
| {api-root}/workgroups/{id} | Get, Put |  |
| {api-root}/workgroups/{id}/users| Get, Post |  |

## 6.1 
## 6.2
## 6.3
## 6.4
## 6.5
## 6.6
## 6.7
## 6.8
## 6.9
## 6.10

-------

# 7 Vault

| URL | Methods  |  Resource Type | 
| :--- | :--- | :--- |
| {api-root}/vaults | Get, Post | vaults|
| {api-root}/vaults/{id}/keys | Get, Post | keys |
| {api-root}/vaults/{id}/keys/{key_id} | Delete | |
| {api-root}/vaults/{id}/keys/{key_id}/derive | Post |  |
| {api-root}/vaults/{id}/secrets| Get, Post |  |
| {api-root}/vaults/{id}/secrets/{secret_id}| Get, Delete |  |
| {api-root}/unseal | Post| |


## 7.1 Create vaults 

```
/vaults:
    post:
      deprecated: false
      description: Creates a `Vault` instance using the parameters provided in the request body
      operationId: createVault
      parameters: []
      requestBody:
        content:
          application/json:
            example:
              description: Example vault description
              name: Example vault name
            schema:
              $ref: '#/components/schemas/Vault'
        required: true
      responses:
        '201':
          content:
            application/json; charset=UTF-8:
              schema:
                $ref: '#/components/schemas/Vault'
          description: The request was successful and a new vault has been created.
        '401':
          $ref: '#/components/responses/Unauthorized'
        '403':
          $ref: '#/components/responses/Forbidden'
        '404':
          $ref: '#/components/responses/NotFound'
        '429':
          $ref: '#/components/responses/TooManyRequests'
        '500':
          $ref: '#/components/responses/InternalServerError'
        '503':
          $ref: '#/components/responses/ServiceUnavailable'

```

## 7.2 Get list of vaults 

```
/vaults:
    get:
      deprecated: false
      description: Returns a list of `Vault` instances in the authorized scope
      operationId: listVaults
      parameters:
        - $ref: '#/components/parameters/page'
        - $ref: '#/components/parameters/results-per-page'
      responses:
        '200':
          content:
            application/json; charset=UTF-8:
              schema:
                items:
                  $ref: '#/components/schemas/Vault'
                type: array
          description: The request was successful and a list of vaults has been returned.
          headers:
            X-Total-Results-Count:
              $ref: '#/components/headers/X-Total-Results-Count'
        '401':
          $ref: '#/components/responses/Unauthorized'
        '403':
          $ref: '#/components/responses/Forbidden'
        '404':
          $ref: '#/components/responses/NotFound'
        '429':
          $ref: '#/components/responses/TooManyRequests'
        '500':
          $ref: '#/components/responses/InternalServerError'
        '503':
          $ref: '#/components/responses/ServiceUnavailable'
      summary: List vaults
      tags:
        - Vault
```



## 7.3

```

```
 
## 7.4 

```

```

## 7.5 

```

```

## 7.6 

```

```

## 7.7 

```

```

## 7.8 

```

```

## 7.9 

```

```

## 7.10 

```

```

## 7.11 

```

```

-------

# 8 Schemas



-------

# 9 Conformance





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

evisions made since the initial stage of this numbered Version of this document have been tracked on [Github](https://github.com/eea-oasis/baseline-standard/blob/main/api/baseline-api-v1.0-psd01.md).

