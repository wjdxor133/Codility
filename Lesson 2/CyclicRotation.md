## 문제 설명

An array A consisting of N integers is given. Rotation of the array means that each element is shifted right by one index, and the last element of the array is moved to the first place. For example, the rotation of array A = [3, 8, 9, 7, 6] is [6, 3, 8, 9, 7] (elements are shifted right by one index and 6 is moved to the first place).

The goal is to rotate array A K times; that is, each element of A will be shifted to the right K times.

Write a function:

> class Solution { public int[] solution(int[] A, int K); }

that, given an array A consisting of N integers and an integer K, returns the array A rotated K times.

For example, given

A = [3, 8, 9, 7, 6]
K = 3

the function should return [9, 7, 6, 3, 8]. Three rotations were made:

[3, 8, 9, 7, 6] -> [6, 3, 8, 9, 7]
[6, 3, 8, 9, 7] -> [7, 6, 3, 8, 9]
[7, 6, 3, 8, 9] -> [9, 7, 6, 3, 8]

For another example, given

A = [0, 0, 0]
K = 1

the function should return [0, 0, 0]

Given

A = [1, 2, 3, 4]
K = 4

the function should return [1, 2, 3, 4]

Assume that:

> N and K are integers within the range [0..100];each element of array A is an integer within the range [−1,000..1,000].

In your solution, focus on **correctness**. The performance of your solution will not be the focus of the assessment.

## 🔎 접근 방법

접근했던 방식은

1. K번 반복하는 동안 배열의 끝에 있는 원소가 맨 앞에 오면 되는 문제이기 때문에 `pop()` , `unshift()`를 사용해서 구현했다.

## 통과 못한 코드

```jsx
// 통과율 87%
function solution(A, K) {
  // write your code in JavaScript (Node.js 8.9.4)
  for (let i = 0; i < K; i++) {
    const lastEl = A.pop();
    A.unshift(lastEl);
  }

  return A;
}
```

- 왜 안될까...

## 통과 코드

```jsx
function solution(A, K) {
  // write your code in JavaScript (Node.js 8.9.4)
  // 이 부분!
  if (!A.length) {
    return [];
  }

  for (let i = 0; i < K; i++) {
    const lastEl = A.pop();
    A.unshift(lastEl);
  }

  return A;
}
```

- 통과가 완전히 안됐던 이유는 A 배열에 원소가 아예 없을 경우를 체크해주지 않았기 때문이다.

## ✔️ 참고

[CyclicRotation coding task - Learn to Code - Codility](https://app.codility.com/programmers/lessons/2-arrays/cyclic_rotation/)
