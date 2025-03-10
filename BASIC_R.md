R_BASIC
================

## Basic of R

<hr>
본 정리는 부산대학교 통계프로그래밍 수업 자료를 참고하여 작성
되었습니다.
<hr>

### 1. 통계 프로그래밍 소개.

(mac) opt + cmd + i =\> make code chunk.

#### R Packages

``` r
#install.packages("combinat")
library(combinat)
```

    ## 
    ## Attaching package: 'combinat'

    ## The following object is masked from 'package:utils':
    ## 
    ##     combn

``` r
combinat::permn(1:3) # Package_name :: function_name(arg)
```

    ## [[1]]
    ## [1] 1 2 3
    ## 
    ## [[2]]
    ## [1] 1 3 2
    ## 
    ## [[3]]
    ## [1] 3 1 2
    ## 
    ## [[4]]
    ## [1] 3 2 1
    ## 
    ## [[5]]
    ## [1] 2 3 1
    ## 
    ## [[6]]
    ## [1] 2 1 3

#### Operator

1.  Binary Operator

``` r
23 + 15
```

    ## [1] 38

``` r
23 - 15
```

    ## [1] 8

``` r
23 * 15
```

    ## [1] 345

``` r
23 / 15
```

    ## [1] 1.533333

``` r
2^3 # Power
```

    ## [1] 8

``` r
4 %% 2 # modulus
```

    ## [1] 0

``` r
4 %/% 2 # integer division
```

    ## [1] 2

2.  Comparison operator

- 두 값을 비교하고 그 결과로 논리값인 참 또는 거짓 값을 반환..
- ==, !=, \>, \<, \>=, \<=

3.  Logical operator

- and, or 연산자 ㅇㅇ
- ~, &, \|

##### Object assgining

``` r
x1 = factorial(5)
x1
```

    ## [1] 120

``` r
x1 + 120 
```

    ## [1] 240
