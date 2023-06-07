#### Insert line after match found
```console
sed '/^anothervalue=.*/a after=me' test.txt
```

#### Insert a line before match found
```console
sed '/^anothervalue=.*/i before=me' test.txt
```

#### Insert multiple lines
```console
sed '/^anothervalue=.*/i before=me\nbefore2=me2' test.txt
```