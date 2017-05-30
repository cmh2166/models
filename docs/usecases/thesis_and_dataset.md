
# Example Use Case: Thesis with DataSet

## Description

A PhD student deposits their Thesis into the institutional repository. With the thesis (a PDF), is the dataset that they used in their research, and the underlying latex and image files used to generate the PDF.  They later update the object with a copy of the publisher supplied PDF Proof of the published version.

```turtle
_:pc1 a pcdm:Object ;
  rdfs:label "Thesis of Jane Smith" ;
  edm:isRepresentationOf _:rwo1 ;
  pcdm:hasMember _: ;
  pcdmw:hasFileSet _:tn2 .

_:front1 a pcdm:Object ;
  rdfs:label "Thesis Document" ;
  pcdmw:hasFileSet _:fs1 .
```
