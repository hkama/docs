
# print

```python
>>> print('hoge', 3) # hoge 3
```

##### ディレクトリ内のpythonファイルを読み込む
import twolayernet

##### dictionary型
```python
>>> a = {'x':1, 'y':2}
>>> a['z'] = 3          # a = {'x': 1, 'y': 2, 'z': 3}
>>> a.keys()            # dict_keys(['x', 'y', 'z'])
>>> a.values()          # dict_values([1, 2, 3])
```

# 配列
## append
```
>>> a=[]
>>> a.append(2)
>>> a.append(3)  # a=[2, 3]
```



# numpy
## 基本
### ndim 次元
``` python
>>> np.arange(6).reshape(2,3).ndim # 2
```
### size 要素の総数
``` python
>>> np.arange(6).reshape(2,3).size # 6
```
### shape
``` python
>>> np.arange(6).reshape(2,3).shape # (2,3)
```
- reshapeは本体は変えないが、resizeは変える
``` python
>>> a=np.arange(6)
>>> a.reshape(2,3); a.shape # (6,)
>>> a.resize(2,3); a.shape  # (2, 3)
```

### dtype 型
```python
>>> np.arange(6).reshape(2,3).dtype # dtype('int64')
```
### itemsize バイトサイズ
```python
>>> np.arange(6).reshape(2,3).itemsize # 8 (=64/8)
```
### 生成時に型も指定可能
``` python
>>> c = np.array( [ [1,2], [3,4] ], dtype=complex)
array([[1.+0.j, 2.+0.j],
       [3.+0.j, 4.+0.j]])
```
### 等間隔
``` python
>>> np.arange( 10, 30, 5 )  # array([10, 15, 20, 25])
>>> np.arange( 0, 2, 0.3 )  # array([0. , 0.3, 0.6, 0.9, 1.2, 1.5, 1.8])
```
- floatを使う際には、浮動小数点の精度のために値を正確に制御することが難しいとのことで、linspaceが推奨されている
``` python
>>> np.linspace( 0, 2, 9 )  # array([0.  , 0.25, 0.5 , 0.75, 1.  , 1.25, 1.5 , 1.75, 2.  ])
```
### 表示
``` python
>>> np.arange(10000) # array([   0,    1,    2, ..., 9997, 9998, 9999])
```
- defaultだと上のように要素が多すぎると省略されるが、それも以下で設定可能
``` python
np.set_printoptions(threshold=np.nan)
```
### 転置

``` python
>>> a=np.arange(6).reshape(2,3)
>>> a.T
array([[0, 3],
       [1, 4],
       [2, 5]])
       
```

## 四則演算
### +-
```python
>>> a=np.array([5,5,5,5]);b=np.arange(4);a+b # array([5, 6, 7, 8])
>>> a=np.arange(4);a+5                       # array([5, 6, 7, 8])
```
### 2乗
``` python
>>> a=np.arange(4);a**2 # array([0, 1, 4, 9])
```
### 判定
``` python
>>> a=np.arange(4);a<2 # array([ True,  True, False, False])
```
### 配列同士*
``` python
>>> a=np.array([[1,2],[3,4]]);b=np.array([[1,2],[3,4]]);a*b
array([[ 1,  4],
       [ 9, 16]])
```
### dot

``` python
>>> a=np.array([[1,2],[3,4]]);b=np.array([[1,2],[3,4]]);np.dot(a,b)
array([[ 7, 10],
       [15, 22]])
```
### sum, min, max
``` python
>>> a=np.arange(4);a.sum() # 6
>>> a=np.arange(4).reshape(2,2);a.sum(axis=1) # array([1, 5])
```
### universal functions: ufunc (exp, sqrt, sin, cos, ...)
``` python
>>> a=np.arange(4); np.exp(a) # array([ 1.        ,  2.71828183,  7.3890561 , 20.08553692])
```
### 四捨五入・切り捨て・切り上げ
``` python
>>> x=10*np.random.rand(5) #           array([5.114784  , 6.53877715, 1.59877045, 7.76199671, 3.55392461])
>>> np.round(x) # 四捨五入             array([5., 7., 2., 8., 4.])
>>> np.trunc(x) # 切り捨て             array([5., 6., 1., 7., 3.])
>>> np.floor(x) # 切り捨て             array([5., 6., 1., 7., 3.])
>>> np.ceil(x) # 切り上げ              array([6., 7., 2., 8., 4.])
>>> np.fix(x) # 零に近い方で整数をとる array([5., 6., 1., 7., 3.])
```


## slicing
``` python
>>> a[8:2:-1] # array([8, 7, 6, 5, 4, 3])
>>> a[::-1]   # array([9, 8, 7, 6, 5, 4, 3, 2, 1, 0])
>>> a[::3]    # array([0, 3, 6, 9])
>>> a[1:3:1]  # array([1, 2])
>>> a=np.arange(12).reshape(3,4);a[:, 1:3]
array([[ 1,  2],
       [ 5,  6],
       [ 9, 10]])
```


## 変換
### ベクトル(1次元配列)を行列(2次元配列)に変換
``` python
>>> a = np.array([1, 2, 3]); np.reshape(a, (1, a.shape[0])) # array([[1, 2, 3]])
```

