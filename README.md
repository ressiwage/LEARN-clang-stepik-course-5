# LEARN-clang-stepik-course-5
# что это?
это решения курса по си https://stepik.org/course/57680/ .

сюда я вписал все свои решения с 20.11.24 по 30.11.24. курс был пройден за 10 дней.

задачи идут по возрастающей сложности, от hello world до malloc, realloc.

большая часть решений сюда не вошла по причине их неинтересности


___
# hello world
### проблема:
### решение:
```c
// начинаем говорить компьютеру "здравствуй", начало программы
#include <stdio.h>

int main()
{
// заканчиваем говорить компьютеру "здравствуй", начало программы

	// тут пишем код
    printf("Hello, world!");  // печать строки Hello, world!

// начинаем говорить компьютеру "до свидания", конец программы
    return 0;
}
// заканчиваем говорить компьютеру "до свидания", конец программы
```

___
# scanf
### problem: 
Эксперимент длится h часа m минут. Сколько это в минутах? Сколько это в секундах?

Дано: два целых числа через пробел (часы и минуты).
Найти: два целых числа, по одному числу на строке. Всего минут. Всего секунд.

### solution: 
```c
#include <stdio.h>

int main()
{
    
    // объявить переменные
    int totalm, totals, m, h;
    scanf("%d %d", &h, &m);
    totalm = h*60+m;
    totals = totalm*60;
    printf("%d\n", totalm);
    printf("%d", totals);
    // прочитать входные данные
    
    // вычислить

    // напечатать результат

    return 0;
}
```

___
# цельсий в фаренгейты
### problem: 
Написать функцию, которая переводит температуру из градусов Цельсия C в градусы Фаренгейта F по формуле
Измерения - в целых числах.

Реализуйте функцию

float fahr(int cel);


### solution: 
```c
float fahr(int cel){
    return cel*(9.0/5.0)+32;
}

```

___
# Расстояние между двумя точками
### problem: 
Отрезок на плоскости задан двумя точками: координаты (x1, y1) и (x2, y2) - целые числа.

Написать функцию

float dist(int x1, int y1, int x2, int y2)
{
    код пишем с отступом в 1 табуляцию
}s

### solution: 
```c
float dist(int x1, int y1, int x2, int y2)
{
    return sqrt(
    pow((double)(x1-x2), 2.0) + pow((double)(y1-y2), 2.0)
        );
}s
```

___
# формула герона
### problem: 
Можно вычислить площадь треугольника s по трем его сторонам.

Скопируйте из предыдущей задачи функцию

float dist(int x1, int y1, int x2, int y2);
, которая вычисляет расстояние между 2 точками.

Напишите функцию

float area(int x1, int y1, int x2, int y2, int x3, int y3);
, которая вычисляет площадь треугольника по 3 точкам по формуле (здесь была формула)
a,b,c - длины сторон треугольника.

В функции main напечатайте найденную площадь с точностью до 3 десятичных знаков. Используйте %.3f

Посылать всю программу целиком. Решения, где функция area не совпадает с требуемым прототипом, будут дисквалифицированы вручную.

### solution: 
```c
#include <stdio.h>
#include <math.h>
// #include <stdlib.h>

float fahr(int cel){
    return cel*(9.0/5.0)+32;
}

float celsius(int fahr){
    return (fahr-32)/(9.0/5.0);
}

float dist(int x1, int y1, int x2, int y2)
{
    return sqrt(
    pow((double)(x1-x2), 2.0) + pow((double)(y1-y2), 2.0)
        );
}

float area(int x1, int y1, int x2, int y2, int x3, int y3){
    float a = dist(x1, y1, x2, y2);
    float b = dist(x2, y2, x3, y3);
    float c = dist(x1, y1, x3, y3);
    float p = (a+b+c)/2.0;

    return sqrt(p*(p-a)*(p-b)*(p-c));
}

int main()
{
    int x1, x2, x3, y1, y2, y3;

    scanf("%d %d %d %d %d %d", &x1, &y1, &x2, &y2, &x3, &y3);
    printf("%.3f\n", area(x1, y1, x2, y2, x3, y3));    // .2f - печатать с точностью до 2 знаков после .

    return 0;
}
```

