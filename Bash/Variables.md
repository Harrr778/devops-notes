# 💾 Bash: Variables

> [!info] What is a variable?
A variable is a "container" where you can store a value and use it in your script.

---

[[Bash/Running]] ← Previous | Next → [[Functions]]

## 🔹 Creating a variable
```bash
NAME="Harut"
echo "Hello, $NAME!"
NAME="Harut" — creating a variable

$NAME — using the variable

🔹 Script arguments
bash

#!/bin/bash
echo "Script name: $0"
echo "First argument: $1"
echo "All arguments: $@"
Run:

bash

./myscript.sh test 123
Output:

bash

Script name: ./myscript.sh
First argument: test
All arguments: test 123
🔹 System variables
Variable	Meaning
$USER	current user
$HOME	home directory
$PWD	current working directory

Example:

bash

echo "You are logged in as $USER"
echo "Your home folder is $HOME"
```

[!tip]  
Variables are **case-sensitive**:  
`NAME` and `name` are **different variables**.
