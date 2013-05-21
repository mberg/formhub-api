---
category: 'Forms'
path: '/forms.json'
title: 'Get forms'
type: 'GET'
layout: nil
---

###Request Parameters###

* `allProperties` - boolean field (default true) specifying that all the core and extended properties should be returned.

`/forms.json?allProperties={true/false}`


SORTING

* `sortAsc` - Sort ascending
* `sortDesc` - Sort descending

`/forms.json?sortAsc={property1}`

Sorting is currently limited to one field

PAGINATION

* `limit` - Number of records to return in a result. Default = 25
* `offset` - Offset of the search result. Default = 0
* `limit=off` - Disables pagination. Pagination on by default.

`/facilities.json?limit=25&offset=50`

PARTIAL RESPONSE

* `fields` - specifies which fields should be returned in the response.

`/facilities.json?fields=name,id,properties:numBeds`

This would return just the specified properties of name, id and numBeds (in the properties sub-object) in a partial response. This is very helpful in optimizing performance in bandwidth constrained settings. All properties in the facility registry are accessible by this method including the core properties and those in the property sub-object.

FILTERING FACILITIES

* `{propertyName}` - name of the property you want to filter by

`/facilities.json?{propertyName}={filterValue}`

* Supports only exact matches of the filter value
* One value per instance of parameter
* Name of a parameter must exactly match the name of the property (core or extended) on which it filters data
* Instances of the same parameter are OR and different are AND.
For example: ?properties:services=OBG&properties:services=ER would filter all facilities offering OBG OR ER, where as ?identifiers:id=2030&identifiers:agency=MOH would filter facilities with an identifier 2030 AND identifier assigned by MOH.

FILTER BY ACTIVE STATUS

* `active` - filter facilities based on whether they are active or not.

`/facilities.json?active={true/false}`

FILTER BY UPDATED SINCE

* `updatedSince` - return facilities updated since a particular date expressed in ISO 8601 format.

`/facilities.json?updatedSince=2011-11-16T00:00:00Z`

### Response

```Status: 200 OK```

Returns a collection of forms



```{
    "forms": [
        {
            "name": "form name",
            "formID": "form_name",
            "version": "",
            "hash": "md5:b62285b40b24bf089a4f81e6b47ca323",
            "downloadUrl": "https://formhub.org/user/forms/form_name/form.xml",
            "manifestUrl": "https: //formhub.org/user/forms/form_name"
        }
    ]
```}


