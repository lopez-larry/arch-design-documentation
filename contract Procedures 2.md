# Contract Procedures
This procedure is especially important in:
* **MERN apps** (backend-to-frontend API boundaries)
* **Microservices** (domain-to-domain communication)
* **Data Mesh** (data product contracts)

## Updated Table: Contract Procedure & Tangible Deliverables

|  # | **Step**                         | **Goal**                                       | **Deliverable**                         | **Format / Location**                                                              |
| -: | -------------------------------- | ---------------------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------- |
|  1 | **Define Endpoints**             | List what operations the service exposes       | ✅ Route definitions                     | `routes/*.js` or `routes/index.js` (Express), or GraphQL SDL                       |
|  2 | **Define Request Schema**        | Validate incoming data structure               | ✅ Request validation schema             | `schemas/*.js` (Joi/Zod), or `schemas/*.json` (JSON Schema)                        |
|  3 | **Define Response Schema**       | Shape returned data (avoid overfetch)          | ✅ DTOs, `.select()` queries, or mappers | `dto/*.js`, `utils/formatResponse.js`, or inline `.select()` in controllers        |
|  4 | **Define Error Contract**        | Provide consistent error messages & structure  | ✅ Central error schema & error handler  | `utils/errorHandler.js`, `errors/*.json`, or error middleware                      |
|  5 | **Define Authorization Rules**   | Document and enforce who can access what       | ✅ Auth middleware & RBAC map            | `middleware/auth.js`, `roles.js`, or `controllers/authGuard.js`                    |
|  6 | **Declare Serialization Format** | Set the encoding rules for data sent over wire | ✅ JSON output shaped to spec            | Automatically handled, but standardized via `.toJSON()` overrides or GraphQL types |
|  7 | **Plan Versioning Strategy**     | Manage safe API evolution                      | ✅ Versioned routes or schema files      | Route files like `routes/v1/users.js`, version tags in OpenAPI (`v1`)              |
|  8 | **Publish Contract**             | Make it discoverable for consumers             | ✅ Interactive API docs UI               | `swagger.yaml` + Swagger UI, Redoc, or GraphQL Playground                          |

---

Below is a step-by-step **procedure** you can use to define a formal contract, including **routes, schemas, auth, validation, and serialization**.
---
## 🛠️ Procedure: How to Define the Components of a Contract
---
### **Step 1: Identify the Interaction Surface**
> What *must* be exposed to other systems or clients?

* What functionality are you exposing? (`GET /users`, `POST /orders`)
* Who are the consumers? (frontend, another domain, 3rd party)
* What is the **intent** of the interaction? (read data, submit form, trigger workflow)

🔹 Deliverable: A list of **endpoints or operations** to include. (Routes)
---

### **Step 2: Define the Request Contract**
> What does the consumer need to send?

* HTTP method (`GET`, `POST`, etc.)
* URL structure (path params, query params)
* Request body schema:

  * Required fields
  * Field types (string, int, array)
  * Constraints (min/max, format, regex)

🔹 Use JSON Schema, Joi, or Zod to define this formally.
---

### **Step 3: Define the Response Contract**
> What will the system return, and in what structure?

* Status codes (`200`, `201`, `404`, etc.)
* Response body fields

  * Which fields are returned?
  * What types and formats?
  * Are any fields optional, nullable, or nested?

🔹 Shape the response via DTOs, serializers, or `.select()` queries.
---

### **Step 4: Define Error Contracts**
> What does failure look like?

* Error structure: `{ error: "message", code: "ERR_TYPE" }`
* Field-level errors vs global errors
* Consistent format for all endpoints
* HTTP status code usage

🔹 Optionally use a shared `ErrorResponse` schema.
---

### **Step 5: Define Authorization & Access Rules**
> Who is allowed to access what?

* Required roles or scopes (e.g., admin-only routes)
* Auth methods (JWT, API key, OAuth)
* Field-level access restrictions (e.g., hide `isAdmin`)

🔹 Document with RBAC tables or auth middleware.
---

### **Step 6: Declare Serialization Format**
> How is the data encoded over the wire?

* Format: JSON (default in MERN), or Avro/Protobuf if optimized
* Media type: `application/json`, `application/vnd.api+json`, etc.
* Field naming: camelCase, snake_case?

🔹 Use standardized serializers or REST conventions.
---

### **Step 7: Versioning Strategy**
> How will you evolve the contract safely?

* URI versioning (`/api/v1/`)
* Semantic versioning for schema files
* Field deprecation warnings (`@deprecated` or `_legacy` fields)

🔹 Plan for backward compatibility.
---

### **Step 8: Publish the Contract**
> Make it discoverable and usable by others.

* **OpenAPI / Swagger** for REST
* **GraphQL SDL** for GraphQL
* Post to developer portal, API gateway, or schema registry
* Enable Swagger UI or GraphQL Playground for exploration

🔹 Contract is now *published* for self-service consumption.
---

## 📌 Summary Checklist

| Component            | Defined By                                 |
| -------------------- | ------------------------------------------ |
| Endpoints            | Express routes, GraphQL operations         |
| Request Schema       | Joi / Zod / JSON Schema                    |
| Response Schema      | DTOs, serializers, `.select()` in Mongoose |
| Errors               | Shared error format and status codes       |
| Auth Rules           | Middleware, RBAC map                       |
| Serialization Format | JSON, Avro, etc.                           |
| Versioning           | URI path or schema files                   |
| Publishing           | Swagger UI, OpenAPI, GraphQL Docs          |

