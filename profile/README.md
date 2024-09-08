# Tower Online

A prototype for Tower Online, MMORPG

### Architecture
```mermaid
graph TD
    C[Client / Godot .NET]
    AS[Auth Server / FastAPI]
    MS[Main Server / C++]
    DB[(Database / MySQL)]

    C -->|HTTPS POST| AS
    C <-->|Serialize/Deserialize data with FlatBuffers| MS
    AS -.-> DB
    MS -.-> DB
```

### Client Authentication Sequence
```mermaid
sequenceDiagram
    participant C as Client
    participant A as Auth Server
    participant M as Main Server

    C->>A: Request token
    A->>C: Return token
    C->>A: Request characters info
    A->>C: Retrun characters info 
    C->>M: Request login with selected character and token
    M->>C: Login confirmation
    loop Start Data Transmission
        C<<->>M: 
    end
```
