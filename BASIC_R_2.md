BASIC_R_2
================

## Basic of R 2

### Create Random Samples

- `sample()`, `distribution()` 함수를 이용한다.

#### Sample function

- `sample()` 함수는 벡터 또는 리스트의 요소 중 n개를 선택하고 추출하는
  함수이다.

<!-- -->

    sample(x, size, replace = TRUE, prob = NULL)

- x : 벡터 또는 리스트
- size : 추출할 갯수
- replace : 비복원(False) 또는 복원(TRUE)의 선택
- prob : 추출할 확률

``` r
sample(x = 1:10)
```

    ##  [1]  9  8 10  6  7  1  4  5  3  2

``` r
sample(x = 1:10, size = 5)
```

    ## [1]  5 10  7  3  2

``` r
sample(x = 1:10, size = 5, replace = TRUE)
```

    ## [1] 4 4 3 8 6

``` r
sample(x = c(1:4), size = 1, prob = c(0.1, 0.2, 0.3, 0.4)) # element wise하게 각 숫자에 확률 부여
```

    ## [1] 2

``` r
s = sample(1:365, 45, replace = TRUE)
s
```

    ##  [1] 314 127 130 296  70 292  85 158 255 326 363 155 229 150   7 254 241 108 365
    ## [20] 312   6 154 317 321 137 129 125  20 242 249  84 162 172 312 113 222 145  43
    ## [39] 256  82 157 263 131 100 110

``` r
unique(s)
```

    ##  [1] 314 127 130 296  70 292  85 158 255 326 363 155 229 150   7 254 241 108 365
    ## [20] 312   6 154 317 321 137 129 125  20 242 249  84 162 172 113 222 145  43 256
    ## [39]  82 157 263 131 100 110

``` r
duplicated(s)
```

    ##  [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [13] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [25] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE
    ## [37] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE

``` r
s[duplicated(s)]
```

    ## [1] 312

#### Distribution Functions

1.  `r` : 난수 생성
2.  `d` : 밀도 함수
3.  `p` : 누적 밀도 함수
4.  `q` : 분위수 함수

``` r
# 난수 생성
rnorm(n = 5, mean = 0, sd = 1)
```

    ## [1] -0.9898199  0.3339789  0.3309123 -0.3816625  0.1717242

``` r
rbinom(n = 10, size = 5, prob = 0.5)
```

    ##  [1] 3 2 3 1 3 3 1 1 2 2

``` r
rchisq(n = 3, df = 10)
```

    ## [1] 13.844718  6.982603 13.358749

``` r
# 밀도 함수(밀도 함수값을 출력...)
dnorm(x = 0, mean = 0, sd = 1)
```

    ## [1] 0.3989423

``` r
dnorm(x = 3, mean = 0, sd = 1)
```

    ## [1] 0.004431848

``` r
dnorm(x = -3, mean = 0, sd = 1)
```

    ## [1] 0.004431848

``` r
# 누적 밀도 함수(적분값)
pnorm(0, mean = 0, sd = 1)
```

    ## [1] 0.5

``` r
pnorm(-3, mean = 0, sd = 1)
```

    ## [1] 0.001349898

``` r
pnorm(3, mean = 0, sd = 1)
```

    ## [1] 0.9986501

``` r
1 - pnorm(-3, mean = 0, sd = 1)
```

    ## [1] 0.9986501

``` r
pnorm(1.96, mean = 0, sd = 1)
```

    ## [1] 0.9750021

``` r
pnorm(-1.96, mean = 0, sd = 1)
```

    ## [1] 0.0249979

``` r
# 분위수(누적값을 주면 그에 해당하는 x 값 출력)
qnorm(0.975, mean = 0, sd = 1)
```

    ## [1] 1.959964

``` r
qnorm(0.025, mean = 0, sd = 1)
```

    ## [1] -1.959964

### 조건문

- 뭐이건…그냥 꼴만알면 되고 그 이후는 능지 문제죠..?
- if - else 구문 쓸 떄 else 붙혀쓰는것만 조심핮.

``` r
# ex1

x = 24
if (x == 3){
  print("x is 3")
}else{
  print("x is not 3")
}
```

    ## [1] "x is not 3"

``` r
# 이 예제만 보면 대충 느낌오쥬?

if (x < 10){
  print("x is less than 10")
}else if(x < 20){
  print("x is less than 20")
}else if(x < 30){
  print("x is less than 30")
}else{
  print("x is greater than or equal to 30")
}
```

    ## [1] "x is less than 30"

- `if(cond) expr1 else expr2` -\> `ifelse()` 사용하자..!
  - 약간 뭐랄까 벡터,메트릭스, 데이터프레임 안에 있는 값을 치환해줄때
    야무지게 쓸 수 있는 느낌??

``` r
x = seq(0, 2, length.out = 6)
x
```

    ## [1] 0.0 0.4 0.8 1.2 1.6 2.0

``` r
ifelse(x <= 1, "small", "big")
```

    ## [1] "small" "small" "small" "big"   "big"   "big"

``` r
y = matrix(1:8, nrow = 2)
y
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    3    5    7
    ## [2,]    2    4    6    8

``` r
ifelse(y > 3 & y < 7, 1, 0)
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    0    0    1    0
    ## [2,]    0    1    1    0

``` r
z = data.frame(
  "A" = c(1,2,3,4),
  "B" = c(1, 2, 3, 4),
  "C" = c(5,6,7,8)
)
z
```

    ##   A B C
    ## 1 1 1 5
    ## 2 2 2 6
    ## 3 3 3 7
    ## 4 4 4 8

``` r
ifelse(z > 3 & z < 7, 1, 0) # matrix로 출력된다.
```

    ##      A B C
    ## [1,] 0 0 1
    ## [2,] 0 0 1
    ## [3,] 0 0 0
    ## [4,] 1 1 0

``` r
as.data.frame(ifelse(z > 3 & z < 7, 1, 0))
```

    ##   A B C
    ## 1 0 0 1
    ## 2 0 0 1
    ## 3 0 0 0
    ## 4 1 1 0

#### 조건문

``` r
fac = NULL # 빈리스트, 자료형을 만드는 것과 동일한 작업
f = 1
for (i in 1:10){
  f = f * i
  fac[i] = f
  print(f)
}
```

    ## [1] 1
    ## [1] 2
    ## [1] 6
    ## [1] 24
    ## [1] 120
    ## [1] 720
    ## [1] 5040
    ## [1] 40320
    ## [1] 362880
    ## [1] 3628800

``` r
fac
```

    ##  [1]       1       2       6      24     120     720    5040   40320  362880
    ## [10] 3628800
