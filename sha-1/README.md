SHA：Secure Hash Algorithm，安全哈希算法



#### SHA-1加密规则

- 将输入数据切割为固定大小的块。
- 通过迭代压缩函数逐块处理。
- 将所有块的结果组合为一个固定长度的哈希值，20byte。



##### 1. 分组 & 填充

- 切分为固定大小的块，64byte。
- 末尾填充 `0x80`。
- 继续填充 `0x00`。
- 最后填充8byte的消息长度。



##### 2. 初始哈希值

将作为第一个块的输入。

```
H0 = 0x67452301
H1 = 0xEFCDAB89
H2 = 0x98BADCFE
H3 = 0x10325476
H4 = 0xC3D2E1F0
```



##### 3. 压缩函数

核心，基于或、与、非、异或、加法操作，每个64byte块经过8次迭代，每次使用不同非线性函数和常量，五个32bit的哈希值不断更新，得到最后的中间哈希值。



##### 4. 计算过程

- 将一个块（64byte）扩充到320字节。
- 



#### 参考

[http://csrc.nist.gov/fips/fip180-1.txt](http://csrc.nist.gov/fips/fip180-1.txt)

[https://github.com/apple/swift-nio/blob/main/Sources/CNIOSHA1/c_nio_sha1.c](https://github.com/apple/swift-nio/blob/main/Sources/CNIOSHA1/c_nio_sha1.c)