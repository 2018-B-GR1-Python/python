```python
adrian = {
  "name": "Adrian",
  "age": 1,
  "married": False
}

adrian["name"] # "Adrian"

adrian.get("name", False) # False

adrian.keys() # ["name","age","married"]
adrian.keys() # ["Adrian",1,False]
adrian["name"] = "Vicente"
```
