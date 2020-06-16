# Troubleshooting Elasticsearch Installation

Sometimes things don't go as planned. If you've set up Liferay DXP with Elasticsearch in remote mode, but Liferay DXP can't connect to Elasticsearch, check these things:

**Cluster name:** The value of the `cluster.name` property in `elasticsearch.yml` must match
the `clusterName` property configured in the Liferay DXP Elasticsearch connector.

**Transport address:** The value of the `transportAddresses` property in the Elasticsearch connector configuration must contain at least one valid host and port where an Elasticsearch node is running. If Liferay DXP is running in embedded mode, and you start a standalone Elasticsearch node or cluster, it detects that port `9300` is taken and switches to port `9301`. If you then set Liferay's Elasticsearch connector to remote mode, it continues to look for Elasticsearch at the default port (`9300`).

The following articles cover the Liferay Connector to Elasticsearch's configuration options in more detail.

**Cluster Sniffing (Additional Configurations):**Elasticsearch clusters can have multiple node [types](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/modules-node.html#modules-node).  [Cluster sniffing](https://www.elastic.co/guide/en/elasticsearch/client/java-api/7.x/transport-client.html), enabled by default in the Liferay DXP connector, looks for `data` nodes configured in the `transportAddresses` property. If none are available, the connector may throw a `NoNodeAvailableException` in the console log. If cluster sniffing is to remain enabled, be sure that your configuration allows for at least one `data` node's transport address to be "sniffable" at all times to avoid this error.

To disable cluster sniffing, add `clientTransportSniff=false` to the `.config` file or un-check the Client Transport Sniff property in System Settings.