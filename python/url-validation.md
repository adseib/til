
```python
import urllib.request as req
import urllib.parse as p

def test(url):

    request = req.Request(url)
        try:
    response = req.urlopen(request)
        except:
            print('not valid earl')
````

>>> test()
