
## Relationship between DPLA MAP and PCDM (Original)

This document notes the ways in which the DPLA Metadata Application Profile and PCDM can be used together.

### Mapping from PCDM to DPLA MAP

#### Collections

One or more `pcdm:Collection`s map to a `dcmitype:Collection`. As `pcdm:Collection`s may be hierarchical, and DPLA's use of `dcmitype:Collection` is not hierarchical, information may be accumulated from multiple `pcdm:Collection`s into one.  

For example, given:

```
_:maps a pcdm:Collection ;
  rdfs:label "Maps Collection" ;
  dc:description " ... " ;
  pcdm:hasMember _:africa .

_:africa a pcdm:Collection ;
  rdfs:label "Maps of Africa" ;
  pcdm:hasMember _:map1, _:map2, ... _:mapn .
```

The resulting `dcmitype:Collection` may take the description from the top level Maps collection, the label from the Maps of Africa collection, and apply it to all of the Map objects.

The resulting collection will be associated with a `dpla:SourceResource` constructed from a `pcdm:Object`.  This is the inverse of the PCDM hierarchy, where Collections have members.


#### Objects

PCDM Objects can be used to describe objects (both conceptual and physical), and parts of those objects.  DPLA is mostly concerned with identifiable cultural heritage objects (`dpla:SourceResource`) and the digital views of that object (`dpla:WebResource`).

When mapping from PCDM to DPLA, a `pcdm:Object` that is not `pcdm:hasMember` another `pcdm:Object` will be treated as a `dpla:SourceResource`.  Other resources may also be treated in this way.  These Objects may or may not be part of a `pcdm:Collection`.

Such objects MUST have a stable web URL at which the object is rendered in a human readable way.  This is the object of `edm:isShownAt`.  Such objects SHOULD have a `dpla:WebResource` which is a `edm:preview` of the object, such as a thumbnail.

As per Collections, the resulting DPLA resource may conflate information from an entire hierarchy of objects into a single resource.

#### Files

Some `pcdm:File`s are `dpla:WebResource`s, but not all.  It would be true in at least the following situations:

* The `pcdm:File` is a view of the `dpla:SourceResource` (`edm:isShownAt`)
* The `pcdm:File` is a preview / thumbnail of the `dpla:SourceResource` (`edm:preview`)

### Further Notes

* The reverse mapping is lossy and thus round-tripping is not possible. This is because DPLA MAP does not store the structure of the object or collection hierarchy, and thus information is lost in the above transformation.
* Any enrichments should therefore happen at the PCDM layer, and then re-exported to DPLA.
