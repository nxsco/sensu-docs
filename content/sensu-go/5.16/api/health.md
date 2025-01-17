---
title: "Health API"
description: "The Sensu health API provides HTTP access to health data for your Sensu instance. This reference includes examples for retrieving health information about your Sensu instance. Read on for the full reference."
version: "5.16"
product: "Sensu Go"
menu:
  sensu-go-5.16:
    parent: api
---

## The `/health` API endpoint

### `/health` (GET)

The `/health` API endpoint provides HTTP GET access to health data for your Sensu instance.

#### EXAMPLE {#health-get-example}

The following example demonstrates a request to the `/health` API endpoint, resulting in a JSON map that contains Sensu health data.

{{< highlight shell >}}
curl http://127.0.0.1:8080/health

HTTP/1.1 200 OK
{
  "Alarms": null,
  "ClusterHealth": [
    {
      "MemberID": 9882886658148554927,
      "Name": "default",
      "Err": "",
      "Healthy": true
    }
  ],
  "Header": {
    "cluster_id": 4255616304056076734,
    "member_id": 9882886658148554927,
    "raft_term": 26
  }
}
{{< /highlight >}}

#### API Specification {#health-get-specification}

/health (GET)  | 
---------------|------
description    | Returns health information about the Sensu instance.
example url    | http://hostname:8080/health
response type  | Map
response codes | <ul><li>**Success**: 200 (OK)</li><li>**Error**: 500 (Internal Server Error)</li></ul>
output         | {{< highlight shell >}}
{
  "Alarms": null,
  "ClusterHealth": [
    {
      "MemberID": 9882886658148554927,
      "Name": "default",
      "Err": "",
      "Healthy": true
    }
  ],
  "Header": {
    "cluster_id": 4255616304056076734,
    "member_id": 9882886658148554927,
    "raft_term": 26
  }
}
{{< /highlight >}}
