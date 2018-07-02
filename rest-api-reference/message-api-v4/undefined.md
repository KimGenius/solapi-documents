# 심플 메시지

여러 건을 한번에 발송 요청할 수 있는 그룹 메시지와 다르게 한 건의 메시지만 발송이 가능합니다.

HTTP Status Code 가 200 이어도 Response 의 `statusCode` 값이 2000 이 아닌 경우 문제가 있는 것으로 [Message Status Codes](../message-status-codes.md) 에서 상세한 설명을 참고하세요.

## Request

{% tabs %}
{% tab title="URI" %}
POST `https://rest.coolsms.co.kr/messages/v4/send`
{% endtab %}

{% tab title="Syntax" %}
```javascript
{
  "message": {
    "to": "String" /* required */,
    "from": "String", /* required */
    "text": "String", /* required */
    "type": "String", /* default 'AUTO' */
    "country": "String",
    "subject": "String",
    "imageId": "String",
    "kakaoOptions": {
      "senderKey": "String",
      "templateCode": "String",
      "buttonName": "String",
      "buttonUrl": "String",
      "disableSms": "Boolean"
    }
    "customFields": {
      ...
    }
  },
  "agent": {
    "appId": "String",
    "appVersion": "String",
    "osPlatform": "String",
    "sdkVersion": "String"
  }
}
```
{% endtab %}

{% tab title="Sample" %}
`$ curl -X POST https://rest.coolsms.co.kr/messages/v4/send --header "Authorization : HMAC-SHA256 ApiKey=[API_KEY], Date=[DATE], Salt=[UNIQID], Signature=[SIGNATRUE]" -d '{ "message": { { "to": "01000000000", "from": "021231234", "text": "테스트 메시지", "type":"sms", "customFields": { "myCustomField": "Value" } } } }'`
{% endtab %}

{% tab title="Description" %}
## Required Parameters

* `message` - Object 형식의 메시지 발송 정보
  * `to` - 수신번호 String 형식입니다.
  * `from` - 발신번호입니다.
  * `text` - 메시지 내용입니다.

## Optional Parameters

* `message` - Object 형식의 메시지 발송 정보
  * `type` - 메시지 타입 기본은 'AUTO'
  * `country` - 국가번호 기본은 '82'
  * `subject` - 타입이 LMS, MMS일 때 제목
  * `imageid` - 이미지 ID Link
  * `kakaoOptions` - 카카오톡 메시지 옵션
    * `senderKey` - 센더 키
    * `templateCode` - 템플릿 코드
    * `buttonName` - 버튼 이름, 10자 제한
    * `buttonUrl` - 버튼 URL, 100자 제한
    * `disableSms` - 알림톡 및 친구톡 발송이 실패하여도 문자메시지로 대체하여 발송하지 않습니다.
  * `customFilds` - 메시지 조회 시 사용할 수 있으며 필드명은 30자 값은 100자까지 가능합니다.
* `agent` - 사용한 앱에 대한 정보입니다.
  * `appId` - 앱 아이디
  * `appVersion` - 사용하는 앱의 버전
  * `osPlatform` - 앱 사용중인 운영체제 버전
  * `sdkVersion` - 사용하는 sdk 버전
{% endtab %}
{% endtabs %}

## Response

{% tabs %}
{% tab title="Syntax" %}
```javascript
{
    "groupId": String,
    "messageId": String,
    "statusCode": String,
    "statusMessage": String,
    "to": String,
    "type": String,
    "from": String,
    "customFields": Object
}
```
{% endtab %}

{% tab title="Sample" %}
```javascript
{
    "groupId": "G4V20180411123353C7LRLQN8VBSWMCV",
    "messageId": "M3V20170911164820TCBLKDEWPAO8VOK",
    "statusCode": "2000",            
    "statusMessage": "정상 접수(이통사로 접수 예정)",
    "to": "01000000000",
    "type": "SMS",
    "from": "01000000000",
    "customFields": {
      "myCustomField": "Value"
    }
}
```
{% endtab %}
{% endtabs %}

## Errors

`ValidationError(400)` - 정해진 형식에 맞게 Parameter를 입력 안할 시

`InvalidStatusCode(400)` - 접수가 실패한 경우입니다. 메시지의 아이디와 status code 가 반환됩니다.

`NotEnoughBalance(402)` - 보유하고 있는 포인트와 캐쉬를 합한 값이 발송시에 드는 금액보다 더 낮은 경우에 출력됩니다.

`InternalError(500)` - 일시적으로 처리량이 많아 처리되지 못한경우 출력입니다. 그룹 생성, 그룹 메시지 추가, 그룹 발송을 확인해주세요.
