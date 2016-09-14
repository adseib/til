#Regular Expression Matching

Match string via regular expression within strings.txt and and print enumerated list to results.txt

```python
import re
target = open("results.txt", "w")
pattern = re.compile("^(A|B|C20|HC|INC|M|NY|PFA|S|SS|T|TI|625|825)*\-[0-9]{1,2}(0|1|M|F){1}[0-5]{1}\-[A-Z0-9]*\-?.*")

for e, line in enumerate(open('strings.txt')):

	
    for match in re.finditer(pattern, line):
	
	if match:
		print 'Match Found:', match.groups(), line 
		target.write (line)
	

target.close()
```

[source](https://docs.python.org/2/library/re.html)
[regexr tool](http://regexr.com/)