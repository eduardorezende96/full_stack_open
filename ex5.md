sequenceDiagram
    participant browser
    participant server

    Note right of browser: Browser loads SPA notes
    
    browser->>server: GET /exampleapp/spa
    activate server
    server-->>browser: HTML do SPA
    deactivate server
    
    browser->>server: GET /exampleapp/main.css
    activate server
    server-->>browser: Arquivo CSS
    deactivate server

    browser->>server: GET /exampleapp/spa.js
    activate server
    server-->>browser: Arquivo JavaScript
    deactivate server

    Note right of browser: Browser starts executing SPA's JavaScript
    
    browser->>server: GET /exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "Nota antiga", "date": "2023-09-25" }, ...]
    deactivate server

    Note right of browser: Browser renders notes

    Note right of browser: User adds a new note via forms

    browser->>server: POST /exampleapp/new_note (note=Nova Nota)
    activate server
    server-->>browser: Resposta em JSON com notas atualizadas
    deactivate server

    Note right of browser: Browser updates notes list
