# Baseline Protocol Specifications

![Baseline Logo](https://raw.githubusercontent.com/ethereum-oasis/baseline/master/docs/assets/baseline-logo/Web/examples/PNGs/horizontal/baselineHorizontal-Logo-FullColor.png)

*Read the full documentation at [docs.baseline-protocol.org](https://docs.baseline-protocol.org/).*

*Join our [Slack workspace](https://communityinviter.com/apps/ethereum-baseline/join-us), view our [Youtube Channel](https://www.youtube.com/channel/UCPkZ73TH69tMBaC111wxHYw) and follow us on [Twitter](https://twitter.com/baselineproto) for Baseline Protocol news and updates!* 

## The Baseline API & Data Model Specification

The document describes the Baseline programming interface and expected behaviors of all instances of this interface together with the required programming interface data model.

## Status

The Baseline API & Data Model Specification is currently in its first release as a draft specification (V0.1).

## Components

<table>
<tr>
    <th>Component</th>
    <th>Component Description</th>
  </tr>
  <tr>
    <td>Baseline</td>
    <td> Baseline core provides internal integration middleware interfaces for baselining systems of record.</td>
  </tr>
  <tr>
    <td>CCSM</td>
    <td>Baseline core CCSM API provides interfaces for general interaction with the underlying CCSM.</td>
  </tr>
  <tr>
    <td>Privacy</td>
    <td>Baseline core privacy provides interfaces supporting general consistency, zero-knowledge cryptography protocols and secure multi-party computation (MPC).</td>
  </tr>
  <tr>
    <td>Registry</td>
    <td>Utilities for resolving DID documents for arbitrary subjects.</td>
  </tr>
  <tr>
    <td>Vault</td>
    <td>Baseline core vault API provides tools and methods for managing digital authentication credentials for Subjects based on roles and `Workgroup` instances.</td>
  </tr>
  <tr>
    <td>Schemas</td>
    <td>Baseline core data schemas used in the Baseline, CCSM, Privacy, Registry and Vault API modules.</td>
  </tr>
  <tr>
    <td>Conformance</td>
    <td>Describes the conformance clauses and tests required to achieve baseline compliant implementations.</td>
  </tr>
</table>

## License

All contribution in this repo is released under the CC0 1.0 Universal public domain dedication. For the full license text, refer to [LICENSE](https://github.com/ethereum-oasis/baseline/blob/master/LICENSE).

## Contributions

To participate in the evolution of Baseline via the specs process, please see our [Contributors Guidelines](https://docs.baseline-protocol.org/community/contributors).
