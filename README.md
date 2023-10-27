## Blocksettle Merchant API Documentation 
# Title: Payment Processing API Documentation

## Endpoint: POST /payin

Initiates a payment into a specified account.

### Request Headers:

- **Authorization**: Bearer token for authentication.

### Request Body:

- **amount** (optional): The amount of money to be paid in. Default value is 100.0 if not provided.

```json
{
    "amount": 200.0,
    "currecny" : "SEK"
}
```

### Responses:

#### Success Response:

- **HTTP Status Code**: 200
- **Body**:

```json
{
    "error": false,
    "data": {
        "amount": 0.0,
        "deposit_ccy": "SEK",
        "merchant_ccy": "EUR",
        "deposit_amount": "0",
        "account": {
            // deposit account details
        },
        "deposit_ref": "unique_deposit_reference"
    },
    "message": null
}
```

#### Error Responses:

- **HTTP Status Code**: 400
- **Body** (Example: No SEK account found):

```json
{
    "error": true,
    "data": null,
    "message": "No SEK account found"
}
```

- **HTTP Status Code**: 401
- **Body** (Example: Authorization header missing or malformed):

```json
{
    "error": true,
    "data": null,
    "message": "Authorization header missing or malformed."
}
```

### Example cURL Request:

```bash
curl -X POST "https://api.example.com/payin" \
     -H "Authorization: Bearer your_token" \
     -d '{"amount":200.0}'
```
