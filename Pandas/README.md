

```python
# create series
```


```python
import numpy as np, pandas as pd
```


```python
# method one: pandas.Series(arr)
arr1 = np.arange(10)
print(arr1)
print(type(arr1))
```

    [0 1 2 3 4 5 6 7 8 9]
    <class 'numpy.ndarray'>
    


```python
s1 = pd.Series(arr1)
print(s1)
print(type(s1))
```

    0    0
    1    1
    2    2
    3    3
    4    4
    5    5
    6    6
    7    7
    8    8
    9    9
    dtype: int32
    <class 'pandas.core.series.Series'>
    


```python
# dictionary
dic1 = {'a':10,'b':20,'c':30,'d':40,'e':50}
print(dic1)
print(type(dic1))
```

    {'a': 10, 'b': 20, 'c': 30, 'd': 40, 'e': 50}
    <class 'dict'>
    


```python
# DataFrame (actually it can also be used in excel?)
arr2 = np.array(np.arange(12)).reshape(4,3)
print(arr2)
print(type(arr2))
```

    [[ 0  1  2]
     [ 3  4  5]
     [ 6  7  8]
     [ 9 10 11]]
    <class 'numpy.ndarray'>
    


```python
df1 = pd.DataFrame(arr2)
print(df1)
print(type(df1))
```

       0   1   2
    0  0   1   2
    1  3   4   5
    2  6   7   8
    3  9  10  11
    <class 'pandas.core.frame.DataFrame'>
    


```python
# created by dictionary
dic2 = {'a':[1,2,3,4],'b':[5,6,7,8],'c':[9,10,11,12],'d':[13,14,15,16]}
print(dic2)
print(type(dic2))
```

    {'a': [1, 2, 3, 4], 'b': [5, 6, 7, 8], 'c': [9, 10, 11, 12], 'd': [13, 14, 15, 16]}
    <class 'dict'>
    


```python
df2 = pd.DataFrame(dic2)
print(df2)
print(type(df2))
```

       a  b   c   d
    0  1  5   9  13
    1  2  6  10  14
    2  3  7  11  15
    3  4  8  12  16
    <class 'pandas.core.frame.DataFrame'>
    


```python
# 就是穿件了每个列行所代表的意思，可以操作excel了
dic3 = {'one':{'a':1,'b':2,'c':3,'d':4},
        'two':{'a':5,'b':6,'c':7,'d':8},
        'three':{'a':9,'b':10,'c':11,'d':12}}
print(dic3)
print(type(dic3))

# dic3 = {'one':{'a':1,'b':2,'c':3,'d':4},
#         'two':{'a':5,'b':6,'c':7,'d':8},
#         'three':{'a':9,'b':10,'c':11,'d':12}}
# print(dic3)
# print(type(dic3))
```

    {'one': {'a': 1, 'b': 2, 'c': 3, 'd': 4}, 'two': {'a': 5, 'b': 6, 'c': 7, 'd': 8}, 'three': {'a': 9, 'b': 10, 'c': 11, 'd': 12}}
    <class 'dict'>
    


```python
df3 = pd.DataFrame(dic3)
print(df3)
print(type(df3))
```

       one  two  three
    a    1    5      9
    b    2    6     10
    c    3    7     11
    d    4    8     12
    <class 'pandas.core.frame.DataFrame'>
    


```python
# craete frame by dataframe's method
df4 = df3[['one','two','three']] # there are not others such as four , five , six , ...
print(df4)
```

       one  two  three
    a    1    5      9
    b    2    6     10
    c    3    7     11
    d    4    8     12
    


```python
s3 = df3['one']
print(s3)
print(type(s3))
```

    a    1
    b    2
    c    3
    d    4
    Name: one, dtype: int64
    <class 'pandas.core.series.Series'>
    


```python
# index's convenent ways
s4 = pd.Series(np.array([1,1,2,3,5,8]))
print(s4)
```

    0    1
    1    1
    2    2
    3    3
    4    5
    5    8
    dtype: int32
    


```python
print(s4.index)
s4.index = ['a','b','c','d','e','f']
print(s4)
print(s4[3]) # 自动建立的索引
print(s4['e']) # 自定义建立的索引
print(s4[[1,3,5]]) # 打印索引以及
# 也可以进行切片操作等
```

    RangeIndex(start=0, stop=6, step=1)
    a    1
    b    1
    c    2
    d    3
    e    5
    f    8
    dtype: int32
    3
    5
    b    1
    d    3
    f    8
    dtype: int32
    


```python
# 自动化对齐
s5 = pd.Series(np.array([10,15,20,30,55,80]),index = ['a','b','c','d','e','f'])
print(s5)
s6 = pd.Series(np.array([12,11,13,15,14,16]),index = ['a','c','g','b','d','f'])
print(s6)
print("按照索引计算结果")
print(s5 + s6)
print(s5/s6)
```

    a    10
    b    15
    c    20
    d    30
    e    55
    f    80
    dtype: int32
    a    12
    c    11
    g    13
    b    15
    d    14
    f    16
    dtype: int32
    按照索引计算结果
    a    22.0
    b    30.0
    c    31.0
    d    44.0
    e     NaN
    f    96.0
    g     NaN
    dtype: float64
    a    0.833333
    b    1.000000
    c    1.818182
    d    2.142857
    e         NaN
    f    5.000000
    g         NaN
    dtype: float64
    


