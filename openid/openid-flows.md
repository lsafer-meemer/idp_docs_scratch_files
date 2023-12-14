### Flow Names

Implicit Flow:
- `token`
- `id_token`
- `id_token token`

Authorization Code Flow:
- `code`

Hybrid Flow:
- `code token`
- `code id_token`
- `code id_token token`

### Flow Returns

| Endpoint         | Authorization Code | Access Token | ID Token               | Refresh Token    |
|------------------|--------------------|--------------|------------------------|------------------|
| `/authorization` | `code`             | `token`      | `id_token`             |                  |
| `/token`         |                    | always       | `openid` or `id_token` | `offline_access` |

`code`
: `response_type` includes `code`

`token`
: `response_type` includes `token`

`id_token`
: `response_type` includes `id_token`

`openid`
: `scope` includes `openid`

`offline_access`
: `scope` includes `offline_access`
