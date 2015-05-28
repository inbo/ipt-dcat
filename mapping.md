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

URI for the INBO Catalog will be http://data.inbo.be/ipt#Catalog. The URI will become dereferenceable using RDFa. In RDFa, a `rdfs:seeAlso` link will be given to the actual DCAT document which contains the entire feed.

| predicate | resource or literal | type | mandatory | IPT resource |
|---:|:---:|:---:|:---:|:---|
|dct:title|literal|xsd:string|Y|[Ipt#name](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/AgentBase.java#L26)|
|dct:description|literal|xsd:string|Y|[Ipt#description](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/Ipt.java#L48)|
|dct:publisher|resource|foaf:Agent|Y|with foaf:name [admin.organisation.name](https://github.com/gbif/ipt/blob/e478aa2fd68926cb1df89ab0bf5b4eae17933d0a/src/main/resources/ApplicationResources_en.properties#L611)|
|dcat:dataset|resource|dcat:Dataset|Y|links to dcat:Dataset URIs we create|

## dcat:Dataset

URI for an INBO dataset will be http://data.inbo.be/ipt/resource?r=belgian-coccinellidae-inbo-occurrences#Dataset. The URI will become dereferenceable using RDFa. In RDFa, a rdfs:seeAlso link will be given to the document with the entire DCAT feed (which will include this URI).

| predicate |  resource or literal | type | mandatory | IPT resource |
|---:|:---:|:---:|:---:|:---|
|dct:title|literal|xsd:string|Y|[manage.resource.create.title](https://github.com/gbif/ipt/blob/e478aa2fd68926cb1df89ab0bf5b4eae17933d0a/src/main/resources/ApplicationResources_en.properties#L701)|
|dct:description|literal|xsd:string|Y|?|

## dcat:Distribution
For each dataset, we'll link 1 distribution: the darwin core zip file. URI for an INBO distribution will be the link to the zip file itself.

| predicate |  resource or literal | type | mandatory | IPT resource |
|---:|:---:|:---:|:---:|:---|
|dct:title|literal|xsd:string|Y|"Darwin core zip file"|
|dct:description|literal|xsd:string|Y|"..."|



