# Invitations

## Get list of invitations by contractor

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("http://example.com/contractors/contractor_id/invitations")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["accept"] = '*/*'

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://example.com/contractors/contractor_id/invitations"

headers = {'accept': '*/*'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl "http://example.com/contractors/contractor_id/invitations"
  -X "GET"
  -H "accept: */*"
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://example.com/contractors/contractor_id/invitations");
xhr.setRequestHeader("accept", "*/*");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
[
  {
      "data": {
        "account_id": "fd1333aa-ffff-49a2-a1b1-2a69e17f0e72",
        "status": "pending",
        "created_date": "2020-02-06T21:15:19.158699",
        "first_name": "joe",
        "last_name": "shmoe",
        "email": "joesemail@example.com",
        "mobile_phone": 1111111111
      }
  }
]
```

This endpoint Returns a list of invitations sent by a specified contractor.

### HTTP Request

`GET http://example.com/contractors/contractor_id/invitations`

### URL Parameters

Parameter | Description 
--------- | ----------- 
contractor_id | The Contractor Id

## Update an invitation's status

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("http://example.com/invitations/invitation_id?status=status")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Put.new(url)
request["accept"] = '*/*'

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://example.com/invitations/invitation_id"

querystring = {"status":"status"}

headers = {'accept': '*/*'}

response = requests.request("PUT", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl "http://example.com/invitations/invitation_id?status=status"
  -X "PUT"
  -H "accept: */*"
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("PUT", "http://example.com/invitations/invitation_id?status=status");
xhr.setRequestHeader("accept", "*/*");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
  {
    "data": {
        "account_id": null,
        "client_id": "77777777-8ddd-4fc9-904f-4ddddac59a0b",
        "enrollment_id": "73333330-ceb6-408e-8880-28c2cdd6e11f",
        "event_type": "/enrollments/events/invitations/invitation_accepted",
        "from_contractor_id": "27e58a95-c106-2222-8c9c-3555555653f0",
        "invitation_id": "c6eeeeee-353e-463d-bf58-26fccccc5e8b",
        "user_id": "faaaaaaa-5e8f-49a2-a1b1-2111117f0e72"
    }
}
```

This endpoint updates the status of a specific invitation.

### HTTP Request

`PUT http://example.com/invitations/invitation_id`

### URL Parameters

Parameter | Description 
--------- | ----------- 
invitation_id | The ID of invitation you want to update

### QUERY Parameters

Parameter | Description | Required
--------- | ----------- | --------
status | The new status of the invitation ("accepted" or "invited") | true

## Post a new Invitation

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("http://example.com/clients/client_id/invitations")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["accept"] = '*/*'
request["content-type"] = 'application/json'

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://example.com/clients/client_id/invitations"

headers = {
    'accept': "*/*",
    'content-type': "application/json"
    }

response = requests.request("POST", url, headers=headers)

print(response.text)
```

```shell
curl "http://example.com/clients/client_id/invitations"
  -X POST
  -H 'accept: */*, content-type: application/json'
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "http://example.com/clients/client_id/invitations");
xhr.setRequestHeader("accept", "*/*");
xhr.setRequestHeader("content-type", "application/json");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "activation_code": "C50DFA35-5BA9",
        "client_id": "9e37a877-873d-4fc9-904f-43df99999a0b",
        "email": "test11@invite.com",
        "enrollment_id": "71b77a30-ceb6-408e-9b80-28c26666611f",
        "event_type": "/enrollments/events/invitations/invitation_created",
        "external_id": null,
        "first_name": "Test11",
        "from_contractor_id": "27e58a95-c106-49b2-8c9c-3111115653f0",
        "invitation_id": "c6fb7d1e-353e-463d-bf58-26fe8888888b",
        "last_name": "Invite",
        "mobile_phone": "1111111111",
        "source": "icm",
        "user_id": "fd1a13aa-5e8f-49a2-a1b1-2aaaaaaf0e72"
    }
}
```

This endpoint posts a new contractor invitation to a client.

### HTTP Request

`POST http://example.com/clients/client_id/invitations`

### URL Parameters

Parameter | Description 
--------- | ----------- 
client_id | The ID of client posting a new invitation

### BODY Parameters

Parameter | Description | Required
--------- | ----------- | --------
first_name | First name of the contractor | true
last_name | Last name of the contractor | true
mobile_phone | Contractor's phone number | true
from_contractor_id | Contractor's id | false
email | Contractor's email | true
activiation_code | Contractor's activiation code | true