```python
stu_dic = {'Age':[14,13,13,14,14,12,12,15,13,12,11,14,12,15,16,12,15,11,15],
'Height':[69,56.5,65.3,62.8,63.5,57.3,59.8,62.5,62.5,59,51.3,64.3,56.3,66.5,72,64.8,67,57.5,66.5],
'Name':['Alfred','Alice','Barbara','Carol','Henry','James','Jane','Janet','Jeffrey','John','Joyce','Judy','Louise','Marry','Philip','Robert','Ronald','Thomas','Willam'],
'Sex':['M','F','F','F','M','M','F','F','M','M','F','F','F','F','M','M','M','M','M'],
'Weight':[112.5,84,98,102.5,102.5,83,84.5,112.5,84,99.5,50.5,90,77,112,150,128,133,85,112]}
student = pd.DataFrame(stu_dic)
print("前五行")
print(student.head())
print("后五行")
print(student.tail())
```

    前五行
       Age  Height     Name Sex  Weight
    0   14    69.0   Alfred   M   112.5
    1   13    56.5    Alice   F    84.0
    2   13    65.3  Barbara   F    98.0
    3   14    62.8    Carol   F   102.5
    4   14    63.5    Henry   M   102.5
    后五行
        Age  Height    Name Sex  Weight
    14   16    72.0  Philip   M   150.0
    15   12    64.8  Robert   M   128.0
    16   15    67.0  Ronald   M   133.0
    17   11    57.5  Thomas   M    85.0
    18   15    66.5  Willam   M   112.0
    


```python
# 根据索引查询指定行数据，单行
print(student.loc[2]) # 注意区别
# loc[[]]多行
print(student.loc[[2,4,5]])
# 根据索引查询指定列数据
print(student["Name"].head()) # 注意区别！
print(student[["Name","Sex"]].head())
```

    Age            13
    Height       65.3
    Name      Barbara
    Sex             F
    Weight         98
    Name: 2, dtype: object
       Age  Height     Name Sex  Weight
    2   13    65.3  Barbara   F    98.0
    4   14    63.5    Henry   M   102.5
    5   12    57.3    James   M    83.0
    0     Alfred
    1      Alice
    2    Barbara
    3      Carol
    4      Henry
    Name: Name, dtype: object
          Name Sex
    0   Alfred   M
    1    Alice   F
    2  Barbara   F
    3    Carol   F
    4    Henry   M
    


```python
# 也可使用查询列 loc[row_index,[col_name]]
print(student.loc[:,["Name"]].head())
```

          Name
    0   Alfred
    1    Alice
    2  Barbara
    3    Carol
    4    Henry
    


```python
# 复合条件查询
print(student[(student['Sex']=='F')&(student['Age']>12)])
print(student[(student['Sex']=='F')&(student['Age']>12)][['Name','Height','Weight']])
```

        Age  Height     Name Sex  Weight
    1    13    56.5    Alice   F    84.0
    2    13    65.3  Barbara   F    98.0
    3    14    62.8    Carol   F   102.5
    7    15    62.5    Janet   F   112.5
    11   14    64.3     Judy   F    90.0
    13   15    66.5    Marry   F   112.0
           Name  Height  Weight
    1     Alice    56.5    84.0
    2   Barbara    65.3    98.0
    3     Carol    62.8   102.5
    7     Janet    62.5   112.5
    11     Judy    64.3    90.0
    13    Marry    66.5   112.0
    


```python
# 统计分析函数模板
def stats(x):
	return pd.Series([x.count(),x.min(),x.idxmin(),x.quantile(.25),x.median(),x.quantile(.75),
                      x.mean(),x.max(),x.idxmax(),x.mad(),x.var(),x.std(),x.skew(),x.kurt()],
                     index = ['Count','Min','Whicn_Min','Q1','Median','Q3','Mean','Max',
                              'Which_Max','Mad','Var','Std','Skew','Kurt'])
```


```python
np.random.seed(1234)
d = pd.Series(2*np.random.normal(size = 120)+3)
print(stats(d)) # 自定义描述指标
print(d.describe()) # 输出多个统计指标 只针对序列或者数据框，一维数组不能如此操作
print(d)
```

    Count        120.000000
    Min           -4.127033
    Whicn_Min     81.000000
    Q1             2.063321
    Median         3.277344
    Q3             4.408703
    Mean           3.068018
    Max            7.781921
    Which_Max     39.000000
    Mad            1.496662
    Var            3.844983
    Std            1.960863
    Skew          -0.651704
    Kurt           1.070332
    dtype: float64
    count    120.000000
    mean       3.068018
    std        1.960863
    min       -4.127033
    25%        2.063321
    50%        3.277344
    75%        4.408703
    max        7.781921
    dtype: float64
    0      3.942870
    1      0.618049
    2      5.865414
    3      2.374696
    4      1.558823
             ...   
    115    2.635649
    116    4.361312
    117   -0.636998
    118    3.094143
    119    3.789688
    Length: 120, dtype: float64
    


