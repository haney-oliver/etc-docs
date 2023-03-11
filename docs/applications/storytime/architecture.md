---
title: Architecture
icon: octicons/stack-16
---

``` mermaid
graph TB
  A[frontend-storytime] -->|HTTP Request| B{/public/v1/offer};
  B -->|Write offer details| C[(Database)]
  B -->|API Token| A
  A ---|HTTP w/ Auth| D{/admin/v1/story};
  D --- E[OpenAI API]
  D --> F[\ETC Bucket/]
  D --- G{storytime-diffuser};
  G --> F
  D -->|Update order fulfillment| C
```


<!-- Generator: Widdershins v4.0.1 -->
## api-storytime

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Base URLs:

* <a href="/api-storytime">/api-storytime</a>

### Authentication

- HTTP Authentication, scheme: bearer 

<h3 id="fastapi-default">Default</h3>

### Generate Story

<a id="opIdgenerate_story_admin_v1_story_post"></a>

> Code samples

=== "bash"
    ```shell
    # You can also use wget
    curl -X POST /api-storytime/admin/v1/story \
      -H 'Content-Type: application/json' \
      -H 'Accept: application/json' \
      -H 'Authorization: Bearer {access-token}'

    ```

=== "js"
    ```javascript
    const inputBody = '{
      "character": "string",
      "genre": "string",
      "setting": "string",
      "interests": [
        "string"
      ],
      "order_id": "string"
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json',
      'Authorization':'Bearer {access-token}'
    };

    fetch('/api-storytime/admin/v1/story',
    {
      method: 'POST',
      body: inputBody,
      headers: headers
    })
    .then(function(res) {
        return res.json();
    }).then(function(body) {
        console.log(body);
    });

    ```
=== "ruby"
    ```ruby
    require 'rest-client'
    require 'json'

    headers = {
      'Content-Type' => 'application/json',
      'Accept' => 'application/json',
      'Authorization' => 'Bearer {access-token}'
    }

    result = RestClient.post '/api-storytime/admin/v1/story',
      params: {
      }, headers: headers

    p JSON.parse(result)

    ```

