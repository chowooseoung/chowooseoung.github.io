---
title: "knking chapter07"
excerpt: ""

toc: true
toc_sticky: true
toc_label: 목차

breadcrumbs: true

categories:
   - 
tags:
   - 

date: "2022-01-22 20:01:38 +0900"
---
---
### basic types

<br>
---
#### integer types
short int  
unsigned short int  

int  
unsigned int  

long int  
unsigned long int  

int는 생략될수있습니다. short, long unsigned short

int의 크기는 컴파일러마다 다를수있습니다. <limit.h> 헤더는 각 정수유형의 매크로를 정의합니다.

##### integer types in C99
C99에서는 long long int, unsigned long long int를 제공합니다.

interger constants
정수는 10진수 8진수 16진수로 쓸수있습니다.
이것은 저장되는 방법에 영향을 주지않습니다. 

10진수 - 10
8진수 - 0123
16진수 - 0x12ff

컴파일러가 긴 정수로 처리하도록 하려면

10진수 - 10L
8진수 - 0123L
16진수 - 0x12ffL

상수부호가 없음을 나타내려면 

10진수 - 10U
8진수 - 0123U
16진수 - 0x12ffU

L(l), U(u)는 같이 사용할수있습니다.(순서와 대소문자는 중요하지않다.)

integer constants in C99
C99에서는 ll또는 LL은 long long int 


integer overflow
산술연산이 정수에 대해 수행될때 결과가 너무 크다면 오버플로우 발생  

reading and writing integers

```c
unsigned int u;
scanf("%u", &u); /* reads u in base 10 */
printf("%u", u); /* writes u in base 10 */
scanf("%o", &u); /* reads u in base 8 */
printf("%o", u); /* writes u in base 8 */
scanf("%x", &u); /* reads u in base 16 */
printf("%x", u); /* writes u in base 16 */
```

short
```c
short s;
scanf("%hd", &s);
printf("%hd", s);
```

long
```c
long l;
scanf("%ld", &l);
printf("%ld", l);
```

long long in C99
```c
long long l;
scanf("%lld", &ll);
printf("%lld", ll);
```

<br>
---
#### floating types
float(single-precision floating-point)  정밀도의 양이 중요하지 않을때  
double(double-precision floating-point)  대부분의 프로그램에서 충분히 높은 정밀도  
long double(extended-precision floating-point)  거의 사용되지 않는다.

컴퓨터마다 부동소수점숫자를 다른방식으로 저장할수있기때문에 c표준은 부동소수점 더블 롱더블 타입이 얼마나 정확한지 명시하지 않는다.

_IEEE floating-point standard_
> 32bit, 64bit  
각 숫자는 세 부분(sign, exponent, fraction)으로 나뉜다.
exponent(지수)를 위해 예약된 비트수는 숫자의 크기,분수(fraction)의 비트수는 정밀도를 결정한다.
single-precision format에서 exponent는 8bit, fraction은 23bit

in C99  
C99에서는 두개의 범주로 나뉜다. float, double, long double타입은 하나의 범주로 분류된다. floating types 은 새롭게 도입된 complex types을 포함한다(float_Complex, double_Complex, long double_Complex)  

floating constants  
부동상수는 다양한 방법으로 쓸수있다. 다음 상수는 모두 57.0을 쓸수있는 방법이다  
`57.0 57. 57.0e0 57E0 5.7e1 5.7e+1 .57e2 570.e-1`  
기본적으로 부동상수는 double-precision으로 저장된다. double값은 float값이 필요할때 자동으로 변환된다. 경우에 따라 float 또는 long double로 저장되게 해야할수도 있다. single-precision으로 저장하려면 f(F) extended-precision으로 저장할때는 l(L)을 넣습니다.  

in C99  
C99에서는 floating constants를 16진수로 작성하는 기능이있다. 거의 사용되지 않습니다.

reading and writing floating-point numbers

%e %f %g

double  l
```c
double d;
scanf("%lf", &d);
```  
scanf에서만 사용하십시오. printf에서는 %e %f %g를 float와 double둘다 쓸수있습니다.  
C99 에서는 %le %lf %lg를 쓸수는 있지만 아무런 효과는 없습니다.

long double L
```c
long double ld;
scanf("%Lf", &ld);
printf("%Lf", ld);
```

<br>
---
#### character types

컴퓨터 마다 기본 문자집합이 다를수 있기 때문에 char type의 값은 컴퓨터마다 다를수있습니다.

```c
char ch;

ch = 'a';
ch = 'A';
ch = '0';
ch = ' ';
```
문자 상수는 작음 따옴표로 묶입니다.

operations on characters  
c는 문자를 작은 정수로 취급한다.  

숫자처럼 문자를 비교할수 있습니다. 소문자 포함여부를 확인하고 대문자로 변환하는 코드  
```c
if ('a' <= ch && ch <= 'z')
    ch = ch - 'a' + 'A';
```
문자들이 숫자와 같은 성질을 가지고 있다는것은 몇가지 장점이 있습니다.  
`for (ch = 'A'; ch <= 'Z'; ch++) ...`