```python
# 当同时处理多行数据时
d1 = np.random.f(2,4,size=120) # 从2~4的浮点数
d2 = np.random.randint(1,100,size=120) # 从1~100的随机整数
```


```python
# 构建二维数据框
df = pd.DataFrame(np.array([d,d1,d2]).T,columns=['x1','x2','x3'])
print(df.head())
```

             x1         x2    x3
    0  3.942870   0.046797  50.0
    1  0.618049   2.112932  32.0
    2  5.865414  13.275777  44.0
    3  2.374696   1.010520  25.0
    4  1.558823   1.429254  84.0
    


```python

```
```python
stu_dic = {'Age':[14,13,13,14,14,12,12,15,13,12,11,14,12,15,16,12,15,11,15],
'Height':[69,56.5,65.3,62.8,63.5,57.3,59.8,62.5,62.5,59,51.3,64.3,56.3,66.5,72,64.8,67,57.5,66.5],
'Name':['Alfred','Alice','Barbara','Carol','Henry','James','Jane','Janet','Jeffrey','John','Joyce','Judy','Louise','Marry','Philip','Robert','Ronald','Thomas','Willam'],
'Sex':['M','F','F','F','M','M','F','F','M','M','F','F','F','F','M','M','M','M','M'],
'Weight':[112.5,84,98,102.5,102.5,83,84.5,112.5,84,99.5,50.5,90,77,112,150,128,133,85,112]}
student = pd.DataFrame(stu_dic)
print(student)
```

        Age  Height     Name Sex  Weight
    0    14    69.0   Alfred   M   112.5
    1    13    56.5    Alice   F    84.0
    2    13    65.3  Barbara   F    98.0
    3    14    62.8    Carol   F   102.5
    4    14    63.5    Henry   M   102.5
    5    12    57.3    James   M    83.0
    6    12    59.8     Jane   F    84.5
    7    15    62.5    Janet   F   112.5
    8    13    62.5  Jeffrey   M    84.0
    9    12    59.0     John   M    99.5
    10   11    51.3    Joyce   F    50.5
    11   14    64.3     Judy   F    90.0
    12   12    56.3   Louise   F    77.0
    13   15    66.5    Marry   F   112.0
    14   16    72.0   Philip   M   150.0
    15   12    64.8   Robert   M   128.0
    16   15    67.0   Ronald   M   133.0
    17   11    57.5   Thomas   M    85.0
    18   15    66.5   Willam   M   112.0
    


```python
# 实现SQL操作
dic = {'Name':['cuiqin','liumengjie'],'Sex':['M','F'],'Age':[19,7],'Height':[175,162],'Weight':[61,45]}
cp = pd.DataFrame(dic)
print(cp)
```

             Name Sex  Age  Height  Weight
    0      cuiqin   M   19     175      61
    1  liumengjie   F    7     162      45
    


```python
# 数据框连接:新增行数据
students = pd.concat([student,cp])
print(students)
```

        Age  Height        Name Sex  Weight
    0    14    69.0      Alfred   M   112.5
    1    13    56.5       Alice   F    84.0
    2    13    65.3     Barbara   F    98.0
    3    14    62.8       Carol   F   102.5
    4    14    63.5       Henry   M   102.5
    5    12    57.3       James   M    83.0
    6    12    59.8        Jane   F    84.5
    7    15    62.5       Janet   F   112.5
    8    13    62.5     Jeffrey   M    84.0
    9    12    59.0        John   M    99.5
    10   11    51.3       Joyce   F    50.5
    11   14    64.3        Judy   F    90.0
    12   12    56.3      Louise   F    77.0
    13   15    66.5       Marry   F   112.0
    14   16    72.0      Philip   M   150.0
    15   12    64.8      Robert   M   128.0
    16   15    67.0      Ronald   M   133.0
    17   11    57.5      Thomas   M    85.0
    18   15    66.5      Willam   M   112.0
    0    19   175.0      cuiqin   M    61.0
    1     7   162.0  liumengjie   F    45.0
    

    C:\ProgramData\Anaconda3\lib\site-packages\ipykernel_launcher.py:2: FutureWarning: Sorting because non-concatenation axis is not aligned. A future version
    of pandas will change to not sort by default.
    
    To accept the future behavior, pass 'sort=False'.
    
    To retain the current behavior and silence the warning, pass 'sort=True'.
    
      
    


