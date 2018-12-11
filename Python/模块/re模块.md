# re模块

## 单个匹配

\w 匹配字母（包含中文）或数字或下划线
\W 匹配非字母（包含中文）或数字或下划线
```python
print(re.findall('\w', 'abc_  123$%^'))  # 返回 ['a', 'b', 'c', '_', '1', '2', '3']
print(re.findall('\W', 'abc哈哈123_  123$%^'))  # 返回 [' ', ' ', '$', '%', '^']
```

\s 	匹配任意的空白符
\S 	匹配任意非空白符
```python
print(re.findall('\s', '哈哈 \t \n'))  # 返回 [' ', '\t', ' ', '\n']
print(re.findall('\S', '哈哈 \t \n'))  # 返回 ['哈', '哈']
```

\d 	匹配数字
\D 	匹配非数字
```python
print(re.findall('\d', 'xeon 哈哈 123'))  # 返回 ['1', '2', '3']
print(re.findall('\D', 'xeon 哈哈 123* \n \t + -'))  # 返回 ['x', 'e', 'o', 'n', ' ', '哈', '哈', ' ', '*', ' ', '\n', ' ', '\t']
```

\A 	从字符串开头匹配
^ 	匹配字符串的开始
```python
print(re.findall('\A太白', '太白 太白 123*'))  # 只匹配第一个，有责返回，无责返回[]
print(re.findall('^太白', '太白 太白 123*'))  # 只匹配第一个，有责返回，无责返回[]
```

$ 	匹配字符串的结尾
```python
print(re.findall('123$', 'xeon 哈哈 123'))  # 返回123
```

\n 	匹配一个换行符
\t 	匹配一个制表符
```python
print(re.findall('\n', '** 太白 哈哈 \n123 \n456'))  # 返回 ['\n', '\n']
print(re.findall('\t', '*\t* 太白 哈哈 \t123 \n456'))  # 返回 ['\t', '\t']
```

## 重复匹配
匹配任意字符，除了换行符（re.DOTALL 这个参数可以匹配\n）
找不到按一位一位找，找到了，从b位后开始找
```python
print(re.findall('a.b', 'ab aab abb a*b a6b a b aaaab'))  # 返回 ['aab', 'abb', 'a*b', 'a6b', 'a b', 'aab']
print(re.findall('a.b', 'ab aab abb a\nb a\tb', re.DOTALL))  # 返回 ['aab', 'abb', 'a\nb', 'a\tb']
```

？匹配0个或者1个由左边字符定义的片段  贪婪匹配
```python
print(re.findall('a?b', 'aaaaab'))  # 返回 ['ab']
print(re.findall('a?b', 'ab aab abb a*b'))  # 返回 ['ab', 'ab', 'ab', 'b', 'b']
```

\* 匹配0个或者多个左边字符表达式。 满足贪婪匹配 @@
```python
print(re.findall('a*b', 'ab aab aaaaaaab abbbbb'))  # 返回 ['ab', 'aab', 'aaaaaaab', 'ab', 'b', 'b', 'b', 'b']
```

\+ 匹配1个或者多个左边字符表达式。 满足贪婪匹配  @@
```python
print(re.findall('a+b', 'ab aab aaab abbb'))  # 返回 ['ab', 'aab', 'aaab', 'ab']
```

{m,n}  匹配m个至n个左边字符表达式。 满足贪婪匹配  @@
```python
print(re.findall('a{2,4}b', 'ab aab aaaab abbbb'))  # 返回 ['aab', 'aaaab']
```

.* 贪婪匹配 从头到尾.  纯贪模式一般不用
```python
print(re.findall('a*b', 'ea*b ab aab aaaaaaaaab abbb'))  # 返回 ['b', 'ab', 'aab', 'aaaaaaaaab', 'ab', 'b', 'b']
```

.*? 此时的?不是对左边的字符进行0次或者1次的匹配  .* 纯贪  ? 作为限制 满足我就取出  常用模式
```python
print(re.findall('a.*?b', 'a*b ab aab aaaaaaaaab abbb'))  # 返回 ['a*b', 'ab', 'aab', 'aaaaaaaaab', 'ab']
```

