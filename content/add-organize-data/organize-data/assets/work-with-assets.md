---
uid: WorkWithAssets
---

# Working with assets created with asset rules

<!-- There may be a better title -->

The following describes the relationship between an asset rule and the generated assets:

- If you delete an asset rule, then any assets created with the rule are also deleted. There may be a short delay between the time the rule is deleted and when the related assets are deleted. 

- You can edit the properties of assets created with asset rules. These edits take precedence over the asset rule configuration. For example, if you edit the asset name, the rule does not overwrite this edit.

- Manually deleting an asset is treated as an edit of the asset. Like other edits, the deletion overrides the rule. Therefore, if you delete an asset created by an asset rule, you will not be able to recreate that asset with the same Id.  If you inadvertently delete an asset, you can recover the asset by first deleting the rule. This will delete any assets created with this rule. Then you can recreate the rule and configure the Id so that it resolves to a different Id. For example, assume that the asset Id in the first rule resolved to *Boiler Tank 1* and this asset is deleted in error. In the second rule, the Id resolves to, for example, *Region 1 - Boiler Tank 1*. OCS sees this as different  asset and will create it. 