```python
# 新增列数据
print(pd.DataFrame(students,columns=['Age','Height','Name','Sex','Weight','Score'])) # 直接在开头引入名称即可
```

        Age  Height        Name Sex  Weight  Score
    0    14    69.0      Alfred   M   112.5    NaN
    1    13    56.5       Alice   F    84.0    NaN
    2    13    65.3     Barbara   F    98.0    NaN
    3    14    62.8       Carol   F   102.5    NaN
    4    14    63.5       Henry   M   102.5    NaN
    5    12    57.3       James   M    83.0    NaN
    6    12    59.8        Jane   F    84.5    NaN
    7    15    62.5       Janet   F   112.5    NaN
    8    13    62.5     Jeffrey   M    84.0    NaN
    9    12    59.0        John   M    99.5    NaN
    10   11    51.3       Joyce   F    50.5    NaN
    11   14    64.3        Judy   F    90.0    NaN
    12   12    56.3      Louise   F    77.0    NaN
    13   15    66.5       Marry   F   112.0    NaN
    14   16    72.0      Philip   M   150.0    NaN
    15   12    64.8      Robert   M   128.0    NaN
    16   15    67.0      Ronald   M   133.0    NaN
    17   11    57.5      Thomas   M    85.0    NaN
    18   15    66.5      Willam   M   112.0    NaN
    0    19   175.0      cuiqin   M    61.0    NaN
    1     7   162.0  liumengjie   F    45.0    NaN
    


```python
# 删除
del students
print(students)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-44-0e2444bdcd7c> in <module>
          1 # 删除
          2 del students
    ----> 3 print(students)
    

    NameError: name 'students' is not defined



```python
# 删除指定的行
print(student)
```

        Age  Height     Name Sex  Weight
    0    14    69.0   Alfred   M   112.5
    1    13    56.5    Alice   F    84.0
    2    13    65.3  Barbara   F    98.0
    3    14    62.8    Carol   F   102.5
    4    14    63.5    Henry   M   102.5
    5    12    57.3    James   M    83.0
    6    12    59.8     Jane   F    84.5
    7    15    62.5    Janet   F   112.5
    8    13    62.5  Jeffrey   M    84.0
    9    12    59.0     John   M    99.5
    10   11    51.3    Joyce   F    50.5
    11   14    64.3     Judy   F    90.0
    12   12    56.3   Louise   F    77.0
    13   15    66.5    Marry   F   112.0
    14   16    72.0   Philip   M   150.0
    15   12    64.8   Robert   M   128.0
    16   15    67.0   Ronald   M   133.0
    17   11    57.5   Thomas   M    85.0
    18   15    66.5   Willam   M   112.0
    


```python
# student = student.drop([4,18])
print(student.drop([1,2,3,4,5,6]))
```

        Age  Height     Name Sex  Weight
    0    14    69.0   Alfred   M   112.5
    7    15    62.5    Janet   F   112.5
    8    13    62.5  Jeffrey   M    84.0
    9    12    59.0     John   M    99.5
    10   11    51.3    Joyce   F    50.5
    11   14    64.3     Judy   F    90.0
    12   12    56.3   Louise   F    77.0
    13   15    66.5    Marry   F   112.0
    14   16    72.0   Philip   M   150.0
    15   12    64.8   Robert   M   128.0
    16   15    67.0   Ronald   M   133.0
    17   11    57.5   Thomas   M    85.0
    18   15    66.5   Willam   M   112.0
    


```python
# 选择删除
## 条件删除
print(student[student['Age']>14])
```

        Age  Height    Name Sex  Weight
    7    15    62.5   Janet   F   112.5
    13   15    66.5   Marry   F   112.0
    14   16    72.0  Philip   M   150.0
    16   15    67.0  Ronald   M   133.0
    18   15    66.5  Willam   M   112.0
    


```python
# 删除指定的行
print(student.drop(['Height','Weight'],axis=1).head()) # 调整axis参数值，注意默认是0，就是默认是序列号
```

       Age     Name Sex
    0   14   Alfred   M
    1   13    Alice   F
    2   13  Barbara   F
    3   14    Carol   F
    4   14    Henry   M
    


```python
# 修改默认的值
print(cp)
```

             Name Sex  Age  Height  Weight
    0      cuiqin   M   19     175      61
    1  liumengjie   F    7     162      45
    


```python
cp.loc[cp['Name'] == 'liumengjie','Age']=19
print(cp[cp['Name'] == 'liumengjie'][['Name','Sex','Age']])
```

             Name Sex  Age
    1  liumengjie   F   19
    


```python
# 聚合排序
print(student.groupby('Sex').mean()) # 求关于sex列的数据的对应的数据的身高和体重的平均值
```

               Age     Height      Weight
    Sex                                  
    F    13.222222  60.588889   90.111111
    M    13.400000  63.910000  108.950000
    


```python
# 分组+多个统计量
print(student.drop('Age',axis=1).groupby('Sex').agg([np.mean,np.median]))
```

            Height             Weight        
              mean median        mean  median
    Sex                                      
    F    60.588889  62.50   90.111111   90.00
    M    63.910000  64.15  108.950000  107.25
    


```python
# sort tools
Data = pd.Series(np.array(np.random.randint(1,20,10)))
print(Data)
```

    0     8
    1     5
    2    16
    3     9
    4     6
    5     1
    6    15
    7    15
    8    16
    9     1
    dtype: int32
    


```python
print(Data.sort_index()) # index sort
```

    0     8
    1     5
    2    16
    3     9
    4     6
    5     1
    6    15
    7    15
    8    16
    9     1
    dtype: int32
    


```python
print(Data.sort_values(ascending=False)) # values sort
```

    8    16
    2    16
    7    15
    6    15
    3     9
    0     8
    4     6
    1     5
    9     1
    5     1
    dtype: int32
    


```python
print(student)
```

        Age  Height     Name Sex  Weight
    0    14    69.0   Alfred   M   112.5
    1    13    56.5    Alice   F    84.0
    2    13    65.3  Barbara   F    98.0
    3    14    62.8    Carol   F   102.5
    4    14    63.5    Henry   M   102.5
    5    12    57.3    James   M    83.0
    6    12    59.8     Jane   F    84.5
    7    15    62.5    Janet   F   112.5
    8    13    62.5  Jeffrey   M    84.0
    9    12    59.0     John   M    99.5
    10   11    51.3    Joyce   F    50.5
    11   14    64.3     Judy   F    90.0
    12   12    56.3   Louise   F    77.0
    13   15    66.5    Marry   F   112.0
    14   16    72.0   Philip   M   150.0
    15   12    64.8   Robert   M   128.0
    16   15    67.0   Ronald   M   133.0
    17   11    57.5   Thomas   M    85.0
    18   15    66.5   Willam   M   112.0
    


```python
# sort by values
print(student.sort_values(by = ['Age','Height'])) # 先对age排序，再在排好序的age中排序height
```

        Age  Height     Name Sex  Weight
    10   11    51.3    Joyce   F    50.5
    17   11    57.5   Thomas   M    85.0
    12   12    56.3   Louise   F    77.0
    5    12    57.3    James   M    83.0
    9    12    59.0     John   M    99.5
    6    12    59.8     Jane   F    84.5
    15   12    64.8   Robert   M   128.0
    1    13    56.5    Alice   F    84.0
    8    13    62.5  Jeffrey   M    84.0
    2    13    65.3  Barbara   F    98.0
    3    14    62.8    Carol   F   102.5
    4    14    63.5    Henry   M   102.5
    11   14    64.3     Judy   F    90.0
    0    14    69.0   Alfred   M   112.5
    7    15    62.5    Janet   F   112.5
    13   15    66.5    Marry   F   112.0
    18   15    66.5   Willam   M   112.0
    16   15    67.0   Ronald   M   133.0
    14   16    72.0   Philip   M   150.0
    


```python
# 数据库连接中的内连接和外连接
dic2 = {'Name':['Alfred','Alice','Barbara','Carol','Henry','Jeffrey','Judy','Philip','Robert','Willam'],
        'Score':[88,76,89,67,79,90,92,86,73,77]}
