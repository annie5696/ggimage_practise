---
title: "Application 04"
author: "Anisha Shrestha"
date: "10/25/2019"
output: 
  html_document:
    keep_md: yes
---



```r
#### including BioC repo for dependencies
#install.packages("ggimage")

setRepositories(ind=1:2)
library(ggplot2)
library(ggimage)
library(ggtree)
```

```
## Registered S3 method overwritten by 'treeio':
##   method     from
##   root.phylo ape
```

```
## ggtree v1.16.6  For help: https://yulab-smu.github.io/treedata-book/
## 
## If you use ggtree in published research, please cite the most appropriate paper(s):
## 
## [36m-[39m Guangchuang Yu, Tommy Tsan-Yuk Lam, Huachen Zhu, Yi Guan. Two methods for mapping and visualizing associated data on phylogeny using ggtree. Molecular Biology and Evolution 2018, 35(12):3041-3043. doi: 10.1093/molbev/msy194
## [36m-[39m Guangchuang Yu, David Smith, Huachen Zhu, Yi Guan, Tommy Tsan-Yuk Lam. ggtree: an R package for visualization and annotation of phylogenetic trees with their covariates and other associated data. Methods in Ecology and Evolution 2017, 8(1):28-36, doi:10.1111/2041-210X.12628
```


##### What package are you using? State the name, whether it was on CRAN or GitHub, and provide the code you used for loading it.

> The package that I used here are: `ggimage`,  `ggplot`. It is on CRAN package. For loading it, I installed the package with `install.pacakages("ggimage")` and in order to do further exploration under this pacakage we also have to set repositories. For that I used, `setRepositories(ind=1:2)` . After the installation, I can simply run the libraries `library("ggplot2")`, `library("emoGG")`, `library(rsvg)`, `library(ggtree)` and `library("ggimage")`. `rsvg` library is used for rendering svg images. `emoGG` library render emoji picture (png) and creat a layer, geom_emoji , to add emoji.  `ggimage` supports image files and graphic objects to be visualized in `ggplot2` graphic system.

> The following object is masked from ‘package:ggimage’: (library("emoGG"))


##### What are you doing with the package? Provide a narrative including code and output.

> In this example, It is showing how to add an image to the plot. We can also add background image using `geom_bgimage` function. The data frames are generated randomly using rnorm with replacement. The link to images are passed in the sample. We can also define the image size.
> `size` help to adjust the size of the image. `size=1` and `rnorm= 1` shows the actual size of the image.



```r
set.seed(2017-02-21)
d <- data.frame(x = rnorm(10),
                y = rnorm(10),
                image = sample(c("https://www.r-project.org/logo/Rlogo.png",
                                 "https://jeroenooms.github.io/images/frink.png"),
                               size=10, replace = TRUE)
                )

ggplot(d, aes(x, y)) + geom_image(aes(image=image), size=.05)
```

![](Application-04_files/figure-html/unnamed-chunk-2-1.png)<!-- -->

> Similar as above replacing image in the image. Also Providing titles and axis to the graphs. 
> Aspect ratio and rnorm:  In order to keep control image size along with the grid and to randomly generate image in the plot.


```r
set.seed(2017-02-21)
example <- data.frame(x = rnorm(30),
                y = rnorm(30),
                image = sample(c("https://www.pngix.com/pngfile/big/17-170000_free-high-quality-cloud-rain-icon-transparent-background.png",
                                 
                                 "https://png2.cleanpng.com/sh/112318173171d4d8ad861cd68217c76e/L0KzQYm3V8ExN6d2f5H0aYP2gLBuTgBia15yedC2Y3BwgMb7hgIucZR0huU2Y3zsgH7okwQueJJohdN3LXnmf7B6TcVjPGY1fapvMUfkdoKBTskzQWo1SqU8MUW2QYO8UsM3P2EAT5D5bne=/kisspng-pac-man-computer-icons-clip-art-pacman-icons-5b450e8f17af18.929902331531252367097.png"),
                               size=10, replace = TRUE)) 
                ggplot(example, aes(x, y)) + geom_image(aes(image=image), size=.07)+labs(title= "Example 2 for Geom Image",y="Icon 1", x = "Icon 2")+theme_classic()
```

![](Application-04_files/figure-html/unnamed-chunk-3-1.png)<!-- -->
 

 >  one of `width` or `height` for specifying size. 


```r
ggplot(d, aes(x, y)) + geom_image(aes(image=image), size=.1, by='height')+labs(title= "Specifying size",
 y="Icon 1", x = "Icon 2")+ theme_classic()
```

