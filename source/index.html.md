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



## Sign up using empty body


### Request

#### Endpoint

```plaintext
POST /api/v3/sign_up/
Content-Type: application/vnd.api+json
```

`POST /api/v3/sign_up/`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Username can't be blank"
    }
  ]
}
```



## Send an email with the instructions, return 200 status


### Request

#### Endpoint

```plaintext
POST /api/v3/password/
Content-Type: application/vnd.api+json
```

`POST /api/v3/password/`

#### Parameters


```json
{"data":{"type":"user","attributes":{"email":"vertie@goyette.info","reset_password_token":"","password":"new_password"}}}
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "success": "Reset password instructions sent to vertie@goyette.info"
  }
}
```



## Update the password and returns the user


### Request

#### Endpoint

```plaintext
PUT /api/v3/password/
Content-Type: application/vnd.api+json
```

`PUT /api/v3/password/`

#### Parameters


```json
{"data":{"type":"user","attributes":{"email":"lorilee.stroman@schumm-hyatt.biz","reset_password_token":"M-GSCeKETQAvzbfkK9pt","password":"new_password"}}}
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1dWlkIjoiZGVkYjMzYjAtMmVmMC00ZWU3LTkyZTUtYzI3YzBkOTc4MTAyIiwic3ViIjoiNTgiLCJzY3AiOiJ1c2VyIiwiYXVkIjpudWxsLCJpYXQiOjE2NzUwNzc3MjUsImV4cCI6MzI1MjkyNTMyNSwianRpIjoiNmMxMTEwOTEtNDI1Zi00ZDBkLWExOTItYzY4M2NlNGQyMThmIn0.uXeYaKcCSQTtgtNzwly1p16HotnigWAJjT91-zO6Cik
200 OK
```


```json
{
  "data": {
    "id": "07196094-6ac8-4f39-84a4-41ad3f0b0576",
    "type": "token",
    "attributes": {
      "access_token": "eyJhbGciOiJIUzI1NiJ9.eyJ1dWlkIjoiZGVkYjMzYjAtMmVmMC00ZWU3LTkyZTUtYzI3YzBkOTc4MTAyIiwic3ViIjoiNTgiLCJzY3AiOiJ1c2VyIiwiYXVkIjpudWxsLCJpYXQiOjE2NzUwNzc3MjUsImV4cCI6MzI1MjkyNTMyNSwianRpIjoiNmMxMTEwOTEtNDI1Zi00ZDBkLWExOTItYzY4M2NlNGQyMThmIn0.uXeYaKcCSQTtgtNzwly1p16HotnigWAJjT91-zO6Cik",
      "token_type": "Bearer",
      "expires_in": null
    }
  },
  "meta": {
    "request_id": "1035b157-8798-4959-a6d1-223e7224638f",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Update the password and returns the user


### Request

#### Endpoint

```plaintext
POST /api/v3/password/token_validation
Content-Type: application/vnd.api+json
```

`POST /api/v3/password/token_validation`

#### Parameters


```json
{"data":{"type":"user","attributes":{"reset_password_token":"JT3USjeByZ67XBzM1N5y"}}}
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Reset password token is valid"
    }
  ]
}
```



## Reset password should expire


### Request

#### Endpoint

```plaintext
POST /api/v3/password/token_validation
Content-Type: application/vnd.api+json
```

`POST /api/v3/password/token_validation`

#### Parameters


```json
{"data":{"type":"user","attributes":{"reset_password_token":"STQSDAF774oNqdovsT5E"}}}
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Reset password token  invalid"
    }
  ]
}
```



## return the user with 200 status


### Request

#### Endpoint

```plaintext
POST /api/v3/sign_in/
Content-Type: application/vnd.api+json
Api-Key: 46e67c525617663b392a53c0e94ba79e62db62a851fb175ae87756d4e73c9718
```

`POST /api/v3/sign_in/`

#### Parameters


```json
{"data":{"attributes":{"email":"jadwiga@schuppe.biz","password":"testPassword"},"type":"user"}}
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1dWlkIjoiZTNkZTAxNDctMjYwYi00ZDIyLWI1OTUtMTc5YTgzMjMxODkyIiwic3ViIjoiNjIiLCJzY3AiOiJ1c2VyIiwiYXVkIjpudWxsLCJpYXQiOjE2NzUwNzc3MjYsImV4cCI6MzI1MjkyNTMyNiwianRpIjoiZDcxMWNlNzMtY2Q1ZS00NGNmLWE3MDgtNDFjMDVjN2Q1OGVlIn0.-N4uJQFGWct-9Km0qB3VPEwDV8kY7GzYhMIBsuCXoPI
200 OK
```


```json
{
  "data": {
    "id": "c5739c21-10cc-4b7b-af53-18f208bf7b1a",
    "type": "token",
    "attributes": {
      "access_token": "eyJhbGciOiJIUzI1NiJ9.eyJ1dWlkIjoiZTNkZTAxNDctMjYwYi00ZDIyLWI1OTUtMTc5YTgzMjMxODkyIiwic3ViIjoiNjIiLCJzY3AiOiJ1c2VyIiwiYXVkIjpudWxsLCJpYXQiOjE2NzUwNzc3MjYsImV4cCI6MzI1MjkyNTMyNiwianRpIjoiZDcxMWNlNzMtY2Q1ZS00NGNmLWE3MDgtNDFjMDVjN2Q1OGVlIn0.-N4uJQFGWct-9Km0qB3VPEwDV8kY7GzYhMIBsuCXoPI",
      "token_type": "Bearer",
      "expires_in": null
    }
  },
  "meta": {
    "request_id": "70a4f0e5-5082-41c7-8963-5b1b72a6d1bf",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



#### Fields

| Name       | Description         |
|:-----------|:--------------------|
| data[attributes][access_token] | access_token for the user |


## returns an error


### Request

#### Endpoint

```plaintext
POST /api/v3/sign_in/
Content-Type: application/vnd.api+json
Api-Key: foo-bar
```

`POST /api/v3/sign_in/`

#### Parameters


```json
{"data":{"attributes":{"email":"adah@buckridge-cruickshank.name","password":"testPassword"},"type":"user"}}
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1dWlkIjoiZWRiZDJkNzMtMzE1ZS00NGNjLThmN2EtZDQzYjM5ODg4NzM4Iiwic3ViIjoiNjQiLCJzY3AiOiJ1c2VyIiwiYXVkIjpudWxsLCJpYXQiOjE2NzUwNzc3MjcsImV4cCI6MzI1MjkyNTMyNywianRpIjoiYjgxY2NlY2UtNjgxMy00OWVhLWE0NzUtZTc5ZDQxMGVlYTZhIn0.IkEIvNBL_yNueKi5-GUo2kTfVbdU5z-6kbIL1GPH-jQ
401 Unauthorized
```


```json
{
  "errors": [
    {
      "status": "unauthorized",
      "source": {
        "pointer": "base"
      },
      "title": "API-Key header is missing/invalid."
    }
  ]
}
```



#### Fields

| Name       | Description         |
|:-----------|:--------------------|
| data[attributes][access_token] | access_token for the user |


## return an error


### Request

#### Endpoint

```plaintext
POST /api/v3/sign_in/
Content-Type: application/vnd.api+json
Api-Key: 46e67c525617663b392a53c0e94ba79e62db62a851fb175ae87756d4e73c9718
Accept-Language: 
```

`POST /api/v3/sign_in/`

#### Parameters


```json
{"data":{"attributes":{"email":"david@papershift.com","password":"wrongPassword"},"type":"user"}}
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Email or password is invalid!"
    }
  ]
}
```



## returns access-token


### Request

#### Endpoint

```plaintext
POST /api/v3/sign_in/
Content-Type: application/vnd.api+json
Api-Key: oItYF3CGFBmbcZphFAaBKSohPX9iytOBUs5pkvO2
Accept-Language: 
```

`POST /api/v3/sign_in/`

#### Parameters


```json
{"data":{"attributes":{"email":"jimmie@howe.io","password":"testPassword"},"type":"user"}}
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1dWlkIjoiMzU1MTllNWYtZmUyMi00OGZmLTg4ZjItNTdmYTk3ODY4MDQ5Iiwic3ViIjoiNzMiLCJzY3AiOiJ1c2VyIiwiYXVkIjpudWxsLCJpYXQiOjE2NzUwNzc3MjgsImV4cCI6MzI1MjkyNTMyOCwianRpIjoiOTdkNzUzYWQtMDE5YS00MzNlLTg0NDktM2E4NTAzNTI0ZGQzIn0.A7sBsTaIKwjDZjOx9N0xgLU7gSuO4OoaSvrT6OvliIA
200 OK
```


```json
{
  "data": {
    "id": "a7f74f69-2c4d-4325-8f86-ee74b23bae0b",
    "type": "token",
    "attributes": {
      "access_token": "eyJhbGciOiJIUzI1NiJ9.eyJ1dWlkIjoiMzU1MTllNWYtZmUyMi00OGZmLTg4ZjItNTdmYTk3ODY4MDQ5Iiwic3ViIjoiNzMiLCJzY3AiOiJ1c2VyIiwiYXVkIjpudWxsLCJpYXQiOjE2NzUwNzc3MjgsImV4cCI6MzI1MjkyNTMyOCwianRpIjoiOTdkNzUzYWQtMDE5YS00MzNlLTg0NDktM2E4NTAzNTI0ZGQzIn0.A7sBsTaIKwjDZjOx9N0xgLU7gSuO4OoaSvrT6OvliIA",
      "token_type": "Bearer",
      "expires_in": null
    }
  },
  "meta": {
    "request_id": "977e4a79-087c-4b48-8d9a-0404fc1eea96",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Sign out


### Request

#### Endpoint

```plaintext
DELETE /api/v3/sign_out/
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/sign_out/`

#### Parameters


None known.


### Response

```plaintext

204 No Content
```

# Errors

The Papershift API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The request is hidden for administrators only.
404 | Not Found -- The specified record could not be found.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.


# Filters

You can easily filter all the collections by following the pattern:

This will query records where the name equals Company_1.

`/api/v3/accounts/1/workspaces?filter[name]=eq:Company_1`

**Note**: Invalid matchers or fields are simply gonna be ignored, so, if your filtering is not working, check for misspellings!

| Name | Description |
|:-----|:------------|
|eq  |equal
|!eq |not equal
|gt  |greather than
|gte |greather or equal
|lt  |less than
|lte |less than or equal
|pre |starts with
|suf |ends with
|ct  |contains
|!ct |does not contain
|in  |match values in array
|present |not null and not empty

# Sorting

You can easily sort all the collections by following the pattern:

Add `+` or nothing to sort in ascending order

Add `-` to sort in descending order

This will sort by name (in ascending order)

`/api/v3/accounts/1/workspaces?sort=name`

This will sort by name (in ascending order) and by id (in descending order):

`/api/v3/accounts/1/workspaces?sort=name,-id`

# Pagination

All our collection endpoints contain a pagination system integrated, to use them you can send the following variables on the query params:

**items**: Items per page

**outset**: Outset on the beginning of list (also known as offset)

**page**: Current page

The following pagination info will be sent in the response meta data:

**Current-Page**: The current page

**Page-Items**: Number of items per page

**Total-Pages**: Number of pages

**Total-Count**: Number of items

# Absences


## returns all absences


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences`

#### Parameters



| Name | Description |
|:-----|:------------|
| filter  | Absences overlapping with range |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 3
200 OK
```


```json
{
  "data": [
    {
      "id": "33",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:54Z",
        "updated_at": "2023-01-30T11:22:54Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "43",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "529",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "34",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "confirmed",
        "confirmed": true,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:54Z",
        "updated_at": "2023-01-30T11:22:54Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "43",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "530",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "35",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "rejected",
        "confirmed": false,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:54Z",
        "updated_at": "2023-01-30T11:22:54Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "43",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "531",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "b15b2200-7b9b-40c6-84f0-d71ddbee9eab",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 3,
    "pending": 1,
    "confirmed": 1,
    "rejected": 1,
    "total_days": 3.0,
    "total_hours": 0.0
  }
}
```



## returns only pending absences


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences?filter[confirmation_status]=pending
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences`

#### Parameters


```json
filter: {&quot;confirmation_status&quot;=&gt;&quot;pending&quot;}
```


| Name | Description |
|:-----|:------------|
| filter  | Absences overlapping with range |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "33",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:54Z",
        "updated_at": "2023-01-30T11:22:54Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "43",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "529",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "70747ad3-d1be-47b3-bab5-d17f5851367b",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1,
    "pending": 1,
    "confirmed": 0,
    "rejected": 0,
    "total_days": 1.0,
    "total_hours": 0.0
  }
}
```



## returns only confirmed absences


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences?filter[confirmation_status]=confirmed
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences`

#### Parameters


```json
filter: {&quot;confirmation_status&quot;=&gt;&quot;confirmed&quot;}
```


| Name | Description |
|:-----|:------------|
| filter  | Absences overlapping with range |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "34",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "confirmed",
        "confirmed": true,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:54Z",
        "updated_at": "2023-01-30T11:22:54Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "43",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "530",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "81c74c48-9a6f-4b43-91c0-1378e386a57e",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1,
    "pending": 0,
    "confirmed": 1,
    "rejected": 0,
    "total_days": 1.0,
    "total_hours": 0.0
  }
}
```



## returns only rejected absences


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences?filter[confirmation_status]=rejected
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences`

#### Parameters


```json
filter: {&quot;confirmation_status&quot;=&gt;&quot;rejected&quot;}
```


| Name | Description |
|:-----|:------------|
| filter  | Absences overlapping with range |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "35",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "rejected",
        "confirmed": false,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:54Z",
        "updated_at": "2023-01-30T11:22:54Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "43",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "531",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "0771dccf-001f-42ef-b07c-d1bd51b8dca8",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1,
    "pending": 0,
    "confirmed": 0,
    "rejected": 1,
    "total_days": 1.0,
    "total_hours": 0.0
  }
}
```



## Absences overlapping with date range


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences?filter[overlapping_with_range]=2023-01-30_2023-02-05
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences`

#### Parameters


```json
filter: {&quot;overlapping_with_range&quot;=&gt;&quot;2023-01-30_2023-02-05&quot;}
```


| Name | Description |
|:-----|:------------|
| filter  | Absences overlapping with range |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 3
200 OK
```


```json
{
  "data": [
    {
      "id": "36",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 5.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-02-04T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:55Z",
        "updated_at": "2023-01-30T11:22:55Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "43",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "532",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "37",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 6.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-02-06T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:55Z",
        "updated_at": "2023-01-30T11:22:55Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "39",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "533",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "38",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 5.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-27T23:00:00Z",
        "ends_at": "2023-02-04T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:55Z",
        "updated_at": "2023-01-30T11:22:55Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "41",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "534",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "c4061441-ac25-4c67-8779-8a11609e152e",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 3,
    "pending": 3,
    "confirmed": 0,
    "rejected": 0,
    "total_days": 16.0,
    "total_hours": 0.0
  }
}
```



## All absences after and during starting date


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences?filter[overlapping_with_range]=2023-01-30
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences`

#### Parameters


```json
filter: {&quot;overlapping_with_range&quot;=&gt;&quot;2023-01-30&quot;}
```


| Name | Description |
|:-----|:------------|
| filter  | Absences overlapping with range |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 4
200 OK
```


```json
{
  "data": [
    {
      "id": "36",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 5.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-02-04T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:55Z",
        "updated_at": "2023-01-30T11:22:55Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "43",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "532",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "37",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 6.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-02-06T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:55Z",
        "updated_at": "2023-01-30T11:22:55Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "39",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "533",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "38",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 5.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-27T23:00:00Z",
        "ends_at": "2023-02-04T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:55Z",
        "updated_at": "2023-01-30T11:22:55Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "41",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "534",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "41",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 2.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-02-05T23:00:00Z",
        "ends_at": "2023-02-07T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:55Z",
        "updated_at": "2023-01-30T11:22:55Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "41",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "537",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "32736b66-6131-4f78-af38-1c3649de7453",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 4,
    "pending": 4,
    "confirmed": 0,
    "rejected": 0,
    "total_days": 18.0,
    "total_hours": 0.0
  }
}
```

# Absences/Attachments

## List of attachments


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences/4/attachments
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences/:absence_id/attachments`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "4",
      "type": "attachment",
      "attributes": {
        "author": "Enrico Schultz",
        "created_at": "2023-01-30T12:21:46+01:00",
        "updated_at": "2023-01-30T12:21:46+01:00",
        "file_name": "example.png",
        "file_content_type": "image/png",
        "file_url": "/system/note_attachments/files/000/000/004/original/example.png"
      }
    }
  ],
  "meta": {
    "request_id": "e0737f12-0ecb-4b10-a781-f9f2e4e87b46",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```

# Absences/Notes

## User create note for absence


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/absences/5/notes
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/absences/:absence_id/notes`

#### Parameters


```json
{"data":{"attributes":{"content":"Create note test"},"type":"note"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| absence_id *required* | Absence ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "333",
    "type": "user_note",
    "attributes": {
      "permissions": null,
      "content": "Create note test",
      "author": "Freiherr Sami Grams",
      "author_role": "admin",
      "type": "UserNote",
      "created_at": "2023-01-30T12:21:49+01:00"
    },
    "relationships": {
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "95191a33-42be-4451-8392-67c26eaf3ff9",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Create note with wrong body


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/absences/6/notes
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/absences/:absence_id/notes`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| absence_id *required* | Absence ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "bad_request",
      "source": {
        "pointer": "base"
      },
      "title": "Param 'note' is missing or empty."
    }
  ]
}
```



## Unauthorized to create note for other employee absence


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/absences/7/notes
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/absences/:absence_id/notes`

#### Parameters


```json
{"data":{"attributes":{"content":"Create note test"},"type":"note"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| absence_id *required* | Absence ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## employee delete his own note of absence


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/absences/8/notes/338
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/absences/:absence_id/notes/:user_note_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| absence_id *required* | Absence ID |
| user_note_id *required* | User Note ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "338",
    "type": "user_note",
    "attributes": {
      "permissions": null,
      "content": "This is a note",
      "author": "Enrico Schultz",
      "author_role": "employee",
      "type": "UserNote",
      "created_at": "2023-01-30T16:21:49+01:00"
    },
    "relationships": {
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "be4fb631-f697-425e-970e-dd56b1dec116",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## admin can delete employee note of absence


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/absences/9/notes/341
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/absences/:absence_id/notes/:user_note_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| absence_id *required* | Absence ID |
| user_note_id *required* | User Note ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "341",
    "type": "user_note",
    "attributes": {
      "permissions": null,
      "content": "This is a note",
      "author": "Enrico Schultz",
      "author_role": "employee",
      "type": "UserNote",
      "created_at": "2023-01-30T16:21:50+01:00"
    },
    "relationships": {
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "fbd7111e-9fe4-487c-b57b-b9bf81f4360a",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Unauthorized employee to delete note of other employee absence


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/absences/10/notes/344
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/absences/:absence_id/notes/:user_note_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| absence_id *required* | Absence ID |
| user_note_id *required* | User Note ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Show a absence note list


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences/11/notes
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences/:absence_id/notes`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |
| permissions  | User Permissions |
| filter  | Type filter |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "345",
      "type": "note",
      "attributes": {
        "permissions": null,
        "content": "Absence has been created.",
        "type": "SystemNote",
        "created_at": "2023-01-30T12:21:50+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "346",
      "type": "note",
      "attributes": {
        "permissions": null,
        "content": "This is a note",
        "author": "Freiherr Sami Grams",
        "author_role": "admin",
        "type": "UserNote",
        "created_at": "2023-01-30T16:21:50+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "4dce75a7-85d8-4d91-b5d9-d02ae8323920",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2
  }
}
```



## With Permissions


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences/12/notes?permissions=read%2C+update
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences/:absence_id/notes`

#### Parameters


```json
permissions: read, update
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |
| permissions  | User Permissions |
| filter  | Type filter |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "347",
      "type": "note",
      "attributes": {
        "permissions": {
          "read": true,
          "update": true
        },
        "content": "Absence has been created.",
        "type": "SystemNote",
        "created_at": "2023-01-30T12:21:50+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "348",
      "type": "note",
      "attributes": {
        "permissions": {
          "read": true,
          "update": true
        },
        "content": "This is a note",
        "author": "Freiherr Sami Grams",
        "author_role": "admin",
        "type": "UserNote",
        "created_at": "2023-01-30T16:21:50+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "cc2381fc-bd53-47a3-89e0-43f1daba6cdc",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2
  }
}
```



## Shows only system notes


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences/13/notes?filter[type]=eq%3ASystemNote
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences/:absence_id/notes`

#### Parameters


```json
filter: {&quot;type&quot;=&gt;&quot;eq:SystemNote&quot;}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |
| permissions  | User Permissions |
| filter  | Type filter |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "349",
      "type": "note",
      "attributes": {
        "permissions": null,
        "content": "Absence has been created.",
        "type": "SystemNote",
        "created_at": "2023-01-30T12:21:51+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "37709cac-e4fc-4e9d-b1c6-6b84c31918cc",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Hides system notes


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences/14/notes?filter[type]=%21eq%3ASystemNote
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences/:absence_id/notes`

#### Parameters


```json
filter: {&quot;type&quot;=&gt;&quot;!eq:SystemNote&quot;}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |
| permissions  | User Permissions |
| filter  | Type filter |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "352",
      "type": "note",
      "attributes": {
        "permissions": null,
        "content": "This is a note",
        "author": "Freiherr Sami Grams",
        "author_role": "admin",
        "type": "UserNote",
        "created_at": "2023-01-30T16:21:51+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "f1cef12d-2a0f-4ed3-ba7b-d937a3c10ca0",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## No system notes are returned when the account does not have the module &#39;show_system_notes&#39;


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences/15/notes
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences/:absence_id/notes`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |
| permissions  | User Permissions |
| filter  | Type filter |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "354",
      "type": "note",
      "attributes": {
        "permissions": null,
        "content": "This is a note",
        "author": "Freiherr Sami Grams",
        "author_role": "admin",
        "type": "UserNote",
        "created_at": "2023-01-30T16:21:51+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "3eb0cbad-148c-4f91-b820-ab33d7a58fde",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Unauthorized to see other employee absence notes


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences/16/notes
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences/:absence_id/notes`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |
| permissions  | User Permissions |
| filter  | Type filter |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## User update note for absence


### Request

#### Endpoint

```plaintext
PUT /api/v3/workspaces/1028/absences/17/notes/358
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PUT /api/v3/workspaces/:workspace_id/absences/:absence_id/notes/:user_note_id`

#### Parameters


```json
{"data":{"attributes":{"content":"Update note test"},"type":"note"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| absence_id *required* | Absence ID |
| user_note_id *required* | User Note ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "358",
    "type": "user_note",
    "attributes": {
      "permissions": null,
      "content": "Update note test",
      "author": "Enrico Schultz",
      "author_role": "employee",
      "type": "UserNote",
      "created_at": "2023-01-30T16:21:52+01:00"
    },
    "relationships": {
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "9f3f2605-b04a-43ff-986f-9aa96a9d9d62",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## update note with wrong body


### Request

#### Endpoint

```plaintext
PUT /api/v3/workspaces/1028/absences/18/notes/361
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PUT /api/v3/workspaces/:workspace_id/absences/:absence_id/notes/:user_note_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| absence_id *required* | Absence ID |
| user_note_id *required* | User Note ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "bad_request",
      "source": {
        "pointer": "base"
      },
      "title": "Param 'note' is missing or empty."
    }
  ]
}
```



## Unauthorized account admin to update note for employee absence


### Request

#### Endpoint

```plaintext
PUT /api/v3/workspaces/1028/absences/19/notes/363
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PUT /api/v3/workspaces/:workspace_id/absences/:absence_id/notes/:user_note_id`

#### Parameters


```json
{"data":{"attributes":{"content":"Update note test"},"type":"note"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| absence_id *required* | Absence ID |
| user_note_id *required* | User Note ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```

# Accounts

Accounts resource

## Show account


### Request

#### Endpoint

```plaintext
GET /api/v3/accounts/1026
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/accounts/:account_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| account_id *required* | Account ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1026",
    "type": "account",
    "attributes": {
      "phone": "+492204948890",
      "country": null,
      "locale": "de",
      "account_name": "Wallstab-Lutje",
      "created_at": "2023-01-30T11:21:41Z",
      "updated_at": "2023-01-30T11:21:41Z"
    }
  },
  "meta": {
    "request_id": "2d818e85-d2a2-4c79-81f4-4080cc07ea56",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Update a account


### Request

#### Endpoint

```plaintext
PATCH /api/v3/accounts/1026
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/accounts/:account_id`

#### Parameters


```json
{"data":{"type":"account","attributes":{"name":"New Name"}}}
```


| Name | Description |
|:-----|:------------|
| account_id *required* | Account ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1026",
    "type": "account",
    "attributes": {
      "phone": "+492204948890",
      "country": null,
      "locale": "de",
      "account_name": "New Name",
      "created_at": "2023-01-30T11:21:41Z",
      "updated_at": "2023-01-30T11:22:00Z"
    }
  },
  "meta": {
    "request_id": "b4296a5c-6631-411a-ac68-375316c3eb11",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```

# Accounts/DataProfiles

Account Data Profiles

## Returns active data profiles


### Request

#### Endpoint

```plaintext
GET /api/v3/accounts/1031/workspaces/1029/data_profiles
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/accounts/:account_id/workspaces/:workspace_id/data_profiles`

#### Parameters



| Name | Description |
|:-----|:------------|
| account_id *required* | Account Id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "4",
      "type": "data_profile",
      "attributes": {
        "permissions": null,
        "title": "data profile 1",
        "position": 0,
        "user_checkin": null,
        "enabled": true
      },
      "relationships": {
        "custom_fields": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "5",
      "type": "data_profile",
      "attributes": {
        "permissions": null,
        "title": "data profile 2",
        "position": 0,
        "user_checkin": null,
        "enabled": true
      },
      "relationships": {
        "custom_fields": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "da1161d6-4e08-4068-bc23-a239461c745b",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2
  }
}
```



## Returns active profiles with employee permissions


### Request

#### Endpoint

```plaintext
GET /api/v3/accounts/1034/workspaces/1031/data_profiles
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/accounts/:account_id/workspaces/:workspace_id/data_profiles`

#### Parameters



| Name | Description |
|:-----|:------------|
| account_id *required* | Account Id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "7",
      "type": "data_profile",
      "attributes": {
        "permissions": null,
        "title": "data profile 2",
        "position": 0,
        "user_checkin": null,
        "enabled": true
      },
      "relationships": {
        "custom_fields": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "b9072e35-946f-4e0f-8f3f-fcc9b8b15d66",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## There is no active profile


### Request

#### Endpoint

```plaintext
GET /api/v3/accounts/1036/workspaces/1032/data_profiles
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/accounts/:account_id/workspaces/:workspace_id/data_profiles`

#### Parameters



| Name | Description |
|:-----|:------------|
| account_id *required* | Account Id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 0
200 OK
```


```json
{
  "data": [

  ],
  "meta": {
    "request_id": "27679a8f-caf2-489e-a042-3aee301fd572",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 0
  }
}
```



## Unauthorized when trying to fetch other user data profiles 


### Request

#### Endpoint

```plaintext
GET /api/v3/accounts/1039/workspaces/1034/data_profiles
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/accounts/:account_id/workspaces/:workspace_id/data_profiles`

#### Parameters



| Name | Description |
|:-----|:------------|
| account_id *required* | Account Id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```

# Accounts/Users

Get users in an account. Requires accounts module*

## returns 200 status with list of users


### Request

#### Endpoint

```plaintext
GET /api/v3/accounts/1026/users?include=account%2C+workspaces%2C+absence_types
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/accounts/:account_id/users`

#### Parameters


```json
include: account, workspaces, absence_types
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |
| account_id *required* | Account ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 5
200 OK
```


```json
{
  "data": [
    {
      "id": "39",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "marcel_littel@hand.net",
        "username": "Freiherr Sami Grams",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 1,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "86re",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [

          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [
            {
              "id": "1",
              "type": "tag"
            }
          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "40",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2022-12-30",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 8,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "17hs",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "41",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "wanda@aufderhar.org",
        "username": "Fr. Ruben Plank",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 3,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "7pbv",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [

          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "42",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "roland@welch.com",
        "username": "Jannes Scherer",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 1,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "rhf7",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "43",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "tressa_wilkinson@bayer-spinka.com",
        "username": "Karina zu Pippig",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 4,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "ygr3",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    }
  ],
  "included": [
    {
      "id": "1026",
      "type": "account",
      "attributes": {
        "phone": "+492204948890",
        "country": null,
        "locale": "de",
        "account_name": "Wallstab-Lutje",
        "created_at": "2023-01-30T11:21:41Z",
        "updated_at": "2023-01-30T11:21:41Z"
      }
    },
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": null,
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    },
    {
      "id": "1028",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 1_759",
        "kind": "vacation"
      }
    }
  ],
  "meta": {
    "request_id": "2d148f3d-b189-43fc-a4df-61deb89b110f",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 5
  }
}
```



## returns 200 status with list of users


### Request

#### Endpoint

```plaintext
GET /api/v3/accounts/1026/users?include=account%2C+workspaces%2C+absence_types
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/accounts/:account_id/users`

#### Parameters


```json
include: account, workspaces, absence_types
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |
| account_id *required* | Account ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 5
200 OK
```


```json
{
  "data": [
    {
      "id": "39",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "marcel_littel@hand.net",
        "username": "Freiherr Sami Grams",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 1,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "86re",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 20.0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [

          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [
            {
              "id": "2",
              "type": "tag"
            }
          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "40",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2022-12-30",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 8,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "17hs",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "41",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "wanda@aufderhar.org",
        "username": "Fr. Ruben Plank",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 3,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "7pbv",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [

          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "42",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "roland@welch.com",
        "username": "Jannes Scherer",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 1,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "rhf7",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "43",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "tressa_wilkinson@bayer-spinka.com",
        "username": "Karina zu Pippig",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 4,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "ygr3",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    }
  ],
  "included": [
    {
      "id": "1026",
      "type": "account",
      "attributes": {
        "phone": "+492204948890",
        "country": null,
        "locale": "de",
        "account_name": "Wallstab-Lutje",
        "created_at": "2023-01-30T11:21:41Z",
        "updated_at": "2023-01-30T11:21:41Z"
      }
    },
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": null,
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    },
    {
      "id": "1028",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 1_759",
        "kind": "vacation"
      }
    }
  ],
  "meta": {
    "request_id": "fe705077-c5e4-407d-a3de-0f3a45c3ebb9",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 5
  }
}
```



## returns 401 status


### Request

#### Endpoint

```plaintext
GET /api/v3/accounts/1026/users?include=account%2C+workspaces%2C+absence_types
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/accounts/:account_id/users`

#### Parameters


```json
include: account, workspaces, absence_types
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |
| account_id *required* | Account ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
401 Unauthorized
```


```json
{
  "errors": [
    {
      "status": "unauthorized",
      "source": {
        "pointer": "base"
      },
      "title": "You need to sign in or sign up before continuing."
    }
  ]
}
```



## Show user


### Request

#### Endpoint

```plaintext
GET /api/v3/accounts/1026/users/40?include=account%2C+areas%2C+workspaces
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/accounts/:account_id/users/:user_id`

#### Parameters


```json
include: account, areas, workspaces
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |
| account_id *required* | Account ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "40",
    "type": "user",
    "attributes": {
      "permissions": null,
      "email": "gail.block@jones.biz",
      "username": "Enrico Schultz",
      "tablet_pin": null,
      "abbreviation": null,
      "hour_holidays": false,
      "time_zone": null,
      "initial_time_account": 0.0,
      "checkin_complete": null,
      "start_of_accounting": "2022-12-30",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 8,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": null,
      "external_id": null,
      "birthday": null,
      "identifier_pin": "17hs",
      "locale": null,
      "status": "active",
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": {
          "id": "1026",
          "type": "account"
        }
      },
      "areas": {
        "data": [
          {
            "id": "1028",
            "type": "area"
          }
        ]
      },
      "workspaces": {
        "data": [
          {
            "id": "1028",
            "type": "workspace"
          }
        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [
          {
            "id": "1028",
            "type": "absence_type"
          }
        ]
      },
      "tags": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "4addaee0-3d53-439a-b0b4-7b6da500d775",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "1026",
      "type": "account",
      "attributes": {
        "phone": "+492204948890",
        "country": null,
        "locale": "de",
        "account_name": "Wallstab-Lutje",
        "created_at": "2023-01-30T11:21:41Z",
        "updated_at": "2023-01-30T11:22:01Z"
      }
    },
    {
      "id": "1028",
      "type": "area",
      "attributes": {
        "permissions": null,
        "name": "Lorenz vom Wollmann",
        "status": "active",
        "color": "#913D88",
        "external_id": null,
        "created_at": "2023-01-30T11:21:43Z",
        "updated_at": "2023-01-30T11:21:43Z"
      },
      "relationships": {
        "users": {
          "data": [
            {
              "id": "40",
              "type": "user"
            },
            {
              "id": "42",
              "type": "user"
            },
            {
              "id": "43",
              "type": "user"
            }
          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    },
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": null,
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    }
  ]
}
```



# Accounts/Workspaces

Workspaces resource

## Create a workspace


### Request

#### Endpoint

```plaintext
POST /api/v3/accounts/1026/workspaces
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/accounts/:account_id/workspaces`

#### Parameters


```json
{"data":{"type":"workspace","attributes":{"name":"New Test Workspace","phone":"+441234567000","time_zone":"Berlin","locale":"de","external_id":"7","avatar":""}}}
```


| Name | Description |
|:-----|:------------|
| account_id *required* | Account ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1037",
    "type": "workspace",
    "attributes": {
      "permissions": null,
      "name": "New Test Workspace",
      "phone": "+441234567000",
      "time_zone": "Berlin",
      "locale": "de",
      "avatar": "/avatars/original/missing.png",
      "external_id": "7",
      "allow_employees_edit_working_session_area": true,
      "allow_employee_edit_punched_working_sessions": false,
      "allow_employees_tag_working_sessions": false,
      "checkin": null
    },
    "relationships": {
      "areas": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "d735f8ea-0cd0-46e9-8626-bcb5aba1c42f",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```

# Actions


## returns 201 status and data for the action created


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/actions`

#### Parameters


```json
{"data":{"attributes":{"action_type":"start","device_id":null,"action_time":"2023-01-30T12:23:02+01:00","user_id":40,"taggings_attributes":[{"tag_id":41}]},"type":"action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "bdca0db2-ef67-478c-a46f-3cad8a0c4d48",
    "type": "action",
    "attributes": {
      "action_type": "start",
      "working_session_id": null,
      "action_time": "2023-01-30T11:23:02Z",
      "created_at": "2023-01-30T11:23:02Z",
      "updated_at": "2023-01-30T11:23:02Z"
    },
    "relationships": {
      "user": {
        "data": {
          "id": "40",
          "type": "user"
        }
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "fb49ee56-1478-4c12-9171-a50a10768ef5",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Index of actions


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/actions
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/actions`

#### Parameters



| Name | Description |
|:-----|:------------|
| filter  | Filter param |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "80ae9e90-800d-4150-b742-bec23300c771",
      "type": "action",
      "attributes": {
        "action_type": "start",
        "working_session_id": null,
        "action_time": "2023-01-30T11:23:02Z",
        "created_at": "2023-01-30T11:23:02Z",
        "updated_at": "2023-01-30T11:23:02Z"
      },
      "relationships": {
        "user": {
          "data": {
            "id": "39",
            "type": "user"
          }
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    }
  ],
  "meta": {
    "request_id": "a4e9fec9-d434-491c-b0a7-509be9bbc3aa",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Show action


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/actions/47aa04af-df99-41c6-8d2d-36d1978746b7
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/actions/:action_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| action_id *required* | Action ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "47aa04af-df99-41c6-8d2d-36d1978746b7",
    "type": "action",
    "attributes": {
      "action_type": "start",
      "working_session_id": null,
      "action_time": "2023-01-30T11:23:03Z",
      "created_at": "2023-01-30T11:23:03Z",
      "updated_at": "2023-01-30T11:23:03Z"
    },
    "relationships": {
      "user": {
        "data": {
          "id": "39",
          "type": "user"
        }
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "4ceaa1f5-8dd6-482f-b825-b22c073ef09a",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```


# Actions/Taggings


## attaches taggings to an action


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/actions/c505a003-c5ef-4ffe-b2fc-67032458d0bb/taggings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/actions/:action_id/taggings`

#### Parameters


```json
{"data":{"attributes":{"tag_id":42},"type":"tagging"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| action_id *required* | Action ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "c985b0fa-fae5-463b-bf9b-3edf78404123",
    "type": "tagging",
    "attributes": {
      "taggable_type": "WorkingSessionAction",
      "taggable_id": "7f5b60b6-facd-4f76-bc31-306b23cb21fa"
    },
    "relationships": {
      "tag": {
        "data": {
          "id": "42",
          "type": "tag"
        }
      }
    }
  },
  "meta": {
    "request_id": "fa8420ee-1088-410d-9dc1-4ebe12d573b1",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## does not attach taggings to an action


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/actions/5e29bb3b-7bbf-4e77-ab0f-809993792cfd/taggings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/actions/:action_id/taggings`

#### Parameters


```json
{"data":{"attributes":{"tag_id":43},"type":"tagging"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| action_id *required* | Action ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Cannot attach tags to completed working session"
    }
  ]
}
```

# IndustryExample

## returns newly created company


### Request

#### Endpoint

```plaintext
GET /api/v3/industry_examples
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/industry_examples`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "choose_your_industry",
      "type": "industry_example",
      "attributes": {
        "name": "Choose industry",
        "label": "[EN] Plain"
      }
    }
  ],
  "meta": {
    "request_id": "9e34da08-dd67-44e3-815c-fdfc50d25dc4",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```

## returns all companies


### Request

#### Endpoint

```plaintext
GET /api/v3/industry_examples
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/industry_examples`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "choose_your_industry",
      "type": "industry_example",
      "attributes": {
        "name": "Choose industry",
        "label": "[EN] Plain"
      }
    },
    {
      "id": "1051",
      "type": "industry_example",
      "attributes": {
        "name": "[EN]",
        "label": ""
      }
    }
  ],
  "meta": {
    "request_id": "8d79aa8c-44f7-4b4e-b3ae-15cf55bb5150",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2
  }
}
```

# Public/Workspaces/User

## returns invited user


### Request

#### Endpoint

```plaintext
GET /api/v3/public/user-details?invite_token=5ad5b36a-f796-4402-b6a5-8ca335fca6ff
Content-Type: application/vnd.api+json
Api-Key: 46e67c525617663b392a53c0e94ba79e62db62a851fb175ae87756d4e73c9718
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/public/user-details`

#### Parameters


```json
invite_token: 5ad5b36a-f796-4402-b6a5-8ca335fca6ff
```


| Name | Description |
|:-----|:------------|
| invite_token *required* | Invitation Token |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "40",
    "type": "invited_user",
    "attributes": {
      "email": "gail.block@jones.biz",
      "username": "Enrico Schultz"
    }
  },
  "meta": {
    "request_id": "71b70942-a70a-440e-97ff-0f3d2602d89d",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



# Public/Workspaces/Users



## Returns email invitation


### Request

#### Endpoint

```plaintext
GET /api/v3/public/users/invitations/6d33b893-c3a0-414c-8dda-a9d0bb685849
Content-Type: application/vnd.api+json
Api-Key: 46e67c525617663b392a53c0e94ba79e62db62a851fb175ae87756d4e73c9718
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/public/users/invitations/:invite_token`

#### Parameters



| Name | Description |
|:-----|:------------|
| invite_token *required* | Invitation Token |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "6d33b893-c3a0-414c-8dda-a9d0bb685849",
    "type": "user_invitation",
    "attributes": {
      "user_checkin": true,
      "welcome_message": "Welcome to your Workspace!"
    }
  },
  "meta": {
    "request_id": "98271351-15af-47f0-8520-8b45960f5c56",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Returns generic invitation


### Request

#### Endpoint

```plaintext
GET /api/v3/public/users/invitations/2929e89c-c1e1-4bb9-a706-1771b40675d8
Content-Type: application/vnd.api+json
Api-Key: 46e67c525617663b392a53c0e94ba79e62db62a851fb175ae87756d4e73c9718
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/public/users/invitations/:invite_token`

#### Parameters



| Name | Description |
|:-----|:------------|
| invite_token *required* | Invitation Token |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "2929e89c-c1e1-4bb9-a706-1771b40675d8",
    "type": "user_invitation",
    "attributes": {
      "user_checkin": true,
      "welcome_message": "Welcome to your Workspace!"
    }
  },
  "meta": {
    "request_id": "d9092179-ec5e-4a08-979c-d273458cc8f2",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```

## returns pending users


### Request

#### Endpoint

```plaintext
GET /api/v3/public/users/invited?invite_token=14b18371-df01-4fb0-97e8-d4c643e78177
Content-Type: application/vnd.api+json
Api-Key: 46e67c525617663b392a53c0e94ba79e62db62a851fb175ae87756d4e73c9718
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/public/users/invited`

#### Parameters


```json
invite_token: 14b18371-df01-4fb0-97e8-d4c643e78177
```


| Name | Description |
|:-----|:------------|
| filter *required* | filter param |
| invite_token *required* | Invitation Token |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "40",
      "type": "invited_user",
      "attributes": {
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz"
      }
    }
  ],
  "meta": {
    "request_id": "f30c799a-9770-42f5-a8d1-89b752e771af",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```

## returns users without email


### Request

#### Endpoint

```plaintext
GET /api/v3/public/users/invited?filter[email]=present%3Afalse&amp;invite_token=5efa0b17-8397-41ec-af8d-7160f57ff3e6
Content-Type: application/vnd.api+json
Api-Key: 46e67c525617663b392a53c0e94ba79e62db62a851fb175ae87756d4e73c9718
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/public/users/invited`

#### Parameters


```json
filter: {&quot;email&quot;=&gt;&quot;present:false&quot;}
invite_token: 5efa0b17-8397-41ec-af8d-7160f57ff3e6
```


| Name | Description |
|:-----|:------------|
| filter *required* | filter param |
| invite_token *required* | Invitation Token |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "40",
      "type": "invited_user",
      "attributes": {
        "email": "",
        "username": "Enrico Schultz"
      }
    }
  ],
  "meta": {
    "request_id": "b7326bc2-9c76-4284-a412-d5fe5847ce20",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```

## Create User


### Request

#### Endpoint

```plaintext
POST /api/v3/public/join-workspace
Content-Type: application/vnd.api+json
Api-Key: 46e67c525617663b392a53c0e94ba79e62db62a851fb175ae87756d4e73c9718
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/public/join-workspace`

#### Parameters


```json
{"data":{"attributes":{"username":"Fabian Ostendarp","email":"chance@langosh.net","password":"jobpzquvsr","token":"140a8508-9515-4bfe-9963-112c8acd5184"},"type":"user"}}
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1dWlkIjoiMzBmYTQ5NTctYWJmZS00OTY1LWI3ZDktYjAwZWI5Njc0OWVkIiwic3ViIjoiNzQiLCJzY3AiOiJ1c2VyIiwiYXVkIjpudWxsLCJpYXQiOjE2NzUwNzc3MzEsImV4cCI6MzI1MjkyNTMzMSwianRpIjoiYzY3ODdiNjgtODY1Mi00MGI0LThiMzAtNmY4YjBhNjg5MDI4In0.QNRuHSQd3Jb5Ka7ra5l4dPYH5isI67nHtZHD0MikP3A
200 OK
```


```json
{
  "data": {
    "id": "405026b6-1c2a-4965-bc20-c493bed40645",
    "type": "token",
    "attributes": {
      "access_token": "eyJhbGciOiJIUzI1NiJ9.eyJ1dWlkIjoiMzBmYTQ5NTctYWJmZS00OTY1LWI3ZDktYjAwZWI5Njc0OWVkIiwic3ViIjoiNzQiLCJzY3AiOiJ1c2VyIiwiYXVkIjpudWxsLCJpYXQiOjE2NzUwNzc3MzEsImV4cCI6MzI1MjkyNTMzMSwianRpIjoiYzY3ODdiNjgtODY1Mi00MGI0LThiMzAtNmY4YjBhNjg5MDI4In0.QNRuHSQd3Jb5Ka7ra5l4dPYH5isI67nHtZHD0MikP3A",
      "token_type": "Bearer",
      "expires_in": null
    }
  },
  "meta": {
    "request_id": "e0b32992-b80b-40bd-b687-2c554d0e313f",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```

# Status

## returns server status


### Request

#### Endpoint

```plaintext
GET /api/v3/status/

```

`GET /api/v3/status/`

#### Parameters


None known.


### Response

```plaintext

204 No Content
```
# TimeTracking

## It confirms the time tracking and returns 200


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"confirm","ids":[61]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Batch action process is running"
  }
}
```



## it confirms all time-trackings


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"confirm","ids":[11],"all":true},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Batch action process is running"
  }
}
```



## It deletes the time tracking and returns 200


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"destroy","ids":[67]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Batch action process is running"
  }
}
```



## Adding tags to time trackings


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"tag","ids":[70],"tag_ids":[45]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Batch action process is running"
  }
}
```



## Overriding tags for multiple time trackings


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"tag","ids":[73],"tag_ids":[47],"override_tags":true},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Batch action process is running"
  }
}
```



## It Assigns followers to time tracking and returns 200


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"follower","ids":[76],"follower_ids":[115,40]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Batch action process is running"
  }
}
```



## It removes followers to time tracking and returns 200


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"follower","ids":[79],"follower_ids":[]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Batch action process is running"
  }
}
```



## It Assigns note for multiple time tracking and returns 200


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"note","ids":[82],"note":{"content":"this is an assigned note"}},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Batch action process is running"
  }
}
```



## It returns an error when batch action params are missing


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"tag","ids":[85]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Params are missing"
    }
  ]
}
```



## It returns an error when sending invalid action


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"invalid","ids":[88]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Invalid batch action"
    }
  ]
}
```



## It return an authorization error when signed in as an employee


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/batch_actions`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Confirm a time tracking


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/time_trackings/108/confirm
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/confirm`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "108",
    "type": "time_tracking",
    "attributes": {
      "permissions": null,
      "assignment_id": null,
      "confirmed": true,
      "last_update_by": null,
      "break_duration": null,
      "default_break_duration": 0,
      "created_by": "browser-stamps",
      "force_custom_break_duration": false,
      "external_id": null,
      "status": "active",
      "start_signature_id": null,
      "end_signature_id": null,
      "current_status": "finished",
      "starts_at": "2023-01-30T09:23:10Z",
      "ends_at": "2023-01-30T11:23:10Z",
      "actual_starts_at": "2023-01-30T09:23:10Z",
      "actual_ends_at": "2023-01-30T11:23:10Z",
      "created_at": "2023-01-30T11:23:10Z",
      "updated_at": "2023-01-30T11:23:10Z",
      "gross_time": 2.0,
      "net_time": 2.0,
      "break_time": 0.0,
      "system_notes_count": 2,
      "user_notes_count": 0,
      "signatures_count": 0,
      "attachments_count": 0
    },
    "relationships": {
      "attachments": {
        "data": [

        ]
      },
      "breaks": {
        "data": [

        ]
      },
      "notes": {
        "data": [
          {
            "id": "648",
            "type": "note"
          },
          {
            "id": "649",
            "type": "note"
          }
        ]
      },
      "signatures": {
        "data": [

        ]
      },
      "tags": {
        "data": [

        ]
      },
      "followers": {
        "data": [

        ]
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "last_editor": {
        "data": null
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "f1744ddb-c093-4962-a16a-b9dde7b62d10",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Admin cannot confirm a running time tracking


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/time_trackings/109/confirm
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/confirm`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Employees are not allowed to confirm time trackings


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/time_trackings/110/confirm
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/confirm`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## returns 201 status and data for the time tracking created


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings`

#### Parameters


```json
{"data":{"attributes":{"assignment_id":"","break_duration":"","breaks_attributes":[{"ends_at":"2020-05-20T05:02:00+02:00","starts_at":"2020-05-20T05:01:00+02:00"}],"company_id":"","confirmed":false,"created_by":"admin","default_break_duration":1800,"end_signature_id":"","ends_at":"2020-05-20T05:06:00+02:00","external_id":"","force_custom_break_duration":false,"import_id":"","limited":false,"planned":false,"start_signature_id":"","starts_at":"2020-05-20T05:00:00+02:00"},"relationships":{"area":{"data":{"id":"1058","type":"area"}},"tags":{"data":[{"id":"48","type":"tag"}]},"user":{"data":{"id":"40","type":"user_overview"}}},"type":"time_tracking"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "111",
    "type": "time_tracking",
    "attributes": {
      "permissions": null,
      "assignment_id": null,
      "confirmed": false,
      "last_update_by": 39,
      "break_duration": 60,
      "default_break_duration": 0,
      "created_by": "admin",
      "force_custom_break_duration": false,
      "external_id": "",
      "status": "active",
      "start_signature_id": null,
      "end_signature_id": null,
      "current_status": "finished",
      "starts_at": "2020-05-20T03:00:00Z",
      "ends_at": "2020-05-20T03:06:00Z",
      "actual_starts_at": "2020-05-20T03:00:00Z",
      "actual_ends_at": "2020-05-20T03:06:00Z",
      "created_at": "2023-01-30T11:23:11Z",
      "updated_at": "2023-01-30T11:23:11Z",
      "gross_time": 0.1,
      "net_time": 0.08,
      "break_time": 0.02,
      "system_notes_count": 2,
      "user_notes_count": 0,
      "signatures_count": 0,
      "attachments_count": 0
    },
    "relationships": {
      "area": {
        "data": {
          "id": "1058",
          "type": "area"
        }
      },
      "attachments": {
        "data": [

        ]
      },
      "breaks": {
        "data": [
          {
            "id": "14",
            "type": "break"
          }
        ]
      },
      "notes": {
        "data": [
          {
            "id": "655",
            "type": "note"
          },
          {
            "id": "656",
            "type": "note"
          }
        ]
      },
      "signatures": {
        "data": [

        ]
      },
      "tags": {
        "data": [
          {
            "id": "48",
            "type": "tag"
          }
        ]
      },
      "followers": {
        "data": [

        ]
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "last_editor": {
        "data": {
          "id": "39",
          "type": "user_overview"
        }
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "cafb40c6-e447-4d28-88db-ac2a61f94401",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## returns 422 status with errors


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings`

#### Parameters


```json
{"data":{"attributes":{"assignment_id":"","break_duration":"","breaks_attributes":[{"ends_at":"2020-05-20T05:02:00+02:00","starts_at":"2020-05-20T05:01:00+02:00"}],"company_id":"","confirmed":false,"created_by":"admin","default_break_duration":1800,"end_signature_id":"","ends_at":"2020-05-20T05:06:00+02:00","external_id":"","force_custom_break_duration":false,"import_id":"","limited":false,"planned":false,"start_signature_id":"","starts_at":"2020-05-20T05:00:00+02:00"},"relationships":{"area":{"data":{"id":"","type":"area"}},"tags":{"data":[{"id":"","type":"tag"}]},"user":{"data":{"id":"99_999","type":"user"}}},"type":"time_tracking"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "user_id"
      },
      "title": "Did not find User with id '99999' within authorized Enterprise!"
    }
  ]
}
```



## returns 401 status


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings`

#### Parameters


```json
{"data":{"attributes":{"assignment_id":"","break_duration":"","breaks_attributes":[{"ends_at":"2020-05-20T05:02:00+02:00","starts_at":"2020-05-20T05:01:00+02:00"}],"company_id":"","confirmed":false,"created_by":"admin","default_break_duration":1800,"end_signature_id":"","ends_at":"2020-05-20T05:06:00+02:00","external_id":"","force_custom_break_duration":false,"import_id":"","limited":false,"planned":false,"start_signature_id":"","starts_at":"2020-05-20T05:00:00+02:00"},"relationships":{"area":{"data":{"id":"","type":"area"}},"tags":{"data":[{"id":"","type":"tag"}]},"user":{"data":{"id":"116","type":"user"}}},"type":"time_tracking"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## returns 201 status and data for the time tracking created


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings`

#### Parameters


```json
{"data":{"attributes":{"assignment_id":"","break_duration":"","breaks_attributes":[{"ends_at":"2020-05-20T05:02:00+02:00","starts_at":"2020-05-20T05:01:00+02:00"}],"company_id":"","confirmed":false,"created_by":"admin","default_break_duration":1800,"end_signature_id":"","ends_at":"2020-05-20T05:06:00+02:00","external_id":"","force_custom_break_duration":false,"import_id":"","limited":false,"planned":false,"start_signature_id":"","starts_at":"2020-05-20T05:00:00+02:00"},"relationships":{"area":{"data":{"id":"1060","type":"area"}},"tags":{"data":[{"id":"50","type":"tag"}]},"user":{"data":{"id":"40","type":"user_overview"}}},"type":"time_tracking"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "112",
    "type": "time_tracking",
    "attributes": {
      "permissions": null,
      "assignment_id": null,
      "confirmed": false,
      "last_update_by": 40,
      "break_duration": 60,
      "default_break_duration": 0,
      "created_by": "admin",
      "force_custom_break_duration": false,
      "external_id": "",
      "status": "active",
      "start_signature_id": null,
      "end_signature_id": null,
      "current_status": "finished",
      "starts_at": "2020-05-20T03:00:00Z",
      "ends_at": "2020-05-20T03:06:00Z",
      "actual_starts_at": "2020-05-20T03:00:00Z",
      "actual_ends_at": "2020-05-20T03:06:00Z",
      "created_at": "2023-01-30T11:23:12Z",
      "updated_at": "2023-01-30T11:23:12Z",
      "gross_time": 0.1,
      "net_time": 0.08,
      "break_time": 0.02,
      "system_notes_count": 2,
      "user_notes_count": 0,
      "signatures_count": 0,
      "attachments_count": 0
    },
    "relationships": {
      "area": {
        "data": {
          "id": "1060",
          "type": "area"
        }
      },
      "attachments": {
        "data": [

        ]
      },
      "breaks": {
        "data": [
          {
            "id": "15",
            "type": "break"
          }
        ]
      },
      "notes": {
        "data": [
          {
            "id": "661",
            "type": "note"
          },
          {
            "id": "662",
            "type": "note"
          }
        ]
      },
      "signatures": {
        "data": [

        ]
      },
      "tags": {
        "data": [
          {
            "id": "50",
            "type": "tag"
          }
        ]
      },
      "followers": {
        "data": [

        ]
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "last_editor": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "10628fe8-0b06-4735-9cd8-6be24e5ef617",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## returns 422 status and errors


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "bad_request",
      "source": {
        "pointer": "base"
      },
      "title": "Param 'time_tracking' is missing or empty."
    }
  ]
}
```



## returns an authorization error


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings`

#### Parameters


```json
{"data":{"attributes":{"assignment_id":"","break_duration":"","breaks_attributes":[{"ends_at":"2020-05-20T05:02:00+02:00","starts_at":"2020-05-20T05:01:00+02:00"}],"company_id":"","confirmed":false,"created_by":"admin","default_break_duration":1800,"end_signature_id":"","ends_at":"2020-05-20T05:06:00+02:00","external_id":"","force_custom_break_duration":false,"import_id":"","limited":false,"planned":false,"start_signature_id":"","starts_at":"2020-05-20T05:00:00+02:00"},"relationships":{"area":{"data":{"id":"1061","type":"area"}},"tags":{"data":[{"id":"51","type":"tag"}]},"user":{"data":{"id":"40","type":"user_overview"}}},"type":"time_tracking"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
401 Unauthorized
```


```json
{
  "errors": [
    {
      "status": "unauthorized",
      "source": {
        "pointer": "base"
      },
      "title": "You need to sign in or sign up before continuing."
    }
  ]
}
```



## Delete a time tracking


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/time_trackings/114
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "114",
    "type": "time_tracking",
    "attributes": {
      "permissions": null,
      "assignment_id": null,
      "confirmed": false,
      "last_update_by": null,
      "break_duration": null,
      "default_break_duration": 0,
      "created_by": "browser-stamps",
      "force_custom_break_duration": false,
      "external_id": null,
      "status": "active",
      "start_signature_id": null,
      "end_signature_id": null,
      "current_status": "finished",
      "starts_at": "2023-01-30T09:23:12Z",
      "ends_at": "2023-01-30T11:23:12Z",
      "actual_starts_at": "2023-01-30T09:23:12Z",
      "actual_ends_at": "2023-01-30T11:23:12Z",
      "created_at": "2023-01-30T11:23:12Z",
      "updated_at": "2023-01-30T11:23:12Z",
      "gross_time": 2.0,
      "net_time": 2.0,
      "break_time": 0.0,
      "system_notes_count": 0,
      "user_notes_count": 0,
      "signatures_count": 0,
      "attachments_count": 0
    },
    "relationships": {
      "attachments": {
        "data": [

        ]
      },
      "breaks": {
        "data": [

        ]
      },
      "notes": {
        "data": [

        ]
      },
      "signatures": {
        "data": [

        ]
      },
      "tags": {
        "data": [

        ]
      },
      "followers": {
        "data": [

        ]
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "last_editor": {
        "data": null
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "35ec51ca-8be7-4abd-9b32-cf5f1d7e9362",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Index


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| permissions  | User Permissions |
| filter  | Filter param |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "127",
      "type": "time_tracking",
      "attributes": {
        "permissions": null,
        "assignment_id": null,
        "confirmed": false,
        "last_update_by": null,
        "break_duration": null,
        "default_break_duration": 0,
        "created_by": "browser-stamps",
        "force_custom_break_duration": false,
        "external_id": null,
        "status": "active",
        "start_signature_id": null,
        "end_signature_id": null,
        "current_status": "finished",
        "starts_at": "2023-01-30T05:23:18Z",
        "ends_at": "2023-01-30T07:23:18Z",
        "actual_starts_at": "2023-01-30T05:23:18Z",
        "actual_ends_at": "2023-01-30T07:23:18Z",
        "created_at": "2023-01-30T11:23:18Z",
        "updated_at": "2023-01-30T11:23:18Z",
        "gross_time": 2.0,
        "net_time": 2.0,
        "break_time": 0.0,
        "system_notes_count": 1,
        "user_notes_count": 0,
        "signatures_count": 0,
        "attachments_count": 0
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        },
        "breaks": {
          "data": [
            {
              "id": "18",
              "type": "break"
            }
          ]
        },
        "notes": {
          "data": [
            {
              "id": "679",
              "type": "note"
            }
          ]
        },
        "signatures": {
          "data": [

          ]
        },
        "tags": {
          "data": [

          ]
        },
        "followers": {
          "data": [

          ]
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "last_editor": {
          "data": null
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    },
    {
      "id": "926e27c3-cb9c-400b-a889-f06062c97220",
      "type": "time_tracking",
      "attributes": {
        "permissions": null,
        "assignment_id": null,
        "confirmed": false,
        "last_update_by": null,
        "break_duration": null,
        "default_break_duration": 0,
        "created_by": "actions",
        "force_custom_break_duration": false,
        "external_id": null,
        "status": "active",
        "start_signature_id": null,
        "end_signature_id": null,
        "current_status": "running",
        "starts_at": "2023-01-30T10:53:18Z",
        "ends_at": null,
        "actual_starts_at": null,
        "actual_ends_at": null,
        "created_at": "2023-01-30T11:23:18Z",
        "updated_at": "2023-01-30T11:23:18Z",
        "breaks": [

        ],
        "gross_time": 0.5,
        "net_time": 0.5,
        "break_time": 0.0,
        "system_notes_count": 0,
        "user_notes_count": 0,
        "signatures_count": 0,
        "attachments_count": 0
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        },
        "breaks": {
          "data": [

          ]
        },
        "notes": {
          "data": [

          ]
        },
        "signatures": {
          "data": [

          ]
        },
        "tags": {
          "data": [

          ]
        },
        "followers": {
          "data": [

          ]
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "last_editor": {
          "data": null
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    }
  ],
  "meta": {
    "request_id": "3317bdd6-c96b-4f99-9ad2-c00139fbae86",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2,
    "total_unconfirmed": 2,
    "total_confirmed": 0,
    "total_running": 1,
    "total_gross_time": 2.5,
    "total_net_time": 2.5,
    "total_break_time": 0.0
  }
}
```



## With Permissions


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings?permissions=read%2C+update
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings`

#### Parameters


```json
permissions: read, update
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| permissions  | User Permissions |
| filter  | Filter param |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "130",
      "type": "time_tracking",
      "attributes": {
        "permissions": {
          "read": true,
          "update": true
        },
        "assignment_id": null,
        "confirmed": false,
        "last_update_by": null,
        "break_duration": null,
        "default_break_duration": 0,
        "created_by": "browser-stamps",
        "force_custom_break_duration": false,
        "external_id": null,
        "status": "active",
        "start_signature_id": null,
        "end_signature_id": null,
        "current_status": "finished",
        "starts_at": "2023-01-30T05:23:19Z",
        "ends_at": "2023-01-30T07:23:19Z",
        "actual_starts_at": "2023-01-30T05:23:19Z",
        "actual_ends_at": "2023-01-30T07:23:19Z",
        "created_at": "2023-01-30T11:23:19Z",
        "updated_at": "2023-01-30T11:23:19Z",
        "gross_time": 2.0,
        "net_time": 2.0,
        "break_time": 0.0,
        "system_notes_count": 1,
        "user_notes_count": 0,
        "signatures_count": 0,
        "attachments_count": 0
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        },
        "breaks": {
          "data": [
            {
              "id": "21",
              "type": "break"
            }
          ]
        },
        "notes": {
          "data": [
            {
              "id": "682",
              "type": "note"
            }
          ]
        },
        "signatures": {
          "data": [

          ]
        },
        "tags": {
          "data": [

          ]
        },
        "followers": {
          "data": [

          ]
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "last_editor": {
          "data": null
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    },
    {
      "id": "d6be1169-ce78-484e-8438-b00d2cd076bf",
      "type": "time_tracking",
      "attributes": {
        "permissions": {
          "read": true,
          "update": true
        },
        "assignment_id": null,
        "confirmed": false,
        "last_update_by": null,
        "break_duration": null,
        "default_break_duration": 0,
        "created_by": "actions",
        "force_custom_break_duration": false,
        "external_id": null,
        "status": "active",
        "start_signature_id": null,
        "end_signature_id": null,
        "current_status": "running",
        "starts_at": "2023-01-30T10:53:19Z",
        "ends_at": null,
        "actual_starts_at": null,
        "actual_ends_at": null,
        "created_at": "2023-01-30T11:23:19Z",
        "updated_at": "2023-01-30T11:23:19Z",
        "breaks": [

        ],
        "gross_time": 0.5,
        "net_time": 0.5,
        "break_time": 0.0,
        "system_notes_count": 0,
        "user_notes_count": 0,
        "signatures_count": 0,
        "attachments_count": 0
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        },
        "breaks": {
          "data": [

          ]
        },
        "notes": {
          "data": [

          ]
        },
        "signatures": {
          "data": [

          ]
        },
        "tags": {
          "data": [

          ]
        },
        "followers": {
          "data": [

          ]
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "last_editor": {
          "data": null
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    }
  ],
  "meta": {
    "request_id": "89f88848-c926-4561-ae20-e928852090ac",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2,
    "total_unconfirmed": 2,
    "total_confirmed": 0,
    "total_running": 1,
    "total_gross_time": 2.5,
    "total_net_time": 2.5,
    "total_break_time": 0.0
  }
}
```



## Show time tracking


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/134?include=workspace%2Cuser%2Carea%2Ctags%2Cbreaks%2Cfollowers
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id`

#### Parameters


```json
include: workspace,user,area,tags,breaks,followers
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time Tracking ID |
| permissions  | User Permissions |
| include  | Included relationships |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "134",
    "type": "time_tracking",
    "attributes": {
      "permissions": null,
      "assignment_id": null,
      "confirmed": false,
      "last_update_by": null,
      "break_duration": null,
      "default_break_duration": 0,
      "created_by": "browser-stamps",
      "force_custom_break_duration": false,
      "external_id": null,
      "status": "active",
      "start_signature_id": null,
      "end_signature_id": null,
      "current_status": "finished",
      "starts_at": "2023-01-30T09:23:20Z",
      "ends_at": "2023-01-30T11:23:20Z",
      "actual_starts_at": "2023-01-30T09:23:20Z",
      "actual_ends_at": "2023-01-30T11:23:20Z",
      "created_at": "2023-01-30T11:23:20Z",
      "updated_at": "2023-01-30T11:23:20Z",
      "gross_time": 2.0,
      "net_time": 2.0,
      "break_time": 0.0,
      "system_notes_count": 1,
      "user_notes_count": 0,
      "signatures_count": 0,
      "attachments_count": 0
    },
    "relationships": {
      "area": {
        "data": {
          "id": "1062",
          "type": "area"
        }
      },
      "attachments": {
        "data": [

        ]
      },
      "breaks": {
        "data": [

        ]
      },
      "notes": {
        "data": [
          {
            "id": "687",
            "type": "note"
          }
        ]
      },
      "signatures": {
        "data": [

        ]
      },
      "tags": {
        "data": [

        ]
      },
      "followers": {
        "data": [

        ]
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "last_editor": {
        "data": null
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "0b4adf97-5c49-4080-a70b-cf1704185744",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": null,
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    },
    {
      "id": "40",
      "type": "user_overview",
      "attributes": {
        "permissions": null,
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz",
        "abbreviation": null,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "status": "active"
      }
    },
    {
      "id": "1062",
      "type": "area",
      "attributes": {
        "permissions": null,
        "name": "Wilbur Hagenes",
        "status": "active",
        "color": "#3A539B",
        "external_id": null,
        "created_at": "2023-01-30T11:23:20Z",
        "updated_at": "2023-01-30T11:23:20Z"
      },
      "relationships": {
        "users": {
          "data": [

          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1092",
            "type": "workspace"
          }
        }
      }
    }
  ]
}
```



## Show time tracking with a pause


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/135?include=workspace%2Cuser%2Carea%2Ctags%2Cbreaks%2Cfollowers
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id`

#### Parameters


```json
include: workspace,user,area,tags,breaks,followers
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time Tracking ID |
| permissions  | User Permissions |
| include  | Included relationships |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "135",
    "type": "time_tracking",
    "attributes": {
      "permissions": null,
      "assignment_id": null,
      "confirmed": false,
      "last_update_by": null,
      "break_duration": null,
      "default_break_duration": 0,
      "created_by": "browser-stamps",
      "force_custom_break_duration": false,
      "external_id": null,
      "status": "active",
      "start_signature_id": null,
      "end_signature_id": null,
      "current_status": "finished",
      "starts_at": "2023-01-30T09:23:20Z",
      "ends_at": "2023-01-30T11:23:20Z",
      "actual_starts_at": "2023-01-30T09:23:20Z",
      "actual_ends_at": "2023-01-30T11:23:20Z",
      "created_at": "2023-01-30T11:23:20Z",
      "updated_at": "2023-01-30T11:23:20Z",
      "gross_time": 2.0,
      "net_time": 2.0,
      "break_time": 0.0,
      "system_notes_count": 1,
      "user_notes_count": 0,
      "signatures_count": 0,
      "attachments_count": 0
    },
    "relationships": {
      "area": {
        "data": {
          "id": "1063",
          "type": "area"
        }
      },
      "attachments": {
        "data": [

        ]
      },
      "breaks": {
        "data": [
          {
            "id": "25",
            "type": "break"
          }
        ]
      },
      "notes": {
        "data": [
          {
            "id": "689",
            "type": "note"
          }
        ]
      },
      "signatures": {
        "data": [

        ]
      },
      "tags": {
        "data": [

        ]
      },
      "followers": {
        "data": [

        ]
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "last_editor": {
        "data": null
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "31de0a2e-6c27-4248-8428-40d3b7a3f6fd",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": null,
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    },
    {
      "id": "40",
      "type": "user_overview",
      "attributes": {
        "permissions": null,
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz",
        "abbreviation": null,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "status": "active"
      }
    },
    {
      "id": "1063",
      "type": "area",
      "attributes": {
        "permissions": null,
        "name": "Msgr. Phillip Erdman",
        "status": "active",
        "color": "#e67e22",
        "external_id": null,
        "created_at": "2023-01-30T11:23:20Z",
        "updated_at": "2023-01-30T11:23:20Z"
      },
      "relationships": {
        "users": {
          "data": [

          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1093",
            "type": "workspace"
          }
        }
      }
    },
    {
      "id": "25",
      "type": "break",
      "attributes": {
        "starts_at": "2023-01-30T11:23:20+01:00",
        "ends_at": "2023-01-30T11:53:20+01:00",
        "created_at": "2023-01-30T12:23:20+01:00",
        "updated_at": "2023-01-30T12:23:20+01:00",
        "start_signature_id": null,
        "end_signature_id": null,
        "created_by": "employee"
      },
      "relationships": {
        "time_tracking": {
          "data": {
            "id": "135",
            "type": "time_tracking"
          }
        }
      }
    }
  ]
}
```



## With Permissions


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/136?include=workspace%2Cuser%2Carea%2Ctags%2Cbreaks%2Cfollowers&amp;permissions=read%2C+update
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id`

#### Parameters


```json
include: workspace,user,area,tags,breaks,followers
permissions: read, update
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time Tracking ID |
| permissions  | User Permissions |
| include  | Included relationships |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "136",
    "type": "time_tracking",
    "attributes": {
      "permissions": {
        "read": true,
        "update": true
      },
      "assignment_id": null,
      "confirmed": false,
      "last_update_by": null,
      "break_duration": null,
      "default_break_duration": 0,
      "created_by": "browser-stamps",
      "force_custom_break_duration": false,
      "external_id": null,
      "status": "active",
      "start_signature_id": null,
      "end_signature_id": null,
      "current_status": "finished",
      "starts_at": "2023-01-30T09:23:20Z",
      "ends_at": "2023-01-30T11:23:20Z",
      "actual_starts_at": "2023-01-30T09:23:20Z",
      "actual_ends_at": "2023-01-30T11:23:20Z",
      "created_at": "2023-01-30T11:23:20Z",
      "updated_at": "2023-01-30T11:23:20Z",
      "gross_time": 2.0,
      "net_time": 2.0,
      "break_time": 0.0,
      "system_notes_count": 1,
      "user_notes_count": 0,
      "signatures_count": 0,
      "attachments_count": 0
    },
    "relationships": {
      "area": {
        "data": {
          "id": "1064",
          "type": "area"
        }
      },
      "attachments": {
        "data": [

        ]
      },
      "breaks": {
        "data": [

        ]
      },
      "notes": {
        "data": [
          {
            "id": "691",
            "type": "note"
          }
        ]
      },
      "signatures": {
        "data": [

        ]
      },
      "tags": {
        "data": [

        ]
      },
      "followers": {
        "data": [

        ]
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "last_editor": {
        "data": null
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "d68a2a49-c667-4088-b1b4-81ae414bbd60",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": {
          "read": true,
          "update": true
        },
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    },
    {
      "id": "40",
      "type": "user_overview",
      "attributes": {
        "permissions": {
          "read": false,
          "update": false
        },
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz",
        "abbreviation": null,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "status": "active"
      }
    },
    {
      "id": "1064",
      "type": "area",
      "attributes": {
        "permissions": {
          "read": false,
          "update": false
        },
        "name": "Pres. Josef Von",
        "status": "active",
        "color": "#ecf0f1",
        "external_id": null,
        "created_at": "2023-01-30T11:23:20Z",
        "updated_at": "2023-01-30T11:23:20Z"
      },
      "relationships": {
        "users": {
          "data": [

          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1094",
            "type": "workspace"
          }
        }
      }
    }
  ]
}
```



## Returns 404 error when the time tracking with the given id does not exist


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/22_22?include=workspace%2Cuser%2Carea%2Ctags%2Cbreaks%2Cfollowers
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id`

#### Parameters


```json
include: workspace,user,area,tags,breaks,followers
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time Tracking ID |
| permissions  | User Permissions |
| include  | Included relationships |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
404 Not Found
```


```json
{
  "errors": [
    {
      "status": "not_found",
      "source": {
        "pointer": "base"
      },
      "title": "Record can't be found!"
    }
  ]
}
```



## Update the time tracking


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/time_trackings/148
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id`

#### Parameters


```json
{"data":{"attributes":{"breaks_attributes":[{"starts_at":"2023-01-30T09:53:23Z","ends_at":"2023-01-30T10:53:23Z"}],"ends_at":"2023-01-30T11:03:23Z","starts_at":"2023-01-30T09:43:23Z"},"relationships":{"area":{"data":{"id":"1068","type":"area"}},"tags":{"data":[{"id":"57","type":"tag"},{"id":"58","type":"tag"}]}},"type":"time_tracking"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "148",
    "type": "time_tracking",
    "attributes": {
      "permissions": null,
      "assignment_id": null,
      "confirmed": false,
      "last_update_by": 39,
      "break_duration": 3600,
      "default_break_duration": 0,
      "created_by": "browser-stamps",
      "force_custom_break_duration": false,
      "external_id": null,
      "status": "active",
      "start_signature_id": null,
      "end_signature_id": null,
      "current_status": "finished",
      "starts_at": "2023-01-30T09:43:23Z",
      "ends_at": "2023-01-30T11:03:23Z",
      "actual_starts_at": "2023-01-30T09:23:23Z",
      "actual_ends_at": "2023-01-30T11:23:23Z",
      "created_at": "2023-01-30T11:23:23Z",
      "updated_at": "2023-01-30T11:23:23Z",
      "gross_time": 1.33,
      "net_time": 0.33,
      "break_time": 1.0,
      "system_notes_count": 3,
      "user_notes_count": 0,
      "signatures_count": 0,
      "attachments_count": 0
    },
    "relationships": {
      "area": {
        "data": {
          "id": "1068",
          "type": "area"
        }
      },
      "attachments": {
        "data": [

        ]
      },
      "breaks": {
        "data": [
          {
            "id": "26",
            "type": "break"
          }
        ]
      },
      "notes": {
        "data": [
          {
            "id": "713",
            "type": "note"
          },
          {
            "id": "717",
            "type": "note"
          },
          {
            "id": "718",
            "type": "note"
          }
        ]
      },
      "signatures": {
        "data": [

        ]
      },
      "tags": {
        "data": [
          {
            "id": "57",
            "type": "tag"
          },
          {
            "id": "58",
            "type": "tag"
          }
        ]
      },
      "followers": {
        "data": [

        ]
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "last_editor": {
        "data": {
          "id": "39",
          "type": "user_overview"
        }
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "a55d8ce0-1d97-4225-9437-f9aa08a12a17",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## returns 422 status with errors


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/time_trackings/149
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id`

#### Parameters


```json
{"data":{"attributes":{"breaks_attributes":[{"starts_at":"2023-01-30T09:53:23Z","ends_at":"2023-01-30T10:53:23Z"}],"ends_at":"2023-01-30T11:03:23Z","starts_at":"2023-01-30T09:43:23Z","user_id":99999},"relationships":{"area":{"data":{"id":"1069","type":"area"}},"tags":{"data":[{"id":"59","type":"tag"},{"id":"60","type":"tag"}]}},"type":"time_tracking"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "user_id"
      },
      "title": "Did not find User with id '99999' within authorized Enterprise!"
    }
  ]
}
```



## Employee is not allowed to edit time trackings


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/time_trackings/150
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id`

#### Parameters


```json
{"data":{"attributes":{"breaks_attributes":[{"starts_at":"2023-01-30T09:53:23Z","ends_at":"2023-01-30T10:53:23Z"}],"ends_at":"2023-01-30T11:03:23Z","starts_at":"2023-01-30T09:43:23Z"},"relationships":{"area":{"data":{"id":"1070","type":"area"}},"tags":{"data":[{"id":"61","type":"tag"},{"id":"62","type":"tag"}]}},"type":"time_tracking"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Employee is allowed to edit time trackings


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/time_trackings/151
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id`

#### Parameters


```json
{"data":{"attributes":{"breaks_attributes":[{"starts_at":"2023-01-30T09:53:23Z","ends_at":"2023-01-30T10:53:23Z"}],"ends_at":"2023-01-30T11:03:23Z","starts_at":"2023-01-30T09:43:23Z"},"relationships":{"area":{"data":{"id":"1071","type":"area"}},"tags":{"data":[{"id":"63","type":"tag"},{"id":"64","type":"tag"}]}},"type":"time_tracking"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "151",
    "type": "time_tracking",
    "attributes": {
      "permissions": null,
      "assignment_id": null,
      "confirmed": false,
      "last_update_by": 40,
      "break_duration": 3600,
      "default_break_duration": 0,
      "created_by": "browser-stamps",
      "force_custom_break_duration": false,
      "external_id": null,
      "status": "active",
      "start_signature_id": null,
      "end_signature_id": null,
      "current_status": "finished",
      "starts_at": "2023-01-30T09:43:23Z",
      "ends_at": "2023-01-30T11:03:23Z",
      "actual_starts_at": "2023-01-30T09:23:23Z",
      "actual_ends_at": "2023-01-30T11:23:23Z",
      "created_at": "2023-01-30T11:23:23Z",
      "updated_at": "2023-01-30T11:23:24Z",
      "gross_time": 1.33,
      "net_time": 0.33,
      "break_time": 1.0,
      "system_notes_count": 3,
      "user_notes_count": 0,
      "signatures_count": 0,
      "attachments_count": 0
    },
    "relationships": {
      "area": {
        "data": {
          "id": "1071",
          "type": "area"
        }
      },
      "attachments": {
        "data": [

        ]
      },
      "breaks": {
        "data": [
          {
            "id": "27",
            "type": "break"
          }
        ]
      },
      "notes": {
        "data": [
          {
            "id": "728",
            "type": "note"
          },
          {
            "id": "732",
            "type": "note"
          },
          {
            "id": "733",
            "type": "note"
          }
        ]
      },
      "signatures": {
        "data": [

        ]
      },
      "tags": {
        "data": [
          {
            "id": "63",
            "type": "tag"
          },
          {
            "id": "64",
            "type": "tag"
          }
        ]
      },
      "followers": {
        "data": [

        ]
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "last_editor": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "3eb26e2d-6e45-44bc-8738-baf68404faaa",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```

# Timetrackings/Attachments

## List of attachments


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/40/attachments
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/attachments`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "5",
      "type": "attachment",
      "attributes": {
        "author": "Enrico Schultz",
        "created_at": "2023-01-30T12:21:58+01:00",
        "updated_at": "2023-01-30T12:21:58+01:00",
        "file_name": "example.png",
        "file_content_type": "image/png",
        "file_url": "/system/note_attachments/files/000/000/005/original/example.png"
      }
    }
  ],
  "meta": {
    "request_id": "758cddff-b9f0-4419-af6b-afaecfc321cc",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```

# Timetrackings/Breaks

## returns 201 status and data for the break created


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/94/breaks
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks`

#### Parameters


```json
{"data":{"attributes":{"ends_at":"2023-01-30T12:03:08+01:00","starts_at":"2023-01-30T10:43:08+01:00"},"type":"break"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | The time tracking ID associated to the break |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "2",
    "type": "break",
    "attributes": {
      "starts_at": "2023-01-30T10:43:08+01:00",
      "ends_at": "2023-01-30T12:03:08+01:00",
      "created_at": "2023-01-30T12:23:08+01:00",
      "updated_at": "2023-01-30T12:23:08+01:00",
      "start_signature_id": null,
      "end_signature_id": null,
      "created_by": "browser-stamps"
    },
    "relationships": {
      "time_tracking": {
        "data": {
          "id": "94",
          "type": "time_tracking"
        }
      }
    }
  },
  "meta": {
    "request_id": "af7b8f1e-e430-4d17-95e7-bfe1d31582ea",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## returns 201 status and data for the break created


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/95/breaks
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks`

#### Parameters


```json
{"data":{"attributes":{"ends_at":"2023-01-30T12:03:08+01:00","starts_at":"2023-01-30T10:43:08+01:00"},"type":"break"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | The time tracking ID associated to the break |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "3",
    "type": "break",
    "attributes": {
      "starts_at": "2023-01-30T10:43:08+01:00",
      "ends_at": "2023-01-30T12:03:08+01:00",
      "created_at": "2023-01-30T12:23:08+01:00",
      "updated_at": "2023-01-30T12:23:08+01:00",
      "start_signature_id": null,
      "end_signature_id": null,
      "created_by": "browser-stamps"
    },
    "relationships": {
      "time_tracking": {
        "data": {
          "id": "95",
          "type": "time_tracking"
        }
      }
    }
  },
  "meta": {
    "request_id": "03609794-5b37-4818-8b39-b5b80e147252",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## returns 422 status and errors


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/96/breaks
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | The time tracking ID associated to the break |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "bad_request",
      "source": {
        "pointer": "base"
      },
      "title": "Param 'pause' is missing or empty."
    }
  ]
}
```



## returns an authorization error


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/97/breaks
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks`

#### Parameters


```json
{"data":{"attributes":{"ends_at":"2023-01-30T12:03:08+01:00","starts_at":"2023-01-30T10:43:08+01:00"},"type":"break"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | The time tracking ID associated to the break |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
401 Unauthorized
```


```json
{
  "errors": [
    {
      "status": "unauthorized",
      "source": {
        "pointer": "base"
      },
      "title": "You need to sign in or sign up before continuing."
    }
  ]
}
```



## response unauthorized


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/time_trackings/98/breaks/4
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks/:break_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* |  workspace |
| time_tracking_id *required* |  time tracking |
| break_id *required* |  break |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Delete a break


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/time_trackings/99/breaks/5
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks/:break_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* |  workspace |
| time_tracking_id *required* |  time tracking |
| break_id *required* |  break |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "5",
    "type": "break",
    "attributes": {
      "starts_at": "2023-01-30T11:23:08+01:00",
      "ends_at": "2023-01-30T11:53:08+01:00",
      "created_at": "2023-01-30T12:23:08+01:00",
      "updated_at": "2023-01-30T12:23:08+01:00",
      "start_signature_id": null,
      "end_signature_id": null,
      "created_by": "employee"
    },
    "relationships": {
      "time_tracking": {
        "data": {
          "id": "99",
          "type": "time_tracking"
        }
      }
    }
  },
  "meta": {
    "request_id": "626744d1-9980-4ab0-b339-b86d1c638547",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Index of breaks


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/100/breaks
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | The time tracking ID associated to the break |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "6",
      "type": "break",
      "attributes": {
        "starts_at": "2023-01-30T11:23:09+01:00",
        "ends_at": "2023-01-30T11:53:09+01:00",
        "created_at": "2023-01-30T12:23:09+01:00",
        "updated_at": "2023-01-30T12:23:09+01:00",
        "start_signature_id": null,
        "end_signature_id": null,
        "created_by": "employee"
      },
      "relationships": {
        "time_tracking": {
          "data": {
            "id": "100",
            "type": "time_tracking"
          }
        }
      }
    }
  ],
  "meta": {
    "request_id": "fb07a476-1e5d-461d-85b7-4db94213dd4d",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## can not access the breaks of other employees


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/100/breaks
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | The time tracking ID associated to the break |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Show break


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/102/breaks/8?include=time_tracking
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks/:break_id`

#### Parameters


```json
include: time_tracking
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | The time tracking ID associated to the break |
| break_id *required* | Break id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "8",
    "type": "break",
    "attributes": {
      "starts_at": "2023-01-30T11:23:09+01:00",
      "ends_at": "2023-01-30T11:53:09+01:00",
      "created_at": "2023-01-30T12:23:09+01:00",
      "updated_at": "2023-01-30T12:23:09+01:00",
      "start_signature_id": null,
      "end_signature_id": null,
      "created_by": "employee"
    },
    "relationships": {
      "time_tracking": {
        "data": {
          "id": "102",
          "type": "time_tracking"
        }
      }
    }
  },
  "meta": {
    "request_id": "777967bc-191e-4c62-90fd-1d72ef25bd30",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "102",
      "type": "time_tracking",
      "attributes": {
        "permissions": null,
        "assignment_id": null,
        "confirmed": false,
        "last_update_by": null,
        "break_duration": null,
        "default_break_duration": 0,
        "created_by": "browser-stamps",
        "force_custom_break_duration": false,
        "external_id": null,
        "status": "active",
        "start_signature_id": null,
        "end_signature_id": null,
        "current_status": "finished",
        "starts_at": "2023-01-30T09:23:09Z",
        "ends_at": "2023-01-30T11:23:09Z",
        "actual_starts_at": "2023-01-30T09:23:09Z",
        "actual_ends_at": "2023-01-30T11:23:09Z",
        "created_at": "2023-01-30T11:23:09Z",
        "updated_at": "2023-01-30T11:23:09Z",
        "gross_time": 2.0,
        "net_time": 2.0,
        "break_time": 0.0,
        "system_notes_count": 1,
        "user_notes_count": 0,
        "signatures_count": 0,
        "attachments_count": 0
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        },
        "breaks": {
          "data": [
            {
              "id": "8",
              "type": "break"
            }
          ]
        },
        "notes": {
          "data": [
            {
              "id": "642",
              "type": "note"
            }
          ]
        },
        "signatures": {
          "data": [

          ]
        },
        "tags": {
          "data": [

          ]
        },
        "followers": {
          "data": [

          ]
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "last_editor": {
          "data": null
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    }
  ]
}
```



## can not access the break of another employee


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/104/breaks/10?include=time_tracking
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks/:break_id`

#### Parameters


```json
include: time_tracking
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | The time tracking ID associated to the break |
| break_id *required* | Break id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Update a break


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/time_trackings/105/breaks/11
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks/:break_id`

#### Parameters


```json
{"data":{"attributes":{"ends_at":"2023-01-30T12:03:10+01:00","starts_at":"2023-01-30T10:43:10+01:00"},"type":"break"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | The time tracking ID associated to the break |
| break_id *required* | Break id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "11",
    "type": "break",
    "attributes": {
      "starts_at": "2023-01-30T10:43:10+01:00",
      "ends_at": "2023-01-30T12:03:10+01:00",
      "created_at": "2023-01-30T12:23:10+01:00",
      "updated_at": "2023-01-30T12:23:10+01:00",
      "start_signature_id": null,
      "end_signature_id": null,
      "created_by": "employee"
    },
    "relationships": {
      "time_tracking": {
        "data": {
          "id": "105",
          "type": "time_tracking"
        }
      }
    }
  },
  "meta": {
    "request_id": "e7824b41-6e46-441b-a1d6-d29ef34f3137",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Employee not allowed to edit breaks


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/time_trackings/106/breaks/12
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks/:break_id`

#### Parameters


```json
{"data":{"attributes":{"ends_at":"2023-01-30T12:03:10+01:00","starts_at":"2023-01-30T10:43:10+01:00"},"type":"break"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | The time tracking ID associated to the break |
| break_id *required* | Break id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Employee is allowed to edit breaks


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/time_trackings/107/breaks/13
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/breaks/:break_id`

#### Parameters


```json
{"data":{"attributes":{"ends_at":"2023-01-30T12:03:10+01:00","starts_at":"2023-01-30T10:43:10+01:00"},"type":"break"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | The time tracking ID associated to the break |
| break_id *required* | Break id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "13",
    "type": "break",
    "attributes": {
      "starts_at": "2023-01-30T10:43:10+01:00",
      "ends_at": "2023-01-30T12:03:10+01:00",
      "created_at": "2023-01-30T12:23:10+01:00",
      "updated_at": "2023-01-30T12:23:10+01:00",
      "start_signature_id": null,
      "end_signature_id": null,
      "created_by": "employee"
    },
    "relationships": {
      "time_tracking": {
        "data": {
          "id": "107",
          "type": "time_tracking"
        }
      }
    }
  },
  "meta": {
    "request_id": "60764ff3-b6fb-4306-8cb7-ac95dda8c618",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```

# TimeTrackings/Exports

## Create time-tracking export


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/exports
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/exports`

#### Parameters


```json
{"data":{"attributes":{"export_type":"sum","format":"xls","ids":[16]},"type":"export"}}
```


| Name | Description |
|:-----|:------------|
| filter  | Filter param |
| workspace_id *required* | Workspace ID/Company ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "13",
    "type": "export",
    "attributes": {
      "id": 13,
      "user_id": 39,
      "export_type": "sum",
      "status": "pending",
      "file_url": "/files/original/missing.png",
      "format": null
    }
  },
  "meta": {
    "request_id": "cb07cb7f-407c-4b51-bc83-dd4c8f0d13f9",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Show time-tracking export


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/exports/15
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/exports/:export_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| workspace_id *required* | Export ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "15",
    "type": "export",
    "attributes": {
      "id": 15,
      "user_id": 40,
      "export_type": "list",
      "status": "success",
      "file_url": "/system/exports/files/000/000/015/original/sit.png?1675077707",
      "format": "png"
    }
  },
  "meta": {
    "request_id": "17b0e222-9c6f-463b-b0eb-71131e1a2a11",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



# Timetrackings/Followers



## Add follower for time tracking


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/18/followers
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/followers`

#### Parameters


```json
{"data":{"attributes":{"ids":[40]},"type":"follower"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| time_tracking_id *required* | Time Tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "18",
    "type": "time_tracking",
    "attributes": {
      "permissions": null,
      "assignment_id": null,
      "confirmed": false,
      "last_update_by": null,
      "break_duration": null,
      "default_break_duration": 0,
      "created_by": "browser-stamps",
      "force_custom_break_duration": false,
      "external_id": null,
      "status": "active",
      "start_signature_id": null,
      "end_signature_id": null,
      "current_status": "finished",
      "starts_at": "2023-01-30T09:21:48Z",
      "ends_at": "2023-01-30T11:21:48Z",
      "actual_starts_at": "2023-01-30T09:21:48Z",
      "actual_ends_at": "2023-01-30T11:21:48Z",
      "created_at": "2023-01-30T11:21:48Z",
      "updated_at": "2023-01-30T11:21:48Z",
      "gross_time": 2.0,
      "net_time": 2.0,
      "break_time": 0.0,
      "system_notes_count": 1,
      "user_notes_count": 0,
      "signatures_count": 0,
      "attachments_count": 0
    },
    "relationships": {
      "attachments": {
        "data": [

        ]
      },
      "breaks": {
        "data": [

        ]
      },
      "notes": {
        "data": [
          {
            "id": "329",
            "type": "note"
          }
        ]
      },
      "signatures": {
        "data": [

        ]
      },
      "tags": {
        "data": [

        ]
      },
      "followers": {
        "data": [
          {
            "id": "40",
            "type": "user_overview"
          }
        ]
      },
      "user": {
        "data": {
          "id": "39",
          "type": "user_overview"
        }
      },
      "last_editor": {
        "data": null
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "444cd572-5fd7-4bcb-8994-037a05712179",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Delete follower for time tracking


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/time_trackings/19/followers/40
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/followers/:follower_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| time_tracking_id *required* | Time Tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "19",
    "type": "time_tracking",
    "attributes": {
      "permissions": null,
      "assignment_id": null,
      "confirmed": false,
      "last_update_by": null,
      "break_duration": null,
      "default_break_duration": 0,
      "created_by": "browser-stamps",
      "force_custom_break_duration": false,
      "external_id": null,
      "status": "active",
      "start_signature_id": null,
      "end_signature_id": null,
      "current_status": "finished",
      "starts_at": "2023-01-30T09:21:48Z",
      "ends_at": "2023-01-30T11:21:48Z",
      "actual_starts_at": "2023-01-30T09:21:48Z",
      "actual_ends_at": "2023-01-30T11:21:48Z",
      "created_at": "2023-01-30T11:21:48Z",
      "updated_at": "2023-01-30T11:21:48Z",
      "gross_time": 2.0,
      "net_time": 2.0,
      "break_time": 0.0,
      "system_notes_count": 1,
      "user_notes_count": 0,
      "signatures_count": 0,
      "attachments_count": 0
    },
    "relationships": {
      "attachments": {
        "data": [

        ]
      },
      "breaks": {
        "data": [

        ]
      },
      "notes": {
        "data": [
          {
            "id": "330",
            "type": "note"
          }
        ]
      },
      "signatures": {
        "data": [

        ]
      },
      "tags": {
        "data": [

        ]
      },
      "followers": {
        "data": [

        ]
      },
      "user": {
        "data": {
          "id": "39",
          "type": "user_overview"
        }
      },
      "last_editor": {
        "data": null
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "610563fe-9b58-413c-8ad0-406a07849e74",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Get time tracking followers list


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/20/followers
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/followers`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| time_tracking_id *required* | Time Tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "40",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2022-12-30",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 8,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "17hs",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "23e4a1c3-54af-497d-b7bf-21f63badebbb",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```

# Timetrackings/Notes

## User create note for time tracking


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/21/notes
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes`

#### Parameters


```json
{"data":{"attributes":{"content":"Create note test"},"type":"note"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| time_tracking_id *required* | Time Tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "365",
    "type": "user_note",
    "attributes": {
      "permissions": null,
      "content": "Create note test",
      "author": "Freiherr Sami Grams",
      "author_role": "admin",
      "type": "UserNote",
      "created_at": "2023-01-30T12:21:52+01:00"
    },
    "relationships": {
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "3ae7b458-1e44-47a6-bce9-7e7034d53849",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Create note with wrong body


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/22/notes
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| time_tracking_id *required* | Time Tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "bad_request",
      "source": {
        "pointer": "base"
      },
      "title": "Param 'note' is missing or empty."
    }
  ]
}
```



## Unauthorized to create note for other employee time tracking


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/23/notes
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes`

#### Parameters


```json
{"data":{"attributes":{"content":"Create note test"},"type":"note"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| time_tracking_id *required* | Time Tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## employee delete his own note of time tracking


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/time_trackings/24/notes/370
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes/:user_note_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| time_tracking_id *required* | Time Tracking ID |
| user_note_id *required* | User Note ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "370",
    "type": "user_note",
    "attributes": {
      "permissions": null,
      "content": "This is a note",
      "author": "Enrico Schultz",
      "author_role": "employee",
      "type": "UserNote",
      "created_at": "2023-01-30T16:21:53+01:00"
    },
    "relationships": {
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "e6bbd948-723e-49a4-91e5-b4b04872aea4",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## admin can delete employee note of time tracking


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/time_trackings/25/notes/373
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes/:user_note_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| time_tracking_id *required* | Time Tracking ID |
| user_note_id *required* | User Note ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "373",
    "type": "user_note",
    "attributes": {
      "permissions": null,
      "content": "This is a note",
      "author": "Enrico Schultz",
      "author_role": "employee",
      "type": "UserNote",
      "created_at": "2023-01-30T16:21:53+01:00"
    },
    "relationships": {
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "ad499c19-b2ab-49e8-b37a-d5ed4f0ff802",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Unauthorized employee to delete note of other employee time tracking


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/time_trackings/26/notes/376
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes/:user_note_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| time_tracking_id *required* | Time Tracking ID |
| user_note_id *required* | User Note ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Show a time tracking note list


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/27/notes
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time Tracking ID |
| permissions  | User Permissions |
| filter  | Type filter |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "377",
      "type": "note",
      "attributes": {
        "permissions": null,
        "content": "time tracking has been created.",
        "type": "SystemNote",
        "created_at": "2023-01-30T12:21:54+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "378",
      "type": "note",
      "attributes": {
        "permissions": null,
        "content": "This is a note",
        "author": "Freiherr Sami Grams",
        "author_role": "admin",
        "type": "UserNote",
        "created_at": "2023-01-30T16:21:54+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "b640f31f-413a-40d8-ad9c-f2aaa0499496",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2
  }
}
```



## With Permissions


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/28/notes?permissions=read%2C+update
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes`

#### Parameters


```json
permissions: read, update
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time Tracking ID |
| permissions  | User Permissions |
| filter  | Type filter |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "379",
      "type": "note",
      "attributes": {
        "permissions": {
          "read": true,
          "update": true
        },
        "content": "time tracking has been created.",
        "type": "SystemNote",
        "created_at": "2023-01-30T12:21:54+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "380",
      "type": "note",
      "attributes": {
        "permissions": {
          "read": true,
          "update": true
        },
        "content": "This is a note",
        "author": "Freiherr Sami Grams",
        "author_role": "admin",
        "type": "UserNote",
        "created_at": "2023-01-30T16:21:54+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "d410a80d-8ace-4289-bdd3-8241f67125a8",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2
  }
}
```



## Shows only system notes


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/29/notes?filter[type]=eq%3ASystemNote
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes`

#### Parameters


```json
filter: {&quot;type&quot;=&gt;&quot;eq:SystemNote&quot;}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time Tracking ID |
| permissions  | User Permissions |
| filter  | Type filter |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "381",
      "type": "note",
      "attributes": {
        "permissions": null,
        "content": "time tracking has been created.",
        "type": "SystemNote",
        "created_at": "2023-01-30T12:21:54+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "2d800d24-e000-4bd1-923c-408b1a965d38",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Hides system notes


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/30/notes?filter[type]=%21eq%3ASystemNote
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes`

#### Parameters


```json
filter: {&quot;type&quot;=&gt;&quot;!eq:SystemNote&quot;}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time Tracking ID |
| permissions  | User Permissions |
| filter  | Type filter |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "384",
      "type": "note",
      "attributes": {
        "permissions": null,
        "content": "This is a note",
        "author": "Freiherr Sami Grams",
        "author_role": "admin",
        "type": "UserNote",
        "created_at": "2023-01-30T16:21:55+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "91046583-8498-452f-9082-4a7263f8c431",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## No system notes are returned when the account does not have the module &#39;show_system_notes&#39;


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/31/notes
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time Tracking ID |
| permissions  | User Permissions |
| filter  | Type filter |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "386",
      "type": "note",
      "attributes": {
        "permissions": null,
        "content": "This is a note",
        "author": "Freiherr Sami Grams",
        "author_role": "admin",
        "type": "UserNote",
        "created_at": "2023-01-30T16:21:55+01:00"
      },
      "relationships": {
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "5c1065e9-cd10-46a5-be97-1160f0e4f348",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Unauthorized to see other employee time tracking notes


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/32/notes
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time Tracking ID |
| permissions  | User Permissions |
| filter  | Type filter |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## User update note for time tracking


### Request

#### Endpoint

```plaintext
PUT /api/v3/workspaces/1028/time_trackings/33/notes/390
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PUT /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes/:user_note_id`

#### Parameters


```json
{"data":{"attributes":{"content":"Update note test"},"type":"note"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| time_tracking_id *required* | Time Tracking ID |
| user_note_id *required* | User Note ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "390",
    "type": "user_note",
    "attributes": {
      "permissions": null,
      "content": "Update note test",
      "author": "Enrico Schultz",
      "author_role": "employee",
      "type": "UserNote",
      "created_at": "2023-01-30T16:21:55+01:00"
    },
    "relationships": {
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "9a6fb25b-f1ab-4f48-aed4-06688471cf94",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## update note with wrong body


### Request

#### Endpoint

```plaintext
PUT /api/v3/workspaces/1028/time_trackings/34/notes/393
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PUT /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes/:user_note_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| time_tracking_id *required* | Time Tracking ID |
| user_note_id *required* | User Note ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "bad_request",
      "source": {
        "pointer": "base"
      },
      "title": "Param 'note' is missing or empty."
    }
  ]
}
```



## Unauthorized account admin to update note for employee time tracking


### Request

#### Endpoint

```plaintext
PUT /api/v3/workspaces/1028/time_trackings/35/notes/395
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PUT /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/notes/:user_note_id`

#### Parameters


```json
{"data":{"attributes":{"content":"Update note test"},"type":"note"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID/Company ID |
| time_tracking_id *required* | Time Tracking ID |
| user_note_id *required* | User Note ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```

# Timetrackings/Signatures

## List of signatures


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/41/signatures
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/signatures`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "1",
      "type": "signature",
      "attributes": {
        "title": "start",
        "image_file_name": "start_signature",
        "image_content_type": "image/jpeg",
        "image_url": "/system/signatures/images/000/000/001/medium/start_signature?1675077718",
        "created_at": "2023-01-30T12:21:58+01:00",
        "image_updated_at": "2023-01-30T12:21:58+01:00"
      }
    }
  ],
  "meta": {
    "request_id": "42240f99-b55a-4769-8729-806a2fa89a1d",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```

# Timetrackings/Tags

## returns 201 status and data for the time tracking tagging created


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/taggings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/taggings`

#### Parameters


```json
{"data":{"attributes":{"tag_id":52,"taggable_id":"88ee0baf-b7df-40a1-8d87-69c202c77487","taggable_type":"TimeTracking"},"type":"tagging"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "2b78d5da-c3c2-412f-918a-0a4083f255e3",
    "type": "tagging",
    "attributes": {
      "taggable_type": "TimeTracking",
      "taggable_id": "88ee0baf-b7df-40a1-8d87-69c202c77487"
    },
    "relationships": {
      "tag": {
        "data": {
          "id": "52",
          "type": "tag"
        }
      }
    }
  },
  "meta": {
    "request_id": "d9b15e42-583c-4fa4-97b9-0fc6fa15d9bd",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Employees are by default not allowed to tag time trackings


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/taggings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/taggings`

#### Parameters


```json
{"data":{"attributes":{"tag_id":53,"taggable_id":"c803770e-af14-4344-b68a-de986ab4fdf8","taggable_type":"TimeTracking"},"type":"tagging"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Employees can tag time trackings if allow_employees_tag_working_sessions setting is set to true


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/taggings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/taggings`

#### Parameters


```json
{"data":{"attributes":{"tag_id":54,"taggable_id":"d841e71e-13e2-4a36-8e8f-954c28b58ddd","taggable_type":"TimeTracking"},"type":"tagging"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "7fbde2af-aeba-49c1-881c-036154ddbb99",
    "type": "tagging",
    "attributes": {
      "taggable_type": "TimeTracking",
      "taggable_id": "d841e71e-13e2-4a36-8e8f-954c28b58ddd"
    },
    "relationships": {
      "tag": {
        "data": {
          "id": "54",
          "type": "tag"
        }
      }
    }
  },
  "meta": {
    "request_id": "e69e9ea2-4ff2-4158-8ffc-215ba1bf09fc",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Empty params return 422 status and errors


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/taggings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/taggings`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "bad_request",
      "source": {
        "pointer": "base"
      },
      "title": "Param 'tagging' is missing or empty."
    }
  ]
}
```



## returns 201 status and data for the tag created


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/143/tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/tags`

#### Parameters


```json
{"data":{"attributes":{"title":"Schwarz","time_tracking_id":143},"type":"tag"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "55",
    "type": "tag",
    "attributes": {
      "title": "Schwarz",
      "active": true,
      "external_id": null,
      "color": null
    },
    "relationships": {
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      },
      "users": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "70dea85c-5e3f-4b17-a563-1cc4587125a3",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Employees are not allowed to create new tags for time trackings


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/144/tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/tags`

#### Parameters


```json
{"data":{"attributes":{"title":"Schwarz","time_tracking_id":144},"type":"tag"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Empty params return 422 status and errors


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/145/tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/tags`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "bad_request",
      "source": {
        "pointer": "base"
      },
      "title": "Param 'tag' is missing or empty."
    }
  ]
}
```



## returns an authentication error


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/time_trackings/146/tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/tags`

#### Parameters


```json
{"data":{"attributes":{"title":"Schwarz","time_tracking_id":146},"type":"tag"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
401 Unauthorized
```


```json
{
  "errors": [
    {
      "status": "unauthorized",
      "source": {
        "pointer": "base"
      },
      "title": "You need to sign in or sign up before continuing."
    }
  ]
}
```



## Index of tags


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_trackings/147/tags
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_trackings/:time_tracking_id/tags`

#### Parameters



| Name | Description |
|:-----|:------------|
| filter  | Tag filter |
| workspace_id *required* | Workspace ID |
| time_tracking_id *required* | Time tracking ID associated to the tags |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "56",
      "type": "tag",
      "attributes": {
        "title": "53-azure",
        "active": true,
        "external_id": null,
        "color": null
      },
      "relationships": {
        "workspace": {
          "data": {
            "id": "1098",
            "type": "workspace"
          }
        },
        "users": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "57a6f3bf-0fc1-4ec0-85b3-c6d5e221fe3c",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```

# Workspaces/Notifications



## Batch delete notifications


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/notifications/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/notifications/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"destroy","all":false,"ids":[1,2]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Batch action process is running"
  }
}
```



## Delete all the notifications of the workspace


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/notifications/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/notifications/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"destroy","all":true,"ids":[11]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Batch action process is running"
  }
}
```



## It returns an error when the action is invalid


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/notifications/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/notifications/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"invalid","all":false,"ids":[11]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Invalid batch action"
    }
  ]
}
```



## It returns an improcessible entity error when the request body is missing


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/notifications/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/notifications/batch_actions`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "bad_request",
      "source": {
        "pointer": "base"
      },
      "title": "Param 'batch_action' is missing or empty."
    }
  ]
}
```



## It returns an authentication error for employees


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/notifications/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/notifications/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"destroy","all":false,"ids":[11]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Delete with valid type param


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/notifications/4?type=trigger_warning
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/notifications/:notification_id?type=:type`

#### Parameters


```json
type: trigger_warning
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| notification_id *required* | Notification ID |
| type *required* | Notification type |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "4",
    "type": "trigger_warning",
    "attributes": {
      "title": "Sample warning",
      "message": "This is a sample warning message.",
      "created_at": "2023-01-30T12:21:57+01:00",
      "updated_at": "2023-01-30T12:21:57+01:00"
    },
    "relationships": {
      "user": {
        "data": {
          "id": "40",
          "type": "user"
        }
      },
      "entity": {
        "data": {
          "id": "37",
          "type": "time_tracking"
        }
      }
    }
  },
  "meta": {
    "request_id": "b2db5828-fbb2-4a1c-8c85-cc3b8579cb08",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Delete with an invalid type param


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/notifications/5?type=trigger_wa
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/notifications/:notification_id?type=:type`

#### Parameters


```json
type: trigger_wa
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| notification_id *required* | Notification ID |
| type *required* | Notification type |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Type trigger_wa is not supported [trigger_warning or notification]"
    }
  ]
}
```



## Index


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/notifications
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/notifications`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "6",
      "type": "trigger_warning",
      "attributes": {
        "title": "Sample warning",
        "message": "This is a sample warning message.",
        "created_at": "2023-01-30T12:21:57+01:00",
        "updated_at": "2023-01-30T12:21:57+01:00"
      },
      "relationships": {
        "user": {
          "data": {
            "id": "40",
            "type": "user"
          }
        },
        "entity": {
          "data": {
            "id": "39",
            "type": "time_tracking"
          }
        }
      }
    },
    {
      "id": "7",
      "type": "trigger_warning",
      "attributes": {
        "title": "Sample warning",
        "message": "This is a sample warning message.",
        "created_at": "2023-01-30T12:21:57+01:00",
        "updated_at": "2023-01-30T12:21:57+01:00"
      },
      "relationships": {
        "user": {
          "data": {
            "id": "40",
            "type": "user"
          }
        },
        "entity": {
          "data": null
        }
      }
    }
  ],
  "meta": {
    "request_id": "c719fdc8-94dd-4ea5-9e67-398ce00c4637",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2
  }
}
```



## Employees can access notifications but not of type trigger_warning


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/notifications
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/notifications`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 0
200 OK
```


```json
{
  "data": [

  ],
  "meta": {
    "request_id": "24ad98b3-8ab4-49d9-a423-c2e9d84a3ec9",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 0
  }
}
```

# Users



## returns 200 status with the current user data


### Request

#### Endpoint

```plaintext
GET /api/v3/users/me
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/users/me`

#### Parameters


```json
{&quot;include&quot;:&quot;account, areas, workspaces&quot;}: 
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "40",
    "type": "user",
    "attributes": {
      "permissions": null,
      "email": "gail.block@jones.biz",
      "username": "Enrico Schultz",
      "tablet_pin": null,
      "abbreviation": null,
      "hour_holidays": false,
      "time_zone": null,
      "initial_time_account": 0.0,
      "checkin_complete": null,
      "start_of_accounting": "2022-12-30",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 8,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": null,
      "external_id": null,
      "birthday": null,
      "identifier_pin": "17hs",
      "locale": null,
      "status": "active",
      "admin_pin": null,
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": {
          "id": "1026",
          "type": "account"
        }
      },
      "areas": {
        "data": [
          {
            "id": "1028",
            "type": "area"
          }
        ]
      },
      "workspaces": {
        "data": [
          {
            "id": "1028",
            "type": "workspace"
          }
        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [
          {
            "id": "1028",
            "type": "absence_type"
          }
        ]
      },
      "tags": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "90e4cdf2-ae39-4566-bdc7-2bc5bdc7bf33",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Including working areas returns 200 status with the details


### Request

#### Endpoint

```plaintext
GET /api/v3/users/me?include=areas
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/users/me`

#### Parameters


```json
include: areas
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "40",
    "type": "user",
    "attributes": {
      "permissions": null,
      "email": "gail.block@jones.biz",
      "username": "Enrico Schultz",
      "tablet_pin": null,
      "abbreviation": null,
      "hour_holidays": false,
      "time_zone": null,
      "initial_time_account": 0.0,
      "checkin_complete": null,
      "start_of_accounting": "2022-12-30",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 8,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": null,
      "external_id": null,
      "birthday": null,
      "identifier_pin": "17hs",
      "locale": null,
      "status": "active",
      "admin_pin": null,
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": {
          "id": "1026",
          "type": "account"
        }
      },
      "areas": {
        "data": [
          {
            "id": "1028",
            "type": "area"
          }
        ]
      },
      "workspaces": {
        "data": [
          {
            "id": "1028",
            "type": "workspace"
          }
        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [
          {
            "id": "1028",
            "type": "absence_type"
          }
        ]
      },
      "tags": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "5d119e0d-8c8c-4cd0-8d2f-ff284a9637ea",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "1028",
      "type": "area",
      "attributes": {
        "permissions": null,
        "name": "Lorenz vom Wollmann",
        "status": "active",
        "color": "#913D88",
        "external_id": null,
        "created_at": "2023-01-30T11:21:43Z",
        "updated_at": "2023-01-30T11:21:43Z"
      },
      "relationships": {
        "users": {
          "data": [
            {
              "id": "40",
              "type": "user"
            },
            {
              "id": "42",
              "type": "user"
            },
            {
              "id": "43",
              "type": "user"
            }
          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    }
  ]
}
```



## Including companies returns 200 status with the details


### Request

#### Endpoint

```plaintext
GET /api/v3/users/me?include=workspaces
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/users/me`

#### Parameters


```json
include: workspaces
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "40",
    "type": "user",
    "attributes": {
      "permissions": null,
      "email": "gail.block@jones.biz",
      "username": "Enrico Schultz",
      "tablet_pin": null,
      "abbreviation": null,
      "hour_holidays": false,
      "time_zone": null,
      "initial_time_account": 0.0,
      "checkin_complete": null,
      "start_of_accounting": "2022-12-30",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 8,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": null,
      "external_id": null,
      "birthday": null,
      "identifier_pin": "17hs",
      "locale": null,
      "status": "active",
      "admin_pin": null,
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": {
          "id": "1026",
          "type": "account"
        }
      },
      "areas": {
        "data": [
          {
            "id": "1028",
            "type": "area"
          }
        ]
      },
      "workspaces": {
        "data": [
          {
            "id": "1028",
            "type": "workspace"
          }
        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [
          {
            "id": "1028",
            "type": "absence_type"
          }
        ]
      },
      "tags": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "5b544a6d-fd2b-4d78-9f40-248889d042cd",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": null,
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null,
        "is_admin": false
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    }
  ]
}
```



## Including companies returns 200 status with the details


### Request

#### Endpoint

```plaintext
GET /api/v3/users/me?include=current_absence
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/users/me`

#### Parameters


```json
include: current_absence
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "40",
    "type": "user",
    "attributes": {
      "permissions": null,
      "email": "gail.block@jones.biz",
      "username": "Enrico Schultz",
      "tablet_pin": null,
      "abbreviation": null,
      "hour_holidays": false,
      "time_zone": null,
      "initial_time_account": 0.0,
      "checkin_complete": null,
      "start_of_accounting": "2022-12-30",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 8,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": null,
      "external_id": null,
      "birthday": null,
      "identifier_pin": "17hs",
      "locale": null,
      "status": "active",
      "admin_pin": null,
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": {
          "id": "1026",
          "type": "account"
        }
      },
      "areas": {
        "data": [
          {
            "id": "1028",
            "type": "area"
          }
        ]
      },
      "workspaces": {
        "data": [
          {
            "id": "1028",
            "type": "workspace"
          }
        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [
          {
            "id": "1028",
            "type": "absence_type"
          }
        ]
      },
      "tags": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "da2616b1-960a-4730-8394-845f00837ac9",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [

  ]
}
```



## Invalid include parameter returns server error


### Request

#### Endpoint

```plaintext
GET /api/v3/users/me?include=working_ar
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/users/me`

#### Parameters


```json
include: working_ar
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
500 Internal Server Error
```


```json
{
  "errors": [
    {
      "status": "internal_server_error",
      "source": {
        "pointer": "base"
      },
      "title": "Included param 'working_ar' is not yet implemented."
    }
  ]
}
```



## returns admin_pin attribute


### Request

#### Endpoint

```plaintext
GET /api/v3/users/me?include=account%2C+areas%2C+workspaces
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/users/me`

#### Parameters


```json
include: account, areas, workspaces
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "39",
    "type": "user",
    "attributes": {
      "permissions": null,
      "email": "marcel_littel@hand.net",
      "username": "Freiherr Sami Grams",
      "tablet_pin": null,
      "abbreviation": null,
      "hour_holidays": false,
      "time_zone": null,
      "initial_time_account": 0.0,
      "checkin_complete": null,
      "start_of_accounting": "2023-01-01",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 1,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": null,
      "external_id": null,
      "birthday": null,
      "identifier_pin": "86re",
      "locale": null,
      "status": "active",
      "admin_pin": "1987",
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": {
          "id": "1026",
          "type": "account"
        }
      },
      "areas": {
        "data": [

        ]
      },
      "workspaces": {
        "data": [
          {
            "id": "1028",
            "type": "workspace"
          }
        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [
          {
            "id": "1028",
            "type": "absence_type"
          }
        ]
      },
      "tags": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "bb152fb9-be33-489e-bcd2-00d851a0d32e",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "1026",
      "type": "account",
      "attributes": {
        "phone": "+492204948890",
        "country": null,
        "locale": "de",
        "account_name": "Wallstab-Lutje",
        "created_at": "2023-01-30T11:21:41Z",
        "updated_at": "2023-01-30T11:21:41Z"
      }
    },
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": null,
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null,
        "is_admin": true
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    }
  ]
}
```

# Users/DataProfiles


## Show data profile


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/40/data_profiles/16?include=custom_fields%2Ccustom_field_values
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/:user_id/data_profiles/:id`

#### Parameters


```json
include: custom_fields,custom_field_values
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| id *required* | Data Profile ID |
| include  | Relationships details |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "16",
    "type": "data_profile",
    "attributes": {
      "permissions": null,
      "title": "Data profile 5_547",
      "position": 0,
      "user_checkin": null,
      "enabled": true
    },
    "relationships": {
      "custom_fields": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "538b9666-753c-45dd-ad44-bd80b8cdf349",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [

  ]
}
```

## Update data profile


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40/data_profiles/22
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/data_profiles/:id`

#### Parameters


```json
{"data":{"type":"data_profile","attributes":{"custom_field_values_attributes":[{"custom_field_id":"234","data_type":"string","value":"Augustus Ernser"},{"custom_field_id":"235","data_type":"float","value":"18.53"},{"custom_field_id":"236","data_type":"boolean","value":"true"},{"custom_field_id":"237","data_type":"date","value":"2023-01-30"},{"custom_field_id":"238","data_type":"time","value":"12:22"},{"custom_field_id":"239","data_type":"country_select","value":"DE"}]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| id *required* | Data Profile ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "22",
    "type": "data_profile",
    "attributes": {
      "permissions": null,
      "title": "Data profile 11_214",
      "position": 0,
      "user_checkin": null,
      "enabled": true
    },
    "relationships": {
      "custom_fields": {
        "data": [
          {
            "id": "239",
            "type": "custom_field"
          },
          {
            "id": "238",
            "type": "custom_field"
          },
          {
            "id": "237",
            "type": "custom_field"
          },
          {
            "id": "236",
            "type": "custom_field"
          },
          {
            "id": "235",
            "type": "custom_field"
          },
          {
            "id": "234",
            "type": "custom_field"
          }
        ]
      }
    }
  },
  "meta": {
    "request_id": "8dc94491-c085-4ee9-bec3-ee62166dcb3a",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```

# Users/Preferences

Destroy User Preferences

## destroy preference


### Request

#### Endpoint

```plaintext
DELETE /api/v3/users/40/preferences/1
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/users/:user_id/preferences/:id`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1",
    "type": "preference",
    "attributes": {
      "key": "employee_list",
      "value": {
        "tags": true,
        "areas": true,
        "email": true,
        "roles": true,
        "status": true,
        "username": true,
        "workspace": true
      }
    }
  },
  "meta": {
    "request_id": "544bb60d-447d-41ed-8024-565f3f36a88c",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Index


### Request

#### Endpoint

```plaintext
GET /api/v3/users/40/preferences
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/users/:user_id/preferences`

#### Parameters



| Name | Description |
|:-----|:------------|
| user_id *required* | User Id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 3
200 OK
```


```json
{
  "data": [
    {
      "id": "2",
      "type": "preference",
      "attributes": {
        "key": "absence_list",
        "value": {
          "days": true,
          "info": true,
          "tags": true,
          "type": true,
          "areas": true,
          "dates": true,
          "hours": true,
          "status": true,
          "employee": true,
          "confirmed_by": true
        }
      }
    },
    {
      "id": "3",
      "type": "preference",
      "attributes": {
        "key": "employee_list",
        "value": {
          "tags": true,
          "areas": true,
          "email": true,
          "roles": true,
          "status": true,
          "username": true,
          "workspace": true,
          "custom_field": true
        }
      }
    },
    {
      "id": "4",
      "type": "preference",
      "attributes": {
        "key": "time_tracking_list",
        "value": {
          "days": true,
          "tags": true,
          "type": true,
          "dates": true,
          "employee": true
        }
      }
    }
  ],
  "meta": {
    "request_id": "f68300db-4d6f-4383-82ad-5593c6c1aa01",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 3
  }
}
```



## User gets authorization error when trying to access another user&#39;s preferences


### Request

#### Endpoint

```plaintext
GET /api/v3/users/39/preferences
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/users/:user_id/preferences`

#### Parameters



| Name | Description |
|:-----|:------------|
| user_id *required* | User Id |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## updates values for user&#39;s employee list prefrence


### Request

#### Endpoint

```plaintext
PATCH /api/v3/users/40/preferences/5
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/users/:user_id/preferences/:id`

#### Parameters


```json
{"data":{"type":"preference","attributes":{"value":{"tags":false,"email":false,"roles":true,"status":false,"username":true,"workspace":true,"areas":true,"custom_key":true}}}}
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "5",
    "type": "preference",
    "attributes": {
      "key": "employee_list",
      "value": {
        "tags": false,
        "email": false,
        "roles": true,
        "status": false,
        "username": true,
        "workspace": true,
        "areas": true,
        "custom_key": true
      }
    }
  },
  "meta": {
    "request_id": "8fbdb0c5-b1e3-47db-bcfd-2aaf99b59499",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## updates values for user&#39;s absence list preference


### Request

#### Endpoint

```plaintext
PATCH /api/v3/users/40/preferences/6
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/users/:user_id/preferences/:id`

#### Parameters


```json
{"data":{"type":"preference","attributes":{"value":{"employee":true,"areas":false,"tags":true,"type":false,"dates":true,"days":false,"hours":true,"confirmed_by":false,"info":true,"status":false,"custom_key":false}}}}
```

None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "6",
    "type": "preference",
    "attributes": {
      "key": "absence_list",
      "value": {
        "employee": true,
        "areas": false,
        "tags": true,
        "type": false,
        "dates": true,
        "days": false,
        "hours": true,
        "confirmed_by": false,
        "info": true,
        "status": false,
        "custom_key": false
      }
    }
  },
  "meta": {
    "request_id": "a7079f27-07cf-4266-9ee5-da25cca35dd9",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```

# Workspaces

Workspaces resource

## Workspaces Index


### Request

#### Endpoint

```plaintext
GET /api/v3/accounts/1026/workspaces?include=areas
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/accounts/:account_id/workspaces`

#### Parameters


```json
include: areas
```


| Name | Description |
|:-----|:------------|
| account_id *required* | The ID of a account |
| permissions  | User Permissions |
| include  | Included relationships |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": null,
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": true,
        "welcome_message": "Welcome to your Workspace!"
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    }
  ],
  "included": [
    {
      "id": "1028",
      "type": "area",
      "attributes": {
        "permissions": null,
        "name": "Lorenz vom Wollmann",
        "status": "active",
        "color": "#913D88",
        "external_id": null,
        "created_at": "2023-01-30T11:21:43Z",
        "updated_at": "2023-01-30T11:21:43Z"
      },
      "relationships": {
        "users": {
          "data": [
            {
              "id": "40",
              "type": "user"
            },
            {
              "id": "42",
              "type": "user"
            },
            {
              "id": "43",
              "type": "user"
            }
          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    }
  ],
  "meta": {
    "request_id": "8bc8e7fe-a41e-41f6-b1ac-473a71f7bb94",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## With Permissions


### Request

#### Endpoint

```plaintext
GET /api/v3/accounts/1026/workspaces?include=areas&amp;permissions=read%2C+update
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/accounts/:account_id/workspaces`

#### Parameters


```json
include: areas
permissions: read, update
```


| Name | Description |
|:-----|:------------|
| account_id *required* | The ID of a account |
| permissions  | User Permissions |
| include  | Included relationships |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": {
          "read": true,
          "update": false
        },
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": true,
        "welcome_message": "Welcome to your Workspace!"
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    }
  ],
  "included": [
    {
      "id": "1028",
      "type": "area",
      "attributes": {
        "permissions": {
          "read": false,
          "update": false
        },
        "name": "Lorenz vom Wollmann",
        "status": "active",
        "color": "#913D88",
        "external_id": null,
        "created_at": "2023-01-30T11:21:43Z",
        "updated_at": "2023-01-30T11:21:43Z"
      },
      "relationships": {
        "users": {
          "data": [
            {
              "id": "40",
              "type": "user"
            },
            {
              "id": "42",
              "type": "user"
            },
            {
              "id": "43",
              "type": "user"
            }
          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    }
  ],
  "meta": {
    "request_id": "ef8ad32b-dc92-4868-96b8-cc42670e0a7e",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Destroy a workspace


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1058
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1058",
    "type": "workspace",
    "attributes": {
      "permissions": null,
      "name": "Company",
      "phone": null,
      "time_zone": "Berlin",
      "locale": "de",
      "avatar": "/avatars/original/missing.png",
      "external_id": null,
      "allow_employees_edit_working_session_area": true,
      "allow_employee_edit_punched_working_sessions": false,
      "allow_employees_tag_working_sessions": false,
      "checkin": null
    },
    "relationships": {
      "areas": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "d370f2df-4bc9-40eb-b281-b32eebaaaa7b",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Invite selected pending users


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/invitations
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/invitations`

#### Parameters


```json
{"data":{"type":"invitation","attributes":{"checkin":true,"welcome_message":"Welcome to your workspace!"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "https://web.papershift.com/join-workspace/6eea6d0b-db7b-42eb-9978-99a0f6260622?lang=de"
  }
}
```



## Employee can not invite users


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/invitations
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/invitations`

#### Parameters


```json
{"data":{"type":"invitation","attributes":{"checkin":true,"welcome_message":"Welcome to your workspace!"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Show workspace


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028?include=areas
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id`

#### Parameters


```json
include: areas
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |
| workspace_id *required* | Workspace ID |
| permissions  | User Permissions |
| include  | Included relationships |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1028",
    "type": "workspace",
    "attributes": {
      "permissions": null,
      "name": "Company",
      "phone": null,
      "time_zone": "Berlin",
      "locale": "de",
      "avatar": "/avatars/original/missing.png",
      "external_id": null,
      "allow_employees_edit_working_session_area": true,
      "allow_employee_edit_punched_working_sessions": false,
      "allow_employees_tag_working_sessions": false,
      "checkin": true,
      "welcome_message": "Welcome to your Workspace!"
    },
    "relationships": {
      "areas": {
        "data": [
          {
            "id": "1028",
            "type": "area"
          }
        ]
      }
    }
  },
  "meta": {
    "request_id": "35a267be-e903-48a8-8e91-1e39817d789d",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "1028",
      "type": "area",
      "attributes": {
        "permissions": null,
        "name": "Lorenz vom Wollmann",
        "status": "active",
        "color": "#913D88",
        "external_id": null,
        "created_at": "2023-01-30T11:21:43Z",
        "updated_at": "2023-01-30T11:21:43Z"
      },
      "relationships": {
        "users": {
          "data": [
            {
              "id": "40",
              "type": "user"
            },
            {
              "id": "42",
              "type": "user"
            },
            {
              "id": "43",
              "type": "user"
            }
          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    }
  ]
}
```



## With Permissions


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028?include=areas&amp;permissions=read%2C+update
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id`

#### Parameters


```json
include: areas
permissions: read, update
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |
| workspace_id *required* | Workspace ID |
| permissions  | User Permissions |
| include  | Included relationships |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1028",
    "type": "workspace",
    "attributes": {
      "permissions": {
        "read": true,
        "update": false
      },
      "name": "Company",
      "phone": null,
      "time_zone": "Berlin",
      "locale": "de",
      "avatar": "/avatars/original/missing.png",
      "external_id": null,
      "allow_employees_edit_working_session_area": true,
      "allow_employee_edit_punched_working_sessions": false,
      "allow_employees_tag_working_sessions": false,
      "checkin": true,
      "welcome_message": "Welcome to your Workspace!"
    },
    "relationships": {
      "areas": {
        "data": [
          {
            "id": "1028",
            "type": "area"
          }
        ]
      }
    }
  },
  "meta": {
    "request_id": "75035a27-66c5-442f-86f2-d9ef3352d2b5",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "1028",
      "type": "area",
      "attributes": {
        "permissions": {
          "read": false,
          "update": false
        },
        "name": "Lorenz vom Wollmann",
        "status": "active",
        "color": "#913D88",
        "external_id": null,
        "created_at": "2023-01-30T11:21:43Z",
        "updated_at": "2023-01-30T11:21:43Z"
      },
      "relationships": {
        "users": {
          "data": [
            {
              "id": "40",
              "type": "user"
            },
            {
              "id": "42",
              "type": "user"
            },
            {
              "id": "43",
              "type": "user"
            }
          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    }
  ]
}
```



## Update a workspace


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id`

#### Parameters


```json
{"data":{"type":"workspace","attributes":{"name":"New Name"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1028",
    "type": "workspace",
    "attributes": {
      "permissions": null,
      "name": "New Name",
      "phone": null,
      "time_zone": "Berlin",
      "locale": "de",
      "avatar": "/avatars/original/missing.png",
      "external_id": null,
      "allow_employees_edit_working_session_area": true,
      "allow_employee_edit_punched_working_sessions": false,
      "allow_employees_tag_working_sessions": false,
      "checkin": null
    },
    "relationships": {
      "areas": {
        "data": [
          {
            "id": "1028",
            "type": "area"
          }
        ]
      }
    }
  },
  "meta": {
    "request_id": "6cb4f4d4-c04a-4a97-9a32-3ddd5b63e52b",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## returns 200 status with the user records summary data


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/40/records/summary
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/:user_id/records/summary`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "40",
    "type": "records_summary",
    "attributes": {
      "confirmed_total_overtime_in_sec": 0.0,
      "total_overtime_in_sec": 0.0
    }
  },
  "meta": {
    "request_id": "6e542a92-c470-49c1-ae20-4be5b285b78e",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## returns 200 status with absence data


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1083/absences_calculations
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences_calculations`

#### Parameters



| Name | Description |
|:-----|:------------|
| absence_type_id  |  absence type |
| starts_at  |  starts at |
| ends_at  |  ends at |
| full_day  |  full day |
| time_zone  |  time zone |
| user_id  |  user |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "hours": null,
  "days": null
}
```

# Workspaces/Absences


## returns unauthorized error


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/absences/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/absences/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"create","starts_at":"2022-05-02T00:00:00+01:00","ends_at":"2022-05-02T23:59:59+01:00","full_day":true,"title":"bulk 1","absence_type_id":1,"user_ids":{"0":"1","1":"2"},"notes_attributes":[{"content":"Sample note"},{"content":"Another note"}]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "unauthorized",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## returns unauthorized error


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/absences/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/absences/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"foobar","starts_at":"2022-05-02T00:00:00+01:00","ends_at":"2022-05-02T23:59:59+01:00","full_day":true,"title":"bulk 1","absence_type_id":1,"user_ids":{"0":"1","1":"2"},"notes_attributes":[{"content":"Sample note"},{"content":"Another note"}]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Invalid batch action"
    }
  ]
}
```



## returns unprocessable entity error


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/absences/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/absences/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"create","starts_at":"2022-05-02T00:00:00+01:00","ends_at":"2022-05-02T23:59:59+01:00","full_day":true,"title":"bulk 1","absence_type_id":1088,"user_ids":[40,41],"notes_attributes":[{"content":"Sample note"},{"content":"Another note"}]},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Validation failed: Absence Did not find AbsenceType with id '1088' within authorized Enterprise!"
    }
  ]
}
```



## creates bulk absences


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/absences/batch_actions
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/absences/batch_actions`

#### Parameters


```json
{"data":{"attributes":{"action":"create","starts_at":"2022-05-02T00:00:00+01:00","ends_at":"2022-05-02T23:59:59+01:00","full_day":true,"title":"bulk 1","absence_type_id":1089,"user_ids":[40,41],"notes_attributes":[{"created_by":40,"content":"Sample note"},{"created_by":41,"content":"Another note"}],"follower_ids":[40,41,42],"force_calc_custom_hours":true},"type":"batch_action"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Batch action process is running"
  }
}
```



## Confirm an absence


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/absences/24/absences_confirmations
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/absences/:absence_id/absences_confirmations`

#### Parameters


```json
{"include":"absence_type,user,confirmed_by_user"}
```


| Name | Description |
|:-----|:------------|
| include  | Confirmed by user |
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "24",
    "type": "absence",
    "attributes": {
      "permissions": null,
      "title": "Holiday 1_759",
      "hours": 0.0,
      "days": 1.0,
      "full_day": true,
      "confirmation_status": "confirmed",
      "confirmed": true,
      "created_by": null,
      "use_custom_values": false,
      "external_id": null,
      "confirm_message": null,
      "attachments_count": 0,
      "starts_at": "2023-01-29T23:00:00Z",
      "ends_at": "2023-01-30T22:59:59Z",
      "confirmed_at": "2023-01-30T11:22:51Z",
      "created_at": "2023-01-30T11:22:51Z",
      "updated_at": "2023-01-30T11:22:51Z",
      "system_notes_count": 2,
      "user_notes_count": 0
    },
    "relationships": {
      "absence_type": {
        "data": {
          "id": "1028",
          "type": "absence_type"
        }
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "confirmed_by_user": {
        "data": {
          "id": "39",
          "type": "user_overview"
        }
      },
      "followers": {
        "data": [

        ]
      },
      "notes": {
        "data": [
          {
            "id": "510",
            "type": "note"
          },
          {
            "id": "511",
            "type": "note"
          }
        ]
      },
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "b4a4771d-b45e-4b24-bad4-cbf5e8ddf211",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Create an absence


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/absences
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/absences`

#### Parameters


```json
{"data":{"attributes":{"charge_days_job_status":"","confirm_message":"","confirmed":"","confirmed_at":"","confirmed_by":"","created_by":"","days":0,"ends_at":"2020-12-03T00:00:00+01:00","external_id":"","full_day":true,"hours":8,"import_id":"","outlook_id":"","secure_id":"","starts_at":"2020-12-02T00:00:00+01:00","title":"","use_custom_values":true,"notes_attributes":[{"created_by":40,"content":"note content"}],"user_id":40,"follower_ids":[100],"absence_type_id":1028},"type":"absence"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "27",
    "type": "absence",
    "attributes": {
      "permissions": null,
      "title": "Holiday 1_759",
      "hours": 0.0,
      "days": 0.0,
      "full_day": true,
      "confirmation_status": "pending",
      "confirmed": null,
      "created_by": null,
      "use_custom_values": false,
      "external_id": "",
      "confirm_message": "",
      "attachments_count": 0,
      "starts_at": "2020-12-01T23:00:00Z",
      "ends_at": "2020-12-03T22:59:59Z",
      "confirmed_at": null,
      "created_at": "2023-01-30T11:22:52Z",
      "updated_at": "2023-01-30T11:22:52Z",
      "system_notes_count": 1,
      "user_notes_count": 1
    },
    "relationships": {
      "absence_type": {
        "data": {
          "id": "1028",
          "type": "absence_type"
        }
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "confirmed_by_user": {
        "data": null
      },
      "followers": {
        "data": [
          {
            "id": "100",
            "type": "user_overview"
          }
        ]
      },
      "notes": {
        "data": [
          {
            "id": "515",
            "type": "note"
          },
          {
            "id": "516",
            "type": "note"
          }
        ]
      },
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "536b94b6-e908-414f-96ed-d94490f866b5",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Delete an absence


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/absences/29
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/absences/:absence_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "29",
    "type": "absence",
    "attributes": {
      "permissions": null,
      "title": "Holiday 1_759",
      "hours": 0.0,
      "days": 2.0,
      "full_day": true,
      "confirmation_status": "pending",
      "confirmed": null,
      "created_by": null,
      "use_custom_values": false,
      "external_id": null,
      "confirm_message": null,
      "attachments_count": 0,
      "starts_at": "2023-01-29T23:00:00Z",
      "ends_at": "2023-01-31T22:59:59Z",
      "confirmed_at": null,
      "created_at": "2023-01-30T11:22:53Z",
      "updated_at": "2023-01-30T11:22:53Z",
      "system_notes_count": 0,
      "user_notes_count": 0
    },
    "relationships": {
      "absence_type": {
        "data": {
          "id": "1028",
          "type": "absence_type"
        }
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "confirmed_by_user": {
        "data": null
      },
      "followers": {
        "data": [

        ]
      },
      "notes": {
        "data": [

        ]
      },
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "8f434171-8638-46e6-a5a6-7fccb74670f0",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Index


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| permissions  | User Permissions |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "42",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:56Z",
        "updated_at": "2023-01-30T11:22:56Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "538",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "3be4fb74-0db3-4913-9521-f9b438b88804",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1,
    "pending": 1,
    "confirmed": 0,
    "rejected": 0,
    "total_days": 1.0,
    "total_hours": 0.0
  }
}
```



## Status counts


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| permissions  | User Permissions |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 6
200 OK
```


```json
{
  "data": [
    {
      "id": "46",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:56Z",
        "updated_at": "2023-01-30T11:22:56Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "542",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "47",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:56Z",
        "updated_at": "2023-01-30T11:22:56Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "543",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "48",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "confirmed",
        "confirmed": true,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:57Z",
        "updated_at": "2023-01-30T11:22:57Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "544",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "49",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "confirmed",
        "confirmed": true,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:57Z",
        "updated_at": "2023-01-30T11:22:57Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "545",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "50",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "confirmed",
        "confirmed": true,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:57Z",
        "updated_at": "2023-01-30T11:22:57Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "546",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "51",
      "type": "absence",
      "attributes": {
        "permissions": null,
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "rejected",
        "confirmed": false,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:57Z",
        "updated_at": "2023-01-30T11:22:57Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "547",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "571836e3-f302-422a-8b3e-319176b23aee",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 6,
    "pending": 2,
    "confirmed": 3,
    "rejected": 1,
    "total_days": 6.0,
    "total_hours": 0.0
  }
}
```



## Index with pagination overflow


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences?page=100
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences`

#### Parameters


```json
page: 100
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| permissions  | User Permissions |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 100
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [

  ],
  "meta": {
    "request_id": "639f3d37-92ae-4f62-908c-edaa0d9a1af9",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 100,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1,
    "pending": 1,
    "confirmed": 0,
    "rejected": 0,
    "total_days": 1.0,
    "total_hours": 0.0
  }
}
```



## With Permissions


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences?permissions=read%2C+update
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences`

#### Parameters


```json
permissions: read, update
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| permissions  | User Permissions |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "53",
      "type": "absence",
      "attributes": {
        "permissions": {
          "read": true,
          "update": true
        },
        "title": "Holiday 1_759",
        "hours": 0.0,
        "days": 1.0,
        "full_day": true,
        "confirmation_status": "pending",
        "confirmed": null,
        "created_by": null,
        "use_custom_values": false,
        "external_id": null,
        "confirm_message": null,
        "attachments_count": 0,
        "starts_at": "2023-01-29T23:00:00Z",
        "ends_at": "2023-01-30T22:59:59Z",
        "confirmed_at": null,
        "created_at": "2023-01-30T11:22:57Z",
        "updated_at": "2023-01-30T11:22:57Z",
        "system_notes_count": 1,
        "user_notes_count": 0
      },
      "relationships": {
        "absence_type": {
          "data": {
            "id": "1028",
            "type": "absence_type"
          }
        },
        "user": {
          "data": {
            "id": "40",
            "type": "user_overview"
          }
        },
        "confirmed_by_user": {
          "data": null
        },
        "followers": {
          "data": [

          ]
        },
        "notes": {
          "data": [
            {
              "id": "549",
              "type": "note"
            }
          ]
        },
        "attachments": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "d0c759a0-7f81-430c-b1fa-cc48d6dac4cd",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1,
    "pending": 1,
    "confirmed": 0,
    "rejected": 0,
    "total_days": 1.0,
    "total_hours": 0.0
  }
}
```



## Reject an absence


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/absences/55/absences_rejections
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/absences/:absence_id/absences_rejections`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "55",
    "type": "absence",
    "attributes": {
      "permissions": null,
      "title": "Holiday 1_759",
      "hours": 0.0,
      "days": 1.0,
      "full_day": true,
      "confirmation_status": "pending",
      "confirmed": null,
      "created_by": null,
      "use_custom_values": false,
      "external_id": null,
      "confirm_message": null,
      "attachments_count": 0,
      "starts_at": "2023-01-29T23:00:00Z",
      "ends_at": "2023-01-30T22:59:59Z",
      "confirmed_at": null,
      "created_at": "2023-01-30T11:22:57Z",
      "updated_at": "2023-01-30T11:22:58Z",
      "system_notes_count": 2,
      "user_notes_count": 0
    },
    "relationships": {
      "absence_type": {
        "data": {
          "id": "1028",
          "type": "absence_type"
        }
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "confirmed_by_user": {
        "data": null
      },
      "followers": {
        "data": [

        ]
      },
      "notes": {
        "data": [
          {
            "id": "551",
            "type": "note"
          },
          {
            "id": "552",
            "type": "note"
          }
        ]
      },
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "f79d1512-889f-4df8-96e3-bd611ed53f75",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Reset an absence


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/absences/57/absences_resettings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/absences/:absence_id/absences_resettings`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "57",
    "type": "absence",
    "attributes": {
      "permissions": null,
      "title": "Holiday 1_759",
      "hours": 0.0,
      "days": 1.0,
      "full_day": true,
      "confirmation_status": "rejected",
      "confirmed": false,
      "created_by": null,
      "use_custom_values": false,
      "external_id": null,
      "confirm_message": null,
      "attachments_count": 0,
      "starts_at": "2023-01-29T23:00:00Z",
      "ends_at": "2023-01-30T22:59:59Z",
      "confirmed_at": null,
      "created_at": "2023-01-30T11:22:58Z",
      "updated_at": "2023-01-30T11:22:58Z",
      "system_notes_count": 2,
      "user_notes_count": 0
    },
    "relationships": {
      "absence_type": {
        "data": {
          "id": "1028",
          "type": "absence_type"
        }
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "confirmed_by_user": {
        "data": null
      },
      "followers": {
        "data": [

        ]
      },
      "notes": {
        "data": [
          {
            "id": "554",
            "type": "note"
          },
          {
            "id": "555",
            "type": "note"
          }
        ]
      },
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "8759b66e-d6a8-4f6a-a155-1b03c2156cb8",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Show absence


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absences/59?include=absence_type%2C+user
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absences/:absence_id`

#### Parameters


```json
include: absence_type, user
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "59",
    "type": "absence",
    "attributes": {
      "permissions": null,
      "title": "Holiday 1_759",
      "hours": 0.0,
      "days": 1.0,
      "full_day": true,
      "confirmation_status": "confirmed",
      "confirmed": true,
      "created_by": null,
      "use_custom_values": false,
      "external_id": null,
      "confirm_message": null,
      "attachments_count": 1,
      "starts_at": "2023-01-29T23:00:00Z",
      "ends_at": "2023-01-30T22:59:59Z",
      "confirmed_at": "2023-01-30T11:22:58Z",
      "created_at": "2023-01-30T11:22:58Z",
      "updated_at": "2023-01-30T11:22:59Z",
      "system_notes_count": 1,
      "user_notes_count": 1
    },
    "relationships": {
      "absence_type": {
        "data": {
          "id": "1028",
          "type": "absence_type"
        }
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "confirmed_by_user": {
        "data": null
      },
      "followers": {
        "data": [
          {
            "id": "105",
            "type": "user_overview"
          }
        ]
      },
      "notes": {
        "data": [
          {
            "id": "557",
            "type": "note"
          },
          {
            "id": "558",
            "type": "note"
          }
        ]
      },
      "attachments": {
        "data": [
          {
            "id": "6",
            "type": "attachment"
          }
        ]
      }
    }
  },
  "meta": {
    "request_id": "09df01ea-3bf8-4027-a607-2df5ae80ee46",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "1028",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 1_759",
        "kind": "vacation"
      }
    },
    {
      "id": "40",
      "type": "user_overview",
      "attributes": {
        "permissions": null,
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz",
        "abbreviation": null,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "status": "active"
      }
    }
  ]
}
```



## Update an absence


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/absences/62
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/absences/:absence_id`

#### Parameters


```json
{"data":{"type":"absence","attributes":{"full_day":true,"force_calc_custom_hours":true,"hours":5.0,"days":1.0,"starts_at":"2023-01-30T00:00:00+01:00","ends_at":"2023-01-30T23:59:59+01:00","notes_attributes":[{"id":564,"content":"new content"},{"id":565,"_destroy":true}]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| absence_id *required* | Absence ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "62",
    "type": "absence",
    "attributes": {
      "permissions": null,
      "title": "Holiday 1_759",
      "hours": 5.0,
      "days": 1.0,
      "full_day": true,
      "confirmation_status": "pending",
      "confirmed": null,
      "created_by": null,
      "use_custom_values": true,
      "external_id": null,
      "confirm_message": null,
      "attachments_count": 0,
      "starts_at": "2023-01-29T23:00:00Z",
      "ends_at": "2023-01-30T22:59:59Z",
      "confirmed_at": null,
      "created_at": "2023-01-30T11:22:59Z",
      "updated_at": "2023-01-30T11:22:59Z",
      "system_notes_count": 3,
      "user_notes_count": 1
    },
    "relationships": {
      "absence_type": {
        "data": {
          "id": "1028",
          "type": "absence_type"
        }
      },
      "user": {
        "data": {
          "id": "40",
          "type": "user_overview"
        }
      },
      "confirmed_by_user": {
        "data": null
      },
      "followers": {
        "data": [
          {
            "id": "108",
            "type": "user_overview"
          },
          {
            "id": "109",
            "type": "user_overview"
          }
        ]
      },
      "notes": {
        "data": [
          {
            "id": "563",
            "type": "note"
          },
          {
            "id": "566",
            "type": "note"
          },
          {
            "id": "564",
            "type": "note"
          },
          {
            "id": "567",
            "type": "note"
          }
        ]
      },
      "attachments": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "93179555-9533-4141-926f-34c4a8ff1ab6",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```

# Workspaces/AbsenceTypes

## All types of admins can access list of absence_types


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absence_types
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absence_types`

#### Parameters



| Name | Description |
|:-----|:------------|
| filter  | Filter |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "1028",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 1_759",
        "kind": "vacation"
      }
    },
    {
      "id": "1044",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 17_582",
        "kind": "vacation"
      }
    }
  ],
  "meta": {
    "request_id": "62d00d15-98d6-4472-9fe8-919c6a9142fb",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2
  }
}
```



## Filtering by users


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absence_types?filter[users_id_in][]=39
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absence_types`

#### Parameters


```json
filter: {&quot;users_id_in&quot;=&gt;[&quot;39&quot;]}
```


| Name | Description |
|:-----|:------------|
| filter  | Filter |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "1028",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 1_759",
        "kind": "vacation"
      }
    }
  ],
  "meta": {
    "request_id": "e5e5715b-b05d-40a2-a336-36792209a579",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Filtering by users


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/absence_types?filter[users_id_in][]=9999
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absence_types`

#### Parameters


```json
filter: {&quot;users_id_in&quot;=&gt;[&quot;9999&quot;]}
```


| Name | Description |
|:-----|:------------|
| filter  | Filter |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 0
200 OK
```


```json
{
  "data": [

  ],
  "meta": {
    "request_id": "a4ace5b9-463c-4444-9992-fe76091fce03",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 0
  }
}
```



## Filtering by intersecting users


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1054/absence_types?filter[intersecting_users][]=75&amp;filter[intersecting_users][]=76
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absence_types`

#### Parameters


```json
filter: {&quot;intersecting_users&quot;=&gt;[&quot;75&quot;, &quot;76&quot;]}
```


| Name | Description |
|:-----|:------------|
| filter  | Filter |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "1049",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 22_236",
        "kind": "vacation"
      }
    }
  ],
  "meta": {
    "request_id": "4a931600-3d43-4010-9fa2-676a015a2ef2",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Filtering by intersecting users


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1056/absence_types?filter[intersecting_users][]=0
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/absence_types`

#### Parameters


```json
filter: {&quot;intersecting_users&quot;=&gt;[&quot;0&quot;]}
```


| Name | Description |
|:-----|:------------|
| filter  | Filter |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 0
200 OK
```


```json
{
  "data": [

  ],
  "meta": {
    "request_id": "b5c017c4-e8c7-4fed-b531-6837e373f62a",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 0
  }
}
```


# Workspaces/Areas

## returns 201 status and data for the working area created


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/areas
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/areas`

#### Parameters


```json
{"data":{"attributes":{"color":"#A2DED0","name":"Example"},"type":"area"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "1030",
    "type": "area",
    "attributes": {
      "permissions": null,
      "name": "Example",
      "status": "active",
      "color": "#A2DED0",
      "external_id": null,
      "created_at": "2023-01-30T11:22:15Z",
      "updated_at": "2023-01-30T11:22:15Z"
    },
    "relationships": {
      "users": {
        "data": [

        ]
      },
      "areas": {
        "data": [

        ]
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "c7eee767-5b83-4478-b8d6-770d9f5e53c7",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Create working area using existing working areas


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/areas
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/areas`

#### Parameters


```json
{"data":{"attributes":{"color":"#A2DED0","name":"Example","area_ids":[1031,1032]},"type":"area"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "1033",
    "type": "area",
    "attributes": {
      "permissions": null,
      "name": "Example",
      "status": "active",
      "color": "#A2DED0",
      "external_id": null,
      "created_at": "2023-01-30T11:22:15Z",
      "updated_at": "2023-01-30T11:22:15Z"
    },
    "relationships": {
      "users": {
        "data": [
          {
            "id": "40",
            "type": "user"
          },
          {
            "id": "39",
            "type": "user"
          }
        ]
      },
      "areas": {
        "data": [

        ]
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "80fe84e3-c878-4970-a2e0-c121d246becd",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Create working area using existing users


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/areas
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/areas`

#### Parameters


```json
{"data":{"attributes":{"color":"#A2DED0","name":"Example","user_ids":[40,39]},"type":"area"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "1034",
    "type": "area",
    "attributes": {
      "permissions": null,
      "name": "Example",
      "status": "active",
      "color": "#A2DED0",
      "external_id": null,
      "created_at": "2023-01-30T11:22:16Z",
      "updated_at": "2023-01-30T11:22:16Z"
    },
    "relationships": {
      "users": {
        "data": [
          {
            "id": "40",
            "type": "user"
          },
          {
            "id": "39",
            "type": "user"
          }
        ]
      },
      "areas": {
        "data": [

        ]
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "95da9baf-390f-48ad-aafe-24caa4c534d2",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Create working area using existing users and working areas


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/areas
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/areas`

#### Parameters


```json
{"data":{"attributes":{"color":"#A2DED0","name":"Example","user_ids":[40,39],"area_ids":[1035,1036]},"type":"area"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "1037",
    "type": "area",
    "attributes": {
      "permissions": null,
      "name": "Example",
      "status": "active",
      "color": "#A2DED0",
      "external_id": null,
      "created_at": "2023-01-30T11:22:16Z",
      "updated_at": "2023-01-30T11:22:16Z"
    },
    "relationships": {
      "users": {
        "data": [
          {
            "id": "40",
            "type": "user"
          },
          {
            "id": "39",
            "type": "user"
          }
        ]
      },
      "areas": {
        "data": [

        ]
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "697ac037-66c9-4cf7-b776-0aa7b62b9f01",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Duplicated names return 422 status and errors


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/areas
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/areas`

#### Parameters


```json
{"data":{"attributes":{"color":"#A2DED0","name":"WA 1"},"type":"area"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "name"
      },
      "title": "has already been taken"
    }
  ]
}
```



## Empty body returns 422 status and errors


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/areas
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/areas`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "bad_request",
      "source": {
        "pointer": "base"
      },
      "title": "Param 'area' is missing or empty."
    }
  ]
}
```



## returns an authorization error for employee


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/areas
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/areas`

#### Parameters


```json
{"data":{"attributes":{"color":"#A2DED0","name":"Example"},"type":"area"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## returns an authorization error for unauthenticated user


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/areas
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/areas`

#### Parameters


```json
{"data":{"attributes":{"color":"#A2DED0","name":"Example"},"type":"area"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
401 Unauthorized
```


```json
{
  "errors": [
    {
      "status": "unauthorized",
      "source": {
        "pointer": "base"
      },
      "title": "You need to sign in or sign up before continuing."
    }
  ]
}
```



## Deletes an area


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/areas/1039
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/areas/:area_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| area_id *required* | Area ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1039",
    "type": "area",
    "attributes": {
      "permissions": null,
      "name": "foo",
      "status": "active",
      "color": "#f1c40f",
      "external_id": null,
      "created_at": "2023-01-30T11:22:16Z",
      "updated_at": "2023-01-30T11:22:16Z"
    },
    "relationships": {
      "users": {
        "data": [

        ]
      },
      "areas": {
        "data": [

        ]
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "900b3c5a-9623-426f-88f1-97663ec5013c",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Index


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/areas
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/areas`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| permissions  | User Permissions |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "1028",
      "type": "area",
      "attributes": {
        "permissions": null,
        "name": "Lorenz vom Wollmann",
        "status": "active",
        "color": "#913D88",
        "external_id": null,
        "created_at": "2023-01-30T11:21:43Z",
        "updated_at": "2023-01-30T11:21:43Z"
      },
      "relationships": {
        "users": {
          "data": [
            {
              "id": "40",
              "type": "user"
            },
            {
              "id": "42",
              "type": "user"
            },
            {
              "id": "43",
              "type": "user"
            }
          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    },
    {
      "id": "1040",
      "type": "area",
      "attributes": {
        "permissions": null,
        "name": "Carlee Langosh",
        "status": "active",
        "color": "#f39c12",
        "external_id": null,
        "created_at": "2023-01-30T11:22:17Z",
        "updated_at": "2023-01-30T11:22:17Z"
      },
      "relationships": {
        "users": {
          "data": [
            {
              "id": "40",
              "type": "user"
            }
          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    }
  ],
  "meta": {
    "request_id": "ebc68b96-b2b8-4694-b701-d1dee6dd6363",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2,
    "can_create_working_areas": false
  }
}
```



## With Permissions


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/areas?permissions=read%2C+update
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/areas`

#### Parameters


```json
permissions: read, update
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| permissions  | User Permissions |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "1028",
      "type": "area",
      "attributes": {
        "permissions": {
          "read": true,
          "update": false
        },
        "name": "Lorenz vom Wollmann",
        "status": "active",
        "color": "#913D88",
        "external_id": null,
        "created_at": "2023-01-30T11:21:43Z",
        "updated_at": "2023-01-30T11:21:43Z"
      },
      "relationships": {
        "users": {
          "data": [
            {
              "id": "40",
              "type": "user"
            },
            {
              "id": "42",
              "type": "user"
            },
            {
              "id": "43",
              "type": "user"
            }
          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    },
    {
      "id": "1041",
      "type": "area",
      "attributes": {
        "permissions": {
          "read": true,
          "update": false
        },
        "name": "Pearl Considine",
        "status": "active",
        "color": "#16a085",
        "external_id": null,
        "created_at": "2023-01-30T11:22:17Z",
        "updated_at": "2023-01-30T11:22:17Z"
      },
      "relationships": {
        "users": {
          "data": [
            {
              "id": "40",
              "type": "user"
            }
          ]
        },
        "areas": {
          "data": [

          ]
        },
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        }
      }
    }
  ],
  "meta": {
    "request_id": "a1187d97-0e8d-4083-8f35-a6d3689f6c9f",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2,
    "can_create_working_areas": false
  }
}
```



## Area Details


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/areas/1043?include=users%2C+workspace
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/areas/:area_id`

#### Parameters


```json
include: users, workspace
```


| Name | Description |
|:-----|:------------|
| include  | Relationships details |
| workspace_id *required* | Workspace ID |
| area_id *required* | Area ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1043",
    "type": "area",
    "attributes": {
      "permissions": null,
      "name": "Rickie Hamill",
      "status": "active",
      "color": "#9b59b6",
      "external_id": null,
      "created_at": "2023-01-30T11:22:17Z",
      "updated_at": "2023-01-30T11:22:17Z"
    },
    "relationships": {
      "users": {
        "data": [
          {
            "id": "40",
            "type": "user"
          }
        ]
      },
      "areas": {
        "data": [

        ]
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "17354dec-dc13-44aa-a296-da1ba6231e72",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "40",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2022-12-30",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 8,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "17hs",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            },
            {
              "id": "1043",
              "type": "area"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": null,
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            },
            {
              "id": "1043",
              "type": "area"
            }
          ]
        }
      }
    }
  ]
}
```



## Area details including users


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/areas/1044?include=users
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/areas/:area_id`

#### Parameters


```json
include: users
```


| Name | Description |
|:-----|:------------|
| include  | Included relationships |
| workspace_id *required* | Workspace ID |
| area_id *required* | Area ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1044",
    "type": "area",
    "attributes": {
      "permissions": null,
      "name": "Missy Hackett",
      "status": "active",
      "color": "#e67e22",
      "external_id": null,
      "created_at": "2023-01-30T11:22:18Z",
      "updated_at": "2023-01-30T11:22:18Z"
    },
    "relationships": {
      "users": {
        "data": [
          {
            "id": "40",
            "type": "user"
          }
        ]
      },
      "areas": {
        "data": [

        ]
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "530eb41a-4571-49a5-84cc-c758993d607a",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [
    {
      "id": "40",
      "type": "user",
      "attributes": {
        "permissions": null,
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2022-12-30",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 8,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "17hs",
        "locale": null,
        "status": "active",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            },
            {
              "id": "1044",
              "type": "area"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        }
      }
    }
  ]
}
```



## returns 200 status with the relationships but no user attributes


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/areas/1045?include=
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/areas/:area_id`

#### Parameters


```json
include: 
```


| Name | Description |
|:-----|:------------|
| include  | Included relationships |
| workspace_id *required* | Workspace ID |
| area_id *required* | Area ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1045",
    "type": "area",
    "attributes": {
      "permissions": null,
      "name": "Numbers Daugherty",
      "status": "active",
      "color": "#e74c3c",
      "external_id": null,
      "created_at": "2023-01-30T11:22:18Z",
      "updated_at": "2023-01-30T11:22:18Z"
    },
    "relationships": {
      "users": {
        "data": [
          {
            "id": "40",
            "type": "user"
          }
        ]
      },
      "areas": {
        "data": [

        ]
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "8d3c796f-2eb5-42d2-ab2c-1dac0ee5ac3b",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## returns server error


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/areas/1046?include=use
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/areas/:area_id`

#### Parameters


```json
include: use
```


| Name | Description |
|:-----|:------------|
| include  | Included relationships |
| workspace_id *required* | Workspace ID |
| area_id *required* | Area ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
500 Internal Server Error
```


```json
{
  "errors": [
    {
      "status": "internal_server_error",
      "source": {
        "pointer": "base"
      },
      "title": "Included param 'use' is not yet implemented."
    }
  ]
}
```



## returns 200 status and no users


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/areas/1047?include=users
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/areas/:area_id`

#### Parameters


```json
include: users
```


| Name | Description |
|:-----|:------------|
| include  | Included relationships |
| workspace_id *required* | Workspace ID |
| area_id *required* | Area ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1047",
    "type": "area",
    "attributes": {
      "permissions": null,
      "name": "Clare Kertzmann",
      "status": "active",
      "color": "#95a5a6",
      "external_id": null,
      "created_at": "2023-01-30T11:22:18Z",
      "updated_at": "2023-01-30T11:22:18Z"
    },
    "relationships": {
      "users": {
        "data": [

        ]
      },
      "areas": {
        "data": [

        ]
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "10d07383-73e6-4584-84fe-83b03f4d8748",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  },
  "included": [

  ]
}
```



## not allowed to access area users


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/areas/1048?include=users
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/areas/:area_id`

#### Parameters


```json
include: users
```


| Name | Description |
|:-----|:------------|
| include  | Included relationships |
| workspace_id *required* | Workspace ID |
| area_id *required* | Area ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Update an area


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/areas/1049
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/areas/:area_id`

#### Parameters


```json
{"data":{"attributes":{"color":"#1abc9c","name":"Another name","user_ids":[40,39]},"type":"area"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| area_id *required* | Area ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "1049",
    "type": "area",
    "attributes": {
      "permissions": null,
      "name": "Another name",
      "status": "active",
      "color": "#1abc9c",
      "external_id": null,
      "created_at": "2023-01-30T11:22:19Z",
      "updated_at": "2023-01-30T11:22:19Z"
    },
    "relationships": {
      "users": {
        "data": [
          {
            "id": "40",
            "type": "user"
          },
          {
            "id": "39",
            "type": "user"
          }
        ]
      },
      "areas": {
        "data": [

        ]
      },
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      }
    }
  },
  "meta": {
    "request_id": "841ddd74-2c96-401f-a420-ddd2d320e160",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Employee is not allowed to edit areas


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/areas/1050
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/areas/:area_id`

#### Parameters


```json
{"data":{"attributes":{"color":"#1abc9c","name":"Another name","user_ids":[40,39]},"type":"area"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| area_id *required* | Area ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



# Workspaces/Features


## returns an authorization error


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/features
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/features`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
401 Unauthorized
```


```json
{
  "errors": [
    {
      "status": "unauthorized",
      "source": {
        "pointer": "base"
      },
      "title": "You need to sign in or sign up before continuing."
    }
  ]
}
```



## returns 200 and has account admin&#39;s active_modules


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/features
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/features`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": [
    {
      "id": "75641c8a-8ca6-11eb-8dcd-0242ac130003 ",
      "type": "feature",
      "attributes": {
        "hint": "WorkspaceUser",
        "permissions": {
          "read_index": true,
          "create_workspace_users": true
        }
      }
    },
    {
      "id": "95e6db1c-a1dc-4f3b-ad6a-a2651c59ca81",
      "type": "feature",
      "attributes": {
        "hint": "Absence",
        "permissions": {
          "read_index": true,
          "create_absences": true
        }
      }
    },
    {
      "id": "ad91901b-4e09-4c74-8c91-87daf1058e35",
      "type": "feature",
      "attributes": {
        "hint": "TimeTracking",
        "permissions": {
          "use_browser_punch_clock": false,
          "read_index": true,
          "create_time_tracking": true
        }
      }
    },
    {
      "id": "cfb7843c-377f-4803-9304-b26b7bc212be",
      "type": "feature",
      "attributes": {
        "hint": "Workflow",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "46e419fd-3e45-44fa-95e2-14372664d4ee",
      "type": "feature",
      "attributes": {
        "hint": "Evaluation",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "3d4b9365-1175-46c2-b7c1-2f1c0242699e",
      "type": "feature",
      "attributes": {
        "hint": "Export",
        "permissions": {
          "read_index": true,
          "create_export": true
        }
      }
    },
    {
      "id": "0792c2f7-b90c-4db8-8d79-e9c65d4608cd",
      "type": "feature",
      "attributes": {
        "hint": "Internationalization",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "69303d65-8a39-44f9-b8bc-8bc993520e91",
      "type": "feature",
      "attributes": {
        "hint": "EmployeeSegmentation",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "0fb78c7f-1ea6-4f0a-8cb4-7a048f5f17ee",
      "type": "feature",
      "attributes": {
        "hint": "UserSkill",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "7045d096-b234-4793-861c-c813d0eae747",
      "type": "feature",
      "attributes": {
        "hint": "Archive",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "54a59364-a0f9-4235-92c9-400bb675c23a",
      "type": "feature",
      "attributes": {
        "hint": "UserSpecificPause",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "98a2b423-fefa-4d55-afb7-ffa52a0fee6d",
      "type": "feature",
      "attributes": {
        "hint": "WorkSchedule",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "8bc5ba1f-31c2-4ab2-9971-8e978ae87375",
      "type": "feature",
      "attributes": {
        "hint": "RightRole",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "4e776224-0e7d-4c59-a71e-4765be8799f3",
      "type": "feature",
      "attributes": {
        "hint": "Import",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "8c3989fc-6ded-4709-b545-18f1e1e0c8a8",
      "type": "feature",
      "attributes": {
        "hint": "AccountExport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d8541d49-f833-4ba3-97a9-45166bdf2214",
      "type": "feature",
      "attributes": {
        "hint": "ExtendedCompanyUserRight",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "636e3a90-6750-4a9b-a380-c80bc596bc11",
      "type": "feature",
      "attributes": {
        "hint": "UserBasedPublicHoliday",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "84d56e49-ec38-4907-9256-232591e5037e",
      "type": "feature",
      "attributes": {
        "hint": "ExtendedAbsenceType",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "6afcfc94-1ee0-4f13-baad-f7b4d4bd6037",
      "type": "feature",
      "attributes": {
        "hint": "LocationTemplate",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "f7fe1493-f279-45e2-95fa-f4095152f6be",
      "type": "feature",
      "attributes": {
        "hint": "NetBreak",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "bc656e6b-9e67-4ce6-be41-8a8e9421cde1",
      "type": "feature",
      "attributes": {
        "hint": "VacationBan",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "bb3b58e2-64a9-4fb2-bdc6-d258b7ace8eb",
      "type": "feature",
      "attributes": {
        "hint": "AssignAutomatically",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d95e2100-7151-4aad-b5a5-589f0e1baca0",
      "type": "feature",
      "attributes": {
        "hint": "Payroll",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d8ed7701-fea6-40f4-9363-8ecdc7e8a72f",
      "type": "feature",
      "attributes": {
        "hint": "WageType",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "65415889-67c6-48c0-97eb-9282314c0134",
      "type": "feature",
      "attributes": {
        "hint": "Report",
        "permissions": {
          "read_index": true,
          "create_report": true
        }
      }
    },
    {
      "id": "a61e0ee6-6683-4f12-9335-fbd9adb287cc",
      "type": "feature",
      "attributes": {
        "hint": "EmployeeReport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "fbac64c5-25bb-4ea6-8c2b-ad39c20f0d59",
      "type": "feature",
      "attributes": {
        "hint": "FileTemplate",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "688fb157-2cd9-4bfa-8d3e-15313d296b48",
      "type": "feature",
      "attributes": {
        "hint": "Upload",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d19a2988-dc00-4658-9f6f-d58de840837a",
      "type": "feature",
      "attributes": {
        "hint": "UploadIndex",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "f5f46141-39d2-401b-bb98-d3d4a2bcaa3e",
      "type": "feature",
      "attributes": {
        "hint": "AccountUser",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "11a8c4c4-6796-42d2-bfd1-5370d11260a8",
      "type": "feature",
      "attributes": {
        "hint": "Hr",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "9d22cddf-255b-43ca-ad94-dc2814813546",
      "type": "feature",
      "attributes": {
        "hint": "UserCheckin",
        "permissions": {
          "read": true
        }
      }
    },
    {
      "id": "c614ad7b-8ecc-47d3-a441-061bb080a351",
      "type": "feature",
      "attributes": {
        "hint": "CustomField",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "b681e42a-6734-466b-a830-0367a103c147",
      "type": "feature",
      "attributes": {
        "hint": "DataProfilesRole",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "f189083b-d4b5-43d8-8413-486baac0d654",
      "type": "feature",
      "attributes": {
        "hint": "Task",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d0ab51cc-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "PushNotification",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "e0695ca2-5fe8-4795-b261-783ab5b1d218",
      "type": "feature",
      "attributes": {
        "hint": "WorkingSessionActionsExport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "b11733fd-40d7-4e16-8352-ce84c6f36bd3",
      "type": "feature",
      "attributes": {
        "hint": "HostedPage",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "9b4e4cdb-74d9-46bd-a066-851716d7efcd",
      "type": "feature",
      "attributes": {
        "hint": "ConfirmAssignment",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "1aecd2d7-11cb-4b44-a0fc-bb912360b224",
      "type": "feature",
      "attributes": {
        "hint": "Search",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "06a89ee9-83ed-4a93-a414-7f9feb747b5b",
      "type": "feature",
      "attributes": {
        "hint": "BrowserClockViaAction",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "54c10d4e-758d-4bd0-b1e2-e4a01eb5b671",
      "type": "feature",
      "attributes": {
        "hint": "WorkspaceSetting",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "06a89ee9-83ed-4a93-a414-7f9feb747b5b",
      "type": "feature",
      "attributes": {
        "hint": "BrowserClockViaAction",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "957554f4-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "UserProfileNote",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "a9528eb0-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "AdvancedPayrollExport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d0ab51cc-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "PushNotification",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "daed51c6-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "EmployeeReportsInUsersIndex",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "e0695ca2-5fe8-4795-b261-783ab5b1d218",
      "type": "feature",
      "attributes": {
        "hint": "WorkingSessionActionsExport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "e129c506-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "TaskGuest",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "75641c8a-8ca6-11eb-8dcd-0242ac130003 ",
      "type": "feature",
      "attributes": {
        "hint": "WorkspaceUser",
        "permissions": {
          "read_index": true,
          "create_workspace_users": true
        }
      }
    },
    {
      "id": "77062197-48e9-456f-ae97-0136f40a7585",
      "type": "feature",
      "attributes": {
        "hint": "TargetHour",
        "permissions": {
          "create_custom_target_hours": false
        }
      }
    },
    {
      "id": "5c398c9c-7985-4692-89d7-47dc894e3974",
      "type": "feature",
      "attributes": {
        "hint": "Tag",
        "permissions": {
          "allow_employees_to_create_tags": false,
          "allow_employees_to_create_time_tracking_tags": false
        }
      }
    },
    {
      "id": "8fdca481-2a60-4b14-9add-cace7cb26422",
      "type": "feature",
      "attributes": {
        "hint": "Profile",
        "permissions": {
          "free_subscription": false
        }
      }
    },
    {
      "id": "b5464d2a-5a81-4959-8ece-02d34fa98b46",
      "type": "feature",
      "attributes": {
        "hint": "General",
        "permissions": {
          "show_system_notes": true
        }
      }
    },
    {
      "id": "6bea72b2-6b44-481c-b550-2c5b388d7d07",
      "type": "feature",
      "attributes": {
        "hint": "Analytic",
        "permissions": {
          "allow_segment": true
        }
      }
    },
    {
      "id": "51ea28ca-4b23-4436-8cd3-98535b0b99c8",
      "type": "feature",
      "attributes": {
        "hint": "Calendar",
        "permissions": {
          "read_index": true
        }
      }
    }
  ]
}
```



## returns 200 and has usercheckin feature


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/features
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/features`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": [
    {
      "id": "75641c8a-8ca6-11eb-8dcd-0242ac130003 ",
      "type": "feature",
      "attributes": {
        "hint": "WorkspaceUser",
        "permissions": {
          "read_index": true,
          "create_workspace_users": true
        }
      }
    },
    {
      "id": "95e6db1c-a1dc-4f3b-ad6a-a2651c59ca81",
      "type": "feature",
      "attributes": {
        "hint": "Absence",
        "permissions": {
          "read_index": true,
          "create_absences": true
        }
      }
    },
    {
      "id": "ad91901b-4e09-4c74-8c91-87daf1058e35",
      "type": "feature",
      "attributes": {
        "hint": "TimeTracking",
        "permissions": {
          "use_browser_punch_clock": false,
          "read_index": true,
          "create_time_tracking": true
        }
      }
    },
    {
      "id": "cfb7843c-377f-4803-9304-b26b7bc212be",
      "type": "feature",
      "attributes": {
        "hint": "Workflow",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "46e419fd-3e45-44fa-95e2-14372664d4ee",
      "type": "feature",
      "attributes": {
        "hint": "Evaluation",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "3d4b9365-1175-46c2-b7c1-2f1c0242699e",
      "type": "feature",
      "attributes": {
        "hint": "Export",
        "permissions": {
          "read_index": true,
          "create_export": true
        }
      }
    },
    {
      "id": "0792c2f7-b90c-4db8-8d79-e9c65d4608cd",
      "type": "feature",
      "attributes": {
        "hint": "Internationalization",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "69303d65-8a39-44f9-b8bc-8bc993520e91",
      "type": "feature",
      "attributes": {
        "hint": "EmployeeSegmentation",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "0fb78c7f-1ea6-4f0a-8cb4-7a048f5f17ee",
      "type": "feature",
      "attributes": {
        "hint": "UserSkill",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "7045d096-b234-4793-861c-c813d0eae747",
      "type": "feature",
      "attributes": {
        "hint": "Archive",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "54a59364-a0f9-4235-92c9-400bb675c23a",
      "type": "feature",
      "attributes": {
        "hint": "UserSpecificPause",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "98a2b423-fefa-4d55-afb7-ffa52a0fee6d",
      "type": "feature",
      "attributes": {
        "hint": "WorkSchedule",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "8bc5ba1f-31c2-4ab2-9971-8e978ae87375",
      "type": "feature",
      "attributes": {
        "hint": "RightRole",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "4e776224-0e7d-4c59-a71e-4765be8799f3",
      "type": "feature",
      "attributes": {
        "hint": "Import",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "8c3989fc-6ded-4709-b545-18f1e1e0c8a8",
      "type": "feature",
      "attributes": {
        "hint": "AccountExport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d8541d49-f833-4ba3-97a9-45166bdf2214",
      "type": "feature",
      "attributes": {
        "hint": "ExtendedCompanyUserRight",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "636e3a90-6750-4a9b-a380-c80bc596bc11",
      "type": "feature",
      "attributes": {
        "hint": "UserBasedPublicHoliday",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "84d56e49-ec38-4907-9256-232591e5037e",
      "type": "feature",
      "attributes": {
        "hint": "ExtendedAbsenceType",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "6afcfc94-1ee0-4f13-baad-f7b4d4bd6037",
      "type": "feature",
      "attributes": {
        "hint": "LocationTemplate",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "f7fe1493-f279-45e2-95fa-f4095152f6be",
      "type": "feature",
      "attributes": {
        "hint": "NetBreak",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "bc656e6b-9e67-4ce6-be41-8a8e9421cde1",
      "type": "feature",
      "attributes": {
        "hint": "VacationBan",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "bb3b58e2-64a9-4fb2-bdc6-d258b7ace8eb",
      "type": "feature",
      "attributes": {
        "hint": "AssignAutomatically",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d95e2100-7151-4aad-b5a5-589f0e1baca0",
      "type": "feature",
      "attributes": {
        "hint": "Payroll",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d8ed7701-fea6-40f4-9363-8ecdc7e8a72f",
      "type": "feature",
      "attributes": {
        "hint": "WageType",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "65415889-67c6-48c0-97eb-9282314c0134",
      "type": "feature",
      "attributes": {
        "hint": "Report",
        "permissions": {
          "read_index": true,
          "create_report": true
        }
      }
    },
    {
      "id": "a61e0ee6-6683-4f12-9335-fbd9adb287cc",
      "type": "feature",
      "attributes": {
        "hint": "EmployeeReport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "fbac64c5-25bb-4ea6-8c2b-ad39c20f0d59",
      "type": "feature",
      "attributes": {
        "hint": "FileTemplate",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "688fb157-2cd9-4bfa-8d3e-15313d296b48",
      "type": "feature",
      "attributes": {
        "hint": "Upload",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d19a2988-dc00-4658-9f6f-d58de840837a",
      "type": "feature",
      "attributes": {
        "hint": "UploadIndex",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "f5f46141-39d2-401b-bb98-d3d4a2bcaa3e",
      "type": "feature",
      "attributes": {
        "hint": "AccountUser",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "11a8c4c4-6796-42d2-bfd1-5370d11260a8",
      "type": "feature",
      "attributes": {
        "hint": "Hr",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "9d22cddf-255b-43ca-ad94-dc2814813546",
      "type": "feature",
      "attributes": {
        "hint": "UserCheckin",
        "permissions": {
          "read": true
        }
      }
    },
    {
      "id": "c614ad7b-8ecc-47d3-a441-061bb080a351",
      "type": "feature",
      "attributes": {
        "hint": "CustomField",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "b681e42a-6734-466b-a830-0367a103c147",
      "type": "feature",
      "attributes": {
        "hint": "DataProfilesRole",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "f189083b-d4b5-43d8-8413-486baac0d654",
      "type": "feature",
      "attributes": {
        "hint": "Task",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d0ab51cc-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "PushNotification",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "e0695ca2-5fe8-4795-b261-783ab5b1d218",
      "type": "feature",
      "attributes": {
        "hint": "WorkingSessionActionsExport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "b11733fd-40d7-4e16-8352-ce84c6f36bd3",
      "type": "feature",
      "attributes": {
        "hint": "HostedPage",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "9b4e4cdb-74d9-46bd-a066-851716d7efcd",
      "type": "feature",
      "attributes": {
        "hint": "ConfirmAssignment",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "1aecd2d7-11cb-4b44-a0fc-bb912360b224",
      "type": "feature",
      "attributes": {
        "hint": "Search",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "06a89ee9-83ed-4a93-a414-7f9feb747b5b",
      "type": "feature",
      "attributes": {
        "hint": "BrowserClockViaAction",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "54c10d4e-758d-4bd0-b1e2-e4a01eb5b671",
      "type": "feature",
      "attributes": {
        "hint": "WorkspaceSetting",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "06a89ee9-83ed-4a93-a414-7f9feb747b5b",
      "type": "feature",
      "attributes": {
        "hint": "BrowserClockViaAction",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "957554f4-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "UserProfileNote",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "a9528eb0-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "AdvancedPayrollExport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d0ab51cc-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "PushNotification",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "daed51c6-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "EmployeeReportsInUsersIndex",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "e0695ca2-5fe8-4795-b261-783ab5b1d218",
      "type": "feature",
      "attributes": {
        "hint": "WorkingSessionActionsExport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "e129c506-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "TaskGuest",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "75641c8a-8ca6-11eb-8dcd-0242ac130003 ",
      "type": "feature",
      "attributes": {
        "hint": "WorkspaceUser",
        "permissions": {
          "read_index": true,
          "create_workspace_users": true
        }
      }
    },
    {
      "id": "77062197-48e9-456f-ae97-0136f40a7585",
      "type": "feature",
      "attributes": {
        "hint": "TargetHour",
        "permissions": {
          "create_custom_target_hours": false
        }
      }
    },
    {
      "id": "5c398c9c-7985-4692-89d7-47dc894e3974",
      "type": "feature",
      "attributes": {
        "hint": "Tag",
        "permissions": {
          "allow_employees_to_create_tags": false,
          "allow_employees_to_create_time_tracking_tags": false
        }
      }
    },
    {
      "id": "8fdca481-2a60-4b14-9add-cace7cb26422",
      "type": "feature",
      "attributes": {
        "hint": "Profile",
        "permissions": {
          "free_subscription": false
        }
      }
    },
    {
      "id": "b5464d2a-5a81-4959-8ece-02d34fa98b46",
      "type": "feature",
      "attributes": {
        "hint": "General",
        "permissions": {
          "show_system_notes": true
        }
      }
    },
    {
      "id": "6bea72b2-6b44-481c-b550-2c5b388d7d07",
      "type": "feature",
      "attributes": {
        "hint": "Analytic",
        "permissions": {
          "allow_segment": true
        }
      }
    },
    {
      "id": "51ea28ca-4b23-4436-8cd3-98535b0b99c8",
      "type": "feature",
      "attributes": {
        "hint": "Calendar",
        "permissions": {
          "read_index": true
        }
      }
    }
  ]
}
```



## returns 200 and has employees active_modules


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/features
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/features`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": [
    {
      "id": "95e6db1c-a1dc-4f3b-ad6a-a2651c59ca81",
      "type": "feature",
      "attributes": {
        "hint": "Absence",
        "permissions": {
          "read_index": true,
          "create_absences": true
        }
      }
    },
    {
      "id": "ad91901b-4e09-4c74-8c91-87daf1058e35",
      "type": "feature",
      "attributes": {
        "hint": "TimeTracking",
        "permissions": {
          "use_browser_punch_clock": false,
          "read_index": true,
          "create_time_tracking": true
        }
      }
    },
    {
      "id": "8fdca481-2a60-4b14-9add-cace7cb26422",
      "type": "feature",
      "attributes": {
        "hint": "Profile",
        "permissions": {
          "free_subscription": false
        }
      }
    },
    {
      "id": "b5464d2a-5a81-4959-8ece-02d34fa98b46",
      "type": "feature",
      "attributes": {
        "hint": "General",
        "permissions": {
          "show_system_notes": true
        }
      }
    },
    {
      "id": "6bea72b2-6b44-481c-b550-2c5b388d7d07",
      "type": "feature",
      "attributes": {
        "hint": "Analytic",
        "permissions": {
          "allow_segment": true
        }
      }
    },
    {
      "id": "51ea28ca-4b23-4436-8cd3-98535b0b99c8",
      "type": "feature",
      "attributes": {
        "hint": "Calendar",
        "permissions": {
          "read_index": true
        }
      }
    }
  ]
}
```



## returns 200 and has employees active_modules


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/features
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/features`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": [
    {
      "id": "95e6db1c-a1dc-4f3b-ad6a-a2651c59ca81",
      "type": "feature",
      "attributes": {
        "hint": "Absence",
        "permissions": {
          "read_index": true,
          "create_absences": true
        }
      }
    },
    {
      "id": "ad91901b-4e09-4c74-8c91-87daf1058e35",
      "type": "feature",
      "attributes": {
        "hint": "TimeTracking",
        "permissions": {
          "use_browser_punch_clock": false,
          "read_index": true,
          "create_time_tracking": true
        }
      }
    },
    {
      "id": "8fdca481-2a60-4b14-9add-cace7cb26422",
      "type": "feature",
      "attributes": {
        "hint": "Profile",
        "permissions": {
          "free_subscription": false
        }
      }
    },
    {
      "id": "b5464d2a-5a81-4959-8ece-02d34fa98b46",
      "type": "feature",
      "attributes": {
        "hint": "General",
        "permissions": {
          "show_system_notes": true
        }
      }
    },
    {
      "id": "6bea72b2-6b44-481c-b550-2c5b388d7d07",
      "type": "feature",
      "attributes": {
        "hint": "Analytic",
        "permissions": {
          "allow_segment": true
        }
      }
    },
    {
      "id": "51ea28ca-4b23-4436-8cd3-98535b0b99c8",
      "type": "feature",
      "attributes": {
        "hint": "Calendar",
        "permissions": {
          "read_index": true
        }
      }
    }
  ]
}
```



## returns 200 and doesnt contain usercheckin feature


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/features
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/features`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": [
    {
      "id": "95e6db1c-a1dc-4f3b-ad6a-a2651c59ca81",
      "type": "feature",
      "attributes": {
        "hint": "Absence",
        "permissions": {
          "read_index": true,
          "create_absences": true
        }
      }
    },
    {
      "id": "ad91901b-4e09-4c74-8c91-87daf1058e35",
      "type": "feature",
      "attributes": {
        "hint": "TimeTracking",
        "permissions": {
          "use_browser_punch_clock": false,
          "read_index": true,
          "create_time_tracking": true
        }
      }
    },
    {
      "id": "8fdca481-2a60-4b14-9add-cace7cb26422",
      "type": "feature",
      "attributes": {
        "hint": "Profile",
        "permissions": {
          "free_subscription": false
        }
      }
    },
    {
      "id": "b5464d2a-5a81-4959-8ece-02d34fa98b46",
      "type": "feature",
      "attributes": {
        "hint": "General",
        "permissions": {
          "show_system_notes": true
        }
      }
    },
    {
      "id": "6bea72b2-6b44-481c-b550-2c5b388d7d07",
      "type": "feature",
      "attributes": {
        "hint": "Analytic",
        "permissions": {
          "allow_segment": true
        }
      }
    },
    {
      "id": "51ea28ca-4b23-4436-8cd3-98535b0b99c8",
      "type": "feature",
      "attributes": {
        "hint": "Calendar",
        "permissions": {
          "read_index": true
        }
      }
    }
  ]
}
```



## returns 200 and doesnt contain usercheckin feature


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/features
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/features`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": [
    {
      "id": "75641c8a-8ca6-11eb-8dcd-0242ac130003 ",
      "type": "feature",
      "attributes": {
        "hint": "WorkspaceUser",
        "permissions": {
          "read_index": true,
          "create_workspace_users": true
        }
      }
    },
    {
      "id": "95e6db1c-a1dc-4f3b-ad6a-a2651c59ca81",
      "type": "feature",
      "attributes": {
        "hint": "Absence",
        "permissions": {
          "read_index": true,
          "create_absences": true
        }
      }
    },
    {
      "id": "ad91901b-4e09-4c74-8c91-87daf1058e35",
      "type": "feature",
      "attributes": {
        "hint": "TimeTracking",
        "permissions": {
          "use_browser_punch_clock": false,
          "read_index": true,
          "create_time_tracking": true
        }
      }
    },
    {
      "id": "cfb7843c-377f-4803-9304-b26b7bc212be",
      "type": "feature",
      "attributes": {
        "hint": "Workflow",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "46e419fd-3e45-44fa-95e2-14372664d4ee",
      "type": "feature",
      "attributes": {
        "hint": "Evaluation",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "3d4b9365-1175-46c2-b7c1-2f1c0242699e",
      "type": "feature",
      "attributes": {
        "hint": "Export",
        "permissions": {
          "read_index": true,
          "create_export": true
        }
      }
    },
    {
      "id": "0792c2f7-b90c-4db8-8d79-e9c65d4608cd",
      "type": "feature",
      "attributes": {
        "hint": "Internationalization",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "69303d65-8a39-44f9-b8bc-8bc993520e91",
      "type": "feature",
      "attributes": {
        "hint": "EmployeeSegmentation",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "0fb78c7f-1ea6-4f0a-8cb4-7a048f5f17ee",
      "type": "feature",
      "attributes": {
        "hint": "UserSkill",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "7045d096-b234-4793-861c-c813d0eae747",
      "type": "feature",
      "attributes": {
        "hint": "Archive",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "54a59364-a0f9-4235-92c9-400bb675c23a",
      "type": "feature",
      "attributes": {
        "hint": "UserSpecificPause",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "98a2b423-fefa-4d55-afb7-ffa52a0fee6d",
      "type": "feature",
      "attributes": {
        "hint": "WorkSchedule",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "8bc5ba1f-31c2-4ab2-9971-8e978ae87375",
      "type": "feature",
      "attributes": {
        "hint": "RightRole",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "4e776224-0e7d-4c59-a71e-4765be8799f3",
      "type": "feature",
      "attributes": {
        "hint": "Import",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "8c3989fc-6ded-4709-b545-18f1e1e0c8a8",
      "type": "feature",
      "attributes": {
        "hint": "AccountExport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d8541d49-f833-4ba3-97a9-45166bdf2214",
      "type": "feature",
      "attributes": {
        "hint": "ExtendedCompanyUserRight",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "636e3a90-6750-4a9b-a380-c80bc596bc11",
      "type": "feature",
      "attributes": {
        "hint": "UserBasedPublicHoliday",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "84d56e49-ec38-4907-9256-232591e5037e",
      "type": "feature",
      "attributes": {
        "hint": "ExtendedAbsenceType",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "6afcfc94-1ee0-4f13-baad-f7b4d4bd6037",
      "type": "feature",
      "attributes": {
        "hint": "LocationTemplate",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "f7fe1493-f279-45e2-95fa-f4095152f6be",
      "type": "feature",
      "attributes": {
        "hint": "NetBreak",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "bc656e6b-9e67-4ce6-be41-8a8e9421cde1",
      "type": "feature",
      "attributes": {
        "hint": "VacationBan",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "bb3b58e2-64a9-4fb2-bdc6-d258b7ace8eb",
      "type": "feature",
      "attributes": {
        "hint": "AssignAutomatically",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d95e2100-7151-4aad-b5a5-589f0e1baca0",
      "type": "feature",
      "attributes": {
        "hint": "Payroll",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d8ed7701-fea6-40f4-9363-8ecdc7e8a72f",
      "type": "feature",
      "attributes": {
        "hint": "WageType",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "65415889-67c6-48c0-97eb-9282314c0134",
      "type": "feature",
      "attributes": {
        "hint": "Report",
        "permissions": {
          "read_index": false,
          "create_report": false
        }
      }
    },
    {
      "id": "a61e0ee6-6683-4f12-9335-fbd9adb287cc",
      "type": "feature",
      "attributes": {
        "hint": "EmployeeReport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "fbac64c5-25bb-4ea6-8c2b-ad39c20f0d59",
      "type": "feature",
      "attributes": {
        "hint": "FileTemplate",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "688fb157-2cd9-4bfa-8d3e-15313d296b48",
      "type": "feature",
      "attributes": {
        "hint": "Upload",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d19a2988-dc00-4658-9f6f-d58de840837a",
      "type": "feature",
      "attributes": {
        "hint": "UploadIndex",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "f5f46141-39d2-401b-bb98-d3d4a2bcaa3e",
      "type": "feature",
      "attributes": {
        "hint": "AccountUser",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "11a8c4c4-6796-42d2-bfd1-5370d11260a8",
      "type": "feature",
      "attributes": {
        "hint": "Hr",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "9d22cddf-255b-43ca-ad94-dc2814813546",
      "type": "feature",
      "attributes": {
        "hint": "UserCheckin",
        "permissions": {
          "read": false
        }
      }
    },
    {
      "id": "c614ad7b-8ecc-47d3-a441-061bb080a351",
      "type": "feature",
      "attributes": {
        "hint": "CustomField",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "b681e42a-6734-466b-a830-0367a103c147",
      "type": "feature",
      "attributes": {
        "hint": "DataProfilesRole",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "f189083b-d4b5-43d8-8413-486baac0d654",
      "type": "feature",
      "attributes": {
        "hint": "Task",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d0ab51cc-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "PushNotification",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "e0695ca2-5fe8-4795-b261-783ab5b1d218",
      "type": "feature",
      "attributes": {
        "hint": "WorkingSessionActionsExport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "b11733fd-40d7-4e16-8352-ce84c6f36bd3",
      "type": "feature",
      "attributes": {
        "hint": "HostedPage",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "9b4e4cdb-74d9-46bd-a066-851716d7efcd",
      "type": "feature",
      "attributes": {
        "hint": "ConfirmAssignment",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "1aecd2d7-11cb-4b44-a0fc-bb912360b224",
      "type": "feature",
      "attributes": {
        "hint": "Search",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "06a89ee9-83ed-4a93-a414-7f9feb747b5b",
      "type": "feature",
      "attributes": {
        "hint": "BrowserClockViaAction",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "54c10d4e-758d-4bd0-b1e2-e4a01eb5b671",
      "type": "feature",
      "attributes": {
        "hint": "WorkspaceSetting",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "06a89ee9-83ed-4a93-a414-7f9feb747b5b",
      "type": "feature",
      "attributes": {
        "hint": "BrowserClockViaAction",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "957554f4-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "UserProfileNote",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "a9528eb0-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "AdvancedPayrollExport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "d0ab51cc-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "PushNotification",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "daed51c6-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "EmployeeReportsInUsersIndex",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "e0695ca2-5fe8-4795-b261-783ab5b1d218",
      "type": "feature",
      "attributes": {
        "hint": "WorkingSessionActionsExport",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "e129c506-31db-11ed-a261-0242ac120002",
      "type": "feature",
      "attributes": {
        "hint": "TaskGuest",
        "permissions": {
          "update": true
        }
      }
    },
    {
      "id": "75641c8a-8ca6-11eb-8dcd-0242ac130003 ",
      "type": "feature",
      "attributes": {
        "hint": "WorkspaceUser",
        "permissions": {
          "read_index": true,
          "create_workspace_users": true
        }
      }
    },
    {
      "id": "77062197-48e9-456f-ae97-0136f40a7585",
      "type": "feature",
      "attributes": {
        "hint": "TargetHour",
        "permissions": {
          "create_custom_target_hours": false
        }
      }
    },
    {
      "id": "5c398c9c-7985-4692-89d7-47dc894e3974",
      "type": "feature",
      "attributes": {
        "hint": "Tag",
        "permissions": {
          "allow_employees_to_create_tags": false,
          "allow_employees_to_create_time_tracking_tags": false
        }
      }
    },
    {
      "id": "8fdca481-2a60-4b14-9add-cace7cb26422",
      "type": "feature",
      "attributes": {
        "hint": "Profile",
        "permissions": {
          "free_subscription": false
        }
      }
    },
    {
      "id": "b5464d2a-5a81-4959-8ece-02d34fa98b46",
      "type": "feature",
      "attributes": {
        "hint": "General",
        "permissions": {
          "show_system_notes": true
        }
      }
    },
    {
      "id": "6bea72b2-6b44-481c-b550-2c5b388d7d07",
      "type": "feature",
      "attributes": {
        "hint": "Analytic",
        "permissions": {
          "allow_segment": true
        }
      }
    },
    {
      "id": "51ea28ca-4b23-4436-8cd3-98535b0b99c8",
      "type": "feature",
      "attributes": {
        "hint": "Calendar",
        "permissions": {
          "read_index": true
        }
      }
    }
  ]
}
```


# Workspaces/Roles


## List of roles


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/roles
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/roles`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 4
200 OK
```


```json
{
  "data": [
    {
      "id": "1",
      "type": "role",
      "attributes": {
        "name": "employee",
        "localized_name": "Employee"
      }
    },
    {
      "id": "2",
      "type": "role",
      "attributes": {
        "name": "working_area_admin",
        "localized_name": "Area Admin"
      }
    },
    {
      "id": "3",
      "type": "role",
      "attributes": {
        "name": "workspace_admin",
        "localized_name": "Workspace Admin"
      }
    },
    {
      "id": "4",
      "type": "role",
      "attributes": {
        "name": "account_admin",
        "localized_name": "Account Admin"
      }
    }
  ],
  "meta": {
    "request_id": "7e4e748a-b552-4983-b7f7-661f9d6d7084",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 4
  }
}
```


# Workspaces/Searches


## Search results for account admin


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/searches?filter[query]=ct%3Aexample&amp;resources=User%2CTag%2CArea&amp;items=3
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/searches`

#### Parameters


```json
filter: {&quot;query&quot;=&gt;&quot;ct:example&quot;}
resources: User,Tag,Area
items: 3
```


| Name | Description |
|:-----|:------------|
| filter *required* | Query filter param |
| resources *required* | Resources to be searched |
| items  | Number of items |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 3
Total-Pages: 1
Total-Count: 3
200 OK
```


```json
{
  "data": [
    {
      "id": "122035db-dcdc-4649-9359-0ef3bee7d3d5",
      "type": "search",
      "attributes": {
        "resource_id": 81,
        "resource_type": "User",
        "title": "Bernard Example"
      }
    },
    {
      "id": "b2ed8df5-9485-4434-86fc-abf54480948f",
      "type": "search",
      "attributes": {
        "resource_id": 1051,
        "resource_type": "Area",
        "title": "Example Room"
      }
    },
    {
      "id": "5cb01109-383c-42a5-a24b-334e4a8d24f5",
      "type": "search",
      "attributes": {
        "resource_id": 3,
        "resource_type": "Tag",
        "title": "Example Tag"
      }
    }
  ],
  "meta": {
    "request_id": "56357046-3d51-4a28-9874-1c977ca96a25",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 3,
    "total_pages": 1,
    "total_count": 3
  }
}
```



## Missing params return unprocessable entity error and 422 status


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/searches?items=3
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/searches`

#### Parameters


```json
items: 3
```


| Name | Description |
|:-----|:------------|
| filter *required* | Query filter param |
| resources *required* | Resources to be searched |
| items  | Number of items |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "bad_request",
      "source": {
        "pointer": "base"
      },
      "title": "Param 'filter' is missing or empty."
    }
  ]
}
```



## Empty param returns unprocessable entity error and 422 status


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/searches?filter[query]=&amp;resources=User%2CTag%2CArea&amp;items=3
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/searches`

#### Parameters


```json
filter: {&quot;query&quot;=&gt;&quot;&quot;}
resources: User,Tag,Area
items: 3
```


| Name | Description |
|:-----|:------------|
| filter *required* | Query filter param |
| resources *required* | Resources to be searched |
| items  | Number of items |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "bad_request",
      "source": {
        "pointer": "base"
      },
      "title": "Param 'query' is missing or empty."
    }
  ]
}
```



## Search results for employee


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/searches?filter[query]=ct%3Aexample&amp;resources=User%2CTag%2CArea&amp;items=3
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/searches`

#### Parameters


```json
filter: {&quot;query&quot;=&gt;&quot;ct:example&quot;}
resources: User,Tag,Area
items: 3
```


| Name | Description |
|:-----|:------------|
| filter *required* | Query filter param |
| resources *required* | Resources to be searched |
| items  | Number of items |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 3
Total-Pages: 1
Total-Count: 3
200 OK
```


```json
{
  "data": [
    {
      "id": "ffbf8266-31d4-49ee-9c65-4c00d9d792d4",
      "type": "search",
      "attributes": {
        "resource_id": 81,
        "resource_type": "User",
        "title": "Bernard Example"
      }
    },
    {
      "id": "3891f30c-2ce4-4f8c-a470-017d5d3c4e79",
      "type": "search",
      "attributes": {
        "resource_id": 1051,
        "resource_type": "Area",
        "title": "Example Room"
      }
    },
    {
      "id": "e99888c2-8f78-46e2-b716-ebfe03f42afc",
      "type": "search",
      "attributes": {
        "resource_id": 3,
        "resource_type": "Tag",
        "title": "Example Tag"
      }
    }
  ],
  "meta": {
    "request_id": "c5952e90-46b8-44eb-9615-d255c14df4df",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 3,
    "total_pages": 1,
    "total_count": 3
  }
}
```



## returns an authorization error


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/searches?filter[query]=ct%3Aexample&amp;resources=User%2CTag%2CArea&amp;items=3
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/searches`

#### Parameters


```json
filter: {&quot;query&quot;=&gt;&quot;ct:example&quot;}
resources: User,Tag,Area
items: 3
```


| Name | Description |
|:-----|:------------|
| filter *required* | Query filter param |
| resources *required* | Resources to be searched |
| items  | Number of items |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
401 Unauthorized
```


```json
{
  "errors": [
    {
      "status": "unauthorized",
      "source": {
        "pointer": "base"
      },
      "title": "You need to sign in or sign up before continuing."
    }
  ]
}
```


# Workspaces/SuggestedFollowers


## All types of admins can access list of suggested_followers


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/suggested_followers
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/suggested_followers`

#### Parameters



| Name | Description |
|:-----|:------------|
| filter  | Filter |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 5
200 OK
```


```json
{
  "data": [
    {
      "id": "40",
      "type": "user",
      "attributes": {
        "username": "Enrico Schultz"
      }
    },
    {
      "id": "41",
      "type": "user",
      "attributes": {
        "username": "Fr. Ruben Plank"
      }
    },
    {
      "id": "39",
      "type": "user",
      "attributes": {
        "username": "Freiherr Sami Grams"
      }
    },
    {
      "id": "42",
      "type": "user",
      "attributes": {
        "username": "Jannes Scherer"
      }
    },
    {
      "id": "43",
      "type": "user",
      "attributes": {
        "username": "Karina zu Pippig"
      }
    }
  ],
  "meta": {
    "request_id": "d48d017f-d819-417d-a562-36da19c29954",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 5
  }
}
```



## All types of employees can access list of suggested_followers


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/suggested_followers
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/suggested_followers`

#### Parameters



| Name | Description |
|:-----|:------------|
| filter  | Filter |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 5
200 OK
```


```json
{
  "data": [
    {
      "id": "40",
      "type": "user",
      "attributes": {
        "username": "Enrico Schultz"
      }
    },
    {
      "id": "41",
      "type": "user",
      "attributes": {
        "username": "Fr. Ruben Plank"
      }
    },
    {
      "id": "39",
      "type": "user",
      "attributes": {
        "username": "Freiherr Sami Grams"
      }
    },
    {
      "id": "42",
      "type": "user",
      "attributes": {
        "username": "Jannes Scherer"
      }
    },
    {
      "id": "43",
      "type": "user",
      "attributes": {
        "username": "Karina zu Pippig"
      }
    }
  ],
  "meta": {
    "request_id": "e4a7cd67-405f-4472-bf02-1382ec24a209",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 5
  }
}
```



## All types of admins can access list of filtered suggested_followers by username


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/suggested_followers?filter[username]=ct%3AEnrico+Schultz
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/suggested_followers`

#### Parameters


```json
filter: {&quot;username&quot;=&gt;&quot;ct:Enrico Schultz&quot;}
```


| Name | Description |
|:-----|:------------|
| filter  | Filter |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "40",
      "type": "user",
      "attributes": {
        "username": "Enrico Schultz"
      }
    }
  ],
  "meta": {
    "request_id": "37b7abab-49ba-4753-8650-29e2f1ef2da9",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



# Workspaces/Summaries

Summaries resource

## Fetch a summary


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/summaries?resource=TimeTracking&amp;scopes=running,unconfirmed,confirmed
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/summaries`

#### Parameters


```json
resource: TimeTracking
scopes: running,unconfirmed,confirmed
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| resource *required* | Resources to be searched |
| scopes  | Scopes to be applied |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 0
200 OK
```


```json
{
  "data": [

  ],
  "meta": {
    "request_id": "ac7efd14-1726-436b-942d-ccf4ec29b2c2",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 0,
    "running": 0,
    "unconfirmed": 0,
    "confirmed": 0
  }
}
```



## Returns success response


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/112/records/summary
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/:user_id/records/summary`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "112",
    "type": "records_summary",
    "attributes": {
      "confirmed_total_overtime_in_sec": 0.0,
      "total_overtime_in_sec": 0.0
    }
  },
  "meta": {
    "request_id": "5d0ee4d4-a8af-4f1c-bcaa-32c0df97bee5",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Includes user id


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/113/records/summary
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/:user_id/records/summary`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "113",
    "type": "records_summary",
    "attributes": {
      "confirmed_total_overtime_in_sec": 0.0,
      "total_overtime_in_sec": 0.0
    }
  },
  "meta": {
    "request_id": "817b1358-3a74-4c61-95bb-58accd83907a",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Includes user attributes


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/114/records/summary
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/:user_id/records/summary`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "114",
    "type": "records_summary",
    "attributes": {
      "confirmed_total_overtime_in_sec": 0.0,
      "total_overtime_in_sec": 0.0
    }
  },
  "meta": {
    "request_id": "90f16855-216a-4a88-9624-586c9a725eb0",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```


# Workspaces/Taggings


## and allow_employees_tag_working_sessions to true


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/taggings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/taggings`

#### Parameters


```json
{"data":{"type":"tagging","attributes":{"taggable_type":"TimeTracking","tag_id":4,"taggable_id":"2b0579ef-c83c-4dc6-b035-d0de4b6d44a8"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "fd7406d2-3f86-483a-bf1f-6c210d597692",
    "type": "tagging",
    "attributes": {
      "taggable_type": "TimeTracking",
      "taggable_id": "2b0579ef-c83c-4dc6-b035-d0de4b6d44a8"
    },
    "relationships": {
      "tag": {
        "data": {
          "id": "4",
          "type": "tag"
        }
      }
    }
  },
  "meta": {
    "request_id": "4b80a312-4ba8-4e74-a561-c21964e8aa1a",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Create a tagging


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/taggings
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/taggings`

#### Parameters


```json
{"data":{"type":"tagging","attributes":{"taggable_type":"TimeTracking","tag_id":4,"taggable_id":"2b0579ef-c83c-4dc6-b035-d0de4b6d44a8"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "06371fcc-5e49-42b7-852c-1f3622f16e75",
    "type": "tagging",
    "attributes": {
      "taggable_type": "TimeTracking",
      "taggable_id": "2b0579ef-c83c-4dc6-b035-d0de4b6d44a8"
    },
    "relationships": {
      "tag": {
        "data": {
          "id": "4",
          "type": "tag"
        }
      }
    }
  },
  "meta": {
    "request_id": "76d3c5b7-5f78-48e2-8778-8632b6f74b18",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Delete a tagging


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/taggings/f848b419-53a9-4166-bcfe-6d776419a8b0
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/taggings/:tagging_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| tagging_id *required* | Tagging ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "f848b419-53a9-4166-bcfe-6d776419a8b0",
    "type": "tagging",
    "attributes": {
      "taggable_type": "TimeTracking",
      "taggable_id": "ff7e1f84-80a4-4132-ad5b-8305a00b06b6"
    },
    "relationships": {
      "tag": {
        "data": {
          "id": "5",
          "type": "tag"
        }
      }
    }
  },
  "meta": {
    "request_id": "c0bfbd96-04c6-4952-99d9-0ddef52585dc",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Index


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/taggings
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/taggings`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "2fc81dc0-3921-4dc2-95eb-f04323f88f62",
      "type": "tagging",
      "attributes": {
        "taggable_type": "TimeTracking",
        "taggable_id": "0ea419ec-da01-4493-8c2f-5ec474250207"
      },
      "relationships": {
        "tag": {
          "data": {
            "id": "6",
            "type": "tag"
          }
        }
      }
    }
  ],
  "meta": {
    "request_id": "44062659-7564-41c6-a86e-6fd4fdd778f7",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Show tagging


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/taggings/d832adbc-7872-426c-ba7a-0e9eb2b2d578
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/taggings/:tagging_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| tagging_id *required* | Tagging ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "d832adbc-7872-426c-ba7a-0e9eb2b2d578",
    "type": "tagging",
    "attributes": {
      "taggable_type": "TimeTracking",
      "taggable_id": "b6361f7c-068d-4c20-9966-e436680a83b1"
    },
    "relationships": {
      "tag": {
        "data": {
          "id": "7",
          "type": "tag"
        }
      }
    }
  },
  "meta": {
    "request_id": "d472304a-aba8-4238-a256-05b8c5e9b226",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```


# Workspaces/Tags


## Tag created


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/tags`

#### Parameters


```json
{"data":{"type":"tag","attributes":{"title":"erster Tag","active":true,"external_id":"External ID","color":"#F5D76E","company_id":1028}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "8",
    "type": "tag",
    "attributes": {
      "title": "erster Tag",
      "active": true,
      "external_id": "External ID",
      "color": "#F5D76E"
    },
    "relationships": {
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      },
      "users": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "8dfe4f69-5fcf-43d3-aec3-12fe04b3569d",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## delete a Tag


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/tags/9
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/tags/:tag_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| tag_id *required* | Tag ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "9",
    "type": "tag",
    "attributes": {
      "title": "7-copper",
      "active": true,
      "external_id": null,
      "color": null
    },
    "relationships": {
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      },
      "users": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "1ae2a5d3-8b6e-4b43-a163-638df48fc03d",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Index


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/tags
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/tags`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "10",
      "type": "tag",
      "attributes": {
        "title": "8-puce",
        "active": true,
        "external_id": null,
        "color": null
      },
      "relationships": {
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        },
        "users": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "9a581d5d-aeaa-4eaa-83ab-27b6a81eed50",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1,
    "can_modify_tags": false,
    "can_create_tags": true
  }
}
```



## Index with users association exist


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/tags
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/tags`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "11",
      "type": "tag",
      "attributes": {
        "title": "9-rose",
        "active": true,
        "external_id": null,
        "color": null
      },
      "relationships": {
        "workspace": {
          "data": {
            "id": "1028",
            "type": "workspace"
          }
        },
        "users": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "a0908691-54b7-45c0-904f-3872a6783210",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1,
    "can_modify_tags": false,
    "can_create_tags": true
  }
}
```



## Tag Details


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/tags/13
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/tags/:tag_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| tag_id *required* | Tag ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "13",
    "type": "tag",
    "attributes": {
      "title": "11-plum",
      "active": true,
      "external_id": null,
      "color": null
    },
    "relationships": {
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      },
      "users": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "1a1cba25-023a-4569-b7d0-54fb74d260bf",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Update a Tag


### Request

#### Endpoint

```plaintext
PUT /api/v3/workspaces/1028/tags/15
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PUT /api/v3/workspaces/:workspace_id/tags/:tag_id`

#### Parameters


```json
{"data":{"attributes":{"title":"Updated_Tag"},"type":"tag"}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| tag_id *required* | Tag ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "15",
    "type": "tag",
    "attributes": {
      "title": "Updated_Tag",
      "active": true,
      "external_id": null,
      "color": null
    },
    "relationships": {
      "workspace": {
        "data": {
          "id": "1028",
          "type": "workspace"
        }
      },
      "users": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "223e507a-e3f2-4595-beaf-da4daafaf759",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```

# Workspaces/Shifts


## Index


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/shifts
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/shifts`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "48",
      "type": "event",
      "attributes": {
        "uuid": "408df777-98a2-4516-b582-1997dff5c62a",
        "number_of_employees": 1,
        "starts_at": "2022-02-03T04:00:00Z",
        "ends_at": "2022-02-03T05:00:00Z",
        "created_at": "2023-01-30T11:23:00Z",
        "updated_at": "2023-01-30T11:23:00Z"
      },
      "relationships": {
        "working_area": {
          "data": {
            "id": "1028",
            "type": "area"
          }
        },
        "recurrence": {
          "data": null
        },
        "users": {
          "data": [

          ]
        },
        "event_pauses": {
          "data": [

          ]
        }
      }
    },
    {
      "id": "47",
      "type": "event",
      "attributes": {
        "uuid": "8d8fb3d7-229c-46bf-90da-9c6610715c5f",
        "number_of_employees": 1,
        "starts_at": "2022-02-03T04:00:00Z",
        "ends_at": "2022-02-03T05:00:00Z",
        "created_at": "2023-01-30T11:23:00Z",
        "updated_at": "2023-01-30T11:23:00Z"
      },
      "relationships": {
        "working_area": {
          "data": {
            "id": "1028",
            "type": "area"
          }
        },
        "recurrence": {
          "data": null
        },
        "users": {
          "data": [

          ]
        },
        "event_pauses": {
          "data": [

          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "7b80732b-b1db-4920-b471-5830cb7da103",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2
  }
}
```


# Workspaces/Vacations


## returns 200 status with the user vacation summary data


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/40/vacations/summary
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/:user_id/vacations/summary`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "40",
    "type": "vacation_summary",
    "attributes": {
      "planned_vacation_days_this_year": 20.0,
      "remaining_vacation_days_this_year": 10.5
    }
  },
  "meta": {
    "request_id": "a4136326-b706-4590-aac7-f7cb184864ba",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```

# Workspaces/TimeTrackingMethods


## List of Time Tracking methods


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_tracking_methods
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_tracking_methods`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": [
    {
      "id": "2",
      "type": "time_tracking_method",
      "attributes": {
        "name": "via_roster",
        "localized_name": "Via Roster",
        "disabled": false,
        "hint": "Is available because the account's plan is not 'core'."
      }
    },
    {
      "id": "3",
      "type": "time_tracking_method",
      "attributes": {
        "name": "via_browser_time_clock",
        "localized_name": "Via Browser-time clock",
        "disabled": true,
        "hint": "Is disabled if module browser_punch_clock is not available as a feature."
      }
    },
    {
      "id": "4",
      "type": "time_tracking_method",
      "attributes": {
        "name": "via_app",
        "localized_name": "Via App",
        "disabled": true,
        "hint": "Is disabled if the employee is not synced to the app."
      }
    },
    {
      "id": "5",
      "type": "time_tracking_method",
      "attributes": {
        "name": "via_terminal_app",
        "localized_name": "Via Terminal App",
        "disabled": true,
        "hint": "Is disabled if the employee is not synced to the app & is not available on a production environment."
      }
    }
  ]
}
```


## List of Time Tracking methods for an account with a &#39;core&#39; plan


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/time_tracking_methods
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/time_tracking_methods`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": [
    {
      "id": "1",
      "type": "time_tracking_method",
      "attributes": {
        "name": "via_time_tracking",
        "localized_name": "Via Time Tracking",
        "disabled": false,
        "hint": "Is the default method if no other method is available."
      }
    },
    {
      "id": "3",
      "type": "time_tracking_method",
      "attributes": {
        "name": "via_browser_time_clock",
        "localized_name": "Via Browser-time clock",
        "disabled": true,
        "hint": "Is disabled if module browser_punch_clock is not available as a feature."
      }
    },
    {
      "id": "4",
      "type": "time_tracking_method",
      "attributes": {
        "name": "via_app",
        "localized_name": "Via App",
        "disabled": true,
        "hint": "Is disabled if the employee is not synced to the app."
      }
    },
    {
      "id": "5",
      "type": "time_tracking_method",
      "attributes": {
        "name": "via_terminal_app",
        "localized_name": "Via Terminal App",
        "disabled": true,
        "hint": "Is disabled if the employee is not synced to the app & is not available on a production environment."
      }
    }
  ]
}
```

# Workspaces/User/Status

Activate User

## Activate as an Account Admin or a Workspace Admin


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40/user_status
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/user_status`

#### Parameters


```json
{"data":{"type":"user","attributes":{"status":"active"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "40",
    "type": "user",
    "attributes": {
      "permissions": null,
      "email": "gail.block@jones.biz",
      "username": "Enrico Schultz",
      "tablet_pin": null,
      "abbreviation": null,
      "hour_holidays": false,
      "time_zone": null,
      "initial_time_account": 0.0,
      "checkin_complete": null,
      "start_of_accounting": "2022-12-30",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 8,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": null,
      "external_id": null,
      "birthday": null,
      "identifier_pin": "17hs",
      "locale": null,
      "status": "active",
      "assumed_role": "employee",
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": {
          "id": "1026",
          "type": "account"
        }
      },
      "areas": {
        "data": [
          {
            "id": "1028",
            "type": "area"
          }
        ]
      },
      "roles": {
        "data": [
          {
            "id": "1",
            "type": "role"
          }
        ]
      },
      "workspaces": {
        "data": [
          {
            "id": "1028",
            "type": "workspace"
          }
        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [
          {
            "id": "1028",
            "type": "absence_type"
          }
        ]
      },
      "tags": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      },
      "last_action": {
        "data": null
      }
    }
  },
  "meta": {
    "request_id": "44e0c4a9-8d06-429b-8a77-c2cf0bc90487",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Activate should result in error


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40/user_status
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/user_status`

#### Parameters


```json
{"data":{"type":"user","attributes":{"status":"active"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "Employee limit is reached - upgrade your account"
    }
  ]
}
```



## An Area Admin can not update a user


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40/user_status
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/user_status`

#### Parameters


```json
{"data":{"type":"user","attributes":{"status":"active"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Not allowed to update oneself


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/39/user_status
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/user_status`

#### Parameters


```json
{"data":{"type":"user","attributes":{"status":"active"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Activate as an Account Admin or a Workspace Admin


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40/user_status
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/user_status`

#### Parameters


```json
{"data":{"type":"user","attributes":{"status":"inactive"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "40",
    "type": "user",
    "attributes": {
      "permissions": null,
      "email": "gail.block@jones.biz",
      "username": "Enrico Schultz",
      "tablet_pin": null,
      "abbreviation": null,
      "hour_holidays": false,
      "time_zone": null,
      "initial_time_account": 0.0,
      "checkin_complete": null,
      "start_of_accounting": "2022-12-30",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 8,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": null,
      "external_id": null,
      "birthday": null,
      "identifier_pin": "17hs",
      "locale": null,
      "status": "inactive",
      "assumed_role": "employee",
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": {
          "id": "1026",
          "type": "account"
        }
      },
      "areas": {
        "data": [
          {
            "id": "1028",
            "type": "area"
          }
        ]
      },
      "roles": {
        "data": [
          {
            "id": "1",
            "type": "role"
          }
        ]
      },
      "workspaces": {
        "data": [
          {
            "id": "1028",
            "type": "workspace"
          }
        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [
          {
            "id": "1028",
            "type": "absence_type"
          }
        ]
      },
      "tags": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      },
      "last_action": {
        "data": null
      }
    }
  },
  "meta": {
    "request_id": "695017e8-6be2-4a73-ac91-4e396c5c7557",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Deactivate should result in error


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40/user_status
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/user_status`

#### Parameters


```json
{"data":{"type":"user","attributes":{"status":"inactive"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "This employee is currently synced with the location app and can not be deactivated or removed."
    }
  ]
}
```



## An Area Admin can not update a user


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40/user_status
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/user_status`

#### Parameters


```json
{"data":{"type":"user","attributes":{"status":"inactive"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Not allowed to update oneself


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/39/user_status
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/user_status`

#### Parameters


```json
{"data":{"type":"user","attributes":{"status":"inactive"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```


# Workspaces/Users


## Invite selected pending users


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/batch_invitations
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/batch_invitations`

#### Parameters


```json
{"data":{"type":"batch_invitation","attributes":{"all":false,"checkin":true,"welcome_message":"Welcome to your workspace!","user_ids":["40"]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Einladungen wurden verschickt."
  }
}
```



## Checkin is enabled for the invite when the workspace&#39;s user_checkin is enabled


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/batch_invitations
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/batch_invitations`

#### Parameters


```json
{"data":{"type":"batch_invitation","attributes":{"all":false,"checkin":true,"welcome_message":"Welcome to your workspace!","user_ids":["40"]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Invitations have been sent."
  }
}
```



## Checkin is enabled for the invite when the workspace&#39;s user_checkin is enabled


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/batch_invitations
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/batch_invitations`

#### Parameters


```json
{"data":{"type":"batch_invitation","attributes":{"all":false,"checkin":true,"welcome_message":"Welcome to your workspace!","user_ids":["40"]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Invitations have been sent."
  }
}
```



## Invite all pending users


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/batch_invitations
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/batch_invitations`

#### Parameters


```json
{"data":{"type":"batch_invitation","attributes":{"all":true,"checkin":false,"welcome_message":"Welcome to your workspace!"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "meta": {
    "message": "Einladungen wurden verschickt."
  }
}
```



## A request missing necessary parameters returns an error


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/batch_invitations
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/batch_invitations`

#### Parameters


```json
{"data":{"type":"batch_invitation","attributes":{"all":false,"checkin":false,"welcome_message":"Welcome to your workspace!"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Params are missing"
    }
  ]
}
```



## Employee can not invite users


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/batch_invitations
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/batch_invitations`

#### Parameters


```json
{"data":{"type":"batch_invitation","attributes":{"all":false,"checkin":false,"welcome_message":"Welcome to your workspace!"}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Create a user


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
{"data":{"type":"user","attributes":{"username":"New user","email":"","tablet_pin":"","avatar":"","abbreviation":"user","hour_holidays":false,"time_zone":"","initial_time_account":"","start_of_accounting":"","saldo_type":0,"salary":"","hours_on_vacation_day":0,"home_office":false,"calc_holiday_options":"target","custom_holiday_hours":0.0,"calc_vacation_options":"target","working_sessions_creator":false,"staff_number":"","external_id":"","birthday":"","identifier_pin":"22z2","locale":"","time_tracking_method_id":"2","filter_ids":[],"wage_type_ids":[],"default_break_ids":[],"absence_type_ids":[],"public_holiday_ids":[],"area_ids":[1052]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "87",
    "type": "user",
    "attributes": {
      "permissions": null,
      "email": "",
      "username": "New user",
      "tablet_pin": "",
      "abbreviation": "user",
      "hour_holidays": false,
      "time_zone": "",
      "initial_time_account": 0.0,
      "checkin_complete": null,
      "start_of_accounting": "2023-01-01",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 4,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": "",
      "external_id": "",
      "birthday": null,
      "identifier_pin": "22z2",
      "locale": "",
      "status": "active",
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": null
      },
      "areas": {
        "data": [
          {
            "id": "1052",
            "type": "area"
          }
        ]
      },
      "workspaces": {
        "data": [

        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [

        ]
      },
      "tags": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "2cb0009b-4801-4627-bdc9-93ccb5ebf04a",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Can not create a new user with a taken email


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
{"data":{"type":"user","attributes":{"username":"New user","email":"gail.block@jones.biz","tablet_pin":"","avatar":"","abbreviation":"user","hour_holidays":false,"time_zone":"","initial_time_account":"","start_of_accounting":"","saldo_type":0,"salary":"","hours_on_vacation_day":0,"home_office":false,"calc_holiday_options":"target","custom_holiday_hours":0.0,"calc_vacation_options":"target","working_sessions_creator":false,"staff_number":"","external_id":"","birthday":"","identifier_pin":"22z2","locale":"","time_tracking_method_id":"2","filter_ids":[],"wage_type_ids":[],"default_break_ids":[],"absence_type_ids":[],"public_holiday_ids":[],"area_ids":[1053]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "email"
      },
      "title": "has already been taken"
    }
  ]
}
```



## Can not create a user with an empty username


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
{"data":{"type":"user","attributes":{"username":"","email":"","tablet_pin":"","avatar":"","abbreviation":"user","hour_holidays":false,"time_zone":"","initial_time_account":"","start_of_accounting":"","saldo_type":0,"salary":"","hours_on_vacation_day":0,"home_office":false,"calc_holiday_options":"target","custom_holiday_hours":0.0,"calc_vacation_options":"target","working_sessions_creator":false,"staff_number":"","external_id":"","birthday":"","identifier_pin":"22z2","locale":"","time_tracking_method_id":"2","filter_ids":[],"wage_type_ids":[],"default_break_ids":[],"absence_type_ids":[],"public_holiday_ids":[],"area_ids":[1054]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "username"
      },
      "title": "can't be blank"
    }
  ]
}
```



## Can not create a new user if user limit is reached


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
{"data":{"type":"user","attributes":{"username":"New user","email":"","tablet_pin":"","avatar":"","abbreviation":"user","hour_holidays":false,"time_zone":"","initial_time_account":"","start_of_accounting":"","saldo_type":0,"salary":"","hours_on_vacation_day":0,"home_office":false,"calc_holiday_options":"target","custom_holiday_hours":0.0,"calc_vacation_options":"target","working_sessions_creator":false,"staff_number":"","external_id":"","birthday":"","identifier_pin":"22z2","locale":"","time_tracking_method_id":"2","filter_ids":[],"wage_type_ids":[],"default_break_ids":[],"absence_type_ids":[],"public_holiday_ids":[],"area_ids":[1055]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "Employee limit is reached - Upgrade your account."
    }
  ]
}
```



## Area admins are not allowed to create new users


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
{"data":{"type":"user","attributes":{"username":"New user","email":"","tablet_pin":"","avatar":"","abbreviation":"user","hour_holidays":false,"time_zone":"","initial_time_account":"","start_of_accounting":"","saldo_type":0,"salary":"","hours_on_vacation_day":0,"home_office":false,"calc_holiday_options":"target","custom_holiday_hours":0.0,"calc_vacation_options":"target","working_sessions_creator":false,"staff_number":"","external_id":"","birthday":"","identifier_pin":"22z2","locale":"","time_tracking_method_id":"2","filter_ids":[],"wage_type_ids":[],"default_break_ids":[],"absence_type_ids":[],"public_holiday_ids":[],"area_ids":[]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Employees are not allowed to create new users


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
{"data":{"type":"user","attributes":{"username":"New user","email":"","tablet_pin":"","avatar":"","abbreviation":"user","hour_holidays":false,"time_zone":"","initial_time_account":"","start_of_accounting":"","saldo_type":0,"salary":"","hours_on_vacation_day":0,"home_office":false,"calc_holiday_options":"target","custom_holiday_hours":0.0,"calc_vacation_options":"target","working_sessions_creator":false,"staff_number":"","external_id":"","birthday":"","identifier_pin":"22z2","locale":"","time_tracking_method_id":"2","filter_ids":[],"wage_type_ids":[],"default_break_ids":[],"absence_type_ids":[],"public_holiday_ids":[],"area_ids":[]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Delete a user in the workspace


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/users/88
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/users/:user_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "88",
    "type": "user",
    "attributes": {
      "permissions": null,
      "email": "ty@mueller.org",
      "username": "Daren Braun",
      "tablet_pin": null,
      "abbreviation": null,
      "hour_holidays": false,
      "time_zone": null,
      "initial_time_account": 0.0,
      "checkin_complete": null,
      "start_of_accounting": "2023-01-01",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 1,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": null,
      "external_id": null,
      "birthday": null,
      "identifier_pin": "231k",
      "locale": null,
      "status": "active",
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": null
      },
      "areas": {
        "data": [

        ]
      },
      "workspaces": {
        "data": [

        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [

        ]
      },
      "tags": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      }
    }
  },
  "meta": {
    "request_id": "a4397628-7985-41d5-b199-f2bd56dc49be",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## A user synced with the location app can not be deleted


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/users/89
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/users/:user_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "This employee is currently synced with the location app and can not be deactivated or removed."
    }
  ]
}
```



## Users can not delete themselves


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/users/43
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/users/:user_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Workspace admins can not delete other Workspace Admins or Account Admins


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/users/39
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/users/:user_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Delete a user


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/users/90
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/users/:user_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Filtering by pending invitations and email presence


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users?permissions=update%2C+destroy%2C+update_account_admin_role&amp;filter[with_pending_invitation]=true&amp;filter[email]=present%3Atrue&amp;include=account%2C+roles%2C+workspaces%2C+absence_types%2C+tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
permissions: update, destroy, update_account_admin_role
filter: {&quot;with_pending_invitation&quot;=&gt;&quot;true&quot;, &quot;email&quot;=&gt;&quot;present:true&quot;}
include: account, roles, workspaces, absence_types, tags
```


| Name | Description |
|:-----|:------------|
| permissions  | User Permissions |
| filter  | Filter |
| include  | Relationships details |
| fields  | Only return specfic attributes |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "40",
      "type": "user",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2022-12-30",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 8,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "17hs",
        "locale": null,
        "status": "active",
        "assumed_role": "employee",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        },
        "roles": {
          "data": [
            {
              "id": "1",
              "type": "role"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        },
        "last_action": {
          "data": null
        }
      }
    }
  ],
  "included": [
    {
      "id": "1026",
      "type": "account",
      "attributes": {
        "phone": "+492204948890",
        "country": null,
        "locale": "de",
        "account_name": "Wallstab-Lutje",
        "created_at": "2023-01-30T11:21:41Z",
        "updated_at": "2023-01-30T11:21:41Z"
      }
    },
    {
      "id": "1",
      "type": "role",
      "attributes": {
        "name": "employee",
        "localized_name": "Employee"
      }
    },
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    },
    {
      "id": "1028",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 1_759",
        "kind": "vacation"
      }
    }
  ],
  "meta": {
    "request_id": "5fbd177a-5d86-4811-9452-b8adc4dae614",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Filtering by absence_types


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users?permissions=update%2C+destroy%2C+update_account_admin_role&amp;filter[absence_types_id_in][]=1066&amp;include=account%2C+roles%2C+workspaces%2C+absence_types%2C+tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
permissions: update, destroy, update_account_admin_role
filter: {&quot;absence_types_id_in&quot;=&gt;[&quot;1066&quot;]}
include: account, roles, workspaces, absence_types, tags
```


| Name | Description |
|:-----|:------------|
| permissions  | User Permissions |
| filter  | Filter |
| include  | Relationships details |
| fields  | Only return specfic attributes |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "39",
      "type": "user",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": false,
          "update_account_admin_role": false
        },
        "email": "marcel_littel@hand.net",
        "username": "Freiherr Sami Grams",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 1,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "86re",
        "locale": null,
        "status": "active",
        "assumed_role": "admin",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [

          ]
        },
        "roles": {
          "data": [
            {
              "id": "2",
              "type": "role"
            },
            {
              "id": "3",
              "type": "role"
            },
            {
              "id": "4",
              "type": "role"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            },
            {
              "id": "1066",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        },
        "last_action": {
          "data": {
            "id": "56bd62f7-ea12-4c5c-8e96-406807c695da",
            "type": "action"
          }
        }
      }
    }
  ],
  "included": [
    {
      "id": "1026",
      "type": "account",
      "attributes": {
        "phone": "+492204948890",
        "country": null,
        "locale": "de",
        "account_name": "Wallstab-Lutje",
        "created_at": "2023-01-30T11:21:41Z",
        "updated_at": "2023-01-30T11:21:41Z"
      }
    },
    {
      "id": "2",
      "type": "role",
      "attributes": {
        "name": "working_area_admin",
        "localized_name": "Area Admin"
      }
    },
    {
      "id": "3",
      "type": "role",
      "attributes": {
        "name": "workspace_admin",
        "localized_name": "Workspace Admin"
      }
    },
    {
      "id": "4",
      "type": "role",
      "attributes": {
        "name": "account_admin",
        "localized_name": "Account Admin"
      }
    },
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    },
    {
      "id": "1028",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 1_759",
        "kind": "vacation"
      }
    },
    {
      "id": "1066",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 39_300",
        "kind": "vacation"
      }
    }
  ],
  "meta": {
    "request_id": "ab4fdc91-54cd-430a-882f-32f9ca0bb079",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Filtering by absence_types


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users?permissions=update%2C+destroy%2C+update_account_admin_role&amp;filter[absence_types_id_in][]=9999&amp;include=account%2C+roles%2C+workspaces%2C+absence_types%2C+tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
permissions: update, destroy, update_account_admin_role
filter: {&quot;absence_types_id_in&quot;=&gt;[&quot;9999&quot;]}
include: account, roles, workspaces, absence_types, tags
```


| Name | Description |
|:-----|:------------|
| permissions  | User Permissions |
| filter  | Filter |
| include  | Relationships details |
| fields  | Only return specfic attributes |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 0
200 OK
```


```json
{
  "data": [

  ],
  "included": [

  ],
  "meta": {
    "request_id": "7bd857c3-3a52-4375-bb69-e4d1834ab8cd",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 0
  }
}
```



## Filtering by intersecting absence_types


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users?permissions=update%2C+destroy%2C+update_account_admin_role&amp;filter[intersecting_absence_types][]=1069&amp;filter[intersecting_absence_types][]=1070&amp;include=account%2C+roles%2C+workspaces%2C+absence_types%2C+tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
permissions: update, destroy, update_account_admin_role
filter: {&quot;intersecting_absence_types&quot;=&gt;[&quot;1069&quot;, &quot;1070&quot;]}
include: account, roles, workspaces, absence_types, tags
```


| Name | Description |
|:-----|:------------|
| permissions  | User Permissions |
| filter  | Filter |
| include  | Relationships details |
| fields  | Only return specfic attributes |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "39",
      "type": "user",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": false,
          "update_account_admin_role": false
        },
        "email": "marcel_littel@hand.net",
        "username": "Freiherr Sami Grams",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 1,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "86re",
        "locale": null,
        "status": "active",
        "assumed_role": "admin",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [

          ]
        },
        "roles": {
          "data": [
            {
              "id": "2",
              "type": "role"
            },
            {
              "id": "3",
              "type": "role"
            },
            {
              "id": "4",
              "type": "role"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            },
            {
              "id": "1069",
              "type": "absence_type"
            },
            {
              "id": "1070",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [

          ]
        },
        "custom_field_values": {
          "data": [

          ]
        },
        "last_action": {
          "data": {
            "id": "9a945328-d70d-464e-ab6f-59b2a67d6f4b",
            "type": "action"
          }
        }
      }
    }
  ],
  "included": [
    {
      "id": "1026",
      "type": "account",
      "attributes": {
        "phone": "+492204948890",
        "country": null,
        "locale": "de",
        "account_name": "Wallstab-Lutje",
        "created_at": "2023-01-30T11:21:41Z",
        "updated_at": "2023-01-30T11:21:41Z"
      }
    },
    {
      "id": "2",
      "type": "role",
      "attributes": {
        "name": "working_area_admin",
        "localized_name": "Area Admin"
      }
    },
    {
      "id": "3",
      "type": "role",
      "attributes": {
        "name": "workspace_admin",
        "localized_name": "Workspace Admin"
      }
    },
    {
      "id": "4",
      "type": "role",
      "attributes": {
        "name": "account_admin",
        "localized_name": "Account Admin"
      }
    },
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    },
    {
      "id": "1028",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 1_759",
        "kind": "vacation"
      }
    },
    {
      "id": "1069",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 42_520",
        "kind": "vacation"
      }
    },
    {
      "id": "1070",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 43_16",
        "kind": "vacation"
      }
    }
  ],
  "meta": {
    "request_id": "8320d49b-5f94-49ff-be98-0acea116246d",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Filtering by intersecting absence_types


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users?permissions=update%2C+destroy%2C+update_account_admin_role&amp;filter[intersecting_absence_types][]=0&amp;include=account%2C+roles%2C+workspaces%2C+absence_types%2C+tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
permissions: update, destroy, update_account_admin_role
filter: {&quot;intersecting_absence_types&quot;=&gt;[&quot;0&quot;]}
include: account, roles, workspaces, absence_types, tags
```


| Name | Description |
|:-----|:------------|
| permissions  | User Permissions |
| filter  | Filter |
| include  | Relationships details |
| fields  | Only return specfic attributes |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 0
200 OK
```


```json
{
  "data": [

  ],
  "included": [

  ],
  "meta": {
    "request_id": "e03fafc2-8269-4cb7-afd1-1fc33df68d6a",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 0
  }
}
```



## returns user associated with tag


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users?permissions=update%2C+destroy%2C+update_account_admin_role&amp;filter[tags]=26&amp;include=account%2C+roles%2C+workspaces%2C+absence_types%2C+tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
permissions: update, destroy, update_account_admin_role
filter: {&quot;tags&quot;=&gt;&quot;26&quot;}
include: account, roles, workspaces, absence_types, tags
```


| Name | Description |
|:-----|:------------|
| permissions  | User Permissions |
| filter  | Filter |
| include  | Relationships details |
| fields  | Only return specfic attributes |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "93",
      "type": "user",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "email": "waldo@collins.name",
        "username": "Sarina Treutel",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 7,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "vm8n",
        "locale": null,
        "status": "active",
        "assumed_role": "employee",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [

          ]
        },
        "roles": {
          "data": [
            {
              "id": "1",
              "type": "role"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [

          ]
        },
        "tags": {
          "data": [
            {
              "id": "26",
              "type": "tag"
            }
          ]
        },
        "custom_field_values": {
          "data": [

          ]
        },
        "last_action": {
          "data": null
        }
      }
    }
  ],
  "included": [
    {
      "id": "1026",
      "type": "account",
      "attributes": {
        "phone": "+492204948890",
        "country": null,
        "locale": "de",
        "account_name": "Wallstab-Lutje",
        "created_at": "2023-01-30T11:21:41Z",
        "updated_at": "2023-01-30T11:21:41Z"
      }
    },
    {
      "id": "1",
      "type": "role",
      "attributes": {
        "name": "employee",
        "localized_name": "Employee"
      }
    },
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    },
    {
      "id": "26",
      "type": "tag",
      "attributes": {
        "title": "24-fuchsia",
        "active": true,
        "external_id": null,
        "color": null
      },
      "relationships": {
        "workspace": {
          "data": {
            "id": "1071",
            "type": "workspace"
          }
        },
        "users": {
          "data": [
            {
              "id": "93",
              "type": "user"
            }
          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "104469e5-c66a-48be-ab7b-8025279e0a4a",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## returns user associated with default tag


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users?permissions=update%2C+destroy%2C+update_account_admin_role&amp;filter[tags]=29&amp;include=account%2C+roles%2C+workspaces%2C+absence_types%2C+tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
permissions: update, destroy, update_account_admin_role
filter: {&quot;tags&quot;=&gt;&quot;29&quot;}
include: account, roles, workspaces, absence_types, tags
```


| Name | Description |
|:-----|:------------|
| permissions  | User Permissions |
| filter  | Filter |
| include  | Relationships details |
| fields  | Only return specfic attributes |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "40",
      "type": "user",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2022-12-30",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 8,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "17hs",
        "locale": null,
        "status": "active",
        "assumed_role": "employee",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        },
        "roles": {
          "data": [
            {
              "id": "1",
              "type": "role"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [
            {
              "id": "29",
              "type": "tag"
            }
          ]
        },
        "custom_field_values": {
          "data": [

          ]
        },
        "last_action": {
          "data": null
        }
      }
    }
  ],
  "included": [
    {
      "id": "1026",
      "type": "account",
      "attributes": {
        "phone": "+492204948890",
        "country": null,
        "locale": "de",
        "account_name": "Wallstab-Lutje",
        "created_at": "2023-01-30T11:21:41Z",
        "updated_at": "2023-01-30T11:21:41Z"
      }
    },
    {
      "id": "1",
      "type": "role",
      "attributes": {
        "name": "employee",
        "localized_name": "Employee"
      }
    },
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    },
    {
      "id": "1028",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 1_759",
        "kind": "vacation"
      }
    },
    {
      "id": "29",
      "type": "tag",
      "attributes": {
        "title": "27-orange",
        "active": true,
        "external_id": null,
        "color": null
      },
      "relationships": {
        "workspace": {
          "data": {
            "id": "1074",
            "type": "workspace"
          }
        },
        "users": {
          "data": [
            {
              "id": "40",
              "type": "user"
            }
          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "54477f48-1090-43f7-aa4d-4f51ab332d3a",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## returns users associated with multiple tag


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users?permissions=update%2C+destroy%2C+update_account_admin_role&amp;filter[tags]=31%2C+30&amp;include=account%2C+roles%2C+workspaces%2C+absence_types%2C+tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
permissions: update, destroy, update_account_admin_role
filter: {&quot;tags&quot;=&gt;&quot;31, 30&quot;}
include: account, roles, workspaces, absence_types, tags
```


| Name | Description |
|:-----|:------------|
| permissions  | User Permissions |
| filter  | Filter |
| include  | Relationships details |
| fields  | Only return specfic attributes |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 2
200 OK
```


```json
{
  "data": [
    {
      "id": "40",
      "type": "user",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "email": "gail.block@jones.biz",
        "username": "Enrico Schultz",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2022-12-30",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 8,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "17hs",
        "locale": null,
        "status": "active",
        "assumed_role": "employee",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        },
        "roles": {
          "data": [
            {
              "id": "1",
              "type": "role"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [
            {
              "id": "1028",
              "type": "absence_type"
            }
          ]
        },
        "tags": {
          "data": [
            {
              "id": "31",
              "type": "tag"
            }
          ]
        },
        "custom_field_values": {
          "data": [

          ]
        },
        "last_action": {
          "data": null
        }
      }
    },
    {
      "id": "95",
      "type": "user",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "email": "roberta.lockman@rowe.biz",
        "username": "Mr. Sanford Bernier",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 4,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "82j2",
        "locale": null,
        "status": "active",
        "assumed_role": "employee",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [

          ]
        },
        "roles": {
          "data": [
            {
              "id": "1",
              "type": "role"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [

          ]
        },
        "tags": {
          "data": [
            {
              "id": "30",
              "type": "tag"
            }
          ]
        },
        "custom_field_values": {
          "data": [

          ]
        },
        "last_action": {
          "data": null
        }
      }
    }
  ],
  "included": [
    {
      "id": "1026",
      "type": "account",
      "attributes": {
        "phone": "+492204948890",
        "country": null,
        "locale": "de",
        "account_name": "Wallstab-Lutje",
        "created_at": "2023-01-30T11:21:41Z",
        "updated_at": "2023-01-30T11:21:41Z"
      }
    },
    {
      "id": "1",
      "type": "role",
      "attributes": {
        "name": "employee",
        "localized_name": "Employee"
      }
    },
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            }
          ]
        }
      }
    },
    {
      "id": "1028",
      "type": "absence_type",
      "attributes": {
        "title": "Holiday 1_759",
        "kind": "vacation"
      }
    },
    {
      "id": "31",
      "type": "tag",
      "attributes": {
        "title": "29-mauve",
        "active": true,
        "external_id": null,
        "color": null
      },
      "relationships": {
        "workspace": {
          "data": {
            "id": "1076",
            "type": "workspace"
          }
        },
        "users": {
          "data": [
            {
              "id": "40",
              "type": "user"
            }
          ]
        }
      }
    },
    {
      "id": "30",
      "type": "tag",
      "attributes": {
        "title": "28-champagne",
        "active": true,
        "external_id": null,
        "color": null
      },
      "relationships": {
        "workspace": {
          "data": {
            "id": "1075",
            "type": "workspace"
          }
        },
        "users": {
          "data": [
            {
              "id": "95",
              "type": "user"
            }
          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "ef941290-a7ad-471c-a597-2cedfc5e573b",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 2
  }
}
```



## returns user associated with working area


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users?permissions=update%2C+destroy%2C+update_account_admin_role&amp;filter[areas]=1056&amp;include=account%2C+roles%2C+workspaces%2C+absence_types%2C+tags
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
permissions: update, destroy, update_account_admin_role
filter: {&quot;areas&quot;=&gt;&quot;1056&quot;}
include: account, roles, workspaces, absence_types, tags
```


| Name | Description |
|:-----|:------------|
| permissions  | User Permissions |
| filter  | Filter |
| include  | Relationships details |
| fields  | Only return specfic attributes |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "96",
      "type": "user",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "email": "sandee@rempel.io",
        "username": "Derek Schoen",
        "tablet_pin": null,
        "abbreviation": null,
        "hour_holidays": false,
        "time_zone": null,
        "initial_time_account": 0.0,
        "checkin_complete": null,
        "start_of_accounting": "2023-01-01",
        "saldo_type": 0,
        "salary": 0.0,
        "recognition_color_variant": 6,
        "hours_on_vacation_day": 0.0,
        "home_office": false,
        "calc_holiday_options": "target",
        "custom_holiday_hours": 0.0,
        "calc_vacation_options": "target",
        "working_sessions_creator": false,
        "staff_number": null,
        "external_id": null,
        "birthday": null,
        "identifier_pin": "k912",
        "locale": null,
        "status": "active",
        "assumed_role": "employee",
        "running_time_tracking": null,
        "remaining_vacation_days_this_year": 0,
        "avatar": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
        "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
      },
      "relationships": {
        "account": {
          "data": {
            "id": "1026",
            "type": "account"
          }
        },
        "areas": {
          "data": [
            {
              "id": "1056",
              "type": "area"
            }
          ]
        },
        "roles": {
          "data": [
            {
              "id": "1",
              "type": "role"
            }
          ]
        },
        "workspaces": {
          "data": [
            {
              "id": "1028",
              "type": "workspace"
            }
          ]
        },
        "current_absence": {
          "data": null
        },
        "absence_types": {
          "data": [

          ]
        },
        "tags": {
          "data": [
            {
              "id": "32",
              "type": "tag"
            }
          ]
        },
        "custom_field_values": {
          "data": [

          ]
        },
        "last_action": {
          "data": null
        }
      }
    }
  ],
  "included": [
    {
      "id": "1026",
      "type": "account",
      "attributes": {
        "phone": "+492204948890",
        "country": null,
        "locale": "de",
        "account_name": "Wallstab-Lutje",
        "created_at": "2023-01-30T11:21:41Z",
        "updated_at": "2023-01-30T11:21:41Z"
      }
    },
    {
      "id": "1",
      "type": "role",
      "attributes": {
        "name": "employee",
        "localized_name": "Employee"
      }
    },
    {
      "id": "1028",
      "type": "workspace",
      "attributes": {
        "permissions": {
          "update": true,
          "destroy": true,
          "update_account_admin_role": true
        },
        "name": "Company",
        "phone": null,
        "time_zone": "Berlin",
        "locale": "de",
        "avatar": "/avatars/original/missing.png",
        "external_id": null,
        "allow_employees_edit_working_session_area": true,
        "allow_employee_edit_punched_working_sessions": false,
        "allow_employees_tag_working_sessions": false,
        "checkin": null
      },
      "relationships": {
        "areas": {
          "data": [
            {
              "id": "1028",
              "type": "area"
            },
            {
              "id": "1056",
              "type": "area"
            }
          ]
        }
      }
    },
    {
      "id": "32",
      "type": "tag",
      "attributes": {
        "title": "30-blue",
        "active": true,
        "external_id": null,
        "color": null
      },
      "relationships": {
        "workspace": {
          "data": {
            "id": "1077",
            "type": "workspace"
          }
        },
        "users": {
          "data": [
            {
              "id": "96",
              "type": "user"
            }
          ]
        }
      }
    }
  ],
  "meta": {
    "request_id": "cf1b7efa-c3f6-4be7-b11f-0ee80e513e5f",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1
  }
}
```



## Applying sparse fieldsets returns only the requested fields


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users?permissions=update%2C+destroy%2C+update_account_admin_role&amp;include=areas&amp;fields[user]=username%2C+birthday&amp;fields[area]=name
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users`

#### Parameters


```json
permissions: update, destroy, update_account_admin_role
include: areas
fields: {&quot;user&quot;=&gt;&quot;username, birthday&quot;, &quot;area&quot;=&gt;&quot;name&quot;}
```


| Name | Description |
|:-----|:------------|
| permissions  | User Permissions |
| filter  | Filter |
| include  | Relationships details |
| fields  | Only return specfic attributes |
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 6
200 OK
```


```json
{
  "data": [
    {
      "id": "97",
      "type": "user",
      "attributes": {
        "username": "Bonnie Hills",
        "birthday": null
      },
      "relationships": {
      }
    },
    {
      "id": "40",
      "type": "user",
      "attributes": {
        "username": "Enrico Schultz",
        "birthday": null
      },
      "relationships": {
      }
    },
    {
      "id": "41",
      "type": "user",
      "attributes": {
        "username": "Fr. Ruben Plank",
        "birthday": null
      },
      "relationships": {
      }
    },
    {
      "id": "39",
      "type": "user",
      "attributes": {
        "username": "Freiherr Sami Grams",
        "birthday": null
      },
      "relationships": {
      }
    },
    {
      "id": "42",
      "type": "user",
      "attributes": {
        "username": "Jannes Scherer",
        "birthday": null
      },
      "relationships": {
      }
    },
    {
      "id": "43",
      "type": "user",
      "attributes": {
        "username": "Karina zu Pippig",
        "birthday": null
      },
      "relationships": {
      }
    }
  ],
  "included": [
    {
      "id": "1028",
      "type": "area",
      "attributes": {
        "name": "Lorenz vom Wollmann"
      },
      "relationships": {
      }
    }
  ],
  "meta": {
    "request_id": "12ab6c31-bdf9-44ba-968c-64d90ae345bd",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 6
  }
}
```



## Fetch current user


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/me
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/me`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "39",
    "type": "user",
    "attributes": {
      "permissions": null,
      "email": "marcel_littel@hand.net",
      "username": "Freiherr Sami Grams",
      "tablet_pin": null,
      "abbreviation": null,
      "hour_holidays": false,
      "time_zone": null,
      "initial_time_account": 0.0,
      "checkin_complete": null,
      "start_of_accounting": "2023-01-01",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 1,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": null,
      "external_id": null,
      "birthday": null,
      "identifier_pin": "86re",
      "locale": null,
      "status": "active",
      "assumed_role": "admin",
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": {
          "id": "1026",
          "type": "account"
        }
      },
      "areas": {
        "data": [

        ]
      },
      "roles": {
        "data": [
          {
            "id": "2",
            "type": "role"
          },
          {
            "id": "3",
            "type": "role"
          },
          {
            "id": "4",
            "type": "role"
          }
        ]
      },
      "workspaces": {
        "data": [
          {
            "id": "1028",
            "type": "workspace"
          }
        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [
          {
            "id": "1028",
            "type": "absence_type"
          }
        ]
      },
      "tags": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      },
      "last_action": {
        "data": null
      }
    }
  },
  "meta": {
    "request_id": "20fba862-01b1-4819-b5ae-780dbb4b2c99",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## An unauthenticated user gets an authorization error


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/me
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/me`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
401 Unauthorized
```


```json
{
  "errors": [
    {
      "status": "unauthorized",
      "source": {
        "pointer": "base"
      },
      "title": "You need to sign in or sign up before continuing."
    }
  ]
}
```



## Show user


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/40?permissions=update%2C+destroy%2C+update_account_admin_role
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/:user_id`

#### Parameters


```json
permissions: update, destroy, update_account_admin_role
```


| Name | Description |
|:-----|:------------|
| permissions  | User Permissions |
| fields  | Only return specfic attributes |
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "40",
    "type": "user",
    "attributes": {
      "permissions": {
        "update": true,
        "destroy": false,
        "update_account_admin_role": false
      },
      "email": "gail.block@jones.biz",
      "username": "Enrico Schultz",
      "tablet_pin": null,
      "abbreviation": null,
      "hour_holidays": false,
      "time_zone": null,
      "initial_time_account": 0.0,
      "checkin_complete": null,
      "start_of_accounting": "2022-12-30",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 8,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": null,
      "external_id": null,
      "birthday": null,
      "identifier_pin": "17hs",
      "locale": null,
      "status": "active",
      "assumed_role": "employee",
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": {
          "id": "1026",
          "type": "account"
        }
      },
      "areas": {
        "data": [
          {
            "id": "1028",
            "type": "area"
          }
        ]
      },
      "roles": {
        "data": [
          {
            "id": "1",
            "type": "role"
          }
        ]
      },
      "workspaces": {
        "data": [
          {
            "id": "1028",
            "type": "workspace"
          }
        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [
          {
            "id": "1028",
            "type": "absence_type"
          }
        ]
      },
      "tags": {
        "data": [

        ]
      },
      "custom_field_values": {
        "data": [

        ]
      },
      "last_action": {
        "data": null
      }
    }
  },
  "meta": {
    "request_id": "fa5dda2b-9089-4a10-be45-4385883c19e2",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## switch user’s role


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/switch_role
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/switch_role`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |



### Response

```plaintext

204 No Content
```




## Update a user as an Account Admin or a Workspace Admin


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id`

#### Parameters


```json
{"data":{"type":"user","attributes":{"username":"Updated Name","checkin_complete":true,"time_tracking_method_id":"3","area_ids":["1057"],"role_ids":["2","3"],"tag_ids":["36"]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "40",
    "type": "user",
    "attributes": {
      "permissions": null,
      "email": "gail.block@jones.biz",
      "username": "Updated Name",
      "tablet_pin": null,
      "abbreviation": null,
      "hour_holidays": false,
      "time_zone": null,
      "initial_time_account": 0.0,
      "checkin_complete": true,
      "start_of_accounting": "2022-12-30",
      "saldo_type": 0,
      "salary": 0.0,
      "recognition_color_variant": 8,
      "hours_on_vacation_day": 0.0,
      "home_office": false,
      "calc_holiday_options": "target",
      "custom_holiday_hours": 0.0,
      "calc_vacation_options": "target",
      "working_sessions_creator": false,
      "staff_number": null,
      "external_id": null,
      "birthday": null,
      "identifier_pin": "17hs",
      "locale": null,
      "status": "active",
      "assumed_role": "admin",
      "running_time_tracking": null,
      "remaining_vacation_days_this_year": 0,
      "avatar": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_thumb_url": "https://app.papershift.com/assets/dudegirl.png",
      "avatar_medium_url": "https://app.papershift.com/assets/dudegirl.png"
    },
    "relationships": {
      "account": {
        "data": {
          "id": "1026",
          "type": "account"
        }
      },
      "areas": {
        "data": [
          {
            "id": "1057",
            "type": "area"
          }
        ]
      },
      "roles": {
        "data": [
          {
            "id": "2",
            "type": "role"
          },
          {
            "id": "3",
            "type": "role"
          }
        ]
      },
      "workspaces": {
        "data": [
          {
            "id": "1028",
            "type": "workspace"
          }
        ]
      },
      "current_absence": {
        "data": null
      },
      "absence_types": {
        "data": [
          {
            "id": "1028",
            "type": "absence_type"
          }
        ]
      },
      "tags": {
        "data": [
          {
            "id": "36",
            "type": "tag"
          }
        ]
      },
      "custom_field_values": {
        "data": [

        ]
      },
      "last_action": {
        "data": null
      }
    }
  },
  "meta": {
    "request_id": "87a6d546-82a3-4350-b3c3-39f019ce3498",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## An Area Admin can not update a user


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id`

#### Parameters


```json
{"data":{"type":"user","attributes":{"username":"Updated Name","checkin_complete":true,"time_tracking_method_id":"3","area_ids":[],"role_ids":["2","3"],"tag_ids":[]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```

# Workspaces/TargetHours


## Create a regular Target Hour


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/40/target_hours
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/:user_id/target_hours`

#### Parameters


```json
{"data":{"type":"target_hour","attributes":{"rhythm_type":"weekly","start_date":"2022-01-20","is_week":true,"week":40.0,"is_month":false,"month":0.0,"target_limited":true,"is_mon":true,"mon":8.0,"is_tue":true,"tue":8.0,"is_wed":true,"wed":8.0,"is_thu":true,"thu":8.0,"is_fri":true,"fri":8.0,"is_sat":false,"sat":0.0,"is_sun":false,"sun":0.0,"per_day":true}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "98",
    "type": "target_hour",
    "attributes": {
      "permissions": null,
      "rhythm_type": "weekly",
      "start_date": "2022-01-20",
      "end_date": "2022-12-31",
      "target_limited": true,
      "reset_confirmed_absences": null,
      "total_hours": 40.0,
      "updated_by": "Freiherr Sami Grams",
      "is_week": true,
      "is_month": false,
      "is_mon": true,
      "mon": 8.0,
      "is_tue": true,
      "tue": 8.0,
      "is_wed": true,
      "wed": 8.0,
      "is_thu": true,
      "thu": 8.0,
      "is_fri": true,
      "fri": 8.0,
      "is_sat": false,
      "sat": 0.0,
      "is_sun": false,
      "sun": 0.0,
      "per_day": true
    }
  },
  "meta": {
    "request_id": "7ddaf818-b89d-47c2-8ecf-600baf5b15ff",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Create a Target Hour with free rhythm when the account does not have the permission for it


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/40/target_hours
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/:user_id/target_hours`

#### Parameters


```json
{"data":{"type":"target_hour","attributes":{"rhythm_type":"free","start_date":"2022-01-22","target_limited":true,"reset_confirmed_absences":false,"target_working_days_attributes":[{"hours":8.0,"day_type":"workday"},{"hours":0.0,"day_type":"freeday"}]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## User has a target hour with the same start date


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/40/target_hours
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/:user_id/target_hours`

#### Parameters


```json
{"data":{"type":"target_hour","attributes":{"rhythm_type":"weekly","start_date":"2022-01-20","is_week":true,"week":40.0,"is_month":false,"month":0.0,"target_limited":true,"is_mon":true,"mon":8.0,"is_tue":true,"tue":8.0,"is_wed":true,"wed":8.0,"is_thu":true,"thu":8.0,"is_fri":true,"fri":8.0,"is_sat":false,"sat":0.0,"is_sun":false,"sun":0.0,"per_day":true}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "start_date"
      },
      "title": "has to be unique."
    }
  ]
}
```



## Create free rhythm target hour without working days


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/40/target_hours
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/:user_id/target_hours`

#### Parameters


```json
{"data":{"type":"target_hour","attributes":{"rhythm_type":"free","start_date":"2022-01-22","target_limited":true,"reset_confirmed_absences":false,"target_working_days_attributes":[]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "Please provide atleast one working day details"
    }
  ]
}
```



## Create a free rhythm Target Hour


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/40/target_hours
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/:user_id/target_hours`

#### Parameters


```json
{"data":{"type":"target_hour","attributes":{"rhythm_type":"free","start_date":"2022-01-22","target_limited":true,"reset_confirmed_absences":false,"target_working_days_attributes":[{"hours":8.0,"day_type":"workday"},{"hours":0.0,"day_type":"freeday"}]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
201 Created
```


```json
{
  "data": {
    "id": "100",
    "type": "target_hour",
    "attributes": {
      "permissions": null,
      "rhythm_type": "free",
      "start_date": "2022-01-22",
      "end_date": "2022-12-31",
      "target_limited": true,
      "reset_confirmed_absences": false,
      "total_hours": 8.0,
      "updated_by": "Freiherr Sami Grams",
      "target_working_days": [
        {
          "id": "1",
          "day_type": "workday",
          "hours": 8.0
        },
        {
          "id": "2",
          "day_type": "freeday",
          "hours": 0.0
        }
      ]
    }
  },
  "meta": {
    "request_id": "41f8330d-11e4-4c2e-babd-24d10e926f74",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Can not create a target hour with an empty start_date


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/40/target_hours
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/:user_id/target_hours`

#### Parameters


```json
{"data":{"type":"target_hour","attributes":{"rhythm_type":"weekly","start_date":"","is_week":true,"week":40.0,"is_month":false,"month":0.0,"target_limited":true,"is_mon":true,"mon":8.0,"is_tue":true,"tue":8.0,"is_wed":true,"wed":8.0,"is_thu":true,"thu":8.0,"is_fri":true,"fri":8.0,"is_sat":false,"sat":0.0,"is_sun":false,"sun":0.0,"per_day":true}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "start_date"
      },
      "title": "can't be blank"
    }
  ]
}
```



## Employees are not allowed to create target hours


### Request

#### Endpoint

```plaintext
POST /api/v3/workspaces/1028/users/40/target_hours
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`POST /api/v3/workspaces/:workspace_id/users/:user_id/target_hours`

#### Parameters


```json
{"data":{"type":"target_hour","attributes":{"rhythm_type":"weekly","start_date":"2022-01-20","is_week":true,"week":40.0,"is_month":false,"month":0.0,"target_limited":true,"is_mon":true,"mon":8.0,"is_tue":true,"tue":8.0,"is_wed":true,"wed":8.0,"is_thu":true,"thu":8.0,"is_fri":true,"fri":8.0,"is_sat":false,"sat":0.0,"is_sun":false,"sun":0.0,"per_day":true}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Delete a regular Target Hour


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/users/40/target_hours/101
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/users/:user_id/target_hours/:target_hour_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| target_hour_id *required* | Target Hour ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "101",
    "type": "target_hour",
    "attributes": {
      "permissions": null,
      "rhythm_type": "weekly",
      "start_date": "2022-01-21",
      "end_date": "2022-12-31",
      "target_limited": false,
      "reset_confirmed_absences": null,
      "total_hours": 40.0,
      "updated_by": null,
      "is_week": true,
      "is_month": false,
      "is_mon": true,
      "mon": 8.0,
      "is_tue": true,
      "tue": 8.0,
      "is_wed": true,
      "wed": 8.0,
      "is_thu": true,
      "thu": 8.0,
      "is_fri": true,
      "fri": 8.0,
      "is_sat": false,
      "sat": 0.0,
      "is_sun": false,
      "sun": 0.0,
      "per_day": false
    }
  },
  "meta": {
    "request_id": "633abf40-f678-4eea-af1d-b09baf5816a4",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Target hour not found


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/users/40/target_hours/8146069402
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/users/:user_id/target_hours/:target_hour_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| target_hour_id *required* | Target Hour ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
404 Not Found
```


```json
{
  "errors": [
    {
      "status": "not_found",
      "source": {
        "pointer": "base"
      },
      "title": "Record can't be found!"
    }
  ]
}
```



## Cannot delete last target hour


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/users/39/target_hours/103
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/users/:user_id/target_hours/:target_hour_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| target_hour_id *required* | Target Hour ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
422 Unprocessable Entity
```


```json
{
  "errors": [
    {
      "status": "unprocessable_entity",
      "source": {
        "pointer": "base"
      },
      "title": "You should have at least one target hour"
    }
  ]
}
```



## Employees are not allowed to delete target hours


### Request

#### Endpoint

```plaintext
DELETE /api/v3/workspaces/1028/users/40/target_hours/104
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`DELETE /api/v3/workspaces/:workspace_id/users/:user_id/target_hours/:target_hour_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| target_hour_id *required* | Target Hour ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```



## Target Hours Index


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/40/target_hours
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/:user_id/target_hours`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 3
200 OK
```


```json
{
  "data": [
    {
      "id": "40",
      "type": "target_hour",
      "attributes": {
        "permissions": null,
        "rhythm_type": "weekly",
        "start_date": "2023-01-01",
        "end_date": null,
        "target_limited": false,
        "reset_confirmed_absences": null,
        "total_hours": 40.0,
        "updated_by": null,
        "is_week": true,
        "is_month": false,
        "is_mon": true,
        "mon": 8.0,
        "is_tue": true,
        "tue": 8.0,
        "is_wed": true,
        "wed": 8.0,
        "is_thu": true,
        "thu": 8.0,
        "is_fri": true,
        "fri": 8.0,
        "is_sat": false,
        "sat": 0.0,
        "is_sun": false,
        "sun": 0.0,
        "per_day": false
      }
    },
    {
      "id": "105",
      "type": "target_hour",
      "attributes": {
        "permissions": null,
        "rhythm_type": "weekly",
        "start_date": "2022-01-20",
        "end_date": "2022-06-20",
        "target_limited": false,
        "reset_confirmed_absences": null,
        "total_hours": 40.0,
        "updated_by": null,
        "is_week": true,
        "is_month": false,
        "is_mon": true,
        "mon": 8.0,
        "is_tue": true,
        "tue": 8.0,
        "is_wed": true,
        "wed": 8.0,
        "is_thu": true,
        "thu": 8.0,
        "is_fri": true,
        "fri": 8.0,
        "is_sat": false,
        "sat": 0.0,
        "is_sun": false,
        "sun": 0.0,
        "per_day": false
      }
    },
    {
      "id": "106",
      "type": "target_hour",
      "attributes": {
        "permissions": null,
        "rhythm_type": "free",
        "start_date": "2022-06-21",
        "end_date": "2022-12-31",
        "target_limited": false,
        "reset_confirmed_absences": null,
        "total_hours": 8.0,
        "updated_by": "Freiherr Sami Grams",
        "target_working_days": [
          {
            "id": "3",
            "day_type": "workday",
            "hours": 8.0
          },
          {
            "id": "4",
            "day_type": "freeday",
            "hours": 0.0
          }
        ]
      }
    }
  ],
  "meta": {
    "request_id": "a5392f72-09ee-4edd-9b8d-6c770dbc5750",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 3,
    "can_create_target_hours": true,
    "last_updated_at": "2023-01-30T12:22:45+01:00",
    "last_updated_by": "Freiherr Sami Grams"
  }
}
```



## With Permissions


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/40/target_hours?permissions=read%2C+update
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/:user_id/target_hours`

#### Parameters


```json
permissions: read, update
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 3
200 OK
```


```json
{
  "data": [
    {
      "id": "40",
      "type": "target_hour",
      "attributes": {
        "permissions": {
          "read": true,
          "update": true
        },
        "rhythm_type": "weekly",
        "start_date": "2023-01-01",
        "end_date": null,
        "target_limited": false,
        "reset_confirmed_absences": null,
        "total_hours": 40.0,
        "updated_by": null,
        "is_week": true,
        "is_month": false,
        "is_mon": true,
        "mon": 8.0,
        "is_tue": true,
        "tue": 8.0,
        "is_wed": true,
        "wed": 8.0,
        "is_thu": true,
        "thu": 8.0,
        "is_fri": true,
        "fri": 8.0,
        "is_sat": false,
        "sat": 0.0,
        "is_sun": false,
        "sun": 0.0,
        "per_day": false
      }
    },
    {
      "id": "107",
      "type": "target_hour",
      "attributes": {
        "permissions": {
          "read": true,
          "update": true
        },
        "rhythm_type": "weekly",
        "start_date": "2022-01-20",
        "end_date": "2022-06-20",
        "target_limited": false,
        "reset_confirmed_absences": null,
        "total_hours": 40.0,
        "updated_by": null,
        "is_week": true,
        "is_month": false,
        "is_mon": true,
        "mon": 8.0,
        "is_tue": true,
        "tue": 8.0,
        "is_wed": true,
        "wed": 8.0,
        "is_thu": true,
        "thu": 8.0,
        "is_fri": true,
        "fri": 8.0,
        "is_sat": false,
        "sat": 0.0,
        "is_sun": false,
        "sun": 0.0,
        "per_day": false
      }
    },
    {
      "id": "108",
      "type": "target_hour",
      "attributes": {
        "permissions": {
          "read": true,
          "update": true
        },
        "rhythm_type": "free",
        "start_date": "2022-06-21",
        "end_date": "2022-12-31",
        "target_limited": false,
        "reset_confirmed_absences": null,
        "total_hours": 8.0,
        "updated_by": "Freiherr Sami Grams",
        "target_working_days": [
          {
            "id": "5",
            "day_type": "workday",
            "hours": 8.0
          },
          {
            "id": "6",
            "day_type": "freeday",
            "hours": 0.0
          }
        ]
      }
    }
  ],
  "meta": {
    "request_id": "1ab68915-7a21-4017-9a88-6319cbdf552e",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 3,
    "can_create_target_hours": true,
    "last_updated_at": "2023-01-30T12:22:46+01:00",
    "last_updated_by": "Freiherr Sami Grams"
  }
}
```



## User has one target hour generated by default on user creation


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/40/target_hours
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/:user_id/target_hours`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Current-Page: 1
Page-Items: 20
Total-Pages: 1
Total-Count: 1
200 OK
```


```json
{
  "data": [
    {
      "id": "40",
      "type": "target_hour",
      "attributes": {
        "permissions": null,
        "rhythm_type": "weekly",
        "start_date": "2023-01-01",
        "end_date": null,
        "target_limited": false,
        "reset_confirmed_absences": null,
        "total_hours": 40.0,
        "updated_by": null,
        "is_week": true,
        "is_month": false,
        "is_mon": true,
        "mon": 8.0,
        "is_tue": true,
        "tue": 8.0,
        "is_wed": true,
        "wed": 8.0,
        "is_thu": true,
        "thu": 8.0,
        "is_fri": true,
        "fri": 8.0,
        "is_sat": false,
        "sat": 0.0,
        "is_sun": false,
        "sun": 0.0,
        "per_day": false
      }
    }
  ],
  "meta": {
    "request_id": "a8db3b82-3c5e-43d3-b059-b976fe85c4e4",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6",
    "link": 0,
    "current_page": 1,
    "page_items": 20,
    "total_pages": 1,
    "total_count": 1,
    "can_create_target_hours": true,
    "last_updated_at": "2023-01-30T12:21:43+01:00"
  }
}
```



## Show Target Hour


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/40/target_hours/109
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/:user_id/target_hours/:target_hour_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| target_hour_id *required* | Target Hour ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "109",
    "type": "target_hour",
    "attributes": {
      "permissions": null,
      "rhythm_type": "weekly",
      "start_date": "2022-01-20",
      "end_date": "2022-12-31",
      "target_limited": false,
      "reset_confirmed_absences": null,
      "total_hours": 40.0,
      "updated_by": null,
      "is_week": true,
      "is_month": false,
      "is_mon": true,
      "mon": 8.0,
      "is_tue": true,
      "tue": 8.0,
      "is_wed": true,
      "wed": 8.0,
      "is_thu": true,
      "thu": 8.0,
      "is_fri": true,
      "fri": 8.0,
      "is_sat": false,
      "sat": 0.0,
      "is_sun": false,
      "sun": 0.0,
      "per_day": false
    }
  },
  "meta": {
    "request_id": "ed7a06a0-7387-40a1-a90a-104de8f6fa0d",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Employees are allowed to read their own target hours


### Request

#### Endpoint

```plaintext
GET /api/v3/workspaces/1028/users/40/target_hours/110
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`GET /api/v3/workspaces/:workspace_id/users/:user_id/target_hours/:target_hour_id`

#### Parameters



| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| target_hour_id *required* | Target Hour ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "110",
    "type": "target_hour",
    "attributes": {
      "permissions": null,
      "rhythm_type": "weekly",
      "start_date": "2022-01-20",
      "end_date": "2022-12-31",
      "target_limited": false,
      "reset_confirmed_absences": null,
      "total_hours": 40.0,
      "updated_by": null,
      "is_week": true,
      "is_month": false,
      "is_mon": true,
      "mon": 8.0,
      "is_tue": true,
      "tue": 8.0,
      "is_wed": true,
      "wed": 8.0,
      "is_thu": true,
      "thu": 8.0,
      "is_fri": true,
      "fri": 8.0,
      "is_sat": false,
      "sat": 0.0,
      "is_sun": false,
      "sun": 0.0,
      "per_day": false
    }
  },
  "meta": {
    "request_id": "294f6538-0905-497e-b8f4-c819e2ad081c",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Update a regular Target Hour


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40/target_hours/111
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/target_hours/:target_hour_id`

#### Parameters


```json
{"data":{"type":"target_hour","attributes":{"rhythm_type":"weekly","start_date":"2022-02-21","is_week":true,"week":20.0,"is_month":false,"month":0.0,"target_limited":true,"is_mon":true,"mon":4.0,"is_tue":true,"tue":5.0,"is_wed":true,"wed":3.0,"is_thu":true,"thu":6.0,"is_fri":true,"fri":2.0,"is_sat":false,"sat":0.0,"is_sun":false,"sun":0.0}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| target_hour_id *required* | Target Hour ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "111",
    "type": "target_hour",
    "attributes": {
      "permissions": null,
      "rhythm_type": "weekly",
      "start_date": "2022-02-21",
      "end_date": "2022-12-31",
      "target_limited": true,
      "reset_confirmed_absences": null,
      "total_hours": 20.0,
      "updated_by": "Freiherr Sami Grams",
      "is_week": true,
      "is_month": false,
      "is_mon": true,
      "mon": 4.0,
      "is_tue": true,
      "tue": 5.0,
      "is_wed": true,
      "wed": 3.0,
      "is_thu": true,
      "thu": 6.0,
      "is_fri": true,
      "fri": 2.0,
      "is_sat": false,
      "sat": 0.0,
      "is_sun": false,
      "sun": 0.0,
      "per_day": false
    }
  },
  "meta": {
    "request_id": "f480b15d-16e6-4fe3-a437-7c9bb046b463",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Update a free rhythm Target Hour


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40/target_hours/112
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/target_hours/:target_hour_id`

#### Parameters


```json
{"data":{"type":"target_hour","attributes":{"rhythm_type":"free","start_date":"2022-02-22","target_limited":false,"reset_confirmed_absences":false,"target_working_days_attributes":[{"hours":7.0,"day_type":"workday"},{"hours":6.0,"day_type":"workday","_destroy":true},{"hours":0.0,"day_type":"freeday"}]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| target_hour_id *required* | Target Hour ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "112",
    "type": "target_hour",
    "attributes": {
      "permissions": null,
      "rhythm_type": "free",
      "start_date": "2022-02-22",
      "end_date": "2022-12-31",
      "target_limited": false,
      "reset_confirmed_absences": false,
      "total_hours": 7.0,
      "updated_by": "Freiherr Sami Grams",
      "target_working_days": [
        {
          "id": "7",
          "day_type": "workday",
          "hours": 7.0
        },
        {
          "id": "8",
          "day_type": "freeday",
          "hours": 0.0
        }
      ]
    }
  },
  "meta": {
    "request_id": "3284fc70-ea3d-433a-b7c1-c5c73f7d54a1",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Update a weekly rhythm to free rhythm Target Hour


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40/target_hours/113
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/target_hours/:target_hour_id`

#### Parameters


```json
{"data":{"type":"target_hour","attributes":{"rhythm_type":"free","start_date":"2022-02-22","target_limited":false,"reset_confirmed_absences":false,"target_working_days_attributes":[{"hours":7.0,"day_type":"workday"},{"hours":6.0,"day_type":"workday","_destroy":true},{"hours":0.0,"day_type":"freeday"}]}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| target_hour_id *required* | Target Hour ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "113",
    "type": "target_hour",
    "attributes": {
      "permissions": null,
      "rhythm_type": "free",
      "start_date": "2022-02-22",
      "end_date": "2022-12-31",
      "target_limited": false,
      "reset_confirmed_absences": false,
      "total_hours": 7.0,
      "updated_by": "Freiherr Sami Grams",
      "target_working_days": [
        {
          "id": "9",
          "day_type": "workday",
          "hours": 7.0
        },
        {
          "id": "10",
          "day_type": "freeday",
          "hours": 0.0
        }
      ]
    }
  },
  "meta": {
    "request_id": "1dff06a7-3639-42a8-a355-2ae8603fa0a5",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Update a weekly rhythm to free rhythm Target Hour


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40/target_hours/114
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/target_hours/:target_hour_id`

#### Parameters


```json
{"data":{"type":"target_hour","attributes":{"rhythm_type":"weekly","start_date":"2022-02-21","is_week":true,"week":20.0,"is_month":false,"month":0.0,"target_limited":true,"is_mon":true,"mon":4.0,"is_tue":true,"tue":5.0,"is_wed":true,"wed":3.0,"is_thu":true,"thu":6.0,"is_fri":true,"fri":2.0,"is_sat":false,"sat":0.0,"is_sun":false,"sun":0.0}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| target_hour_id *required* | Target Hour ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
200 OK
```


```json
{
  "data": {
    "id": "114",
    "type": "target_hour",
    "attributes": {
      "permissions": null,
      "rhythm_type": "weekly",
      "start_date": "2022-02-21",
      "end_date": "2022-12-31",
      "target_limited": true,
      "reset_confirmed_absences": null,
      "total_hours": 20.0,
      "updated_by": "Freiherr Sami Grams",
      "is_week": true,
      "is_month": false,
      "is_mon": true,
      "mon": 4.0,
      "is_tue": true,
      "tue": 5.0,
      "is_wed": true,
      "wed": 3.0,
      "is_thu": true,
      "thu": 6.0,
      "is_fri": true,
      "fri": 2.0,
      "is_sat": false,
      "sat": 0.0,
      "is_sun": false,
      "sun": 0.0,
      "per_day": false
    }
  },
  "meta": {
    "request_id": "7424a4d5-6bc2-4bab-ba60-2bc680504675",
    "git_commit": "7b76d14af1ad08fe9054f001812710db546da7c6"
  }
}
```



## Employees are not allowed to update target hours


### Request

#### Endpoint

```plaintext
PATCH /api/v3/workspaces/1028/users/40/target_hours/115
Content-Type: application/vnd.api+json
Authorization: Bearer YOUR_TOKEN_HERE
```

`PATCH /api/v3/workspaces/:workspace_id/users/:user_id/target_hours/:target_hour_id`

#### Parameters


```json
{"data":{"type":"target_hour","attributes":{"rhythm_type":"weekly","start_date":"2022-02-21","is_week":true,"week":20.0,"is_month":false,"month":0.0,"target_limited":true,"is_mon":true,"mon":4.0,"is_tue":true,"tue":5.0,"is_wed":true,"wed":3.0,"is_thu":true,"thu":6.0,"is_fri":true,"fri":2.0,"is_sat":false,"sat":0.0,"is_sun":false,"sun":0.0}}}
```


| Name | Description |
|:-----|:------------|
| workspace_id *required* | Workspace ID |
| user_id *required* | User ID |
| target_hour_id *required* | Target Hour ID |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
403 Forbidden
```


```json
{
  "errors": [
    {
      "status": "forbidden",
      "source": {
        "pointer": "base"
      },
      "title": "You are not authorized to perform this action."
    }
  ]
}
```