score = pd.DataFrame(dic2)
print(score)
```

          Name  Score
    0   Alfred     88
    1    Alice     76
    2  Barbara     89
    3    Carol     67
    4    Henry     79
    5  Jeffrey     90
    6     Judy     92
    7   Philip     86
    8   Robert     73
    9   Willam     77
    


```python
# 两个表关联
stu_score1 = pd.merge(student,score, on='Name') # only on view in successfully connecting
print(stu_score1)
```

       Age  Height     Name Sex  Weight  Score
    0   14    69.0   Alfred   M   112.5     88
    1   13    56.5    Alice   F    84.0     76
    2   13    65.3  Barbara   F    98.0     89
    3   14    62.8    Carol   F   102.5     67
    4   14    63.5    Henry   M   102.5     79
    5   13    62.5  Jeffrey   M    84.0     90
    6   14    64.3     Judy   F    90.0     92
    7   16    72.0   Philip   M   150.0     86
    8   12    64.8   Robert   M   128.0     73
    9   15    66.5   Willam   M   112.0     77
    


```python
 # default as 'left' and 能匹配多少就匹配多少，匹配不到的显示为NaN
# merge 实现的是两个表的内连接 merge(table1,table2,on=value_name,how=methods(['left','right','outer']))
stu_score2 = pd.merge(student,score, on='Name', how='left')
print(stu_score2)
```

        Age  Height     Name Sex  Weight  Score
    0    14    69.0   Alfred   M   112.5   88.0
    1    13    56.5    Alice   F    84.0   76.0
    2    13    65.3  Barbara   F    98.0   89.0
    3    14    62.8    Carol   F   102.5   67.0
    4    14    63.5    Henry   M   102.5   79.0
    5    12    57.3    James   M    83.0    NaN
    6    12    59.8     Jane   F    84.5    NaN
    7    15    62.5    Janet   F   112.5    NaN
    8    13    62.5  Jeffrey   M    84.0   90.0
    9    12    59.0     John   M    99.5    NaN
    10   11    51.3    Joyce   F    50.5    NaN
    11   14    64.3     Judy   F    90.0   92.0
    12   12    56.3   Louise   F    77.0    NaN
    13   15    66.5    Marry   F   112.0    NaN
    14   16    72.0   Philip   M   150.0   86.0
    15   12    64.8   Robert   M   128.0   73.0
    16   15    67.0   Ronald   M   133.0    NaN
    17   11    57.5   Thomas   M    85.0    NaN
    18   15    66.5   Willam   M   112.0   77.0
    


```python
# 填补数据 for tthree methods : 
```


```python
# 删除法
s = stu_score2['Score']
print(s)
```

    0     88.0
    1     76.0
    2     89.0
    3     67.0
    4     79.0
    5      NaN
    6      NaN
    7      NaN
    8     90.0
    9      NaN
    10     NaN
    11    92.0
    12     NaN
    13     NaN
    14    86.0
    15    73.0
    16     NaN
    17     NaN
    18    77.0
    Name: Score, dtype: float64
    


```python
# check how many values was lost
print(sum(pd.isnull(s)))
```

    9
    


```python
# and del them
print(s.dropna()) # dropna = drop null all
```

    0     88.0
    1     76.0
    2     89.0
    3     67.0
    4     79.0
    8     90.0
    11    92.0
    14    86.0
    15    73.0
    18    77.0
    Name: Score, dtype: float64
    


```python
df = pd.DataFrame([[1,1,2],[3,5,np.nan],[13,21,34],[55,np.nan,10],[np.nan,np.nan,np.nan],[np.nan,1,2]],columns=('x1','x2','x3'))
print(df)
print("after:")
print(df.dropna()) # 只要包含NaN，就删除对应行
```

         x1    x2    x3
    0   1.0   1.0   2.0
    1   3.0   5.0   NaN
    2  13.0  21.0  34.0
    3  55.0   NaN  10.0
    4   NaN   NaN   NaN
    5   NaN   1.0   2.0
    after:
         x1    x2    x3
    0   1.0   1.0   2.0
    2  13.0  21.0  34.0
    


```python
# 填补法
print(df.fillna(0))
```

         x1    x2    x3
    0   1.0   1.0   2.0
    1   3.0   5.0   0.0
    2  13.0  21.0  34.0
    3  55.0   0.0  10.0
    4   0.0   0.0   0.0
    5   0.0   1.0   2.0
    


```python
print("前项填充")
print(df.fillna(method='ffill'))
print("后项填充")
print(df.fillna(method='bfill'))
```

    前项填充
         x1    x2    x3
    0   1.0   1.0   2.0
    1   3.0   5.0   2.0
    2  13.0  21.0  34.0
    3  55.0  21.0  10.0
    4  55.0  21.0  10.0
    5  55.0   1.0   2.0
    后项填充
         x1    x2    x3
    0   1.0   1.0   2.0
    1   3.0   5.0  34.0
    2  13.0  21.0  34.0
    3  55.0   1.0  10.0
    4   NaN   1.0   2.0
    5   NaN   1.0   2.0
    


```python
print("使用常量填充不同的列")
print(df.fillna({'x1':1,'x2':2,'x3':3}))
```

    使用常量填充不同的列
         x1    x2    x3
    0   1.0   1.0   2.0
    1   3.0   5.0   3.0
    2  13.0  21.0  34.0
    3  55.0   2.0  10.0
    4   1.0   2.0   3.0
    5   1.0   1.0   2.0
    


```python
# 使用统计量填充更加合理：众数、均值、中位数
x1_median = df['x1'].median()
x2_mean = df['x2'].mean()
x3_mean = df['x3'].mean()