___
# Печать номера билета наоборот
### problem: 
Дано целое шестизначное число (6 цифр). Написать функцию

void print_revers(int x);
Она печатает 6 цифр числа x в обратном порядке.

### solution: 
```c
void print_revers(int x){
    char* snum = malloc(snprintf(NULL, 0, "%d", x)+1);
    snprintf( snum, 7, "%d", x );
    for( int i=5; i>=0;i--){
        printf("%c", snum[i]);
    }
    free(snum);
}

```

___
# swap
### problem: 
void swap(int * px, int * py) меняет значения переменных, на которые указывают px и py. Функция уже написана. Вам нужно только ее вызвать.

Нужно послать только функцию main. В нее дописать ОДНУ строку - вызов функции swap.

### solution: 
```c

#include <stdio.h>

void swap(int * px, int * py);

int main()
{
    int x, y;
    scanf("%d%d", &x, &y);      // если ввели 2 3

    // напишите вызов функции swap
    swap(&x, &y);

    printf("%d %d\n", x, y);    // то напечатает 3 2

    return 0;
}

```

___
# swap
### problem: 
void swap(int * px, int * py) меняет значения переменных, на которые указывают px и py. Напишите и пошлите эту функцию.

Функцию main посылать не нужно.

### solution: 
```c
void swap(int * px, int * py){
    int temp;
    temp = *px;
    *px = *py;
    *py = temp;
}


```

___
# mirror
### problem: 
Написать и использовать функцию

void mirror(int *px, int *py);
которая зеркально отображает точку с координатами (x,y) относительно оси Y.

Послать всю программу, и функцию mirror, и функцию main.

Input format: 2 целых числа через пробел - x и y координаты точки до отображения.

Output format: 2 целых числа через пробел - x и y координаты точки после отображения.

### solution: 
```c
#include <stdio.h>

void min2time(int mm, int *ph, int *pm)
{
    *ph = mm / 60;
    *pm = mm % 60;
}

void mirror(int *px, int *py){
    *px = -*px;
}

int main()
{
    int x,y;
    scanf("%d %d", &x, &y);
    mirror(&x, &y);
    printf("%d %d\n", x, y);

    return 0;
}

```

___
# из большой в маленькую
### problem: 
Дана большая латинская буква. Напечатайте соответствующую ей маленькую латинскую букву.

Посылать всю программу. Проверку входных данных делать не нужно, гарантируется, что первый символ входного потока - большая латинская буква.

### solution: 
```c
#include <stdio.h>

void min2time(int mm, int *ph, int *pm)
{
    *ph = mm / 60;
    *pm = mm % 60;
}

void mirror(int *px, int *py){
    *px = -*px;
}

int main()
{
    char c;
    scanf("%c", &c);
    printf("%c\n", c+('a'-'A'));

    return 0;
}
```

___
# следующая клетка
### problem: 
В записи шахматных партий клетки шахматной доски кодируются буквой и цифрой. Буква означает номер столбца, цифра - номер ряда.

Напечатать, координаты клетки на один ряд выше.

Будут даны клетки из рядов с 1 по 7.

### solution: 
```c
#include <stdio.h>

void min2time(int mm, int *ph, int *pm)
{
    *ph = mm / 60;
    *pm = mm % 60;
}

void mirror(int *px, int *py){
    *px = -*px;
}

int main()
{
    char c;
    int d;
    scanf("%c%d", &c, &d);
    printf("%c%d\n",c, d+1);

    return 0;
}
```

___
# Площадь прямоугольника - 2
### problem: 
Прямоугольник на плоскости XY со сторонами, параллельным осям, задан x и y координатами левой верхней и правой нижней вершин. Для его хранения объявлена структура (ее посылать НЕ надо!)
struct Point {
    int x;
    int y;
};
struct Rect {
    struct Point lt;    // координаты левой верхней вершины
    struct Point rb;    // координаты правой нижней вершины
};
Напишите функцию, которая возвращает площадь прямоугольника a.

