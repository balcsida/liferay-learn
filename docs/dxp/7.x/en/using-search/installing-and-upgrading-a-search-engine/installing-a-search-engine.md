# Installing a Search Engine

A search engine is a critical component of your Liferay DXP installation. The [creating an example cluster](./../../installation-and-upgrades/setting-up-liferay-dxp/clustering-for-high-availability/example-creating-a-simple-dxp-cluster.md#prepare-a-search-engine) documentation can get you started with the installation, but this section will cover more of the details (though at a high level) you need for setting up a production system.

<!-- DIAGRAM -->

When you start Liferay DXP an Elasticsearch server is simultaneously started. This default search engine makes local testing convenient since lots of Liferay DXP's functionality depends on a search engine, but it isn't supported for use in production environments. See the [Installing Elasticsearch](./elasticsearch/installing-elasticsearch.md) instructions for more details.
<!-- Is this the place to introduce sidecar which will replace embedded in GA4? -->

```note::
   Besides Elasticsearch, DXP also supports `Solr <http://lucene.apache.org/solr>`__. Note that Solr is not embedded and has to be connected remotely. To use Solr, see the `Installing Solr <https://help.liferay.com/hc/articles/360032264052-Installing-Solr>`__ article.
```
<!-- Is this the place to mention our deprecation of solr support? -->

## Satisfying the Java Requirements

- You must set the [`JAVA_HOME` environment variable](https://docs.oracle.com/cd/E19182-01/820-7851/inst_cli_jdk_javahome_t/).

- Elasticsearch and Liferay DXP must use the same Java version and distribution (e.g., Oracle Open JRE 1.8.0_201). Consult the [Elasticsearch compatibility matrix](https://www.elastic.co/support/matrix#matrix_jvm) and the [Liferay DXP compatibility matrix](https://help.liferay.com/hc/sections/360002103292-Compatibility-Matrix) to learn more about supported JDK distributions and versions. You can specify this in Elasticsearch:

   ```properties
   [Elasticsearch Home]/bin/elasticsearch.in.sh`: `JAVA_HOME=/path/to/java`
   ```

```note::
   The same requirement is not applicable to Solr as no JVM level serialization happens between the servers. Rather, all communication occurs at the HTTP level.
```
## Clustering the Search Engine

A production environment's search engine should be clustered for load managements and optimal Liferay DXP performance. Both Elasticsearch and Solr can be configured successfully on multiple nodes in the remote environment.

* To configure a remote Elasticsearch server or cluster, see [Installing Elasticsearch](./installing-elasticsearch.md).

* To configure a remote Solr server or cluster, see the [Installing Solr](https://help.liferay.com/hc/articles/360032264052-Installing-Solr) article.

## Selecting a Search Engine Vendor and Version

Elasticsearch and Solr are supported, but support for Solr is [deprecated]()<!-- link to somewhere -->. Therefore, Elasticsearch is the recommended search engine for search and indexing with Liferay DXP.

```important::
   Always refer to the `compatibility matrix <https://www.liferay.com/documents/10182/246659966/Liferay+DXP+7.2+Compatibility+Matrix.pdf/ed234765-db47-c4ad-7c82-2acb4c73b0f9>`__ to find the exact versions supported.
```

- [Install the latest supported Elasticsearch version](./elasticsearch/installing-elasticsearch.md)
- [Installing the latest supported Solr version](./solr/installing-solr.md)

<!-- Goes in the Solr section intro article and will need updates
## Using Solr

There are some drawbacks to using Solr as the search engine. These limitations affect how Solr processes search requests in various Liferay products.

### End User Feature Limitations of Liferay's Solr Integration

* [Liferay Commerce](https://help.liferay.com/hc/en-us/articles/360017869952)
* [Workflow Metrics](https://help.liferay.com/hc/en-us/articles/360029042071-Workflow-Metrics-The-Service-Level-Agreement-SLA-)
* [Custom Filter search widget](https://help.liferay.com/hc/en-us/articles/360028721272-Filtering-Search-Results-with-the-Custom-Filter-Widget)
* [The Low Level Search Options widget](https://help.liferay.com/hc/en-us/articles/360032607571-Low-Level-Search-Options-Searching-Additional-or-Alternate-Indexes)
* [Search Tuning: Customizing Search Results](https://help.liferay.com/hc/en-us/articles/360034473872-Search-Tuning-Customizing-Search-Results)
* [Search Tuning: Synonyms](https://help.liferay.com/hc/articles/360034473852-Search-Tuning-Synonym-Sets)

### Developer Feature Limitations of Liferay's Solr Integration

Implementation for the following APIs may be added in the future, but they are not currently supported by Liferay's Solr connector.

* From Portal Core (Module: `portal-kernel`, Artifact:
    `com.liferay.portal.kernel`):
  * `com.liferay.portal.kernel.search.generic.NestedQuery`
  * `com.liferay.portal.kernel.search.filter`:
    * `ComplexQueryPart`
    * `GeoBoundingBoxFilter`
    * `GeoDistanceFilter`
    * `GeoDistanceRangeFilter`
    * `GeoPolygonFilter`
* From the Portal Search API (Module: `portal-search-api`, Artifact:
    `com.liferay.portal.search.api`):
  * `com.liferay.portal.search.filter`:
    * `ComplexQueryPart`
    * `TermsSetFilter`
  * `com.liferay.portal.search.geolocation.*`
  * `com.liferay.portal.search.highlight.*`
  * `com.liferay.portal.search.query.function.*`
  * `com.liferay.portal.search.query.*`:
  * `com.liferay.portal.search.script.*`
  * `com.liferay.portal.search.significance.*`
  * `com.liferay.portal.search.sort.*`: only `Sort`,`FieldSort`, and `ScoreSort` are supported
* Portal Search Engine Adapter API (Module: `portal-search-engine-adapter-api`,
    Artifact: `com.liferay.portal.search.engine.adapter.api`)
  * `com.liferay.portal.search.engine.adapter.cluster.*`
  * `com.liferay.portal.search.engine.adapter.document.UpdateByQueryDocumentRequest`
  * `com.liferay.portal.search.engine.adapter.index.*`: only `RefreshIndexRequest` is supported
  * `com.liferay.portal.search.engine.adapter.search.*`:
    * `MultisearchSearchRequest`
    * `SuggestSearchRequest`
  * `com.liferay.portal.search.engine.adapter.snapshot.*`

Liferay Commerce requires the `TermsSetFilter` implementation which is only available in the Elasticsearch connector.
-->