=== "py"
    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json',
      'Authorization': 'Bearer {access-token}'
    }

    r = requests.post('/api-storytime/admin/v1/story', headers = headers)

    print(r.json())
    ```
=== "java"
    ```java
    URL obj = new URL("/api-storytime/admin/v1/story");
    HttpURLConnection con = (HttpURLConnection) obj.openConnection();
    con.setRequestMethod("POST");
    int responseCode = con.getResponseCode();
    BufferedReader in = new BufferedReader(
        new InputStreamReader(con.getInputStream()));
    String inputLine;
    StringBuffer response = new StringBuffer();
    while ((inputLine = in.readLine()) != null) {
        response.append(inputLine);
    }
    in.close();
    System.out.println(response.toString());

    ```
=== "go"
    ```go
    package main

    import (
          "bytes"
          "net/http"
    )

    func main() {

        headers := map[string][]string{
            "Content-Type": []string{"application/json"},
            "Accept": []string{"application/json"},
            "Authorization": []string{"Bearer {access-token}"},
        }

        data := bytes.NewBuffer([]byte{jsonReq})
        req, err := http.NewRequest("POST", "/api-storytime/admin/v1/story", data)
        req.Header = headers

        client := &http.Client{}
        resp, err := client.Do(req)
        // ...
    }

    ```

`POST /admin/v1/story`

> Body parameter

```json
{
  "character": "string",
  "genre": "string",
  "setting": "string",
  "interests": [
    "string"
  ],
  "order_id": "string"
}
```

<h4 id="generate-story-parameters">Parameters</h4>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[StoryRequest](#schemastoryrequest)|true|none|

> Example responses

> 200 Response

```json
null
```

<h4 id="generate-story-responses">Responses</h4>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

<h4 id="generate-story-responseschema">Response Schema</h4>

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
HTTPBearer
</aside>

### Healthcheck

<a id="opIdhealthcheck_public_v1_healthz_get"></a>

> Code samples
=== "bash"
    ```shell
    # You can also use wget
    curl -X GET /api-storytime/public/v1/healthz \
      -H 'Accept: application/json'

    ```

=== "js"
    ```javascript

    const headers = {
      'Accept':'application/json'
    };

    fetch('/api-storytime/public/v1/healthz',
    {
      method: 'GET',

      headers: headers
    })
    .then(function(res) {
        return res.json();
    }).then(function(body) {
        console.log(body);
    });

    ```

=== "ruby"
    ```ruby
    require 'rest-client'
    require 'json'

    headers = {
      'Accept' => 'application/json'
    }

    result = RestClient.get '/api-storytime/public/v1/healthz',
      params: {
      }, headers: headers

    p JSON.parse(result)

    ```

=== "py"
    ```python
    import requests
    headers = {
      'Accept': 'application/json'
    }

    r = requests.get('/api-storytime/public/v1/healthz', headers = headers)

    print(r.json())

    ```

=== "java"
    ```java
    URL obj = new URL("/api-storytime/public/v1/healthz");
    HttpURLConnection con = (HttpURLConnection) obj.openConnection();
    con.setRequestMethod("GET");
    int responseCode = con.getResponseCode();
    BufferedReader in = new BufferedReader(
        new InputStreamReader(con.getInputStream()));
    String inputLine;
    StringBuffer response = new StringBuffer();
    while ((inputLine = in.readLine()) != null) {
        response.append(inputLine);
    }
    in.close();
    System.out.println(response.toString());
    ```
=== "go"
    ```go
    package main

    import (
          "bytes"
          "net/http"
    )

    func main() {

        headers := map[string][]string{
            "Accept": []string{"application/json"},
        }

        data := bytes.NewBuffer([]byte{jsonReq})
        req, err := http.NewRequest("GET", "/api-storytime/public/v1/healthz", data)
        req.Header = headers

        client := &http.Client{}
        resp, err := client.Do(req)
        // ...
    }

    ```

`GET /public/v1/healthz`

> Example responses

> 200 Response

```json
{
  "ok": true,
  "message": "string"
}
```

<h4 id="healthcheck-responses">Responses</h4>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|[HealthcheckResponse](#schemahealthcheckresponse)|

<aside class="success">
This operation does not require authentication
</aside>

### Process Order

<a id="opIdprocess_order_public_v1_order_post"></a>

> Code samples

=== "bash"
    ```shell
    # You can also use wget
    curl -X POST /api-storytime/public/v1/order \
      -H 'Content-Type: application/json' \
      -H 'Accept: application/json'

    ```
=== "js"
    ```javascript
    const inputBody = '{
      "email": "string",
      "amount": 0,
      "billing_address": {
        "street_address": "string",
        "state": "string",
        "zip_code": "string",
        "city": "string"
      },
      "credit_card": {
        "number": "string",
        "expiration_month": "string",
        "expiration_year": "string",
        "security_code": "string",
        "name_on_card": "string"
      }
    }';
    const headers = {
      'Content-Type':'application/json',
      'Accept':'application/json'
    };

    fetch('/api-storytime/public/v1/order',
    {
      method: 'POST',
      body: inputBody,
      headers: headers
    })
    .then(function(res) {
        return res.json();
    }).then(function(body) {
        console.log(body);
    });

    ```
=== "ruby"
    ```ruby
    require 'rest-client'
    require 'json'

    headers = {
      'Content-Type' => 'application/json',
      'Accept' => 'application/json'
    }

    result = RestClient.post '/api-storytime/public/v1/order',
      params: {
      }, headers: headers

    p JSON.parse(result)

    ```
=== "python"
    ```python
    import requests
    headers = {
      'Content-Type': 'application/json',
      'Accept': 'application/json'
    }

    r = requests.post('/api-storytime/public/v1/order', headers = headers)

    print(r.json())

    ```

=== "java"
    ```java
    URL obj = new URL("/api-storytime/public/v1/order");
    HttpURLConnection con = (HttpURLConnection) obj.openConnection();
    con.setRequestMethod("POST");
    int responseCode = con.getResponseCode();
    BufferedReader in = new BufferedReader(
        new InputStreamReader(con.getInputStream()));
    String inputLine;
    StringBuffer response = new StringBuffer();
    while ((inputLine = in.readLine()) != null) {
        response.append(inputLine);
    }
    in.close();
    System.out.println(response.toString());

    ```
=== "go"
    ```go
    package main

    import (
          "bytes"
          "net/http"
    )

    func main() {

        headers := map[string][]string{
            "Content-Type": []string{"application/json"},
            "Accept": []string{"application/json"},
        }

        data := bytes.NewBuffer([]byte{jsonReq})
        req, err := http.NewRequest("POST", "/api-storytime/public/v1/order", data)
        req.Header = headers

        client := &http.Client{}
        resp, err := client.Do(req)
        // ...
    }

    ```

`POST /public/v1/order`

> Body parameter

```json
{
  "email": "string",
  "amount": 0,
  "billing_address": {
    "street_address": "string",
    "state": "string",
    "zip_code": "string",
    "city": "string"
  },
  "credit_card": {
    "number": "string",
    "expiration_month": "string",
    "expiration_year": "string",
    "security_code": "string",
    "name_on_card": "string"
  }
}
```

<h4 id="process-order-parameters">Parameters</h4>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[OrderDTO](#schemaorderdto)|true|none|

> Example responses

> 200 Response

```json
null
```

<h4 id="process-order-responses">Responses</h4>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful Response|Inline|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Validation Error|[HTTPValidationError](#schemahttpvalidationerror)|

<h4 id="process-order-responseschema">Response Schema</h4>

<aside class="success">
This operation does not require authentication
</aside>

### Schemas

<h3 id="tocS_BillingAddressDTO">BillingAddressDTO</h3>
<!-- backwards compatibility -->
<a id="schemabillingaddressdto"></a>
<a id="schema_BillingAddressDTO"></a>
<a id="tocSbillingaddressdto"></a>
<a id="tocsbillingaddressdto"></a>

```json
{
  "street_address": "string",
  "state": "string",
  "zip_code": "string",
  "city": "string"
}

