### Group members

121891 &nbsp; Salomon Metre <br>
131548 &nbsp; Nathan Ruru <br>
134977 &nbsp; Jeff Munyigi <br>
119314 &nbsp; Oguta Cassey Moses <br> 
129040 &nbsp; Wambua James Mutua <br>

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
