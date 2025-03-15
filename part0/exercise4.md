sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server->>browser: HTTP 302, perform new GET https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate server

    Note right of server: 302 response prompts browser to reload notes page

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server->>browser: css file
    deactivate server
 
 
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server->>browser: js file
    deactivate server
    
    Note right of browser: browser begins executing javascript file that pulls JSON data from the server 
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server->>browser: [{"content": "hello", "date": "2025-03-15T03:06:21.010Z"}, ... ]
    deactivate server