## 📊 Flujo Completo de Trabajo en Equipo

``` mermaid

graph TD
    A[🏠 Inicio] --> B[git clone]
    B --> C[git checkout main]
    C --> D[git pull origin main]
    D --> E[git checkout -b feature/nueva-funcionalidad]
    
    E --> F[💻 Trabajar en código]
    F --> G[git add .]
    G --> H[git commit -m 'mensaje']
    
    H --> I{¿Más cambios?}
    I -->|Sí| F
    I -->|No| J[git pull origin main --rebase]
    
    J --> K{¿Conflictos?}
    K -->|Sí| L[🔧 Resolver conflictos]
    L --> M[git add archivos-resueltos]
    M --> N[git rebase --continue]
    N --> O[git push origin feature/nueva-funcionalidad]
    
    K -->|No| O
    
    O --> P[🔀 Crear Merge Request en GitLab]
    P --> Q[👥 Code Review]
    Q --> R{¿Aprobado?}
    
    R -->|No| S[Hacer cambios solicitados]
    S --> F
    
    R -->|Sí| T[Merge a main]
    T --> U[git checkout main]
    U --> V[git pull origin main]
    V --> W[git branch -d feature/nueva-funcionalidad]
    W --> X[🎉 Fin del ciclo]
    
    style A fill:#90EE90
    style X fill:#90EE90
    style L fill:#FFB6C1
    style K fill:#FFD700
    style R fill:#FFD700
    style P fill:#87CEEB
    
```

## 🌳 Estructura de Ramas

``` mermaid
gitGraph
    commit id: "Initial commit"
    commit id: "Setup project"
    
    branch feature/login
    checkout feature/login
    commit id: "Add login form"
    commit id: "Add validation"
    
    checkout main
    branch feature/dashboard
    checkout feature/dashboard
    commit id: "Create dashboard"
    
    checkout main
    merge feature/login tag: "v1.1"
    
    checkout feature/dashboard
    commit id: "Add charts"
    
    checkout main
    merge feature/dashboard tag: "v1.2"
    
    branch hotfix/bug-123
    checkout hotfix/bug-123
    commit id: "Fix critical bug"
    
    checkout main
    merge hotfix/bug-123 tag: "v1.2.1"
```
## 🔄 Sincronización Diaria con el Equipo

``` mermaid
sequenceDiagram
    participant Dev1 as 👨‍💻 Desarrollador 1
    participant Local1 as 💻 Local
    participant Remote as ☁️ GitLab Remote
    participant Local2 as 💻 Local
    participant Dev2 as 👩‍💻 Desarrollador 2
    
    Dev1->>Local1: git checkout -b feature/A
    Dev1->>Local1: Hacer cambios
    Dev1->>Local1: git commit
    Dev1->>Remote: git push origin feature/A
    
    Dev2->>Local2: git checkout -b feature/B
    Dev2->>Local2: Hacer cambios
    Dev2->>Local2: git commit
    
    Note over Remote: Merge Request aprobado
    Remote->>Remote: feature/A merged to main
    
    Dev2->>Remote: git pull origin main --rebase
    
    alt Sin conflictos
        Remote-->>Local2: ✅ Actualización exitosa
        Dev2->>Remote: git push origin feature/B
    else Con conflictos
        Remote-->>Local2: ⚠️ Conflictos detectados
        Dev2->>Local2: Resolver conflictos
        Dev2->>Local2: git add + git rebase --continue
        Dev2->>Remote: git push origin feature/B
    end
```
