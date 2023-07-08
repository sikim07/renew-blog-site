---
title: 'Chocolate Feast - HackerRank / Javascript'
date: 2022-08-16 22:42:17
category: 'Algorithms'
draft: false
---

## Question.

Little Bobby loves chocolate. He frequently goes to his favorite 5 & 10 store, Penny Auntie, to buy them. They are having a promotion at Penny Auntie. If Bobby saves enough wrappers, he can turn them in for a free chocolate.

Example
```
n=15
c=3
m=2
```
He has `15` to spend, bars cost `3`, and he can turn in `2` wrappers to receive another bar. Initially, he buys `5` bars and has `5` wrappers after eating them. He turns in `4` of them, leaving him with `1`, for `2` more bars. After eating those two, he has `3` wrappers, turns in `2` leaving him with `1` wrapper and his new bar. Once he eats that one, he has wrappers and turns them in for another bar. After eating that one, he only has `1` wrapper, and his feast ends. Overall, he has eaten `5+2+1+1=9` bars.

### Example 1:
```
Input: n = 10, c = 2, m = 5
Output: 6
```

### Example 2:
```
Input: n = 12, c = 4, m = 4
Output: 3
```

### Example 3:
```
Input: n = 6, c = 2, m = 2
Output: 5
```


### Constraints: 

- `2 <= n <= 10^5`
- `1 <= c <= n`
- `2 <= m <= n`


## Answer.

### My Code:

반복문을 통해서 계산이 되지 않을 때까지 계산하는 문제로 판단하고 첫 계산 후 while문으로 계산되지 않을 조건까지 반복되도록 구현했다.
현재 HackerRank의 easy 난이도 문제들을 풀고있는데, 앞으로 난이도를 높이거나 다양한 플랫폼에서 테스트를 진행할 생각이다.

```js
/**
 * @param Number n
 * @param Number c
 * @param Number m
 * @return Number
 */
function chocolateFeast(n, c, m) {
    let result = Math.floor(n / c);
    let wrap = result;

    while(wrap >= m) {
        const newChocolate = Math.floor(wrap / m);
        const usedWrap = newChocolate * m;
        result += newChocolate;
        wrap = wrap - usedWrap + newChocolate;
    }

    return result;
}
```



### Most Voted:

```js
function chocolateFeast(n, c, m) {
    let initial = Math.floor( n/ c)
    let wraps = initial ;
    let remainder;
    while(wraps >= m) {
        remainder = wraps % m
        wraps = Math.floor(wraps/m);

        initial += wraps;
        wraps += remainder;
    }
    return initial;
}
```
