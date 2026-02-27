
## ⚠️ Resolución de Conflictos - Proceso Detallado
``` mermaid
flowchart TD
    A[git pull origin main --rebase] --> B{¿Conflicto detectado?}
    
    B -->|No| C[✅ Push exitoso]
    
    B -->|Sí| D[⚠️ CONFLICT en archivo.js]
    D --> E[git status]
    E --> F[Abrir archivo en conflicto]
    
    F --> G["Buscar marcadores:<br/><<<<<<< HEAD<br/>=======<br/>>>>>>>> "]
    
    G --> H{Decisión}
    H -->|Mantener tu código| I[Eliminar código ajeno y marcadores]
    H -->|Mantener código ajeno| J[Eliminar tu código y marcadores]
    H -->|Combinar ambos| K[Integrar ambos códigos y eliminar marcadores]
    
    I --> L[git add archivo.js]
    J --> L
    K --> L
    
    L --> M[git rebase --continue]
    M --> N{¿Más conflictos?}
    
    N -->|Sí| D
    N -->|No| O[git push origin feature/mi-rama]
    O --> C
    
    style D fill:#FFB6C1
    style C fill:#90EE90
    style H fill:#FFD700
```

## 🚨 Comandos de Emergencia

``` mermaid
flowchart LR
    A[😱 Problema] --> B{¿Qué pasó?}
    
    B -->|Commit equivocado| C[git reset --soft HEAD~1]
    B -->|Cambios no deseados| D[git checkout -- archivo]
    B -->|Merge problemático| E[git merge --abort]
    B -->|Rebase problemático| F[git rebase --abort]
    B -->|Todo está mal| G[git stash<br/>git checkout main<br/>git pull]
    
    C --> H[✅ Arreglado]
    D --> H
    E --> H
    F --> H
    G --> H
    
    style A fill:#FF6B6B
    style H fill:#90EE90
```
