\mainmatter

# 文档展示 {#tidyverse-rmarkdown}

## Rmarkdown {#markdown-intro}

**(本篇为试行篇，日后将进一步丰富，将包括从package下载，project建立，Rmarkdown主题格式，插入图片，kable及kableExtra包插入优化表格，Rmarkdown导出)**

有时，我们需要**展示**我们的数据分析结果给他人，但是长篇的代码难以阅读，除了使用tidyverse减少代码长度外，我们同样可以将分析背景、分析过程、分析结果以及图表等形成**报告**，让他人能重复和验证我们的结果，确保结论的真实可信。 因此，本书开篇将会介绍如何生成分析报告。

## markdown 基本语法

markdown编写十分简单，例如


```markdown
# title

#  第一章
##  第一节

sentences.

```

常见的markdown语法包括：

::: {style="width:400px"}
| Type this...             | ...to get this         |
|--------------------------|------------------------|
| `normal text`            | normal text            |
| `*italic text*`          | *italic text*          |
| `**bold text**`          | **bold text**          |
| `***bold italic text***` | ***bold italic text*** |
| `e^2^`                   | e^2^                   |
| `~~strikethrough~~`      | ~~strikethrough~~      |
| `` `code ` ``            | `code`                 |
:::

### R代码块

一般通过 {R} 来插入，插入代码段的快捷键：win[Ctrl+Alt+I]

#### eval include echo与collapse 选项

eval参数控制运行与否，eval=FALSE , 可以使得代码仅显示而不实际运行。 这样的代码段如果有标签， 可以在后续代码段中被引用。 

include参数控制是否写入，include=FALSE ， 则本代码段仅运行， 但是代码和结果都不写入到生成的文档中。

echo参数控制了markdown是否显示代码块。若 echo=TRUE， 则表示代码块显示在 markdown 文档显示代码块；反之，代码块不出现在输出结果中。

collapse参数控制输出，markdown默认将一个代码块的代码、输出通常被分解为多个原样文本块中， 如果希望所有的代码、输出都写到同一个原样文本块中， 加选项 collapse=TRUE。


### 网页

如果想添加网页链接，可以用方括号和圆括号


```r
[Download R](http://www.r-project.org/)
```

[Download R](http://www.r-project.org/)

### 简单表格

如果想制作简单表格，列与列之间用 `|` 分隔，表格的首行下面添加`--------`


```r
Table Header  | Second Header
------------- | -------------
Cell 1, 1     | Cell 2, 1
Cell 1, 2     | Cell 2, 2
```

| Table Header | Second Header |
|--------------|---------------|
| Cell 1, 1    | Cell 2, 1     |
| Cell 1, 2    | Cell 2, 2     |

### 公式

如果要插入公式，可以在Rmarkdwon里输入 `$$\frac{\sum (\bar{x} - x_i)^2}{n-1}$$`，那么实际输出:

$$\frac{\sum (\bar{x} - x_i)^2}{n-1}$$

可以使用latex的等式环境， 比如

``` latex
$$a^{2}=b^{2}+c^{2}-2bc\cos A $$
$$f(x) = \int_{-\infty}^\infty  \hat f(x)\xi\,e^{2 \pi i \xi x}  \,\mathrm{d}\xi $$
```

得到

$$
 a^{2}=b^{2}+c^{2}-2bc\cos A 
$$ $$
 f(x) = \int_{-\infty}^\infty  \hat f(x)\xi\,e^{2 \pi i \xi x}  \,\mathrm{d}\xi
$$\

### 代码

想要运行代码


```r
summary(iris)
```

```
##   Sepal.Length    Sepal.Width     Petal.Length    Petal.Width   
##  Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100  
##  1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300  
##  Median :5.800   Median :3.000   Median :4.350   Median :1.300  
##  Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199  
##  3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800  
##  Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500  
##        Species  
##  setosa    :50  
##  versicolor:50  
##  virginica :50  
##                 
##                 
## 
```

### 表格与图片

输出表格与图片仅仅简单介绍，详细请阅读[《Rmarkdown 入门手册》]<https://cosx.org/2021/04/rmarkdown-introduction/>


````default

```{r tables-mtcars,  echo = F}
knitr::kable(iris[1:5, ], caption = "example0")
```

````


Table: (\#tab:tables-mtcars)example0

| Sepal.Length| Sepal.Width| Petal.Length| Petal.Width|Species |
|------------:|-----------:|------------:|-----------:|:-------|
|          5.1|         3.5|          1.4|         0.2|setosa  |
|          4.9|         3.0|          1.4|         0.2|setosa  |
|          4.7|         3.2|          1.3|         0.2|setosa  |
|          4.6|         3.1|          1.5|         0.2|setosa  |
|          5.0|         3.6|          1.4|         0.2|setosa  |


````default

```{r}
plot(iris)
```

````


<img src="01-Rmarkdown_files/figure-html/unnamed-chunk-7-1.png" width="85%" />
````


### 延申阅读

-   Rmarkdown 介绍 <https://bookdown.org/yihui/rmarkdown/>
-   Rmarkdown 手册 <https://bookdown.org/yihui/rmarkdown-cookbook/>
-   Rmarkdown 入门手册 <https://cosx.org/2021/04/rmarkdown-introduction/>
