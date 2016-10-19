
## Works

### Introduction

Works are a digital repository object core class. They represent the digital repository resource specifically being managed, retrieved, displayed.

The profile, structure, and expectations of Works change according to the Work or Object types (brought out more in the Use Cases), but the information below is core. The concept of a Work here is the class of resource primarily being indexed, displayed, preserved, managed or updated - as opposed to Related Resources or Parts.

Something about relationship of Works to Bibliographic Resource RWOs.

### Model

#### pcdm:Object < hydra-works:Work

| Field            | Predicate              | Recommendation                     | Expected Value    |
| ---------------- | ---------------------- | ---------------------------------- | ----------------- |
| *Label*          | rdfs:label             | MUST, unless dct:title is supplied | Literal           |
| *Title*          | dct:title              | SHOULD                             | Literal           |
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


* dcterms:creator (SHOULD)
* dc:date (SHOULD)
* dc:description (SHOULD)
* dc:language (SHOULD)
* dc:rights (SHOULD)
* dcterms:rightsHolder (SHOULD)
* dcterms:subject (SHOULD)
* dcterms:isPartOf (MAY)
* edm:hasType (MAY)
* dcterms:medium (MAY)
* bf:identifiedBy (MAY)
* dcterms:contributor (MAY)
* dcterms:publisher (MAY)
* marcrel:rps (MAY)
* dcterms:extent (MAY)
* dcterms:spatial (MAY)
