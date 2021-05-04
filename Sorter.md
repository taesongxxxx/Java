# 컴퓨터 알고리즘

## 9주차 과제: 정렬 알고리즘 

## 1. 정렬 알고리즘 

### (1) 버블 정렬

![image](https://user-images.githubusercontent.com/82091824/116995180-b30f2f00-ad14-11eb-95cf-ad9b7bf56467.png)    
**▲ 1번째 패스의 수행과정**
- 두 인접한 원소를 비교하여 정렬하는 방법이다. 오름차순으로 정렬하면 작은수는 앞쪽으로 이동시키는 과정을 반복한다. 원소의 이동이 거품처럼 위로 올라가는것을 연상케한다하여 붙여진 이름이다. 입력을 전체적으로 1번 처리하는 것을 패스(pass)라고 하며, n개의 원소가 있으면 (n-1)번의 패스가 수행된다.
- pass=1이면 (n-1)번 비교하고, pass=2이면 (n-2)번 비교하고, pass=n-1이면 1번 비교한다.  총 비교 횟수: (n-1)+(n-2)+... = n(n-1)/2  
- 시간복잡도:  ![CodeCogsEqn (34)](https://user-images.githubusercontent.com/82091824/116996511-7f350900-ad16-11eb-8118-1fb1aa3ba8e6.gif)

#### 장점
- 코드가 직관적이며, 코드구현이 간단하다.
- 데이터를 하나씩 비교가능해 정밀하게 비교가능하다.
#### 단점
- 항상 ![CodeCogsEqn (33)](https://user-images.githubusercontent.com/82091824/116893044-79ceb480-ac6b-11eb-8a73-abdc0a9c41dd.gif)
의 시간복잡도를 가진다.
- n개의 원소에 대하여 n개의 메모리를 사용하여, 원소의 개수가 많아지면 성능면에서 좋은 알고리즘은 아니다. 
   
    
    
### (2) 선택 정렬

![image](https://user-images.githubusercontent.com/82091824/116998564-637f3200-ad19-11eb-9dff-a890b9b0e411.png)

- 주어진 배열에서 최소값을 찾고, 그 값을 배열의 맨 앞에 위치한 값과 자리를 바꾼다. 맨 처음 인덱스를 제외한 나머지 배열을 같은 방법으로 교체한다. 이 과정을 (n-1)만큼 반복한다.
-  
#### 장점
- 코드구현이 간단하다.
- 비교횟수는 많으나, 교환횟수는 적어 교환이 많이 일어나는 배열에서 좋은 성능을 보여준다. ex) 내림차순정렬을 오름차순정렬로 재정렬할 때
#### 단점
- 항상 ![CodeCogsEqn (33)](https://user-images.githubusercontent.com/82091824/116893044-79ceb480-ac6b-11eb-8a73-abdc0a9c41dd.gif)
의 시간복잡도를 가진다.
- 비교횟수가 많아 이미 정렬된 배열에 추가적인 데이터가 입력되면 재정렬할 때 최악의 성능을 보여준다.
### (3) 삽입 정렬 
- 설명
#### 장점
- 크기가 적은 데이터 집합을 정렬할때 버블정렬보다 좋은 성능을 보여준다.
- 거의 정렬된 입력에 대해서는 다른 정렬 알고리즘보다 빠르다.
#### 단점
- 입력된 데이터의 크기나 상태에 따라 성능의 편차가 크다.

### (4) 쉘 정렬
- 설명
#### 장점
- 입력 크기가 매우크지 않은 경우에 매우 좋은 성능을 보여준다.
#### 단점
- 간격을 잘못 설정할 경우, 좋지않은 성능을 보여줄 수도 있다.

## 2. 코드 구현

### (1) 버블 정렬
```java
    public int[] Bubble(int[] A){
        for(int pass=1; pass<=A.length-1; pass++)
            for(int i=1; i<=A.length-pass; i++)
                if(A[i-1] > A[i])
                   swap(A,i-1,i);
        return A;
    }

```
### (2) 선택 정렬
```java
    public int[] Selection(int[] A){
        for(int i=0; i<A.length-1; i++){
            int min = i;
            for(int j=i+1; j<A.length; j++){
                if(A[j] < A[min])
                    min = j;
            }
            swap(A,i,min);
        }
        return A;
```
### (3) 삽입 정렬
```java
   public int[] Insertion(int[] A){
        for(int i=1; i<A.length; i++){
            int CurrentElement = A[i];
            int j = i-1;
            while(j>=0 && A[j]>CurrentElement){
                A[j+1] = A[j];
                j=j-1;
            }
            A[j+1] = CurrentElement;
        }
        return A;
    }
```
### (4) 쉘 정렬
```java
```
## 3. 성능 분석


## 4. 결론
