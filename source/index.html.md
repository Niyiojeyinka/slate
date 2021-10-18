---
title: CREDITABLE ID API Reference

# language_tabs: # must be one of https://git.io/vQNgJ
#   - shell
#   - javascript
#   - html

toc_footers:
  - <a href='#'>Sign Up for a APP and Secret Key</a>
  - <a href='https://creditable.id'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: Creditable ID
    content: Creditable ID identity management service
---

# Introduction

We provide API for Authorization ,Authentication ,Profile Data retrieval and any other actions you can perform via the creditable ID [Dashboard](https://creditable.id) as a business.

# Products

## Authorization

> With creditable ID, you can perform a Face Authorization with ease.

This let you authorise logged in user with creditable ID

```html
<script src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
<link
  rel="stylesheet"
  href="https://res.cloudinary.com/open-source/raw/upload/v1628317436/creditableid/style_k1nsp7.css"
/>
```

in you footer , place the below snippet,and also edit the config object with user's email `userEmail` and your application `(appId)` with your application Id you created in your creditable ID dashboard.
[Learn to create Creditable Id APP how to create creditable ID integration application](https://creditable.id)

```html
<script>
  //config also will goes here
  const credConfig = {
    appId: "test-9876543234567",
    userEmail: "example@gmail.com",
    callback: function (payload) {
      console.log(payload);
    },
  };
</script>
<script
  type="text/babel"
  src="https://res.cloudinary.com/open-source/raw/upload/v1631266374/creditable_jsnfjy.js"
></script>
```

The call back payload will be in form of the snippet below on success

```javascript
//the parsed response
{
        email: "example@gmail.com",
        url: "captured image",
        authKey:"examleauthkeystring",
      }
```

The next step is to use the returned authKey and your secret key to confirm the authentication status.

<aside class="notice">
<!-- You must replace <code>meowmeowmeow</code> with your personal API key. -->
With creditable ID, you can perform a Face Authorization with ease
</aside>

## Authentication

> With creditable ID, you can perform a Face Authentication with ease.

This let you authenticate user: user will have to provide image and capture face

```html
<script src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
<link
  rel="stylesheet"
  href="https://res.cloudinary.com/open-source/raw/upload/v1628317436/creditableid/style_k1nsp7.css"
/>
```

in you footer , place the below snippet,and also edit the config object with your application `(appId)` with your application Id you created in your creditable ID dashboard.
[Learn to create Creditable Id APP how to create creditable ID integration application](https://creditable.id)

```html
<div id="cred" class="cred-hide"></div>
<!-- this div is needed for the popup modal -->
<script>
  //config also will goes here
  const credConfig = {
    appId: "test-9876543234567",
    userEmail: null, //important for authentication flow to be activated
    callback: function (payload) {
      console.log(payload);
    },
  };
</script>
<script
  type="text/babel"
  src="https://res.cloudinary.com/open-source/raw/upload/v1631266374/creditable_jsnfjy.js"
></script>
```

The call back payload will be in form of the snippet below on success

```javascript
//the parsed response
{
        email: "example@gmail.com",
        url: "captured image",
        authKey:"examleauthkeystring",
      }
```

The next step is to use the returned authKey and your secret key to confirm the authentication status.

<aside class="notice">
<!-- You must replace <code>meowmeowmeow</code> with your personal API key. -->
With creditable ID, you can perform a Face Authorization with ease
</aside>

## Verification (Confirm Authorization /Authentication Status)

This let you verify in your backend the status of an action using the `auth key` returned above and your `secret key` gotten from
your [Creditable ID Dashboard](https://creditable.id)

This endpoint retrieves all kittens.

### HTTP Request

`POST https://server.creditable.id/api/gateway/validate/face`

### Body Parameters

| Parameter | Required | Type   | Description                                                                                     |
| --------- | -------- | ------ | ----------------------------------------------------------------------------------------------- |
| authKey   | true     | string | The Auth key returned above unique for every successful attempt.                                |
| secretKey | true     | string | The business account secret key ,can be gotten from the Creditable ID business/staff dashboard. |

<aside class="others">
Remember verification are required to be done in the backend and client side
</aside>

<aside class="success">

200 OK SUCCESS RESPONSE :successful face match

</aside>

```json
//success response
{
  "result": 1,
  "message": "success",
  "data": {
    "email": "example@gmail.com",
    "status": "matched"
  }
}
```

<aside class="warning">

400 ERROR RESPONSE : face not matched or other error occured

</aside>

```json
//error response
{ "result": 0, "message": "Error : error message" }
```
