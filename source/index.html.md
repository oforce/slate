---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - invitations
  - errors

search: true
---

# Introduction

Welcome to OpenForce's open API documentaion. We are a super dope app that allows you to do super dope things. 
If you see issues with our documentation, please open pull requests at: https://github.com/oforce/slate.

Integrating with our API services enables you to achieve the data connectivity you need to more effectively manage contractors. Enjoy the benefits of reduced manual processes and obstacles while keeping your business current and responsive to the changing landscape.

Begin using our API services quickly by following the guide below.

# Getting Started

You can begin using our APIs after you've received your API credentials. Please email our support team directly to receive your credentials: clientcare@oforce.com

# Authentication

The Openforce API uses an OAuth2 authentication scheme. The Client Credentials Grant is the only supported oAuth2 Flow.

Requests to the API must be authenticated using a bearer token in the Authorization header.

Applications will obtain bearer tokens via the token endpoint: https://oforce.auth.us-west-2.amazoncognito.com/oauth2/token

When making a request to the token endpoint, the basic auth credentials must be a base64 encoded string in the format client_id:client_secret.

Aditional information can be found [here] (https://docs.aws.amazon.com/cognito/latest/developerguide/token-endpoint.html)

> Example of a sucessful authentication response:

```json
HTTP/1.1 200 OK
Content-Type: application/json
{
    "access_token":"eyJz9sdfsdfsdfsd",
    "token_type": "Bearer",
    "expires_in": 3600
}
```

<aside class="notice">
You can make little things like this that have code <code>meowmeowmeow</code> cool beans.
</aside>