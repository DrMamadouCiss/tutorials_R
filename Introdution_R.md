Introduction au logiciel R
================
Dr Mamadou Ciss
14 janvier 2019

-   [Environnement de travail](#environnement-de-travail)
    -   [Connaitre son repertoire de travail actuel](#connaitre-son-repertoire-de-travail-actuel)
    -   [Changer de repertoire de travail](#changer-de-repertoire-de-travail)
-   [Les packages sous R](#les-packages-sous-r)
    -   [Installation de package](#installation-de-package)
    -   [Telechargement de package](#telechargement-de-package)
-   [Importation de donnees](#importation-de-donnees)
    -   [Donnees texte simple](#donnees-texte-simple)
    -   [Donnees au format CSV](#donnees-au-format-csv)
-   [Representation de donnees sous R](#representation-de-donnees-sous-r)
    -   [Entete d'un fichier](#entete-dun-fichier)
    -   [Fin d'un fichier](#fin-dun-fichier)
-   [Statistiques basiques d'une base donnees](#statistiques-basiques-dune-base-donnees)
    -   [Taille d'un fichier](#taille-dun-fichier)
    -   [Nombre de lignes d'un fichier](#nombre-de-lignes-dun-fichier)
    -   [Nombre de colonnes d'un fichier](#nombre-de-colonnes-dun-fichier)
    -   [Longueur d'un vecteur](#longueur-dun-vecteur)
    -   [Sommaire de la base de donnees](#sommaire-de-la-base-de-donnees)
    -   [Moyenne d'un vecteur](#moyenne-dun-vecteur)
    -   [Minimum d'un vecteur](#minimum-dun-vecteur)
    -   [Maximum d'un vecteur](#maximum-dun-vecteur)
    -   [Somme d'un vecteur](#somme-dun-vecteur)
    -   [Variance d'un vecteur](#variance-dun-vecteur)
    -   [Ecart-type d'un vecteur](#ecart-type-dun-vecteur)

Environnement de travail
------------------------

### Connaitre son repertoire de travail actuel

    getwd()

### Changer de repertoire de travail

``` r
setwd("C:/Users/hp/Google Drive/ISRA/Formation/Dispensees/R/Test_Rmarkdown")
```

Les packages sous R
-------------------

### Installation de package

    install.packages('ggplot2')

### Telechargement de package

    library('ggplot2')

Importation de donnees
----------------------

### Donnees texte simple

``` r
myfile<-read.table("pheno.txt",h=T,dec=".")
```

### Donnees au format CSV

``` r
myfile2<-read.csv2("fwsd.csv",h=T,dec=".")
```

Representation de donnees sous R
--------------------------------

### Entete d'un fichier

``` r
head(myfile)
```

    ##   Populations Floraison Poids_sec Nb_involucres Poids_graines
    ## 1        pop1        28         8            15          3.22
    ## 2        pop1        29        10            21          2.56
    ## 3        pop1        29         8            18          2.79
    ## 4        pop1        28        10            16          2.65
    ## 5        pop1        32         9            17          2.51
    ## 6        pop1        34         9            18          2.75

``` r
head(myfile,n=3)
```

    ##   Populations Floraison Poids_sec Nb_involucres Poids_graines
    ## 1        pop1        28         8            15          3.22
    ## 2        pop1        29        10            21          2.56
    ## 3        pop1        29         8            18          2.79

### Fin d'un fichier

``` r
tail(myfile)
```

    ##     Populations Floraison Poids_sec Nb_involucres Poids_graines
    ## 505      pop_17        23        13            17          1.91
    ## 506      pop_17        30        12             7          1.33
    ## 507      pop_17        25        11            15          1.62
    ## 508      pop_17        28         8            10          1.28
    ## 509      pop_17        27        12            16          1.23
    ## 510      pop_17        26        13            11          0.60

``` r
tail(myfile,n=2)
```

    ##     Populations Floraison Poids_sec Nb_involucres Poids_graines
    ## 509      pop_17        27        12            16          1.23
    ## 510      pop_17        26        13            11          0.60

Statistiques basiques d'une base donnees
----------------------------------------

### Taille d'un fichier

``` r
dim(myfile)
```

    ## [1] 510   5

``` r
names(myfile)
```

    ## [1] "Populations"   "Floraison"     "Poids_sec"     "Nb_involucres"
    ## [5] "Poids_graines"

``` r
colnames(myfile)
```

    ## [1] "Populations"   "Floraison"     "Poids_sec"     "Nb_involucres"
    ## [5] "Poids_graines"

### Nombre de lignes d'un fichier

``` r
nrow(myfile)
```

    ## [1] 510

### Nombre de colonnes d'un fichier

``` r
ncol(myfile)
```

    ## [1] 5

### Longueur d'un vecteur

``` r
length(myfile$Poids_sec)
```

    ## [1] 510

### Sommaire de la base de donnees

``` r
summary(myfile)
```

    ##   Populations    Floraison       Poids_sec     Nb_involucres  
    ##  pop_10 : 30   Min.   :11.00   Min.   : 1.00   Min.   : 1.00  
    ##  pop_11 : 30   1st Qu.:21.00   1st Qu.: 9.00   1st Qu.:10.00  
    ##  pop_12 : 30   Median :25.00   Median :11.00   Median :15.00  
    ##  pop_13 : 30   Mean   :25.75   Mean   :10.95   Mean   :14.76  
    ##  pop_14 : 30   3rd Qu.:31.00   3rd Qu.:13.00   3rd Qu.:19.00  
    ##  pop_15 : 30   Max.   :41.00   Max.   :22.00   Max.   :29.00  
    ##  (Other):330                                                  
    ##  Poids_graines  
    ##  Min.   :0.420  
    ##  1st Qu.:1.740  
    ##  Median :2.300  
    ##  Mean   :2.277  
    ##  3rd Qu.:2.780  
    ##  Max.   :4.530  
    ##  NA's   :1

``` r
str(myfile)
```

    ## 'data.frame':    510 obs. of  5 variables:
    ##  $ Populations  : Factor w/ 17 levels "pop_10","pop_11",..: 11 11 11 11 11 11 11 11 11 11 ...
    ##  $ Floraison    : int  28 29 29 28 32 34 27 30 27 32 ...
    ##  $ Poids_sec    : int  8 10 8 10 9 9 4 9 13 11 ...
    ##  $ Nb_involucres: int  15 21 18 16 17 18 16 15 17 20 ...
    ##  $ Poids_graines: num  3.22 2.56 2.79 2.65 2.51 2.75 3.49 2.88 2.27 3.07 ...

``` r
myfile[2,]
```

    ##   Populations Floraison Poids_sec Nb_involucres Poids_graines
    ## 2        pop1        29        10            21          2.56

``` r
myfile[,3]
```

    ##   [1]  8 10  8 10  9  9  4  9 13 11  9 11  9 10 12  6 10 11  9 10  9  9 16
    ##  [24] 11  8  8 12  9 11  9 11 13  8  8  8  8 12  8 13  7  6  9  7  8 11  6
    ##  [47]  9 12  3  9  9 10  8  9 11  9 12 13  8  9 11  7 11 12 13  7 12  8 11
    ##  [70] 10  7 15  5  9 11 12 19 10 12  9  4 11 14  6 12 12 10 12  9 11 16 17
    ##  [93]  8 11 10  6 12  9 12 12 13  9 12 14  5  9  1  7  6  6  6 11 15 10  6
    ## [116]  8 12  2  8  9 10 16  9 14 11 14 12 10  9  6  6 12 11 13 17  9 13 13
    ## [139] 10  9 17  8  5 13 11 10 15  9 10 13 17 13 13 10 11  6 14 10 13 13  9
    ## [162] 15 15  4 12 18  6  9 12 11 10 11 10 12 14 16 11 15 16 11 16 12 14 15
    ## [185] 20 10 12 13 15 15 20 16 14 19 19 14 17 13 15 22 17 12 18 18 19 20 15
    ## [208] 16 14 16  9  8 15  9  8 15 13 15  9 10 10  8  9 10  7 13 12 12 18 12
    ## [231] 13 11 13  6  8 16 14 10  8  4 13  8  7  6 16 10 12  3  6  9 10 15 11
    ## [254]  5 12 10  5  9 12 12 12  8 12  8 13  8 13 14 17  9  6  9 10  9  3 10
    ## [277] 10  9  8 12 11  8 11  5  8  9  8  6  1 10  2  5 12  9 14  9 15  9  8
    ## [300]  9 15 10  8 12 11 11 16 12 10 10 13  9  8 13 14 13  7  7 15 17 13 12
    ## [323] 11 13 13 13 11 10 11  8  7 10  9 13 11 10  9  8 13 10 16 12  6  7 12
    ## [346] 12 12 12 16 11 14  9 11 14 10 12 14  7  9  9 13 12 14  7  9 13  9 11
    ## [369] 14  8  8  8 15 12  9  7 10 11 13  8 11  9  8 11 16  9  7  8 17  8 15
    ## [392]  7  7 11 13 12 10 14 14 10 13  7 12 12  5 16 13 10 14 14 10 14  9 10
    ## [415] 11 14 12 12 14  7 13 16 17 13 18 15 16 14 16 13 15 19 18 17 10 16 13
    ## [438] 21 11 17 12 13 20 13 18 14 16 13 10 16 10 10 10  7  7  6 11  8 11  8
    ## [461]  9  8  7 12  6  8  8  8 11  9  8 10  9  7 12 11 12  7 11  9 13 12 15
    ## [484] 10 14 11  9  6 15  4 18 10 12 12 10  7  8  5 15 12  8 10 11  8 13 12
    ## [507] 11  8 12 13

``` r
myfile[1,5]
```

    ## [1] 3.22

``` r
myfile[2:4,]
```

    ##   Populations Floraison Poids_sec Nb_involucres Poids_graines
    ## 2        pop1        29        10            21          2.56
    ## 3        pop1        29         8            18          2.79
    ## 4        pop1        28        10            16          2.65

``` r
myfile[c(2,4),]
```

    ##   Populations Floraison Poids_sec Nb_involucres Poids_graines
    ## 2        pop1        29        10            21          2.56
    ## 4        pop1        28        10            16          2.65

``` r
myfile[c(2,4),5]
```

    ## [1] 2.56 2.65

Les commandes `max(x)`, `min(x)`, `range(x)`, `sum(x)`, `diff(x)`, `prod(x)`, `mean(x)`, `median(x)` et `sd(x)` fournissent le maximum, minimum, amplitude, somme, différences, produit, moyenne, médiane et écart-type des données. Afin de considérer les données manquantes, il est nécessaire d'y inclure `na.rm = TRUE`.

### Moyenne d'un vecteur

``` r
mean(myfile$Nb_involucres)
```

    ## [1] 14.76471

### Minimum d'un vecteur

``` r
min(myfile$Poids_graines)
```

    ## [1] NA

``` r
min(myfile$Poids_graines,na.rm = TRUE)
```

    ## [1] 0.42

``` r
mean(myfile$Nb_involucres,na.rm = TRUE)
```

    ## [1] 14.76471

### Maximum d'un vecteur

``` r
max(myfile$Floraison)
```

    ## [1] 41

### Somme d'un vecteur

``` r
sum(myfile$Poids_graines)
```

    ## [1] NA

``` r
sum(myfile$Poids_graines,na.rm = TRUE)
```

    ## [1] 1158.98

### Variance d'un vecteur

``` r
var(myfile$Poids_graines)
```

    ## [1] NA

``` r
var(myfile$Poids_graines,na.rm = TRUE)
```

    ## [1] 0.5225452

### Ecart-type d'un vecteur

``` r
sd(myfile$Poids_graines,na.rm = TRUE)
```

    ## [1] 0.7228729

La commande `table()` permet de compter les niveaux d'une variable (qualitative ou quantitative). Cette commande génère un tableau d'effectifs pour une ou deux variables.

``` r
table(myfile$Populations)
```

    ## 
    ## pop_10 pop_11 pop_12 pop_13 pop_14 pop_15 pop_16 pop_17  pop_8  pop_9 
    ##     30     30     30     30     30     30     30     30     30     30 
    ##   pop1   pop2   pop3   pop4   pop5   pop6   pop7 
    ##     30     30     30     30     30     30     30

La commande `levels()` permet de lister les niveaux d'une variable qualitative

``` r
levels(myfile$Populations)
```

    ##  [1] "pop_10" "pop_11" "pop_12" "pop_13" "pop_14" "pop_15" "pop_16"
    ##  [8] "pop_17" "pop_8"  "pop_9"  "pop1"   "pop2"   "pop3"   "pop4"  
    ## [15] "pop5"   "pop6"   "pop7"

La commande `nlevels()` permet de compter le nombre de niveaux d'une variable qualitative

``` r
nlevels(myfile$Populations)
```

    ## [1] 17
