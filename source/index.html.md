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

{
  @original_filename="Data points.csv",
  @content_type="text/csv",
  @headers="Content-Disposition: form-data;,
  "window_size"=>"1",
  "threshold"=>"1"
}


### Response

```plaintext
Content-Type: application/json; charset=utf-8
```


```json
[
  0,0,0,0,0,0,1,1,1,0,0,0,0
]
```
