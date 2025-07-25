# Mini-C Lexer and Parser

This repository contains a foundational project for a compiler front-end, developed as a class assignment. It focuses on the **lexical analysis (tokenizing)** and **parsing** phases for a simplified C-like language, often referred to as "Mini-C."

## Project Overview

The primary goal of this project was to implement a lexer and a basic parser capable of processing Mini-C source code. The lexer breaks down the raw source into a stream of meaningful tokens, while the parser then processes this token stream, performs syntactic analysis, and builds a symbol table to manage identifiers and their types.

The current implementation outputs the recognized tokens along with their attributes, line numbers, and column numbers, demonstrating the successful tokenization and initial stages of parsing.

## Features

* **Lexical Analysis:** Converts Mini-C source code into a stream of tokens (e.g., keywords, identifiers, operators, integer/float literals).

* **Token Recognition:** Identifies various Mini-C language constructs such as `FUNC`, `VAR`, `INT`, `BOOL`, `FLOAT`, `VOID`, `IF`, `ELSE`, `WHILE`, `RETURN`, `BREAK`, `CONTINUE`, `PRINT`, `STRUCT`, `SIZE`, `NEW`, `LPAREN`, `RPAREN`, `LBRACKET`, `RBRACKET`, `SEMI`, `COMMA`, `DOT`, `ADDR`, `VALUE`, `ASSIGN`, `TYPEOF`, arithmetic operators (`+`, `-`, `*`, `/`, `and`, `or`, `not`), and relational operators (`=`, `<>`, `<`, `>`, `<=`, `>=`).

* **Symbol Table Integration:** Demonstrates the creation of new symbol table entities for identifiers during the lexical/parsing process.

* **Error Handling:** Includes basic lexical error detection for unexpected characters.

* **Line and Column Tracking:** Provides precise location information for each token.

## How it Works

The project utilizes `JFlex` for lexical analysis and custom Java classes for parsing and overall compilation flow.

* **`Lexer.jflex` (JFlex specification):** Defines the regular expressions and rules for recognizing tokens in Mini-C. JFlex generates `Lexer.java` from this file.

* **`Lexer.java` (Generated):** The actual lexical analyzer, responsible for reading input characters and producing tokens.

* **`Parser.java`:** Consumes the token stream from the `Lexer`. It defines token constants and includes the `yyparse()` method which drives the token processing and prints token information.

* **`ParserVal.java`:** A utility class used to hold the semantic values (attributes) associated with the recognized tokens (e.g., the integer value of an `INT_LIT` token).

* **`Compiler.java`:** The orchestrator class that initializes the `Parser` and initiates the parsing process.

* **`Program.java`:** The main entry point of the application. It reads the Mini-C source file and passes it to the `Compiler`.

## Getting Started

### Prerequisites

* Java Development Kit (JDK) 8 or higher

* JFlex 1.6.1 (or compatible version)

### Building the Project

1.  **Navigate to the `src` directory:**

    ```bash
    cd proj2-minic-lexer/src
    ```

2.  **Copy JFlex JAR:**
    Ensure `jflex-1.6.1.jar` is present in the `src` directory. If not, download it and place it there.

3.  **Compile the Lexer using JFlex:**

    ```bash
    java -jar jflex-1.6.1.jar Lexer.flex
    ```

    This command will generate `Lexer.java` in the `src` directory.

4.  **Compile all Java files:**

    ```bash
    javac *.java
    ```

### Running the Program

1.  **From the `src` directory**, execute the `Program` class, providing a Mini-C source file as an argument.
    For example, using `test/solu1.txt` as input (you may need to adjust the path depending on where you run it from):

    ```bash
    java Program ../test/solu1.txt
    ```

    To capture the output to a file (recommended for analysis):

    ```bash
    java Program ../test/solu1.txt > output.txt
    ```

## Example Output

When running the program with a sample Mini-C file, the output will detail the recognized tokens, their attributes, and their position in the source code.

**Input (e.g., `test/solu1.txt`):**

```minic
FUNC main()
BEGIN
    VAR a BOOL;
    a := 1;
    PRINT a;
END
```

## Author

Rohan Mankame

## License

This project was a part of my CMPSC470 course at Penn State University.

