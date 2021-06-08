# 모의 담금질 기법


![Hill_Climbing_with_Simulated_Annealing](https://user-images.githubusercontent.com/82091824/120922713-aad85400-c705-11eb-9a9a-74e07b66f818.gif)

**모의 담금질 기법**(Simulated Annealing)은 해 탐색 알고리즘으로 어원은 담금질(quenching)에서 왔는데 이는 풀림(annealing)의 오역이다.
풀림은 금속재료를 가열한 다음 조금씩 냉각해 결정을 성장시켜 그 결함을 줄이는 작업으로 모의 담금질 기법은 이 과정을 모방한다.
높은 온도에서 해를 탐색할때는 특정한 패턴없이 자유분방하게 이루어지지만, 온도가 점차 낮아짐에따라 해 탐색이 점점 규칙적인 방식으로 이루어진다.

다음은 모의 담금질 기법을 이용해 전역최적해를 구하는 과정이다.

![image](https://user-images.githubusercontent.com/82091824/121193672-00009b00-c8a9-11eb-91a2-2dc8c25929cb.png)


(1) 후보해를 설정한 뒤 이웃해와 비교하여 더 우수한 해를 후보해로 둔다.

(2) 이 과정을 반복하여 계속 우수한 해를 찾아간다.

하지만 이렇게 이웃해만 비교하여 최적점을 찾다보면 지역최적점은 쉽게 찾을수 있겠지만, 그 점이 전역 최적점일 확률은 극히 낮을 것이다.
 
모의 담금질 기법은 여기에서 확률 개념을 도입하여 전역 최적점을 찾을 확률을 높인다.

적당한 확률 p를 설정한 뒤 0~1까지 주사위를 굴려 나온 값이 p보다 작으면 임의의 점을 구해 그 값이 후보해보다 더 우수하지 않더라도 그 점으로
이동하는 자유분방함을 보여준다. 이렇게하면 전역 최적점을 구하는데 걸리는 시간은 훨씬 많이 걸리지만 전역 최적해를 찾을 확률은
높아진다.


다음은 java에서 구현한 모의 담금질 기법의 기본적인 알고리즘이다. 
```java 
       for (int i=0; i<niter; i++){
            int kt = (int) t * 20;
            for(int j=0; j<kt; j++){
                double x1 = r.nextDouble()  * (upper - lower) + lower;
                double f1 = p.fit(x1);

                if(p.isNeighborBetter(f0,f1)){
                    x0 = x1;
                    f0 =f1;
                    hist.add(f0);
                }else{
                    double d = Math.abs(f1 - f0);
                    double p0 = Math.exp(-d/t);
                    if(r.nextDouble() < p0) {
                        x0 = x1;
                        f0 = f1;
                        hist.add(f0);
                    }
                }
            }
            t *= a;
        }
        return x0;
```

t(온도)를 너무 급속히 낮추면 전역최적점에 도달할 확률이 낮아지고, 너무 천천히 낮추면 적역최적점에 도달할 확률은 높아지지만
반복횟수가 많아져 그만큼 시간이 오래 걸린다. 그래서 적절한 a(냉각율)을 설정하는게 중요하다.

온도가 점차 낮아짐에 따라

###References
■ https://ko.wikipedia.org/wiki/%EB%8B%B4%EA%B8%88%EC%A7%88_%EA%B8%B0%EB%B2%95   
■ https://en.wikipedia.org/wiki/Simulated_annealing


