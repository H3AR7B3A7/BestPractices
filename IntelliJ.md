# IntelliJ IDEA

## Live Reload

To have a Spring project live reload your changes:
- Add devtools dependencies to your pom.xml

    ```xml
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
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

*PS: For war deployments with a TomCat Server, choose for an exploded war. In configurations select 'update classes and resources' for **on frame deactivation**.
And in LiveReload enter the full path + application context as provided in the Deployment tab.*

## Auto Imports

- In your intellij IDEA go to: **Ctrl+Alt+S** ->Editor->General->Auto Import
  - Select optimize imports on the fly

- In your intellij IDEA go to: **Ctrl+Alt+S** ->Editor->Code Style->Java->Imports
  - Set Class count to use imports with '*' to 9999
  - Set Names count to use static imports with '*' to 9999