# TDSBridge

## Description
This open source tool serves as our middleware.

Our current work involves inspecting the incoming queries in the form of a TDS message.

In `BridgedConnection.cs` line 90, incoming SQL TDS messages is stored in the variable `bBuffer`. The SQL statement within the message is encoded in Unicode, thus we tried to decode the entire bytestream from Unicode into string through:
```cs
string temp = Encoding.Unicode.GetString(bBuffer);
```

With the original query from the client being: `SELECT * FROM alpha.dbo.TSACCESSCO;`, we then attempted to modify db `alpha` to `bravo` through:

```cs
bBuffer = Encoding.Unicode.GetBytes(temp.Replace("alpha", "bravo"));
```

The above code replaces the query from database alpha to database bravo, and converts it back to Unicode before `SocketCouple.BridgeSQLSocket.Send()` is called.

This, however, did not work as intended since only the SQL statement data within the TDS message can be represented as string. The rest of the data however, are non-text bytestreams. Attempting to convert non-text bytestreams to string will yield undefined behaviours such as byte loss.

Our future plan to tackle this issue to only convert the SQL statement data within the TDS message to string, through a specific offset since network protocol packet headers are always fixed. A more in-depth explanation on this can be found within the findings report.