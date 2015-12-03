# Implementation Components #

COURT defines some conceptual components to concretize how to create implementations for collecting, managing and exposing timelines.

Many of these concepts exist as independent implementations. For instance, a plethora of tools such as document and triple/quad stores are available for indexing the data put into a depot. These may also serve as the backend for managing the timeline data of each depot entry. [PubSubHubbub](http://code.google.com/p/pubsubhubbub/) can be used for notification.

The COURT project may also host implementations of one or more of these components. They should not be considered as specifications, but rather as proof of concepts to show that this approach is feasible in many programming platforms ranging from "do it yourself" solutions to COURT-wrapping of existing products.

## Depot ##

A depot is simply the local storage containing the entry data. It is the component tracking create, update and delete, and delivering the timeline documents. Its purpose is to store and provide representation(s) for each resource.

It also needs to know (or delegate the handling of) the timeline of modifications, so that archives (the sliced lists of events) can be created, and possibly the location of active entries in archives to be able to compact them properly if they are modified (updated/deleted).

## Collector ##

A collector reeds timeline feeds. It needs to track source dates, and in the case of **complete** source feeds, the set of resources collected from a dataset (identified by the feed id of its complete feed).

## Indexing ##

Indexing can be done in any way, and is really independent of anything else here. However, it can prove beneficial to inject the indexing service as a tracker to both depot and collector components, and delegate to it the function of logging the stream of entry modifications, thus keeping track of timestamps, position in an archive etc. of current and historical entries.

A collector can also log collect events (and possibly errors) in an index, to be exposed and queried via a separate channel (which may very well be an Atom feed containing RDF).

### Data Services ###

Index services can also be used to drive implementations of data services exposing convenience formats and search/facet functions upon datasets. Some interesting existing service specs upon indexed data (such as triple stores) are:

  * [GData](http://code.google.com/intl/sv-SE/apis/gdata/)
  * [linked-data-api](http://code.google.com/p/linked-data-api/)
  * _RData (TBD)_

## Relations to Similar Initiatives ##

CMIS, ... (too much/little/off..?)

Platforms: DSpace, Fedora, ... (how much stack, what is necessary, how to stay movable..?)

Stores/internals: anything document-oriented (may work as internal fundament), [CDL Digital Library Building Blocks](http://www.cdlib.org/inside/diglib/), ...