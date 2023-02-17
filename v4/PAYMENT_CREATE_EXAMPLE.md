## Go
```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://bsc.gogateway.io/api/v4/payment/create"

	payload := strings.NewReader("{\n  \"amountIn\": 500,\n  \"currency\": \"KZT\",\n  \"paymentMethod\": \"QIWIVISAMASTER\",\n  \"creditCard\": \"2200220022002200\",\n  \"email\": \"support@gogateway.io\",\n  \"lang\": \"en\"\n}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("GOGATEWAY-v4-token", "RYXwLOxxkKIYb165ZPEebSmJhO6RP1ni")
	req.Header.Add("Content-Type", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

## NodeJs
```js
const axios = require("axios").default;

const options = {
  method: 'POST',
  url: 'https://bsc.gogateway.io/api/v4/payment/create',
  headers: {'GOGATEWAY-v4-token': 'RYXwLOxxkKIYb165ZPEebSmJhO6RP1ni', 'Content-Type': 'application/json'},
  data: {
    amountIn: 500,
    currency: 'KZT',
    paymentMethod: 'QIWIVISAMASTER',
    creditCard: '2200220022002200',
    email: 'support@gogateway.io',
    lang: 'en'
  }
};

axios.request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

## Python
```python
import requests

url = "https://bsc.gogateway.io/api/v4/payment/create"

payload = {
    "amountIn": 500,
    "currency": "KZT",
    "paymentMethod": "QIWIVISAMASTER",
    "creditCard": "2200220022002200",
    "email": "support@gogateway.io",
    "lang": "en"
}
headers = {
    "GOGATEWAY-v4-token": "RYXwLOxxkKIYb165ZPEebSmJhO6RP1ni",
    "Content-Type": "application/json"
}

response = requests.request("POST", url, json=payload, headers=headers)

print(response.text)
```

## curl
```curl
curl -XPOST 'https://bsc.gogateway.io/api/v4/payment/create' \
     -H 'GOGATEWAY-v4-token: RYXwLOxxkKIYb165ZPEebSmJhO6RP1ni' \
     -H 'Content-Type: application/json' \
     -d '{"amountIn":500,"currency":"KZT","paymentMethod":"QIWIVISAMASTER","creditCard":"2200220022002200","email":"support@gogateway.io","lang":"en"}' \
     --compressed
```


## HTTP
```http
POST /api/v4/payment/create HTTP/1.1
GOGATEWAY-V4-Token: RYXwLOxxkKIYb165ZPEebSmJhO6RP1ni
Content-Type: application/json
Host: https://bsc.gogateway.io
Content-Length: 150

{
  "amountIn": 500,
  "currency": "KZT",
  "paymentMethod": "QIWIVISAMASTER",
  "creditCard": "2200220022002200",
  "email": "support@gogateway.io",
  "lang": "en"
}
```
