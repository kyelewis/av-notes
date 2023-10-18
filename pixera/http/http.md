```lua
-- Used for helper.dump to print the respons
local helper = require "pixcHelper";

-- GET and POST requests
-- GET, POST, DELETE and PUT are supported directly
-- (You can use the CUSTOMREQUEST curl option to use others)
local get = pixc.getRoot().Utils.NetworkExtension.Http.execGetAsync;
local post = pixc.getRoot().Utils.NetworkExtension.Http.execPostAsync;

-- Get request
local url = "https://jsonplaceholder.typicode.com/posts/1";
local params = { isAGetRequest = "yes"};
local headers ={"Authorization: Bearer abc123"};
-- Same as easy_setopt_options but without the CURLOPT_ prefix
local curlOptions = { USERAGENT="my-user-agent/0.1" };

local success, code, responseHeaders, body = pcall(get, url, params, headers, curlOptions);

pixc.log("Call Success? " .. tostring(success));
pixc.log((success and "Status Code: " or "Error: ") .. math.floor(code));
pixc.log("Headers: " .. helper.dump(responseHeaders));
pixc.log("Body: " .. body);
 
-- Post request
local url = "https://jsonplaceholder.typicode.com/posts";
local body = nil;
local params = { title = "Hello", body = "World", userId = "1" };
local headers ={"Authorization: Bearer abc123"};
local curlOptions = nil;

local success, codeOrError, responseHeaders, body = pcall(post, url, body, params, headers, curlOptions);

pixc.log("Call Success? " .. tostring(success));
pixc.log((success and "Status Code: " .. math.floor(codeOrError) or "Error: " .. codeOrError ));
pixc.log("Headers: " .. helper.dump(responseHeaders));
pixc.log("Body: " .. body);
```
