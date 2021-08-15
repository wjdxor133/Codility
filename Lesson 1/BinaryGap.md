## 문제 설명

A binary gap within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of N.

For example, number 9 has binary representation 1001 and contains a binary gap of length 2. The number 529 has binary representation 1000010001 and contains two binary gaps: one of length 4 and one of length 3. The number 20 has binary representation 10100 and contains one binary gap of length 1. The number 15 has binary representation 1111 and has no binary gaps. The number 32 has binary representation 100000 and has no binary gaps.

Write a function:

> function solution(N);

that, given a positive integer N, returns the length of its longest binary gap. The function should return 0 if N doesn't contain a binary gap.

For example, given N = 1041 the function should return 5, because N has binary representation 10000010001 and so its longest binary gap is of length 5. Given N = 32 the function should return 0, because N has binary representation '100000' and thus no binary gaps.

Write an **efficient** algorithm for the following assumptions:

> N is an integer within the range [1..2,147,483,647].

## 🔎 접근 방법

기존에 접근했던 방식은

1. 주어진 정수를 이진수로 변환한다.
2. 변환 후 1의 개수를 구한다.
3. 1을 기준으로 0의 묶음을 나눈다.
4. 0의 묶음이 0이면 0을 반환하고, 0이 아니면 0의 묶음 중 가장 큰수를 반환한다.

## 통과 못한 코드

```jsx
// 통과율 86퍼
function solution(N) {
  // write your code in JavaScript (Node.js 8.9.4)
  const binary = N.toString(2);
  const oneLen = binary.split("").filter((b) => b === "1").length;
  const zaroLen = Math.max(...binary.split("1").map((zero) => zero.length));

  // 1이 하나 들어있거나 0으로만 이루어져 있을 때
  return oneLen <= 1 || zaroLen === 0 ? 0 : zaroLen;
}
```

- 왜 안될까...

## 통과 코드

```jsx
function solution(N) {
  // write your code in JavaScript (Node.js 8.9.4)
  const binaryNum = N.toString(2);
  const binaryGaps = binaryNum.slice(
    binaryNum.indexOf("1") + 1,
    binaryNum.lastIndexOf("1")
  );

  const zeroCounted = binaryGaps.split("1").map((zeros) => zeros.length);

  return zeroCounted.length ? Math.max(...zeroCounted) : 0;
}
```

- 결국 찾아보게 되었다! 💪🏻

## ✔️ 참고

[1. Iterations lesson - Learn to Code - Codility](https://app.codility.com/programmers/lessons/1-iterations/)

[코딜리티 Lesson1 binary gap 문제풀기 (javascript)](https://slee2540.tistory.com/50)
