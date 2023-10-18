```lua
-- Used for helper.dump to print the response headers
local helper = require "pixcHelper";

local get = pixc.getRoot().Utils.NetworkExtension.Http.execGetAsync;

local url = "http://localhost";

-- Same as easy_setopt_options but without the CURLOPT_ prefix
-- GET, POST, DELETE and PUT are supported directly,
-- but you can use the CUSTOMREQUEST curl option to use others
local curlOptions = { USERAGENT="my-user-agent/0.1", CUSTOMREQUEST="OPTIONS" };

local success, statusCodeOrError, responseHeaders, body = pcall(get, url, nil, nil, curlOptions);

if success then
  pixc.log("Status Code" .. math.floor(statusCodeOrError));
  pixc.log("Headers: " .. helper.dump(responseHeaders));
  pixc.log("Body: " .. body);
else
  pixc.log("Error: "  .. statusCodeOrError);
end