```

#### BillingAddressDTO

Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|street_address|string|true|none|none|
|state|string|true|none|none|
|zip_code|string|true|none|none|
|city|string|true|none|none|

<h3 id="tocS_CreditCardDTO">CreditCardDTO</h3>
<!-- backwards compatibility -->
<a id="schemacreditcarddto"></a>
<a id="schema_CreditCardDTO"></a>
<a id="tocScreditcarddto"></a>
<a id="tocscreditcarddto"></a>

```json
{
  "number": "string",
  "expiration_month": "string",
  "expiration_year": "string",
  "security_code": "string",
  "name_on_card": "string"
}

```

#### CreditCardDTO

Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|number|string|true|none|none|
|expiration_month|string|true|none|none|
|expiration_year|string|true|none|none|
|security_code|string|true|none|none|
|name_on_card|string|true|none|none|

<h3 id="tocS_HTTPValidationError">HTTPValidationError</h3>
<!-- backwards compatibility -->
<a id="schemahttpvalidationerror"></a>
<a id="schema_HTTPValidationError"></a>
<a id="tocShttpvalidationerror"></a>
<a id="tocshttpvalidationerror"></a>

```json
{
  "detail": [
    {
      "loc": [
        "string"
      ],
      "msg": "string",
      "type": "string"
    }
  ]
}

```

#### HTTPValidationError

Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|detail|[[ValidationError](#schemavalidationerror)]|false|none|none|

<h3 id="tocS_HealthcheckResponse">HealthcheckResponse</h3>
<!-- backwards compatibility -->
<a id="schemahealthcheckresponse"></a>
<a id="schema_HealthcheckResponse"></a>
<a id="tocShealthcheckresponse"></a>
<a id="tocshealthcheckresponse"></a>

```json
{
  "ok": true,
  "message": "string"
}