print("x1_median:",x1_median)
print("x2_mean:",x2_mean)
print("x3_mean:",x3_mean)
print(df.fillna({'x1':x1_median,'x2':x2_mean,'x3':x3_mean})) # x1 fill in median, x2 fill in mean, x3 fill in mean
```

    x1_median: 8.0
    x2_mean: 7.0
    x3_mean: 12.0
         x1    x2    x3
    0   1.0   1.0   2.0
    1   3.0   5.0  12.0
    2  13.0  21.0  34.0
    3  55.0   7.0  10.0
    4   8.0   7.0  12.0
    5   8.0   1.0   2.0
    


```python
# operate the excel table
# pivot_table(data,values=None,index=None,aggfunc='mean',fill_value=None,margins=False,dropna=True,margins_name='All')
print(student)
```

        Age  Height     Name Sex  Weight
    0    14    69.0   Alfred   M   112.5
    1    13    56.5    Alice   F    84.0
    2    13    65.3  Barbara   F    98.0
    3    14    62.8    Carol   F   102.5
    4    14    63.5    Henry   M   102.5
    5    12    57.3    James   M    83.0
    6    12    59.8     Jane   F    84.5
    7    15    62.5    Janet   F   112.5
    8    13    62.5  Jeffrey   M    84.0
    9    12    59.0     John   M    99.5
    10   11    51.3    Joyce   F    50.5
    11   14    64.3     Judy   F    90.0
    12   12    56.3   Louise   F    77.0
    13   15    66.5    Marry   F   112.0
    14   16    72.0   Philip   M   150.0
    15   12    64.8   Robert   M   128.0
    16   15    67.0   Ronald   M   133.0
    17   11    57.5   Thomas   M    85.0
    18   15    66.5   Willam   M   112.0
    


```python
Table = pd.pivot_table(student, values=['Height','Weight'],columns=['Sex','Age']).unstack()
print("means in different age, height and weight")
print(Table)
```

    means in different age, height and weight
    Age           11          12    13      14      15     16
           Sex                                               
    Height F    51.3   58.050000  60.9   63.55   64.50    NaN
           M    57.5   60.366667  62.5   66.25   66.75   72.0
    Weight F    50.5   80.750000  91.0   96.25  112.25    NaN
           M    85.0  103.500000  84.0  107.50  122.50  150.0
    


```python
Table_more = pd.pivot_table(student,values=['Height','Weight'],columns=['Sex'],aggfunc=[np.mean,np.median,np.std])
print(Table_more)
```

                 mean         median                std           
    Sex             F       M      F       M          F          M
    Height  60.588889   63.91   62.5   64.15   5.018328   4.937937
    Weight  90.111111  108.95   90.0  107.25  19.383914  22.727186
    


```python
# 高维数据转换成为低维数据，多层索引也可以转换成为数据框的形式
s = pd.Series(np.arange(1,10),index=[["a","a","a","b","b","c","c","d","d"],[1,2,3,1,2,3,1,2,3]])
print(s)
print(s.index)
```

    a  1    1
       2    2
       3    3
    b  1    4
       2    5
    c  3    6
       1    7
    d  2    8
       3    9
    dtype: int32
    MultiIndex([('a', 1),
                ('a', 2),
                ('a', 3),
                ('b', 1),
                ('b', 2),
                ('c', 3),
                ('c', 1),
                ('d', 2),
                ('d', 3)],
               )
    


```python
print(s['a'])
print(s['a',1])
print(s['a'][[1,2]])
```

    1    1
    2    2
    3    3
    dtype: int32
    1
    1    1
    2    2
    dtype: int32
    


```python
# 将Series 转化成数据框，残缺的数据用NaN填补
print(s.unstack())
```

         1    2    3
    a  1.0  2.0  3.0
    b  4.0  5.0  NaN
    c  7.0  NaN  6.0
    d  NaN  8.0  9.0
    


```python
# if you want to know more operation you can search for them
```


```python
# 层次化索引
data = pd.DataFrame(np.random.randint(0,150,size=(8,12)),
               columns = pd.MultiIndex.from_product([['模拟考','正式考'],
                                                   ['数学','语文','英语','物理','化学','生物']]),
               index = pd.MultiIndex.from_product([['期中','期末'],
                                                   ['崔秦','刘梦洁'],
                                                  ['测试一','测试二']]))
