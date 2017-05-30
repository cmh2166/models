# Works

## Introduction

Works are a digital repository object core class. They represent the digital repository resource specifically being retrieved, displayed, preserved, or otherwise generally managed by the repository.

The profile, structure, and expectations of Works change according to the Work (or Object) types, but the information below is core. The concept of a Work here is the class of resource primarily being indexed, displayed, preserved, managed or updated - as opposed to Related Resources or Parts.

There is an optional relationship (edm:isRepresentationOf) between the Work in our repository and a RWO representing the "Intellectual Work" in external datastores (say, our catalog). While one could, theoretically, have an Intellectual Work for each Digital Work Object Level (or the Digital Collection itself), we are limiting these RWOs or Intellectual Works for the time being to those represented roughly by bibliographic objects - with an eye to system efficiency and object interoperability in delineating this. Resource abstractions/domain models like FRBR or RDA:Work etc. are not to be used here. 'Work' is used in a broader way.

PCDM-Works:Work currently is the way to indicate Work right now, but it is set for removal from PCDM-Works the ontology. The indication of a "Work" as described here should be clear through context as well as typing. (fill more in here)

## Model

![Drawing of CUL Works modeling](https://docs.google.com/drawings/d/1iILGx-bHaEIERNjD8XXpNRDiYG21GaBQDji97Wk-O0w/pub?w=960&h=720)

I'll try to get together a drawing that just indicates relationship of the Work concept to the following values.

### `pcdm-works:Work`

Entailment with ... (from ...).

    ```turtle
    ex:Work a rdfs:Class ;
       ... .
    ```

| Field            | Predicate               | Recommendation | Expected Value | Obligation |
| ---------------- | ----------------------- | -------------- | -------------- | ---------- |
| *Abstract*       | `dct:abstract`      | MAY            | xs:string      | {0,n}      |
| *Alternative Title* | `dc:alternative` | MAY            | xs:string     | {0,n}      |
| *Bibliographic Citation* | `dct:bibliographicCitation` | MAY            | xs:string     | {0,n} |
| *Compiler* | `rdau:P50189` | MAY            | foaf:Agent    | {0,n} |
| *Contributor* | `dcterms:contributor` | MAY            | foaf:Agent    | {0,n} |
| *Copyright date* | `rdau:P60069` | MAY            | edtf date    | {0,n} |
| *Creator* | `dct:creator` | SHOULD            | foaf:Agent   | {0,n} |
| *Editor* | `rdau:P60393` | MAY            | foaf:Agent   | {0,n} |
| *Translator* | `rdau:P60613` | MAY            | foaf:Agent   | {0,n} |
| *Date Created (Work)* | `dct:created` | SHOULD            | edtf date   | {0,n} |

Extent	models/intellectual_work.rb	Intellectual Work	HydraWorks:Work	dcterms:extent	xs:string	{0,n}	extent
Format	models/intellectual_work.rb	Intellectual Work	HydraWorks:Work	dc:format	xs:string	{0,n}	format
Format URI	models/intellectual_work.rb	Intellectual Work	HydraWorks:Work	dcterms:format	URI < dcterms:MediaTypeOrExtent.	{0,n}	format_URI
Identifier	models/intellectual_work.rb	Intellectual Work	HydraWorks:Work	dcterms:identifier	literal (typed as DLXS ID)	{0,n}	identifier
Identifier (Catalog Bib ID)	PROPOSED	Intellectual Work	HydraWorks:Work	dcterms:identifier	literal (typed as bibliographic ID)	{0,n}	bibID
Language	BasicMetadata	Intellectual Work	HydraWorks:Work	dc:language	xs:string	{0,n}	language
Language_URI	BasicMetadata	Intellectual Work	HydraWorks:Work	dcterms:language	URI < dcterms:LinguisticSystem	{0,n}	language_URI
Note	BasicMetadata	Intellectual Work	HydraWorks:Work	dcterms:description	xs:string	{0,n}	note
OCR	BasicMetadata	Intellectual Work	HydraWorks:Work	dc:relation	xs:string	{0,n}	book_ocr
Place of Origin	BasicMetadata	Intellectual Work	HydraWorks:Work	VIVO:placeOfPublication	xs:string	{0,n}	pubplace
Publisher	BasicMetadata	Intellectual Work	HydraWorks:Work	dc:publisher	xs:string	{0,n}	publisher
Publisher URI	BasicMetadata	Intellectual Work	HydraWorks:Work	dcterms:publisher	URI < dcterms:Agent	{0,n}	publisher_URI
Repository	models/intellectual_work.rb	Intellectual Work	HydraWorks:Work	EDM.currentLocation	literal for now	{1,1}	repository
Rights	models/intellectual_work.rb	Intellectual Work	HydraWorks:Work	dc:rights	xs:string	{0,n}	rights
Rights Holder	models/intellectual_work.rb	Intellectual Work	HydraWorks:Work	dcterms:rightsHolder	URI < dcterms:Agent	{0,n}	rightsHolder
Rights URI	models/intellectual_work.rb	Intellectual Work	HydraWorks:Work	dcterms:rights	URI < dcterms:RightsStatement	{0,n}	rights_URI
Physical Source (Catalog Bib ID)	PROPOSED	Intellectual Work	HydraWorks:Work	dcterms:source	literal for now	{0,n}	physicalVersion
Set/Series/Collection Title	PROPOSED	Intellectual Work	HydraWorks:Work	dcterms:isPartOf	xs:string	{0,n}	set_statement
Subject	BasicMetadata	Intellectual Work	HydraWorks:Work	dc:subject	xs:string	{0,n}	subject
Subject URI	BasicMetadata	Intellectual Work	HydraWorks:Work	dcterms:subject	URI	{0,n}	subject_URI
Title	RequiredMetadata	Intellectual Work	HydraWorks:Work	dcterms:title	xs:string	{1,1}	title
Type	models/intellectual_work.rb	Intellectual Work	HydraWorks:Work	dc:type	xs:string	{0,n}	type
Type URI	models/intellectual_work.rb	Intellectual Work	HydraWorks:Work	dcterms:type	URI < loc:resourceTypes	{0,n}	type_URI

## Usage

### Defining new Works and new Work Subclasses

    ```turtle
    TBD
    ```

### References to Widgets

    ```turtle
    <repo:/cars/car0> a ex:Vehicle ;
        ex:hasWidget <repo:/widgets/widget0> .
    ```

From previous docs on Works:

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
