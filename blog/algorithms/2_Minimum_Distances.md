---
title: 'Minimum_Distances - HackerRank / Javascript'
date: 2021-08-08 17:12:08
category: 'Algorithms'
draft: false
---

## Question.

We define the distance between two array values as the number of indices between the two values. Given `a`, find the minimum distance between any pair of equal elements in the array. If no such value exists, print `-1`.

For example, if `a = [3,2,1,2,3]`, there are two matching pairs of values: `3` and `2`. The indices of the `3`‘s are `i = 0` and `j = 4`, so their distance is `d[i,j] = |j - i| = 4`. The indices of the `2`‘s are `i = 1` and `j = 3`, so their distance is `d|i,j| = |j - i| = 2`.


### Example :
```
Input: a = [7, 1, 3, 4, 1, 7]
Output: 3
```


### Constraints: 

- `1 <= n <= 10^3`
- `1 <= a[i] <= 10^5`


## Answer.

### My Code:

가장 가까이에 pair를 가진 element 사이의 거리 중 최소값을 반환하는 문제로,
왼쪽에서 시작하든, 오른쪽에서 시작하든, 중간에서 시작하든 값이 달라질 수 있어 모든 element를 확인해야 한다고 생각했다.
대상이 되는 element를 제외한 Array를 만들어 pair가 되는 element의 index값을 거리로 하여 값을 구하고 그 중 최소값을 반환하도록 했다.

```js
/**
 * @param {[Number]} a
 * @return {Number}
 */
function minimumDistances(a) {
    let result = Infinity;
    a.forEach((val, idx) => {
        const reminder = a.slice(idx+1);
        const distance = reminder.findIndex(el => el === val) + 1;
        if(distance > 0) {
            result = Math.min(result, distance);
        }
    });
    if (result === Infinity) {
        result = -1;
    }
    return result;
}
```



### Most Voted:

```js
function minimumDistances(a) {
    // Write your code here
    let last, lastIndex;
    let ar = []
    while(a.length !== 0) {
        last = a.pop();
        lastIndex = a.length - 1;
        if(a.includes(last)) {
            let dist = Math.abs(a.indexOf(last) - (lastIndex+1));
            ar.push(dist);
        }
    }
    if(ar.length === 0){
        return -1;
    } else {
        return Math.min(...ar);
    }
}
```
