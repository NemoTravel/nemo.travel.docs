---
title: HostCommand
taxonomy:
    category:
        - docs
---

### Running the Terminal Command (HostCommand)

Execution of a terminal command in the GDS.

#### Request

##### Format Description

-  **Source** - ID of the package of requisites (source) under which you want to execute the command. Data type - 32-bit integer.
-  **SessionID** - ID of the session within which the command is to be executed. Data type - string.
-  **Command** - executed command. Data type - string.

##### Sample

```xml
<Source>1</Source>
<SessionID>9c47e9d3-6103-4495-bf22-f56379e5d2b1+0</SessionID>
<Command>AAA</Command>
```

#### Response

##### Format Description

-  **Response** - result of the terminal command execution. Data type - string.

##### Sample

```xml
<Response> FAAAA </ Response>
```
