There are a variety of special tokens available for use in field labels. These tokens resolve to a specific value for a field. The following list describes each available token.

<ul>
	<li><code>{CommunityId}</code>—The value of the community identifier.</li>
	<li><code>{CommunityName}</code>—The value of the community name.</li>
	<li><code>{IdentifyingValue}</code>—The value of the identifying field.</li>
	<li><code>{Key}</code>—The value of the first of the "Keys" specified on the field.</li>
	<li><code>{QueryId}</code>—The id of the query that produced the field.</li>
	<li><code>{StreamReferenceName}</code>—The value of the first of the "StreamReferenceNames" specified on the field.</li>
	<li><code>{SummaryType}</code>—The value of the summary type of the field (if defined).</li>
	<li><code>{SummaryDirection}</code>—The value of the summary direction of the field (if summary type is defined).</li>
	<li><code>{Uom}</code>——The value of the unit of measure of the field (if UOM is present in the source).</li>
</ul>

If a special parameter fails to resolve, it becomes an empty string, `""`.