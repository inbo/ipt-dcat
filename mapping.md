# Mapping of the IPT fields to RDF DCAT

| namespace prefix | base URIs |
|----:|:----|
| dct:| `http://purl.org/dc/terms/` |
| dcat:| `http://www.w3.org/ns/dcat#`|
| xsd:| `http://www.w3.org/2001/XMLSchema#`|
| skos:| `http://www.w3.org/2004/02/skos/core#`|
| rdfs:| `http://www.w3.org/2000/01/rdf-schema#`|
| foaf:| `http://xmlns.com/foaf/0.1/`|
| schema:| `http://schema.org/`|

## dcat:Catalog

URI for the INBO Catalog will be http://data.inbo.be/ipt#Catalog. The URI will become dereferenceable using RDFa. In RDFa, a `rdfs:seeAlso` link will be given to a document which contains the entire DCAT feed.

| predicate | resource or literal | type | mandatory | IPT resource |
|---:|:---:|:---:|:---:|:---|
|dct:title|literal|xsd:string|Y|[Ipt#name](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/AgentBase.java#L65)|
|dct:description|literal|xsd:string|Y|[Ipt#description](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/Ipt.java#L47)|
|dct:publisher|resource|foaf:Agent|Y|with foaf:name [Organisation#name](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/AgentBase.java#L65)|
|dcat:dataset|resource|dcat:Dataset|Y|links to dcat:Dataset URIs we create|

## dcat:Dataset

URI for an INBO Dataset will be http://data.inbo.be/ipt/resource?r=bird-tracking-gull-occurrences#Dataset. The URI will become dereferenceable using RDFa. In RDFa, a `rdfs:seeAlso` link will be given to a document which contains the entire DCAT feed (including this URI).

| predicate |  resource or literal | type | mandatory | IPT resource |
|---:|:---:|:---:|:---:|:---|
|dct:title|literal|xsd:string|Y|[Eml#title](https://github.com/gbif/gbif-metadata-profile/blob/master/src/main/java/org/gbif/metadata/eml/Eml.java#L715)|
|dct:description|literal|xsd:string|Y|[Eml#description](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/Ipt.java#L47)|

## dcat:Distribution
For each dataset, we'll link 1 distribution: the Darwin Core Archive (a zip file). URI for an IPT Distribution will be the link to the zip file itself.

| predicate |  resource or literal | type | mandatory | IPT resource |
|---:|:---:|:---:|:---:|:---|
|dct:title|literal|xsd:string|Y|"Darwin Core Archive"|
|dct:description|literal|xsd:string|Y|"..."|
