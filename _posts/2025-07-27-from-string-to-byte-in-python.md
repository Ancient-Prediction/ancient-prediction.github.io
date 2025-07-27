---
title: From String to Byte in Python
date: 2025-07-28 00:57:00 +0800
categories: [Fundamental, Python Basics]
tags: [initial version]
description: The relationship among String, Byte and Encoding in Python.
---

![](/assets/img/from-string-to-byte-in-python-1.png)

In fact, `'H'.encode('utf-8')` will produce `b'H'`, not `b'\x48'`, because H is a ASCII character, which will be displayed as is, but this is about notation or representation, and, at its very nature, it’s an integer when it’s converted to byte sequence, or multiple integers when using different encodings other than UTF-8 like UTF-16LE. 

![](/assets/img/from-string-to-byte-in-python-2.png)

## Reference

* Fluent Python by Luciano Ramalho
* Wikipedia
