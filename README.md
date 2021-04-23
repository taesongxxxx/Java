# 컴퓨터 알고리즘

## 중간고사: *Strassen Algorithm* 설명 및 코드구현, 성능분석

## 1. *Strassen Algorithm?*
- ***Strassen Algorithm*** **은 행렬 곱셈 알고리즘으로 정의에 따라 두 행렬의 곱을 이용하면 ![CodeCogsEqn (1)](https://user-images.githubusercontent.com/82091824/115876342-26957e80-a481-11eb-887c-efc0b27350dd.gif)의 시간이 소모지만, 이 알고리즘을 이용하면 대략 ![CodeCogsEqn (1)](https://user-images.githubusercontent.com/82091824/115876522-62304880-a481-11eb-9ce5-d29a375b6247.gif)의 시간 복잡도가 걸린다.**

### (1) 행렬의 곱 기본 Algorithm         

<br><p align="center"><img src="https://user-images.githubusercontent.com/82091824/115886929-601fb700-a48c-11eb-9b04-113a20819ce2.gif"></p><br>
    
<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115892111-ceb34380-a491-11eb-9c56-925150cd7399.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115887747-331fd400-a48d-11eb-9d28-8bce60085689.gif"></p>
   
<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115887891-55195680-a48d-11eb-8970-9c36c787898e.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115888071-78440600-a48d-11eb-8d55-032b2ca2db1b.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115888168-94e03e00-a48d-11eb-817a-71cf9abc2f7e.gif"></p><br/>

- **이 알고리즘으로 행렬의 곱을 계산하면 과정에서 8번의 곱셈연산과 4번의 덧셈연산이 일어난다.**   
- **![CodeCogsEqn (13)](https://user-images.githubusercontent.com/82091824/115889827-4338b300-a48f-11eb-8131-b8ed38a5dc13.gif) 행렬과 ![CodeCogsEqn (13)](https://user-images.githubusercontent.com/82091824/115889827-4338b300-a48f-11eb-8131-b8ed38a5dc13.gif) 행렬의 곱일때, 시간복잡도는 ![CodeCogsEqn (14)](https://user-images.githubusercontent.com/82091824/115890032-78dd9c00-a48f-11eb-99a7-a3eeebc23c18.gif) 이다.**

### (2) *Strassen Algorithm*을 이용한 행렬 곱    
<br><p align="center"><img src="https://user-images.githubusercontent.com/82091824/115886929-601fb700-a48c-11eb-9b04-113a20819ce2.gif"></p><br/>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115897959-fb6a5980-a497-11eb-86d5-4674664b67b6.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115897715-afb7b000-a497-11eb-9903-50a956c512b5.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115898179-3a001400-a498-11eb-9261-4a9a5a012eff.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115898302-5b610000-a498-11eb-97ad-61a59fac8c3b.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115898400-7a5f9200-a498-11eb-9ac6-25ecb57dcd80.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115898522-9cf1ab00-a498-11eb-8602-676736253971.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115898607-b4309880-a498-11eb-9615-557658bed8d9.gif"></p><br>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115901707-7f264500-a49c-11eb-8562-7590145405d5.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115901882-bd236900-a49c-11eb-8ed6-f477f4270d5c.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115901953-d0cecf80-a49c-11eb-8d56-88274e20e995.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115902013-e47a3600-a49c-11eb-99cc-56dacfa758db.gif"></p><br/>

- **기본 알고리즘으로 계산시 8번의 곱셈연산이 일어나는 반면, 위 알고리즘을 이용하면 7번의 곱셈연산과 18번의 덧셈연산이 일어나는 것을 볼 수있다. 행렬이 커지면 일반적으로 곱셈보다는 덧셈의 연산속도가 더 빠르므로 행렬의 크기가 커질수록 Strassen Algorithm 의 효율이 좋아진다.**    
   
- **위 과정을 재귀적으로 반복할 경우 ![CodeCogsEqn (29)](https://user-images.githubusercontent.com/82091824/115904518-d548b780-a49f-11eb-8236-ddb0b383eaf6.gif) 번의 연산이 필요하다.  ![CodeCogsEqn (30)](https://user-images.githubusercontent.com/82091824/115904895-4d16e200-a4a0-11eb-875d-1ef0ac6b3504.gif) 이므로, 시간복잡도는 약  ![CodeCogsEqn (1)](https://user-images.githubusercontent.com/82091824/115876522-62304880-a481-11eb-9ce5-d29a375b6247.gif) 이다**

## 2. 코드설명

## 3. 성능비교

## 4. 결론

## 5. 전체 코드
```java
import java.util.Random;
import java.util.Scanner;

public class Main {
    //행렬 입력
    public static int[][] init_matrix(int n){
        int [][] matrix = new int[n][n];
        Random random = new Random();
        for(int i=0; i<n; i++)
            for(int j=0; j<n; j++)
                matrix[i][j] = random.nextInt(10);
        return matrix;
    }
    //행렬 출력
    void print_matrix(int[][] matrix){
        for(int i=0; i<matrix.length; i++) {
            for (int j = 0; j < matrix[0].length; j++) {
                System.out.printf("%d ", matrix[i][j]);
            }
            System.out.println();
        }
    }
    //행렬 분할
    public int[][] subM(int[][] matrix, int a, int b, int n){
        int x= 0;
        int y= 0;
        int[][] subM = new int[n][n];
        for(int i=a; i<a+n; i++) {
            for (int j = b; j < b + n; j++) {
                subM[x][y] = matrix[i][j];
                y++;
            }
            y=0;
            x++;
        }
        return subM;
    }
    //행렬 합치기
    public int[][] merge_subM(int n, int[][] c11, int[][] c12, int[][] c21, int[][] c22){
        int[][] mergeM = new int[2*n][2*n];
        for(int i=0; i<n; i++){
            for(int j=0; j<n; j++) {
                mergeM[i][j] = c11[i][j];
                mergeM[i+n][j] = c12[i][j];
                mergeM[i][j+n] = c21[i][j];
                mergeM[i+n][j+n] = c22[i][j];
            }
        }
        return mergeM;
    }
    //행렬 * 행렬
    public int[][] Mmul(int n,int[][] matrixA, int[][] matrixB){
       int[][] Mmul = new int[n][n];
        for(int i=0; i<n; i++){
            for(int j=0; j<n; j++){
                for(int k=0; k<n; k++){
                    Mmul[i][j] += matrixA[i][k]*matrixB[k][j];
                }
            }
        }
        return Mmul;
    }
    //행렬 + 행렬
    public int[][] Msum(int n,int[][] matrixA, int[][] matrixB){
        int[][] Msum = new int[n][n];
        for(int i=0; i<n; i++)
            for(int j=0; j<n; j++){
                Msum[i][j] = matrixA[i][j]+matrixB[i][j];
            }
        return Msum;
    }
    //행렬 - 행렬
    public int[][] Msub(int n,int[][] matrixA, int[][] matrixB){
        int[][] Msub = new int[n][n];
        for(int i=0; i<n; i++)
            for(int j=0; j<n; j++){
                Msub[i][j] = matrixA[i][j]-matrixB[i][j];
            }
        return Msub;
    }
    //Strassen Algorithm
    public int[][] Strassen(int n, int[][] matrixA, int[][] matrixB){
        if(n < 2){
            int[][] matrixC = Mmul(n,matrixA,matrixB);
            return matrixC;
        }
        int k = n/2;

        int[][] suba11 = subM(matrixA,0,0,k);
        int[][] suba12 = subM(matrixA,k,0,k);
        int[][] suba21 = subM(matrixA,0,k,k);
        int[][] suba22 = subM(matrixA,k,k,k);

        int[][] subb11 = subM(matrixB,0,0,k);
        int[][] subb12 = subM(matrixB,k,0,k);
        int[][] subb21 = subM(matrixB,0,k,k);
        int[][] subb22 = subM(matrixB,k,k,k);

        int[][] M1 = Strassen(k,Msum(k,suba11,suba22),Msum(k,subb11,subb22));
        int[][] M2 = Strassen(k,Msub(k,suba21,suba22),subb11);
        int[][] M3 = Strassen(k,suba11,Msub(k,subb12,subb22));
        int[][] M4 = Strassen(k,suba22,Msub(k,subb21,subb11));
        int[][] M5 = Strassen(k,Msum(k,suba11,suba12),subb22);
        int[][] M6 = Strassen(k,Msub(k,suba21,suba11),Msum(k,subb11,subb12));
        int[][] M7 = Strassen(k,Msub(k,suba12,suba22),Msum(k,subb21,subb22));

        int[][] c11 = Msub(k,Msum(k,M1,M4),Msum(k,M5,M7));
        int[][] c12 = Msum(k,M3,M5);
        int[][] c21 = Msum(k,M2,M4);
        int[][] c22 = Msum(k,Msub(k,M1,M2),Msum(k,M3,M6));

        int[][] matrixC = merge_subM(k, c11, c12, c21, c22);
        return matrixC;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int[][] matrixA = init_matrix(n);
        int[][] matrixB = init_matrix(n);

        Main test = new Main();
        int[][] matrixC = test.Mmul(n,matrixA,matrixB);
        test.print_matrix(matrixA);
        System.out.println();
        test.print_matrix(matrixB);
        System.out.println();
        test.print_matrix(matrixC);
        System.out.println();
        int[][] matrixC2 = test.Strassen(n,matrixA,matrixB);
        test.print_matrix(matrixC2);
    }
}
```
