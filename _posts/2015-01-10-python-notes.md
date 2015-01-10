---
layout: post
title: Python Notes
---

**Ground Work**

- sys.argv[0] ---- program name itself 
- arguments and variables similar no types 

``` python
def Hello(name):
    a = 'hello'
```    

- `print` seperate by , then space is includes automatically
- `print 'Hello',name,a`   ===> Hello rohan!!! 10
- `print'Hello'+name+str(a)` ⇒ Hellorohan!!!10
- string not empty, num is not 0 -- > true

**How python works**

- does everything at last possible second
- in the moment it checks at every line 
- strings are immutable (returns new string)
- `a.find()` - returns first occurance
- `a.lower()` 
- place holder `%`
- `'Hi %s I have %d donuts' %  (‘Alice’,29)`
- These are not python strings and not unicode strings these are just series of bytes.

**Strings slice**

``` 
>>> a = 'Hello'
>>> a
'Hello'
>>> a[1:3]
'el'
>>> a[1:2]
'e'
>>> a[1:5]
'ello'
>>> a[1:]
'ello'
>>> a[:5]
'Hello'
>>> a[:]
'Hello'
```

***Negatives***

```
>>> a = 'Hello'
>>> a[-1]
'o'
>>> a[-3:]
'llo'
>>> a[-3:-1]
'll'

```
**Lists**

- Same syntax across all 
- `a = [1,2,3,’a’]`
- `len(a)` to find length
- `b = a` (does not create a copy both point to same)
- lists are *'mutable'*
- python has garbage collector {need to make copies is not much}
- `a ==b` does the same returns `true`
- *slices* works fine with lists as well
- There is built in **for each**
```
for var in list:
    print var
```    
- **Check** if value in a list {works for lot of DS - in hash table does }
- value in list
- Built in for lists
- `append` - does not return new list returns None
- `a = [1,2,3]`
- `a.append(4)`
- `a = a.append(4) # error NO NO`
-  `a.pop(0)`  pops of element and returns it
- delete a from local scope
- `del a` {complete list}
- `del a[1]`   {delete a element}
- The `range(n)` function yields the numbers 0, 1, ... 
- `for i in range(100)    print i`

**Sorting**

- sorting of lists - don't use `.sort()`
- `sorted` - makes a new list and sorts.
- comparison depends on the type of elements compared.{strings,ints,char}

**custom sorting**

- old way 2 argument comparator method. python has new way
- sort by length

```
>>> sorted(a,key=len)
['d', 'a', 'dc', 'aa', 'ccc']
>>> def last(s): return s[-1]

>>> sorted(a,key=last)
['a', 'aa', 'ccc', 'dc', 'd']
split, join
>>> ':'.join(a)
'z:d:dc:a:aa'
>>> '\n'.join(a)
'z\nd\ndc\na\naa'
>>> ':'.join(a)
'z:d:dc:a:aa'
>>> b = ':'.join(a)
>>> b.split(':')
['z', 'd', 'dc', 'a', 'aa']
```

- Don’t modify list while iterating a list (even java has same constraint)

**Tuple**

- Fixed size 
- immutable
- `tup = (1,2,3)`
- `(x,y,z)` coordinates; `(url,score)` {taking fixed number of strings and pass together)
```
>>> a = (1,3,3)
>>> a
(1, 3, 3)
>>> len(a)
3
>>> a[0]
1
>>> a[0]=2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
Sort by one thing and then sort by other 
Write key function that returns a tuple
	>>> a = [(1,"b"),(2,"a"),(1,"a")]
>>> a
[(1, 'b'), (2, 'a'), (1, 'a')]
>>> sorted(a)
[(1, 'a'), (1, 'b'), (2, 'a')]
Parallel assignment 
	>>> (x,y) = (1,2)
```

**HashTable , /Dictionary**

- {}
- key,value bindings
- constant time retrieval 

```
>>> d ={}
>>> d['a'] = 'alpha'
>>> d['a']
'alpha'
>>> d['B']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'B'
```

**get(),keys(),items()**

```
d.get()
>>> d.get('a')
'alpha'
>>> d.get('f')
how to find if something is in dict
‘a’ in d
True
.keys()

>>> d.keys()
['a']
>>> d['b'] = 'beta'
>>> d.keys()
['a', 'b']
values()
>>> d.values()
['alpha', 'beta']
```

