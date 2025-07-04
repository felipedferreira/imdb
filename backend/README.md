# IMDB Project

This is a .NET-based IMDB-like application with a clean architecture implementation.

## Project Structure

The solution is organized into several projects following clean architecture principles:

- **IMDB.Domain**: Contains the core business logic and domain entities
- **IMDB.Application**: Contains application logic, interfaces, and use cases
- **IMDB.Infrastructure**: Handles external concerns like data access and external services
- **IMDB.WebApi**: The API layer that handles HTTP requests and responses

## Technical Stack

- .NET 9.0
- Clean Architecture
- RESTful API

## Getting Started

### Prerequisites

- .NET 9.0 SDK
- Your preferred IDE (Visual Studio, Rider, VS Code)

### Building the Project

```bash
dotnet build
```

### Running the Application

```bash
cd IMDB.WebApi
dotnet run
```

## Architecture Diagram

```mermaid
flowchart TD
    %% Define the four layers as subgraphs for clarity
    subgraph WebApi ["1. WebApi (Presentation Layer)"]
      WA["Web API<br/>(Entry point,<br/>HTTP requests)"]
    end

    subgraph Application ["2. Application Layer"]
      AP["Application Layer<br/>(Use cases, Service logic)"]
    end

    subgraph Domain ["3. Domain Layer (Core)"]
      DM["Domain Layer<br/>(Entities, Value Objects,<br/>Interfaces e.g. IMovieRepository)"]
    end

    subgraph Infrastructure ["4. Infrastructure Layer"]
      INF["Infrastructure Layer<br/>(EF Core, SMTP, etc.)"]
    end

    %% Dependency arrows
    WA -->|Depends on| AP
    AP -->|Depends on| DM
    INF -->|Implements| DM
    WA -->|Wires up<br/>via DI| INF

    %% Layer boundaries (optional, for clarity)
    classDef subgraphClass fill:#f6faff,stroke:#222,stroke-width:2px;
    class WebApi,Application,Domain,Infrastructure subgraphClass;
```

The diagram above shows the dependencies between projects:

- IMDB.WebApi depends on both Application and Infrastructure layers
- IMDB.Application contains interfaces and depends only on the Domain layer
- IMDB.Infrastructure implements interfaces from Application and depends on Domain
- IMDB.Domain is the core and doesn't depend on any other layer

## Project Status

This project is currently under development.

## License

[Your chosen license]

---
*Note: This README is a template and should be updated with specific project details and requirements.*
