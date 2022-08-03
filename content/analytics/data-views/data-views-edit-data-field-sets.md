---
uid: data-views-edit-data-field-sets
---

# Edit data field sets

Eiusmod sit qui proident nostrud ea enim enim adipisicing qui fugiat veniam voluptate irure. Amet consectetur reprehenderit exercitation aliquip ea cillum adipisicing ipsum tempor in eu. Magna sit adipisicing nulla cillum. Incididunt cupidatat nulla eu elit dolore culpa est deserunt aute aliqua. Et culpa ea eiusmod quis cupidatat. Nisi exercitation voluptate id amet exercitation.

## Add data field to field set

Each data field set is composed of data fields from streams or assets. You can organize your data view to use one or more of these fields to group your data view. The fields you choose to use for grouping display in the data view to the immediate right of the index field.

1. In the left pane, select **Analytics** > **Data Views**.

1. Select the data view that you want to edit.

1. Select **Edit Data View**.

1. From the left panel, select **Add**.

	The **Add Data Fields** window opens, listing the field set for each query. 

1. Add the data fields that you want to include in your field sets.

	**Note:** Each data field set must include each least one field. If you edit a data view that includes a query with no data fields in its field set, you are prompted automatically prompted to add data fields to the set.

1. Select **Apply**.

The data fields are added to the field set.

## Remove data field from a field set

1. From the left panel, select the data fields that you want to remove from each query. 

	**Tip:** You can select all fields for a field set by selecting the checkbox for the query.

1. Select **Remove**.

	**Note:** Removing all fields from a field set does not remove the query from the field set—only the fields. For more information on removing a query from a data view, see [To remove queries from a data view](xref:data-views-manage-queries#to-remove-queries-from-a-data-view).

	The selected fields are removed from the applicable field sets.

## Add identifying field to field set

If the field set resolves to multiple data items in any group (or if grouping is not used), then you should designate an **Identifying field** for the field set. The identifying field of a data field set specifies the primary field to identify multiple items in a group. This identification methods allows the identifying field value to be used automatically in field labels of the group. If a lone criterion is not a sufficient or useful way of disambiguating the fields, then grouping by additional criteria may be necessary. 

Fields are only eligible if they include one or more of the following source types listed in the table below. Some source types include the an requirement of having a key defined. following table lists eligible data sources along with additional requirements for keys.

| Eligible source type | Key required? |
|----------------------|---------------|
| Id                   | &#10006;      |
| Name                 | &#10006;      |
| Metadata             | ✔            |
| Tags                 | ✔            |

To add an identifying field to a field set, select **Identifying Field** and choose an eligible field. You can only choose a single field.

**Add an identifying field**

![add-an-identifying-field](_images/add-an-identifying-field.png)

## Edit data fields

Fugiat velit ullamco ex consectetur sunt irure commodo. Sint ad et proident do ad in. Id esse dolor eu labore commodo aute adipisicing tempor sit exercitation. Consectetur laboris non deserunt incididunt elit. Exercitation et laboris reprehenderit eiusmod eu adipisicing dolor commodo. Et deserunt velit eiusmod sint eu incididunt nisi aute consectetur enim aliquip amet ipsum voluptate.

## Edit field order

Culpa dolor eiusmod cillum consequat sit ipsum deserunt pariatur officia dolor minim eu. Magna sint nisi tempor officia commodo in fugiat consectetur minim proident consequat est enim. Dolor fugiat irure tempor elit. Consequat do adipisicing magna fugiat officia incididunt aute. Qui amet dolore deserunt eiusmod enim incididunt reprehenderit dolor sit sunt.

## Link fields

Commodo aliqua adipisicing laboris minim voluptate. Aliqua nisi esse reprehenderit amet esse cupidatat qui excepteur officia amet officia esse ea. Quis ad excepteur id consectetur aute anim nisi ipsum ex qui fugiat ipsum esse irure. Voluptate non eiusmod incididunt elit labore. Aute commodo velit et eiusmod consequat ad.

## View field mappings

Irure dolor veniam incididunt nulla quis voluptate ut adipisicing anim. Dolor anim eu fugiat dolor consequat cillum nisi pariatur laborum ipsum duis aliquip. Eu deserunt nisi sint cupidatat proident. Enim incididunt voluptate nulla veniam. Ullamco anim non enim adipisicing dolor non eiusmod dolor fugiat. Est amet pariatur pariatur esse adipisicing in duis et qui excepteur. Anim pariatur velit cillum velit excepteur consequat minim aute non in occaecat enim.