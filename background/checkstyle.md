# Checkstyle Template & Usage

## Intro
Our team uses a **Checkstyle template** to enforce consistent coding standards across all robot code.  
This ensures readability, reduces errors, and makes peer reviews easier.

---

## 6️⃣ Rules Summary

Here is a summary of the coding rules enforced by our Checkstyle template:

- **Trailing Whitespace:** Warns on lines with trailing spaces (ignores comments).  
- **Braces:** All `if`, `else`, `while`, `for`, `do` statements must use braces.  
- **Nested If Depth:** Maximum of 3 levels to maintain readability.  
- **Javadoc Comments:**
  - Classes, interfaces, enums must have Javadoc.  
  - Public/protected methods must have Javadoc. Methods with `@Override` are skipped.  
  - Missing `@param`, `@return`, `@throws` tags allowed for flexibility.  
- **Brace Placement:** Opening brace `{` at end-of-line; closing brace `}` enforced.  
- **Naming Conventions:**
  - **Classes/Enums:** PascalCase (`DrivetrainSubsystem`)  
  - **Methods:** camelCase (`setMotorSpeed`)  
  - **Local Variables / Members / Parameters:** camelCase (`leftMotor`, `maxSpeed`, `speed`)  

---

## 1️⃣ Location of Template
- Place the `checkstyle.xml` file in your project:  
  - Recommended path: `config/checkstyle/checkstyle.xml`

---

## 2️⃣ Integrating Checkstyle with Gradle
1. Add the Checkstyle plugin in `build.gradle`:
```gradle
plugins {
    id 'checkstyle'
}

checkstyle {
    toolVersion = '10.12.2' // recommended version
    configFile = rootProject.file('config/checkstyle/checkstyle.xml')
}

tasks.withType(Checkstyle) {
    reports {
        xml.required = false
        html.required = true
        html.outputLocation = file("$buildDir/reports/checkstyle/checkstyle.html")
    }
}
```

### Create the checkstyle file

1. In your project, open the folder `config/checkstyle` (create it if it doesn’t exist).  
2. Create or edit `checkstyle.xml` with the following content:

```json
<?xml version="1.0"?>
<!DOCTYPE module PUBLIC
  "-//Checkstyle//DTD Checkstyle Configuration 1.3//EN"
  "https://checkstyle.org/dtds/configuration_1_3.dtd">

<module name="Checker">
  <!--
    RegexpSingleline:
    Checks each line for trailing whitespace,
    but skips lines that are comments (starting with //, /*, or * inside block comments).
    Severity set to "info" so it's a warning, not an error.
  -->
  <module name="RegexpSingleline">
    <property name="format" value="^(?!\s*(//|/\*|\*)).*\s+$"/>
    <property name="message" value="Line has trailing whitespace."/>
    <property name="severity" value="info"/>
  </module>

  <!--
    TreeWalker module analyzes Java AST (Abstract Syntax Tree).
    Most style checks are inside TreeWalker.
  -->
  <module name="TreeWalker">

    <!--
      NeedBraces:
      Enforces that all if, else, while, for, do statements use braces.
      Helps prevent bugs from single-line statements without braces.
    -->
    <module name="NeedBraces"/>

    <!--
      NestedIfDepth:
      Limits how deeply nested 'if' statements can be.
      Here max nesting is 3 levels deep to keep code readable.
    -->
    <module name="NestedIfDepth">
      <property name="max" value="3"/>
    </module>

    <!--
      JavadocType:
      Enforces Javadoc comments on classes, interfaces, enums.
      Allows missing @param tags inside class Javadocs since those don’t apply.
    -->
    <module name="JavadocType">
      <property name="allowMissingParamTags" value="true"/>
    </module>

    <!--
      JavadocMethod:
      Enforces Javadoc comments on methods with public or protected access.
      Allows missing param, return, and throws tags for flexibility.
      Skips methods annotated with @Override (no need to document inherited methods).
    -->
    <module name="JavadocMethod">
      <property name="accessModifiers" value="public, protected"/>
      <property name="allowMissingParamTags" value="true"/>
      <property name="allowMissingReturnTag" value="true"/>
      <property name="allowedAnnotations" value="Override"/>
    </module>


    <!--
      LeftCurly and RightCurly:
      Enforce brace placement.
      LeftCurly option "eol" means opening braces must be at end of the line, not next line.
    -->
    <module name="LeftCurly">
      <property name="option" value="eol"/>
    </module>
    <module name="RightCurly"/>

    <!--
      TypeName:
      Enforces class and enum names follow PascalCase convention.
    -->
    <module name="TypeName"/>

    <!--
      MethodName:
      Enforces method names follow camelCase convention.
    -->
    <module name="MethodName"/>

    <!--
      LocalVariableName:
      Enforces local variables follow camelCase naming.
    -->
    <module name="LocalVariableName">
      <property name="format" value="^[a-z][a-zA-Z0-9]*$"/>
    </module>

    <!--
      MemberName:
      Enforces field/member variable names follow camelCase.
    -->
    <module name="MemberName">
      <property name="format" value="^[a-z][a-zA-Z0-9]*$"/>
    </module>

    <!--
      ParameterName:
      Enforces method parameter names follow camelCase.
    -->
    <module name="ParameterName">
      <property name="format" value="^[a-z][a-zA-Z0-9]*$"/>
    </module>

  </module>
</module>
```


### Optional: Create a VS Code Task for Checkstyle

1. In your project, open the folder `.vscode/` (create it if it doesn’t exist).  
2. Create or edit `tasks.json` with the following content:

```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Run Checkstyle",
            "type": "shell",
            "command": "./gradlew check",
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "presentation": {
                "reveal": "always",
                "panel": "shared"
            },
            "problemMatcher": []
        }
    ]
}
```



