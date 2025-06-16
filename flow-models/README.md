# Data flow specifications

This folder contains standalone, data-oriented specifications describing how requests are processed across the system. Each file documents one self-contained flow, component responsibility, and interface contract.

## Contents

- [User authentication](user-authentication.md)  
  Authentication flow via TIM and issuance of client JWT.

- [Request validation](request-validation.md)  
  External request validation via Turvis before internal processing.

- [Manifest validation and OpenAPI](manifest-validation-and-openapi.md)  
  Structural validation of requests against DSL manifests and OpenAPI spec generation.

- [Identity validation](identity-validation.md)  
  Validation of JWTs using TIM before request execution.

- [Relational database queries](relational-database-queries.md)  
  Execution of database operations via Resql using DSL-defined logic.

- [X-road queries](xroad-queries.md)  
  Interfacing with external services via XTR and X-road.

- [Schema formatting](schema-formatting.md)  
  Response shaping and filtering using DataMapper.

- [Timed tasks execution](timed-tasks-execution.md)  
  Triggering automated workflows using CronManager.

All logic is enforced through DSL definitions and mediated by Ruuter. No business rules exist outside DSLs.
