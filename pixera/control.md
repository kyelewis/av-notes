# Library Path:
C:\Program Files\AV Stumpfl\Pixera\build_1-8-302\data\control_library_standard

# Lua Version
Lua 5.3

# pixcHelper
## Static
.isInitialized(object)
.isValidFunctionName(name)
.framesToHmsf(frames,fps)
.framesToHmfsTable(frames,fps)
.HmfsToFrames(hmsf,fps)
.dump(object)
.trimR(string)
.trimL(string)
.trim(string)
.stringSplit(string, separator)
.wrapCallback(callback)
.toBool(stringOrBoolean, default)
.dedupArray

## Class
local helper = createPixcHelper(picx, self());
// setmetatable, unknown

:getNum()
:setProperty(prop,value)
:loadAllProperties(props)
:getProperty(prop,default)
:addEmptyPropertyIfMissing(prop)
:clearProperty(prop)


## pixcProtocolHttp - HTTP Client
### Static
.urldecode(string)
.urlencode(string)

### Class
```lua
local http = createPixcProtocolHttp();
local success, statusCode, headerDict, content= :httpPost("http://localhost", "body", { parameter1: "Hello" }, { "Authorization": "Bearer abc123" }, { curloptions })

:httpGet
:httpGetCallback
:httpPost
:httpPostCallback
:httpDelete
:httpDeletCallback
:httpPut
:httpPutCallback
:sendMail
:sendMailCB
```

### Calling Directly
call(pixc.getRoot().Utils.NetworkExtension.Http.execGetCb, callback, url, parameterDict, customHeaderArray, curloptionDict)

# pixcCommon

pixcCommon.toJson - 1 arg
pixcCommon.execAttribute - 5 args
pixcCommon.getFirstCallRefResult - no args


# Code Block must knows!

- Prevent a value from being returned
pixc.supressCallRefs();

# LUA script sources:
C:\Program Files\AV Stumpfl\Pixera\build_1-8-302\Avio\Scripts\Lua

# Example module JSON
```json
{
 "api": [
  {
   "kind": "func", // func, ns, class
   "name": "helloWorld",
   "params": [
     { "name": "testInput", type: "string" },
   ],
   "result": {
     "name": "handle",
     "type": "handle"  // string, handle, int, bool, double, null, type[]
   },
   "body": "picx.log("\"Hello, World!\")" 
  },
  {
    "kind": "ns", // Namespace, known in the UI as a folder
    "name": "Unreal",
    "elems": [ { ... } ]
  },
  {
    "kind": "class", 
    "name": "Abc123",
   "deliver": "One.Two.Three",  // unknown, optional, used in functions- makes something available to the function? or used as the params?
    "elems": [ { ... } ]
 ],
 "cjv": {
  "h": 200.0,
  "w": 200.0,
  "x": 551.0,
  "y": 361.0
 },
 "definedExternally": false,
 "hostInfo": {
  "systemType": ""
 },
 "libraryExportPath": "O:\\Repos\\nui\\data\\control_library_standard\\Protocols\\SimpleHttpClient.json",
 "license": "1GNTlyr7sewU1l3S6nhV4h0N8TSPr5oX9mGNB4TQtzURUv6J4xXfYdHXFzdcJ3hPqJBugJQzSOBntTDHwBId9YUcVKowQLxY3XGNXgNvQJk=",
 "name": "SimpleHttpClient",
 "separateCode": false,
 "uiUrl": ""
}
```

# http Client:

## Direct using utils

local helper = require "pixcHelper";
local get = pixc.getRoot().Utils.NetworkExtension.Http.execGetAsync;
local post = pixc.getRoot().Utils.NetworkExtension.Http.execPostAsync;

-- Get request
local url = "https://httpbin.org/get";
local params = { };
local headers = { "Authorization: Bearer 123"}
local curlOptions = {};

local result = {pcall(get, url, params, headers, curlOptions)};
pixc.log(helper.dump(result))

-- Post request
local url = "https://httpbin.org/post";
local body = "Hi";
local params = { };
local headers = {"Authorization: Bearer 123"}
local curlOptions = {};

local result = {pcall(post, url, body, params, headers, curlOptions)};
pixc.log(helper.dump(result))

pixc.suppressReport();
pixc.suppressCallRefs();


