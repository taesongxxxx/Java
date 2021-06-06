# 모의 담금질 기법


![Hill_Climbing_with_Simulated_Annealing](https://user-images.githubusercontent.com/82091824/120922713-aad85400-c705-11eb-9a9a-74e07b66f818.gif)



**모의 담금질 기법**(Simulated Annealing)은 해 탐색 알고리즘으로 어원은 담금질(quenching)에서 왔는데 이는 풀림(annealing)의 오역이다.
풀림은 금속재료를 가열한 다음 조금씩 냉각해 결정을 성장시켜 그 결함을 줄이는 작업으로 모의 담금질 기법은 이 과정을 모방한다.
높은 온도에서 해를 탐색할때는 특정한 패턴없이 자유분방하게 이루어지지만, 온도가 점차 낮아짐에따라 점점 규칙적인 방식으로 이루어진다.

다음은 모의 담금질 기법을 이용해 전역최적해를 구하는 과정이다.

다음은 java에서 구현한 모의 담금질 기법의 기본적인 알고리즘이다.
```java

```

임의의 후보해 x0를 정하고

하지만 이렇게 이웃해만 비교하여 최적점을 찾다보면 지역최적점은 찾을수 있겠지만, 그 점이 전역최적점일 확률은 매우 낮다.

그래서 확률개념을 도입하여 


몇개의 ~~~

이 값들을 잘 설정하여 ~~~

그렇게 해서나온 최적의 ~~~

###References
■ https://ko.wikipedia.org/wiki/%EB%8B%B4%EA%B8%88%EC%A7%88_%EA%B8%B0%EB%B2%95   
■ https://en.wikipedia.org/wiki/Simulated_annealing
