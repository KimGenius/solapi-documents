# Overview

쿨에스엠에스의 REST API Reference 내용을 담고 있습니다.

_참고_ REST는 Representational State Transfer의 약자로 API 연동 규격을 명확하게 정의되고 쉽게 구현 할 수 있습니다. [https://ko.wikipedia.org/wiki/REST](https://ko.wikipedia.org/wiki/REST)

쿨에스엠에스 SMS REST API 서버로 Request를 보내기 위해서 인증을 거쳐야 합니다.

[요청 인증](request-authentication.md) 를 참고하세요.

## Resource URL 구성

`https://rest.coolsms.co.kr/<ServiceName>/<Version>/<ResourcePath>`

`<ServiceName>`

* 메시지 API 4

`<Version>`

* 서비스 버전

`<ResourcePath>`

* 필요시 특정 리소스 경로를 나타냅니다

`<Action>`

* 서비스 혹은 리소스의 액션을 나타냅니다

## Types

이 문서에서 JSON 형식으로 구성된 Syntax를 설명할 때 사용되는 파라메터들의 형식을 아래와 같이 표기합니다.

`{Map}` - Key: Value 형식의 데이터를 담을 수 있습니다.

```javascript
{
  "key1": "value1",
  ...
}
```

`[Array]` - 배열 형식으로 같은 형식의 데이터를 담는 역할을 합니다.

```javascript
[
  "value1",
  "value2",
  ...
]
```

`"String"` - 문자열의 파라메터를 표현합니다.

```javascript
  "value"
```

`"Date"` - 날짜형식의 문자열을 표현합니다.

```javascript
  "2017-06-06 16:49:02"
```

`Number` - 숫자를 나타냅니다.

```javascript
  369
```

`"Boolean"` - 참, 거짓값을 문자열로 표현합니다.

```javascript
  "true"
  "false"
```

