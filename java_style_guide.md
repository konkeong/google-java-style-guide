# Overview

The Java style guide is based on [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html) with modifications and adaptations.

| | | |
| --- | --- | --- |
| 2022-05-10 | konkeong | First version |

- [Overview](#overview)
  - [1. Introduction](#1-introduction)
    - [1.1 Terminology notes](#11-terminology-notes)
    - [1.2 Guide notes](#12-guide-notes)
  - [2 Source file basics](#2-source-file-basics)
    - [2.1 File name](#21-file-name)
    - [2.2 File encoding: UTF-8](#22-file-encoding-utf-8)
    - [2.3 Special characters](#23-special-characters)
      - [2.3.1 Whitespace characters](#231-whitespace-characters)
      - [2.3.2 Special escape sequences](#232-special-escape-sequences)
      - [2.3.3 Non-ASCII characters](#233-non-ascii-characters)
  - [3 Source file structure](#3-source-file-structure)
    - [3.1 License or copyright information, if present](#31-license-or-copyright-information-if-present)
    - [3.2 Package statement](#32-package-statement)
    - [3.3 Import statements](#33-import-statements)
      - [3.3.1 No wildcard imports](#331-no-wildcard-imports)
      - [3.3.2 No line-wrapping](#332-no-line-wrapping)
      - [3.3.3 Ordering and spacing](#333-ordering-and-spacing)
      - [3.3.4 No static import for classes](#334-no-static-import-for-classes)
    - [3.4 Class declaration](#34-class-declaration)
      - [3.4.1 Exactly one top-level class declaration](#341-exactly-one-top-level-class-declaration)
      - [3.4.2 Ordering of class contents](#342-ordering-of-class-contents)
        - [3.4.2.1 Overloads: never split](#3421-overloads-never-split)
  - [4 Formatting](#4-formatting)
    - [4.1 Braces](#41-braces)
      - [4.1.1 Use of optional braces](#411-use-of-optional-braces)
      - [4.1.2 Nonempty blocks: K & R style](#412-nonempty-blocks-k--r-style)
      - [4.1.3 Empty blocks: may be concise](#413-empty-blocks-may-be-concise)
    - [4.2 Block indentation: +4 spaces](#42-block-indentation-4-spaces)
    - [4.3 One statement per line](#43-one-statement-per-line)
    - [4.4 Column limit](#44-column-limit)
    - [4.5 Line-wrapping](#45-line-wrapping)
      - [4.5.1 Where to break](#451-where-to-break)
      - [4.5.2 Indent continuation lines at least +8 spaces](#452-indent-continuation-lines-at-least-8-spaces)
    - [4.6 Whitespace](#46-whitespace)
      - [4.6.1 Vertical Whitespace](#461-vertical-whitespace)
      - [4.6.2 Horizontal whitespace](#462-horizontal-whitespace)
      - [4.6.3 Horizontal alignment: never required](#463-horizontal-alignment-never-required)
    - [4.7 Grouping parentheses: recommended](#47-grouping-parentheses-recommended)
    - [4.8 Specific constructs](#48-specific-constructs)
      - [4.8.1 Enum classes](#481-enum-classes)
      - [4.8.2 Variable declarations](#482-variable-declarations)
        - [4.8.2.1 One variable per declaration](#4821-one-variable-per-declaration)
        - [4.8.2.2 Declared when needed](#4822-declared-when-needed)
      - [4.8.3 Arrays](#483-arrays)
        - [4.8.3.1 Array initializers: can be "block-like"](#4831-array-initializers-can-be-block-like)
        - [4.8.3.2 No C-style array declarations](#4832-no-c-style-array-declarations)
      - [4.8.4 Switch statements](#484-switch-statements)
        - [4.8.4.1 Indentation](#4841-indentation)
        - [4.8.4.2 Fall-through: commented](#4842-fall-through-commented)
        - [4.8.4.3 Presence of the `default` label](#4843-presence-of-the-default-label)
      - [4.8.5 Annotations](#485-annotations)
        - [4.8.5.1 Type-use annotations](#4851-type-use-annotations)
        - [4.8.5.2 Class annotations](#4852-class-annotations)
        - [4.8.5.3 Method and constructor annotations](#4853-method-and-constructor-annotations)
        - [4.8.5.4 Field annotations](#4854-field-annotations)
        - [4.8.5.5 Parameter and local variable annotations](#4855-parameter-and-local-variable-annotations)
      - [4.8.6 Comments](#486-comments)
        - [4.8.6.1 Block comment style](#4861-block-comment-style)
      - [4.8.7 Modifiers](#487-modifiers)
      - [4.8.8 Numeric Literals](#488-numeric-literals)
  - [5 Naming](#5-naming)
    - [5.1 Rules common to all identifiers](#51-rules-common-to-all-identifiers)
    - [5.2 Rules by identifier type](#52-rules-by-identifier-type)
      - [5.2.1 Package names](#521-package-names)
      - [5.2.2 Class names](#522-class-names)
      - [5.2.3 Method names](#523-method-names)
        - [5.2.3.1 Unit test method name](#5231-unit-test-method-name)
      - [5.2.4 Constant names](#524-constant-names)
      - [5.2.5 Non-constant field names](#525-non-constant-field-names)
      - [5.2.6 Parameter names](#526-parameter-names)
      - [5.2.7 Local variable names](#527-local-variable-names)
      - [5.2.8 Type variable names](#528-type-variable-names)
    - [5.3 Camel case: defined](#53-camel-case-defined)
  - [6 Programming Practices](#6-programming-practices)
    - [6.1 `@Override`: always used](#61-override-always-used)
    - [6.2 Caught exceptions: not ignored](#62-caught-exceptions-not-ignored)
    - [6.3 Static members: qualified using class](#63-static-members-qualified-using-class)
    - [6.4 Finalizers: not used](#64-finalizers-not-used)
  - [7 Javadoc](#7-javadoc)
    - [7.1 Formatting](#71-formatting)
      - [7.1.1 General form](#711-general-form)
      - [7.1.2 Paragraphs](#712-paragraphs)
      - [7.1.3 Block tags](#713-block-tags)
    - [7.2 The summary fragment](#72-the-summary-fragment)
    - [7.3 Where Javadoc is used](#73-where-javadoc-is-used)
      - [7.3.1 Exception: self-explanatory members](#731-exception-self-explanatory-members)
      - [7.3.2 Exception: overrides](#732-exception-overrides)
      - [7.3.4 Non-required Javadoc](#734-non-required-javadoc)

## 1. Introduction

This document serves as the **complete** definition of Google's coding standards for source code in the Java™ Programming Language. A Java source file is described as being in *Google Style* if and only if it adheres to the rules herein.

Like other programming style guides, the issues covered span not only aesthetic issues of formatting, but other types of conventions or coding standards as well. However, this document focuses primarily on the **hard-and-fast rules** that we follow universally, and avoids giving *advice* that isn't clearly enforceable (whether by human or tool).

### 1.1 Terminology notes

In this document, unless otherwise clarified:

1. The term *class* is used inclusively to mean an "ordinary" class, enum class, interface or annotation type (`@interface`).
2. The term *member* (of a class) is used inclusively to mean a nested class, field, method, or *constructor*; that is, all top-level contents of a class except initializers and comments.
3. The term *comment* always refers to *implementation* comments. We do not use the phrase "documentation comments", and instead use the common term "Javadoc."

Other "terminology notes" will appear occasionally throughout the document.

### 1.2 Guide notes

Example code in this document is **non-normative**. That is, while the examples are in *Google Style*, they may not illustrate the *only* stylish way to represent the code. Optional formatting choices made in examples should not be enforced as rules.

## 2 Source file basics

### 2.1 File name

The source file name consists of the case-sensitive name of the top-level class it contains (of which there is [exactly one](#341-exactly-one-top-level-class-declaration)), plus the `.java` extension.

### 2.2 File encoding: UTF-8

Source files are encoded in **UTF-8**.

### 2.3 Special characters

#### 2.3.1 Whitespace characters

Aside from the line terminator sequence, the **ASCII horizontal space character (0x20)** is the only whitespace character that appears anywhere in a source file. This implies that:

1. All other whitespace characters in string and character literals are escaped.
2. Tab characters are **not** used for indentation.

#### 2.3.2 Special escape sequences

For any character that has a [special escape sequence](http://docs.oracle.com/javase/tutorial/java/data/characters.html) (`\b`, `\t`, `\n`, `\f`, `\r`, `\"`, `\'` and `\\`), that sequence is used rather than the corresponding octal (e.g. `\012`) or Unicode (e.g. `\u000a`) escape.

#### 2.3.3 Non-ASCII characters

For the remaining non-ASCII characters, either the actual Unicode character (e.g. `∞`) or the equivalent Unicode escape (e.g. `\u221e`) is used. The choice depends only on which makes the code **easier to read and understand**, although Unicode escapes outside string literals and comments are strongly discouraged.

---
**Tip**: In the Unicode escape case, and occasionally even when actual Unicode characters are used, an explanatory comment can be very helpful.

---

Examples:

| Example | Discussion |
| --- | --- |
| `String unitAbbrev = "μs";` | Best: perfectly clear even without a comment. |
| `String unitAbbrev = "\u03bcs"; // "μs"` | Allowed, but there's no reason to do this. |
| `String unitAbbrev = "\u03bcs"; // Greek letter mu, "s"` | Allowed, but awkward and prone to mistakes. |
| `String unitAbbrev = "\u03bcs";` | Poor: the reader has no idea what this is. |
| `return '\ufeff' + content; // byte order mark` | Good: use escapes for non-printable characters, and comment if necessary. |

---
**Tip**: Never make your code less readable simply out of fear that some programs might not handle non-ASCII characters properly. If that should happen, those programs are **broken** and they must be **fixed**.

---

## 3 Source file structure

A source file consists of, **in order**:

1. License or copyright information, if present
2. Package statement
3. Import statements
4. Exactly one top-level class

**Exactly one blank line** separates each section that is present.

### 3.1 License or copyright information, if present

If license or copyright information belongs in a file, it belongs here. However it is not necessary to have copyright notice at the top of the source file.

### 3.2 Package statement

The package statement is **not line-wrapped**. The column limit (Section [4.4, Column limit](#44-column-limit)) does not apply to package statements.

### 3.3 Import statements

#### 3.3.1 No wildcard imports

**Wildcard imports**, static or otherwise, **are not used**.

```java
import static java.util.Map.*;  // not allowed

import static org.junit.Assert.*;  // not allowed

import java.util.*;  // not allowed
```

```java
import static java.util.Map.Entry;            // preferred

import static org.junit.Assert.assertEquals;  // preferred
import static org.junit.Assert.assertNull;    // preferred

import java.util.ArrayList;  // preferred
import java.util.List;       // preferred
```

#### 3.3.2 No line-wrapping

Import statements are **not line-wrapped**. The column limit (Section [4.4 Column limit](#44-column-limit)) does not apply to import statements.

#### 3.3.3 Ordering and spacing

Imports are ordered as follows:

1. All static imports are grouped first.
2. All non-static imports are grouped next.

If there are both static and non-static imports, a single blank line separates the two blocks.

Logical grouping by package prefix is allowed. Usually will follow the [maven grouping](https://mvnrepository.com/). A single blank line is used to separate the logical groupings.

The logical groups are sorted with package prefix of `java` first, follows by `javax`, follows by others.

Within each block the imported names appear in ASCII sort order. (**Note**: this is not the same as the import *statements* being in ASCII sort order, since '`.`' sorts before '`;`'.)

```java
// not this simple ASCII sort ordering
import com.google.common.base.Preconditions;
import java.io.File;
import javax.sql.DataSource;
import org.junit.Test;
```

```java
import java.io.File;                          // java.* first
import java.util.Arrays;

import javax.jms.JMSContext;                  // javax.* second
import javax.sql.DataSource;

import com.google.common.base.Preconditions;  // the rest in maven grouping
import com.google.common.collect.Lists;

import org.apache.commons.codec.binary.Base64; // Apache Commons Codec

import org.apache.poi.ss.usermodel.Cell;  // Apache POI
import org.apache.poi.ss.usermodel.Row;
import org.apache.poi.ss.usermodel.Sheet;
import org.apache.poi.ss.usermodel.Workbook;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;

import org.junit.After;  // JUnit
import org.junit.Assert;
import org.junit.Before;
import org.junit.Test;
```

#### 3.3.4 No static import for classes

Static import is not used for static nested classes. They are imported with normal imports.

Nested inner `class` / `enum` / `interface` is allowed.

### 3.4 Class declaration

#### 3.4.1 Exactly one top-level class declaration

Each top-level class resides in a source file of its own.

#### 3.4.2 Ordering of class contents

The order you choose for the members and initializers of your class can have a great effect on readability. However, there's no single correct recipe for how to do it; different classes may order their contents in different ways.

What is important is that each class uses ***some* logical order**, which its maintainer could explain if asked. For example, new methods are not just habitually added to the end of the class, as that would yield "chronological by date added" ordering, which is not a logical ordering.

One possible organization is:

- nested `interface`
- nested `enum`
- nested `class`
- `abstract` methods
- `private` static final constants
- `public` static final constants
- `private` static fields
- `public` static fields
- `private` instance fields
- `public` instance fields
- constructors
- accessors (getters and setters in pair)
- `private` static methods
- `public` static methods
- `private` instance methods
- `public` instance methods
- `hashCode()` and `equals()`
- `toString()` (last)

Rule of thumb is to define or instantiate items/tokens (interface / enum / class / field / method) at the top of source code before it is used or referenced later.

Exception is when there is logical linkage/grouping of static fields and instance fields (or static methods and instance methods).

```java
public static String trimToNull(....) { .... }

public int calculateAverage(....) { .... }

public static boolean validateString(....) { .... }

public boolean validateEmail(....) {
    validateString(....);
}

// validateString() is after public instance methods,
// and park closer to "validate" related methods
// validateString() as a static method is slipped between
// other public instance methods
```

Exception is no-arg constructor is placed first, over other form of constructors.

```java
public SomeClass() {
    this(null, null);
}

public SomeClass(String first) {
    this(first, null);
}

public SomeClass(String first, String second) {
    ....
}
```

##### 3.4.2.1 Overloads: never split

Methods of a class that share the same name appear in a single contiguous group with no other members in between. The same applies to multiple constructors (which always have the same name). This rule applies even when modifiers such as `static` or `private` differ between the methods.

Usually the overridden methods follow the ordering of how it is defined in the super class / interface. Starting with methods from the top most (root) level down.

## 4 Formatting

**Terminology Note**: *block-like construct* refers to the body of a class, method, constructor, initializer code block or lambda body. Note that, by Section 4.8.3.1 on [array initializers](#4831-array-initializers-can-be-block-like), any array initializer *may* optionally be treated as if it were a block-like construct.

### 4.1 Braces

#### 4.1.1 Use of optional braces

Braces are used with `if`, `else`, `for`, `do`, `while` and `switch` statements, even when the body is empty or contains only a single statement.

```java
// not OKAY, missing braces
if (needToDoSomething == true)
    callToDoSomething();

// this is preferred
if (needToDoSomething == true) {
    callToDoSomething();
}
```

Other optional braces, such as those in a lambda expression, remain optional.

#### 4.1.2 Nonempty blocks: K & R style

Braces follow the Kernighan and Ritchie style ("[Egyptian brackets](http://www.codinghorror.com/blog/2012/07/new-programming-jargon.html)") for *nonempty* blocks and block-like constructs:

- No line break before the opening brace, except as detailed below.
- Line break after the opening brace.
- Line break before the closing brace.
- Line break after the closing brace, *only if* that brace terminates a statement or terminates the body of a method, constructor, or *named* class. For example, there is *no* line break after the brace if it is followed by `else` or a comma (`,`).

**Exception**: In places where these rules allow a single statement ending with a semicolon (`;`), a block of statements can appear, and the opening brace of this block is preceded by a line break. Blocks like these are typically introduced to limit the scope of local variables, for example inside `switch` statements.

Examples:

```java
return () -> {
    while (condition()) {
        method();
    }
};

return new MyClass() {
    @Override
    public void method() {
        if (condition()) {
            try {
                something();
            } catch (ProblemException e) {
                recover();
            }
        } else if (otherCondition()) {
            somethingElse();
        } else {
            lastThing();
        }
        {
            int x = foo();
            frob(x);
        }
    }
};
```

A few exceptions for enum classes are given in Section [4.8.1 Enum classes](#481-enum-classes).

#### 4.1.3 Empty blocks: may be concise

An empty block or block-like construct may be in K & R style (as described in Section [4.1.2](#412-nonempty-blocks-k--r-style)). Alternatively, it may be closed immediately after it is opened, with no characters or line break in between (`{}`), **unless** it is part of a *multi-block statement* (one that directly contains multiple blocks: `if/else` or `try/catch/finally`).

Examples:

```java
// This is acceptable
void doNothing() {}

// This is equally acceptable
void doNothingElse() {
}

// This is not acceptable: No concise empty blocks in a multi-block statement
try {
    doSomething();
} catch (Exception e) {}

// This is acceptable
try {
    doSomething();
} catch (Exception expected) {
}

// empty initializer, no need to break
char[] chars = {};

// not OKAY
char[] chars = {
};
```

### 4.2 Block indentation: +4 spaces

Each time a new block or block-like construct is opened, the indent increases by four (4) spaces. When the block ends, the indent returns to the previous indent level. The indent level applies to both code and comments throughout the block. (See the example in Section [4.1.2 Nonempty blocks: K & R Style](#412-nonempty-blocks-k--r-style).)

2 spaces is too narrow / cramp. Each indentation must be 4 spaces.

### 4.3 One statement per line

Each statement is followed by a line break.

No section of code (block-like construct) is separated by more than one (1) line break. Comments can be placed instead to provide more visible segregation. See Section [4.6.1 Vertical Whitespace](#461-vertical-whitespace)

### 4.4 Column limit

Each line of Java code has a column limit of 100 characters. However this is not an unbreakable limit, it could be set at 400 characters, depends on the project type. Rule of thumb to allow for long line of code is to ensure consistent *viewing pattern*. Whenever there is a long line of code, this usually signify a need to refactor the code (encapsulate as standalone function, re-evaluate the logic flow).

A "character" means any Unicode code point. Except as noted below, any line that would exceed this limit must be line-wrapped, as explained in Section [4.5 Line-wrapping](#45-line-wrapping).

---
**Note**: Each Unicode code point counts as one character, even if its display width is greater or less. For example, if using [fullwidth characters](https://en.wikipedia.org/wiki/Halfwidth_and_fullwidth_forms), you may choose to wrap the line earlier than where this rule strictly requires.

---

**Exceptions**:

1. Lines where obeying the column limit is not possible (for example, a long URL in Javadoc, or a long JSNI method reference).
2. `package` and `import` statements (see Sections [3.2 Package statement](#32-package-statement) and [3.3 Import statements](#33-import-statements)).
3. Command lines in a comment that may be copied-and-pasted into a shell.
4. Very long identifiers, on the rare occasions they are called for, are allowed to exceed the column limit. In that case, the valid wrapping for the surrounding code is as produced by [google-java-format](https://github.com/google/google-java-format).

### 4.5 Line-wrapping

**Terminology Note**: When code that might otherwise legally occupy a single line is divided into multiple lines, this activity is called *line-wrapping*.

There is no comprehensive, deterministic formula showing *exactly* how to line-wrap in every situation. Very often there are several valid ways to line-wrap the same piece of code.

---
**Note**: While the typical reason for line-wrapping is to avoid overflowing the column limit, even code that would in fact fit within the column limit *may* be line-wrapped at the author's discretion.

---

---
**Tip**: Extracting a method or local variable may solve the problem without the need to line-wrap.

---

#### 4.5.1 Where to break

The prime directive of line-wrapping is: prefer to break at a **higher syntactic level**. Also:

1. When a line is broken at a *non-assignment* operator the break comes *before* the symbol. (Note that this is not the same practice used in Google style for other languages, such as C++ and JavaScript.)
    - This also applies to the following "operator-like" symbols:
      - the dot separator (`.`)
      - the two colons of a method reference (`::`)
      - an ampersand in a type bound (`<T extends Foo & Bar>`)
      - a pipe in a catch block (`catch (FooException | BarException e)`).

    ```java
    // OKAY
    sb.append(....)
        .append(....)
        .append(....);

    // OKAY
    result = demo.numCheck(IntPredicatesChecker
        ::isEven,
        num);

    // OKAY
    public class SomeClass<T extends Foo
        & Bar> {
        ....
    }

    // OKAY
    try {
        ....
    } catch (FooException
        | BarException e) {
        ....
    }
    ```

2. When a line is broken at an *assignment* operator the break typically comes *after* the symbol, but either way is acceptable.
    - This also applies to the "assignment-operator-like" colon (`:`) in an enhanced `for` ("foreach") statement.

    ```java
    // OKAY
    int something =
        a + b;

    // OKAY
    for (Map.Entry<String, Integer> entry :
        map.entrySet()) {
        ....
    }
    ```

3. A method or constructor name stays attached to the open parenthesis (`(`) that follows it.

    ```java
    // not OKAY
    public SomeClass
        (String name,
        String description) {
        ....
    }

    // OKAY
    public SomeClass(
        String name,
        String description) {
        ....
    }
    ```

4. A comma (`,`) stays attached to the token that precedes it.

    ```java
    // not OKAY
    doSomething(
        one
        , two
        , three);

    // OKAY
    doSomething(
        one,
        two,
        three);
    ```

5. A line is never broken adjacent to the arrow in a lambda, except that a break may come immediately after the arrow if the body of the lambda consists of a single unbraced expression. Examples:

    ```java
    MyLambda<String, Long, Object> lambda =
        (String label, Long value, Object obj) -> {
            ....
        };

    // OKAY to omit {} for lambda
    Predicate<String> predicate = str ->
        longExpressionInvolving(str);
    ```

6. Should not have hanging `)`.

    ```java
    // not OKAY
    doSomething(
            param1,
            param2,
            param3
    );

    // OKAY
    doSomething(
            param1,
            param2,
            param3);
    ```

    ```java
    // not OKAY
    if (
            ....
            ....
    ) {
        ....
    }

    // OKAY
    if (
            ....
            ....) {
        ....
    }
    ```

    ```java
    List<String> list = new ArrayList<>();

    // not OKAY
    for (
            java.util.Iterator<String> iter = list.iterator();
            iter.hasNext();
    ) {
        String val = iter.next();
    }

    // OKAY
    for (
            java.util.Iterator<String> iter = list.iterator();
            iter.hasNext(); ) {
        String val = iter.next();
    }

    // OKAY
    java.util.Iterator<String> iter2 = list.iterator();
    for ( ; iter2.hasNext(); ) {
        String val = iter2.next();
    }
    ```

    ```java
    // OKAY
    for ( ; ; ) {
        ....
    }

    // this is acceptable
    for (;;) {
        ....
    }
    ```

---
**Note**: The primary goal for line wrapping is to have clear code, not necessarily code that fits in the smallest number of lines.

---

#### 4.5.2 Indent continuation lines at least +8 spaces

When line-wrapping, each line after the first (each *continuation line*) is indented at least +8 (twice the normal indentation) from the original line.

When there are multiple continuation lines, indentation may be varied beyond +8 as desired. In general, two continuation lines use the same indentation level if and only if they begin with syntactically parallel elements.

Section 4.6.3 on [Horizontal alignment](#463-horizontal-alignment-never-required) addresses the discouraged practice of using a variable number of spaces to align certain tokens with previous lines.

### 4.6 Whitespace

#### 4.6.1 Vertical Whitespace

A single blank line always appears:

1. *Between* consecutive members or initializers of a class: fields, constructors, methods, nested classes, static initializers, and instance initializers.
    - **Exception**: A blank line between two consecutive fields (having no other code between them) is optional. Such blank lines are used as needed to create *logical groupings* of fields.
    - **Exception**: Blank lines between enum constants are covered in Section [4.8.1 Enum classes](#481-enum-classes).

2. As required by other sections of this document (such as Section [3 Source file structure](#3-source-file-structure), and Section [3.3 Import statements](#33-import-statements)).

A single blank line may also appear anywhere it improves readability, for example between statements to organize the code into logical subsections. A blank line before the first member or initializer, or after the last member or initializer of the class, is neither encouraged nor discouraged.

*Multiple* consecutive blank lines are permitted, but never required (or encouraged).

#### 4.6.2 Horizontal whitespace

Beyond where required by the language or other style rules, and apart from literals, comments and Javadoc, a single ASCII space also appears in the following places **only**.

1. Separating any reserved word, such as `if`, `for`, `while`, `switch`, `return`, `assert` or `catch`, from an open parenthesis (`(`) that follows it on that line

    ```java
    // not OKAY
    if(condition) {
        ....
    }

    // OKAY
    if (condition) {
        ....
    }
    ```

    ```java
    // this is preferred, with space
    assert (....)
    catch (....)
    for (....)
    if (....)
    return (....)
    switch (....)
    while (....)

    // this is preferred, with no space
    super(....)
    this(....)
    ```

2. Separating any reserved word, such as `else` or `catch`, from a closing curly brace (`}`) that precedes it on that line

    ```java
    // not OKAY
    if (condition) {
        ....
    }
    else {
        ....
    }

    // OKAY
    if (condition) {
        ....
    } else {
        ....
    }
    ```

    ```java
    // not OKAY
    if (condition) {
        ....
    }
    else if (condition2) {
        ....
    }
    else {
        ....
    }

    // OKAY
    if (condition) {
        ....
    } else if (condition2) {
        ....
    } else {
        ....
    }
    ```

    ```java
    // not OKAY
    try {
        ....
    }
    catch (Exception e) {
        ....
    }

    // OKAY
    try {
        ....
    } catch (Exception e) {
        ....
    }
    ```

3. Before any open curly brace (`{`), with two exceptions:

    ```java
    // no space is used, this is allowed
    @SomeAnnotation({a, b})

    // no space between {{, this is allowed
    String[][] x = {{"foo"}};

    // space is used, this is preferred
    @SomeAnnotation({ a, b })

    // space between {{, this is preferred
    String[][] x = {{ "foo" }};
    ```

4. On both sides of any binary or ternary operator. This also applies to the following "operator-like" symbols:
    - the ampersand (`&`) in a conjunctive type bound: `<T extends Foo & Bar>`
    - the pipe (`|`) for a catch block that handles multiple exceptions: `catch (FooException | BarException e)`
    - the colon (`:`) in an enhanced `for` ("foreach") statement
    - the arrow (`->`) in a lambda expression: `(String str) -> str.length()`

    - but not the two colons (`::`) of a method reference, which is written like `Object::toString`
    - but not the dot separator (`.`), which is written like `object.toString()`

5. After `,;?:` or the closing parenthesis (`)`) of a cast

    ```java
    // space after ,
    // space after ;
    for (int ix = 0, iy = 1; ix < 10; ix += 1) {
        ....
    }

    // space after ?
    // space after :
    isTrue() ? doSomething() : doElse();

    // space after cast
    String name = (String) fields[0];
    ```

6. Between any content and a double slash (`//`) which begins a comment. Multiple spaces are allowed.

7. Between a double slash (`//`) which begins a comment and the comment's text. Multiple spaces are allowed.

8. Between the type and variable of a declaration: `List<String> list`

9. *Optional* just inside both braces of an array initializer
    - `new int[] {5, 6}` and `new int[] { 5, 6 }` are both valid

10. No space between a type annotation and `[]` or `...` (varargs).

    ```java
    byte[] bytes = new byte[] {};

    public static void main(String... args) {
        ....
    }
    ```

11. No space between `(` and `)` that are on the same line, that are not wrapped (Section [4.5 Line-wrapping](#45-line-wrapping)).

    ```java
    // not OKAY
    if ( 1 + 2 >= 3 ) {
        ....
    }

    // OKAY
    if (1 + 2 >= 3) {
        ....
    }
    ```

12. Ternary operator, spaces around `?` and `:`

    ```java
    condition ? expression1 : expression2;
    ```

13. Spaces around `/*` and `*/`

    ```java
    /* This is a comment, surrounded with space.  Allow multiple spaces. */
    ```

This rule is never interpreted as requiring or forbidding additional space at the start or end of a line; it addresses only interior space.

#### 4.6.3 Horizontal alignment: never required

**Terminology Note**: *Horizontal alignment* is the practice of adding a variable number of additional spaces in your code with the goal of making certain tokens appear directly below certain other tokens on previous lines.

This practice is permitted, but is **never required** by *Google Style*. It is not even required to *maintain* horizontal alignment in places where it was already used.

Here is an example without alignment, then using alignment:

```java
private int x; // this is fine
private Color color; // this too

private int   x;      // permitted, but future edits
private Color color;  // may leave it unaligned
```

---
**Note**: Alignment can aid readability, but it creates problems for future maintenance. Consider a future change that needs to touch just one line. This change may leave the formerly-pleasing formatting mangled, and that is **allowed**.

More often it prompts the coder (perhaps you) to adjust whitespace on nearby lines as well, possibly triggering a cascading series of reformattings. That one-line change now has a "blast radius." This can at worst result in pointless busywork, but at best it still corrupts version history information, slows down reviewers and exacerbates merge conflicts.

---

Hence should not perform horizontal alignments everywhere. Limit the scope to constants and enumerations.

```java
public static final String FILE_NOT_EXIST   = "E10012";
public static final String RECORD_NOT_FOUND = "E10031";
```

```java
public enum StatusCode {
    SUCCESS    ("0" , "Success"),
    IN_PROGRESS("31", "In progress"),
    FAILURE    ("99", "Failure");

    private final String code;
    private final String description;

    private StatusCode(String code, String description) {
        this.code = code;
        this.description = description;
    }
}
```

### 4.7 Grouping parentheses: recommended

Optional grouping parentheses are omitted only when author and reviewer agree that there is no reasonable chance the code will be misinterpreted without them, nor would they have made the code easier to read. It is *not* reasonable to assume that every reader has the entire Java operator precedence table memorized.

Rule of thumb is remove as many parentheses as possible, without compromising code logic and understanding.

```java
// this is acceptable
return (success ? "SUCCESS" : "FAILURE");

// this is preferred
return success ? "SUCCESS" : "FAILURE";

// this is acceptable
if (((1 + 2) >= 3) && ((2 + 3) >= 5)) {
    ....
}

// this is also acceptable
if ((1 + 2) >= 3 && (2 + 3) >= 5) {
    ....
}

// this is preferred
if (1 + 2 >= 3 && 2 + 3 >= 5) {
    ....
}
```

### 4.8 Specific constructs

#### 4.8.1 Enum classes

After each comma that follows an enum constant, a line break is optional. Additional blank lines (usually just one) are also allowed. This is one possibility:

```java
private enum Answer {
    YES {
        @Override
        public String toString() {
            return "yes";
        }
    },

    NO,
    MAYBE
}
```

An enum class with no methods and no documentation on its constants may optionally be formatted as if it were an array initializer (see Section 4.8.3.1 on [array initializers](#4831-array-initializers-can-be-block-like)).

```java
private enum Suit { CLUBS, HEARTS, SPADES, DIAMONDS }
```

Since enum classes are *classes*, all other rules for formatting classes apply.

#### 4.8.2 Variable declarations

##### 4.8.2.1 One variable per declaration

Every variable declaration (field or local) declares only one variable: declarations such as `int a, b;` are not used.

**Exception**: Multiple variable declarations are acceptable in the header of a `for` loop.

```java
// not OKAY
int a, b, c;

// OKAY
int a;
int b;
int c;

// OKAY
for (int ix = 0, iy = 1; ix < 10; ix += 1) {
    ....
}
```

##### 4.8.2.2 Declared when needed

Local variables are **not** habitually declared at the start of their containing block or block-like construct. Instead, local variables are declared close to the point they are first used (within reason), to minimize their scope. Local variable declarations typically have initializers, or are initialized immediately after declaration.

In the case of returned variable, then it should be declared upfront.

```java
public SomeResult doSomething(....) {
    SomeResult result = new SomeResult(....); // declare upfront
    /*
     * Complicated logic flow in between,
     * spanning over 100+ lines.
     */
    return result;
}
```

#### 4.8.3 Arrays

##### 4.8.3.1 Array initializers: can be "block-like"

Any array initializer may *optionally* be formatted as if it were a "block-like construct." For example, the following are all valid (**not** an exhaustive list):

```java
// OKAY
new int[] {
    0, 1, 2, 3
}

// OKAY
new int[] {
    0, 1,
    2, 3
}

// OKAY
new int[] {
    0,
    1,
    2,
    3
}

// OKAY, opening brace allow to start on new line
// with closing brace must be on same line
// for single line content
new int[]
    { 0, 1, 2, 3 }

// OKAY
new int[]
    {
        0, 1,
        2, 3
    }
```

##### 4.8.3.2 No C-style array declarations

The square brackets form a part of the `type`, not the variable: `String[] args`, not `String args[]`.

```java
// not OKAY
public void doSomething(String args[]) {
    ....
}

// OKAY
public void doSomething(String[] args) {
    ....
}
```

#### 4.8.4 Switch statements

**Terminology Note**: Inside the braces of a *switch block* are one or more *statement groups*. Each statement group consists of one or more *switch labels* (either `case FOO:` or `default:`), followed by one or more statements (or, for the *last* statement group, *zero* or more statements).

##### 4.8.4.1 Indentation

As with any other block, the contents of a *switch block* are indented +4.

After a *switch label*, there is a line break, and the indentation level is increased +4, exactly as if a block were being opened. The following *switch label* returns to the previous indentation level, as if a block had been closed.

##### 4.8.4.2 Fall-through: commented

Within a *switch block*, each statement group either terminates abruptly (with a `break`, `continue`, `return` or thrown exception), or is marked with a comment to indicate that execution will or *might* continue into the next statement group. Any comment that communicates the idea of fall-through is sufficient (typically `// fall through`). This special comment is not required in the last statement group of the *switch block*.

Example:

```java
switch (input) {
    case 1:
    case 2:
        prepareOneOrTwo();
        // fall through
    case 3:
        handleOneTwoOrThree();
        break;
    default:
        handleLargeNumber(input);
}
```

Notice that no comment is needed after `case 1:`, only at the end of the statement group.

```java
switch (result) {
    case FAIL_CONNECT:
        ....
        break;
    case RECORD_DUPLICATE:
        ....
        break;
    case OK:
        ....
        break;
    case DATABASE_ERROR:
        // $FALL-THROUGH$
    case ERROR:
        // $FALL-THROUGH$
    default:
        ....
        break;
}
```

##### 4.8.4.3 Presence of the `default` label

Each *switch statement* includes a `default` statement group, even if it contains no code.

**Exception**: A *switch statement* for an `enum` type *may* omit the `default` statement group, *if* it includes explicit cases covering *all* possible values of that type. This enables IDEs or other static analysis tools to issue a warning if any cases were missed.

```java
switch (status) {
    case 1:
        ....
        break;
    case 2:
        ....
        break;
    case 3:
        ....
        break;
    default:
        throw new IllegalArgumentException("not catered for status=[" + status + "]");
}
```

Usually throw some sort of `Exception` in the `default` branch.

#### 4.8.5 Annotations

##### 4.8.5.1 Type-use annotations

Type-use annotations appear immediately before the annotated type. An annotation is a type-use annotation if it is meta-annotated with `@Target(ElementType.TYPE_USE)`.

Example:

```java
final @Nullable String name;

public @Nullable Person getPersonByName(String name);
```

##### 4.8.5.2 Class annotations

Annotations applying to a class appear immediately after the documentation block, and each annotation is listed on a line of its own (that is, one annotation per line). These line breaks do not constitute line-wrapping (Section [4.5 Line-wrapping](#45-line-wrapping)), so the indentation level is not increased.

Example:

```java
@Deprecated
@CheckReturnValue
public final class Frozzler { .... }
```

```java
@RequestMapping(
        name = "someName",
        path = { "/path1", "/path2" },
        method = {
                RequestMethod.GET,
                RequestMethod.POST })
public void doSomething(....) { .... }
```

##### 4.8.5.3 Method and constructor annotations

The rules for annotations on method and constructor declarations are the same as the [previous section](#4852-class-annotations).

Example:

```java
@Deprecated
@Override
public String getNameIfPresent() { .... }
```

**Exception**: A *single* parameterless annotation *may* instead appear together with the first line of the signature, for example:

```java
// this is allowed
@Override public int hashCode() { .... }

// this is preferred
@Override
public int hashCode() { .... }
```

##### 4.8.5.4 Field annotations

Annotations applying to a field also appear immediately after the documentation block, but in this case, *multiple* annotations (possibly parameterized) may be listed on the same line; for example:

```java
// this is allowed
protected @Partial @Mock DataLoader loader;

// this is preferred
@Partial
@Mock
protected DataLoader loader;

// this is preferred
@JsonView
@JsonProperty(value = "roles")
private List<RoleWithPrivileges> roles;
```

##### 4.8.5.5 Parameter and local variable annotations

There are no specific rules for formatting annotations on parameters or local variables (except, of course, when the annotation is a type-use annotation).

#### 4.8.6 Comments

This section addresses *implementation comments*. Javadoc is addressed separately in Section [7 Javadoc](#7-javadoc).

Any line break may be preceded by arbitrary whitespace followed by an implementation comment. Such a comment renders the line non-blank.

##### 4.8.6.1 Block comment style

Block comments are indented at the same level as the surrounding code. They may be in `/* .... */` style or `// ....` style. For multi-line `/* .... */` comments, subsequent lines must start with `*` aligned with the `*` on the previous line.

```java
/*
 * This is
 * okay.
 */

// And so
// is this.

/* Or you can
 * even do this. */
```

Comments are not enclosed in boxes drawn with asterisks or other characters.

---
**Tip**: When writing multi-line comments, use the `/* .... */` style if you want automatic code formatters to re-wrap the lines when necessary (paragraph-style). Most formatters don't re-wrap lines in `// ....` style comment blocks.

---

#### 4.8.7 Modifiers

Class and member modifiers, when present, appear in the order recommended by the [Java Language Specification](https://checkstyle.sourceforge.io/config_modifier.html#ModifierOrder):

1. public
2. protected
3. private
4. abstract
5. default
6. static
7. sealed
8. non-sealed
9. final
10. transient
11. volatile
12. synchronized
13. native
14. strictfp

```java
public protected private abstract default static sealed non-sealed final transient volatile synchronized native strictfp
```

#### 4.8.8 Numeric Literals

`long`-valued integer literals use an uppercase `L` suffix, never lowercase (to avoid confusion with the digit `1`). For example, `3000000000L` rather than `3000000000l`.

```java
// not OKAY
long one = 3000000000l;

// OKAY
long two = 3000000000L;

// this is preferred
long tre = 3_000_000_000L;
```

Refer to ["Default Values"](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html) section.

```java
// float literal must ends with "f" or "F"
float valf = 1.23f;

// double literal optionally ends with "d" or "D"
double vald = 1.23d;

// this is preferred
double vale = 1.23;
```

Hexadecimal literal, prefer to be lowercase form.

```java
// this is acceptable
String vala = "0123456789ABCDEF";

// this is preferred
String valb = "0123456789abcdef";
```

## 5 Naming

### 5.1 Rules common to all identifiers

Identifiers use only ASCII letters and digits, and, in a small number of cases noted below, underscores. Thus each valid identifier name is matched by the regular expression `\w+`.

In *Google Style*, special prefixes or suffixes are **not** used. For example, these names are not *Google Style*: `name_`, `_name`, `mName`, `s_name`, `kName` and `fSuccess`.

Exception would be localized "throw-away" or temporary variable, such as counter in `for` loop.

Normally, identifiers should not have underscore, except for:

- entity/class generated by tooling (Hibernate)
- Spring framework related function/method naming
- unit testing function/method naming

### 5.2 Rules by identifier type

#### 5.2.1 Package names

Package names use only lowercase letters and digits (no underscores). Consecutive words are simply concatenated together. For example, `com.example.deepspace`, not `com.example.deepSpace` or `com.example.deep_space`.

Exception cases would be:

- JAXB generated packages
- Hibernate generated packages

#### 5.2.2 Class names

Class names are written in [UpperCamelCase](#53-camel-case-defined).

Class names are typically nouns or noun phrases. For example, `Character` or `ImmutableList`. Interface names may also be nouns or noun phrases (for example, `List`), but may sometimes be adjectives or adjective phrases instead (for example, `Readable`).

There are no specific rules or even well-established conventions for naming annotation types.

A *test* class has a name that ends with Test, for example, `HashIntegrationTest`. If it covers a single class, its name is the name of that class plus `Test`, for example `HashImplTest`.

Class name is of singular noun and not plural form. `RolePrivilege` is preferred over `RolePrivileges`.

Class name is allowed to have prefix (`Abstract`, `Base`) and suffix (`Exception`, `Impl`, `Controller`). Prefix and suffix should denotes system, layer, module, functionality rather than data/object type.

#### 5.2.3 Method names

Method names are written in [lowerCamelCase](#53-camel-case-defined).

Method names are typically verbs or verb phrases. For example, `sendMessage` or `stop`.

Underscores may appear in JUnit *test* method names to separate logical components of the name, with *each* component written in [lowerCamelCase](#53-camel-case-defined), for example `transferMoney_deductsFromSource`. There is no "One Correct Way" to name test methods.

##### 5.2.3.1 Unit test method name

Refer to <https://matheus.ro/2017/09/24/unit-test-naming-convention/>.

1. UnitOfWork_StateUnderTest_ExpectedBehavior
    - sum_biggerThanZeroNumbers_returnCalculatedValue
    - sum_negativeNumberAs1stParameter_throwException
    - sum_negativeNumberAs2ndParameter_throwException

2. Given_Preconditions_When_StateUnderTest_Then_ExpectedBehavior
   - given_sumCalculator_when_biggerThanZeroNumbersAsParameters_then_returnCalculatedValue
   - given_sumCalculator_when_negativeNumberAs1stParameter_then_throwException
   - given_sumCalculator_when_negativeNumberAs2ndParameter_then_throwException

3. Should_ExpectedBehavior_When_StateUnderTest
   - should_returnCalculatedValue_when_sumWithBiggerThanZeroNumbersAsParameters
   - should_throwException_when_sumWithNegativeNumberAs1stParameter
   - should_throwException_when_sumWithNegativeNumberAs2ndParameter

#### 5.2.4 Constant names

Constant names use `UPPER_SNAKE_CASE`: all uppercase letters, with each word separated from the next by a single underscore. But what *is* a constant, exactly?

Constants are static final fields whose contents are deeply immutable and whose methods have no detectable side effects. Examples include primitives, strings, immutable value classes, and anything set to `null`. If any of the instance's observable state can change, it is not a constant. Merely *intending* to never mutate the object is not enough.

Examples:

```java
// Constants
static final int NUMBER = 5;
static final ImmutableList<String> NAMES = ImmutableList.of("Ed", "Ann");
static final Map<String, Integer> AGES = ImmutableMap.of("Ed", 35, "Ann", 32);
static final Joiner COMMA_JOINER = Joiner.on(','); // because Joiner is immutable
static final SomeMutableType[] EMPTY_ARRAY = {};

// Not constants
static String nonFinal = "non-final";
final String nonStatic = "non-static";
static final Set<String> mutableCollection = new HashSet<String>();
static final ImmutableSet<SomeMutableType> mutableElements = ImmutableSet.of(mutable);
static final ImmutableMap<String, SomeMutableType> mutableValues =
    ImmutableMap.of("Ed", mutableInstance, "Ann", mutableInstance2);
static final Logger logger = Logger.getLogger(MyClass.getName());
static final String[] nonEmptyArray = { "these", "can", "change" };
```

These names are typically nouns or noun phrases.

#### 5.2.5 Non-constant field names

Non-constant field names (static or otherwise) are written in [lowerCamelCase](#53-camel-case-defined).

These names are typically nouns or noun phrases. For example, `computedValues` or `index`.

#### 5.2.6 Parameter names

Parameter names are written in [lowerCamelCase](#53-camel-case-defined).

One-character parameter names in public methods should be avoided.

Parameter name refers to the element in the method. For example, `msisdn` in `validateMsisdn(String msisdn)`

#### 5.2.7 Local variable names

Local variable names are written in [lowerCamelCase](#53-camel-case-defined).

Even when final and immutable, local variables are not considered to be constants, and should not be styled as constants.

```java
// not OKAY
final String EMPTY = "";

// OKAY
final String empty = "";
```

Local variable names can have short name (1 character only), as long as it is commonly understandable by context.

```java
// OKAY
int i;
Object el;
int num;
try {
    ....
} catch (Exception e) {
    ....
}
```

#### 5.2.8 Type variable names

Each type variable is named in one of two styles:

- A single capital letter, optionally followed by a single numeral (such as `E`, `T`, `X`, `T2`)
- A name in the form used for classes (see Section [5.2.2 Class names](#522-class-names)), followed by the capital letter `T` (examples: `RequestT`, `FooBarE`).

### 5.3 Camel case: defined

Sometimes there is more than one reasonable way to convert an English phrase into camel case, such as when acronyms or unusual constructs like "IPv6" or "iOS" are present. To improve predictability, *Google Style* specifies the following (nearly) deterministic scheme.

Beginning with the prose form of the name:

1. Convert the phrase to plain ASCII and remove any apostrophes. For example, "Müller's algorithm" might become "Muellers algorithm".

2. Divide this result into words, splitting on spaces and any remaining punctuation (typically hyphens).
    - *Recommended*: if any word already has a conventional camel-case appearance in common usage, split this into its constituent parts (e.g., "AdWords" becomes "ad words"). Note that a word such as "iOS" is not really in camel case *per se*; it defies *any convention*, so this recommendation does not apply.

3. Now lowercase *everything* (including acronyms), then uppercase only the first character of:
    - .... each word, to yield *upper camel case*, or
    - .... each word except the first, to yield *lower camel case*

4. Finally, join all the words into a single identifier.

Note that the casing of the original words is almost entirely disregarded.

Examples:

| Prose form | Correct | Incorrect |
| --- | --- | --- |
| "XML HTTP request"      | `XmlHttpRequest`    | `XMLHTTPRequest`    |
| "new customer ID"       | `newCustomerId`     | `newCustomerID`     |
| "inner stopwatch"       | `innerStopwatch`    | `innerStopWatch`    |
| "supports IPv6 on iOS?" | `supportIpv6OnIos`  | `supportIPv6OnIOS`  |
| "YouTube importer"      | `YoutubeImporter`   | `YouTubeImporter`   |
| "AdWords processor"     | `AdwordsProcessor`  | `AdWordsProcessor`  |

`supportIpv6OnIos` is preferred over `supportsIpv6OnIos`. Verb should not ends with "s".

`YoutubeImporter` is preferred over `YouTubeImporter`, even though "YouTube" is the proper brand name.

`UmobileGateway` is preferred over `UMobileGateway`, even though the correct name is [U Mobile](https://u.com.my). Separating "U Mobile" into "U" and "Mobile" will distort the original meaning of the corporation.

---
**Note**: Some words are ambiguously hyphenated in the English language: for example "nonempty" and "non-empty" are both correct, so the method names `checkNonempty` and `checkNonEmpty` are likewise both correct. However `checkNonEmpty` is preferred.

---

## 6 Programming Practices

### 6.1 `@Override`: always used

A method is marked with the `@Override` annotation whenever it is legal. This includes a class method overriding a superclass method, a class method implementing an interface method, and an interface method respecifying a superinterface method.

**Exception**: `@Override` may be omitted when the parent method is `@Deprecated`. However it is preferred to retain the `@Override` for deprecated methods.

One possible ordering of [annotation](https://docs.oracle.com/javase/tutorial/java/annotations/predefined.html) is:

- `@Override` (first)
- `@SuppressWarnings`
- `@SafeVarargs`
- `@FunctionalInterface`
- other annotations (used by frameworks) in logical grouping, more general at the top, more specific at the bottom
- `@Deprecated` (last)

### 6.2 Caught exceptions: not ignored

Except as noted below, it is very rarely correct to do nothing in response to a caught exception. (Typical responses are to log it, or if it is considered "impossible", rethrow it as an `AssertionError` or `RuntimeException`.)

When it truly is appropriate to take no action whatsoever in a catch block, the reason this is justified is explained in a comment.

```java
try {
    int i = Integer.parseInt(response);
    return handleNumericResponse(i);
} catch (NumberFormatException ok) {
    // it's not numeric; that's fine, just continue
}
return handleTextResponse(response);
```

**Exception**: In tests, a caught exception may be ignored without comment *if* its name is or begins with `expected`. The following is a very common idiom for ensuring that the code under test *does* throw an exception of the expected type, so a comment is unnecessary here.

```java
try {
    emptyStack.pop();
    fail();
} catch (NoSuchElementException expected) {
}
```

[Checkstyle](https://checkstyle.sourceforge.io/config_blocks.html#EmptyCatchBlock) will ignore if there is some comment in the empty `catch` block.

### 6.3 Static members: qualified using class

When a reference to a static class member must be qualified, it is qualified with that class's name, not with a reference or expression of that class's type.

```java
Foo aFoo = ....;
Foo.aStaticMethod(); // good
aFoo.aStaticMethod(); // bad
somethingThatYieldsAFoo().aStaticMethod(); // very bad
```

### 6.4 Finalizers: not used

It is **extremely rare** to override `Object.finalize`.

---
**Tip**: Don't do it. If you absolutely must, first read and understand [Effective Java Item 8](http://books.google.com/books?isbn=0134686047), "Avoid finalizers and cleaners" very carefully, and *then* don't do it.

---

## 7 Javadoc

### 7.1 Formatting

#### 7.1.1 General form

The *basic* formatting of Javadoc blocks is as seen in this example:

```java
/**
 * Multiple lines of Javadoc text are written here,
 * wrapped normally....
 */
public int method(String p1) { .... }
```

.... or in this single-line example:

```java
/** An especially short bit of Javadoc. */
```

The basic form is always acceptable. The single-line form may be substituted when the entirety of the Javadoc block (including comment markers) can fit on a single line. Note that this only applies when there are no block tags such as `@return`.

#### 7.1.2 Paragraphs

One blank line - that is, a line containing only the aligned leading asterisk (`*`) - appears between paragraphs, and before the group of block tags if present. Each paragraph except the first has `<p>` immediately before the first word, with no space after it. HTML tags for other block-level elements, such as `<ul>` or `<table>`, are *not* preceded with `<p>`.

#### 7.1.3 Block tags

Any of the standard "block tags" that are used appear in the order `@param`, `@return`, `@throws`, `@deprecated`, and these four types never appear with an empty description. When a block tag doesn't fit on a single line, continuation lines are indented eight (or more) spaces from the position of the `@`.

### 7.2 The summary fragment

Each Javadoc block begins with a brief **summary fragment**. This fragment is very important: it is the only part of the text that appears in certain contexts such as class and method indexes.

This is a fragment - a noun phrase or verb phrase, not a complete sentence. It does **not** begin with `A {@code Foo} is a....`, or `This method returns....`, nor does it form a complete imperative sentence like `Save the record.`. However, the fragment is capitalized and punctuated as if it were a complete sentence.

---
**Tip**: A common mistake is to write simple Javadoc in the form `/** @return the customer ID */`. This is incorrect, and should be changed to `/** Returns the customer ID. */`.

---

### 7.3 Where Javadoc is used

At the *minimum*, Javadoc is present for every `public` class, and every `public` or `protected` member of such a class, with a few exceptions noted below.

Additional Javadoc content may also be present, as explained in Section [7.3.4 Non-required Javadoc](#734-non-required-javadoc).

#### 7.3.1 Exception: self-explanatory members

Javadoc is optional for "simple, obvious" members like `getFoo()`, in cases where there *really and truly* is nothing else worthwhile to say but "Returns the foo".

---
**Important**: it is not appropriate to cite this exception to justify omitting relevant information that a typical reader might need to know. For example, for a method named `getCanonicalName`, don't omit its documentation (with the rationale that it would say only `/** Returns the canonical name. */`) if a typical reader may have no idea what the term "canonical name" means!

---

#### 7.3.2 Exception: overrides

Javadoc is not always present on a method that overrides a supertype method.

#### 7.3.4 Non-required Javadoc

Other classes and members have Javadoc as *needed* or *desired*.

Whenever an implementation comment would be used to define the overall purpose or behavior of a class or member, that comment is written as Javadoc instead (using `/**`).

Non-required Javadoc is not strictly required to follow the formatting rules of Sections [7.1.1 General form](#711-general-form), [7.1.2 Paragraphs](#712-paragraphs), [7.1.3 Block tags](#713-block-tags), and [7.2 The summary fragment](#72-the-summary-fragment), though it is of course recommended.
