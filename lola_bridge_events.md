# LOLA BRIDGE EVENTS
#### JSON examples

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

This document contains the example json for the different cases of the events
1) Missing user data
2) Missing Deposit method
3) Both
4) Accept

Requests should be to this endpoint
https://lola-bridge-development.up.railway.app/v1/eventManager/init-operation

## Actions from case
The parameter that defines the event will be event_case which can only have the following values.

| Case | Param event_case values |
| ------ |------|
| 1) Missing user data | update_user |
| 2) Missing Deposit method | add_payment_method |
| 3) Both | add_user_and_payment_method |
| 4) Accept | accept_payment |

## Case 1 : Missing user data (no support) 
```json
{
    "eventCase": "update_user",
    "userFrom": {
        "userId": "user123",
        "orgId": "org123",
        "firstName": "John",
        "lastName": "Doe",
        "phoneNumber": "+1234567890",
        "email": "john.doe@example.com",
        "imageUrl": "http://example.com/image.jpg",
        "country": "USA",
        "profilePictureUrl": "http://example.com/profile.jpg"
    },
    "userTo": {
        "userId": "user456",
        "orgId": "org456",
        "firstName": "Jane",
        "lastName": "Smith",
        "phoneNumber": "+0987654321",
        "email": "jane.smith@example.com",
        "imageUrl": "http://example.com/image2.jpg",
        "country": "MEX",
        "profilePictureUrl": "http://example.com/profile2.jpg"
    },
    "pendingPaymentMethod": "method123",
    "pendingUserData": ["data1", "data2"],
    "operation": {
        "id": "operation123",
        "platId": "plat123",
        "correlationId": "corr123",
        "type": "payment",
        "createdAt": "2023-10-01T12:00:00Z",
        "amount": 100.0,
        "status": "pending",
        "statusDetails": "Awaiting confirmation",
        "mobileStatus": "active",
        "reason": "Payment processing",
        "code": "OP123",
        "recipientAmount": 95.0,
        "senderAmount": 100.0,
        "showWarningScreen": false,
        "currency": "USD",
        "senderCurrency": "USD",
        "recipientCurrency": "EUR",
        "sourcePaymentMethod": {
            "id": "pm123",
            "number": "4111111111111111",
            "country": "USA",
            "currency": "USD",
            "accountNumber": "123456789",
            "isPrimary": true,
            "type": "credit_card",
            "name": "Visa",
            "bin": "411111",
            "accountPrefix": "1234"
        },
        "destinationPaymentMethod": {
            "id": "pm456",
            "number": "4222222222222222",
            "country": "FRA",
            "currency": "EUR",
            "accountNumber": "987654321",
            "isPrimary": false,
            "type": "debit_card",
            "name": "MasterCard",
            "bin": "422222",
            "accountPrefix": "5678"
        },
        "sourceFee": 2.0,
        "transactionFee": 3.0,
        "destinationFee": 1.0,
        "exchangeRate": 0.85,
        "estimatedExchangeRate": 0.84,
        "hasReferenceCode": true,
        "fromUser": {
            "userId": "user123",
            "orgId": "org123",
            "firstName": "John",
            "lastName": "Doe",
            "phoneNumber": "+1234567890",
            "email": "john.doe@example.com",
            "imageUrl": "http://example.com/image.jpg",
            "country": "USA"
        },
        "toUser": {
            "userId": "user456",
            "orgId": "org456",
            "firstName": "Jane",
            "lastName": "Smith",
            "phoneNumber": "+0987654321",
            "email": "jane.smith@example.com",
            "imageUrl": "http://example.com/image2.jpg",
            "country": "FRA"
        },
        "attributionLink": "http://example.com/attribution",
        "isIgnored": false,
        "ignoredData": null,
        "tenantFee": 5.0,
        "totalAmount": 110.0,
        "tax": 1.5,
        "userId": "user123"
    }
}
```

