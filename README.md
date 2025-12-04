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
    graph LR
    %% Styles
    classDef actorStyle fill:#fff,stroke:#333,stroke-width:2px;
    classDef boxStyle fill:#f9f9f9,stroke:#333,stroke-width:2px;
    classDef dbStyle fill:#e1f5fe,stroke:#0277bd,stroke-width:2px;

    %% Nodes
    User((Actor)):::actorStyle
    LB[Load Balancer]:::boxStyle
    Cache[Cache Server]:::boxStyle
    
    subgraph App_Servers [App Servers Cluster]
        S1[Server 1]:::boxStyle
        S2[Server 2]:::boxStyle
        S3[Server 3]:::boxStyle
    end

    subgraph Data_Layer [Data Persistence]
        DB[(Primary DB)]:::dbStyle
        Rep1[(Replica 1)]:::dbStyle
        Rep2[(Replica 2)]:::dbStyle
    end

    %% Connections
    User ==>|100% Traffic| LB
    LB -->|25%| S1
    LB -->|25%| S2
    LB -->|50%| S3

    %% Server Connections
    S1 & S2 & S3 --> DB
    S1 & S2 & S3 --> Cache
    
    %% Replication
    DB -.->|Replicate| Rep1
    DB -.->|Replicate| Rep2
