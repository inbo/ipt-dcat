# Mapping of RDF DCAT to IPT concepts

| namespace prefix | base URIs |
|----:|:----|
| dct:| `http://purl.org/dc/terms/` |
| dcat:| `http://www.w3.org/ns/dcat#`|
| xsd:| `http://www.w3.org/2001/XMLSchema#`|
| skos:| `http://www.w3.org/2004/02/skos/core#`|
| rdfs:| `http://www.w3.org/2000/01/rdf-schema#`|
| foaf:| `http://xmlns.com/foaf/0.1/`|
| schema:| `http://schema.org/`|
| adms:| `http://www.w3.org/ns/adms#`|

## dcat:Catalog

### URI

The URI for the IPT catalog will be `http://homepage-of-ipt#Catalog` (e.g. http://data.inbo.be/ipt#Catalog). The URI will become dereferenceable using RDFa. In RDFa, a `rdfs:seeAlso` link will be given to a document which contains the entire DCAT feed.

### Concepts

Mandatory concepts are indicated in bold.

| predicate | resource or literal | type | IPT concept | example |
|---:|:---:|:---:|:---|:---|
|**dct:title**|literal|xsd:string|[Ipt#Name](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/AgentBase.java#L65)|INBO IPT|
|**dct:description**|literal|xsd:string|[Ipt#Description](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/Ipt.java#L47)|The INBO IPT is hosted at the Research Institute for Nature and Forest (INBO) in Brussels, Belgium.|
|**dct:publisher**|resource|foaf:Agent|with foaf:name [Organisation#Name](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/AgentBase.java#L65)|Research Institute for Nature and Forest (INBO)|
|**dcat:dataset**|resource|dcat:Dataset|links to dcat:Dataset URIs we create|http://data.inbo.be/ipt/resource?r=bird-tracking-gull-occurrences#Dataset|
|foaf:homepage|resource||[#Ipt#HomepageURL](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/AgentBase.java#L49)|http://data.inbo.be/ipt|
|dct:rights|resource|||https://creativecommons.org/publicdomain/zero/1.0/|
|dct:issued|literal|xsd:DateTime|date of creation||
|dct:modified|literal|xsd:DateTime|date of last modification||
|dcat:themeTaxonomy|resource|skos:ConceptScheme|_todo_||
|dct:spatial|resource|dct:Location|There is a latitude/longitude in the IPT settings||

## dcat:Dataset

## URI

The URI for an IPT dataset will be `http://homepage-of-ipt/resource?r=dataset-name#dataset` (e.g. http://data.inbo.be/ipt/resource?r=bird-tracking-gull-occurrences#Dataset). The URI will become dereferenceable using RDFa. In RDFa, a `rdfs:seeAlso` link will be given to a document which contains the entire DCAT feed (including this URI).

## Concepts

Mandatory concepts are indicated in bold.

| predicate | resource or literal | type | IPT concept | example |
|---:|:---:|:---:|:---|:---|
|**dct:title**|literal|xsd:string|[Eml#Title](https://github.com/gbif/gbif-metadata-profile/blob/master/src/main/java/org/gbif/metadata/eml/Eml.java#L715)|Bird tracking - GPS tracking of Lesser Black-backed Gull and Herring Gull breeding at the Belgian coast|
|**dct:description**|literal|xsd:string|[Eml#Description](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/Ipt.java#L47)|Bird tracking - GPS tracking of Lesser Black-backed Gull and Herring Gull breeding at the Belgian coast is a species occurrence dataset published by the Research Institute for Nature and Forest (INBO). The dataset curently ...|
|dcat:theme|resource|skos:Concept|default to Eurovoc URI for biodiversity|
|dcat:keyword|literal|xsd:string|[EML#Keywords](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/Ipt.java#L47)|animal movement|
|dct:issued|literal|xsd:DateTime|date of creation||
|dct:modified|literal|xsd:DateTime|date of last modification||
|dct:isVersionOf|resource|dcat:Dataset|_Separate versions can be different resources which point to a generic dataset_||
|dct:spatial|resource|dct:Location|[EML#BoundingCoordinates](https://github.com/gbif/gbif-metadata-profile/blob/master/src/main/java/org/gbif/metadata/eml/GeospatialCoverage.java#L59)||
|adms:versionInfo|literal||_todo_||
|adms:versionNotes|literal||Admins can enter version notes with each publication||
|adms:contactPoint|resource|vcard:Kind|[EML#Contacts](https://github.com/gbif/gbif-metadata-profile/blob/3c312d84f62fb3efbeca08e4fc9178ac4dfe5397/src/main/java/org/gbif/metadata/eml/Eml.java#L356)|Eric Stienen, Peter Desmet|
|dcat:landingPage|resource|||http://data.inbo.be/ipt/resource?r=bird-tracking-gull-occurrences|

## dcat:Distribution
For each dataset, we'll link 1 distribution: the darwin core zip file. URI for an INBO distribution will be the link to the zip file itself.

| predicate |  resource or literal | type | mandatory | IPT resource |
|---:|:---:|:---:|:---:|:---|
|dct:description|literal|xsd:string|Y|"Darwin core zip file"|
|dct:license|resource|dct:LicenseDocument|Y|https://creativecommons.org/publicdomain/zero/1.0/|
|dcat:mediaType|resource|dct:MediaTypeOrExtent|Y||
|dcat:downloadURL|resource|||same URI|
