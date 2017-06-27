# Regular Expression Matching (Python 3)

Match string via regular expression within strings.txt and and print enumerated list to results.txt

```python
import re

regxString = ''

target = open("results.txt", "w")
pattern = re.compile(regxString)

for e, line in enumerate(open('strings.txt')):

    for match in re.finditer(pattern, line):
        if match:
            print ()'Match Found:', match.groups(), line)
            target.write (line)

target.close()
```

[re documentation](https://docs.python.org/2/library/re.html)

[regexr tool](http://regexr.com/)
