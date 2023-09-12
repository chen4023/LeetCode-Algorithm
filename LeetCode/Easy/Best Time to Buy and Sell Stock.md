## 📚 문제

<img src="../img/Best Time.png" style="width:500px">

</br>

## 💡 문제 접근 방법

이 문제를 해결하기 위해서는 주식을 사고 파는 과정이기 때문에 배열의 뒤 부터 접근하면 좋을 것 같다는 생각을 했다. 그래서 배열의 마지막부터 앞에 있는 요소에 접근하며 각 요소들의 차이가 양수인 결과의 값만 배열에 새롭게 추가하였다. 해당 배열의 Max 값이 음수이면 0을 반환하고, 양수이면 해당 Max 값을 반환하도록 해주었다.

</br>

## 아쉬운 점

나는 두개의 중첩 루프를 사용하여 배열을 반복하므로, 코드의 시간복잡도는 O(n^2)이 된다. 시간 복잡도를 고려하지 못한 점이 아쉬웠다. 테스트케이스는 통과했지만, 런타임 에러가 났다. 시간 복잡도를 항상 고려하여 코드를 짜도록 노력해야겠다. (🚨 최대한 중첩 루프는 피할 것 !)

```js
const maxProfit = (prices) => {
  let left = 0;
  let right = 1;
  let max_profit = 0;
  while (right < price.length) {
    if (prices[left] < prices[right]) {
      let profit = prices[right] - prices[left];
      max_profit = Math.max(max_profit, profit);
    } else {
      left = right;
    }
    right++;
  }
  return max_profit;
};
```

</br>

## 📝 내가 작성한 코드

```js
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function (prices) {
  let arr = [];
  for (let i = 0; i < prices.length; i++) {
    for (let j = i + 1; j < prices.length; j++) {
      if (prices[j] - prices[i] > 0) {
        let max = prices[j] - prices[i];
        arr.push(max);
      }
    }
  }
  const result = Math.max(...arr);
  if (result < 0) {
    return 0;
  } else {
    return result;
  }
};
```
