# ZipMonster API

## Endpoints

### `GET` /api/zip/check

Returns information about zip code.

Request example:

```json
{
    "zip": "91360"
}
```

Response example:

```json
{
    "zip": "91360",
    "state": {
        "name": "California",
        "abbreviation": "Calif.",
        "postal_code": "CA"
    },
    "county": "Ventura",
    "city": "Thousand Oaks"
}
```
