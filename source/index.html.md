---
title: API V3 Documentation
language_tabs:
  - ruby

search: true

code_clipboard: true

---
# Authentication

Authentication endpoints

## Sign up using username/email/password


### Request

#### Endpoint

```plaintext
POST /api/v3/sign_up/
Content-Type: application/vnd.api+json
```

`POST /api/v3/sign_up/`

#### Parameters


```json
{"data":{"attributes":{"email":"curt_hirthe@oberbrunner.io","password":"testPassword","username":"Wyatt Nitzsche"},"type":"user"}}
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1dWlkIjoiYjMyODNjYmQtYzQzMS00ODU1LWFlZGUtOGNmZWUwYzFjMzNmIiwic3ViIjoiNTUiLCJzY3AiOiJ1c2VyIiwiYXVkIjpudWxsLCJpYXQiOjE2NzUwNzc3MjQsImV4cCI6MzI1MjkyNTMyNCwianRpIjoiZDRjMjRhMDctZDE1MC00NDFmLTg0NTMtYTRkY2MyNTUwZWYzIn0.D88Gtu7ERXjehnLm54GBGc1nrgzjokqCnaqQhUoWEYc
201 Created
```


```json
{
  "data": {
    "id": "eddf80cc-3bd9-4418-b6a4-dccc9027d2b7",
    "type": "token",
    "attributes": {
      "access_token": "eyJhbGciOiJIUzI1NiJ9.eyJ1dWlkIjoiYjMyODNjYmQtYzQzMS00ODU1LWFlZGUtOGNmZWUwYzFjMzNmIiwic3ViIjoiNTUiLCJzY3AiOiJ1c2VyIiwiYXVkIjpudWxsLCJpYXQiOjE2NzUwNzc3MjQsImV4cCI6MzI1MjkyNTMyNCwianRpIjoiZDRjMjRhMDctZDE1MC00NDFmLTg0NTMtYTRkY2MyNTUwZWYzIn0.D88Gtu7ERXjehnLm54GBGc1nrgzjokqCnaqQhUoWEYc",
      "token_type": "Bearer",
      "expires_in": null
    }
  },
  "meta": {
    "request_id": "8a2c3f7e-3772-4255-b376-02dd1fd822a5",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```
