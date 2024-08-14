# LOLA BRIDGE EVENTS
#### JSON examples

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

This document contains the example json for the different cases of the events
1) Missing user data
2) Missing Deposit method
3) Both
4) Accept

## Actions from case
The parameter that defines the event will be event_case which can only have the following values.

| Case | Param event_case values |
| ------ |------|
| 1) Missing user data | add_user |
| 2) Missing Deposit method | add_payment_method |
| 3) Both | add_user_and_payment_method |
| 4) Accept | accept_payment |

## Case 1 : Missing user data (no support) 
```sh
{
    "event_case": "add_user",
    "sender": {
        "organization_id": "string",
        "organization_name": "string",
        "phone_number": "string",
        "sender_name": "string"
    }
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
        pending_user_data : ["name", "last_name","DOB","gender", "Address"]
    }
}
```

## Case 2 : Missing Deposit method
```sh
{
    "event_case": "add_payment_method",
    "sender": {
        "organization_id": "string",
        "organization_name": "string",
        "phone_number": "string",
        "sender_name": "string"
    }
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
        pending_user_data : ["all"]
    }
}
```

## Case 3 : Both
```sh
{
    "event_case": "add_user_and_payment_method",
    "sender": {
        "organization_id": "string",
        "organization_name": "string",
        "phone_number": "string",
        "sender_name": "string"
    }
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
        pending_user_data : ["all"]
    }
}
```
## Case 4 : Accept
```sh
{
    "event_case": "accept_payment",
    "sender": {
        "organization_id": "string",
        "organization_name": "string",
        "phone_number": "string",
        "sender_name": "string"
    }
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
        pending_user_data : []
    }
}
```