## 結合
### concatenate
- 2個以上の配列を軸指定して結合
``` python
>>> a1 = np.array([[1, 2, 3], [4, 5, 6]])
>>> a2 = np.array([[7, 8, 9], [0, 11, 12]])
>>> np.concatenate([a1, a2], axis=0)
array([[ 1,  2,  3],
       [ 4,  5,  6],
       [ 7,  8,  9],
       [ 0, 11, 12]])
>>> np.concatenate([a1, a2], axis=1)
np.concatenate([a1, a2], axis=1)
array([[ 1,  2,  3,  7,  8,  9],
       [ 4,  5,  6,  0, 11, 12]])
```
### vstack等(軸専用)
- vstackは1軸目、hstackは2軸目、concatenateは任意の軸に対してstackする
    - In general, for arrays of with more than two dimensions, hstack stacks along their second axes, vstack stacks along their first axes, and concatenate allows for an optional arguments giving the number of the axis along which the concatenation should happen.
    - [numpy quickstart](https://docs.scipy.org/doc/numpy/user/quickstart.html)
- 縦方向の結合：vstack()、row_stack()
- 横方向の結合：hstack()、column_stack()
- 深さ方向(axis=2)の結合：dstack()
- row_stackとvstackは挙動が完全に同一
- column_stackとhstackは微妙に挙動が違う
    - 2D arraysの時のみ同じ挙動を示す
``` python
>>> a = np.array([4.,2.])
>>> b = np.array([3.,8.])
>>> np.column_stack((a,b)) 
array([[4., 3.],
       [2., 8.]])
>>> np.hstack((a,b))
array([4., 2., 3., 8.])
```


### r_, c_
```python
>>> a1 = np.arange(6).reshape(2, 3); a2 = np.arange(100, 700, 100).reshape(2, 3)
>>> np.r_[a1, a2]
array([[  0,   1,   2],
       [  3,   4,   5],
       [100, 200, 300],
       [400, 500, 600]])
>>> np.c_[a1, a2]
array([[  0,   1,   2, 100, 200, 300],
       [  3,   4,   5, 400, 500, 600]])
```
- スライスを使って配列を作ることも出来る
``` python
>>> np.r_[:4, 10, 10, 4:0:-1] # array([ 0,  1,  2,  3, 10, 10,  4,  3,  2,  1])
```
``` python
>>> np.c_[:4, [10]*4, 4:0:-1]
array([[ 0, 10,  4],
       [ 1, 10,  3],
       [ 2, 10,  2],
       [ 3, 10,  1]])
```

## 分割
### split
``` python
>>> a = np.arange(12).reshape(6, 2)
>>> np.split(a, [1, 3])
[array([[0, 1]]),
 array([[2, 3],
        [4, 5]]),
 array([[6, 7],
        [8, 9],
        [10,11]])]
```
- 個別に受け取ることも出来る
```
>>> a = np.arange(12).reshape(6, 2)
>>> a1, a2, a3 = np.split(a, [1, 3]) 
```
### hsplit
- 水平ラインでぶった切る
``` python
>>> a = np.floor(10*np.random.random((2,12)))
array([[7., 9., 9., 4., 6., 4., 7., 1., 7., 7., 4., 7.],
       [1., 4., 2., 6., 3., 0., 8., 1., 9., 6., 0., 1.]])
>>> np.hsplit(a,3) # Split a into 3
np.hsplit(a,3)
[array([[7., 9., 9., 4.],
       [1., 4., 2., 6.]]), array([[6., 4., 7., 1.],
       [3., 0., 8., 1.]]), array([[7., 7., 4., 7.],
       [9., 6., 0., 1.]])]
>>> np.hsplit(a,(3,4)) # Split a after the third and the fourth column
np.hsplit(a,(3,4))
[array([[7., 9., 9.],
       [1., 4., 2.]]), array([[4.],
       [6.]]), array([[6., 4., 7., 1., 7., 7., 4., 7.],
       [3., 0., 8., 1., 9., 6., 0., 1.]])]
```
### vsplit, array_split
- vsplitは垂直、array_splitは任意の軸方向で切る

## flat
### flat
- flatはiterator
- flattenとは違う
``` python
>>> for i in a.flat:
...     print (i)
0
1
2
3
4
5
>>>
```
a=np.arange(6).reshape(2,3)
from itertools import chain
list(chain.from_iterable(a))


### flatten リストをflatten
``` python
>>> a=np.arange(6).reshape(2,3).flatten() # array([0, 1, 2, 3, 4, 5])
```
- chain使うと早いらしい
```python
>>> from itertools import chain
>>> list(chain.from_iterable(a))
[0, 1, 2, 3, 4, 5]
>>> 
```
- flattenにも色んな方法がある
``` python
>>> a=np.arange(6).reshape(2,3).ravel() # array([0, 1, 2, 3, 4, 5])
```

## random
### rand
- 0.0以上、1.0未満
```
>>> np.random.rand()  # 0.0410063888990444
```
### randint
- 任意の範囲の整数
```
>>> np.random.randint(300) # 92
```
### randn
- 平均0、標準偏差1
```
>>> np.random.randn()  # 0.47897015271001475
```

### choice
```
>>> np.random.choice(4000, 4)  # array([ 452,  672, 3871,  912])
```

## Copies and Views
### no copy at all
``` python
>>> a = np.arange(12)
>>> b = a            # no new object is created
>>> b is a           # a and b are two names for the same ndarray object
True
>>> b.shape = 3,4    # changes the shape of a
>>> a.shape
(3, 4)
```
- Python passes mutable objects as references, so function calls make no copy
``` python
>>> def f(x):
...     print(id(x))
...
>>> id(a)                           # id is a unique identifier of an object
148293216
>>> f(a)
148293216
```


