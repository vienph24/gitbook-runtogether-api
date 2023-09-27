# NFC

## NFC active

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

CURL example:

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

## Get NFC info

{% swagger method="get" path="/nfc/get-by-code" baseUrl="https://api-prod.runtogether.net" summary="Get an NFC code's info" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="Bearer" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="hash-client" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="query" name="nfc_code" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```json
{
    "id": 1,
    "user_id": 42044,
    "nfc_code": "53:BE:2E:1B:10:00:01",
    "warranty": 180,
    "activation_date": "2022-08-23 03:20:56.900",
    "status": 1,
    "exp_date": "2023-08-18 03:20:56.900",
    "extra_data": {
        "name": "NFC Sneaker",
        "image": "https://run-image.s3.ap-southeast-1.amazonaws.com/run_newshoes/run_shoes_grey_NFC_852.png"
    },
    "created_time": "2022-06-16 07:05:38.957",
    "updated_time": "2022-12-26 09:04:12.008",
    "gift_type": 0,
    "nfc_old": null,
    "imei": null,
    "owner": {
        "email": "user01@gmail.com",
        "name": "User 01",
        "avatar": "https://runtogether-s3.s3.ap-southeast-1.amazonaws.com/f6ed1a90-b198-4109-9b1d-a083d687d77eScreenshot_20220408-141316_Brave.jpg"
    },
    "sneaker": {
        "id": 203155,
        "user_id": "48518",
        "type": 5,
        "level": 1,
        "name": "Nfc sneaker #-569819407",
        "image": "https://run-image.s3.ap-southeast-1.amazonaws.com/run_newshoes/run_shoes_grey_NFC_852.png",
        "quality": 1,
        "status": 1,
        "efficiency": 0,
        "luck": 0,
        "comfy": 0,
        "sturdence": 0,
        "energy": 9999,
        "extra_data": null,
        "sturdence_remain": 100,
        "energy_remain": 9999,
        "repair_remain": 9999,
        "is_box_open": 1,
        "img_box": "https://run-image.s3.ap-southeast-1.amazonaws.com/run_newshoes/run_shoes_grey_NFC_852.png",
        "token_id": 569819407,
        "chain_type": 4,
        "updated_time": "2022-12-22 03:21:38.561",
        "created_time": "2022-11-17 09:16:44.113",
        "used_energy": 0,
        "activation_date": "2022-11-17 09:16:44.112",
        "expired_date": "2023-11-12 09:16:44.112"
    },
    "nft": {
        "id": 202304,
        "user_id": "48518",
        "type": 3,
        "level": 1,
        "name": "NFC MetaRace #533552934",
        "image": "https://run-image.s3.ap-southeast-1.amazonaws.com/run_newshoes/giay/3_rare+852.png",
        "quality": 1,
        "status": 1,
        "efficiency": 16,
        "luck": 20,
        "comfy": 20,
        "sturdence": 21,
        "energy": 8,
        "extra_data": null,
        "sturdence_remain": 98.025,
        "energy_remain": 8,
        "repair_remain": 9999,
        "is_box_open": 1,
        "img_box": "https://run-image.s3.ap-southeast-1.amazonaws.com/run_newshoes/box/3_rare+852.png",
        "token_id": 533552934,
        "chain_type": 2,
        "updated_time": "2022-12-22 03:32:39.480",
        "created_time": "2022-11-01 06:51:37.727",
        "used_energy": 0,
        "activation_date": "2022-11-17 09:16:44.110",
        "expired_date": "2023-11-12 09:16:44.110"
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
{% endswagger %}

CURL example:

```shell
curl --location '<runtogether_url>/nfc/get-by-code?nfc_code=04:59:78:CA:D8:11:91' \
--header 'hash-client: <hash_value>' \
--header 'Authorization: Bearer <access_token>'
```
