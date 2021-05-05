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
**▲ 선택 정렬 수행과정**
- 주어진 배열에서 최소값을 찾고, 그 값을 배열의 맨 앞에 위치한 값과 자리를 바꾼다. 맨 처음 인덱스를 제외한 나머지 배열을 같은 방법으로 교체한다. 이 과정을 (n-1)만큼 반복한다.   
- 시간 복잡도: ![CodeCogsEqn (34)](https://user-images.githubusercontent.com/82091824/116996511-7f350900-ad16-11eb-8118-1fb1aa3ba8e6.gif)
#### 장점
- 코드구현이 간단하다.
- 비교횟수는 많으나, 교환횟수는 적어 교환이 많이 일어나는 배열에서 좋은 성능을 보여준다. ex) 내림차순정렬을 오름차순정렬로 재정렬할 때
#### 단점
- 항상 ![CodeCogsEqn (33)](https://user-images.githubusercontent.com/82091824/116893044-79ceb480-ac6b-11eb-8a73-abdc0a9c41dd.gif)
의 시간복잡도를 가진다.
- 비교횟수가 많아 이미 정렬된 배열에 추가적인 데이터가 입력되면 재정렬할 때 최악의 성능을 보여준다.
### (3) 삽입 정렬 
![image](https://user-images.githubusercontent.com/82091824/116999429-9118ab00-ad1a-11eb-971f-ed52de1e9df3.png)   
**▲ 삽입 정렬 수행과정**
- 배열을 이미 정렬된 부분과, 정렬 안 된 부분으로 나눈뒤, 정렬 안 된 부분의 가장 왼쪽 원소를 정렬된 부분의 적절한 위치에 삽입하여 정렬되도록 하는 과정을 반복한다.
- 버블 정렬이나 선택 정렬과 같은 알고리즘에 비교하여 빠르다.
- 최선일 때 시간복잡도: 배열이 이미 정렬되어 있으면 (n-1)번의 비교만 하면 되고, 이 때 시간복잡도는 ![CodeCogsEqn (36)](https://user-images.githubusercontent.com/82091824/116999810-2025c300-ad1b-11eb-9ed4-9b11b86f5fba.gif) 이다.
- 최악일 때 시간복잡도: 최악의 경우일 때 시간복잡도는  ![CodeCogsEqn (34)](https://user-images.githubusercontent.com/82091824/116996511-7f350900-ad16-11eb-8118-1fb1aa3ba8e6.gif)
이다.
#### 장점
- 크기가 적은 데이터 집합을 정렬할때 좋은 성능을 보여준다.
- 거의 정렬된 입력에 대해서는 다른 정렬 알고리즘보다 빠르다.
#### 단점
- 입력된 데이터의 크기나 상태에 따라 성능의 편차가 크다.

### (4) 쉘 정렬
![image](https://user-images.githubusercontent.com/82091824/117001796-c377d780-ad1d-11eb-816a-1b89a2f17d39.png)

![image](https://user-images.githubusercontent.com/82091824/117001817-c8d52200-ad1d-11eb-92ec-b4143b60922d.png)   
**▲ 쉘 정렬 수행과정**
- 간격(gap)을 설정한 뒤, 배열을 간격만큼 쪼갠다. 쪼개진 배열에서 같은 부분에 있는 원소들끼리 삽입정렬을 수행한다. 간격을 줄여가면서 이 과정을 반복한다. 마지막에는 반드시 간격을 1로 설정해야 한다.
- 삽입정렬은 배열의 마지막 원소가 가장 작은 숫자일 경우 그 숫자가 배열의 맨 앞으로 이동하고 모든 다른 숫자들이 1칸 씩 오른쪽으로 이동해야하는 단점이 있는데, 쉘 정렬은 이를 보완할 수 있는 알고리즘이다. 
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
    public int[] Shell(int[] A){
        for(int gap=A.length/2; gap>=1; gap /= 2){
            for(int i=gap; i<A.length; i++){
                int CurrentElement = A[i];
                int j = i;
                while(j>=gap && A[j-gap]>CurrentElement){
                    A[j]=A[j-gap];
                    j=j-gap;
                }
                A[j]=CurrentElement;
            }
        }
        return A;
    }
```
## 3. 성능 분석

**▼n = 1000**

**▼n = 2000**

**▼n = 3000**

**▼n = 4000**

**▼n = 5000**

**▼n = 6000**

**▼n = 7000**

**▼n = 8000**

**▼n = 9000**

**▼n = 10000**

## 4. 결론

## 5. 소스코드
```java
import java.util.Random;

interface type{
    public void random(int[] A);
    public void descending(int[] A);
    public void almost(int[] A);
}

public class Sorter implements type{

    public void random(int[] A){            //랜덤 정렬
        Random r = new Random();
        for(int i=0; i<A.length; i++)
            A[i] = r.nextInt(1000);
    }

    public void descending(int[] A){        //내림차순 정렬
        int[] B = new int[A.length];
        for(int i=0; i<A.length; i++)
            B[i] = A[i];
        for(int i=0; i<A.length; i++)
            A[i] = B[A.length-(1+i)];
    }

    public void almost(int[] A){             //거의 정렬
        Random r = new Random();
        for(int i=0; i<A.length/10; i++){
            swap(A,r.nextInt(A.length-1),r.nextInt(A.length-1));
        }
    }

    public void swap(int[] A, int index1, int index2){
        int temp = A[index1];
        A[index1] = A[index2];
        A[index2] = temp;
    }

    public int[] Bubble(int[] A){           //버블 정렬
        for(int pass=1; pass<=A.length-1; pass++)
            for(int i=1; i<=A.length-pass; i++)
                if(A[i-1] > A[i])
                   swap(A,i-1,i);
        return A;
    }

    public int[] Selection(int[] A){        //선택 정렬
        for(int i=0; i<A.length-1; i++){
            int min = i;
            for(int j=i+1; j<A.length; j++){
                if(A[j] < A[min])
                    min = j;
            }
            swap(A,i,min);
        }
        return A;
    }

    public int[] Insertion(int[] A){        //삽입 정렬
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

    public int[] Shell(int[] A){            //쉘 정렬
        for(int gap=A.length/2; gap>=1; gap /= 2){
            for(int i=gap; i<A.length; i++){
                int CurrentElement = A[i];
                int j = i;
                while(j>=gap && A[j-gap]>CurrentElement){
                    A[j]=A[j-gap];
                    j=j-gap;
                }
                A[j]=CurrentElement;
            }
        }
        return A;
    }

    public static void main(String[] args) {
        Sorter sorter = new Sorter();
        int n = 1000;
        int[] A1 = new int[n];
        int[] A2 = new int[n];
        int[] A3 = new int[n];
        int[] A4 = new int[n];

        sorter.random(A1);
        for (int i=0; i<A1.length; i++) A2[i] = A1[i];
        for (int i=0; i<A1.length; i++) A3[i] = A1[i];
        for (int i=0; i<A1.length; i++) A4[i] = A1[i];

        long start1 = System.currentTimeMillis();
        sorter.Bubble(A1);
        long finshi1 = System.currentTimeMillis();

        long start2 = System.currentTimeMillis();
        sorter.Selection(A2);
        long finshi2 = System.currentTimeMillis();

        long start3 = System.currentTimeMillis();
        sorter.Insertion(A3);
        long finshi3 = System.currentTimeMillis();

        long start4 = System.currentTimeMillis();
        sorter.Shell(A4);
        long finshi4 = System.currentTimeMillis();

        System.out.println("Random -> 오름차순");
        System.out.println("버블 정렬: "+(finshi1-start1)+ "ms");
        System.out.println("선택 정렬: "+(finshi2-start2)+ "ms");
        System.out.println("삽입 정렬: "+(finshi3-start3)+ "ms");
        System.out.println("쉘 정렬: "+(finshi4-start4)+ "ms");
        System.out.println();

        sorter.descending(A1);
        sorter.descending(A2);
        sorter.descending(A3);
        sorter.descending(A4);

        start1 = System.currentTimeMillis();
        sorter.Bubble(A1);
        finshi1 = System.currentTimeMillis();

        start2 = System.currentTimeMillis();
        sorter.Selection(A2);
        finshi2 = System.currentTimeMillis();

        start3 = System.currentTimeMillis();
        sorter.Insertion(A3);
        finshi3 = System.currentTimeMillis();

        start4 = System.currentTimeMillis();
        sorter.Shell(A4);
        finshi4 = System.currentTimeMillis();

        System.out.println("내림차순 -> 오름차순");
        System.out.println("버블 정렬: "+(finshi1-start1)+ "ms");
        System.out.println("선택 정렬: "+(finshi2-start2)+ "ms");
        System.out.println("삽입 정렬: "+(finshi3-start3)+ "ms");
        System.out.println("쉘 정렬: "+(finshi4-start4)+ "ms");
        System.out.println();

        sorter.almost(A1);
        sorter.almost(A2);
        sorter.almost(A3);
        sorter.almost(A4);

        start1 = System.currentTimeMillis();
        sorter.Bubble(A1);
        finshi1 = System.currentTimeMillis();

        start2 = System.currentTimeMillis();
        sorter.Selection(A2);
        finshi2 = System.currentTimeMillis();

        start3 = System.currentTimeMillis();
        sorter.Insertion(A3);
        finshi3 = System.currentTimeMillis();

        start4 = System.currentTimeMillis();
        sorter.Shell(A4);
        finshi4 = System.currentTimeMillis();

        System.out.println("거의 정렬 -> 오름차순");
        System.out.println("버블 정렬: "+(finshi1-start1)+ "ms");
        System.out.println("선택 정렬: "+(finshi2-start2)+ "ms");
        System.out.println("삽입 정렬: "+(finshi3-start3)+ "ms");
        System.out.println("쉘 정렬: "+(finshi4-start4)+ "ms");
    }
}
```
