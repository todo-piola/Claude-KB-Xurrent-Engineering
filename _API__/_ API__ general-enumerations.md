# Enumerations API

The Xurrent fields in which one option can be selected form a fixed list of values are called enumerations. The Enumerations API provides an easy way to view all enumerations defined by the system.

## List enumerations

The enumerations are available in a few formats:

- [JSON - https://api.xurrent.com/v1/enums](https://api.xurrent.com/v1/enums) (default)
- [HTML - https://api.xurrent.com/v1/enums.html](https://api.xurrent.com/v1/enums.html)
- [CSV - https://api.xurrent.com/v1/enums.csv](https://api.xurrent.com/v1/enums.csv)

And in several languages (see also [internationalization](../../index.html#internationalization)), examples include:

- [English - https://api.xurrent.com/v1/enums.html](https://api.xurrent.com/v1/enums.html) (default)
- [French - https://api.xurrent.com/v1/enums/fr.html](https://api.xurrent.com/v1/enums/fr.html)
- [Danish - https://api.xurrent.com/v1/enums/da.html](https://api.xurrent.com/v1/enums/da.html)

By default all enumerations in the Xurrent application are retrieved in the locale of the API user:

```
GET /enums
```

### Response

```
status: 200 OK
```

```
{"request.status":[{"id":"declined","txt":"Declined"},{"id":"assigned","txt":"Assigned"},{"id":"accepted","txt":"Accepted"},"..."],"task.category":[{"id":"risk_and_impact","txt":"Risk & Impact"},{"id":"approval","txt":"Approval"},{"id":"implementation","txt":"Implementation"}],"language":["..."]}
```
