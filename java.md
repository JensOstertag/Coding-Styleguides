# Java Coding Style Guide
Language-specific Coding Style Guide for Java.

These Style Guides are based on the official Google Coding Style Guide for Java.

## Source Files
### File Name
The Source File Name consists of the case-sensitive Name of the top-level Class it contains plus the ``.java`` Extension.

### Basic Structure
A Source File consists of
<ol>
<li>
    Package Statement
</li>
<li>
    Import Statements
</li>
<li>
    JavaDoc Comment
</li>
<li>
    Exactly one top-level Class
</li>
</ol>

#### Package Statement
The Package Statement is spcifying the Package that the Class is located in.

#### Import Statements
The Import Statements are listing each Import the Class is depending on. Wildcard Imports aren't used.

#### JavaDoc Comment
A JavaDoc Comment for the whole File consisting of
- Class Description
- Author Name and / or Company Name (multiple ``@author``-Tags might be used)
- The Project's current Version (optional)
- The Project's Version at which the Class was first implemented (optional)

### Example
File Name: ``Example.java``:
```java
package com.theauthor.project;

import pack.name.Class;

/** Example Description
 * @author Author Name and / or Company Name
 * @version Current Project Version
 * @since Implementation Version
 */
public class Example {
    // The Code
}
```

## Formatting
### Braces
Optional Braces are used with ``if``, ``else``, ``for``, ``do`` and ``while``, even when it's Body is empty or contains only one Line.
Braces are always styled by the following Rules:
- No Line Break before the opening Brace
- Line Break after the opening Brace
- Line Break before the closing Brace
- Line Break after a closing Brace, only if it terminates a Statement, Method Body, Constructor or an inner Class. There is no Line Break after a closing Brace if e.g. an ``else``, ``catch`` or a Comma is following.

#### Examples
```java
if(/* Condition */) {
    /* Do something */
} else {
    /* Do something else */
}
```
```java
for(/* Iterator Definitions */) {
    /* Do something */
}
```
```java
do {
    /* Do something */
} while(/* Iterator Definitions */);
```
```java
try {
    /* Try something */
} catch(/* Exception Declaration */) {
    /* Exception Handling */
}
```
These Rules also apply for Array Declarations (or Similar):
```java
int[] arr = new int[] {
    0, 1, 2, 3
};
```

### Indentations
Each Time a new Block is opened, the Indent increases by 4 Spaces (= 1 Tab).

### One Statement per Line
Each Statement is followed by a Line Break.

### Whitespaces
#### Horizontal Whitespaces
Apart from where Required by the Language, other Style Rules, Comments or JavaDoc, a single horizontal Whitespace appears only in the following Places:
- Between closing curly Brace and a Keyword such as ``else`` or ``catch``
- Before any opening curly Brace with the Exceptions:
    - An opening curly Brace directly following another opening curly Brace (e.g. in Array Initializations)
    ```java
    int[][] x = {{42}};
    ```
- After the closing Parenthesis ``)`` of a Type-Cast.
- Between the Type and the Variable in Variable Declarations
- Before and after an Equals Symbol ``=`` in Variable Declarations
- Before and after any binary, ternary or mathematical Operator, as well as any of the following "Operator-like" Symbols:
    - Ampersand ``&`` in conjunctive Type Bounds
    ```java
    <T extends A & B>
    ```
    - Pipe ``|`` for a Catch Blocks handling multiple Exceptions
    ```java
    catch(ExceptionA | ExceptionB e)
    ```
    - Colon ``:`` in a foreach Loops
    - Arrow ``->`` in Lambda Expressions
    ```java
    (String str) -> str.length()
    ```
- After Commas ``,``, Colons ``:`` and Semicolons ``;`` that don't end a Line.
- Between any Content and a double Slash ``//`` starting a Comment

#### Vertical Whitespaces
Apart from other Style Rules, Comments or JavaDoc, a single vertical Whitespace only appears in the following Places:
- Between consecutive Members or Initializers of a Class: Fields, Constructors, Methods, nested Classes, static Initializers and instance Initializers
- Anywhere, if it improves Readability (e.g. between Statements to organize the Code into logical Subsections), under the Condition that it is done uniformly
- As Required by other Sections in this Document or the General Coding Style Guide.

It's disccouraged to use multiple consecutive vertical Whitespaces.

### Comments
For multiline Comments, a ``/* ... */``-Comment Block is used in Advance to the Line or Section that is being commented.
```java
/*
 * A long Comment regarding
 * the following Line
 */
int x = 42;
```
For writing singleline Comments regarding a Code Section, a ``//`` Comment is used in Advance to the Section that is being commented.
```java
// A short Comment regarding the following Section
int a = 20;
int x = (a * a) / (a / 2) + (a / (a / 2));
```
For writing singleline Comments regarding a single Code Line, a ``//`` Comment is used in the same Line as the Code that is being commented.
```java
int x = 42; // A short Comment regarding this Line
```

## Naming
### General Rules
For each of the following Names, it is important to find a descriptive Name. Short and undescriptive Names should be avoided, except for generally accepted Names like ``int i`` in ``for`` Loops or other trivial Functions.

### Package Names
Package Names only use lowercase Letters and Digits. Consecutive Words are concatenated.
Underscores or dashes are not used.

### Class Names
Class Names are written in UpperCamelCase. 
They're typically Nouns or Noun Phrases.

### Method Names
Method Names are written in lowerCamelCase.
They're typically Verbs or Verb Phrases.

### Method Parameter Names
Method Parameter Names are written in lowerCamelCase.

### Constant Names
Constant Names are written in UPPER_SNAKE_CASE.
Variables are considered Constants if they are deeply immutable and their Methods have no detectable side effects.

### Variable Names
Variable Names are written in lowerCamelCase.
They're typically Nouns or Noun Phrases.

## Programming Practices
### Using ``@Override`` Annotations
A Method is marked with the ``@Override`` Annotation whenever it's possible.

### Never Ignore thrown Exceptions
It's rarely correct to leave the Body of a ``catch`` Block empty. In most cases, an Exception will at least get logged.
When it's correct to leave the Body empty, the Reason for that is explained in a Comment.

### Calling Static Functions 
Static Functions are always called by the Class's Name, not by a Reference of the Class's Type.

## JavaDoc
### Usage of JavaDoc
At least for every (non-overriding) public Method and for every Class, a JavaDoc Description is present.
When a Tag is specified in a JavaDoc Comment, it has to be described.

### JavaDoc for Classes
The JavaDoc Comment for a whole Class consists of
- Class Description
- Author Names and / or Company Name (multiple ``@author``-Tags might be used)
- The Project's current Version (optional)
- The Project's version at which the Class was first implemented (optional)

and is formatted like the following:
```java
/** Example Description
 * @author Author Name and / or Company Name
 * @version Current Project Version
 * @since Implementation Version
 */
 ```

### JavaDoc for Methods
The JavaDoc Comments for a Method consists of
- Method Description
- Parameter List and Description (multiple ``@param``-Tags might be used) (if exists)
- Return Value Description (if exists)
- Exception List and Description (multiple ``@throws``-Tags might be used) (if exists)
- Deprecated Tag (optional)

and is formatted like the following:
```java
/** Method Description
 * @param Parameter Parameter Description
 * @return Return Description
 * @throws Exception Exception Description
 * (@deprecated)
 */
