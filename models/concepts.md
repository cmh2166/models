
## Concepts (Topics)

### Introduction

Concepts are a key, context class (i.e. not a digital repository object core class). They are primarily topical and cover general or abstract areas (i.e. subjects like "Love"), but can also represent groups of objects (i.e. "Trombones" or "Firefighters").

There are four possibilities for including Concepts in repository object metadata, enumerated below:

1. keep Concepts as a Class, but always an externally-managed resource for instance data (i.e. each new field that expects an Concept instance will take a URI for an external to the repository system that represents the Concept - id.loc.gov, AAT, FAST, local systems, etc.)
2. keep Concepts as a Class, but always an internally-managed resource for instance data (i.e., the underlying Fedora instance will manage all Concept instances, and relations to external system URIs will be synced through sameAs assertions on the Fedora-managed Concept resources).
3. keep Concepts as a Class, and could be externally or internally managed URIs (if no external URI, create an internal resource/URI).
4. captured Concept through a datatype property / string literal field on the digital repository object resources (following many repositories' current practice).

Pros/cons of these are discussed in the Implementation of Context Classes document.

### Model

If implementation option 2 or 3 is selected, this is the proposed model for Agent:

#### skos:ConceptScheme

| Field            | Predicate              | Recommendation | Expected Value |
| ---------------- | ---------------------- | -------------- | -------------- |
| *Label*          | rdfs:label             | MUST           | Literal        |
| *About*          | dcterms:description    | MAY            | Literal        |

#### skos:Concept

| Field             | Predicate       | Recommendation | Expected Value |
| ----------------- | --------------- | -------------- | -------------- |
| *Label*           | rdfs:label      | MUST           | Literal        |
| *Preferred Label* | skos:prefLabel  | SHOULD         | Literal        |
| *Alternate Label* | skos:altLabel   | MAY            | Literal        |
| *Definition*      | skos:definition | MAY            | Literal        |
| *Scheme*          | skos:inScheme   | MAY            | Literal        |
| *Note*            | skos:note       | MAY            | Literal |
| *Broader Term*    | skos:broader    | MAY            | Literal |
| *Narrower Term*   | skos:narrower   | MAY            | Literal |
| *Close Match*     | skos:closeMatch | MAY            | Literal |
| *Exact Match*     | skos:exactMatch | MAY            | Literal |

### Usage

#### Defining New Concepts

```
<repo:/concepts/scifi> a skos:Concept ;
  skos:inScheme <repo:/schemes/genres> ;
  skos:prefLabel "Sci-Fi"@en ;
  skos:definition "Science Fiction" ;
  skos:note "Created 2016/07/20 to have a more friendly prefLabel" ;
  skos:exactMatch <http://id.loc.gov/authorities/genreForms/gf2014026529> .

<repo:/schemes/genres> a skos:ConceptScheme ;
  rdfs:label "Local Genre classifications" .
```

#### References to Concepts

Concepts can be referenced in the following ways:

 * bf:classification for a classification of the resource (e.g. some LCCN)
 * dcterms:subject for the subject or topic of the resource (e.g. Star Wars)
 * edm:hasType for the genre of the resource (e.g. SciFi)
 * dcterms:medium for the carrier type of the resource (e.g. DVD)

```
<repo:/descriptions/object1> a bf:Work ;
  bf:classification <repo:/concepts/subject1> ;
  dcterms:subject <repo:/concepts/subject2> ;
  edm:hasType <repo:/concepts/genre1> ;
  dcterms:medium <repo:/concepts/carrier1> .
```

### External Taxonomies

The use of external taxonomies (concept schemes) is encouraged.  Several appropriate SKOS concept schemes can be found via the following URLs:

* http://id.loc.gov/
* http://www.getty.edu/research/tools/vocabularies/index.html
* https://www.w3.org/2001/sw/wiki/SKOS/Datasets

