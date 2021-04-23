# 컴퓨터 알고리즘

## 중간고사: *Strassen Algorithm* 설명 및 코드구현, 성능분석

## 1. Strassen Algorithm?
**Strassen Algorithm**은 행렬 곱셈 알고리즘으로 정의에 따라 두 행렬의 곱을 이용하면 ![CodeCogsEqn (1)](https://user-images.githubusercontent.com/82091824/115876342-26957e80-a481-11eb-887c-efc0b27350dd.gif)의 시간이 소모지만, 이 알고리즘을 이용하면 대략 ![CodeCogsEqn (1)](https://user-images.githubusercontent.com/82091824/115876522-62304880-a481-11eb-9ce5-d29a375b6247.gif)의 시간 복잡도가 걸린다.

### (1) 행렬의 곱 단순한 방법
![CodeCogsEqn (8)](https://user-images.githubusercontent.com/82091824/115886929-601fb700-a48c-11eb-9b04-113a20819ce2.gif)

![CodeCogsEqn (9)](https://user-images.githubusercontent.com/82091824/115887747-331fd400-a48d-11eb-9d28-8bce60085689.gif)

![CodeCogsEqn (10)](https://user-images.githubusercontent.com/82091824/115887891-55195680-a48d-11eb-8970-9c36c787898e.gif)

![CodeCogsEqn (11)](https://user-images.githubusercontent.com/82091824/115888071-78440600-a48d-11eb-8d55-032b2ca2db1b.gif)

![CodeCogsEqn (12)](https://user-images.githubusercontent.com/82091824/115888168-94e03e00-a48d-11eb-817a-71cf9abc2f7e.gif)

- 이 방법으로 행렬의 곱을 구하면 계산 과정에서 8번의 곱과 4번의 덧셈이 필요하다.   
- ![CodeCogsEqn (13)](https://user-images.githubusercontent.com/82091824/115889827-4338b300-a48f-11eb-8131-b8ed38a5dc13.gif) 행렬과 ![CodeCogsEqn (13)](https://user-images.githubusercontent.com/82091824/115889827-4338b300-a48f-11eb-8131-b8ed38a5dc13.gif) 행렬의 곱일때, 시간복잡도는 ![CodeCogsEqn (14)](https://user-images.githubusercontent.com/82091824/115890032-78dd9c00-a48f-11eb-99a7-a3eeebc23c18.gif) 이다
### (2) *Strassen Algorithm*을 이용한 행렬 곱 



## 2. 코드설명

## 3. 성능비교

## 4. 결론

## 5. 전체 코드

