

# RDF-specific practices and vocabularies #

While the use of RDF is not necessary to use the COURT Timelines principles. But when dataset modifications are exposed on the web, COURT advocates the [Linked Data](http://linkeddata.org/) principles and thus use of RDF to describe relevant resources (both published and related).

RDF excels at describing arbitrary domains of resource, ranging from digial artifacts such as images and articles, via descriptions of physical resources such as people and things, to higher abstractions such as organisations, concepts, vocabularies and the properties and types describing all of this.

Moreover, COURT advocates the use of (and defines if necessary) certain vocabularies for various practices particular to the management of data.

## Sources, Collections, Datasets ##

A dataset can be thought of as a collection of resources. The boundaries and provenance of a collection is not defined by the COURT approach. The dataset can be an instrumental device used to handle the content management (and other logistics), and fairly orthogonal to the domain of the resources themselves.

It is reasonable to describe this data (e.g. s provenance and discovery) as RDF, as opposed to pushing such metadata into the delivery mechanism syntax (e.g. the linked Atom feed documents).

It may also be beneficial to describe each _context/named graph_ to provide for the publication of [Timelines](Timelines.md) from datasets. See [#RDF\_Timelines](#RDF_Timelines.md) below.

Related vocabularies:

  * [voiD](http://semanticweb.org/wiki/VoiD)
  * [dcat](http://vocab.deri.ie/dcat)


## Description and Discovery ##

There is a relation between the dataset/collection and the timeline resource. The simplest defined URI for this relation is:
```
<http://www.iana.org/assignments/relation/current>
```

, but it is currently undefined by IANA whether this URI identifies a real RDF Property. It has been used in the wild for this purpose though..

Related vocabularies:

  * [Dady](http://purl.org/NET/dady)

For general discussions, see the [Dataset Dynamics Discussion Group](http://groups.google.com/group/dataset-dynamics).

## RDF Timelines ##

[Timelines](Timelines.md) themselves can also be described as RDF. This means to describe the logical structure/partitioning of a dataset, along with timestamps for each context. This is useful both for native RDF datastores who should be exposed using COURT timelines, and for e.g. logging the collection of data from remote datasets who publish such timelines.

A vocabulary expressing the Atom semantics in RDF is [AtomOwl](http://bblfish.net/work/atom-owl/2006-06-06/#).

To express the additional types and properties necessary to describe Feed Archives, Complete Feeds, Deleted Entries and e.g. link extensions for checksums, COURT does not yet define or recommended a certain vocabulary. There are URI:s for these concepts at:

  * [AtomOwl extensions by Toby Inkster](http://ontologi.es/atomix)
  * [DeletedEntry @ OpenVocab](http://open.vocab.org/docs/DeletedEntry)
  * [hasMD5 @ OpenVocab](http://open.vocab.org/docs/hasMD5)

(_Note:_ The relation between Atom (AtomOwl) and (e.g.) [SIOC](http://sioc-project.org/) remains to be investigated, according to how well each meets the needs of describing COURT practises in RDF. SIOC may be to open-ended and  community-oriented (even "organic") to meet the very specific, instrumental and rather artificial needs of the COURT mechanics.)

## Provenance and event (C(R)UD) logging ##

See [Dataset Dynamics: Components (Vocabularies, Protocols, Formats)](http://groups.google.com/group/dataset-dynamics/web/components-vocabularies-protocols-formats) for a discussion about e.g. changeset descriptions.

## Validation ##

_TBD_

## URI minting: COIN ##

The [COIN](COIN.md) vocabulary descibes how to descibe what properties of a resource constitute parts (segments) of a hierarchically built URI. (Who for all other purposes are supposed to be treated as opaque.)

Data described using COIN can be used to control how to to mint and/or check URI:s of resources.