### Request validation via Turvis

Before any processing begins, Ruuter receives the request (from GUI) and, if defined so, performs a mandatory validation step via an external component called Turvis. Turvis verifies that the request is structurally and semantically acceptable.

If Turvis returns anything other than HTTP 200, Ruuter halts the process immediately.

This step ensures:

- Incoming requests are pre-validated externally;
- Ruuter avoids wasteful processing of malformed or unauthorized data;
- All other components can assume they only receive pre-approved input.

```mermaid
sequenceDiagram
    participant EndClient
    participant GUI
    participant Ruuter
    participant Turvis

    Note over Ruuter, Turvis: Request validation before anything else

    EndClient->>GUI: Send request (with JWT)
    GUI->>Ruuter: Forward request
    Ruuter->>Turvis: Validate structure and constraints
    alt Turvis response is 200 OK
        Turvis-->>Ruuter: HTTP 200 OK
        Note right of Ruuter: Proceed - initiate Ruuter DSL
    else Any other status
        Turvis-->>Ruuter: Error response
        Ruuter-->>GUI: Halt with error
    end
```
