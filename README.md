# Basic Python Tuple Parser

A Java-based interpreter that parses and executes a subset of Python's tuple syntax, built with ANTLR 3.5.2.

## About

This project implements a complete parsing and execution pipeline for a simplified Python-like language focused on tuple operations. It uses ANTLR to generate a lexer and parser from a formal grammar, with embedded semantic actions that execute statements at parse time.

### Supported Operations

- **Tuple creation:** `X = ('hello', 'world', 42)`
- **Tuple slicing:** `Y = X[:2]` and `Z = X[2:]`
- **Tuple concatenation:** `A = Y + Z`
- **Tuple unpacking:** `(A, B, C) = X`
- **Element access/update:** `X[0] = 'new value'`
- **String and integer variables:** `A = 'text'` or `A = 100`
- **Print statements:** `print(X)`
- **Comments:** `// single-line comments`

## How It Works

1. **Grammar.g** defines the lexical and syntactic rules using ANTLR grammar notation
2. **ANTLR** generates `GrammarLexer.java` and `GrammarParser.java` from the grammar
3. **ActionRoutines.java** provides the runtime, storing tuples and variables in HashMaps and executing operations like creation, slicing, concatenation, and unpacking
4. **TestT.java** reads `input.txt` and drives the lexer/parser to interpret the program

## Prerequisites

- Java JDK
- ANTLR 3.5.2 (included as `antlr-3.5.2-complete.jar`)

## Usage

On Windows, run the included batch script:

```bat
run.bat
```

Or manually:

```sh
java -cp ".;antlr-3.5.2-complete.jar" org.antlr.Tool Grammar.g
javac -cp ".;antlr-3.5.2-complete.jar" *.java
java -cp ".;antlr-3.5.2-complete.jar" TestT
```

On Linux/macOS, replace `;` with `:` in the classpath separator.

## Example

Given `input.txt`:

```
X = ('This is', 'the first', 'EECE', 334, 'Assignment')
print(X)
Y = X[:2]
print(Y)
Z = X[2:]
print(Z)
A = Y + Z
print(A)
```

The interpreter outputs each tuple's contents as it encounters each `print` statement.
