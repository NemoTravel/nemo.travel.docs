---
title: HostCommand
taxonomy:
    category:
        - docs
---

### Running the Terminal Command (HostCommand)

Used to execute the terminal command in the GDS.

#### Request

##### Format Description

-  **Source** - The ID of the package of requisites (source) under which you want to execute the command. The data type is an integer 32-bit number.
-  **SessionID** - The session ID, within which the command will be executed. The data type is a string.
-  **Command** - The execute command. The data type is a string.

##### Example

```xml
<Source>1</Source>
<SessionID>9c47e9d3-6103-4495-bf22-f56379e5d2b1+0</SessionID>
<Command>AAA</Command>
```

#### Response

##### Format Description

-  **Response** - The result of the terminal command execution. The data type is a string.

##### Example

```xml
<Response> FAAAA </ Response>
```