## Case 2 : Missing Deposit method
```json
{
    "eventCase": "add_payment_method",
    "userFrom": {
        "userId": "user123",
        "orgId": "org123",
        "firstName": "John",
        "lastName": "Doe",
        "phoneNumber": "+1234567890",
        "email": "john.doe@example.com",
        "imageUrl": "http://example.com/image.jpg",
        "country": "USA",
        "profilePictureUrl": "http://example.com/profile.jpg"
    },
    "userTo": {
        "userId": "user456",
        "orgId": "org456",
        "firstName": "Jane",
        "lastName": "Smith",
        "phoneNumber": "+0987654321",
        "email": "jane.smith@example.com",
        "imageUrl": "http://example.com/image2.jpg",
        "country": "MEX",
        "profilePictureUrl": "http://example.com/profile2.jpg"
    },
    "pendingPaymentMethod": "method123",
    "pendingUserData": ["data1", "data2"],
    "operation": {
        "id": "operation123",
        "platId": "plat123",
        "correlationId": "corr123",
        "type": "payment",
        "createdAt": "2023-10-01T12:00:00Z",
        "amount": 100.0,
        "status": "pending",
        "statusDetails": "Awaiting confirmation",
        "mobileStatus": "active",
        "reason": "Payment processing",
        "code": "OP123",
        "recipientAmount": 95.0,
        "senderAmount": 100.0,
        "showWarningScreen": false,
        "currency": "USD",
        "senderCurrency": "USD",
        "recipientCurrency": "EUR",
        "sourcePaymentMethod": {
            "id": "pm123",
            "number": "4111111111111111",
            "country": "USA",
            "currency": "USD",
            "accountNumber": "123456789",
            "isPrimary": true,
            "type": "credit_card",
            "name": "Visa",
            "bin": "411111",
            "accountPrefix": "1234"
        },
        "destinationPaymentMethod": {
            "id": "pm456",
            "number": "4222222222222222",
            "country": "FRA",
            "currency": "EUR",
            "accountNumber": "987654321",
            "isPrimary": false,
            "type": "debit_card",
            "name": "MasterCard",
            "bin": "422222",
            "accountPrefix": "5678"
        },
        "sourceFee": 2.0,
        "transactionFee": 3.0,
        "destinationFee": 1.0,
        "exchangeRate": 0.85,
        "estimatedExchangeRate": 0.84,
        "hasReferenceCode": true,
        "fromUser": {
            "userId": "user123",
            "orgId": "org123",
            "firstName": "John",
            "lastName": "Doe",
            "phoneNumber": "+1234567890",
            "email": "john.doe@example.com",
            "imageUrl": "http://example.com/image.jpg",
            "country": "USA"
        },
        "toUser": {
            "userId": "user456",
            "orgId": "org456",
            "firstName": "Jane",
            "lastName": "Smith",
            "phoneNumber": "+0987654321",
            "email": "jane.smith@example.com",
            "imageUrl": "http://example.com/image2.jpg",
            "country": "FRA"
        },
        "attributionLink": "http://example.com/attribution",
        "isIgnored": false,
        "ignoredData": null,
        "tenantFee": 5.0,
        "totalAmount": 110.0,
        "tax": 1.5,
        "userId": "user123"
    }
}
```

## Case 3 : Both
```json
{
    "eventCase": "add_user_and_payment_method",
    "userFrom": {
        "userId": "user123",
        "orgId": "org123",
        "firstName": "John",
        "lastName": "Doe",
        "phoneNumber": "+1234567890",
        "email": "john.doe@example.com",
        "imageUrl": "http://example.com/image.jpg",
        "country": "USA",
        "profilePictureUrl": "http://example.com/profile.jpg"
    },
    "userTo": {
        "userId": "user456",
        "orgId": "org456",
        "firstName": "Jane",
        "lastName": "Smith",
        "phoneNumber": "+0987654321",
        "email": "jane.smith@example.com",
        "imageUrl": "http://example.com/image2.jpg",
        "country": "MEX",
        "profilePictureUrl": "http://example.com/profile2.jpg"
    },
    "pendingPaymentMethod": "method123",
    "pendingUserData": ["data1", "data2"],
    "operation": {
        "id": "operation123",
        "platId": "plat123",
        "correlationId": "corr123",
        "type": "payment",
        "createdAt": "2023-10-01T12:00:00Z",
        "amount": 100.0,
        "status": "pending",
        "statusDetails": "Awaiting confirmation",
        "mobileStatus": "active",
        "reason": "Payment processing",
        "code": "OP123",
        "recipientAmount": 95.0,
        "senderAmount": 100.0,
        "showWarningScreen": false,
        "currency": "USD",
        "senderCurrency": "USD",
        "recipientCurrency": "EUR",
        "sourcePaymentMethod": {
            "id": "pm123",
            "number": "4111111111111111",
            "country": "USA",
            "currency": "USD",
            "accountNumber": "123456789",
            "isPrimary": true,
            "type": "credit_card",
            "name": "Visa",
            "bin": "411111",
            "accountPrefix": "1234"
        },
        "destinationPaymentMethod": {
            "id": "pm456",
            "number": "4222222222222222",
            "country": "FRA",
            "currency": "EUR",
            "accountNumber": "987654321",
            "isPrimary": false,
            "type": "debit_card",
            "name": "MasterCard",
            "bin": "422222",
            "accountPrefix": "5678"
        },
        "sourceFee": 2.0,
        "transactionFee": 3.0,
        "destinationFee": 1.0,
        "exchangeRate": 0.85,
        "estimatedExchangeRate": 0.84,
        "hasReferenceCode": true,
        "fromUser": {
            "userId": "user123",
            "orgId": "org123",
            "firstName": "John",
            "lastName": "Doe",
            "phoneNumber": "+1234567890",
            "email": "john.doe@example.com",
            "imageUrl": "http://example.com/image.jpg",
            "country": "USA"
        },
        "toUser": {
            "userId": "user456",
            "orgId": "org456",
            "firstName": "Jane",
            "lastName": "Smith",
            "phoneNumber": "+0987654321",
            "email": "jane.smith@example.com",
            "imageUrl": "http://example.com/image2.jpg",
            "country": "FRA"
        },
        "attributionLink": "http://example.com/attribution",
        "isIgnored": false,
        "ignoredData": null,
        "tenantFee": 5.0,
        "totalAmount": 110.0,
        "tax": 1.5,
        "userId": "user123"
    }
}
```

