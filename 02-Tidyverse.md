# Tidyverse {#tidyverse-intro}

## 简介

在介绍Tidyverse时，不得不提到开发者[**Hardley**](https://github.com/hadley)，ggplot2的简洁与易懂自不必多说，正如introduction所述，tidyverse是一系列R包的集合，包含了**dplyr、ggplot2、forcats、tibble、readr、tidyr、stringr、purrr**等，避免base-r所带来的冗长代码与数据分析者不懂算法而来的龟速运行，本章将花费约1个月时间完成对于tidyverse基本操作的介绍以及近几年出现的类似tidy流派package的简述，大致包括tidymodels、mlr3verse、rstatix、tidybayes、timetk、quanteda、tidybulk与sparklyr，如有时间进一步学习，将对未完成的mlr3torch文档进行部分解读。 
正如Hardley所讲，the main tools of data science is importing, tidying, transforming, and visualizing data.

<img src="./images/data science.png" width="50%" style="display: block; margin: auto auto auto 0;" />

本章将从import、tidy、transform、visualize和model分别介绍，其中import、tidy与transform将会在tidyverse基础操作中以详细案例讲解，并将会用表格列出所有function以便大家查询，实例以匹斯堡睡眠量表分数计算与r4ds实例进行讲解，对于已经熟悉tidy操作或暂时对此类操作不感兴趣的同学请直接跳转到visualize部分，本章visualize将会对ggplot2及其附加包进行讲解，但由于近期ggplot2的巨大改动可能会等待其功能稳定且我也同样熟练使用后进行梳理；model部分将单独作为statistic analysis出现，并介绍各类常用模型所需要的变量类型与使用条件，模型将会尽量囊括我们可能使用到的全部模型，如线性模型、Logistic回归（包括多分类）、Possion回归、Cox比例风险模型（包括时系变化Cox模型）、相关数据分析、嵌套数据分析、纵向数据分析及多分类数据分析，除此之外，还将会对bayes相关方法与机器学习内容进行详细的梳理，当然，这些大概是1个月后的事情。

## Import

本节将重点介绍如何将文件导入R，介绍读取单个文件及多个文件数据并合并成自己需要的数据集，所采用的案例为[r4ds](https://r4ds.had.co.nz)书中所写，对于多数为.csv格式文件的数据导入而言，整合在Tidyverse中的readr包可以很好的完成此项工作，除此之外，readxl适用于导入excel文件，haven包适合导入SAS、SPSS、Stata文件，xml2适用于导入xml文件，函数中的，下面表格列出常见文件的读取函数


| 文件格式             | **R** 函数                                    |
|:---------------------|:----------------------------------------------|
| .txt                 | `read.table()`                                |
| .Rdata or rda        | `load()`                                      |
| .csv                 | `readr::read_csv()`                           |
| .xls and .xlsx       | `readxl::read_excel()`                        |
| .sav(SPSS files)     | `haven::read_sav()`                           |
| .dta                 | `haven::read_dta()` and `haven::read_stata()` |
| .sas7bdat(SAS files) | `haven::read_sas()`                           |
| .rds                 | `readRDS()` and `readr::read_rds()`           |
| .xml                 | `read_RDS()` and `readr::read_rds()_xml`      |


在各函数()中需填写对应文件路径，如`read_csv("E:/data/SHHS1.csv")`,若文件在R的工作路径中，则可以简略写为`read_csv("./SHHS1.csv")`，若不确定路径则可以使用`here()`告诉我们当前所在的目录。当使用运行`read_csv()`时，它输出数据的行数和列数、使用的分隔符以及列名和列的数据类型，这些都可以帮我们很快的了解数据是否正确导入以及对数据有大致了解。我们这里就[r4ds](https://r4ds.hadley.nz/data-import)中的students数据集案例进行演示，读者可自行查看原版演示及讲解


```r
library(tidyverse)
```

```
## -- Attaching core tidyverse packages ------------------------ tidyverse 2.0.0 --
## v dplyr     1.1.4     v readr     2.1.4
## v forcats   1.0.0     v stringr   1.5.1
## v ggplot2   3.4.4     v tibble    3.2.1
## v lubridate 1.9.3     v tidyr     1.3.0
## v purrr     1.0.1     
## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
## i Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
```

```r
students <- read_csv("./data/students.csv")
```

```
## Rows: 6 Columns: 5
## -- Column specification --------------------------------------------------------
## Delimiter: ","
## chr (4): Full Name, favourite.food, mealPlan, AGE
## dbl (1): Student ID
## 
## i Use `spec()` to retrieve the full column specification for this data.
## i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

```r
students
```

```
## # A tibble: 6 x 5
##   `Student ID` `Full Name`      favourite.food     mealPlan            AGE  
##          <dbl> <chr>            <chr>              <chr>               <chr>
## 1            1 Sunil Huffmann   Strawberry yoghurt Lunch only          4    
## 2            2 Barclay Lynn     French fries       Lunch only          5    
## 3            3 Jayendra Lyne    N/A                Breakfast and lunch 7    
## 4            4 Leon Rossini     Anchovies          Lunch only          <NA> 
## 5            5 Chidiegwu Dunkel Pizza              Breakfast and lunch five 
## 6            6 Güven<U+00E7> Attila    Ice cream          Lunch only          6
```

## Tidy

待写

## Transform

待写
