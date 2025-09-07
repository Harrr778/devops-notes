# ⚙️ Configs (Python DevOps)

[[Network]] ← Previous | Next → [[Python/Practice]]

> [!info] Purpose
In DevOps, scripts often need **configuration files**. Using JSON or YAML makes scripts flexible and maintainable.

---

## 🔹 Working with JSON
```python
import json

# Read JSON
with open("config.json") as f:
    config = json.load(f)

print(config["host"])

# Write JSON
config["port"] = 8080
with open("config.json", "w") as f:
    json.dump(config, f, indent=4)
🔹 Working with YAML
python
Copy code
import yaml

# Read YAML
with open("config.yaml") as f:
    config = yaml.safe_load(f)

print(config["database"]["user"])

# Write YAML
config["database"]["password"] = "secret"
with open("config.yaml", "w") as f:
    yaml.safe_dump(config, f)
Use pip install pyyaml if yaml is not installed

YAML is common in CI/CD pipelines (GitHub Actions, GitLab CI, Ansible)
```

[!tip]
Always separate config files from scripts. This allows changing parameters without editing code.