# 📝 Bash: Conditions

> [!info] What is a condition?
A condition allows your script to **make decisions** and execute code **only if certain criteria are met**.

---
[[Loops]] ← Previous | Next → [[Bash/Practice]]
## 🔹 If-Else statement
```bash
#!/bin/bash

if [ "$USER" == "root" ]; then
    echo "You are root"
else
    echo "You are a regular user"
fi
if [ condition ]; then ... fi — basic syntax

else — alternative code if the condition is false

🔹 If-Elif-Else

bash

#!/bin/bash

num=7

if [ $num -gt 10 ]; then
    echo "Number is greater than 10"
elif [ $num -eq 7 ]; then
    echo "Number is seven"
else
    echo "Number is something else"
fi
elif — “else if” for multiple conditions

🔹 File checks
Test	Meaning
-f file	Does the file exist?
-d dir	Does the directory exist?
-e path	Does the path exist?

Example:

bash

if [ -f "/etc/passwd" ]; then
    echo "File exists"
fi
[!tip]

Conditions can be combined with && (and) and || (or).

Always use spaces around brackets: [ $a -eq $b ] not [$a -eq $b].