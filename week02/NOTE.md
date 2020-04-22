## 1. 写一个正则表达式 匹配所有 Number 直接量
#### 答案
- 整型字面量
```
/^-?[0-9]\d*$/g
```

- 十六进制字面量
```
/(0x)?[0-9a-fA-F]+/g
```

- 浮点型字面量
```
/^-?([1-9]\d*\.\d*|0\.\d*[1-9]\d*|0?\.0+|0)$/g
```

## 2. 写一个 UTF-8 Encoding 的函数
#### 答案
```
function encoding(str) {
  let code = encodeURIComponent(str)
  let charCodeList = []

  for (let i = 0; i < code.length; i++) {
    let char = code.charAt(i)
    if (char === '%') {
      let hex = code.charAt(i + 1) + code.charAt(i + 2)
      let hexValue = parseInt(hex, 16)
      charCodeList.push(hexValue)
      i += 2
    } else {
      charCodeList.push(char.charCodeAt(0))
    }
  }
  return charCodeList
}
```

## 3. 写一个正则表达式，匹配所有的字符串直接量，单引号和双引号
#### 答案
```
/?:[^"]|\.)*"|'(?:[^']|\.)*|^[\u4E00-\u9FA5A-Za-z0-9]+$ /g
```