## Case 4 : Accept
```json
{
    "eventCase": "accept_payment",
    "userFrom": {
        "userId": "user123",
        "orgId": "org123",
        "firstName": "John",
        "lastName": "Doe",
        "phoneNumber": "+1234567890",
        "email": "john.doe@example.com",
        "imageUrl": "http://example.com/image.jpg",
        "country": "USA",
        "profilePictureUrl": "http://example.com/profile.jpg"
    },
    "userTo": {
        "userId": "user456",
        "orgId": "org456",
        "firstName": "Jane",
        "lastName": "Smith",
        "phoneNumber": "+0987654321",
        "email": "jane.smith@example.com",
        "imageUrl": "http://example.com/image2.jpg",
        "country": "MEX",
        "profilePictureUrl": "http://example.com/profile2.jpg"
    },
    "pendingPaymentMethod": "method123",
    "pendingUserData": ["data1", "data2"],
    "operation": {
        "id": "operation123",
        "platId": "plat123",
        "correlationId": "corr123",
        "type": "payment",
        "createdAt": "2023-10-01T12:00:00Z",
        "amount": 100.0,
        "status": "pending",
        "statusDetails": "Awaiting confirmation",
        "mobileStatus": "active",
        "reason": "Payment processing",
        "code": "OP123",
        "recipientAmount": 95.0,
        "senderAmount": 100.0,
        "showWarningScreen": false,
        "currency": "USD",
        "senderCurrency": "USD",
        "recipientCurrency": "EUR",
        "sourcePaymentMethod": {
            "id": "pm123",
            "number": "4111111111111111",
            "country": "USA",
            "currency": "USD",
            "accountNumber": "123456789",
            "isPrimary": true,
            "type": "credit_card",
            "name": "Visa",
            "bin": "411111",
            "accountPrefix": "1234"
        },
        "destinationPaymentMethod": {
            "id": "pm456",
            "number": "4222222222222222",
            "country": "FRA",
            "currency": "EUR",
            "accountNumber": "987654321",
            "isPrimary": false,
            "type": "debit_card",
            "name": "MasterCard",
            "bin": "422222",
            "accountPrefix": "5678"
        },
        "sourceFee": 2.0,
        "transactionFee": 3.0,
        "destinationFee": 1.0,
        "exchangeRate": 0.85,
        "estimatedExchangeRate": 0.84,
        "hasReferenceCode": true,
        "fromUser": {
            "userId": "user123",
            "orgId": "org123",
            "firstName": "John",
            "lastName": "Doe",
            "phoneNumber": "+1234567890",
            "email": "john.doe@example.com",
            "imageUrl": "http://example.com/image.jpg",
            "country": "USA"
        },
        "toUser": {
            "userId": "user456",
            "orgId": "org456",
            "firstName": "Jane",
            "lastName": "Smith",
            "phoneNumber": "+0987654321",
            "email": "jane.smith@example.com",
            "imageUrl": "http://example.com/image2.jpg",
            "country": "FRA"
        },
        "attributionLink": "http://example.com/attribution",
        "isIgnored": false,
        "ignoredData": null,
        "tenantFee": 5.0,
        "totalAmount": 110.0,
        "tax": 1.5,
        "userId": "user123"
    }
}
```

### All cases respond with the same format
#### Example Response Success

```json
{
  "status": "success",
  "code_transaction": "d2fa8f99",
  "url_transaccion": "https://lola-bridge-development.up.railway.app/v1/eventManager/url?codeTX=d2fa8f99"
}
```
#### Example Response Error

```json
{
    "detail": [
        {
            "field": "amount",
            "message": "Input should be a valid number, unable to parse string as a number"
        },
        {
            "field": "card",
            "message": "Input should be a valid boolean, unable to interpret input"
        },
        {
            "field": "CLABE",
            "message": "Input should be a valid boolean, unable to interpret input"
        }
    ]
}
```
