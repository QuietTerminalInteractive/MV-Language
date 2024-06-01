# MV Documentation

## Introduction
MV is a modern programming language designed with a strong focus on solving one main problem: version control. While current version control systems handle collaboration and history tracking for codebases, they often fall short in several key areas: they are complex, cumbersome, and the real kicker, they need to be online (not pointing fingers but *cough cough* Github *cough cough*). MV addresses these issues by incorporating version control directly into the language syntax, allowing developers to manage data states and history with ease within their programs.

MV aims to be a general-purpose, fast, and imperative language, balancing simplicity with speed. Significant indentation is a core part of its syntax, ensuring readability and structure.

## Syntax Guide

### Control Structures

1. **if**: Starts a conditional block.
    ```plaintext
    if condition:
        # Code to execute if condition is true
    ```

2. **else**: Follows an `if` block to execute code if the condition is false.
    ```plaintext
    if condition:
        # Code if true
    else:
        # Code if false
    ```

3. **elif**: Else if; checks another condition if the previous `if` or `elif` was false.
    ```plaintext
    if condition1:
        # Code if condition1 is true
    elif condition2:
        # Code if condition2 is true
    else:
        # Code if none are true
    ```

4. **while**: Starts a loop that continues while the condition is true.
    ```plaintext
    while condition:
        # Code to execute while condition is true
    ```

5. **for**: Starts a loop that iterates over a sequence.
    ```plaintext
    for item in collection:
        # Code to execute for each item
    ```

6. **in**: Used in loops to iterate over sequences.
    ```plaintext
    for item in collection:
        # Code for each item
    ```

7. **break**: Exits the nearest enclosing loop.
    ```plaintext
    for item in collection:
        if some_condition:
            break
    ```

8. **continue**: Skips the rest of the code inside the loop for the current iteration and starts the next iteration.
    ```plaintext
    for item in collection:
        if some_condition:
            continue
        # Code for each item
    ```

9. **return**: Exits a function and optionally returns a value.
    ```plaintext
    function add(a: Integer, b: Integer) -> Integer:
        return a + b
    ```

10. **match**: Pattern matching/switch-case statement.
    ```plaintext
    match value:
        case pattern1:
            # Code if value matches pattern1
        case pattern2:
            # Code if value matches pattern2
        default:
            # Code if no patterns match
    ```

### Data Types and Declarations

11. **let**: Declares a mutable variable.
    ```plaintext
    let x = 10
    x = 20  # Mutable, so reassignment is allowed
    ```

12. **versioned**: Declares a version-controlled variable.
    ```plaintext
    versioned let data = [1, 2, 3]
    data.append(4)
    data.commit()
    data.revert()  # Reverts to [1, 2, 3]
    ```

13. **const**: Declares an immutable variable.
    ```plaintext
    const y = 30
    y = 40  # Error: cannot reassign to a const variable
    ```

14. **function**: Declares a function.
    ```plaintext
    function greet(name: String) -> void:
        print("Hello, " + name)
    ```

15. **class**: Declares a class.
    ```plaintext
    class Person:
        let name: String
        function init(name: String):
            self.name = name
    ```

16. **struct**: Declares a struct, a composite data type.
    ```plaintext
    struct Point:
        let x: Integer
        let y: Integer
    ```

17. **enum**: Declares an enumerated type.
    ```plaintext
    enum Color:
        RED
        GREEN
        BLUE
    ```

18. **interface**: Declares an interface.
    ```plaintext
    interface Drivable:
        function drive() -> void
    ```

19. **type**: Declares a new type alias.
    ```plaintext
    type Age = Integer
    let myAge: Age = 25
    ```

20. **alias**: Creates an alias for an existing type or namespace.
    ```plaintext
    alias Vec = Vector
    let v: Vec = Vector(1, 2, 3)
    ```

### Concurrency

21. **async**: Declares an asynchronous function.
    ```plaintext
    async function fetchData() -> Data:
        # Asynchronous data fetching logic
    ```

22. **await**: Waits for an asynchronous operation to complete.
    ```plaintext
    let data = await fetchData()
    ```

23. **thread**: Declares a new thread for concurrent execution.
    ```plaintext
    thread let t = Thread(startFunction)
    ```

24. **spawn**: Starts a new thread.
    ```plaintext
    spawn taskFunction()
    ```

25. **sync**: Ensures atomicity of operations on versioned data.
    ```plaintext
    versioned let data = [1, 2, 3]
    sync data:
        data.append(4)
        data.append(5)
        data.commit()  # Commits both changes as a single atomic operation
    ```

