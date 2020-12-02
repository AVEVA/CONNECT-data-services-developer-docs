# What AF data gets transferred in PI to OCS?

The AF data you can transfer from your on-premises PI system to OCS include the following:

<ul><li>Elements</li>
<ul><li>Static attribute values</li>
<li>Simple PI point attributes</li></ul>.  

A simple PI point attribute consists of only a server and tag name.  This data does not include any data retrieval qualifiers.  The associated event data is also include with simple PI point attributes with the same historical and streaming transfer mechanism as points not associated with AF.  



| AF Object | Supported in transfer to PI to OCS? | 
| ------------- | ----------------- | 
| Elements | Yes |
| Attributes | Yes|
| PI point references | Yes |
| Constant values/string | Yes |
| Excluded attributes | Yes |
| Formulas | No |
| Event frames | No|
| PI point arrays | No |
| Hidden attributes | No |