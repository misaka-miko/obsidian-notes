# Quick Reference
- `.` : any one character
- `*` : match any number of the previous (including **ZERO**)  
- `+` : match any number of the previous
- `$` : end of the line
- `^` : beginning of the line
- `\S` : any non-whitespace character
- `\s` : any whitespace character
- `?` : optional
- `\` : escape something
- `[a-z]` : any lowercase letter
- `[A-Z]` : any uppercase letter
- `[A-Za-z]` :  any letter

**哪里去尝试**：使用 `grep` `sed` `awk` ...

---
# 匹配特定字符
比如说我们要在文件里找 `file` 这个pattern，我们可以使用 `grep "file" <filename>` 其中 `file` 已经是一个regex了

---
# 匹配任意字符
比如我要找的词开头和结尾都一样，只有中间的词不一样，如：
- fix
- fox
- fax
- ...
使用 `grep "f.x" <filename>` 即可

---
# 匹配任意数量的字符
`grep "f.*x" <filename>` 可以匹配
- fox
- fix
- fooooooooox
- fx
- ...

**你可以注意到**：我们甚至匹配到了 `fx` 原因在于 `*` 代表的任意数量包含 *0* 
为了避免这件事，请使用 `+` （可能需要加 `\` ）