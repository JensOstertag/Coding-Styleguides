# PHP Coding Style Guide
Language-specific Coding Style Guide for PHP.

## Source Files
### File Name
If the Source File contains a Class, the Source File Name consists of the case-sensitive Name of the top-level Class it contains plus the Extension ``.class.php``, with ``.class`` symbolizing it contains a Class.
If the Source File doesn't contain a Class and is supposed to be Part of a Website, API or similar (retrievable to Clients), the File Name consists of a descriptive Expression written in lower-kebab-case plus the ``.php`` Extension.

### Basic Structure
A Source File containing a Class consists of
<ol>
<li>
    PHP Opening Tag
</li>
<li>
    Include Statements (optional)
</li>
<li>
    Exactly one top-level Class
</li>
</ol>
A Source File that doesn't contain a Class consists of
<ol>
<li>
    PHP Opening Tag
</li>
<li>
    Include Statements (optional)
</li>
<li>
    PHP Code (optional)
</li>
<li>
    PHP Closing Tag, only if there is HTML Code following
</li>
<li>
    HTML Code (optional)
</li>
</ol>
Source Files that do not contain HTML Code don't contain a PHP Closing Tag.

#### Include Statements
The Include Statements are listing each Dependency used in the Source File.

### Example
File Name: ``Example.class.php``:
```php
<?php
    include_once 'Dependency.class.php';
    include_once 'dependency.php';

    class Example {
        // The Code
    }
```
File Name: ``example.php``:
```php
<?php
    include_once 'Dependency.class.php';
    include_once 'dependency.php';

    // The Code
?>

<!DOCTYPE html>
<html>
    <head>
        // Head
    </head>
    <body>
        // Body
    </body>
</html>
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
```php
if(/* Condition */) {
    /* Do something */
} else {
    /* Do something else */
}
```
```php
for(/* Iterator Definitions */) {
    /* Do something */
}
```
```php
do {
    /* Do something */
} while(/* Iterator Definitions */);
```
```php
try {
    /* Try something */
} catch(/* Exception Declaration */) {
    /* Exception Handling */
}
```
These Rules also apply for Array Declarations (or Similar):
```php
$arr = array(
    "Key" => "Value"
);
```
```php
$arr = [
    "Key" => "Value"
];
```

### Indentations
Each Time a new Block is opened, the Indent increases by 4 Spaces (= 1 Tab).

### One Statement per Line
Each Statement is followed by a Line Break.

### Whitespaces
#### Horizontal Whitespaces
Apart from where Required by the Language, other Style Rules or Comments, a single horizontal Whitespace appears only in the following Places:
- Between a closing curly Brace and a Keyword such as ``else``, ``catch`` or ``while`` of a do-while Loop
- Before any opening curly Brace
- Before and after an Equals Symbol ``=`` in Variable Declarations as well as an Arrow ``=>`` in Array Initializations
- Before and after any binary, ternary or mathematical Operator, as well as any of the following "Operator-like" Symbols:
    - Pipe ``|`` for a Catch Blocks handling multiple Exceptions
    ```php
    catch(ExceptionA | ExceptionB $e)
    ```
    - Colon ``:`` in a foreach Loops
- After Commas ``,``, Colons ``:`` and Semicolons ``;`` that don't end a Line.
- Between any Content and a double Slash ``//`` starting a Comment

#### Vertical Whitespaces
Apart from other Style Rules or Comments, a single vertical Whitespace only appears in the following Places:
- Between consecutive Members or Initializers of a Class: Fields, Constructors, Methods, nested Classes, static Initializers and instance Initializers
- Anywhere, if it improves Readability (e.g. between Statements to organize the Code into logical Subsections), under the Condition that it is done uniformly
- As Required by other Sections in this Document or the General Coding Style Guide.

It's disccouraged to use multiple consecutive vertical Whitespaces.

### Comments
For multiline Comments, a ``/* ... */``-Comment Block is used in Advance to the Line or Section that is being commented.
```php
/*
 * A long Comment regarding
 * the following Line
 */
$x = 42;
```
For writing singleline Comments regarding a Code Section, a ``//`` Comment is used in Advance to the Section that is being commented.
```php
// A short Comment regarding the following Section
$a = 20;
$x = (a * a) / (a / 2) + (a / (a / 2));
```
For writing singleline Comments regarding a single Code Line, a ``//`` Comment is used in the same Line as the Code that is being commented.
```php
$x = 42; // A short Comment regarding this Line
```

## Naming
### General Rules
For each of the following Names, it is important to find a descriptive Name. Short and undescriptive Names should be avoided, except for generally accepted Names like ``$i`` in ``for`` Loops or other trivial Functions.

### Folder Names
Folder Names are written in lower-kebab-case. Underscores are not used.

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
### Specifying Method Parameter and Return Types
For newer PHP Versions (PHP7 or higher), the Types of a Method's Parameters or it's Return Type are always specified to the following Rules:
```php
function theFunction(ParamType $parameter): ReturnType {
    // The Code
}
```
The Types of Parameters or Return Values may be specified as nullable:
```php
function theFunction(?ParamType $parameter): ?ReturnType {
    // The Code
}
```
