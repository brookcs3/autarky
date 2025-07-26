# Architecture

```mermaid
flowchart TD
    CLI((autarky CLI)) --> UI[Ink + React UI]
    UI -->|dispatches| Store((Redux Store))
    UI --> Child1[Child Process: search]
    Child1 --> FS[(File System)]
    UI --> Child2[Child Process: delete]
    Child2 --> FS
    Store --> UI
```

The CLI is written using React components rendered via [Ink](https://github.com/vadimdemedes/ink). Heavy file system operations run in child processes to keep the UI responsive. Redux tracks chosen directories and user confirmations.
