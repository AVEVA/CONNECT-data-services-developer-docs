---
uid: MetadataRulesOverview
---

# Metadata Rules (Preview)

Metadata, or “data about data,” is information you assign to data objects.  The value of metadata itself lies in its capacity to enrich sequential data, and to facilitate logical segregation and contextualization of data, thus supporting analytical, visualization, organizational and searchability efforts. 

Metadata rules enable the bulk creation and maintenance of stream metadata, which can then be used across OSIsoft Cloud Services. Other services and applications, such as OCS data views, leverage stream metadata to simplify finding data and to provide context about stream data.

## The Metadata rules feature
The metadata rules feature in the OCS Portal simplifies the process of defining metadata and assigning it to streams.  The user interface guides you through the designation of the parts of the selected stream name as metadata, string literals, or wildcards, and prompts you to define key-value pairs for the parts you designate as metadata.

After you save the rule, it assigns the defined metadata to every stream matching the pattern defined in your rule. Changes and deletions of existing metadata rules may cascade through to all affected streams.  A change in the metadata rule definition can result in the rule capturing a different set of streams. When deleting a rule, you have the option of keeping or deleting assigned metadata from all streams captured by the rule.

## Metadata Rules Documentation
OCS Metadata rules enable you to define and create metadata, which OCS assigns to objects that meet the criteria you specify. Metadata rules help users define patterns in their stream names, using delimited parts of the selected stream name, to quickly extract valuable information as more streams are added. 

You begin by selecting an existing stream name in the OCS Portal, and observing the delimited parts of the stream name.  Name parts can be “delimited,” or separated, by any non-alphanumeric character placed within the name, typically to separate meaningful sections of the name.  

An example stream name follows:

```
chi.x22.flow
```

In the above example, “chi” is the location code for a customer facility, “x22” is the device ID for a specific device, and “flow” is the type of data provided by this stream.

You can create a new metadata rule based on stream name chi.x22.flow, where the delimited parts of the stream name have the following meanings:

- chi = facility location
- x22 = a specific device
- flow = the data provided by the stream

For each delimited part of a stream name, you assign one of the following part types:

- metadata = key-value pair
- string literal = accepts only exact match
- wildcard = accepts any value

If the rule is intended to capture streams from the “chi” facility location only, that part of the stream name should be designated as a string literal.  This is not a variable, and only stream names displaying this literal location code should be captured.

If “x22” is the ID for a specific device, and you want to capture “flow” streams for all devices in the “chi” location, then the “x22” part of the stream name should be designated as metadata, with a key defined as Device ID.  This will allow the rule to capture streams with any value in that part of the stream name, and assign Device ID as its key.

**Note:**	If the rule were intended to capture any type of streams for all devices in the “chi” location, then the “flow” part of the stream name should be designated as a wildcard.  To capture only streams of type "flow," the "flow" stream type should be designated as a string literal.

## Key-Value pairs
For each part of the stream name that you designate as metadata, you define a key, under which any value that occupies that specific part of the stream name pattern will be categorized. This creates a key-value pair for each value captured by that portion of the rule.  The key-value structure will facilitate analytical processing of the data returned by the rule you create. 
