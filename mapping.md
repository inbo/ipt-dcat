# Mapping of RDF DCAT to IPT concepts

namespace prefix | base URIs
----:|:----
dct:| `http://purl.org/dc/terms/`
dcat:| `http://www.w3.org/ns/dcat#`
xsd:| `http://www.w3.org/2001/XMLSchema#`
skos:| `http://www.w3.org/2004/02/skos/core#`
rdfs:| `http://www.w3.org/2000/01/rdf-schema#`
foaf:| `http://xmlns.com/foaf/0.1/`
schema:| `http://schema.org/`
adms:| `http://www.w3.org/ns/adms#`

## dcat:Catalog

### URI

The URI for the IPT catalog will be `http://homepage-of-ipt#Catalog` (e.g. http://data.inbo.be/ipt#Catalog). The URI will become dereferenceable using RDFa. In RDFa, a `rdfs:seeAlso` link will be given to a document which contains the entire DCAT feed.

### Concepts

Mandatory concepts are indicated in bold.

predicate | resource or literal | type | # | IPT concept | example
---:|:---:|:---:|:---:|:---|:---
**dct:title**|literal|xsd:string|1|[IPT#Name](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/AgentBase.java#L65)|`INBO IPT`
**dct:description**|literal|xsd:string|1|[IPT#Description](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/Ipt.java#L47)|`The INBO IPT is hosted at the Research Institute for Nature and Forest (INBO) in Brussels, Belgium.`
**dct:publisher**|resource|foaf:Agent|1|`http://gbif.org/publisher/` + [IPT#Organization:Key](http://www.gbif.org/publisher/1cd669d0-80ea-11de-a9d0-f1765f95f18b#Organization) with foaf:name [IPT#Organization:Name](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/AgentBase.java#L65)|`http://www.gbif.org/publisher/1cd669d0-80ea-11de-a9d0-f1765f95f18b#Organization` with foaf:name `Research Institute for Nature and Forest (INBO)`
**dcat:dataset**|resource|dcat:Dataset|M|`dcat:Dataset URI` we create (see below)|`http://data.inbo.be/ipt/resource?r=bird-tracking-gull-occurrences#Dataset`
foaf:homepage|resource||1|[IPT#HomepageURL](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/AgentBase.java#L49)|`http://data.inbo.be/ipt`
dct:rights|resource||1|static|`https://creativecommons.org/publicdomain/zero/1.0/`
dct:issued|literal|xsd:DateTime|1|date of creation|
dct:modified|literal|xsd:DateTime|1|date of last modification|
dcat:themeTaxonomy|resource|skos:ConceptScheme|1|static|`http://eurovoc.europa.eu/5463`
dct:spatial|resource|dct:Location|1|[IPT#Latitude](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/config/AppConfig.java#L145), [IPT#Longitude](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/config/AppConfig.java#L157)|`{ "type": "Point", "coordinates": [ 4.334187, 50.842133 ] }`

## dcat:Dataset

## URI

The URI for an IPT dataset will be `http://homepage-of-ipt/resource?r=dataset-name#dataset` (e.g. http://data.inbo.be/ipt/resource?r=bird-tracking-gull-occurrences#Dataset). The URI will become dereferenceable using RDFa. In RDFa, a `rdfs:seeAlso` link will be given to a document which contains the entire DCAT feed (including this URI).

## Concepts

Mandatory concepts are indicated in bold.

predicate | resource or literal | type | # | IPT concept | example
---:|:---:|:---:|:---:|:---|:---
**dct:title**|literal|xsd:string|1|[EML#Title](https://github.com/gbif/gbif-metadata-profile/blob/master/src/main/java/org/gbif/metadata/eml/Eml.java#L715)|`Bird tracking - GPS tracking of Lesser Black-backed Gull and Herring Gull breeding at the Belgian coast`
**dct:description**|literal|xsd:string|1|[EML#Description](https://github.com/gbif/gbif-metadata-profile/blob/master/src/main/java/org/gbif/metadata/eml/Eml.java#L753) concatenated|`Bird tracking - GPS tracking of Lesser Black-backed Gull and Herring Gull breeding at the Belgian coast is a species occurrence dataset published by the Research Institute for Nature and Forest (INBO). The dataset curently ...`
dct:publisher|resource|foaf:Agent|1|`http://gbif.org/publisher/` + [Resource#Organization:Key](http://www.gbif.org/publisher/1cd669d0-80ea-11de-a9d0-f1765f95f18b#Organization) with foaf:name [Resource#Organization:Name](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/AgentBase.java#L65)|`http://www.gbif.org/publisher/1cd669d0-80ea-11de-a9d0-f1765f95f18b#Organization` with foaf:name `Research Institute for Nature and Forest (INBO)`
dcat:theme|resource|skos:Concept|1|static|`http://eurovoc.europa.eu/5463`
dcat:keyword|literal|xsd:string|M|[EML#Keywords](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/Ipt.java#L47)|`animal movement`
dct:issued|literal|xsd:DateTime|1|[Resource#created](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/Resource.java#L339)|`2014-05-15`
dct:modified|literal|xsd:DateTime|1|[Resource#LastPublished](https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/model/Resource.java#L449)|`2015-05-07`
dct:isVersionOf|resource|dcat:Dataset|1|_Separate versions can be different resources which point to a generic dataset_|
dct:spatial|resource|dct:Location|1|[EML#BoundingCoordinates](https://github.com/gbif/gbif-metadata-profile/blob/master/src/main/java/org/gbif/metadata/eml/GeospatialCoverage.java#L59)|`{ "type": "Polygon", "coordinates": [ [ [-25, 10], [-25, 60], [10, 60], [10, 10], [-25, 10] ] ] }`
adms:versionInfo|literal||1|_todo_|
adms:versionNotes|literal||1|Admins can enter version notes with each publication|
adms:contactPoint|resource|vcard:Kind|M|[EML#Contacts](https://github.com/gbif/gbif-metadata-profile/blob/3c312d84f62fb3efbeca08e4fc9178ac4dfe5397/src/main/java/org/gbif/metadata/eml/Eml.java#L356)|`[a vcard:Individual; vcard:fn "Eric Stienen"; vcard:hasEmail <mailto:eric.stienen@inbo.be>]`
dcat:landingPage|resource||1|Resource URL or DOI|`http://data.inbo.be/ipt/resource?r=bird-tracking-gull-occurrences`

## dcat:Distribution

### URI

For each dataset, we'll link to 1 distribution: the Darwin Core Zip file. The URI for such a distribution will be the link to the zip file itself. We ignore EML and RTF distributions, as they do not contain data, only metadata.

### Concepts

Mandatory concepts are indicated in bold.

predicate |  resource or literal | type | # | IPT concept | example
---:|:---:|:---:|:---:|:---|:---
**dct:description**|literal|xsd:string|1|static|`Darwin Core Archive`
**dct:license**|resource|dct:LicenseDocument|1|[Resource#License](https://github.com/gbif/gbif-metadata-profile/blob/master/src/main/java/org/gbif/metadata/eml/Eml.java#L1273)|`http://creativecommons.org/publicdomain/zero/1.0/legalcode`
**dcat:mediaType**|resource|dct:MediaTypeOrExtent|1|static|`application/zip`|
**dct:format**|resource|dct:MediaTypeOrExtent|1|static|`dwc-a`|
**dcat:downloadURL**|resource||1|URI of distribution|`http://data.inbo.be/ipt/archive.do?r=bird-tracking-gull-occurrences`
