### Group members

121891 Salomon Metre
131548 Nathan Ruru
134977 Jeff Munyigi
119314 Oguta Cassey Moses 
129040 Wambua James Mutua

### Logic of Task 1

The Python script reads a C++ file line by line and identifies comments within the code. The comments can be single-line comments starting with `//` or multi-line comments enclosed between `/*` and `*/`.

### Function to Check if a Line is a Comment

```python
def is_comment(line):
    if line.strip().startswith("//"):
        return True
    return re.match(r'/\*.*\*/', line.strip()) is not None
```

### 
