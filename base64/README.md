### Base64编码规则

将二进制数据以文本形式表达和传输。

- 编码表：共64个字符（a-z, A-Z, 0-9,+,/），`ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/`

- 需要 `4bit` 即可表示所有 `base64` 字符，映射到编码表。
- 每 `3byte` 为一组，可有四个 `base64` 字符表示（24bit），需要确保编码后的长度为4的倍数。
  - 4的倍数：解码器解析更高效，只需要以4为单位长度解析。
- 填充，存在三种情况：
  - 字节数 % 3 == 0，不需要填充。
  - 字节数 % 3 == 1，先填充4个0，再填充2个 `=` 字符。
    - `xxxxxx xx0000` + `=` + `=`
  - 字节数 % 3 == 2，先填充2个0，需要填充1个 `=` 字符。
    - `xxxxxx xxxxxx xxxx00` + `=`



#### 不同lang实现

- Swift：`base64.swift`





#### 实现

- `https://github.com/lemire/fastbase64/blob/master/src/chromiumbase64.c`
- `https://github.com/swift-extras/swift-extras-base64/blob/main/Sources/ExtrasBase64/Base64.swift`
- `https://github.com/apple/swift-nio/blob/main/Sources/_NIOBase64/Base64.swift`
