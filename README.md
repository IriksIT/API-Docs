# Iriks-IT API
## _API Documentation_

[![N|Solid](https://iriks-it.nl/iriks-it.png)](https://iriks-it.nl/)

> **View the live interactive documentation at [https://docs.iriks-it.nl](https://docs.iriks-it.nl)**
>
> The OpenAPI spec in this repository is the source of truth, but the rendered docs at the link above are much nicer to browse.

## What's in the API?

| Area | Description |
| ------ | ------ |
| Account | Register, verify, and log in to obtain a Bearer token |
| Products | Product catalog — list, create, update, and delete |
| Hot Wheels | Hot Wheels collection tracker — full CRUD |
| IP Tools | IP intelligence: geolocation, ASN, proxy detection, AbuseIPDB threat data, and reporting an IP to AbuseIPDB |

## Authentication

All endpoints (except register, verify, and login) require a Bearer token:

```
Authorization: Bearer <your-token>
```

Tokens are obtained via `/v1/auth/login` and expire after **24 hours**.

## Rate Limiting

The API enforces per-account rate limiting on all authenticated endpoints.

| Header | Description |
| ------ | ------ |
| `X-RateLimit-Limit` | Maximum requests allowed in the current window |
| `X-RateLimit-Remaining` | Requests remaining before the window resets |
| `X-RateLimit-Reset` | Unix timestamp of when the window resets |

When the limit is exceeded the API returns **HTTP 429** with a `Retry-After` header indicating how many seconds to wait.

Certain endpoints (such as IP lookup) may enforce a lower limit specific to that operation. The headers always reflect the limit in effect for the current request.

## Handy Links

| Name | Link |
| ------ | ------ |
| Live docs | [https://docs.iriks-it.nl](https://docs.iriks-it.nl) |
| API | [https://api.iriks-it.nl](https://api.iriks-it.nl) |

## License

MIT

**Free Software, Hell Yeah!**