signed and unsigned characters
문자와 정수사이의 밀접한 관계를 고려하여 C89는 integer types 과 character types을 언급하는데 integral types이라는 용어를 씁니다. enumerated types또한 integral types 입니다.  
C99에서는 integral types이라는 용어를 사용하지 않습니다. 대신 integer types용어를 확장해서 사용합니다(character types과 enumerated types을 포함해서). C99의 \_Bool type은 부호없는 정수타입으로 간주된다.

arithmetic types(산술 types)  
integer types 과 floating types 은 arithmetic types에 포함된다.  
다음은 C89의 arithmetic types의 categories와 sub-categories이다.

C89
- integral types
    - char
    - signed integer tyeps(signed char, short int, int, long int)
    - unsigned integer tyeps(unsigned char, unsigned short int, unsigned int, unsigned long int)
    - enumerated types
- floating types(float, double, long double)

C99
- integer types
    - char
    - signed integer types, both standard(signed char, short int, int, long int, long long int)and extended
    - unsigned integer types, both standard(unsigned char, unsigned short int, unsigned int, unsigned long int, unsigned long long int, \_Bool)and extended
    - enumerated types
- floating types
    - real floating types(float, double, long double)
    - complex types(float\_Complex, double\_Complex, long double\_Complex)  

escape sequences
줄바꿈 문자처럼 인쇄되지않는 특수문자
`\t, \n, ...`
문자상수로 사용할경우 excape sequences는 작음 따옴표로 묶여야합니다. #define 을 사용하여 이름을 지정하는것이 좋습니다.  
`#define ESC \'\33\' /* ascii escape character */`  

character-handling functions  
대소문자를 변환하는 더빠른 방법은 toupper library를 이용하는것이다.  
```c
#include <ctype.h>
...
ch = toupper(ch); /* converts ch to upper case */
```  

reading and writing character using scanf and printf  
```c
char ch;
scanf("%c", &ch);
pritnf("%c", ch);
```

```c
scnaf(" %c", &ch); /* skips white space, then reads ch */
```

```c
do {
    scanf("%c", &ch);
} while (ch != '\n');
```
줄바꿈 확인

reading and writing character using *getchar* and *putchar*  

scanf와 printf 대신 getchar putchar을 쓸수있습니다.  
`putchar(ch);`  single character을 씁니다.  
`ch=getchar(); /* reads a character and stores it in ch */`  
getchar은 char value 대신 int value를 반환합니다.

scanf처럼 getchar은 공백을 건너뛰지 않습니다.
getchar, putchar을 사용하면 프로그램 실행시간이 절약됩니다. 두가지 이유로 빠릅니다.
1. 다양한 형식의 데이터를 읽고 쓸수 있도록 설계된 scanf, printf 보다 간단하다.  
2. getchar, putchar는 보통 추가속도를 위한 매크로로 구현된다. 
```c
do {
    scanf("%c", &ch);
} while (ch != '\n');
```

convert get char
```c
do {
    ch = getchar();
} while (ch != '\n');
```

```c
while ((ch = getchar()) != '\n')
    ;
```
이 loop는 문자를 읽고 변수 ch 에 저장한 다음 ch 가 줄바꿈 문자와 다른지 테스트합니다. 
```c
while (getchar() != '\n')
    ;
```

scanf와 getchar을 섞어쓰면 주의해야한다. 버퍼관련.

<br>
---
#### type conversion
컴퓨터가 arithmetic operation(산술연산)을 수행하기 위해서는 피연산자가 같은 비트수여야 하며 같은 방식으로 저장되어야한다. 컴퓨터는 16bit integer를 더할순있지만 16bit integer 와 32bit integer, 32bit integer와 32bit floating-point는 더할수없습니다  
C에서는 이를 할수 있습니다. 그러면 c컴파일러는 변환하는 명령어를 생성해야 할수있다.  
컴퓨터는 이를 자동으로처리하기 때문에 이를 implicit conversions이라고 합니다. 또한 c는 프로그래머가 cast operator를 사용하여 explicit conversions을 수행할수 있게 한다.  

다음과 같은 경우 implicit conversion이 수행된다.  
- 산술식 또는 논리식의 피연산자가 동일하지 않을때
- 할당 오른쪽에 있는 식이 왼쪽에 있는 변수와 일치하지 않을때
- 함수호출의 인수유형이 해당 매개변수 유형과 일치하지 않을때
- 반환문의 식이 반황유형과 일치하지 않을떄  

the usual arithmetic conversions  
일반적인 산술연산 전략은 피연산자 두 값을 안전하게 수용할수 있는 가장 좁은 유형으로 변하는것이다.

long double > double > float  

unsigned long int > long int > unsigned int > int  

