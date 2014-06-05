‌‌

Statements 
----------

In Swift, there are two kinds of statements: simple statements and
control flow statements. Simple statements are the most common and
consist of either an expression or a declaration. Control flow
statements are used to control the flow of execution in a program. There
are three types of control flow statements in Swift: loop statements,
branch statements, and control transfer statements.

Loop statements allow a block of code to be executed repeatedly, branch
statements allow a certain block of code to be executed only when
certain conditions are met, and control transfer statements provide a
way to alter the order in which code is executed. Each type of control
flow statement is described in detail below.

A semicolon (;) can optionally appear after any statement
and is used to separate multiple statements if they appear on the same
line.

Grammar of a statement

‌ statement →
[expression](Expressions.xhtml#expression);~opt~

‌ statement →
[declaration](Declarations.xhtml#declaration);~opt~

‌ statement →
[loop-statement](Statements.xhtml#loop-statement);~opt~

‌ statement →
[branch-statement](Statements.xhtml#branch-statement);~opt~

‌ statement → [labeled-statement](Statements.xhtml#labeled-statement)

‌ statement →
[control-transfer-statement](Statements.xhtml#control-transfer-statement);~opt~

‌ statements →
[statement](Statements.xhtml#statement)[statements](Statements.xhtml#statements)~opt~

‌

### Loop Statements 

Loop statements allow a block of code to be executed repeatedly,
depending on the conditions specified in the loop. Swift has four loop
statements: a for statement, a
for
statement, and a do statement.

Control flow in a loop statement can be changed by a
break statement
and is discussed in [Break
Statement](Statements.xhtml#TP40014097-CH33-XID_976) and [Continue
Statement](Statements.xhtml#TP40014097-CH33-XID_979) below.

Grammar of a loop statement

‌ loop-statement → [for-statement](Statements.xhtml#for-statement)

‌ loop-statement → [for-in-statement](Statements.xhtml#for-in-statement)

‌ loop-statement → [while-statement](Statements.xhtml#while-statement)

‌ loop-statement →
[do-while-statement](Statements.xhtml#do-while-statement)

‌

### For Statement 

A for statement allows a block of code to be executed
repeatedly while incrementing a counter, as long as a condition remains
true.

A for statement has the following form:

-   ~~~~ 
    for initialization; condition; increment {
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    }
    ~~~~

The semicolons between the *initialization*, *condition*, and
*increment* are required. The braces around the *statements* in the body
of the loop are also required.

A for statement is executed as follows:

1.  The *initialization* is evaluated only once. It is typically used to
    declare and initialize any variables that are needed for the
    remainder of the loop.

2.  The *condition* expression is evaluated.

    If true, the program executes the *statements*, and
    execution continues to step 3. If false, the program
    does not execute the *statements* or the *increment* expression, and
    the program is finished executing the for statement.

3.  The *increment* expression is evaluated, and execution returns to
    step 2.

Variables defined within the *initialization* are valid only within the
scope of the for statement itself.

The value of the *condition* expression must have a type that conforms
to the LogicValue protocol.

Grammar of a for statement

‌ for-statement →
for[expression](Expressions.xhtml#expression)~opt~[code-block](Declarations.xhtml#code-block)

‌ for-statement →
for[code-block](Declarations.xhtml#code-block)

‌ for-init →
[variable-declaration](Declarations.xhtml#variable-declaration)
[expression-list](Expressions.xhtml#expression-list)

‌

### For-In Statement 

A for statement allows a block of code
to be executed once for each item in a collection (or any type) that
conforms to the Sequence protocol.

A for statement has the following form:

-   ~~~~ 
    for item in collection {
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    }
    ~~~~

The generate method is called on the *collection*
expression to obtain a value of a generator type—that is, a type that
conforms to the Generator protocol. The program begins
executing a loop by calling the next method on the
stream. If the value returned is not None, it is assigned
to the *item* pattern, the program executes the *statements*, and then
continues execution at the beginning of the loop. Otherwise, the program
does not perform assignment or execute the *statements*, and it is
finished executing the for statement.

Grammar of a for-in statement

‌ for-in-statement →
for[expression](Expressions.xhtml#expression)[code-block](Declarations.xhtml#code-block)

‌

### While Statement 

A while statement allows a block of code to be executed
repeatedly, as long as a condition remains true.

A while statement has the following form:

-   ~~~~ 
    while condition {
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    }
    ~~~~

A while statement is executed as follows:

1.  The *condition* is evaluated.

    If true, execution continues to step 2. If
    false, the program is finished executing the
    while statement.

2.  The program executes the *statements*, and execution returns to step
    1.

Because the value of the *condition* is evaluated before the
*statements* are executed, the *statements* in a while
statement can be executed zero or more times.

The value of the *condition* must have a type that conforms to the
LogicValue protocol. The condition can also be an
optional binding declaration, as discussed in [Optional
Binding](TheBasics.xhtml#TP40014097-CH5-XID_432).

Grammar of a while statement

‌ while-statement →
while[while-condition](Statements.xhtml#while-condition)[code-block](Declarations.xhtml#code-block)

‌ while-condition → [expression](Expressions.xhtml#expression)
[declaration](Declarations.xhtml#declaration)

‌

### Do-While Statement 

A do statement allows a block of
code to be executed one or more times, as long as a condition remains
true.

A do statement has the following
form:

-   ~~~~ 
    do {
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    } while condition
    ~~~~

A do statement is executed as
follows:

1.  The program executes the *statements*, and execution continues to
    step 2.

2.  The *condition* is evaluated.

    If true, execution returns to step 1. If
    false, the program is finished executing the
    do statement.

Because the value of the *condition* is evaluated after the *statements*
are executed, the *statements* in a
do statement are executed at least
once.

The value of the *condition* must have a type that conforms to the
LogicValue protocol. The condition can also be an
optional binding declaration, as discussed in [Optional
Binding](TheBasics.xhtml#TP40014097-CH5-XID_432).

Grammar of a do-while statement

‌ do-while-statement →
do[while-condition](Statements.xhtml#while-condition)

‌

### Branch Statements 

Branch statements allow the program to execute certain parts of code
depending on the value of one or more conditions. The values of the
conditions specified in a branch statement control how the program
branches and, therefore, what block of code is executed. Swift has two
branch statements: an if statement and a
switch statement.

Control flow in a switch statement can be changed by a
break statement and is discussed in [Break
Statement](Statements.xhtml#TP40014097-CH33-XID_976) below.

Grammar of a branch statement

‌ branch-statement → [if-statement](Statements.xhtml#if-statement)

‌ branch-statement →
[switch-statement](Statements.xhtml#switch-statement)

‌

### If Statement 

An if statement is used for executing code based on the
evaluation of one or more conditions.

There are two basic forms of an if statement. In each
form, the opening and closing braces are required.

The first form allows code to be executed only when a condition is true
and has the following form:

-   ~~~~ 
    if condition {
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    }
    ~~~~

The second form of an if statement provides an additional
*else clause* (introduced by the else keyword) and is
used for executing one part of code when the condition is true and
another part code when the same condition is false. When a single else
clause is present, an if statement has the following
form:

-   ~~~~ 
    if condition {
    ~~~~

-   ~~~~ 
        statements to execute if condition is true
    ~~~~

-   ~~~~ 
    } else {
    ~~~~

-   ~~~~ 
        statements to execute if condition is false
    ~~~~

-   ~~~~ 
    }
    ~~~~

The else clause of an if statement can contain another
if statement to test more than one condition. An
if statement chained together in this way has the
following form:

-   ~~~~ 
    if condition 1 {
    ~~~~

-   ~~~~ 
        statements to execute if condition 1 is true
    ~~~~

-   ~~~~ 
    } else if condition 2 {
    ~~~~

-   ~~~~ 
        statements to execute if condition 2 is true
    ~~~~

-   ~~~~ 
    } else {
    ~~~~

-   ~~~~ 
        statements to execute if both conditions are false
    ~~~~

-   ~~~~ 
    }
    ~~~~

The value of any condition in an if statement must have a
type that conforms to the LogicValue protocol. The
condition can also be an optional binding declaration, as discussed in
[Optional Binding](TheBasics.xhtml#TP40014097-CH5-XID_432).

Grammar of an if statement

‌ if-statement →
if[if-condition](Statements.xhtml#if-condition)[code-block](Declarations.xhtml#code-block)[else-clause](Statements.xhtml#else-clause)~opt~

‌ if-condition → [expression](Expressions.xhtml#expression)
[declaration](Declarations.xhtml#declaration)

‌ else-clause →
else[code-block](Declarations.xhtml#code-block)
else[if-statement](Statements.xhtml#if-statement)

‌

### Switch Statement 

A switch statement allows certain blocks of code to be
executed depending on the value of a control expression.

A switch statement has the following form:

-   ~~~~ 
    switch control expression {
    ~~~~

-   ~~~~ 
    case pattern 1:
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    case pattern 2 where condition:
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    case pattern 3 where condition,
    ~~~~

-   ~~~~ 
    pattern 4 where condition:
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    default:
    ~~~~

-   ~~~~ 
        statements
    ~~~~

-   ~~~~ 
    }
    ~~~~

The *control expression* of the switch statement is
evaluated and then compared with the patterns specified in each case. If
a match is found, the program executes the *statements* listed within
the scope of that case. The scope of each case can’t be empty. As a
result, you must include at least one statement following the colon
(:
statement if you don’t intend to execute any code in the body of a
matched case.

The values of expressions your code can branch on is very flexible. For
instance, in addition to the values of scalar types, such as integers
and characters, your code can branch on the values of any type,
including floating-point numbers, strings, tuples, instances of custom
classes, and optionals. The value of the *control expression* can even
be matched to the value of a case in an enumeration and checked for
inclusion in a specified range of values. For examples of how to use
these various types of values in switch statements, see
[Switch](ControlFlow.xhtml#TP40014097-CH9-XID_163) in the [Control
Flow](ControlFlow.xhtml) chapter.

A switch case can optionally contain a guard expression
after each pattern. A *guard expression* is introduced by the keyword
where followed by an expression, and is used to provide
an additional condition before a pattern in a case is considered matched
to the *control expression*. If a guard expression is present, the
*statements* within the relevant case are executed only if the value of
the *control expression* matches one of the patterns of the case and the
guard expression evaluates to true. For instance, a
*control expression* matches the case in the example below only if it is
a tuple that contains two elements of the same value, such as
(1, 1).

    case
    x:

As the above example shows, patterns in a case can also bind constants
using the keyword let (they can also bind variables using
the keyword var). These constants (or variables) can then
be referenced in a corresponding guard expression and throughout the
rest of the code within the scope of the case. That said, if the case
contains multiple patterns that match the control expression, none of
those patterns can contain constant or variable bindings.

A switch statement can also include a default case,
introduced by the keyword default. The code within a
default case is executed only if no other cases match the control
expression. A switch statement can include only one
default case, which must appear at the end of the switch
statement.

Although the actual execution order of pattern-matching operations, and
in particular the evaluation order of patterns in cases, is unspecified,
pattern matching in a switch statement behaves as if the
evaluation is performed in source order—that is, the order in which they
appear in source code. As a result, if multiple cases contain patterns
that evaluate to the same value, and thus can match the value of the
control expression, the program executes only the code within the first
matching case in source order.

‌

### Switch Statements Must Be Exhaustive 

In Swift, every possible value of the control expression’s type must
match the value of at least one pattern of a case. When this simply
isn’t feasible (for instance, when the control expression’s type is
Int), you can include a default case to satisfy the
requirement.

‌

### Execution Does Not Fall Through Cases Implicitly 

After the code within a matched case has finished executing, the program
exits from the switch statement. Program execution does
not continue or “fall through” to the next case or default case. That
said, if you want execution to continue from one case to the next,
explicitly include a fallthrough statement, which simply
consists of the keyword fallthrough, in the case from
which you want execution to continue. For more information about the
fallthrough statement, see [Fallthrough
Statement](Statements.xhtml#TP40014097-CH33-XID_982) below.

Grammar of a switch statement

‌ switch-statement →
switch

‌ switch-cases →
[switch-case](Statements.xhtml#switch-case)[switch-cases](Statements.xhtml#switch-cases)~opt~

‌ switch-case →
[case-label](Statements.xhtml#case-label)[statements](Statements.xhtml#statements)
[default-label](Statements.xhtml#default-label)[statements](Statements.xhtml#statements)

‌ switch-case → [case-label](Statements.xhtml#case-label);
[default-label](Statements.xhtml#default-label);

‌ case-label →
case

‌ case-item-list →
[pattern](Patterns.xhtml#pattern)[guard-clause](Statements.xhtml#guard-clause)~opt~
[pattern](Patterns.xhtml#pattern)[guard-clause](Statements.xhtml#guard-clause)~opt~,[case-item-list](Statements.xhtml#case-item-list)

‌ default-label → default

‌ guard-clause →
where[guard-expression](Statements.xhtml#guard-expression)

‌ guard-expression → [expression](Expressions.xhtml#expression)

‌

### Labeled Statement 

You can prefix a loop statement or a switch statement
with a *statement label*, which consists of the name of the label
followed immediately by a colon (:). Use statement labels with
break statements to be
explicit about how you want to change control flow in a loop statement
or a switch statement, as discussed in [Break
Statement](Statements.xhtml#TP40014097-CH33-XID_976) and [Continue
Statement](Statements.xhtml#TP40014097-CH33-XID_979) below.

The scope of a labeled statement is the entire statement following the
statement label. You can nest labeled statements, but the name of each
statement label must be unique.

For more information and to see examples of how to use statement labels,
see [Labeled Statements](ControlFlow.xhtml#TP40014097-CH9-XID_180) in
the [Control Flow](ControlFlow.xhtml) chapter.

Grammar of a labeled statement

‌ labeled-statement →
[statement-label](Statements.xhtml#statement-label)[loop-statement](Statements.xhtml#loop-statement)
[statement-label](Statements.xhtml#statement-label)[switch-statement](Statements.xhtml#switch-statement)

‌ statement-label →
[label-name](Statements.xhtml#label-name):

‌ label-name → [identifier](LexicalStructure.xhtml#identifier)

‌

### Control Transfer Statements 

Control transfer statements can change the order in which code in your
program is executed by unconditionally transferring program control from
one piece of code to another. Swift has four control transfer
statements: a break
statement, a fallthrough statement, and a
return statement.

Grammar of a control transfer statement

‌ control-transfer-statement →
[break-statement](Statements.xhtml#break-statement)

‌ control-transfer-statement →
[continue-statement](Statements.xhtml#continue-statement)

‌ control-transfer-statement →
[fallthrough-statement](Statements.xhtml#fallthrough-statement)

‌ control-transfer-statement →
[return-statement](Statements.xhtml#return-statement)

‌

### Break Statement 

A break statement ends program execution of a loop or a
switch statement can
consist of only the keyword break, or it can consist of
the keyword break followed by the name of a statement
label, as shown below.

-   ~~~~ 
    break
    ~~~~

-   ~~~~ 
    break label name
    ~~~~

When a break statement is followed by the name of a
statement label, it ends program execution of the loop or
switch statement named by that label.

When a break statement is not followed by the name of a
statement label, it ends program execution of the switch
statement or the innermost enclosing loop statement in which it occurs.

In both cases, program control is then transferred to the first line of
code following the enclosing loop or switch statement, if
any.

For examples of how to use a break statement, see
[Break](ControlFlow.xhtml#TP40014097-CH9-XID_174) and [Labeled
Statements](ControlFlow.xhtml#TP40014097-CH9-XID_180) in the [Control
Flow](ControlFlow.xhtml) chapter.

Grammar of a break statement

‌ break-statement →
break[label-name](Statements.xhtml#label-name)~opt~

‌

### Continue Statement 

A continue statement ends program execution of the
current iteration of a loop statement but does not stop execution of the
loop statement. A continue statement can consist of only
the keyword continue, or it can consist of the keyword
continue followed by the name of a statement label, as
shown below.

-   ~~~~ 
    continue
    ~~~~

-   ~~~~ 
    continue label name
    ~~~~

When a continue statement is followed by the name of a
statement label, it ends program execution of the current iteration of
the loop statement named by that label.

When a continue statement is not followed by the name of
a statement label, it ends program execution of the current iteration of
the innermost enclosing loop statement in which it occurs.

In both cases, program control is then transferred to the condition of
the enclosing loop statement.

In a for statement, the increment expression is still
evaluated after the continue statement is executed,
because the increment expression is evaluated after the execution of the
loop’s body.

For examples of how to use a continue statement, see
[Continue](ControlFlow.xhtml#TP40014097-CH9-XID_172) and [Labeled
Statements](ControlFlow.xhtml#TP40014097-CH9-XID_180) in the [Control
Flow](ControlFlow.xhtml) chapter.

Grammar of a continue statement

‌ continue-statement →
continue[label-name](Statements.xhtml#label-name)~opt~

‌

### Fallthrough Statement 

A fallthrough statement consists of the
fallthrough keyword and occurs only in a case block of a
switch statement
causes program execution to continue from one case in a
switch statement to the next case. Program execution
continues to the next case even if the patterns of the case label do not
match the value of the switch statement’s control
expression.

A fallthrough statement can appear anywhere inside a
switch statement, not just as the last statement of a
case block, but it can’t be used in the final case block. It also cannot
transfer control into a case block whose pattern contains value binding
patterns.

For an example of how to use a fallthrough statement in a
switch statement, see [Control Transfer
Statements](ControlFlow.xhtml#TP40014097-CH9-XID_171) in the [Control
Flow](ControlFlow.xhtml) chapter.

Grammar of a fallthrough statement

‌ fallthrough-statement → fallthrough

‌

### Return Statement 

A return statement occurs only in the body of a function
or method definition and causes program execution to return to the
calling function or method. Program execution continues at the point
immediately following the function or method call.

A return statement can consist of only the keyword
return, or it can consist of the keyword
return followed by an expression, as shown below.

-   ~~~~ 
    return
    ~~~~

-   ~~~~ 
    return expression
    ~~~~

When a return statement is followed by an expression, the
value of the expression is returned to the calling function or method.
If the value of the expression does not match the value of the return
type declared in the function or method declaration, the expression’s
value is converted to the return type before it is returned to the
calling function or method.

When a return statement is not followed by an expression,
it can be used only to return from a function or method that does not
return a value (that is, when the return type of the function or method
is Void).

Grammar of a return statement

‌ return-statement →
return[expression](Expressions.xhtml#expression)~opt~
