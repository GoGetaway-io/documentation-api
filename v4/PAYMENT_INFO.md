### Redirect Link
Redirection works for such currencies as EUR, USD, UZS, TRY, INR.
The link must be in the format: https://gogateway.io
Supported links are: successLink, failureLink.

For successLink and failureLink, the txnId parameters are added to the address.
Example, successLink = https://gogateway.io/api/callback/success

The final link will look like https://gogateway.io/api/callback/success?txnId=bf3c5d88-b8c3-4c5e-81ff-7aca056df538

txnId, this is the id parameter from the body of the request to create a payment

### Status code
- PAYMENT_CANCELED - Payment has been canceled
- PAYMENT_SUCCESSFUL - Payment was successful
- PAYMENT_UNDEFINED - Unidentified error
- TIME_EXPIRED - Payment was not paid within the allotted time.

### List of currencies and supported payment methods
* RUB - ALFA, RAIFFEISENBANK, VTB, SBERBANK, OTKRITIE, MKB, TINKOFF, SBP_SBERBANK, SBP_TINKOFF, MASTERCARD (Bank selection occurs on the payment side)
* KZT - KASPI, EURASIAN, JUSAN, MASTERCARD (Bank selection occurs on the payment side)
* EUR - MASTERCARD
* USD - MASTERCARD
* UZS - MASTERCARD
* TRY - MASTERCARD
* INR - MASTERCARD
* BRL - MASTERCARD

## Email config
This is the configuration object for sending emails.

If you want us to send emails, set all values to true.

This is the object :
```json
{
  "client": boolean,
  "merchant": boolean
}
```

## Customer
Customer, this is the data from the Card Holder.
Transmitted in the format:
```json
{
  "customer": {
    "firstName": "FIRST",
    "lastName": "LAST"
  }
}
```

## Credit Card
This is only needed for USD currency

```json
{
  "card": {
      "cardholder": "Test User",
      "csc": "111",
      "pan": "4596610005864424",
      "expiry": "0139"
  } 
}
```

## Language
Supported language:
* ru
* en
