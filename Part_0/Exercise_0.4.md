
```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: The browser creates a new note form data with the information typed when the save button is pressed

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server: Saves the received data at an array called "notes"
    server-->>browser: Requests a new HTTP GET to the browser
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET chrome-extension://bgpmiljelfnilfcfmoppijdkmccbccel/isolated-first.jst
    activate server
    server-->>browser: Receives JST document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
```
