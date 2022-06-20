There are a variety of special tokens available for use in field labels. These tokens resolve to a specific value for a field. The following list describes each available token.

<table>
	<thead>
	<tr>
		<th>Token</th>
		<th>Description</th>
	</tr>
	</thead>
	<tbody>
	<tr>
		<td><code>{CommunityId}</code></td>
		<td>The value of the community identifier.</td>
	</tr>
	<tr>
		<td><code>{CommunityName}</code></td>
		<td>The value of the community name.</td>
	</tr>
	<tr>
		<td><code>{IdentifyingValue}</code></td>
		<td>The value of the identifying field.</td>
	</tr>
	<tr>
		<td><code>{Key}</code></td>
		<td>The value of the first of the <code>Key</code> objects specified on the field.</td>
	</tr>
	<tr>
		<td><code>{QueryId}</code></td>
		<td>The identifier of the query that produced the field.</td>
	</tr>
	<tr>
		<td><code>{StreamReferenceName}</code></td>
		<td>The value of the first of the <code>StreamReferenceName</code> objects specified on the field.</td>
	</tr>
	<tr>
		<td><code>{SummaryType}</code></td>
		<td>The value of the summary type of the field (if defined).</td>
	</tr>
	<tr>
		<td><code>{SummaryDirection}</code></td>
		<td>The value of the summary direction of the field (if summary type is defined).</td>
	</tr>
	<tr>
		<td><code>{Uom}</code></td>
		<td>The value of the unit of measure of the field (if UOM is present in the source).</td>
	</tr>
	<tbody>
</table>

If a special parameter fails to resolve, it becomes an empty string, `""`.