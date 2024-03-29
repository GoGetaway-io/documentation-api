### FAQ
- [PAYOUT_TYPE](PAYMENT_INFO.md#payout-type)

## Host url - https://bsc.gogateway.io

## PAYOUT
 - Request Method: POST
 - Request Path: /api/v4/payout

### Request Description
Create order for payout.

#### Headers

| Name            | Required | Description
|-----------------|----------|-----------------
| GOGATEWAY-V4-TOKEN | √        | Token
| Content-Type    | √        | application/json

#### Request Payload

 - Content-Type: application/json

## RUB
```json
{
    "amount": number,
    "currency": string,
    "paymentMethod": PAYOUT_TYPE,
    "requisites": string,
}
```

## INR
### PhonePe
```json
{
    "amount": number,
    "currency": "INR",
    "paymentMethod": "MASTERCARD",
    "paymentInfo": {
        "type": "phone_pe",
        "phone": "89995520074",
        "accountNumber": "ZX872AA"
    }
}
```

### Upi
```json
{
    "amount": number,
    "currency": "INR",
    "paymentMethod": "MASTERCARD",
    "paymentInfo": {
        "type": "upi",
        "cardholder": "FIRST SECOND",
        "accountNumber": "ZX872AA"
    }
}
```

### imps
```json
{
    "amount": number,
    "currency": "INR",
    "paymentMethod": "MASTERCARD",
    "paymentInfo": {
        "type": "imps",
        "cardholder": "FIRST SECOND",
        "accountNumber": "ZX872AA",
        "swiftBic": "RACZHUH1"
    }
}
```

### Example Response

#### 1. Success.

 - Status Code: 200 OK
 - Content-Type: application/json; charset=utf-8


```json
{
    "success": true,
    "data": {
        "id": "acb63380-fba7-480d-a5d9-57acdc9afa61",
        "code": "PROCESSING"
    }
}
```
#### 2. Check Card.

 - Status Code: 400 Bad Request
 - Content-Type: application/json; charset=utf-8


```json
{
    "success": false,
    "data": {
        "message": "Invalid parameter for creditCard Specified bin not found"
    }
}
```

#### 2. Wrong payment amount

 - Status Code: 400 Bad Request
 - Content-Type: application/json; charset=utf-8


```json
{
    "success": false,
    "data": {
        "message": "Invalid amount"
    }
}
```

#### 3. Incorrect token.

 - Status Code: 401 Unauthorized
 - Content-Type: application/json; charset=utf-8


```json
{
    "success": false,
    "data": {
        "message": "Dont valid token"
    }
}
```

## Successful CallBack
Callback url set manually, via GOGATEWAY support (telegram, facebook, otc...)

```
POST: custom url
```
If the response status isn't 200, send a repeat callback after 15 minutes.

signature - encrypted data to check if the request body matches the sent data.

### Request Parameters
#### Header
| Name | Type | Desc |
| :------ | :------ | :------ |
| `signature` | `string` | `amount:id`
#### Body
| Name | Type | Desc |
| :------ | :------ | :------ |
| `data.id` | `number` | `Transaction id`
| `data.amount` | `number` | `Sum payment`
| `data.currency` | `string` | `Currency of the made payment`
| `data.feeAmount` | `number` | `Payment fee, maybe missing`
| `meta.code` | `string` | `Status code of payment`

### Response
Status 200 - OK
```
{}
```

## PAYOUT LIST INFO
 - Request Method: POST
 - Request Path: /api/v4/payout/statuses

### Request Description
Get information about all payouts.

#### Headers

| Name            | Required | Description
|-----------------|----------|-----------------
| GOGATEWAY-V4-TOKEN | √        | Token
| Content-Type    | √        | application/json


### Example Response

#### 1. Success.

 - Status Code: 200 OK
 - Content-Type: application/json; charset=utf-8


```json
{
    "success": true,
    "data": [
        {
            "id": "a5047386-6081-4c78-a461-ef1383a6c2dd",
            "amount": 10000,
            "currency": "INR",
            "created": "2023-01-22T09:52:21.992Z",
            "status": "PROCESSING"
        }
   ]
}
```
