---
uid: PIAdapterForDNP3DataSourceDiscovery
---

# Data source discovery

A discovery against the data source of a DNP3 adapter allows you to specify the optional **query** parameter. The discovery query defines which outstations to discover.

**Note:** Only one discovery at a time is supported.

## Query string

The string of the **query** parameter may contain string items in the following form: <br>`OutstationIds=<id>,<id2>,<id3>,...`<br><br>
| String item      | Required | Description |
|------------------|----------|-------------|
| **OutstationIds**  | Optional |  The outstation IDs to be discovered.<br>**Note:** To specify multiple outstation IDs in the query, separate the outstation IDs with a comma. If **OutstationIds** is not specified, the adapter will perform discovery for each outstation in the data source. |

**Note:** An outstation id is a user-defined identifier for an outstation in the data source configuration.

### Query rules

The following rules apply for specifying the query string:

- Multiple comma-separated outstationIds are supported.
- Each outstation ID specified in the query string must be present in the data source.
- `OutstationIds=` must be followed by a outstationId.
- Empty string and all white spaces string is equivalent to no query specified.
- White spaces in the `OutstationIds=` section of the query are not supported

**Note:** The data source might contain many outstations, or outstations that already have corresponding data selection items. Use `OutstationIds` to limit discovery to the outstations that should be discovered.

## Discovery query example

The query parameter of the DNP3 component must be specified as shown in this example:
`OutstationIds=Outstation1,Outstation2`.

### Data source discovery initiation

```json
{
    "id" : "SampleA",
    "query" : "OutstationIds=Outstation1,Outstation2"
}
```

### Data source discovery results

```json
[
    {
        "id": "SampleA",
        "query": "OutstationIds=Outstation1,Outstation2",
        "startTime": "2020-12-14T14:19:01.4383791-08:00",
        "endTime": "2020-12-14T14:19:31.8549164-08:00",
        "progress": 30,
        "itemsFound": 700,
        "newItems": 200,
        "resultUri": "http://127.0.0.1:5590/api/v1/Configuration/DNP3-1/Discoveries/SampleA/result",
        "autoSelect": false,
        "status": "Complete",
        "errors": null
    }
]
```

### DNP3 discovered selection items

The following items are an example of what might be discovered on _Outstation1_ and _Outstation2_. This will vary based on what is returned by the integrity scan used for discovery. 

```json
[
  {
    "outstationId": "Outstation1",
    "group": 1,
    "index": 0,
  },
  {
    "outstationId": "Outstation1",
    "group": 30,
    "index": 0,
  },
  {
    "outstationId": "Outstation1",
    "group": 20,
    "index": 0,
  },
  {
    "outstationId": "Outstation2",
    "group": 3,
    "index": 1,
  },
  {
    "outstationId": "Outstation2",
    "group": 30,
    "index": 2,
  }
]
```
