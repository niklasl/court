# CoIN (The Composition of Identifier Names) #

## Introduction ##

The CoIN vocabulary defines a set of classes and properties used to descibe what properties of a resource constitute components of a URI. (Who for all other purposes are supposed to be treated as opaque.)

Data described using CoIN can thus be used to control how to mint and/or check such URI:s.

With CoIN you describe schemes for URI construction. These schemes use [URI templates](http://tools.ietf.org/html/draft-gregorio-uritemplate-04), whose variables are mapped to literals (or resource URI:s) by matching properties of the resource.

URI:s are coined for a resource by reading the scheme and trying to match a full path (greediest match "wins"). This includes matching by type, or computing tokens for property values, either directly, from the property value of a reference, or by finding a "slug token" for the referenced resource (in a given dataset).

## Details ##

**Namespace URI**: `http://purl.org/court/def/2009/coin#`

N3 source: http://purl.org/court/def/2009/coin.n3

Usage example: http://court.googlecode.com/hg/resources/examples/coin/example_1.n3

The [CoIN Specification](http://court.googlecode.com/hg/resources/docs/coin/spec.html) (draft).

## Mechanics ##

_This is an outline of how an algorithm for minting URI:s using CoIN should work._

A URI can minted for a resource by using a `coin:CoinScheme`. A scheme defines a set of Templates (via `coin:template`). They are defined as the combination of a `coin:uriTemplate` (based on the syntax of the URI template draft), and `coin:component` definitions.

Each component of a template defines a property (`coin:property`) for which a value will be used to fill in a variable in the URI template. The variable name is either given explicitly (using `coin:variable`), or by using the leaf part of the URI of the property _(N.B.: this "leaf" usage should be considered experimental)_.

If there is a value for **all** of the components, the template "matches" and a URI can be constructed by using the URI template and the values for the variables.

A scheme can also define a base (`coin:base`) to be used for constructing the URI (thus the URI templates need not be full URI:s, only absolute).

Furthermore, templates can narrow the match by defining which type the resource must have for the template to match (using `coin:forType`).

The value is expected to be a literal (of any type), unless the component defines a second property (using `coin:slugFrom`). If present, the value to use is the value for a related resource (related via the object of the component's `coin:property`). In SPARQL:

```
  ?component
    coin:property ?property;
    coin:slugFrom ?slugFrom .
  ?resource ?property ?related .
  ?related ?slugFrom ?value .
```

There is also a way to define how to mint fragment URI:s by appending resolved fragment templates to a base URI picked from a relation from or to the resource. _[has yet to be documented.](This.md)_

Finally, CoIN defines properties for describing how values must be translated before the URI is constructed (using `coin:slugTranslation` with e.g. type(s) `coin:LowerCasedTranslation`, `coin:BaseCharTranslation`, optionally defining a specific `coin:spaceReplacement` and/or matching/stripping using regexps). Once completed, remaining characters illegal in URI segments must be URI encoded (unless a complete base is presevered by prepending them with "+", according to the URI Templates draft).