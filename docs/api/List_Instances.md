---
layout: default
permalink: /docs/api/List_Instances/
sidebar: yes
---

List all configured Yamcs instances:

    GET /api/instances


### Parameters

<table class="inline">
    <tr>
        <th>Name</th>
        <th>Type</th>
        <th>Description</th>
    </tr>
    <tr>
        <td class="code">pretty</td>
        <td class="code">bool</td>
        <td>format the JSON result in a human readable manner</td>
    </tr>
</table>

### Response

{% highlight json %}
{
  "instance" : [ {
    "name" : "simulator",
    "missionDatabase" : {
      "configName" : "landing",
      "name" : "",
      "url" : "http://localhost:8090/api/mdb/simulator",
      "parametersUrl" : "http://localhost:8090/api/mdb/simulator/parameters{/namespace}{/name}",
      "containersUrl" : "http://localhost:8090/api/mdb/simulator/containers{/namespace}{/name}",
      "commandsUrl" : "http://localhost:8090/api/mdb/simulator/commands{/namespace}{/name}"
    },
    "processor" : [ {
      "name" : "realtime",
      "url" : "http://localhost:8090/api/processors/simulator/realtime",
      "parametersUrl" : "http://localhost:8090/api/processors/simulator/realtime/parameters{/namespace}{/name}",
      "commandsUrl" : "http://localhost:8090/api/processors/simulator/realtime/commands{/namespace}{/name}"
    } ],
    "url" : "http://localhost:8090/api/instances/simulator",
    "clientsUrl" : "http://localhost:8090/api/clients/simulator{/processor}",
    "commandQueuesUrl" : "http://localhost:8090/api/cqueues/simulator{/processor}",
    "eventsUrl" : "http://localhost:8090/api/events/simulator"
  } ]
}
{% endhighlight %}


### Protobuf

Response is of type `Rest.ListInstancesResponse`.

{% highlight nginx %}
message ListInstancesResponse {
  repeated yamcsManagement.YamcsInstance instance = 1;
}
{% endhighlight %}

Supporting definitions:

<pre class="header">
    yamcsManagement.proto
</pre>

{% highlight nginx %}
message YamcsInstance {
  required string name = 1;
  optional MissionDatabase missionDatabase = 3;
  repeated ProcessorInfo processor = 4;
  optional string url = 5;
  optional string clientsUrl = 6;
  optional string commandQueuesUrl = 7;
  optional string eventsUrl = 8;
}

message MissionDatabase {
  required string configName = 1; //this is the config section in mdb.yaml
  required string name = 2; //XTCE root SpaceSystem name
  optional string version = 3; //XTCE root SpaceSystem header version
  optional string url = 4;
  optional string parametersUrl = 5;
  optional string containersUrl = 6;
  optional string commandsUrl = 7;
}
{% endhighlight %}