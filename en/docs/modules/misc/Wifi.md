# Wifi
<img src="https://docs.retrogadgets.game/api/modules/Wifi.png" width="200" align="right">

Wifi is a chip that allows you to send and receive data other the internet. It can only be placed on the edge of a gadget and has two indicators. The one on the left activates when something is being uploaded, and the one on the right activates when something is being downloaded.

**⚠️ This page is incomplete and unverified.**

## Properties

### AccessDenied `boolean`

## Methods
Requests sent by the chip return a `number` that represents its handler, which can be used to represent it later.

### WebGet(url `string`) `number`
Sends a GET request to the specified URL.

### WebPutData(url `string`, data `string`) `number`
Sends a PUT request to the specified URL.

### WebPostData(url `string`, data `string`) `number`
Sends a POST request to the specified URL.

### WebPostForm(url `string`, form `{}`) `number`

### WebCustomRequest(url `string`, method `string`, customHeaderFields `{}`, contentType `string`, contentData `string`) `number`

### WebAbort(handle `number`) `boolean`

### GetWebUploadProgress(handle `number`) `number`

### GetWebDownloadProgress(handle `number`) `number`

### ClearCookieCache()

### ClearUrlCookieCache(url `string`)

## Events

### WifiWebResponseEvent : {RequestHandle `number`, ResponseCode `number`, IsError `boolean`, ErrorType `string`, ErrorMessage `string`, ContentType `string`, Text `string`, Type `string`}