**looping**

```
>>> for k in sorted(d.keys()): print 'key:',k,'->',d[k]
... 
key: a -> alpha
key: b -> beta
d.items()
	>>> d.items()
[('a', 'alpha'), ('b', 'beta')]
>>> for tuple in d.items(): print tuple
... 
('a', 'alpha')
('b', 'beta')
```


**Files**

- creating cat python
- `f = open(filename,'r')`
- diff modes - `'r','w''rU'`
```
text = f.read()
lines = f.readlines()
f.open(fname,”w”)
f.write(text)   {be careful we can zero out file}
```

**Regular Expression**

- import re
- returns a match object
- match = re.search(pattern,text)
- match = re.search(‘iig’,’its a piiiiiiiig’)
- if match:
- . dot any character except new line
--\w word character
--\d digit
--\s space
- left to right once it finds solution it is done 
- if looking for period char 
```
>>> Find('a\.','its a. piiiiiiiig')
a.
```
- raw string 
 - do not do any special processing with backslashes
- uses for writing regex

```
\S non whitespace
\s whitespace
\d digit 0-9
\w word character a-z A-Z 0-9
```


**Email example**

```
>>> m = re.search(r'([\w.]+)@([\w.]+)','egrreg gjkenrkj@snfjkv.com erngjk @ ')
>>> m
<_sre.SRE_Match object at 0xb7467800>
>>> m.group()
'gjkenrkj@snfjkv.com'
>>> m.group(1)
'gjkenrkj'
>>> m.group(2)
'snfjkv.com'
>>> m = re.search(r'([\w.]+)@([\w.]+)','egrreg gjken.rkj@snfjkv.com erngjk @ ')
>>> m
<_sre.SRE_Match object at 0xb7467140>
>>> m.group(1)
'gjken.rkj'
>>> m.group(2)
'snfjkv.com'
findall()
	>>re.findall(r'[\w.]+@[\w.]+','egrreg@fmail.com gjken.rkj@snfjkv.com erngjk @ ')
['egrreg@fmail.com', 'gjken.rkj@snfjkv.com']

 re.findall(r'([\w.]+)@([\w.]+)','egrreg@fmail.com gjken.rkj@snfjkv.com erngjk @ ')
[('egrreg', 'fmail.com'), ('gjken.rkj', 'snfjkv.com')]
```

**Flags**

- DOTALL also matches newline aswell 
- how to use constants
```
>>> m = re.search(r'rohan','ROHAN',re.IGNORECASE)
>>> m
<_sre.SRE_Match object at 0xb726b3d8>
>>> m.group()
'ROHAN'
```

**Modules**

- os module
- platform independent systime 
- `listdir(path)` ----> list of strings
     1. `import os`       
        `os.path.exists(‘/tmp/foo’)`
     2. `import shutil` <br />
	  `shutil.copy(source, dest)`   ---- >file copying 
     3. `import commands`<br />
	launch a external process and wait for it to finish<br />
	`commands.getstatusoutput(cmd)` <br />
	returns a tuple of length 2 `(status,output)` 1st int exit code 2nd is all output std output and std error
- `zip -j name all absolute paths`

**Exceptions**

``` 
def cat(filename):
  try:
    f = open(filename, 'rU') #U ignare dos line ending unix
    print '-----',filename
    text = f.read() #having just 1 string
    print text
    f.close()
  except IOError:
    print 'No File',filename 
def main():
  args = sys.argv[1:]
  for arg in args:
    cat(arg)
```

**Modularity**

- just .py file namespace 
- when we load a python file it runs (do not wrie print outside)<br/> 
```
>>> import babynames
Hi There !!!
>>> dir(babynames)
['__builtins__', '__doc__', '__file__', '__name__', '__package__', 'extract_names', 'main', 're', 'sys']
   >>help(babynames.extract_names)
```

**urllib**

- Takes url and makes it to look like a file
- `import urllib`
- Takes a url and tries to look like a file
- `uf = urllib.urlopen(‘http://google.com’)`
- `uf.read()`
- has lots of features , set cookies 
 ```
>>> urllib.urlretrieve('http://google.com/intl/en_ALL/images/logo.gif','blah.gif')
('blah.gif', <httplib.HTTPMessage instance at 0xb6fa870c>)
```
