# Send OSC Message using Driver Directly

```lua
-- Create OSC Driver Instance
local addInstance = pixc.getRoot().Utils.Driver.addInstance;
local isStreaming = false;
local success, osc = pcall(addInstance, isStreaming, "osc");

-- Create Network Socket
local createConnection = pixc.getRoot().Utils.Network.UDP.createConnection;
local success, socket = pcall(createConnection)

-- Generate OSC message
local success, result = pcall(osc.generateOsc, {}, "/test", 1);

-- Send OSC message
local remoteIp = "127.0.0.1";
local remotePort = 8000;
local success = pcall(socket.send, result, remoteIp, remotePort);
```
