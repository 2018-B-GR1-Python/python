```
adrian = {
  "name": "Adrian"
}

try:
  adrian["last_name"]
except KeyError: # For keys
  print("Error in key")
except TypeError as error: # For Types
  print("Error in Type")
  print(error)
except Exception: # For unknown errors
  print("Error in Type")
```
