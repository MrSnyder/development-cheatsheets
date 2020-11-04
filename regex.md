# Regex Cheatsheet

## sed
```bash
# base structure
sed 's/FIND_STRING/REPLACE_STRING/OPTIONS'
# examples
sed 's/<proxyBaseUrl>.*<\/proxyBaseUrl>/<proxyBaseUrl>https:\/\/whatever.de<\/proxyBaseUrl>/'
```
### Options
* /g: global (by default, only replaces the first match)