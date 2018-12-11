# day01 练习题

1、简述变量命名规范
```python
a.变量必须要有数字,字母,下划线,任意组合
b.变量不能是数字开头
c.不能是python中的关键字
d.变量要具有可描述性
e.变量不建议使用中文
f.变量不能过长
j.变量写法推荐使用下划线方法: age_of_student = 23
```

2、name = input(“>>>”) name变量是什么数据类型？
```
name是字符串类型
```

3、if条件语句的基本结构?
结构1:
```
if 条件:
    pass
```

结构2:
```
if 条件:
    pass
elif:
    pass
```    

结构3:
```
if 条件:
    pass
elif:
    pass
else:
    pass
```    

4、用print打印出下面内容：
文能提笔安天下,
武能上马定乾坤.
心存谋略何人胜,
古今英雄唯是君.
```python
msg = """
文能提笔安天下,
武能上马定乾坤.
心存谋略何人胜,
古今英雄唯是君.
"""
print(msg)
```

5、利用if语句写出猜大小的游戏：
设定一个理想数字比如：66，让用户输入数字，
如果比66大，则显示猜测的结果大了；
如果比66小，则显示猜测的结果小了;
只有等于66，则显示猜测结果正确。
```python
number = int(input('请输入数字:'))
if number > 66:
   print('猜测的结果大了')
elif number < 66:
   print('猜测的结果小了')
elif number == 66:
   print('猜测结果正确')
```


6、提示用户输入他的年龄, 程序进行判断.
如果小于10,提示小屁孩儿,
如果大于10,小于20. 提示青春期叛逆的小屁孩儿.
如果大于20,小于30. 提示开始定性, 开始混社会的小屁孩儿,
如果大于30,小于40. 提示看老大不小了, 赶紧结婚生屁孩儿.
如果大于40,小于50. 提示家有个不听话的小屁孩儿.
如果大于50,小于60. 提示自己马上变成不听话的老屁孩儿.
如果大于60,小于70. 提示活着还不错的老屁孩儿.
如果大于70,小于90. 提示就快结束了的一个老屁孩儿.
如果大于90以上.    提示再见了这个世界.

方法1:
```python
age = int(input('请输入您的年龄：'))
if age < 10:
    print('小屁孩儿.')
elif age > 10 and age < 20:
    print('青春期叛逆的小屁孩儿.')
elif age > 20 and age < 30:
    print('开始定性, 开始混社会的小屁孩儿.')
elif age > 30 and age < 40:
    print('看老大不小了, 赶紧结婚生屁孩儿.')
elif age > 40 and age < 50:
    print('家里有个不听话的小屁孩儿.')
elif age > 50 and age < 60:
    print('自己马上变成不听话的老屁孩儿.')
elif age > 60 and age < 70:
    print('活着还不错的老屁孩儿.')
elif age > 70 and age < 90:
    print('人生就快结束了的一个老屁孩儿.')
elif age > 90:
    print('再见了这个世界...')
```

方法2:
```python
age = int(input('请输入您的年龄：'))
if age < 10:
    print('小屁孩儿.')
elif 10 < age < 20:
    print('青春期叛逆的小屁孩儿.')
elif 20 < age < 30:
    print('开始定性, 开始混社会的小屁孩儿.')
elif 30 < age < 40:
    print('看老大不小了, 赶紧结婚生屁孩儿.')
elif 40 < age < 50:
    print('家里有个不听话的小屁孩儿.')
elif 50 < age < 60:
    print('自己马上变成不听话的老屁孩儿.')
elif 60 < age < 70:
        print('活着还不错的老屁孩儿.')
elif 70 < age < 90:
        print('人生就快结束了的一个老屁孩儿.')
elif age > 90:
    print('再见了这个世界...')
```

方法3:
```python
age = int(input('请输入您的年龄：'))
if age < 50:
    if 10 < age < 20:
        print('青春期叛逆的小屁孩儿.')
    elif 20 < age < 30:
        print('开始定性, 开始混社会的小屁孩儿.')
    elif 30 < age < 40:
        print('看老大不小了, 赶紧结婚小屁孩儿.')
    elif age < 50:
        print('家里有个不听话的小屁孩儿.')
    else:
        print('小屁孩儿.')
elif age > 50:
    if age < 60:
        print('自己马上变成不听话的老屁孩儿.')
    elif 60 < age < 70:
        print('活着还不错的老屁孩儿.')
    elif 70 < age < 90:
        print('人生就快结束了的一个老屁孩儿.')
    else:
        print('再见了这个世界...')
```

7、单行注释以及多行注释？
```
单行注释：每次只能注释一行
多行注释：可以注释多行，可以和变量来结合使用。
```


8、简述你所知道的Python3x和Python2x的区别？
```
Python2x：
    1.源码重复，冗长
    2.默认字符编码为ASCII, 默认不支持中文
    3.打印可以使用print '内容' 或者 print('内容')
    4.有长整型 long int
    5.有raw_input() 和 input('') 只能输入数字类型

Python3x：
    1.将源码规范化，简单化，清晰化
    2.默认字符编码为UTF-8, 默认支持中文
    3.打印只能使用print('内容')
    4.无长整型 long int
    5.只有input('')
```


9、提示用户输入麻花藤. 判断用户输入的对不对. 如果对, 提示真聪明, 如果不对, 提示你是傻x么？
```python
username = input('请输入用户名：')
if username == '麻花藤':
    print(username, '真聪明')
else:
    print(username, '你是傻x么？')
```


10、使用while循环输入 1 2 3 4 5 6 8 9 10
方法1:
```
count = 1
while count < 11:
    if count == 7:
        count += 1
    print(count)
    count += 1
```

方法2:
```python
count = 1
while count < 10:
    if count != 7:
        print(count)
    count += 1
```

11、求1-100的所有数的和
```python
sum = 0
count = 1
while count < 101:
    sum += count
    count += 1
print(sum)
```

12、输出 1-100 内的所有奇数
方法1:
```
count = 1
while count < 101:
   print(count)
   count += 2
```

方法2:
```python
count = 1
while count < 100:
    if count % 2 == 0:  # 对2取余为0时,加1则为奇数
        count += 1
    print(count)
    count += 1
```

方法3:
```python
count = 0
while count < 100:
    count += 1
    if count % 2 == 1:
        print(count)
```

13、输出 1-100 内的所有偶数

方法1:
```
count = 0
while count < 101:
    print(count)
    count = count + 2
```

方法2:
```python
count = 1
while count < 100:
    if count % 2 == 1:  # 对2取余为1时,加1则为偶数
        count += 1
    print(count)
    count += 1
```

方法3:
```python
count = 1
while count < 100:
    count += 1
    if count % 2 == 0:
        print(count)
```


14、求1-2+3-4+5 ... 99的所有数的和
```python
sum = 0
count = 1
while count < 100:
    if count % 2 == 0:
        sum -= count
    else:
        sum += count
    count += 1
print(sum)
```