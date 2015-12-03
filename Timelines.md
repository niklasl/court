

# Timelines #

A timeline represents the modification of a collection over time.

Timelines are naturally expressed on the web by using feeds. A feed document represent a series of resources by listing combinations of URI:s and timestamps. Each document represents a segment of a _collection_, partitioned by timestamps and linked together using feed archives. These in turn contain descriptions of creation, update and deletion of resources.

## Atom Timelines ##

[The Atom Syndication Format](http://tools.ietf.org/html/rfc4287) is a concrete format for feeds which fulfils the details technical requirements COURT has on timelines for resource representations.

Timelines in Atom can be achieved by combining:

  * [Feed Archives](http://tools.ietf.org/html/rfc5005#section-4)
  * [Tombstones](http://tools.ietf.org/html/draft-snell-atompub-tombstones-06)

, or for smaller datasets a complete listing of all contained entries:

  * [Complete Feeds](http://tools.ietf.org/html/rfc5005#section-2)

(Note that regular [paged feeds](http://tools.ietf.org/html/rfc5005#section-3) are _not_ stable enough to describe these collectable timelines, since they cannot be guaranteed to be complete (due to variations of a feed page over time, which can cause a climbing mechanism to miss entry updates).)

_Note:_ Securing and verifying transmission can easily be done using HTTPS, and for linked representations providing simple checksums using e.g.:

  * [Link Extensions](http://tools.ietf.org/html/draft-snell-atompub-link-extensions-02#section-3.1)

## Delivering Data ##

In Atom, each resource is "packaged" by entries (by structure only), who are put into feed documents representing lists from some kind of collection. Atom entries contain or link to representations of different media types. One of these representations _can_ be an RDF document describing and linking the subject resource. Atom entries can also link to "enclosures", which is very useful for delivering compound resources (e.g. where an information resource for practical reasons is split into several documents).

Data is delivered in Atom Entries via the `<content>`element, and auxiliary data via zero or more `<link>` elements. COURT recomends to deliver resources described in RDF by providing an RDF representation describing the resource via one of these mechanisms.

The exact format depends on expected consumers, but using current standard RDF syntaxes is adviced. Currently (spring 2010) this basically boils down to RDF/XML or (X)HTML+RDFa. But there are several optional formats in the wild.

## Notification ##

It's beneficial to have depots delivering timelines to notify subscribers of these. This can be done by "pinging" the subscriber, commonly POST:ing the subscription feed of the depot to a subscriber listener.

See [PubSubHubbub](http://pubsubhubbub.googlecode.com/svn/trunk/pubsubhubbub-core-0.2.html) for a specified, feature-rich mechanism of doing this in a federated way.

## Description and Discovery ##

Recommended ways to use RDF semantics to describe both datasets/collections, and discover source feeds for them is described in [RDF\_Practices](RDF_Practices.md). Timelines as RDF is also discussed there.

## Relations to Similar Initiatives ##

  * [OAI-PMH](http://www.openarchives.org/pmh)
  * [Semantic Web Crawling: A Sitemap Extension](http://sw.deri.org/2007/07/sitemapextension/)
  * ...