# Schema Management

## Problem Description

To enable data exchange and functional interoperability between business Parties involved in a Baseline Workflow (or only Workstep?), there must be present a set of pre-agreed schemas. 

Furthermore, at least identifying different versions of the same schema must be possible for each Baseline instance. A Baseline instance may support different versions of the same schema.

## Schema
  
Minimum data model describing the structure of exchanged messages between different components and APIs. It must include list of mandatory fields/properties and their types and should include their description.

## Agreement on Schema
(in scope?)
An agreement could be _explicit_ with stating the list of agreed upon versioned schemas (e.g. structured as a Merkle Tree with schemas as leaves) by all the parties or _implicit_ by their implementation. 

(question: An explicit agreement could be seen as a commitment which makes Baseline processes (at least the intial setup) more expensive where an implicit one could be seen as a set of supported APIs which is already live but poses runtime incompatibility.)

## Reaching an Agreement on Schema
(in scope?)

## Managing Different Schemas

All the schemas must be available to all the Baseline instances involved in a Workflow (or only Workstep?).

Schemas may be made available publicly.

A Schema must be uniquely identifiable by the Baseline instances.

## Schema Management Component

Responsible to hold a registry (mapping) of which schemas are used in which working groups. (or Workflow/Wrokstep?)

(question: Is this component also responsible to store the schemas locally?)

## Components/APIs/interfaces require schema agreement
?

## Example of a Schema
?