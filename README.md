# Hybox Modeling as Modeling Exemplar

## Goal

Use and expand the Hybox Modeling work and documentation done so far so it can serve as an exemplar of data modeling in action.

This work to make a modeling exemplar project involves:

1. Generating further documentation about the models given ;
2. Update examples, sample RDF for the chosen models ;
3. Look into creating machine-actionable metadata application profiles ;
2. Evaluating the implementation of those models and profiles in the Hybox Sufia application layer ;
3. Documenting that data/conceptual model to application layer for more general Hydra reference, discussion.

## Scope

The scope of this work includes:

* Data Modeling
  * The structures and usage of the actual content

* Metadata Modeling
  * Descriptive
  * Administrative
  * Rights
  * Technical

* Linked Data modeling of technical requirements
  * Ontology selection and development where no existing ontology suffices
  * JSON-LD context and frame specification

* Protocol requirements regarding Linked Data
  * Web ACL
  * LDP projection

* Review Models versus Implementation through:
  * Fedora 4 - Hydra / Sufia stack
  * APIs (?)
  * Implementation pattern requirements
  * Behaviors


## Agreements

* All models will be in RDF, following the Linked Data best practices
* Core ontologies to build application profiles on include PCDM, DC, EDM/DPLA, FOAF, WebACL, ...
* JSON-LD will a primary serialization
* LDP will be the base interaction model
* We will use the outcomes of Hydra Metadata WGs and engage with them

