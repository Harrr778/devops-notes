# 🚀 Bash: Running Scripts

> [!info] What is Bash?
**Bash (Bourne Again Shell)** is a popular shell in Linux and macOS.  
It allows you to execute commands and write **automation scripts**.

---
Next → [[Variables]]
## ✨ First script
```bash
#!/bin/bash
echo "Hello, World!"
#!/bin/bash — tells the system to use Bash to run the script

echo — prints text to the screen

🔧 How to run a script
Create a file:

bash

nano hello.sh
Paste the code:

bash

#!/bin/bash
echo "Hello, World!"
Make it executable:

bash

chmod +x hello.sh
Run it:

bash

./hello.sh
[!tip]
You can also run it without changing permissions:

bash

bash hello.sh