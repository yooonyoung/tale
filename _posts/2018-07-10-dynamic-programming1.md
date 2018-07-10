---

layout: post

title: "다이나믹 프로그래밍(Dynamic Programming)의 기본 풀이 방법"

---
**다이나믹 프로그래밍(Dynamic Programming)**이란, 큰 문제를 작은 문제로 나눠서 푸는 알고리즘을 말한다. 작은 문제로부터 큰 문제의 정답을 찾을 수 있기 때문에 같은 문제는 구할 때마다 정답이 같고, 정답을 한 번 풀었다면 정답을 메모해놓아야 한다. 이런 메모를 코드에서는 배열에 저장하는 방식으로 할 수 있으며, 이것을 Memoization이라고 한다.<br>
피보나치 문제를 예시로 들어보겠다.<br>
```c++
int fibonacci(int n) {
	if(n <= 1) {
    	return n;
    } else {
    	return fibonacci(n-1) + fibonacci(n-2);
    }
}
```
위 코드를 Memoization을 이용해 다음과 같이 구현할 수 있다.
```c++
int memo[100];
int fibonacci(int n) {
	if (n <= 1) {
    	return n;
    } else {
    	memo[n] = fibonacci(n-1) + fibonacci(n-2);
        return memo[n];
    }
}
```
<br>
`memo[i] = i번째 피보나치 수`<br>
보통 다이나믹 프로그래밍 문제에서는 memo[i]를 d[i], 또는 dp[i] 라고 한다.<br>
-> d[i]에 무엇이 들어가야 할지 먼저 정의해야 한다.<br>
`d[i] = i번째 피보나치 수`<br>
이렇게 정의할 수 있다면, d[i]를 어떻게 만들 수 있는지 식을 써줄 수 있어야 한다.<br>
`i번째 피보나치 수 = i-1번째 피보나치 수 + i-2번째 피보나치 수`
즉, `d[i] = d[i-1] + d[i-2]`<br>
이렇게 점화식을 완성한 다음부터는 테이블을 하나씩 채워나가는 방식으로 문제를 풀어나갈 수 있다.

**Top-down** : 큰 문제를 점점 작게 만들어나가는 방식(보통 재귀함수) <br>
fibonacci(n)을 풀어야한다고 가정하자. fibonacci(n)을 fibonacci(n-1)과 fibonacci(n-2)로 나누고, fibonacci(n-1)과 fibonacci(n-2)를 호출해 문제를 푼다. 그리고 fibonacci(n-1)의 값과 fibonacci(n-2)의 값을 더해 fibonacci(n)을 푼다. 시간복잡도는 채워야 하는 칸의 수 * 1칸을 채우는 시간복잡도 이다.
```c++
int d[100];
int fibonacci(int n) {
	if (n <= 1) {
    	return n;
    } else {
    	if (d[n] > 0) {
        	return d[n];
        }
        d[n] = fibonacci(n-1) + fibonacci(n-2);
        return d[n];
    }
}
```
시간복잡도 : N(채워야 하는 칸의 수) * O(1)(1칸을 채우는 복잡도) = O(N)

**Bottom-up** : 작은 문제부터 차례대로 푸는 방식
문제를 크기가 작은 문제부터 차례대로, 하나도 빠짐없이 점점 크게 만들면서 푼다. 작은 문제부터 하나도 빠짐없이 다 풀면 원래의 문제도 풀 수 있다.
```c++
int d[100];
int fibonacci(int n) {
	d[0] = 0;
    d[1] = 1;
    for (int i=2; i<=n; i++) { // 제일 작은 문제부터 제일 큰 문제까지 +1씩 증가시키면서 모두 푼다.
    	d[i] = d[i-1] + d[i-2];
    }
    return d[n];
}
```

top-down으로 풀 것인지, bottom-up으로 풀 것인지 자신이 편한 방법으로 풀면 된다.
재귀함수를 이용하거나, for문을 이용해주면 된다.
문제를 작은 문제로 나누고, 수식을 이용해서 문제를 표현해야 한다.
