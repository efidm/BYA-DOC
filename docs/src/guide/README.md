### General

::: tip ✨ BYA API IS HERE!
Now you can use our API to manage a business system
by the bya platform
:::


In order to generate the API TOKEN you must send an XML similar to the following example:


### Endpoint

```http
POST http://backbuya.019mobile.co.il:8085
```

### Body structure


### Request headers

|     Header      |       Type       |      Required      |
|:-------------:|:----------------:|:------------------:|
| Content-Type  | application/json | :heavy_minus_sign: |
|     Authorization |    Bearer {token}| :heavy_check_mark: |


### Response 

### <span style="color: green"> Success responses </span>

### Failure responses
#### Error structure accentColor
####  Validation errors:
``status - 400 ``
##### Parameter error

```http 
{
    "phone": {
        "code": 1009,
        "message": "Invalid phone"
    },
    "password": {
        "code": 1008,
        "message": "Invalid value"
    }
 }
```

##### General error

```http 
{
    "general": {
        "code": 20001,
        "message": "The value entered is not valid"
    }
}
```

### Parameters

|      Name       |  Type  |            Description            |
|:---------------:|:------:|:---------------------------------:|
|     status      | string |          Response status          |
|     message     | string |        New / current token        |
| expiration_date | string | Expiration_date of returned token |


<br><br>



After generating API Token you can use it in our services
<br><br>
[SMS →](/sms/)
<br>
[WHATSAPP →](/whatsapp/)