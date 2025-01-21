## Whitelist
Upload and download wallets in your whitelist. 

Custom whitelisting in AML compliance involves creating a list of entities or individuals that are classified as trusted or verified, exempting them from certain scrutiny processes. 
These entities are added to the whitelist only after a thorough due diligence process, ensuring they pose minimal risk of involvement in money laundering or other
financial crimes. 

The main objective of custom whitelisting is to minimize false positives in risk assessments and streamline the compliance process.
When a wallet is included in the custom whitelist, its risk level in the risk assessment process is automatically reduced to a low level.

### [GET]/v1/whitelists/whitelist.csv

Method is used to **download whitelist as a file**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```
**Example**
```
https://my.tonguard.org/v1/whitelists/whitelist.csv
```

**Responses**

`200` **Data successfully downloaded**

**Content-Type** `application/json`

```json
{
  "title": "Response Download"
}
```

**Error codes** see full specification [here ](../errors.md)

***


### [POST]/v1/whitelists/whitelist.csv
Method is used to **upload whitelist data**

```
HTTP request header provide  with `token` in the following format:
token: "Bearer <jwt token>"
```

```
{
  // CSV file containing whitelist data.
  file: string
}
```

**Responses**

`200` **Data successfully uploaded**

**Content-Type** `application/json` 

```
{
  "title": "Response Upload"
}
```

**Error codes** see full specification [here ](../errors.md)

***