data
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th></th>
      <th></th>
      <th colspan="6" halign="left">模拟考</th>
      <th colspan="6" halign="left">正式考</th>
    </tr>
    <tr>
      <th></th>
      <th></th>
      <th></th>
      <th>数学</th>
      <th>语文</th>
      <th>英语</th>
      <th>物理</th>
      <th>化学</th>
      <th>生物</th>
      <th>数学</th>
      <th>语文</th>
      <th>英语</th>
      <th>物理</th>
      <th>化学</th>
      <th>生物</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="4" valign="top">期中</td>
      <td rowspan="2" valign="top">崔秦</td>
      <td>测试一</td>
      <td>37</td>
      <td>17</td>
      <td>85</td>
      <td>58</td>
      <td>20</td>
      <td>131</td>
      <td>51</td>
      <td>66</td>
      <td>32</td>
      <td>9</td>
      <td>72</td>
      <td>124</td>
    </tr>
    <tr>
      <td>测试二</td>
      <td>63</td>
      <td>62</td>
      <td>112</td>
      <td>86</td>
      <td>115</td>
      <td>31</td>
      <td>17</td>
      <td>35</td>
      <td>127</td>
      <td>44</td>
      <td>113</td>
      <td>102</td>
    </tr>
    <tr>
      <td rowspan="2" valign="top">刘梦洁</td>
      <td>测试一</td>
      <td>112</td>
      <td>15</td>
      <td>104</td>
      <td>134</td>
      <td>46</td>
      <td>132</td>
      <td>126</td>
      <td>99</td>
      <td>31</td>
      <td>100</td>
      <td>100</td>
      <td>44</td>
    </tr>
    <tr>
      <td>测试二</td>
      <td>28</td>
      <td>71</td>
      <td>141</td>
      <td>66</td>
      <td>1</td>
      <td>61</td>
      <td>99</td>
      <td>49</td>
      <td>45</td>
      <td>86</td>
      <td>38</td>
      <td>43</td>
    </tr>
    <tr>
      <td rowspan="4" valign="top">期末</td>
      <td rowspan="2" valign="top">崔秦</td>
      <td>测试一</td>
      <td>23</td>
      <td>103</td>
      <td>65</td>
      <td>118</td>
      <td>30</td>
      <td>20</td>
      <td>69</td>
      <td>3</td>
      <td>125</td>
      <td>100</td>
      <td>147</td>
      <td>110</td>
    </tr>
    <tr>
      <td>测试二</td>
      <td>54</td>
      <td>71</td>
      <td>76</td>
      <td>44</td>
      <td>4</td>
      <td>85</td>
      <td>6</td>
      <td>10</td>
      <td>103</td>
      <td>22</td>
      <td>59</td>
      <td>132</td>
    </tr>
    <tr>
      <td rowspan="2" valign="top">刘梦洁</td>
      <td>测试一</td>
      <td>85</td>
      <td>90</td>
      <td>23</td>
      <td>89</td>
      <td>134</td>
      <td>11</td>
      <td>110</td>
      <td>14</td>
      <td>18</td>
      <td>107</td>
      <td>69</td>
      <td>20</td>
    </tr>
    <tr>
      <td>测试二</td>
      <td>83</td>
      <td>7</td>
      <td>109</td>
      <td>65</td>
      <td>141</td>
      <td>119</td>
      <td>40</td>
      <td>83</td>
      <td>146</td>
      <td>131</td>
      <td>85</td>
      <td>75</td>
    </tr>
  </tbody>
