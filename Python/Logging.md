# 📝 Logging (Python DevOps)

[[Path Handling]] ← Previous | Next → [[Network]]

> [!info] Purpose
Logging is essential for **monitoring, debugging, and auditing** DevOps scripts.  
It’s better than using `print()` for production scripts.

---

## 🔹 Basic Logging Setup
```python
import logging

logging.basicConfig(
    filename="script.log",
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s"
)

logging.info("Script started")
logging.warning("This is a warning")
logging.error("An error occurred")
```

filename → file to save logs

level → minimum logging level (INFO, WARNING, ERROR)

format → customize log message

🔹 Logging Exceptions
```python

try:
    1 / 0
except ZeroDivisionError as e:
    logging.exception("Something went wrong!")
logging.exception() automatically logs the stack trace
```

[!tip]
Always log start and end of script, key actions, and errors for reliable DevOps automation.