# NFC

{% swagger method="put" path="/nfc/active" baseUrl="https://api-prod.runtogether.net" summary="" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="Bearer <access_token>" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
```
{
    "error_code": "NFC_NOT_EXIST",
    "error_msg": {
        "vi": "Mã NFC không tồn tại",
        "en": "NFC code does not exist"
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
