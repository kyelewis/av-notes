```lua
-- Used for helper.dump to print the response headers
local helper = require "pixcHelper";
local execPostAsync = pixc.getRoot().Utils.NetworkExtension.Http.execPostAsync;

-- Post request
local url = "https://jsonplaceholder.typicode.com/posts";
local body = nil;
local params = { title = "Hello", body = "World", userId = "1" };
local headers = { "Authorization: Bearer abc123" };

local success, codeOrError, responseHeaders, body = pcall(execPostAsync, url, body, params, headers);

if success then
  pixc.log("Status Code: " .. math.floor(codeOrError))
  pixc.log("Headers: " .. helper.dump(responseHeaders))
  pixc.log("Body: " .. body)
else
  pixc.log("Error: " .. codeOrError)
end
```
