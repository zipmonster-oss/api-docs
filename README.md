# ZipMonster API

## Endpoints

Base URL for all endpoints: https://zip-monster-backend.herokuapp.com

All requests should include `api_key`. For testing purposes, you can use `"api_key": "test"`. To receive your personal API key, [contact administrator](mailto:russo.programmisto@gmail.com).

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
    "city": "Thousand Oaks",
    "location": {
        "latitude": 34.2090940366232,
        "longitude": -118.875059125606
    }
}
```

----

### `GET` /api/zip/by-ip-address

Finds zip code by IP address and returns full information.

Request example *(will use client's IP address)*:

```json
{
    "api_key": "test"
}
```

Another request example *(will use value from* `ip_address` *parameter)*:

```json
{
    "api_key": "test",
    "ip_address": "161.185.160.20"
}
```

Response example:

```json
{
    "ip_address": "161.185.160.20",
    "zip": "11221",
    "state": {
        "name": "New York",
        "abbreviation": "N.Y.",
        "postal_code": "NY"
    },
    "county": "Kings",
    "city": "Brooklyn",
    "location": {
        "latitude": 40.6910642109398,
        "longitude": -73.9284754630217
    }
}
```

----

### `GET` /api/address/check

Verifies if address exists and returns full information about it.

Request example:

```json
{
    "full_address": "1600 Amphitheatre Parkway Mountain View, CA 94043",
    "api_key": "test"
}
```

Alternatively, you can send JSON payload that includes separate elements of the address:

```json
{
    "line_1": "1600 Amphitheatre Parkway",
    "city": "Mountain View",
    "state": "CA",
    "zip": "94043",
    "api_key": "test"
}
```

In both cases you will receive the same response:

```json
{
    "exists": true,
    "address": {
        "line_1": "1600 Amphitheatre Pkwy",
        "street_number": "1600",
        "street_name": "Amphitheatre",
        "street_suffix": "Pkwy",
        "city": "Mountain View",
        "county": "Santa Clara",
        "state": {
            "name": "California",
            "abbreviation": "Calif.",
            "postal_code": "CA"
        },
        "zip": "94043"
    }
}
```

Btw, even if your request doesn't include zip code, ZipMonster will find it automatically and return in response! So you can simply send `"1600 Amphitheatre Parkway Mountain View CA"`, zip code is an optional thing here.

