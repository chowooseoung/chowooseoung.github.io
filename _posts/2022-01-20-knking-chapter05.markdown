---
title: "knking-chapter05"
excerpt: "챕터5 키워드 정리"

toc: true
toc_sticky: true
toc_label: 목차

breadcrumbs: true

categories:
   - c
tags:
   - [KNK]

date: "2022-01-20 07:52:47 +0900"
---
---
### selection statements

- [selection statements - if, switch]()  
- iteration statements - while, do for  
- jump statements - break, continue, goto, return  

- 여러개의 문을 하나로 그룹화 하는 compound statement, 아무것도 안하는 null statement.

챕터 5 는 selection statement, compound statement 

<br>
--- 
#### logical expressions
`<` `>` `<=` `>=` `==` `!=` `!` `&&` `||`

<br>
--- 
#### the if statement
식을 테스트 후 해당 문을 실행  
`if (expression) statement`


compound statement  
`{statement}`

if 문 템플릿에서 문은 복수가 아닌 단수.  

if ( expression ) statement  
문 그룹 주위에 중괄호를 둠으로써 컴파일러가 단일 문으로 처리하도록 강제할수있다.  

예제  
`{ num = 0; page_num++; }`
```c
{
    num = 0;
    page_num++;
}
```

```c
if (line_num == MAX_LINES) {
    line_num = 0;
    page_num++;
}
```

the else clause
if 문은 다음과 같은 else 절을 가질수있습니다.
`if (expression) statement else statement`

예제.  
```c
if (i > j)
    max = i;
else
    max = j;
```

cascaded if statements(else if)
```c
if (expression)
    statement
else if (expression)
    statement
else
    statement
```

conditional expressions

conditional operator `?` `:`  
`expr1 ? expr2 : expr3`

```c
int i, j, k;

i = 1;
j = 2;
k = i > j ? i : j;         /* k is now 2 */
k = (i >= 0 ? i : 0) + j;  /* k is now 3 */
```  

boolean value in C89  
`_BOOL`

```c
_BOOL flag;

flag = 5; /* flag is assigned 1 */

if (flag) /* tests whether flag is 1 */
```

C99는 <stdbool.h> 헤더를 제공한다  
`bool flag; /* same as _BOOL flag; */`
<stdbool.h> 헤더는 true false 라는 이름의 매크로도 제공하며 각각 1, 0 을 의미한다.  
```
flag = false;
/* */ 
flag = true;
```

#### the switch statement

```c
switch (grade) {
    case 4:  printf("Excellent");
             break;
    case 3:  printf("Good");
             break;
    case 2:  printf("Averabe");
             break;
    case 1:  printf("Poor");
             break;
    case 0:  printf("Failing");
             break;
    default: printf("Illegal grade");
             break;
}
```
switch statement는 소수의 사례가 있을때 보통 if statements보다 빠른경우가 많다.  
```c
switch (expression) {
    case constant-expression : statements
    ...
    case constant-expression : statements
    default : statements
}
```

controlling expression.
- `switch` 뒤에는 정수식이 와야합니다. 문자는 c에서 정수로 처리되므로 가능합니다. 그러나 부동소수점 숫자와 문자열은 적합하지 않습니다.

case labels.
- constant expression 변수나 함수호출을 포함할수없다. 
- statements 

default는 항상 필요하지않습니다. 