int area(struct Rect a);

### solution: 
```c
int area(struct Rect a){
    return (a.rb.x-a.lt.x)*(-a.rb.y+a.lt.y)
    ;}

```

___
# Холодильник и дверь
### problem: 
Нужно пронести холодильник в дверь. Размер двери w h сантиметров, размер холодильника a, b, c сантиметров.

Холодильник можно поворачивать и класть на бок.

Даны размеры двери через пробел на одной строке и размеры холодильника через пробел на другой строке.

Напечатайте YES, если холодильник можно пронести в дверь. Иначе напечатайте NO.

Читаем, что если ширина двери 60, то холодильник шириной 60 в него пройдет (если пройдет по высоте).

В дверь 80х180 холодильник 60х90х200 пройдет (YES). Надо развернуть так, чтобы в 80х180 проходило 60х90.

В дверь 80х180 холодильник 60х190х200 не пройдет (NO). Никак не повернуть, чтобы в 80х180 проходило 60х190.

### solution: 
```c
#include <stdio.h>
#define and &&
#define or ||
#define not !
#define is(x,y) (&(x)==&(y))

int check(int w,int  h,int  a,int  b){
    if ( (a<w&&b<h)||(b<w&&a<h) ){return 1;}
    else{return 0;}
}
int main()
{
    int w,h,a,b,c;
    scanf("%d %d\n%d %d %d", &w, &h, &a, &b, &c);
    if(check(w,h,a,b)||check(w,h,b,c)||check(w,h,a,c)){
    printf("YES");}else{printf("NO");}

    return 0;
}

```

___
# Высокие студенты
### problem: 
У студентов измерили рост в сантиметрах (целое число) и записали числа на одной строке через пробел. Напечатайте сколько студентов измерили и сколько человек было выше 170 сантиметров?

### solution: 
```c
#include <stdio.h>
#include<math.h>
#define and &&
#define or ||
#define not !
#define is(x,y) (&(x)==&(y))

int main()
{
    int a,b,c,d;
    a=0;b=0;c=0;d=0;
    while(scanf("%d", &a)==1){
         b+=1;
        if(a>170){c++;}
    }
    printf("%d %d", b, c);
    return 0;
}

```

___
# Размен
### problem: 
В банкомате монеты имеют цену 1, 2, 5, 10, 50, 100, 500, 1000, 5000 рублей.

Надо выдать банкоматом X рублей так, чтобы количество монет было наименьшим.

Дано натуральное число Х.

Напечатать сколько каких монет надо выдавать. Печатать цену монеты и количество таких монет через пробел, по паре чисел на строку, от самой большой монеты к меньшей.

### solution: 
```c
#include <stdio.h>
#include<math.h>
#define and &&
#define or ||
#define not !
#define is(x,y) (&(x)==&(y))

int main()
{
    int array[9] = {5000, 1000,500, 100, 50, 10, 5, 2, 1};
    int res[9] = {0};
    int a = 0;
    scanf("%d", &a);
    for(int i =0; i<9; i++){
        res[i] = a/array[i];
        printf("%d %d\n",array[i], res[i]);
        a = a%array[i];
    }
    return 0;
}
```

___
# Печать длинного числа
### problem: 
В Си целые числа ограничены типами unsigned long long int. Чтобы работать с большими числами нужно придумать как их хранить и написать функции для работы с ними.
число 147 это 7*10^0 + 4*10^1 + 1*10^2
Будем хранить коэффициенты 
​
  в массиве a как a[0], a[1], a[2]. И будем в n хранить максимальную степень 10 в разложении числа по степеням 10.
Объединим массив a и поле n в структуру Decimal, так как они описывают одно и то же число. Чисел в программе может быть много, поэтому лучше их объединить в структуру. Например, мы захотим посчитать 50 число Фибоначчи.
```c
#define N 100
typedef struct {
    char a[N];       // number is a[0]*10^0 + a[1]*10^1 + ..+ a[n]*10^n
    unsigned int n;  // наибольшая степень десяти
}Decimal;
```
Напишите функцию void elong_print(Decimal x), которая печатает длинное число и \n в конце.

