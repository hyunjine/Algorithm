# 1375번 Bulb Switcher3

[문제 보러가기](https://leetcode.com/problems/bulb-switcher-iii/)

## 🅰 설계

moment 를 카운트하는 전역변수를 하나두고, 킬때를 기준으로 왼쪽이 다켜져있으면, 카운트를 증가시켜보자.
풀다가 조건이 하나 더 생겼다. 그 전구기준으로 오른쪽에 전구가 켜있으면 전체가 파란색으로 바뀌지 않는다. 그 기준 왼쪽 전구가 전부 파란색일때 카운팅해야한다.
계속 생각하니까 가장 오른쪽에 있는 전구랑 현재 켜져있는 전구의 수가 같아야한다.

## ✅ 후기

```js
var numTimesAllBlue = function (light) {
  let onCount = 0,
    furthestRight = -1,
    result = 0;

  for (let currentBulb of light) {
    onCount++;
    furthestRight = Math.max(furthestRight, currentBulb);
    if (onCount === furthestRight) result++;
  }

  return result;
};
```

```java
  public int numTimesAllBlue(int[] A) {
        int right = 0, res = 0, n = A.length;
        for (int i = 0; i < n; ++i) {
            right = Math.max(right, A[i]);
            if (right == i + 1) ++res;
        }
        return res;
    }
```

// 새롭게 알게되거나 공유해서 알게된 점

쉽게생각했어야되는데..ㅠ자꾸 어렵게 시간복잡도만증가하게 풀고있었다.

// 고생한 점

계속 순회해서 풀려고하니까 고생했다. 좀 규칙과 멀리서 보는 것을 연습해야할 것 같다.
