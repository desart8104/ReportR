

# Практика № 2

Основы обработки данных с помощью R и Dplyr

## Цель работы

1.  Развить практические навыки использования языка программирования R
    для обработки данных

2.  Закрепить знания базовых типов данных языка R

3.  Развить практические навыки использования функций обработки данныхх
    пакета dplyr - функции select(), filter(), mutate(), arrange(),
    group_by()

## Исходные данные

1.  Ноутбук

2.  OC Windows

3.  Rstudio

4.  Пакет dplyr

5.  Встроенный набор данных starwars

6.  Github

## План выполнения работы

1.  Установить пакет dplyr

2.  Выполнение поставленных задач

## Содержание практической работы

### Шаг 1

**На данном шаге происходит установка пакета dplyr**

Установка пакета dplyr

``` r
#install.packages('dplyr')
```

Подключение пакета

``` r
library(dplyr)
```

    Warning: package 'dplyr' was built under R version 4.4.2


    Attaching package: 'dplyr'

    The following objects are masked from 'package:stats':

        filter, lag

    The following objects are masked from 'package:base':

        intersect, setdiff, setequal, union

### Шаг 2

**На данном шаге происходит выполнение заданий**

Подключение встроенных данных starwars

``` r
starwars <- dplyr::starwars
```

#### Задание 1. Сколько строк в датафрейме?

Для этого воспользуюсь командой nrow()

``` r
starwars |> nrow()
```

    [1] 87

#### Задание 2. Сколько столбцов в датафрейме?

Для этого воспользуюсь командой ncol()

``` r
starwars |> ncol()
```

    [1] 14

#### Задание 3. Как просмотреть примерный вид датафрейма?

Для просмотра вида датафрейма существует команда glimpse

``` r
glimpse(starwars)
```

    Rows: 87
    Columns: 14
    $ name       <chr> "Luke Skywalker", "C-3PO", "R2-D2", "Darth Vader", "Leia Or…
    $ height     <int> 172, 167, 96, 202, 150, 178, 165, 97, 183, 182, 188, 180, 2…
    $ mass       <dbl> 77.0, 75.0, 32.0, 136.0, 49.0, 120.0, 75.0, 32.0, 84.0, 77.…
    $ hair_color <chr> "blond", NA, NA, "none", "brown", "brown, grey", "brown", N…
    $ skin_color <chr> "fair", "gold", "white, blue", "white", "light", "light", "…
    $ eye_color  <chr> "blue", "yellow", "red", "yellow", "brown", "blue", "blue",…
    $ birth_year <dbl> 19.0, 112.0, 33.0, 41.9, 19.0, 52.0, 47.0, NA, 24.0, 57.0, …
    $ sex        <chr> "male", "none", "none", "male", "female", "male", "female",…
    $ gender     <chr> "masculine", "masculine", "masculine", "masculine", "femini…
    $ homeworld  <chr> "Tatooine", "Tatooine", "Naboo", "Tatooine", "Alderaan", "T…
    $ species    <chr> "Human", "Droid", "Droid", "Human", "Human", "Human", "Huma…
    $ films      <list> <"A New Hope", "The Empire Strikes Back", "Return of the J…
    $ vehicles   <list> <"Snowspeeder", "Imperial Speeder Bike">, <>, <>, <>, "Imp…
    $ starships  <list> <"X-wing", "Imperial shuttle">, <>, <>, "TIE Advanced x1",…

#### Задание 4. Сколько уникальных рас персонажей (species) представлено в данных?

``` r
length(unique(starwars$species))
```

    [1] 38

#### Задание 5. Найти самого высокого персонажа

``` r
starwars |> arrange(desc(height)) |> head(1) |> select(name)
```

    # A tibble: 1 × 1
      name       
      <chr>      
    1 Yarael Poof

#### Задание 6. Найти всех персонажей ниже 170

