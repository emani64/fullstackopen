sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server->>browser: HTTP 201 resouce created, default action prevented
    deactivate server

    Note right of browser: Before sending the POST request to the server, the browser executes the JavaScript code to create a new note, add it to the list, and the list and rerender the list without needing to reload