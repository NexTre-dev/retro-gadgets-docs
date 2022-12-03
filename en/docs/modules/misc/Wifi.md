# Wifi
<img src="https://docs.retrogadgets.game/api/modules/Wifi.png" width="200" align="right">

Wifi is a chip that allows you to send and receive data other the internet. It can only be placed on the edge of a gadget and has two indicators. The one on the left activates when something is being uploaded, and the one on the right activates when something is being downloaded.

**⚠️ This page is incomplete and unverified.**

## Properties

### AccessDenied `boolean`
Is true when the Wifi chip is unable to function due to the gadget's permissions being improperly set. To remedy this, go into your gadget settings menu, click permissions, and then turn on the setting for data transmit.

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
Sends a custom `method` request to `url`. Should only be used if you know your way around HTTP.

### WebAbort(handle `number`) `boolean`
Cancel any running transmissions. `handle` is the number returned by request functions. You'll need to save them to a variable if you want to control them later.

```lua
local req = gdt.Wifi0:WebGet("http://example.com")
-- ...
gdt.Wifi0:WebAbort(req)
```

### GetWebUploadProgress(handle `number`) `number`
Return the current upload progress of the request specified, from 0 to 100.

### GetWebDownloadProgress(handle `number`) `number`
Return the current download progress of the request specified, from 0 to 100.

### ClearCookieCache()
Clear cookies from all websites.

### ClearUrlCookieCache(url `string`)
Clear cookies from a specific website.


## Event - `WifiWebResponseEvent`
The event emitted as part of the [CPU](./CPU.md) event system.

Sent when a web request is completed.

⚠️ This section requires further investigation.

### RequestHandle - `number`
### ResponseCode - `number`
### IsError - `boolean`
### ErrorType - `string`
### ErrorMessage - `string`
### ContentType - `string`
### Text - `string`
Text contains the body of the result, represented as a single string.