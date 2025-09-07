# 🛠 Bash: Functions

> [!info] What is a function?
A function is a **mini-script inside your script**.  
It allows you to write reusable code.

---

[[Variables]] ← Previous | Next → [[Loops]]
## 🔹 Simple function
```bash
#!/bin/bash

function say_hello {
    echo "Hello from the function!"
}

say_hello
function say_hello { ... } — define a function

say_hello — call the function

🔹 Function with arguments
bash

#!/bin/bash

function greet {
    echo "Hello, $1!"
}

greet Harut
$1 — first argument to the function

You can pass any number of arguments

🔹 Return value
bash

#!/bin/bash

function sum {
    local result=$(( $1 + $2 ))
    echo $result
}

total=$(sum 5 7)
echo "Sum: $total"
local result — local variable inside function

Use $(...) to capture the function output

echo inside the function returns the result

[!tip]
Functions help keep your script clean and structured.
Use them when the same code is repeated multiple times.