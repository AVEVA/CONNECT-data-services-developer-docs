---
uid: sdsCompression
---

# Compression

To use network bandwidth efficiently, the Sequential Data Store supports compression for [stream data](xref:sds-stream-data) through the REST API.

## Supported compression schemes

- `gzip`
- `deflate`

## Request compression for writing data

The body content of an HTTP request can be compressed using the [supported compression schemes](#supported-compression-schemes), allowing you to send stream values to the REST API more efficiently.

Use the `Content-Encoding` HTTP header to specify the compression scheme of compressed-content requests. This header provides context to the API to properly decode the request content.

## Response compression for reading data

You can request compressed responses from the REST API by specifying one of the [supported compression schemes](#supported-compression-schemes) using the `Accept-Encoding` HTTP header.

Compressed responses from the REST API include a `Content-Encoding` HTTP header that indicates the compression scheme used to compress the response content.

> [!NOTE]
> Specifying a compression scheme through the use of the `Accept-Encoding` HTTP header does not guarantee a compressed response. Always refer to the presence and value of the `Content-Encoding` HTTP header of the response to properly decode the response content.
