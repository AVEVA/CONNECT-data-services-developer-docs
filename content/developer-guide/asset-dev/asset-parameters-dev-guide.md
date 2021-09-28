---
uid: asset-parameters-dev-guide
---

# Asset Parameters

The asset feature supports the HTTP entity tag (ETag) and If-Match for conditional requests. When a `GET` call is performed, the HTTP response header includes an Etag which indicates what version of the asset resource will be retrieved.

See [Asset and AssetType Access Control API](xref:AssetOrAssetTypeAccessControlAPI), [Asset Centric Data API](xref:AssetCentricDataAPI), and [Assets Search API](xref:AssetsSearchAPI) for additional API details.

## Example Etag Response Header
This is version 7 of this particular asset.

```
Etag: "7"
```

To edit or delete the asset, specify `If-Match` in the HTTP request header when calling `DELETE` or `PUT`.

## Example If-Match Response Header
Modify or delete only if the current asset matches version 7. Otherwise, do not perform this operation. If this condition fails, return a 412. 

```
If-Match : "7"
```

**Note:** `If-Match` is optional. If you want to delete or modify an asset regardless of the asset version, do not specify an `If-Match`.

## Asset Type Concordance

If an asset type `Id` is specified for an asset, then the following is true:
- The stream references name of an asset is set to null if the stream reference `Id` matches the stream reference `Id` of the asset type.
- If the asset and asset type have a metadata value with the same `Id`, then the `Name` property on the asset is set to null. 
