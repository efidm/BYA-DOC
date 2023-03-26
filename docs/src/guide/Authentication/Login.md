


# Authentication
## _Login_

You can use this API to login the application with your account.

Actions
- Confirm Password
- Generate tokens
<br>
<br>
  When logging in to the system after password verification.
  OTP verification may be required.(depending on user setting)

  If OTP is needed:
- Creation of an access token with a short validity and will be saved in the HEADER.
- Create otp and send it.

  If no OTP is needed:

- We will receive information about the user, department, services, role, permissions (modules and actions) and language.

- We will create a refresh token with a slightly longer validity and save it in COOKIES.



### Endpoint

```http
POST /auth/login
```

### Parameters

|   Name   |  Type  | Description | Validation                              |      Required      |
| :------: | :----: | :---------: |:----------------------------------------| :----------------: |
|  phone   | string |    phone    | IL - mobile(10 digit)                   | :heavy_check_mark: |
| password | string |  password   | According to the international standard | :heavy_check_mark: |

### Request

```http
POST /auth/login 
Content-Type: application/json
{
"phone":"0555555555",
"password":"********"
}
```

### response
If OTP is needed:

``` http
HTTP/1.1 200 OK
Content-Type: application/json

HEADER: 
authorization : Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhZ2VudElkIjo1ODQsImlhdCI6MTY3OTU2NTIzNiwiZXhwIjoxNjc5NTY1MzU2fQ.dEO7MVVTMItqmBWxRDtU1LOtme891wA8ih8aRsoYXJg

BODY:
{
    "needOtp": 1,
}
```

If no OTP is needed:

``` http
HTTP/1.1 200 OK
Content-Type: application/json

HEADER: 
authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhZ2VudElkIjo1ODQsImlhdCI6MTY3OTU2NTIzNiwiZXhwIjoxNjc5NTY1MzU2fQ.dEO7MVVTMItqmBWxRDtU1LOtme891wA8ih8aRsoYXJg
COOKIES:
Set-Cookie: refresh=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhZ2VudElkIjo1ODQsImlhdCI6MTY3OTU2NTU3MSwiZXhwIjoxNjc5NTY1ODcxfQ.9gXu5o2lPgRAyRhIGRkIfEVVYR_tXz7fYOIFo6tLYGg; 
Max-Age=2592; Path=/; Expires=Thu, 23 Mar 2023 10:42:43 GMT; HttpOnly; Secure; SameSite=None
BODY:
{
    "agentId": 1,
    "departmentId": 1,
    "name": "user user",
    "lang": "he",
    "roles": {
        "roleId": 1,
        "roleName": "Team Lead",
        "roleNameHe": "ראש צוות",
        "subToOrder": 1
    },
    "services": [
        {
            "id": "1",
            "label": "label"
        },...
    ],
    "permissions": [
        {
            "moduleId": 58,
            "label": "customers",
            "canView": 1,
            "canAdd": 1,
            "canEdit": 1,
            "canDelete": 0,
            "agModuleId": 38,
            "actions": [
                {
                    "actionId": 9,
                    "label": "edit_customer"
                },
                {
                    "actionId": 10,
                    "label": "close_customer"
                },
                {
                    "actionId": 11,
                    "label": "send_boradcast_sms"
                }
            ]
        },
       ...
    ],
    "activityTime": {
        "0": {
            "startTime": "6:30",
            "endTime": "22:00"
        },
       ...
    },
    "needOtp": 0
}
```





## Signup

You can use this API to signup the application with your account.

### Logout

```bash
POST /auth/logout
```

### Parameters

|   Name   |  Type  | Description |      Required      |
| :------: | :----: | :---------: | :----------------: |
| username | string |  username   | :heavy_check_mark: |
|  phone   | string |    phone    | :heavy_check_mark: |
| password | string |  password   | :heavy_check_mark: |

### Response

```http
POST /api/users HTTP/1.1
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john.doe@example.com",
  "password": "mysecretpassword"
}
```

