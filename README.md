# html-portfolio
graph TD
    subgraph HLD [High Level Design (HLD)]
        direction TB
        A[Cloud Architecture] --- B[Microservices]
        B --- C[Database Schema]
        C --- D[API Gateway]
        style HLD fill:#e3f2fd,stroke:#1565c0
    end

    subgraph LLD [Low Level Design (LLD)]
        direction TB
        E[Class Diagram] --> F[Method Logic]
        F --> G[Data Types]
        G --> H[Error Handling Code]
        style LLD fill:#fff3e0,stroke:#e65100
    end
    
    HLD -.->|Defines Scope for| LLD
