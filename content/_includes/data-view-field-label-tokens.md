There are a variety of special tokens available for use in field labels. These tokens resolve to a specific value for a field.

Token | Description 
--|--
`{CommunityId}` | The value of the community identifier. 
`{CommunityName}` | The value of the community name. 
`{IdentifyingValue}` | The value of the identifying field. 
`{Key}` | The value of the first of the `"Keys"` specified on the field. 
`{StreamReferenceName}` | The value of the first of the `"StreamReferenceNames"` specified on the field. 
`{SummaryType}` | The value of the summary type of the field (if defined). 
`{SummaryDirection}` | The value of the summary direction of the field (if summary type is defined). 
`{QueryId}` | The id of the query that produced the field. 
`{Uom}` | The value of the unit of measure of the field (if UOM is present in the source). 

If a special parameter fails to resolve, it becomes an empty string, `""`.