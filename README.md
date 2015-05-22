# eml2dcat

Mapping of Ecological Metadata Language (EML) to Data Catalog Vocabulary (DCAT)

## Resources

I talked to [@kbraak](https://github.com/kbraak) from [GBIF](http://www.gbif.org) regarding mapping EML to DCAT and here a couple of resources we could use.

1. EML is described at https://knb.ecoinformatics.org/#external//emlparser/docs/index.html
2. The GBIF IPT uses a GBIF profile of EML, defined at http://rs.gbif.org/schema/eml-gbif-profile/
3. The latest version of the EML GBIF profile is [1.1](http://rs.gbif.org/schema/eml-gbif-profile/1.1/): http://rs.gbif.org/schema/eml-gbif-profile/1.1/eml-gbif-profile.xsd
4. The IPT uses as custom library to express EML as Java classes: https://github.com/gbif/gbif-metadata-profile. If a new version of the EML GBIF profile is published, this library is manually updated. The IPT only uses one version of the profile (the latest one).
5. GBIF has already done a EML mapping exercise, which could serve as an example: from EML to the metadata format used by DataCite (which issues DOIs).
6. They did this by expressing the DataCite metadata as Java classes (in https://github.com/gbif/gbif-doi), using an external plugin/library: see [this line](https://github.com/gbif/gbif-doi/blob/master/pom.xml#L91).
7. The IPT uses https://github.com/gbif/gbif-doi as a dependency to get DOI functionality (see [pom file](https://github.com/gbif/ipt/blob/master/pom.xml#L337))
8. The actual mapping between EML and the DataCite metadata is done in the IPT code: https://github.com/gbif/ipt/blob/master/src/main/java/org/gbif/ipt/utils/DataCiteMetadataBuilder.java
9. This mapping is described at https://code.google.com/p/gbif-providertoolkit/wiki/IPT2DataCiteMappings
