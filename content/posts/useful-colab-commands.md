+++
title = '有用的Google Colab命令'
date = 2025-09-06T16:52:09-06:00
draft = false
+++

#### 如何将Jupyter Notebook转成PDF

```shell
!sudo apt-get install texlive-xetex texlive-fonts-recommended texlive-plain-generic

!sudo apt-get install pandoc

! jupyter nbconvert --to pdf <path to jupyter notebook>.ipynb
```