```c
char c;
short int s;
int i;
unsigned int u;
long int l;
unsigned long int ul;
float f;
double d;
long double ld;

i = i + c; /* c is converted to int */
i = i + s; /* s is converted to int */
u = u + i; /* i is converted to unsigned int */
l = l + u; /* u is converted to long int */
ul = ul + l; /* l is converted to unsigned long int */
f = f + ul; /* ul is converted to float */
d = d + f; /* f is converted to doubele */
ld = ld + d; /* d is converted to long double */
```  

conversion during assignment  
variable's type이 expression보다 wide 할때 변환된다
```c
char c;
int i;
float f;
double d;

i = c; /* c is converted to int */
f = i; /* i is converted to float */
d = f; /* f is converted to double */
```  

implicit conversions in C99  
변환규칙을 정의하기 위해 각 정수타입에 정수변환 순위를 부여한다  
1. long long int, unsigned long long int
2. long int, unsigned long int
3. int unsigned int
4. short int, unsigned short int
5. char, signed char, unsigned char
6. \_Bool
단순화를 위해 extended integer type과 enumerated types은 무시했습니다.  

C89의 integral promotions대신에 C99는 integer promotions 이 있습니다.  

- 피연산자 중 하나의 유형이 floating type 일때. 규칙은 이전과 동일.
- 둘다 floating type이 아닐때. 두 피연산자에서 integer promotion을 수행합니다. 그렇지않으면 아래 규칙을 따릅니다.
  - 두 피연산자가 둘다 signed type 이거나 둘다 unsigned type 일경우, 변환순위가 작은 피연산자를 순위가 큰 피연산자 유형으로 변환
  - unsigned type 피연산자 순위가 signed type 피연산자 순위보다 크거나 같으면 signed type 피연산자를 unsigned type 으로 변환
  - signed type 피연산자가 unsigned type 피연산자의 모든값을 나타낼수 있는 경우 unsigned type을 signed type 으로 변환
  - 그렇지 않으면, 두 피연산자를 signed type에 상응하는 unsigned type으로 변환합니다.

casting  
unary operator.  

`(type-name) expression`  
```c
float f, frac_part;
frac_part = f - (int) f;
```

```c
float quotient;
int dividend, divisior;

quotient = dividend / divisior;
```
나눗셈의 결과(int)는 quotient에 할달되기 전에 float로 변환된다. casting 을 사용하면 더 정확한 값을 얻을수있다.  

`quotient = (float) dividend / divisior;`  

overflow를 피하기위해서 casting이 필요하다. 
```c
long i;
int j = 1000;

i = j * j; /* overflow may occur */
```

`i = (long) j * j;`  
`i = (long) (j * j); /** wrong **/`


<br>
---
#### type difinitions
bool type을 사용할수 있는 매크로를 만들었었다.
`#define BOOL int`  

더 나은 방법이 있습니다.
`typedef int Bool;`
`Bool flag; /* same as int flag */`
컴파일러는 Bool을 int와 같이 취급한다.  


adventages of type definitions  
프로그램을 더 이해하기 쉽게 만들수 있다.

`typedef float Dollars;`  

`Dollars cash_in, cash_out;`
이 더 낫습니다.  
`float cash_in, cash_out;`
보다

type definitions and portability  
`i = 100000;`  
이는 32비트정수가 있는 컴퓨터에서는 괜찮지만 16비트 컴퓨터에서는 실패합니다.

`typedef int Quantity;`  
위와 같이 사용하다가 프로그램을 더 짧은 정수를 가진 기계로 전송할때 정의를 변경합니다.  
`typedef long int Quantity;`  

이것으로 모든 문제를 해결할순 없습니다. printf와 scanf도 수정해야합니다.

c library는 typedef를 상용하여 c구현체마다 다를수 있는 타입의 이름을 만든다. 다음은 일반적인 예입니다.  
```c
typedef long int ptrdiff_t;
typedef unsigned long int size_t;
typedef int wchar_t;
```  

C99에서 <stdint.h>헤더는 typedef 를 사용하여 특정 비트수를 가진 정수타입의 이름을 정의한다.
예를들어 int32\_t는 정확히 32비트의 부호정수형입니다.

<br>
---
#### the `sizeof` operator
특정 유형의 값을 저장하기위해 얼마나 많은 메모리가 요구되는지  
`sizeof (type-name)`  
sizeof(char)은 항상 1이지만 다른유형의 크기는 다를수있습니다. sizeof(int) 32bit 시스템에서의 크기는 일반적으로 4입니다.  
  
sizeof expression은 size\_t라는 implementation-defined type이기 때문에 sizeof value의 print는 주의가 필요합니다.  
C89에서는 unsigned long으로 캐스팅 한 다음 %lu%lu 를 사용하는것이 좋습니다.  
`printf("Size of int: %lu\n", (unsigned long) sizeof(int));`  
C99에서는 size\_t type의 크기가 unsigned long 보다 클수있습니다. 그러나 C99에서는 printf가 casting 없이 size\_t값을 표시할수있습니다.  
`printf("Size of int: %zu\n", sizeof(int)); /* C99 only */`  






















 








