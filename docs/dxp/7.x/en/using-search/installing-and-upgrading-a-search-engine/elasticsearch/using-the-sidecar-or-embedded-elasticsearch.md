# Using the Sidecar or Embedded Elasticsearch

If you obtained Liferay DXP by downloading a Tomcat bundle or pulling a Docker tag, an Elasticsearch node is started with DXP as either an embedded or sidecar server. To confirm,

- If running Liferay DXP 7.2, access the embedded server at <http://localhost:9200>
- If running Liferay DXP 7.3, access the sidecar server at <http://localhost:9201>

You'll see information like this:

```json
{
  "name" : "liferay",
  "cluster_name" : "LiferayElasticsearchCluster",
  "cluster_uuid" : "pb71L4whRS-PxTHgGdGM-Q",
  "version" : {
    "number" : "7.3.0",
    "build_flavor" : "unknown",
    "build_type" : "unknown",
    "build_hash" : "de777fa",
    "build_date" : "2019-07-24T18:30:11.767338Z",
    "build_snapshot" : false,
    "lucene_version" : "8.1.0",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}
```

Liferay DXP starts with an embedded (Liferay DXP 7.2) or sidecar (Liferay DXP 7.3) Elasticsearch node. While convenient for development and testing, neither is suitable for production.

```note::
   While it's not a supported production configuration, installing Kibana to monitor the embedded Elasticsearch server is useful during development and testing. Just be aware that you must install the `OSS only Kibana build <https://www.elastic.co/downloads/kibana-oss>`__.
```

You wouldn't run an embedded database like HSQL in production, and you shouldn't run Elasticsearch in embedded mode in production either. Instead, run Elasticsearch in [_remote operation mode_](./getting-started-with-elasticsearch.md), as a standalone server or cluster of server nodes.

```important::
   Synonym Sets and Result Rankings are applications that use the search index for primary data storage. No data is stored in the Liferay DXP database. Therefore, if you have Synonym Sets or Result Rankings configured while sidecar or embedded mode are in use, switching to remote mode and reindexing will `not` restore those configurations. Instead you must manually bring the Synonym Sets and Result Rankings into the remote cluster. See the `Upgrade Guide <../upgrading_elasticsearch.rst>`_ for details on using Elastic's `Snapshot and Restore <https://www.elastic.co/guide/en/elasticsearch/reference/7.x/snapshot-restore.html>`_ feature to preserve these indexes.
```

## How to Use the Default Elasticsearch

Common uses for the default Elasticsearch server (embedded or sidecar) include

- Testing your custom [search and indexing code](../../developer-guide/search-and-indexing.md)
- Developing search queries by running queries directly on Elasticsearch through Kibana
- Testing the [search tuning](../../search_administration_and_tuning.rst) functionality
- Exploring and configuring the [search widgets](../../search_pages_and_widgets.rst)

## App Server Differences

While an Elasticsearch sidecar server is pre-installed for Liferay DXP 7.3 and Liferay Portal CE 7.3 GA4+ Tomcat bundles and Docker images, there are some key differences if you're installing the Lifery DXP WAR onto Tomcat or the other supported application servers.

| Liferay DXP Flavor       | Default Elasticsearch | Pre-Installed | Requires Manual Intervention |
| ------------------------ | ------------------- | ------------- | ---------------------------- |
| Tomcat bundle: 7.3 GA4+  | Sidecar             | &#10004;      | &#10008;                     |
| Tomcat: 7.3 GA4+         | Sidecar             | &#10008;      | &#10008; (auto-downloaded)   |
| Docker tag:    7.3 GA4+  | Sidecar             | &#10004;      | &#10008;                     |
| JBoss: 7.3 GA4+          | Sidecar             | &#10008;      | &#10008; (auto-downloaded)   |
| Wildfly: 7.3 GA4+        | Sidecar             | &#10008;      | &#10008; (auto-downloaded)   |
| WebSphere: 7.3 GA4+      | Sidecar             | &#10008;      | &#10004;                     |
| Weblogic: 7.3 GA4+       | Sidecar             | &#10008;      | &#10004;                     |
| _All flavors: 7.2/7.3 GA3-_ | _Embedded_       | &#10004;      | &#10008;                     |

If you downloaded a bundle for an application server besides Tomcat, when you start the server an Elasticsearch distribution is downloaded on-the-fly and started as a sidecar server.

Installation instructions for Liferay DXP 7.3 on the [WebSphere](../../../installation-and-upgrades/installing-liferay/installing-liferay-on-an-application-server/installing-on-websphere.md) and [Weblogic](../../../installation-and-upgrades/installing-liferay/installing-liferay-on-an-application-server/installing-on-weblogic.md) application servers include directions for manually providing the Elasticsearch archives required for the sidecar server to be initialized.
<!-- ongoing work, LRDOCS-8008 -->

```important::
   The built-in Elasticsearch server is useful for development and testing purposes and must not be used in production. See `Installing Elasticsearch <./getting-started-with-elasticsearch.md>`__ to learn about installing a REMOTE mode search engine.
```

## Embedded versus Sidecar

| EMBEDDED           | SIDECAR           |
| ------------------ | ----------------- |
| Runs at <http://localhost:9200> | Runs at <http://localhost:9201> |
| Pre-Installed on all Liferay DXP distributions  | Not Always Pre-Installed  |
| Not supported for production  | Not supported for production |
| No special steps required for any app server | [Some app servers](#app-server-differences) require additional steps |