``` r
starwars |> filter(height < 170) |> select(name)
```

    # A tibble: 22 × 1
       name                 
       <chr>                
     1 C-3PO                
     2 R2-D2                
     3 Leia Organa          
     4 Beru Whitesun Lars   
     5 R5-D4                
     6 Yoda                 
     7 Mon Mothma           
     8 Wicket Systri Warrick
     9 Nien Nunb            
    10 Watto                
    # ℹ 12 more rows

#### Задание 7. Подсчитать ИМТ (индекс массы тела) для всех персонажей. ИМТ подсчитать по формуле.

``` r
starwars |> filter(!is.na(mass), !is.na(height)) |> mutate("ИМТ" = mass/(height * height)) |> select(name, "ИМТ")
```

    # A tibble: 59 × 2
       name                   ИМТ
       <chr>                <dbl>
     1 Luke Skywalker     0.00260
     2 C-3PO              0.00269
     3 R2-D2              0.00347
     4 Darth Vader        0.00333
     5 Leia Organa        0.00218
     6 Owen Lars          0.00379
     7 Beru Whitesun Lars 0.00275
     8 R5-D4              0.00340
     9 Biggs Darklighter  0.00251
    10 Obi-Wan Kenobi     0.00232
    # ℹ 49 more rows

#### Задание 8. Найти 10 самых вытянутых персонажей. “Вытянутость” оценить по отношению массы к росту персонажей

``` r
starwars |> filter(!is.na(mass), !is.na(height)) |> mutate('Вытянутость' = mass/height) |> arrange(desc(Вытянутость)) |> head(10) |> select(name, 'Вытянутость')
```

    # A tibble: 10 × 2
       name                  Вытянутость
       <chr>                       <dbl>
     1 Jabba Desilijic Tiure       7.76 
     2 Grievous                    0.736
     3 IG-88                       0.7  
     4 Owen Lars                   0.674
     5 Darth Vader                 0.673
     6 Jek Tono Porkins            0.611
     7 Bossk                       0.595
     8 Tarfful                     0.581
     9 Dexter Jettster             0.515
    10 Chewbacca                   0.491

#### Задание 9. Найти средний возраст персонажей каждой рассы вселенной звездных войн

``` r
starwars |> filter(!is.na(birth_year)) |> group_by(species) |> summarise('Сред' = mean(birth_year))
```

    # A tibble: 15 × 2
       species         Сред
       <chr>          <dbl>
     1 Cerean          92  
     2 Droid           53.3
     3 Ewok             8  
     4 Gungan          52  
     5 Human           53.7
     6 Hutt           600  
     7 Kel Dor         22  
     8 Mirialan        49  
     9 Mon Calamari    41  
    10 Rodian          44  
    11 Trandoshan      53  
    12 Twi'lek         48  
    13 Wookiee        200  
    14 Yoda's species 896  
    15 Zabrak          54  

#### Задание 10. Найти самый распространенный цвет глаз персонажей вселенной Звездных войн.

``` r
starwars |> filter(!is.na(eye_color)) |> group_by(eye_color) |> summarise('CountEye'= n()) |> arrange(desc(CountEye)) |> head(1) |> select(eye_color)
```

    # A tibble: 1 × 1
      eye_color
      <chr>    
    1 brown    

#### Задание 11. Подсчитать среднюю длину имени в каждой расе вселенной Звездных Войн

``` r
starwars |> mutate('lenName' = nchar(name)) |> group_by(species) |> summarise('meanNameLen' = mean(lenName))
```

    # A tibble: 38 × 2
       species   meanNameLen
       <chr>           <dbl>
     1 Aleena          12   
     2 Besalisk        15   
     3 Cerean          12   
     4 Chagrian        10   
     5 Clawdite        10   
     6 Droid            4.83
     7 Dug              7   
     8 Ewok            21   
     9 Geonosian       17   
    10 Gungan          11.7 
    # ℹ 28 more rows

## Оценка результатов

1.  Были успешно выполнены поставленные задачи

2.  Изучена библиотека dplyr и соответствующие функции для решения задач
    (filter, group_by…)

## Вывод

Получен навык практической работы с функциями обработки данных:
select(), filter(), mutate(), arrange(), group_by()
