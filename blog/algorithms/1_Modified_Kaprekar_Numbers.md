---
title: 'Modified Kaprekar Numbers - HackerRank / Javascript'
date: 2022-08-14 21:51:19
category: 'Algorithms'
draft: false
---

## Question.

A modified Kaprekar number is a positive whole number with a special property. If you square it, then split the number into two integers and sum those integers, you have the same value you started with.

Consider a positive whole number `n` and `d` with digits. We square `n` to arrive at a number that is either `2*d` digits long or `(2*d)-1` digits long. Split the string representation of the square into two parts,`l` and `r`. The right hand part, `r` must be `d` digits long. The left is the remaining substring. Convert those two substrings back to integers, add them and see if you get `n`.

Example

`n=5`

`d=1`

First calculate that `n^2=25`. Split that into two strings and convert them back to integers `2` and `5`. Test `2+5=7!=5`, so this is not a modified Kaprekar number. If `n=9`, still `d=1`, and `n^2=81`. This gives us , the original `n`.

Note: `r` may have leading zeros.

### Example :
```
Input: p = "1", q = "100"
Output: "1 9 44 45 99"
```


### Constraints: 

- `0 < p < q < 100000`


## Answer.

### My Code:

Kaprekar Number를 구하는 특정 규칙이 있을 것 같아서 고민했지만 특징이 없다고 판단이 되어
순차척으로 Kaprekar Number인지 찾는 함수를 구현했다.
1. `p`가 `2`보다 작을 경우 `1`이 반드시 포함될 것.
2. `p`와 `q` 범위 안에 Kaprekar Number가 없을 경우 `INVALID RANGE`를 출력할 것.
3. `Square`(제곱)가 홀수자리일 경우 두 번에 나눠서 결정할 것.

범위 안의 수를 i로 하고 `Square`값을 구한 후, 배열로 만들어 자릿수 별로 구분할 수 있도록 나누어
`left`와 `right`로 분리한 후 i값과 동일한 지 확인한다.

가장 많은 득표수를 받은 함수와 비교해보면 내가 보기 보기 쉽게 하기 위해 나눠놓은 변수들을 한줄로 작성한 차이가 있었다.

```js
/**
 * @param {Number} p
 * @param {Number} q
 * @return {string}
 */
function kaprekarNumbers(p, q) {
    // Write your code here
    let result = "";
    if (p < 2) result = "1";
    for(let i = p; i <= q; i++) {
        const square = Math.pow(i,2);
        const length = square.toString().length;
        const half = Math.floor(length/2);
        const arr = square.toString().split('');
        let left = Number(arr.slice(0, half).join(''));
        let right = Number(arr.slice(half).join(''))
        if (left+right === i && left * right > 0) {
            result = result.concat(` ${i}`);
        } else if(length / 2 !== 0) {
            left = Number(arr.slice(0, half+1).join(''));
            right = Number(arr.slice(half+1).join(''));
            if (left+right === i && left * right > 0) {
                result = result.trim().concat(` ${i}`);
            }
        }
    }
    if (result.length === 0) result = "INVALID RANGE";
    console.log(result.trim());
}
```


### Most Voted:

```js
function kaprekarNumbers(p, q) {
    let answers = [];
    for (let i = p; i <= q; i++) {
        const square = (i * i).toString();
        let r = square.substring(square.length - i.toString().length);
        let l = square.substring(0, square.length - i.toString().length);
        if (parseInt(r) + parseInt(l || 0) === i) {
            answers.push(i);
        }
    }

    console.log(answers.length ? answers.join(' ') : 'INVALID RANGE');
}
```
