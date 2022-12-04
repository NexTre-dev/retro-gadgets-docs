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

## Events

### WifiWebResponseEvent : {RequestHandle `number`, ResponseCode `number`, IsError `boolean`, ErrorType `string`, ErrorMessage `string`, ContentType `string`, Text `string`, Type `string`}
Sent by the Wifi chip when a response is completed. Contains the following information:

- RequestHandle: ?
- ResponseCode: The [HTML response code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) provided by the request. Ideally, it should be `200`.
- IsError: Returns true if an error was encountered.
- ErrorMessage: If an error was encountered, displays its information.
- ContentType: Displays the [content type](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type) of the information returned. For example, an HTML document would have the ContentType of `text/html`.
- Text: What is returned; will depend on the content type of the page. A normal HTML page will return its source, whereas a RESTful API will return stringified JSON data.
- Type: ?

## Remarks

### How to use
The wifi chip takes advantage of CPU events, which can be hard to wrap your head around at first. The following is a brief tutorial on how to send a simple GET request.

First, place a Wifi chip and a CPU on your gadget and select your CPU with your Multitool:

![Selecting the CPU](../../../assets/docs/Wifi/SelectCPU.png)

Then, select EventChannels and set the first event channel to be your Wifi chip.

![Setting the event channel](../../../assets/docs/Wifi/EventChannel.gif)

Now go into your CPU's code and add the following function:

```lua
function eventChannel1(sender:Wifi, arg:WifiWebResponseEvent)
end
```

Remember that it MUST be global! Prepending the local keyword will prevent the CPU from recognizing it. Adding this kind of function will cause the CPU to automatically run it whenever the Wifi chip allocated to the first EventChannel finishes a request.

Now, insert code inside of the function to handle the request. You can use arg to access the data returned. For example, to print "OK" if the response code is 200, insert this into your function:

```lua
if arg.ResponseCode == 200 then
  log("OK")
end
```