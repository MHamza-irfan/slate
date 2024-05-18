---
title: API V3 Documentation
language_tabs:
  - ruby

code_clipboard: true

---
# Detect Data peaks

Detecting data peaks in data

## Detect


### Request

#### Endpoint

```plaintext
POST /data_peaks/detect/
```

`POST /data_peaks/detect/`

#### Parameters

Content-Disposition: attachment; filename="data.csv"
Content-Type: text/csv


### Response

```plaintext
Content-Type: application/json; charset=utf-8
```


```json
[
  0,0,0,0,0,0,1,1,1,0,0,0,0
]
```
