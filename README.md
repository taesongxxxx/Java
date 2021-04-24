# 컴퓨터 알고리즘

## 중간고사: *Strassen Algorithm* 설명 및 코드구현, 성능분석

## 1. *Strassen Algorithm?*
- ***Strassen Algorithm*** **은 행렬 곱셈 알고리즘으로 정의에 따라 두 행렬의 곱을 이용하면 ![CodeCogsEqn (1)](https://user-images.githubusercontent.com/82091824/115876342-26957e80-a481-11eb-887c-efc0b27350dd.gif)의 시간이 소모지만, 이 알고리즘을 이용하면 대략 ![CodeCogsEqn (1)](https://user-images.githubusercontent.com/82091824/115876522-62304880-a481-11eb-9ce5-d29a375b6247.gif)의 시간 복잡도가 걸린다.**

### (1) 기본 *Algorithm*을 이용한 행렬 곱
<br><p align="center"><img src="https://user-images.githubusercontent.com/82091824/115886929-601fb700-a48c-11eb-9b04-113a20819ce2.gif"></p><br>
    
<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115892111-ceb34380-a491-11eb-9c56-925150cd7399.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115887747-331fd400-a48d-11eb-9d28-8bce60085689.gif"></p>
   
<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115887891-55195680-a48d-11eb-8970-9c36c787898e.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115888071-78440600-a48d-11eb-8d55-032b2ca2db1b.gif"></p>

<p align="center"><img src="https://user-images.githubusercontent.com/82091824/115888168-94e03e00-a48d-11eb-817a-71cf9abc2f7e.gif"></p><br/>

- **위 알고리즘으로 행렬의 곱을 계산하면 과정에서 8번의 곱셈연산과 4번의 덧셈연산이 일어난다.**   
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

- **기본 *Algorithm*으로 계산시 8번의 곱셈연산과 4번의 덧셈연산이 일어나는 반면, Strassen Algorithm을 이용하면 7번의 곱셈연산과 18번의 덧셈연산이 일어난다. 행렬이 커지면 일반적으로 곱셈보다는 덧셈의 연산속도가 더 빠르므로 행렬의 크기가 커질수록 *Strassen Algorithm* 의 효율이 좋아진다.**    
   
- **위 과정을 재귀적으로 반복할 경우 ![CodeCogsEqn (29)](https://user-images.githubusercontent.com/82091824/115904518-d548b780-a49f-11eb-8236-ddb0b383eaf6.gif) 번의 연산이 필요하다.  ![CodeCogsEqn (30)](https://user-images.githubusercontent.com/82091824/115904895-4d16e200-a4a0-11eb-875d-1ef0ac6b3504.gif) 이므로, 시간복잡도는 약  ![CodeCogsEqn (1)](https://user-images.githubusercontent.com/82091824/115876522-62304880-a481-11eb-9ce5-d29a375b6247.gif) 이다**

## 2. 코드설명
(1) **행렬 값 입력 *Method***
```java
    public static int[][] init_matrix(int n){
        int [][] matrix = new int[n][n];
        Random random = new Random();
        for(int i=0; i<n; i++)
            for(int j=0; j<n; j++)
                matrix[i][j] = random.nextInt(10);
        return matrix;
    }
```
(2) **행렬 값 출력 *Method***
```java
    void print_matrix(int[][] matrix){
        for(int i=0; i<matrix.length; i++) {
            for (int j = 0; j < matrix[0].length; j++) {
                System.out.printf("%d ", matrix[i][j]);
            }
            System.out.println();
        }
    }
```
(3) **행렬 분할 *Method***
```java
 public int[][] subM(int[][] matrix, int a, int b,int n){
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
```
(4) **행렬 *Merge* *Method***
```java
 public int[][] merge_subM(int n, int[][] c11, int[][] c12, int[][] c21, int[][] c22){
        n= c11.length;
        int[][] mergeM = new int[2*n][2*n];
        for(int i=0; i<n; i++){
            for(int j=0; j<n; j++) {
                mergeM[i][j] = c11[i][j];
                mergeM[i][j+n] = c12[i][j];
                mergeM[i+n][j] = c21[i][j];
                mergeM[i+n][j+n] = c22[i][j];
            }
        }
        return mergeM;
```
(5) **행렬 곱셈 *Method***
```java
    public int[][] Mmul(int[][] matrixA, int[][] matrixB){
        int n = matrixA.length;
        int[][] Mmul = new int[n][n];
        for(int i=0; i<n; i++){
            for(int j=0; j<n; j++){
                for(int k=0; k<n; k++){
                    Mmul[i][j] += matrixA[i][k]*matrixB[k][j];
                }
            }
        }
        return Mmul;
```
(6) **행렬 덧셈 *Method***
```java
   public int[][] Msum(int[][] matrixA, int[][] matrixB){
        int n = matrixA.length;
        int[][] Msum = new int[n][n];
        for(int i=0; i<n; i++)
            for(int j=0; j<n; j++){
                Msum[i][j] = matrixA[i][j]+matrixB[i][j];
            }
        return Msum;
    }
```
(7) **행렬 뺄셈 *Method***
```java
    public int[][] Msub(int[][] matrixA, int[][] matrixB){
        int n = matrixA.length;
        int[][] Msub = new int[n][n];
        for(int i=0; i<n; i++)
            for(int j=0; j<n; j++){
                Msub[i][j] = matrixA[i][j]-matrixB[i][j];
            }
        return Msub;
```
(8) ***Strassen Algortihm***
```java
    public int[][] Strassen(int n, int[][] matrixA, int[][] matrixB){

        if(n < 2){
            int[][] matrixC = Mmul(matrixA,matrixB);
            return matrixC;
        }

        int[][] suba11 = subM(matrixA,0,0,n/2);
        int[][] suba12 = subM(matrixA,0,n/2,n/2);
        int[][] suba21 = subM(matrixA,n/2,0,n/2);
        int[][] suba22 = subM(matrixA,n/2,n/2,n/2);

        int[][] subb11 = subM(matrixB,0,0,n/2);
        int[][] subb12 = subM(matrixB,0,n/2,n/2);
        int[][] subb21 = subM(matrixB,n/2,0,n/2);
        int[][] subb22 = subM(matrixB,n/2,n/2,n/2);

        int[][] M1 = Strassen(n/2,Msum(suba11,suba22),Msum(subb11,subb22));
        int[][] M2 = Strassen(n/2,Msum(suba21,suba22),subb11);
        int[][] M3 = Strassen(n/2,suba11,Msub(subb12,subb22));
        int[][] M4 = Strassen(n/2,suba22,Msub(subb21,subb11));
        int[][] M5 = Strassen(n/2,Msum(suba11,suba12),subb22);
        int[][] M6 = Strassen(n/2,Msub(suba21,suba11),Msum(subb11,subb12));
        int[][] M7 = Strassen(n/2,Msub(suba12,suba22),Msum(subb21,subb22));

        int[][] c11 = Msum(Msub(Msum(M1,M4),M5),M7);
        int[][] c12 = Msum(M3,M5);
        int[][] c21 = Msum(M2,M4);
        int[][] c22 = Msum(Msub(Msum(M1,M3),M2),M6);

        int[][] matrixC = merge_subM(n/2, c11, c12, c21, c22);
        return matrixC;
    }

```
(9) ***Debugging***
- ***n*값이 ![CodeCogsEqn (31)](https://user-images.githubusercontent.com/82091824/115957892-0678c480-a540-11eb-8109-8312954becfe.gif) 형태일때만 제대로 된 값이 출력되고, 그 외에는 이상한 값이 뜨거나 에러 발생..   
 *ex)*
``` java
n = 10

행렬 A                    행렬 B
1 0 9 3 3 9 3 5 5 8       5 3 6 4 4 7 9 1 3 8 
9 7 4 8 6 5 4 8 5 5       6 4 4 9 0 3 5 7 7 0 
2 1 1 8 0 0 9 4 9 4       2 6 9 1 8 1 1 0 1 4
2 3 1 0 9 8 4 4 2 9       9 7 3 4 3 7 1 4 4 6 
9 6 3 8 5 8 4 2 8 8       6 6 5 8 0 7 8 7 5 7 
7 8 8 8 9 9 3 2 4 8       0 3 6 1 4 0 3 8 9 5 
0 4 5 5 7 9 2 9 8 2       6 1 3 0 9 5 5 2 9 8 
5 7 9 7 8 6 6 4 5 7       9 8 2 8 9 1 6 3 7 7
1 3 5 2 6 7 6 5 3 0       3 6 2 6 0 8 1 4 2 5 
5 1 4 9 5 2 1 1 9 5       3 1 3 5 4 9 2 8 4 0 

A*B 기본 Algorithm
170 204 218 168 225 190 138 211 224 212 
329 289 255 307 240 299 274 264 309 316 
219 171 114 156 173 231 118 139 189 213 
177 159 177 205 156 208 194 250 249 193 
279 255 258 277 202 333 242 292 299 293 
297 289 314 301 229 321 265 322 324 302 
244 274 211 256 198 202 189 248 274 263 
304 287 293 287 255 307 251 286 315 305 
177 180 175 157 177 136 163 167 225 215 
207 210 172 198 125 263 139 180 159 215 

A*B Strassen Algorithm
128 178 179 104 97 98 126 177 
278 248 210 234 212 216 182 259 
207 167 102 136 195 110 107 173 
96 96 105 88 64 104 115 168 
219 227 245 189 186 177 195 247 
196 230 170 190 135 129 183 231 
235 232 232 188 188 173 174 247 
141 144 145 109 94 115 125 195 

```
- **문제점**

## 3. 성능비교

## 4. 결론

## 5. 전체 코드
```java

```