```

#### HealthcheckResponse

Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ok|boolean|true|none|none|
|message|string|true|none|none|

<h3 id="tocS_OrderDTO">OrderDTO</h3>
<!-- backwards compatibility -->
<a id="schemaorderdto"></a>
<a id="schema_OrderDTO"></a>
<a id="tocSorderdto"></a>
<a id="tocsorderdto"></a>

```json
{
  "email": "string",
  "amount": 0,
  "billing_address": {
    "street_address": "string",
    "state": "string",
    "zip_code": "string",
    "city": "string"
  },
  "credit_card": {
    "number": "string",
    "expiration_month": "string",
    "expiration_year": "string",
    "security_code": "string",
    "name_on_card": "string"
  }
}

```

#### OrderDTO

Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|email|string|true|none|none|
|amount|integer|true|none|none|
|billing_address|[BillingAddressDTO](#schemabillingaddressdto)|true|none|none|
|credit_card|[CreditCardDTO](#schemacreditcarddto)|true|none|none|

<h3 id="tocS_StoryRequest">StoryRequest</h3>
<!-- backwards compatibility -->
<a id="schemastoryrequest"></a>
<a id="schema_StoryRequest"></a>
<a id="tocSstoryrequest"></a>
<a id="tocsstoryrequest"></a>

```json
{
  "character": "string",
  "genre": "string",
  "setting": "string",
  "interests": [
    "string"
  ],
  "order_id": "string"
}

```

#### StoryRequest

Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|character|string|true|none|none|
|genre|string|true|none|none|
|setting|string|true|none|none|
|interests|[string]|false|none|none|
|order_id|string|true|none|none|

<h3 id="tocS_ValidationError">ValidationError</h3>
<!-- backwards compatibility -->
<a id="schemavalidationerror"></a>
<a id="schema_ValidationError"></a>
<a id="tocSvalidationerror"></a>
<a id="tocsvalidationerror"></a>

```json
{
  "loc": [
    "string"
  ],
  "msg": "string",
  "type": "string"
}

```

#### ValidationError

Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|loc|[anyOf]|true|none|none|

anyOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|string|false|none|none|

or

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|integer|false|none|none|

continued

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|msg|string|true|none|none|
|type|string|true|none|none|

???+ question "What does the full workflow look like end to end?"
    User requests an order by sending an POST request to `/public/v1/order` with the following shape:
    ```json
    {
        "email": "asdf@email.com",
        "billing_address": {
            "street_address":"123 Home Rd.",
            "city": "City",
            "zip_code": "12345",
            "state": "FL"
        },
        "credit_card": {
            "expiration_month": "12",
            "expiration_year": "2027",
            "number": "4242 4242 4242 4242",
            "security_code": "111",
            "name_on_card": "some guy"
        }
    }
    ```
    The `order` service then idempotently inserts entities into the database in the following order:
    
    1. User
    2. Credit Card
    3. Billing Address
    4. Order

    The `order` returns a `token` which is used in the subsequent request as a Bearer token to the `/admin/v1/story` endpoint.
    The request to the story endpoint looks like:
    ```json
    {
      "character": "Fran",
      "interests": [
        "Formual-1 racing",
        "rock-climbing",
        "going to the beach"
      ],
      "genre": "mystery",
      "setting": "the country"
    }
    ```
    The `story` service then reaches out to the OpenAI API to generate a children's story, utilizing the user input provided by the request data.
    That generated story is then cleaned and stored in a linode bucket.

    In the future, there will be another endpoint that accepts a file uploaded from the user to be used be `storytime-diffuser` to generate coherent and consistent visuals to accompany the generated narrative. This has yet to be implemented.

    The `story` service then updates the state of the order associate with the token provided to fulfilled.
    Once the order is fulfilled, the user can read/download their story from the user portal.
