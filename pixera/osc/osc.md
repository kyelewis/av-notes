-- Create OSC Driver Instance
local addInstance = pixc.getRoot().Utils.Driver.addInstance;
local isStreaming = false;
local oscDropLimit = 0;
local oscLogEveryDropped = 10;
local success, osc = pcall(addInstance, isStreaming, "osc", oscDropLimit, oscLogEveryDropped);

-- Create Network Socket
local createConnection = pixc.getRoot().Utils.Network.UDP.createConnection;
local localIp = "127.0.0.1";
local localPort = 0;
local success, socket = pcall(createConnection, localIp, localPort)

-- Generate OSC message
local success, result = pcall(osc.generateOsc, {"i"}, "/test", "1.0");

-- Send OSC message
local remoteIp = "127.0.0.1";
local remotePort = 59999;
local success = pcall(socket.send, result, remoteIp, remotePort);
