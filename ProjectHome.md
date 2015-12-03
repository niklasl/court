# Crafting Organization Using Resources and Time #

COURT defines a set of practices for organizing resources and exposing their data.

The core premise is to leverage existing technologies to make this straightforward:

  * [Atom](http://tools.ietf.org/html/rfc4287) for delivery and timeline,
  * [RDF](http://www.w3.org/RDF/) for describing the actual (domain-specific) data.

The goal is to gather a concise set of existing specs and practices to form a usable whole, to be used as a basis for many kinds of resource distribution and collection scenarios.

## Concepts ##

The term "resource" refers to the concept used [on the web](http://en.wikipedia.org/wiki/Resource_(Web)) (the "R" in both URI and RDF), for which there is commonly one or more digital representations (either direct representations or related descriptions).

These resource representations are exposed on the web, and are modified over time.

### [Timelines](Timelines.md) ###

Representing timelines for RDF data is a primary motive of COURT. A timeline represents the modification of a collection over time. The use of Atom for this is the current recommendation.

See [Timelines](Timelines.md) for further information.

### Data: [RDF Practices](RDF_Practices.md) ###

Orthogonal to timelines is how to describe datasets, provenance, logging and other things related to the management of RDF _data_.

See [RDF Practices](RDF_Practices.md) for further information.

#### Vocabularies ####

Vocabularies pertaining to management of RDF data, defined under the COURT umbrella:

  * [COIN](COIN.md)

## Implementation ##

COURT describes some components useful when implementing COURT practices. See: [Implementation Components](Implementation_Components.md).