# ZipMonster API

## Endpoints

All requests should include `api_key`. For testing purposes, you can use `"api_key": "test"`.

### `GET` /api/zip/check

Returns information about zip code.

Request example:

```json
{
    "zip": "91360",
    "api_key": "test"
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
