
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
- 縦方向の結合：vstack()、row_stack()
- 横方向の結合：hstack()、column_stack()
- 深さ方向(axis=2)の結合：dstack()
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

