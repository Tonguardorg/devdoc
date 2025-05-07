## Organizations

### [GET]/api/v2/get_organizations
**Get list of organizations**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

**Example**
```
https://api.tonguard.org/api/v2/get_organizations
```

**Content-Type** `application/json`

**Responses**

| Parameter | Type   | Description                |
|-----------|--------|----------------------------|
| `organizations` | array | List of organizations |

Each organization in the array contains:

| Parameter | Type   | Description                |
|-----------|--------|----------------------------|
| `id`      | string | Organization ID            |
| `name`    | string | Organization name          |
| `type`    | string | Organization type          |
| `status`  | string | Organization status        |
| `created_at` | string | Creation date           |
| `updated_at` | string | Last update date        |

### [POST]/api/v2/upload_claims
**Upload claims for organization**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

**Example**
```
https://api.tonguard.org/api/v2/upload_claims
```

**Content-Type** `multipart/form-data`

**Request Body**

| Parameter | Type   | Description                | Required |
|-----------|--------|----------------------------|----------|
| `organization_id` | string | Organization ID        | yes      |
| `claims_file` | file | Claims file in CSV format | yes      |

**Responses**

| Parameter | Type    | Description                |
|-----------|---------|----------------------------|
| `success` | boolean | Whether upload was successful |
| `message` | string  | Status message             |
``` 