# LocI Linkset Metrics

This repository contains a description of, and code for, the calculation of Linkset metrics for the [LocI project](http://locationindex.org/).

### Linkset
A Linkset is a specialised type of [RDF](https://www.w3.org/2001/sw/wiki/RDF) Dataset that contains links between other datasets. Linksets are created to be managed separately from either of the Datasets that they join as this allows for more powerful governance. By publishing Linksets for dataset links, the LocI project ensures...

### Metrics
The metrics that are calculated for each LocI Linkset are published on the Linkset's README page, for example, the metrics for the Linkset **[Current Addresses to 2011 Mesh Block Linkset](https://github.com/CSIRO-enviro-informatics/addrmb11-linkset)** are visible on that Linkset's home page.

The metrics calculated so far are:

1. Number of links
2. Number of items in Dataset A (from) not linked
3. Number of items in Dataset B (to) not linked
4. Number of link creation methods used
5. Numbers of uses of each link-creation method

As an example of results, the metrics for the Linkset **[Current Addresses to 2011 Mesh Block Linkset](https://github.com/CSIRO-enviro-informatics/addrmb11-linkset)**, found on that Linkset's home page, are:

**Metric** | **Value**
-- | --
Number of links | 14173051
Number of items in Dataset A (from) not linked | *not yet calculated* 
Number of items in Dataset B (to) not linked | *not yet calculated*
Number of link creation methods used | 5
Numbers of uses of each link-creation method | m1: 13361555<br />m2: 188410<br />m3: 114823<br />m4: 459270<br />m5: 48993


## Linkset code
The code used to generate a Linkset's metrics are a series of [SPARQL queries](https://www.w3.org/TR/sparql11-overview/) that are stored in the [queries/](queries/) folder of this repository. 

One example query is that used to generate the *Number of links* metric which is:

```
PREFIX m: <http://linked.data.gov.au/def/loci/hadGenerationMethod>
SELECT (COUNT(?s) AS ?count)
WHERE {
    GRAPH <http://linked.data.gov.au/linkset/addrmb11> {
		  ?s m: ?m .
    }
}
```
In words, this query asks: *"How many triples are there in the graph `<.../addrmb11>` that have a `loci:hadGenerationMethod` property?"*.

### Using the metric queries
The queries in [queries/](queries/) folder need to be run against a Linkset that is available for SPARQL querying. This will involve loading a Linkset into a [triplestore](https://en.wikipedia.org/wiki/Triplestore) and then executing the query against it. For large linksets, such as **[Current Addresses to 2011 Mesh Block Linkset](https://github.com/CSIRO-enviro-informatics/addrmb11-linkset)** which contains 14,173,051 links, such queries can take a minute or two, even on well-provisioned triplestores.


## Rights & License
The content of this API is licensed for use under the [Creative Commons 4.0 License](https://creativecommons.org/licenses/by/4.0/). See the [license deed](LICENSE) all details.


## Contacts
*creator*:  
**Nicholas Car**  
CSIRO Land & Water, Environmental Informatics Group  
<nicholas.car@csiro.au>  

