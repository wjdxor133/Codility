## 문제 설명

A non-empty array A consisting of N integers is given. The array contains an odd number of elements, and each element of the array can be paired with another element that has the same value, except for one element that is left unpaired.

For example, in array A such that:

A[0] = 9 A[1] = 3 A[2] = 9
A[3] = 3 A[4] = 9 A[5] = 7
A[6] = 9

> the elements at indexes 0 and 2 have value 9,the elements at indexes 1 and 3 have value 3,the elements at indexes 4 and 6 have value 9,the element at index 5 has value 7 and is unpaired.

Write a function:

> function solution(A);

that, given an array A consisting of N integers fulfilling the above conditions, returns the value of the unpaired element.

For example, given array A such that:

A[0] = 9 A[1] = 3 A[2] = 9
A[3] = 3 A[4] = 9 A[5] = 7
A[6] = 9

the function should return 7, as explained in the example above.

Write an **efficient** algorithm for the following assumptions:

> N is an odd integer within the range [1..1,000,000];each element of array A is an integer within the range [1..1,000,000,000];all but one of the values in A occur an even number of times.

## 🔎 접근 방법

홀수들로 이루어진 배열이 주어지며 빈 배열은 없다고 가정했을 때,

모든 배열의 요소들은 딱 하나의 요소를 제외하곤 모두 짝을 이룬다.

즉, A 배열이 [9, 3, 9, 3, 9, 7, 9]라면 모든 배열의 요소가 짝수 번 등장하는데 7만 홀수 번 등장한다.

이 때 7을 리턴하는 함수를 만들면 된다.

즉, **A 배열의 요소 중 짝수 번 등장하는 숫자 하나를 리턴하는 함수를 만드는 문제**이다.

💡 **접근했던 방식**

1. 배열의 원소들을 객체로 만든다. { 배열 원소: 개수 }
2. 개수를 2로 나눠서 나머지가 1인 수를 추출해 반환한다.

## 통과 못한 코드

```jsx
// 통과률 66퍼..
function solution(A) {
  // write your code in JavaScript (Node.js 8.9.4)
  const objA = A.reduce((acc, cur) => {
    acc[cur] = (acc[cur] || 0) + 1;
    return acc;
  }, {});

  for (let key in objA) {
    if (objA[key] === 1) {
      return parseInt(key);
    }
  }
}
```

- 왜 안될까...

## 통과 코드

```jsx
// you can write to stdout for debugging purposes, e.g.
// console.log('this is a debug message');

function solution(A) {
  // write your code in JavaScript (Node.js 8.9.4)
  const objA = A.reduce((acc, cur) => {
    acc[cur] = (acc[cur] || 0) + 1;
    return acc;
  }, {});

  for (let key in objA) {
    if (objA[key] % 2 === 1) {
      return parseInt(key);
    }
  }
}
```

- % 2로 변경하니 통과했다.
- 아마 명시적으로 표기해서 통과율이 저조했던 것 같다.

## 시간복잡도

<img width="509" alt="스크린샷 2021-08-21 오후 9 09 59" src="https://user-images.githubusercontent.com/47416686/130321473-dedabbc0-0460-4889-964f-c53093120e33.png">

## ✔️ 참고

[OddOccurrencesInArray coding task - Learn to Code - Codility](https://app.codility.com/programmers/lessons/2-arrays/odd_occurrences_in_array/)

[[Javascript] 배열 중복 값 개수 구하기](https://hianna.tistory.com/459)

[[알고리즘/자바스크립트] Codility, OddOccurrencesInArray 문제 풀이](https://im-developer.tistory.com/179)