### solution: 
```c
void elong_print(Decimal x)
{
    for(int i=x.n;i>=0;i--){
        printf("%d", x.a[i]);
    }
    printf("\n");
}
```

___
# Задаем большие числа
### problem: 
Для хранения больших чисел объявили структуру

```c
#define N 100
typedef struct {
    char a[N];       // number is a[0]*10^0 + a[1]*10^1 + ..+ a[n]*10^n
    unsigned int n;  // наибольшая степень десяти
}Decimal;
```
Реализуйте функцию записи значения большого числа res из строки str.

void elong_set (Decimal * res, const char str[ ]);

В проверяющую систему посылать только реализацию требуемой функции elong_set.

### solution: 
```c
#define foreachs(i, string) for(int i=0; string[i]!='\0'; i+=sizeof(string[0]))

void elong_set(Decimal *res, const char str[])
{
    foreachs(i, str){
        res->a[strlen(str)-1-i] = str[i]-'0'; 
    }
    res->n = strlen(str)-1;
    printf("\n");
}

```

___
 # Задача про капитана Флинта
### problem: 
Капитан Флинт зарыл клад на Острове сокровищ. Он оставил описание, как найти клад. Описание состоит из строк вида: North 5, где первое слово – одно из "North", "South", "East", "West", а второе число – количество шагов, необходимое пройти в этом направлении.

Напишите программу, которая по описанию пути к кладу определяет точные координаты клада, считая, что начало координат находится в начале пути, ось OX направлена на восток, ось OY – на север.

Программа получает на вход последовательность строк указанного вида, завершающуюся строкой со словом "Treasure!". Программа должна вывести два целых числа: координаты клада.

### solution: 
```c
#include <stdio.h>
#include <math.h>
#include <string.h>

#define and &&
#define or ||
#define not !
#define is(x, y) (&(x) == &(y))
#define arr_size(array) (sizeof(array)/sizeof(array[0]))
#define foreach(i, array) for(int i=0; i<sizeof(array)/sizeof(array[0]); i+=sizeof(array[0]))
//reversed foreach
#define rforeach(i, array) for(int i=sizeof(array)/sizeof(array[0]); i>=0; i-=sizeof(array[0]))
//foreach for string
#define foreachs(i, string) for(int i=0; string[i]!='\0'; i+=sizeof(string[0]))

int main()
{
    char s[10];
    int d, x, y;
    x=0;
    y=0;
    while(1) {
        scanf("%11s", s);
        if(strcmp(s, "Treasure!")==0){
            break;
        }
        scanf("%d\n", &d);
        if (strcmp(s, "North")==0){
            y+=d;
        }else if(strcmp(s, "South")==0){
            y-=d;
        } else if(strcmp(s, "East")==0){
            x+=d;
        } else if(strcmp(s, "West")==0){
            x-=d;
        } 
    }
    printf("%d %d", x, y);

    return 0;
}

```

___
 # Замена подстроки в строке
### problem: 
Вы уже решали эту задачу, но без выделения динамической памяти.

Напечатать текст, заменив все подстроки bomb на watermelon.

Для замены подстроки напишите функцию

char * replace (const char * src);

которая выделяет память для новой строки, копирует туда src, заменяя bomb на watermelon и возвращает получившуюся строку.

В проверяющую систему пошлите только реализацию функции replace.

