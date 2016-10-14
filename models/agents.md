
## Agents

### Introduction

Agents are a key, context class (i.e. not a digital repository object core class). They can be Agents that act on resources in the repository (i.e. authenticated users in the repository application) or act on resources outside the context of the repository (i.e. physical/analog resource creators, publishers, contributors, agents depicted in the resource, etc.).

There are four possibilities for including agents in repository object metadata, enumerated below:

1. keep Agents as a Class, but always an externally-managed resource for instance data (i.e. each new field that expects an Agent instance will take a URI for an external to the repository system that represents the Agent - id.loc.gov, ULAN, local systems, etc.)
2. keep Agents as a Class, but always an internally-managed resource for instance data (i.e., the underlying Fedora instance will manage all Agent instances, and relations to external system URIs will be synced through sameAs assertions on the Fedora-managed Agent resources).
3. keep Agents as a Class, and could be externally or internally managed URIs (if no external URI, create an internal resource/URI).
4. captured Agent information through a datatype property / string literal field on the digital repository object resources (following many repositories' current practice).

5. Another option: Follow the VIVO model and create VCard resources for Agent entries which have very little information / could or probably will become better defined Agent resources in the future (or don't matter).

Pros/cons of these are discussed in the Implementation of Context Classes document.

Compare to [Authorities Vitro Pilot](https://github.com/cul-it/lts-vitro-pilot/wiki#foafperson--madsrdfauthority) work?

### Model

If implementation option 2 or 3 is selected, this is the proposed model for Agent:

#### foaf:Agent (broader than Person or Organization)

| Field            | Predicate             | Recommendation                     | Expected Value |
| ---------------- | --------------------- | ---------------------------------- | -------------- |
| *Label*          | rdfs:label            | MUST, unless foaf:name is supplied | Literal        |
| *Preferred Name* | foaf:name             | SHOULD                             | Literal        |
| *Alternate Name* | schema:additionalName | MAY                                | Literal        |
| *Email*          | foaf:mbox             | MAY                                | Literal        |
| *Homepage*       | foaf:homepage         | MAY                                | URL            |
| *About*          | dcterms:description   | MAY                                | Literal        |
| *Identifier*     | bf:identifiedBy       | SHOULD (if applicable)             | bf:Identifier  |

#### foaf:Person < foaf:Agent ; Entailment with bibframe:Person, schema:Person

| Field            | Predicate              | Recommendation                     | Expected Value    |
| ---------------- | ---------------------- | ---------------------------------- | ----------------- |
| *Label*          | rdfs:label             | MUST, unless foaf:name is supplied | Literal           |
| *Preferred Name* | foaf:name              | SHOULD                             | Literal           |
| *Alternate Name* | schema:additionalName  | MAY                                | Literal           |
| *Email*          | foaf:mbox              | MAY                                | Literal           |
| *Homepage*       | foaf:homepage          | MAY                                | URL               |
| *About*          | dcterms:description    | MAY                                | Literal           |
| *Family Name*    | foaf:familyName        | MAY                                | Literal           |
| *Given Name*     | foaf:givenName         | MAY                                | Literal           |
| *Prefix*         | schema:honorificPrefix | MAY                                | Literal           |
| *Suffix*         | schema:honorificSuffix | MAY                                | Literal           |
| *Gender*         | foaf:gender            | MAY                                | Literal           |
| *Birthdate*      | schema:birthDate       | MAY                                | Date              |
| *Birth Place*    | schema:birthPlace      | MAY                                | edm:Place         |
| *Date of death*  | schema:deathDate       | MAY                                | Date              |
| *Place of death* | schema:deathPlace      | MAY                                | Literal           |
| *Nationality*    | schema:nationality     | MAY                                | Literal           |
| *Knows*          | foaf:knows             | MAY                                | foaf:Person       |
| *Affiliation*    | schema:affiliation     | MAY                                | foaf:Organization |
| *Identifier*     | bf:identifiedBy        | SHOULD (if applicable)             | bf:Identifier     |

#### foaf:Organization

| Field            | Predicate              | Recommendation                     | Expected Value    |
| ---------------- | ---------------------- | ---------------------------------- | ----------------- |
| *Label*          | rdfs:label             | MUST, unless foaf:name is supplied | Literal           |
| *Preferred Name* | foaf:name              | SHOULD                             | Literal           |
| *Alternate Name* | schema:additionalName  | MAY                                | Literal           |
| *Email*          | foaf:mbox              | MAY                                | Literal           |
| *Homepage*       | foaf:homepage          | MAY                                | URL               |
| *About*          | dcterms:description    | MAY                                | Literal           |
| *Based Near*     | foaf:basedNear         | MAY                                | edm:Place         |
| *Knows*          | foaf:knows             | MAY                                | foaf:Person       |
| *Affiliation*    | schema:affiliation     | MAY                                | foaf:Organization |
| *Identifier*     | bf:identifiedBy        | SHOULD (if applicable)             | bf:Identifier     |


If implementation option 1 or 3 is selected, this is the expected, minimal assertions for external Agent resources once dereferenced for display purposes:

 * rdfs:label or skos:prefLabel or foaf:name

### Usage

#### Defining New Agents

```
<repo:/agents/cmh2166> a foaf:Agent ;
   rdfs:label "Christina Harlow" .
```

### References to Agents

* dcterms:creator
* dcterms:contributor
* dcterms:publisher
* dcterms:rightsHolder
* MARC Relators: http://id.loc.gov/vocabulary/relators.html



