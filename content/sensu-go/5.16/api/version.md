---
title: "Version API"
description: "The Sensu version API provides HTTP access to the Sensu and etcd versions. This reference includes examples for returning version information about your Sensu instance. Read on for the full reference."
version: "5.16"
product: "Sensu Go"
menu:
  sensu-go-5.16:
    parent: api
---

## The `/version` API endpoint

### `/version` (GET)

The `/version` API endpoint provides HTTP GET access to the Sensu backend and etcd versions for the Sensu instance.

#### EXAMPLE {#version-get-example}

The following example demonstrates a request to the `/version` API endpoint, resulting in a JSON map that contains Sensu version data.

{{< highlight shell >}}
curl http://127.0.0.1:8080/version

HTTP/1.1 200 OK
{
  "Etcd": {
    "etcdserver": "3.3.2",
    "etcdcluster": "3.3.0"
  },
  "SensuBackend": "5.x.x#yyyyyyy"
}
{{< /highlight >}}

#### API Specification {#version-get-specification}

/version (GET)      |      |
--------------------|------
description         | Returns the Sensu backend and etcd version for the Sensu instance.
example url         | http://hostname:8080/version
response type       | Map
response codes      | <ul><li>**Success**: 200 (OK)</li><li>**Error**: 500 (Internal Server Error)</li></ul>
response parameters | Required: <ul><li>`Etcd.etcdserver` (string). Etcd server version.</li><li>`SensuBackend` (string). Sensu backend version in the format x.x.x#yyyyyyy where x.x.x is the Sensu version and yyyyyyy is the release SHA</li></ul><br>Optional:<ul><li>`Etcd.etcdcluster` (string). Etcd cluster version for Sensu instances with the default embedded etcd. Not required to match the etcd server version or the cluster versions of other backends in the cluster.</li></ul>
output         | {{< highlight shell >}}
{
  "Etcd": {
    "etcdserver": "3.3.2",
    "etcdcluster": "3.3.0"
  },
  "SensuBackend": "5.x.x#yyyyyyy"
}
{{< /highlight >}}
