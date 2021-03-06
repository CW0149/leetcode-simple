# [1比特与2比特字符](https://leetcode-cn.com/problems/1-bit-and-2-bit-characters)

### 问题

有两种特殊字符。第一种字符可以用一比特0来表示。第二种字符可以用两比特(10 或 11)来表示。

现给一个由若干比特组成的字符串。问最后一个字符是否必定为一个一比特字符。给定的字符串总是由0结束。

示例 1:

```
输入:
bits = [1, 0, 0]
输出: True
解释:
唯一的编码方式是一个两比特字符和一个一比特字符。所以最后一个字符是一比特字符。
```
示例 2:

```
输入:
bits = [1, 1, 1, 0]
输出: False
解释:
唯一的编码方式是两比特字符和两比特字符。所以最后一个字符不是一比特字符。
```
注意:

* 1 <= len(bits) <= 1000.
* bits[i] 总是0 或 1.

### 解答

```
/**
 * @param {number[]} bits
 * @return {boolean}
 */
//      00 1比特
//     010 2比特
//    0110 1比特
//   01110 2比特
//  011110 1比特...
//  111110 2/1比特...
// 转为数0前连续1的奇偶，1为奇数则是2比特，偶数1比特
var isOneBitCharacter = function(bits) {
    let cnt = 0
    for (let i = bits.length - 2; i >= 0; i -= 1) {
        if (bits[i] !== 1) break
        cnt += 1
    }
    return cnt % 2 === 0
};
```
