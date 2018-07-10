

##### ディレクトリ内のpythonファイルを読み込む
import twolayernet

##### dictionary型
hoge = {'a':1, 'b':2}
hoge['c'] = 3
``` raw-token-data
>>> hoge
hoge
{'a': 1, 'b': 2, 'c': 3}
>>> hoge.keys()
hoge.keys()
dict_keys(['a', 'b', 'c'])
>>> hoge.values()
hoge.values()
dict_values([1, 2, 3])
```

# 配列
## append
```
>>> a.append(2)
>>> a.append(3)
>>> a
[2, 3]

```

# numpy

## random
### rand
- 0.0以上、1.0未満
```
>>> np.random.rand()
np.random.rand()
0.0410063888990444
```
### randint
- 任意の範囲の整数
```
>>> np.random.randint(300)
np.random.randint(300)
92
```
### randn
- 平均0、標準偏差1

```
>>> np.random.randn()
np.random.randn()
0.47897015271001475
```

### choice
```
>>> np.random.choice(4000, 4)
np.random.choice(4000, 4)
array([ 452,  672, 3871,  912])
```

