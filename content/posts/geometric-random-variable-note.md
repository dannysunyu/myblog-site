+++
title = '几何随机变量的定义分歧'
date = 2025-11-03T21:50:59-07:00
draft = false
+++

发现在一些主流教材中，几何型随机变量(Geometric Random Variable)的定义有细微的分歧。主流教材中给的定义是，重复多次的抛硬币试验
(单次试验是Bernoulli experiment)，

>_Number of flips (failures) until the first heads (success)_

但有有些教材会定义为：

>_Number of flips (failures) before the first heads (success)_

虽然中外主流教材都是采用第一种定义，但是遗憾的是**R**和**Python**中的概率计算库使用的是第二种定义。

比如为要计算X ~ Geo(0.5)，X = 1的概率，需要传入0：

```R
dgeom(0, 0.5)
```

这种定义的不一致带来毫无必要的麻烦。