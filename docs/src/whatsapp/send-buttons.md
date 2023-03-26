
### _Send buttons_
---
<br>

::: warning pay attention
You can use the "Send Message" API in one case only:

You reply to a message that the client sent, within 24 hours since the client sent his last message.

If you send a message to a new client, or try to send a message to an old client (old client means that 24 hours since client's last message has passed), you must use the "Send Template Message" API instead.

If you send a template message to the client, and the client did not reply yet, and you want to send another message to him, you must use the template message again.

:::



#### <u>Remarks</u>

* You can only send a message to private people, not groups.
* The billing is per "conversation". conversation means a 24 hours session between you and the client (this 24 hours conversation session is unrelated to the 24 hours timer for template message)
* You can send unlimited messages within the 24 hours session time of a conversation.
* 24 hours session conversation starts when you send a message to the client.
* Every time the user replies, the template message session resets. which means that you don't have to use template message during this 24 hours template message session.



### Endpoint

```http
POST https://019sms.co.il/api/whatsapp/sendMessage
```


### Header

|     Name      |         Type          |      Required      |
|:-------------:|:---------------------:|:------------------:|
| Authorization | Bearer authentication | :heavy_check_mark: |
| Content-Type  |   application/json    | :heavy_check_mark: |


### Parameters

|  Name   |  Type  |                                                              Description                                                               |      Required      |
|:-------:|:------:|:--------------------------------------------------------------------------------------------------------------------------------------:|:------------------:|
|  from   | string |                            your WhatsApp account. international number without +. for example: 972771234567                            | :heavy_check_mark: |
|   to    | string |                                 The number you want to send the message to. for example: 972501234567                                  | :heavy_check_mark: |
|  body   | string |         your message goes here<br><br> \n for new line<br> *text* for bold<br> _text_ for italic<br> ~text~ for strike through         | :heavy_check_mark: |
| replyTo | string | In case you want to reply to a message that the end user has sent (quoted message), here you can provide the unique ID of that message | :heavy_minus_sign: |


---
<br><br>

### Response

```http 
POST api/whatsapp/sendMessage HTTPS/1.1
Content-Type: application/json

{
"status": "OK",
"unique": "65dfd4r4dref34rdfxd34r",
"body": "your message",
"timestamp": 1600115719,
"from": "972507654321",
"to": "972501234567",
"templateTimeLeft": "400",
"conversationTimeLeft": "800",
"reason": 1
}
```

### Parameters

|         Name         |  Type  |                                                                            Description                                                                             |
|:--------------------:|:------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|        status        | string |                                          your WhatsApp account. international number without +. for example: 972771234567                                          |
|        unique        | string |                                                                     unique ID for any message                                                                      |
|         body         | string |                                                                         the text you sent                                                                          |
|      timestamp       | string |                                                                             time stamp                                                                             |
|         from         | string |                                                                       your WhatsApp account                                                                        |
|          to          | string |                                                              the number that the message was sent to                                                               |
|   templateTimeLeft   | string |  amount of minutes left since client's last message. if passed, you must use Template Message. This value resets every time the client is sending you a message.   |
| conversationTimeLeft | string | amount of minutes left for the conversation session to end. if passed, any message after that, will be considered as a new conversation, and the timer will reset. |




### Status explanation

| Status | Description                                                                                                                         |
|--------|-------------------------------------------------------------------------------------------------------------------------------------|
| 1      | not FAIL. the status is OK                                                                                                          |
| 2      | Your "from" number account does not exist, or JSON syntax error                                                                     |
| 3      | wrong apiKey                                                                                                                        |
| 4      | 'to' is either empty or wrong number format                                                                                         |
| 5      | 'body' can't be empty                                                                                                               |
| 6      | WhatsApp error - try again                                                                                                          |
| 7      | You are trying to send a message but it has been more than 24 hours since client's last message. please use 'Send Template' instead |
| 8      | You are trying to send a message for first time to a contact. please use 'Send Template' message instead                            |