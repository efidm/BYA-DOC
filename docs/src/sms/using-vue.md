


## Login

You can use this API to login the application with your account.

### Endpoint

```http
POST /auth/login
```

### Parameters

|   Name   |  Type  | Description |      Required      |
| :------: | :----: | :---------: | :----------------: |
| username | string |  username   | :heavy_check_mark: |
|  phone   | string |    phone    | :heavy_minus_sign: |
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


## Logout

You can use this API to signup the application with your account.

### Endpoint

```bash
POST /Authentication/signup
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

