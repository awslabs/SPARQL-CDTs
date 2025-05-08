# SPARQL-CDTs
This repository contains the artifacts for a specification that defines an approach to represent composite values (lists and maps, in particular) as literals in RDF data, and to extend SPARQL with features related to such literals. These extensions include
* an aggregation function to produce these composite values,
* functions to operate on these composite values in expressions, and
* a new operator to unfold such composite values into their individual components.

The **latest version of the specification document**, which includes an [informal description of the approach](https://w3id.org/awslabs/neptune/SPARQL-CDTs/spec/latest.html#description), is published under the following permanent identifier:
* https://w3id.org/awslabs/neptune/SPARQL-CDTs/spec/latest.html

## Contents of this repository
* **The [spec](https://github.com/awslabs/SPARQL-CDTs/tree/main/spec) directory** contains the various versions of the specification document, including the editors' draft. If you want to look at the current snapshot of the editors' draft directly in your browser, use the following permanent address: https://w3id.org/awslabs/neptune/SPARQL-CDTs/spec/editors_draft.html
* **The [tests](https://github.com/awslabs/SPARQL-CDTs/tree/main/tests) directory** contains a test suite with a comprehensive collection of tests that developers of RDF and SPARQL systems can use to check whether their implementation of the different features defined in the specification is correct.

## Implementations
### Apache Jena
We have extended the Java-based RDF programming framework [Apache Jena](https://jena.apache.org/) with a complete implementation of all the features defined in the specification. This extension has become part of the official Jena releases in [version 5.2.0](https://lists.apache.org/thread/ynf70r2z6cs7x48cvytqqk5bxh6qln9l).

To try this implementation, [download the latest release](https://jena.apache.org/download/index.cgi) of Jena, unpack it, and use the [ARQ command line programs](https://jena.apache.org/documentation/query/cmds.html) of Jena to run SPARQL queries that use the features defined in the specification.

Alternatively, and even easier, you can also simply run such SPARQL queries via the [online SPARQL query processor](https://sparql.org/sparql.html) at https://sparql.org/, which is built on Jena. As an initial example, you may try the following query for which you do not even need a file with RDF data.
```
PREFIX cdt:	<http://w3id.org/awslabs/neptune/SPARQL-CDTs/>
PREFIX ex:	<http://example.org/>

SELECT ?list3 ?elmt ?key ?value WHERE {
  BIND( "[1, 'hello'@en]"^^cdt:List AS ?list1 ) # provide the literal directly
  BIND( cdt:List(ex:test, 42) AS ?list2 )       # or use the cdt:List constructor
  BIND( cdt:concat(?list1, ?list2) AS ?list3 )
  BIND( cdt:get(?list3, 3) AS ?elmt )

  UNFOLD( "{ 'hello': 'world' }"^^cdt:Map AS ?key, ?value )
}
```

### Attean
We have also extended the Perl-based RDF programming framework [Attean](https://github.com/kasei/attean) with a complete implementation of the specification. This extension has become part of [Attean version 0.034](https://metacpan.org/release/GWILLIAMS/Attean-0.034).

### SPARQL-CDT-Tools
We are working on a collection of command-line tools related to the approach. Currently, it contains a tool to convert RDF data that uses [RDF collections](https://www.w3.org/TR/rdf-mt/#collections) to RDF data in which the collections are replaced by [cdt:List literals](https://awslabs.github.io/SPARQL-CDTs/spec/latest.html#list-datatype). The relevant repository is: https://github.com/hartig/SPARQL-CDT-Tools

### DCM2RDF
[DCM2RDF](https://github.com/ebremer/dcm2rdf) is tool that extracts metadata from DICOM files and converts this metadata into an RDF representation. Since [version 1.1.0](https://github.com/ebremer/dcm2rdf/releases/tag/1.1.0), the tool supports the option to use cdt:List literals to represent polygonal data.

### Other implementations?
If you have another implementation, let us know!

## Other relevant links
* [SEP-0009](https://github.com/w3c/sparql-dev/blob/main/SEP/SEP-0009/sep-0009.md), which is a SPARQL Enhancement Proposal of the approach, submitted to the [SPARQL-DEV Community Group](https://www.w3.org/community/sparql-dev/)