26. **lock**: Locks a resource to prevent concurrent access.
    ```plaintext
    lock data:
        data.append(4)
        data.revert()
        data.commit()
    ```

### Exception Handling

27. **try**: Starts a block to catch exceptions.
    ```plaintext
    try:
        # Code that might throw an exception
    ```

28. **catch**: Catches exceptions thrown in a `try` block.
    ```plaintext
    catch (error):
        # Code to handle the exception
    ```

29. **finally**: A block that always executes after `try` and `catch`, used for cleanup.
    ```plaintext
    finally:
        # Cleanup code
    ```

30. **throw**: Throws an exception.
    ```plaintext
    throw new Error("Something went wrong")
    ```

31. **assert**: Checks a condition and throws an exception if it is false.
    ```plaintext
    assert value > 0, "Value must be positive"
    ```

### Access Modifiers

32. **public**: Makes a class member accessible from anywhere.
    ```plaintext
    class Example:
        public let x: Integer
    ```

33. **private**: Makes a class member accessible only within the class.
    ```plaintext
    class Example:
        private let x: Integer
    ```

34. **protected**: Makes a class member accessible within the class and its subclasses.
    ```plaintext
    class Example:
        protected let x: Integer
    ```

35. **internal**: Makes a class member accessible only within the same module.
    ```plaintext
    class Example:
        internal let x: Integer
    ```

### Memory Management

36. **free**: Frees manually allocated memory.
    ```plaintext
    let bigData = [1, 2, 3] * 1000000
    bigData.free()  # Manually free memory
    ```

### Data Versioning

37. **commit**: Commits changes to a versioned variable.
    ```plaintext
    versioned let data = [1, 2, 3]
    data.append(4)
    data.commit()
    ```

38. **revert**: Reverts changes to the last committed state of a versioned variable.
    ```plaintext
    versioned let data = [1, 2, 3]
    data.append(4)
    data.revert()  # Reverts to [1, 2, 3]
    ```

### Operators

39. **and**: Logical AND operator.
    ```plaintext
    if condition1 and condition2:
        # Code if both conditions are true
    ```

40. **or**: Logical OR operator.
    ```plaintext
    if condition1 or condition2:
        # Code if either condition is true
    ```

41. **not**: Logical NOT operator.
    ```plaintext
    if not condition:
        # Code if condition is false
    ```

### Other Keywords

42. **import**: Imports modules or libraries.
    ```plaintext
    import math
    ```

43. **export**: Exports modules or functions.
    ```plaintext
    export function myFunction() -> void:
        pass
    ```

44. **from**: Specifies the source of an import.
    ```plaintext
    from module import function
    ```

45. **as**: Renames an imported module or alias.
    ```plaintext
    import module as mod
    ```

46. **is**: Checks for identity.
    ```plaintext
    if a is b:
        # Code if a and b are the same object
    ```

47. **new**: Creates a new instance of a class.
    ```plaintext
    let obj = new ClassName()
    ```

48. **delete**: Deletes a variable or object.
    ```plaintext
    delete obj
    ```

49. **null**: Represents a null or no value.
    ```plaintext
    let value = null
    ```

50. **true**: Boolean true value.
    ```plaintext
    let isValid = true
    ```

51. **false**: Boolean false value.
    ```plaintext
    let isValid = false
    ```

52. **void**: Indicates a function returns no value.
    ```plaintext
    function logMessage(msg: String) -> void:
        print(msg)
    ```

53. **yield**: Pauses and returns a value from a generator function.
    ```plaintext
    function counter() -> Generator:
        let i = 0
        while true:
            yield i
            i += 1
    ```

54. **defer**: Defers the execution of a statement until the scope is exited.
    ```plaintext
    defer:
        # Code to execute at the end of the scope
    ```

55. **with**: Simplifies resource management by automatically releasing resources.
    ```plaintext
    with open('file.txt', 'r') as file:
        # Code using file
    ```

56. **lambda**: Declares an anonymous function.
    ```plaintext
    let add = lambda a, b: a + b
    ```

57. **doc**: Inline documentation.
    ```plaintext
    doc "This function adds two numbers"
    function add(a: Integer, b: Integer) -> Integer:
        return a + b
    ```

58. **meta**: Metadata annotations.
    ```plaintext
    @meta("author", "John Doe")
    class Example:
        pass
    ```

This syntax guide provides an overview of each keyword in the MV programming language and how to use them effectively in your code. By integrating version control and simplifying concurrency, MV offers a robust and efficient solution for modern programming challenges.
