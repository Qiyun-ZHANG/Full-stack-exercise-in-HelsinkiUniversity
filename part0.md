part0

In the section [Loading a page containing JavaScript - review](https://fullstackopen.com/en/part0/fundamentals_of_web_apps#loading-a-page-containing-java-script-review), the chain of events caused by opening the page https://studies.cs.helsinki.fi/exampleapp/notes is depicted as a [sequence diagram](https://www.geeksforgeeks.org/unified-modeling-language-uml-sequence-diagrams/)

The diagram was made as a GitHub Markdown-file using the [Mermaid](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams)-syntax, as follows:

```text
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
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

    Note right of browser: The browser executes the callback function that renders the notescopy
```

**Create a similar diagram** depicting the situation where the user creates a new note on the page https://studies.cs.helsinki.fi/exampleapp/notes by writing something into the text field and clicking the *Save* button.

If necessary, show operations on the browser or on the server as comments on the diagram.

The diagram does not have to be a sequence diagram. Any sensible way of presenting the events is fine.

#### 0.5: Single page app diagram

Create a diagram depicting the situation where the user goes to the [single-page app](https://fullstackopen.com/en/part0/fundamentals_of_web_apps#single-page-app) version of the notes app at https://studies.cs.helsinki.fi/exampleapp/spa.

#### 0.6: New note in Single page app diagram

Create a diagram depicting the situation where the user creates a new note using the single-page version of the app.

```
##create new note
note over browser:
User interacts with the page:
- Enters text in the text field
- Clicks the submit button
end note

browser->server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/notes
server-->browser: New note created successfully

note over browser:
Browser updates the UI with the new note
end note



##0.5: Single page app diagram
note over browser:
SPA version starts executing js-code
that handles navigation and requests
end note

browser->server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/spa.js
server-->browser: spa.js

note over browser:
Browser executes SPA event handlers
and dynamically updates the UI
end note




##0.6: New note in Single page app diagram
note over browser:
User interacts with the page:
- Enters text in the text field
- Clicks the submit button
end note

browser->server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/notes
server-->browser: New note created successfully

note over browser:
Browser updates the SPA UI with the new note
end note

```

![image-20240131195708087](C:\Users\zqy\AppData\Roaming\Typora\typora-user-images\image-20240131195708087.png)