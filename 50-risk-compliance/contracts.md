# Contracts
A contract in a software system is a formal agreement that defines how components (services, clients, or domains) communicate with each other — including what data is exchanged, how, and under what rules.

## In System Terms, a Contract Includes:
| Layer                  | Description                                                           |
| ---------------------- | --------------------------------------------------------------------- |
| **Endpoints / Routes** | What actions are allowed (e.g., `GET /users`, `POST /login`)          |
| **Request Structure**  | What fields are required, optional, their types, and validation rules |
| **Response Structure** | What data is returned, in what format, and under what conditions      |
| **Error Format**       | Standard way to report problems (`400`, `422`, etc.)                  |
| **Auth Rules**         | Who is allowed to access what (roles, tokens, scopes)                 |
| **Data Serialization** | Agreed data format (e.g., JSON, GraphQL, Avro)                        |
| **Versioning**         | How the interface evolves without breaking clients                    |
| **Performance Bounds** | Optional: limits on payload size, rate, frequency                     |

## In a MERN Stack System
A contract defines:
- How the React frontend communicates with the Node.js backend
- How the backend routes enforce structure and validation (via models, middleware, DTOs)
- How data is serialized and shaped (e.g., user.name, not full user object)
- What errors or responses the frontend should expect


## In a Distributed System or Data Mesh
A contract allows:
- Other services or domains to safely consume your data
- Consumers to self-serve (no need to inspect source code)
- Strong boundaries so you can evolve safely without breaking others

## Why Contracts Matter
| Benefit              | Impact                                                       |
| -------------------- | ------------------------------------------------------------ |
|  **Loose Coupling**  | Services interact without knowing internals                  |
|  **Scalability**    | You can optimize data exchange (e.g., avoid overfetching)    |
|  **Security**       | Data access and shape are strictly controlled                |
|  **Version Control** | You can evolve your API without breaking consumers           |
|  **Discoverability** | Other teams can understand and use your API without meetings |