[ ] 代表一个字符  # erw 任意选一个
```python
print(re.findall('a[erw][erw]b', 'ab aab aeb arb arwb arewb'))  # 返回 ['arwb']
str1 = 'a1b a2b a3b aab aeb a9b'
str2 = 'a1b aTb a3b aAb aeb a_b ayb'
str3 = 'a1b aTb a3b a-b a%b a!b a&b'
print(re.findall('a[0-9]b', str1))  # ['a1b', 'a2b', 'a3b', 'a9b']
print(re.findall('a[a-z]b', str2))  # ['aeb', 'ayb']
print(re.findall('a[a-z,A-Z]b', str3))  # 返回 ['aTb']
```
##分组
() 制造了一个模板(.*?)_sb
```python
print(re.findall('(.*?)_sb', 'alex_sb wusir_sb 日天_sb'))  # 返回 ['alex', ' wusir', ' 日天']
print(re.findall('href="(.*?)"', '<a href="http://www.baidu.com">点击</a>'))  # 取出网址并以列表显示
```

| 匹配 左边或者右边
```python
print(re.findall('alex|太白|wusir', 'alex太白wusiraleeeex太太白odlb'))  # 返回 ['alex', '太白', 'wusir', '太白']
print(re.findall('compan(ies|y)','Too many companies have gone bankrupt, and the next one is my company'))  # ['ies', 'y']

# 但是我想将 companies  company ?: 对分组进行一个应用，全部都取出来
print(re.findall('compan(?:ies|y)','Too many companies have gone bankrupt, and the next one is my company'))
返回 ['companies', 'company']
```

##re模块的操作方法
findall 找到全部
```python
print(re.findall('a.b', 'abaabb'))  # ['aab']
```
search 相当于 in
```python
print(re.search('sb|alex', 'alex sb sb barry 日天'))  # <_sre.SRE_Match object; span=(0, 4), match='alex'>
print(re.search('aaa', 'alex sb sb barry 日天'))  # <_sre.SRE_Match object; span=(0, 4), match='alex'>
print(re.search('sb|alex', ' 666 sb alex sb barry 日天').group())  # sb
```

match 匹配的就是开始
```python
print(re.match('aaa', 'aaa sb sb barry 日天'))  # <_sre.SRE_Match object; span=(0, 3), match='aaa'>
print(re.match('aaa', 'aa sb sb barry 日天'))  # None
print(re.findall('^aaa', 'aa sb sb barry 日天'))  # []
```

## 分割 替换
```
split 分割 可按照任意分割符进行分割
s1 = 'alex wusir 日天 太白'
s1 = 'alex wusir,日天;太白|二狗'
print(s1.split())

对字符串按照不同分隔符进行分割
print(re.split(' |,|;|\|',s1))
sub 替换
print(re.sub('barry', '太白', 'barry是最好的讲师，barry就是一个普通老师，请不要将barry当男神对待。'))
print(re.sub('(alex)( )(is)( )(sb)', r'\5\2\3\4\1', r'alex is sb'))

将字符串的第一个与最后一个单词！互换位置
print(re.sub('([a-zA-Z]+)([^a-zA-Z]+)([a-zA-Z]+)([^a-zA-Z]+)([a-zA-Z]+)', r'\5\2\3\4\1', r'alex     is 1232 sb'))
print(re.findall('[a-zA-Z]+', 'alex1wusir3 12321'))

obj = re.compile('\d{2}')
print(obj.search('abc123eeee').group())
print(obj.findall('abc123eeee'))

ret = re.finditer('\d', 'ds3sy4784a')   #finditer返回一个存放匹配结果的迭代器
print(ret)  # <callable_iterator object at 0x10195f940>
print(next(ret).group())  #查看第一个结果 3
print(next(ret).group())  #查看第二个结果 4
print([i.group() for i in ret])  #查看剩余的左右结果 ['7', '8', '4']
```
##举例

例子1:
s1 = "1-2*(60+(-40.35/5)-(-4*3))"
```python
1 匹配所有的整数  (pass)
print(re.findall('\d+', s1))  # ['1', '2', '60', '40', '35', '5', '4', '3']

2 匹配所有的数字（包含小数）
print(re.findall('\d+\.?\d*', s1))  # ['1', '2', '60', '40.35', '5', '4', '3']

3 匹配所有的数字
print(re.findall('-?\d+\.?\d*', s1))  # ['1', '-2', '60', '-40.35', '5', '-4', '3']
```

例子2：
`s1 = '''
<p><a style="text-decoration: underline;" href="http://www.cnblogs.com/jin-xin/articles/7459977.html" target="_blank">python基础一</a></p>
<p><a style="text-decoration: underline;" href="http://www.cnblogs.com/jin-xin/articles/7562422.html" target="_blank">python基础二</a></p>
'''`
```
1.找到所有的p标签
print(re.findall('<p>.*?</p>', s1))
```