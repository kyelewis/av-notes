```lua
-- Used for helper.dump to print the response headers
local helper = require "pixcHelper";
local execGetAsync = pixc.getRoot().Utils.NetworkExtension.Http.execGetAsync;

-- Get request
local url = "https://jsonplaceholder.typicode.com/posts/1";
local queryParams = { sort = "id" };
local headers = { "Authorization: Bearer abc123" };

local success, codeOrError, responseHeaders, body = pcall(execGetAsync, url, queryParams, headers);

if success then
  pixc.log("Status Code: " .. math.floor(codeOrError))
  pixc.log("Headers: " .. helper.dump(responseHeaders))
  pixc.log("Body: " .. body)
else
  pixc.log("Error: " .. codeOrError)
end
```
