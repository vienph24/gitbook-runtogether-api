# NFC

{% swagger method="put" path="/nfc/active" baseUrl="https://api-prod.runtogether.net" summary="Active an NFC code" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="Bearer" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="hash-client" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="nfc_code" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="extra_data" type="Object" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```json
{
    "user_id": 54165,
    "activation_date": "2023-04-27 13:55:10.225",
    "id": 147975,
    "exp_date": "2024-04-21 13:55:10.224",
    "extra_data": {
        "name": "NFC Sneaker",
        "image": "https://run-image.s3.ap-southeast-1.amazonaws.com/run_newshoes/run_shoes_grey_NFC_852.png"
    },
    "sneaker": null,
    "nft": {
        "id": 1,
        "user_id": "1",
        "type": 1,
        "level": 1,
        "name": "Trial sneaker #-795345",
        "image": "https://run-image.s3.ap-southeast-1.amazonaws.com/run_newshoes/giay/trial.png",
        "quality": 1,
        "status": 1,
        "efficiency": 0,
        "luck": 0,
        "comfy": 0,
        "sturdence": 0,
        "energy": 2,
        "extra_data": null,
        "sturdence_remain": 100,
        "energy_remain": 2,
        "repair_remain": 9999,
        "is_box_open": 1,
        "img_box": "https://run-image.s3.ap-southeast-1.amazonaws.com/run_newshoes/giay/trial.png",
        "token_id": 795345,
        "chain_type": 3,
        "updated_time": "2022-12-22 03:27:01.941",
        "created_time": "2022-05-22 13:58:37.420",
        "used_energy": 0,
        "activation_date": "2022-08-12 11:41:40.121",
        "expired_date": "2023-08-07 11:41:40.121"
    }
}

```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="NFC code does not exist" %}
```json
{
    "error_code": "NFC_NOT_EXIST",
    "error_msg": {
        "vi": "Mã NFC không tồn tại",
        "en": "NFC code does not exist"
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="NFC code is old nfc code" %}
```json
{
    "error_code": "NFC_CODE_EXIST",
    "error_msg": null
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="NFC code invalid" %}
```json
{
    "error_code": "NFC_NOT_VALID",
    "error_msg": {
        "vi": "Mã NFC không hợp lệ!",
        "en": "NFC code invalid!",
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="NFC code has been activated" %}
```json
{
    "error_code": "NFC_ACTIVATED",
    "error_msg": {
        "vi": "NFC đã được kích hoạt",
        "en": "NFC code has been activated",
    }
}
```
{% endswagger-response %}
{% endswagger %}

* Endpoint: `PUT /nfc/active`
* Headers:
  * `Authorization: Bearer <access_token>`
  * `Content-Type: application/json`
  * `hash-client: <hash_value>` // secret\_key + endPoint + timestamp
* Body request (JSON)
  * nfc\_code:
    * type: string
    * required: true
  * extra\_data:
    * type: Object
    * required: false
* Response
  * error\_code: `NFC_CODE_EXIST`, reasons:
    * nfc\_code is incorrectly format
  * error\_code: `NFC_CODE_EXIST` reasons:
    * nfc\_code is old nfc code
  * error\_code: `NFC_NOT_VALID`, reasons:
    * nfc\_code is not shipped out
  * error\_code: `NFC_ACTIVATED`, reasons:
    * nfc\_code is activated by an user
  * error\_code is empty then the request was processed successfully
* For example,

```shell
curl --location --request PUT '<runtogether_url>/nfc/active' \
--header 'hash-client: <hash_value>' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <access_token>' \
--data-raw '{
    "nfc_code": "04:59:78:CA:D8:11:90",
    "extra_data": {}
}'
```

## Get NFC code is activated

* Endpoint: `GET /nfc/get-by-code`
* Headers:
  * `Authorization: Bearer <access_token>`
  * `Content-Type: application/json`
  * `hash-client: <hash_value>` // secret\_key + endPoint + timestamp
* Query param
  * nfc\_code:
    * type: string
    * required: true
* Response
  * error\_code: `NFC_NOT_EXIST`, reasons:
    * nfc\_code is not activated
  * nfc\_code is activated. The `error_code` is empty string and the `data` field is responds to an object
* For example, get a nfc\_code is not activated

```shell
curl --location '<runtogether_url>/nfc/get-by-code?nfc_code=04:59:78:CA:D8:11:91' \
--header 'hash-client: <hash_value>' \
--header 'Authorization: Bearer <access_token>'
```