</table>
</div>




```python
data['模拟考'][['语文','数学']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th></th>
      <th>语文</th>
      <th>数学</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="4" valign="top">期中</td>
      <td rowspan="2" valign="top">崔秦</td>
      <td>测试一</td>
      <td>17</td>
      <td>37</td>
    </tr>
    <tr>
      <td>测试二</td>
      <td>62</td>
      <td>63</td>
    </tr>
    <tr>
      <td rowspan="2" valign="top">刘梦洁</td>
      <td>测试一</td>
      <td>15</td>
      <td>112</td>
    </tr>
    <tr>
      <td>测试二</td>
      <td>71</td>
      <td>28</td>
    </tr>
    <tr>
      <td rowspan="4" valign="top">期末</td>
      <td rowspan="2" valign="top">崔秦</td>
      <td>测试一</td>
      <td>103</td>
      <td>23</td>
    </tr>
    <tr>
      <td>测试二</td>
      <td>71</td>
      <td>54</td>
    </tr>
    <tr>
      <td rowspan="2" valign="top">刘梦洁</td>
      <td>测试一</td>
      <td>90</td>
      <td>85</td>
    </tr>
    <tr>
      <td>测试二</td>
      <td>7</td>
      <td>83</td>
    </tr>
  </tbody>
</table>
</div>




```python
# method one
print(data.loc['期中','崔秦','测试一'])
```

    模拟考  数学     37
         语文     17
         英语     85
         物理     58
         化学     20
         生物    131
    正式考  数学     51
         语文     66
         英语     32
         物理      9
         化学     72
         生物    124
    Name: (期中, 崔秦, 测试一), dtype: int32
    


```python
# method two
print(data.iloc[0])
```

    模拟考  数学     37
         语文     17
         英语     85
         物理     58
         化学     20
         生物    131
    正式考  数学     51
         语文     66
         英语     32
         物理      9
         化学     72
         生物    124
    Name: (期中, 崔秦, 测试一), dtype: int32
    


```python
data['正式考']
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th></th>
      <th>数学</th>
      <th>语文</th>
      <th>英语</th>
      <th>物理</th>
      <th>化学</th>
      <th>生物</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="4" valign="top">期中</td>
      <td rowspan="2" valign="top">崔秦</td>
      <td>测试一</td>
      <td>51</td>
      <td>66</td>
      <td>32</td>
      <td>9</td>
      <td>72</td>
      <td>124</td>
    </tr>
    <tr>
      <td>测试二</td>
      <td>17</td>
      <td>35</td>
      <td>127</td>
      <td>44</td>
      <td>113</td>
      <td>102</td>
    </tr>
    <tr>
      <td rowspan="2" valign="top">刘梦洁</td>
      <td>测试一</td>
      <td>126</td>
      <td>99</td>
      <td>31</td>
      <td>100</td>
      <td>100</td>
      <td>44</td>
    </tr>
    <tr>
      <td>测试二</td>
      <td>99</td>
      <td>49</td>
      <td>45</td>
      <td>86</td>
      <td>38</td>
      <td>43</td>
    </tr>
    <tr>
      <td rowspan="4" valign="top">期末</td>
      <td rowspan="2" valign="top">崔秦</td>
      <td>测试一</td>
      <td>69</td>
      <td>3</td>
      <td>125</td>
      <td>100</td>
      <td>147</td>
      <td>110</td>
    </tr>
    <tr>
      <td>测试二</td>
      <td>6</td>
      <td>10</td>
      <td>103</td>
      <td>22</td>
      <td>59</td>
      <td>132</td>
    </tr>
    <tr>
      <td rowspan="2" valign="top">刘梦洁</td>
      <td>测试一</td>
      <td>110</td>
      <td>14</td>
      <td>18</td>
      <td>107</td>
      <td>69</td>
      <td>20</td>
    </tr>
    <tr>
      <td>测试二</td>
      <td>40</td>
      <td>83</td>
      <td>146</td>
      <td>131</td>
      <td>85</td>
      <td>75</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
