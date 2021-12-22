[原文](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)

#### 语法
>grep [options] pattern [files]

>Options Description  
-c : This prints only a count of the lines that match a pattern  
-h : Display the matched lines, but do not display the filenames.  
-i : Ignores, case for matching  
-l : Displays list of a filenames only.  
-n : Display the matched lines and their line numbers.  
-v : This prints out all the lines that do not matches the pattern  
-e exp : Specifies expression with this option. Can use multiple times.  
-f file : Takes patterns from file, one per line.  
-E : Treats pattern as an extended regular expression (ERE)  
-w : Match whole word  
-o : Print only the matched parts of a matching line, with each such part on a separate output line.  
-A n : Prints searched line and nlines after the result.  
-B n : Prints searched line and n line before the result.  
-C n : Prints searched line and n lines after before the result.  

#### 示例
```console
$ cat > geekfile.txt  
unix is great os. unix is opensource. unix is free os.  
learn operating system.  
Unix linux which one you choose.  
uNix is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful.
```

1. 忽略大小写
```console
$ grep -i "UNix" geekfile.txt  
unix is great os. unix is opensource. unix is free os.
Unix linux which one you choose.
uNix is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful.
```

2. 查询匹配的行数
```console
$ grep -c "unix" geekfile.txt
2
```

3. 查询包含模式的文件名
```console
$ grep -l "unix" geekfile.txt f1.txt f2.txt f3.xt f4.txt
geekfile.txt
```

4. 仅匹配whole word
```console
$ grep -w "unix" geekfile.txt
unix is great os. unix is opensource. unix is free os.
uNix is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful.
```

5. 仅打印匹配的模式部分
```console
$ grep -o "unix" geekfile.txt
unix
unix
unix
unix
unix
unix
```

6. 打印匹配行所在的行数
```console
$ grep -n "unix" geekfile.txt
1:unix is great os. unix is opensource. unix is free os.
4:uNix is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful.
```

7. 打印不匹配的行
```console
$ grep -v "unix" geekfile.txt
learn operating system.
Unix linux which one you choose.
```