![](Application-04_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

```r
ggplot(example, aes(x, y)) + geom_image(aes(image=image), size=.1, by='width')+labs(title= "Specifying size", y="Icon 1", x = "Icon 2")+ theme_classic()
```

![](Application-04_files/figure-html/unnamed-chunk-4-2.png)<!-- -->


> Showing Only one image



```r
ggplot(d, aes(x, y)) + geom_image(image=d$image[1])
```

![](Application-04_files/figure-html/unnamed-chunk-5-1.png)<!-- -->

```r
ggplot(example, aes(x, y)) + geom_image(image=example$image[1])
```

![](Application-04_files/figure-html/unnamed-chunk-5-2.png)<!-- -->




```r
d$size=seq(.05, .15, length.out=10)
ggplot(d, aes(x, y)) + geom_image(aes(image=image, size=I(size)))
```

![](Application-04_files/figure-html/unnamed-chunk-6-1.png)<!-- -->

```r
example$size=seq(.05, .15, length.out=10)
ggplot(example, aes(x, y)) + geom_image(aes(image=image, size=I(size)))
```

![](Application-04_files/figure-html/unnamed-chunk-6-2.png)<!-- -->



```r
ggplot(d, aes(x, y)) + geom_image(aes(image=image), color="firebrick")
```

![](Application-04_files/figure-html/unnamed-chunk-7-1.png)<!-- -->

> Exploratory Analysis


```r
ggplot(example, aes(x = x, y = 0.25, image = image)) + geom_image(size = 0.05, by="width") +scale_size_identity() +labs(title= "  ", y="Icon 1", x = "Icon 2")+ theme_minimal()
```

![](Application-04_files/figure-html/unnamed-chunk-8-1.png)<!-- -->


> Putting image inbetween the points. `images` \n
> We can simply specify the x & y aesthetics to locate the image into graphs and size will help with scaling if needed



```r
dta_img <- data.frame(x = 6, y = 3, image = 'https://www.r-project.org/logo/Rlogo.png')
ggplot(iris, aes(x = Sepal.Length, y = Petal.Length)) + 
  geom_image(data = dta_img, aes(x, y, image = image), size = 0.1) +
  geom_point()
```

![](Application-04_files/figure-html/unnamed-chunk-9-1.png)<!-- -->


> Geom Pokemon \n
> inheritParams geom_pokemon \n
> return ggplot2 layer \n
> aes= aes mapping \n
> This is getting the pokemon icon `pikachu` and `tauros`.



```r
ggplot(d, aes(x, y)) + geom_pokemon(aes(image=ifelse(x>0, 'pikachu', 'tauros')), size=.2)
```

![](Application-04_files/figure-html/unnamed-chunk-10-1.png)<!-- -->





```r
#Example for Pokemon

set.seed(2018-12-11)
df  <-  data.frame(x=1:10, y=1:10,
                  type = sample(LETTERS[1:3], 10, replace=T),
                  angle = runif(10, 0, 360))

options(ggimage.keytype = "point")
ggplot(df, aes(x, y, colour=type, angle=angle)) +
    geom_pokemon(aes(image=ifelse(x>5, 'pikachu', 'tauros')))
```

![](Application-04_files/figure-html/unnamed-chunk-11-1.png)<!-- -->

```r
options(ggimage.keytype = "rect")
ggplot(df, aes(x, y, colour=type, angle=angle)) +
    geom_pokemon(aes(image=ifelse(x>5, 'pikachu', 'tauros')))
```

![](Application-04_files/figure-html/unnamed-chunk-11-2.png)<!-- -->






> This code below only plots one emoji in a plot. \n
> this shows how we can embeed different emojis in R code chunks



```r
set.seed(123)
iris2 <- iris[sample(1:nrow(iris), 30),]
model <- lm(Petal.Length ~ Sepal.Length, data=iris2)
iris2$fitted <- predict(model)

ggplot(iris2, aes(x = Sepal.Length, y = Petal.Length)) +
  geom_linerange(aes(ymin = fitted, ymax = Petal.Length),
                 colour = "purple") +
  geom_abline(intercept = model$coefficients[1],
              slope = model$coefficients[2]) +
    geom_emoji(aes(image = ifelse(abs(Petal.Length-fitted) > 0.5, '1f622', '1f600')))
```

![](Application-04_files/figure-html/unnamed-chunk-12-1.png)<!-- -->




> geom_flag \n
> geom layer for using flag image \n
> title geom_flag \n
> return flag vector \n
> scale fill mannual values shows three types of medel with respective color. \n
> The `ggimage package` is able to create a geom layer for an image. A dataframe with all the country's flag and count are stored in `f` and then in the geom_flag() function specifies the image argument.


```r
f <- system.file("extdata/medals.txt", package="ggimage")
medals <- read.table(f, header=TRUE)
p <- ggplot(medals, aes(Country, count)) + geom_col(aes(fill = medal), width = .8)

p + geom_flag(y = -2, aes(image = code)) +
    coord_flip() + expand_limits(y = -2)  +
    scale_fill_manual(values = c("Gold" = "gold", "Bronze" = "#cd7f32", "Silver" = "#C0C0C0"))+labs(title= "Geom Layer For using Flag Image")+ theme_minimal()
```

![](Application-04_files/figure-html/unnamed-chunk-13-1.png)<!-- -->

> geom_icon \n
> Here, we have used rsvg library, and plotted 3 icon with replacement.


```r
library(rsvg)
d$icon=sample(c('ios-power', 'ios-wifi', 'ios-pie'), 10, replace=TRUE)
ggplot(d, aes(x,y)) + geom_icon(aes(image=icon))
```

![](Application-04_files/figure-html/unnamed-chunk-14-1.png)<!-- -->




```r
library(tibble)
dd <- data.frame(x=LETTERS[1:3], y=1:3)
pie <- ggplot(dd, aes(x=1, y, fill=x)) + geom_bar(stat="identity", width=1) + coord_polar(theta="y") +
    theme_void() + theme(legend.position="none") + theme_transparent()

df <- data_frame(x = sample(2:9),
                 y = sample(2:9),
                 width = sample(seq(0.5, 3, length.out=length(x))),
                 pie = list(pie))
```

```
## Warning: `data_frame()` is deprecated, use `tibble()`.
## This warning is displayed once per session.
```

 > geom_subview \n
 > title geom_subview \n
 > importFrom ggplot2 annotation_custom \n
 > x position of subview. This parameter works if mapping and data is not provided \n
 > y position of subview. This parameter works if mapping and data is not provided \n
 > subview to plot, if not provided in data and specify by mapping


```r
p <- ggplot(data=data.frame(x=c(0, 10), y=c(0, 10)), aes(x, y))+geom_blank()
p + geom_subview(aes(x=x, y=y, subview=pie, width=width, height=width), data=df)
```

![](Application-04_files/figure-html/unnamed-chunk-16-1.png)<!-- -->


> geom layer for using Twitch emotes


```r
set.seed(1)
x <- 1:10
y <- x + rnorm(10, sd = 1)
notlikethis <- data.frame(x = x, y = y)
n_pals      <- 200
pals        <- data.frame(
  x = runif(n_pals, -2, 12), y = runif(n_pals, -2, 12),
  pal = sample(c("wutface", "kappa", "pogchamp"), size = n_pals, replace = TRUE)
)

ggplot(notlikethis, aes(x = x, y = y)) +
  geom_twitchemote(data = pals,
                   aes(image = 'pogchamp'), size = 0.03, alpha = 0.3) +
  geom_twitchemote(aes(image = 'notlikethis'), size = 0.15) +
  geom_smooth()
```

```
## `geom_smooth()` using method = 'loess' and formula 'y ~ x'
```

![](Application-04_files/figure-html/unnamed-chunk-17-1.png)<!-- -->


> The layers defined in ggimage can be directly applied to ggtree to annotate phylogenetic tree using local/online image files. \n
> query phylopic to get `uid` from scientific name: phylopic_uid() \n
> This function reads a file which contains one or several trees in parenthetic format known as the Newick or New Hampshire format. \n
> Uses the viridis color scale. \n
> add tip label layer: geom_tiplab , arguement like, linetype, linesize, ajust etc.



```r
newick <- "((Pongo_abelii,(Gorilla_gorilla_gorilla,(Pan_paniscus,Pan_troglodytes)Pan,Homo_sapiens)Homininae)Hominidae,Nomascus_leucogenys)Hominoidea;"

tree <- read.tree(text=newick)

idlist <- ggimage::phylopic_uid(tree$tip.label)
ids <- sapply(idlist, function(x) x[1,1])

d <- data.frame(label = tree$tip.label, uid = ids, 
                body_mass = c(52, 114, 47, 45, 58, 6))

p <- ggtree(tree) %<+% d + 
  geom_tiplab(aes(image=uid, colour=body_mass), geom="phylopic", offset=2.5) +
  geom_tiplab(aes(label=label), offset = .2) + xlim(NA, 7) +
  scale_color_viridis_c()
p
```

![](Application-04_files/figure-html/unnamed-chunk-18-1.png)<!-- -->



> ggtree provides a layer, geom_inset, for adding subplots to a phylogenetic tree. The input is a named list of ggplot graphic objects (can be any kind of charts). These objects should named by node numbers. Users can also use ggplotify to convert plots that generated by other functions (even implemented by base graphics) to ggplot objects, which can then be used in geom_inset.
 
 















