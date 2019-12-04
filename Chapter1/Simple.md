# 第2节：极简应用

## 

## 1.1.1 世界你好

```python
print(‘hello world’)
```

## 1.1.2 界面升级版

```python
python -c "from Tkinter import *;root = Tk();w = Label(root, text='Hello！World！'); w.pack(); root.mainloop()”
```

##  1.1.3 网络：python -m

```python
python **-**m SimpleHTTPServer 8000
```

## 1.1.4 算法：快速排序

```python
qs = lambda xs : ( (len(xs) <= 1 and [xs]) or [ qs( [x for x in xs[1:] if x < xs[0]] ) + [xs[0]] + qs( [x for x in xs[1:] if x >= xs[0]] ) ] )[0]
```

## 1.1.5 娱乐：看漫画

```python
import antigravity 
```

## 1.1.6 回忆：一行代码打印九九乘法

```python
print('\n'.join([' '.join(['%s*%s=%-2s' % (y, x, x*y) for y in range(1, x+1)]) for x in range(1, 10)]))
```

## 1.1.7 简易计算器

```python
print(eval(input()))
```





