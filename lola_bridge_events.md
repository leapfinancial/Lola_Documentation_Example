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
    "event_case": "update_user",
    "sender": {
        "organization_id": "string",
        "organization_name": "string",
        "phone_number": "string",
        "sender_name": "string"
    },
    "tx": {
        "amount": "number",
        "country_origin": "string alpha2",
        "country_destination": "string alpha2",
        "currency_origin": "string",
        "currency_destination": "string"
    },
    "receiver": {
        "organization_id": "string",
        "phone": "string",
        "pending_payment_method": {
            "card": "boolean",
            "CLABE": "boolean"
        },
        "pending_user_data" : ["name", "last_name","DOB","gender", "Address"]
    }
}
```

## Case 2 : Missing Deposit method
```json
{
    "event_case": "add_payment_method",
    "sender": {
        "organization_id": "string",
        "organization_name": "string",
        "phone_number": "string",
        "sender_name": "string"
    },
    "tx": {
        "amount": "number",
        "country_origin": "string alpha2",
        "country_destination": "string alpha2",
        "currency_origin": "string",
        "currency_destination": "string"
    },
    "receiver": {
        "organization_id": "string",
        "phone": "string",
        "pending_payment_method": {
            "card": "boolean",
            "CLABE": "boolean"
        }
    }
}
```

## Case 3 : Both
```json
{
    "event_case": "add_user_and_payment_method",
    "sender": {
        "organization_id": "string",
        "organization_name": "string",
        "phone_number": "string",
        "sender_name": "string"
    },
    "tx": {
        "amount": "number",
        "country_origin": "string alpha2",
        "country_destination": "string alpha2",
        "currency_origin": "string",
        "currency_destination": "string"
    },
    "receiver": {
        "organization_id": "string",
        "phone": "string",
        "pending_payment_method": {
            "card": "boolean",
            "CLABE": "boolean"
        },
        "pending_user_data" : ["all"]
    }
}
```

## Case 4 : Accept
```json
{
    "event_case": "accept_payment",
    "sender": {
        "organization_id": "string",
        "organization_name": "string",
        "phone_number": "string",
        "sender_name": "string"
    },
    "tx": {
        "amount": "number",
        "country_origin": "string alpha2",
        "country_destination": "string alpha2",
        "currency_origin": "string",
        "currency_destination": "string"
    },
    "receiver": {
        "organization_id": "string",
        "phone": "string"
    }
}
```

### All cases respond with the same format
#### Example Response Success

```json
{
    "status": "success",
    "code_transaction": "4ac78c51"
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
