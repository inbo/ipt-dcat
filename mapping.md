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

URI for the INBO Catalog will be http://data.inbo.be/ipt#Catalog

| predicate |  resource or literal | type | mandatory | IPT resource |
|---:|:---:|:---:|:---:|:---|
|dct:title|literal|xsd:string|Y|[admin.ipt.name](https://github.com/gbif/ipt/blob/e478aa2fd68926cb1df89ab0bf5b4eae17933d0a/src/main/resources/ApplicationResources_en.properties#L573)|
|dct:description|literal|xsd:string|Y|[admin.ipt.description](https://github.com/gbif/ipt/blob/e478aa2fd68926cb1df89ab0bf5b4eae17933d0a/src/main/resources/ApplicationResources_en.properties#L574)|
|dct:publisher|resource|foaf:Agent|with foaf:name [admin.organisation.name](https://github.com/gbif/ipt/blob/e478aa2fd68926cb1df89ab0bf5b4eae17933d0a/src/main/resources/ApplicationResources_en.properties#L611)|

## dcat:Dataset


| predicate |  resource or literal | type | mandatory | IPT resource |
|---:|:---:|:---:|:---:|:---|
|dct:title|literal|xsd:string|Y|[manage.resource.create.title](https://github.com/gbif/ipt/blob/e478aa2fd68926cb1df89ab0bf5b4eae17933d0a/src/main/resources/ApplicationResources_en.properties#L701)|
|dct:description|literal|xsd:string|Y|?|


## dcat:Distribution

For each dataset, we'll link 1 distribution: the darwin core zip file

| predicate |  resource or literal | type | mandatory | IPT resource |
|---:|:---:|:---:|:---:|:---|
|dct:title|literal|xsd:string|Y|"Darwin core zip file"|
|dct:description|literal|xsd:string|Y|"..."|



