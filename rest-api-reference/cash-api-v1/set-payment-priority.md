---
description: 자동결제가 되는 카드를 설정합니다.
---

# 자동결제 우선순위 설정

{% api-method method="put" host="https://rest.coolsms.co.kr" path="/cash/v1/payment" %}
{% api-method-summary %}
Set Payment Priority
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="paymentIds" type="array" required=true %}
payment Id 가 담겨있는 배열입니다.  
인덱스가 낮을수록 우선순위가 높습니다.  
  
index = 0 이면, 첫 번째로 결제를 시도합니다.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
ValidationError \(paymentIds 에 중복된 값이 들어간 경우\)
{% endapi-method-response-example-description %}

```javascript
{
    "errorCode": "ValidationError",
    "errorMessage": "상황에 따른 메시지"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}


