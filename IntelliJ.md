# IntelliJ IDEA

## Live Reload

To have a Spring project live reload your changes:

- Add devtools dependencies to your pom.xml

    ```xml
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
        <optional>true</optional>
        <scope>runtime</scope>
    </dependency>
    ```

- In your intellij IDEA go to: **Ctrl+Alt+S** ->build,execution,deployment->compiler
    - Select build project automatically
- In your intellij IDEA: **Ctrl+Shift+A** ->registry
    - Select compiler.automake.allow.when.app.running
- Add LiveReload extension in your browser
    - Enter a rule for html (e.g. localhost:8080)
    - Enter a rule for css (e.g. localhost:8080/style.css)
    - ...

*PS: For war deployments with a TomCat Server, choose for an exploded war. In configurations select 'update classes and
resources' for **on frame deactivation**. And in LiveReload enter the full path + application context as provided in the
Deployment tab.*

## Auto Imports

- In your intellij IDEA go to: **Ctrl+Alt+S** ->Editor->General->Auto Import
    - Select optimize imports on the fly

- In your intellij IDEA go to: **Ctrl+Alt+S** ->Editor->Code Style->Java->Imports
    - Set Class count to use imports with '*' to 9999
    - Set Names count to use static imports with '*' to 9999

## Requests

We can create a scratch file by navigating to the project tab and creating a new file:

**Alt + 1** -> **Alt + Insert** -> Scratch file -> Http Request

```http request
GET localhost:8080/user?firstname=Bob&lastname=Builder&age=44
Accept: application/json
```

*We can then run our requests by clicking the play button from the scratch file.*

We can find more about using the HTTP client in Intellij
IDEA [here](https://www.jetbrains.com/help/idea/http-client-in-product-code-editor.html)

## Interesting Keyboard Shortcuts

- **Ctrl + K**: Commit
- **Ctrl + Shift + K**: Push
- **Alt + 1**: Project folder
- **Alt + Insert**: Generate file or code
- **Ctrl + I**: Implement interface
- **Ctrl + Alt + V**: Extract variable
- **Ctrl + Alt + M**: Extract method
- **Ctrl + Alt + F**: Extract field
- **Ctrl + B**: Find usage in code
- **Shift + F6**: Refactor name
- **Ctrl + Alt + S**: Open Settings
- **Ctrl + Shift + Space**: Code suggestions
- **Shift x2**: Search everywhere
- **Ctrl + F**: Find in file
- **Ctrl + Shift + F**: Find in project/module/directory/scope
- **Ctrl + R**: Find and replace in file
- **Ctrl + ALt + L**: Format file
- **Alt + Shift + Up/Down**: Move line
- **Ctrl + Shift + Up/Down**: Move block
- **Ctrl + D**: Duplicate line
- **Ctrl + /**: Comment out / Uncomment

*Some other functions do not have keyboard shortcuts, you might want to consider assigning some of these:*

- Extract interface