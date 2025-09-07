# 🔁 Bash: Loops

> [!info] What is a loop?
A loop allows you to **repeat the same code multiple times** without copying it.

---
[[Functions]] ← Previous | Next → [[Conditions]]
## 🔹 For loop (over a list)
```bash
#!/bin/bash

for i in 1 2 3 4 5; do
    echo "Number: $i"
done
for i in ...; do ... done — basic syntax

$i — current value in each iteration

🔹 While loop (while condition is true)
bash

#!/bin/bash

count=1
while [ $count -le 5 ]; do
    echo "Counter: $count"
    ((count++))
done
[ $count -le 5 ] — condition check

((count++)) — increment counter

🔹 Until loop (while condition is false)
bash

#!/bin/bash

num=1
until [ $num -gt 5 ]; do
    echo "num = $num"
    ((num++))
done
until executes until the condition becomes true

[!tip]

Use loops for processing lists of files, arguments, or numbers.

break — exit the loop

continue — skip the current iteration