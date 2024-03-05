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
We have extended the Java-based RDF programming framework [Apache Jena](https://jena.apache.org/) with a complete implementation of all the features defined in the specification. Currently, the source code of this extension can be found in the [UnfoldAndFoldWithCompositeValues branch](https://github.com/hartig/jena/tree/UnfoldAndFoldWithCompositeValues) of the [hartig/jena fork](https://github.com/hartig/jena/) of the official [Jena Github repository](https://github.com/apache/jena/). We are planning to contribute this extension to the Jena project.

TODO ... (how to ...)

### Attean
We have also extended the Perl-based RDF programming framework [Attean](https://github.com/kasei/attean) with a complete implementation of the specification. Currently, the source code of this extension can be found in the [mutli-value-exprs branch](https://github.com/kasei/attean/tree/mutli-value-exprs) directly within the [Attean Github repository](https://github.com/kasei/attean), ready to be merged after discussion with the Attean community.

### Other implementations?
If you have another implementation, let us know!

## Other relevant links
* [Github repo](https://github.com/w3c/sparql-dev/) of the [SPARQL-DEV Community Group](https://www.w3.org/community/sparql-dev/)
