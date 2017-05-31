新北市死亡車禍與測速照相機之關系 B0344140 王柏晧
================

分析議題背景
------------

新聞中最常看到的新聞是哪裡又發生了車禍，大多都是酒駕、超速、闖紅燈，而最主要的原因 還是車速過快，因此我們有設置測速照相機作為預防，但是真的有效果嗎?

分析動機
--------

我們平常一定會使用到交通工具，不想等車的一定會自己騎車或開車，而近年來馬路三寶的 人數越來越多，十次車禍有九次快，因此我想知道測速照相機的位置是否跟死亡車禍有相關 而且我本身也是通勤

使用資料
--------

我使用的是政府資料公開平台的新北市的測速照相位置和新北市104年度A1(死亡車禍)的資訊

載入使用資料們

``` r
#這是R Code Chunk
library(readr)
```

    ## Warning: package 'readr' was built under R version 3.3.3

``` r
accidentP <- read_csv("C:/Users/Blackcross/Downloads/accidentP.csv", 
    )
```

    ## Parsed with column specification:
    ## cols(
    ##   date = col_character(),
    ##   district = col_character(),
    ##   location = col_character(),
    ##   field1 = col_character(),
    ##   field2 = col_character(),
    ##   field3 = col_character()
    ## )

``` r
library(readr)
photoP <- read_csv("C:/Users/Blackcross/Downloads/photoP.csv", 
    )
```

    ## Parsed with column specification:
    ## cols(
    ##   district = col_character(),
    ##   location = col_character(),
    ##   limit = col_character(),
    ##   item = col_character(),
    ##   `location(all)` = col_character()
    ## )

資料處理與清洗
--------------

大多都先用Excel作整理 也沒有缺值

處理資料

``` r
#這是R Code Chunk
```

探索式資料分析
--------------

圖文並茂圖文並茂

``` r
#這是R Code Chunk
library(dplyr)
```

    ## Warning: package 'dplyr' was built under R version 3.3.3

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
accident<-group_by(accidentP,district)
summarise(accident,nlocation=n())%>%
arrange(desc(nlocation))
```

    ## # A tibble: 29 × 2
    ##    district nlocation
    ##       <chr>     <int>
    ## 1    中和區        11
    ## 2    板橋區        10
    ## 3    土城區         8
    ## 4    五股區         8
    ## 5    三峽區         7
    ## 6    汐止區         6
    ## 7    泰山區         6
    ## 8    新莊區         6
    ## 9    樹林區         6
    ## 10   八里區         5
    ## # ... with 19 more rows

``` r
photo<-group_by(photoP,district)
summarise(photo,nlocation=n())%>%
arrange(desc(nlocation))
```

    ## # A tibble: 28 × 2
    ##    district nlocation
    ##       <chr>     <int>
    ## 1    八里區        20
    ## 2    新店區        19
    ## 3    淡水區        18
    ## 4    林口區        17
    ## 5    板橋區        15
    ## 6    三峽區        13
    ## 7    土城區        13
    ## 8    瑞芳區        13
    ## 9    新莊區        12
    ## 10   樹林區        12
    ## # ... with 18 more rows

期末專題分析規劃
----------------

希望能加上酒駕、及其他事故的種類