### solution: 
```c
char * replace (const char * src){
    char *psc = strdup(src);
    size_t bwdiff = strlen("watermelon") - strlen("bomb"); 
    size_t mellen = strlen("watermelon");
    size_t bomlen = strlen("bomb");

    char *tmp = strdup(src);

    int bombs = 0;
    for(char * entry = strstr(psc, "bomb"); entry!=NULL; entry=strstr(psc+(entry-psc)+bomlen, "bomb"), bombs++){
        // printf("12");
        size_t ind = entry-psc + (bombs*bwdiff);
        tmp = realloc(tmp, strlen(tmp)+bwdiff+1);
        memmove(tmp + ind+mellen, tmp + ind+bomlen, strlen(tmp + ind+bomlen)+1);
        char melon[] = "watermelon";
        memcpy(tmp + ind, melon, mellen);

        // printf("<%s> <%zu>\n", psc, sizeof psc);
        

    }
    free(psc);
    return tmp;
    // char * entrybomb = strstr(src, "bomb");
}
```

___
 # Сложение чисел
### problem: 
Для хранения больших чисел объявили структуру

```c
typedef struct {
    char * a;           // number is a[0]*10^0 + a[1]*10^1 + ..+ a[n]*10^n
    unsigned int n;     // наибольшая степень десяти
    unsigned int size;  // размер выделенной динамической памяти в а
}Decimal;
```
Ноль должен быть представлен как 0*10^0
Реализуйте функцию сложения чисел a и b, которая возвращает сумму чисел.

void elong_add (const Decimal * a, const Decimal * b, Decimal * res);

В проверяющую систему посылать только реализацию требуемой функции. Номера строк вашего кода начинаются с 100001.

### solution: 
```c
#define min_(a, b) ((a) < (b) ? (a) : (b))
#define max_(a, b) ((a) > (b) ? (a) : (b))
void elong_add (const Decimal * a, const Decimal * b, Decimal * res){
    res->size = 0;
    res->n = -1;
    int max_size = max_(a->size, b->size);
    res->a = malloc(max_size * sizeof(char));
    int left = 0;
    
    for(int i = 0; i < max_size; i++){
        char val_a, val_b;
        if(i>a->n){val_a = 0;} else{val_a = a->a[i];}
        if(i>b->n){val_b = 0;} else{val_b = b->a[i];}

        res->n +=1; res->size += 1;
        res->a[i] = (left + val_a + val_b) % 10;
        left = (left + val_a + val_b) / 10;
    }
    if(left!=0){
        char *new_arr = realloc(res->a, (res->size +1) *sizeof(char));
        
        new_arr[(res->size)*sizeof(char) ]=left;
        res->a = new_arr;
        res->size+=1;res->n+=1;
    }

}
```

___
 # Сложение чисел
### problem: 
Для хранения больших чисел объявили структуру

```c
typedef struct {
    char * a;           // number is a[0]*10^0 + a[1]*10^1 + ..+ a[n]*10^n
    unsigned int n;     // наибольшая степень десяти
    unsigned int size;  // размер выделенной динамической памяти в а
}Decimal;
```
Реализуйте функцию сложения чисел a и b, которая возвращает сумму чисел.

Decimal * elong_add (const Decimal * a, const Decimal * b);

В проверяющую систему посылать только реализацию требуемой функции.

### solution: 
```c
#define min_(a, b) ((a) < (b) ? (a) : (b))
#define max_(a, b) ((a) > (b) ? (a) : (b))

Decimal * elong_add (const Decimal * a, const Decimal * b){
    Decimal * res = malloc(sizeof(Decimal));
    res->size = 0;
    res->n = -1;
    int max_size = max_(a->size, b->size);
    res->a = malloc(max_size * sizeof(char));
    int left = 0;
    
    for(int i = 0; i < max_size; i++){
        char val_a, val_b;
        if(i>a->n){val_a = 0;} else{val_a = a->a[i];}
        if(i>b->n){val_b = 0;} else{val_b = b->a[i];}

        res->n +=1; res->size += 1;
        res->a[i] = (left + val_a + val_b) % 10;
        left = (left + val_a + val_b) / 10;
    }
    if(left!=0){
        char *new_arr = realloc(res->a, (res->size +1) *sizeof(char));
        
        new_arr[(res->size)*sizeof(char) ]=left;
        res->a = new_arr;
        res->size+=1;res->n+=1;
    }
    return res;

}

```

