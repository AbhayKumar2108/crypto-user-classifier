# Crypto User Classification Flowchart

This project classifies Twitter users as **Crypto Users (1) or Non-Crypto Users (0)** based on various factors.

```mermaid
graph TD;
    A[Start] --> B[Load Config & DB Connection]
    B --> C{Check if is_crypto_user Column Exists}
    C -- Yes --> D[Fetch Batch of Users]
    C -- No --> E[Add Column is_crypto_user]
    E --> D
    D --> F{Check Bio for Crypto Keywords}
    F -- Yes --> G[Set is_crypto_user = 1]
    F -- No --> H{Check Professional Category for Crypto Keywords}
    H -- Yes --> G
    H -- No --> I{Check if User Tweeted Crypto Keywords}
    I -- Yes --> G
    I -- No --> J{Check Cashtag Mentions}
    J -- Yes --> G
    J -- No --> K[Set is_crypto_user = 0]
    G --> L[Update Database]
    K --> L
    L --> M{More Users Left?}
    M -- Yes --> D
    M -- No --> N[End]
