---
title: "Alphabetic"
date: 2018-04-20T10:51:54+09:00
draft: false
---

```
>>>'a'.isalpha()
True
>>> '京'.isalpha()
True
```

昨天，碰到一个问题，为什么**京**会是 alpha 呢？回来仔细看了一下 rust 文档，上面清楚的写到是否为 alphabetic 是根据属于 Unicode Derived Core Property 'Alphabetic'部分来判断的。想来 Python 也是一样。(不是我不想查 Python 的文档，是查不到。)

[![asciicast](https://asciinema.org/a/wrSH1nwYmfSW7Ar1bxkN8o1Ha.png)](https://asciinema.org/a/wrSH1nwYmfSW7Ar1bxkN8o1Ha)

让我们来看看 DerivedCoreProperties Alphabetic 的定义

[DerivedCoreProperties](https://unicode.org/Public/UNIDATA/DerivedCoreProperties.txt)

其中有一行正好包括了我们的**京**的 `4eac`

```
4E00..9FEA    ; Alphabetic # Lo [20971] CJK UNIFIED IDEOGRAPH-4E00..CJK UNIFIED IDEOGRAPH-9FEA
```

哦，原来如此。

那么，问题来了 💝 是不是 Alphabatic 呢？

```python
'💝'.isalpha()
```
