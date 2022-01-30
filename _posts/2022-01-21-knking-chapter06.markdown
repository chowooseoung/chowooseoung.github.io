---
title: "knking-chapter06"
excerpt: ""

toc: true
toc_sticky: true
toc_label: 목차

breadcrumbs: true

categories:
   - 
tags:
   - 

date: "2022-01-21 13:02:06 +0900"
---
---
### loops
반복문.  

[while](#the-while-statement) 루프 본체가 실행되기 전에 제어식을 테스트 하는 루프에 사용  
[do](#do) 루프 본문이 실행된 후 식을 테스트 하는 경우 사용  
[for](#) 계수 가변성을 증가시키거나 감소시키는 루프에 사용  

<br>
---
#### the `while` statement
```c
while (expression) statement
```

```c
while (i < n)  /* controlling expression */
    i = i * 2; /* loop body */
```
괄호는 필수  
제어식이 먼저 계산. 0이 아닌경우 본문 실행. 

복합문이 필요한경우
```c
while (i < 0) {
    printf("T minus %d and counting\n", i);
    i--;
}
```

<br>
---
#### the `do` statement
```c
do statement while ( expression  );
```  

```c
i = 10;
do {
    printf("T minus %d and counting\n", i);
    --i;
} while (i > 0);
```

<br>
---
#### the `for` statement
```c
for (expr1; expr2; expr3) statement
```

```c
for (i=10; i>0; i--)
    printf("T minus %d and counting\n", i);
```

for statement는 while statement와 밀접한 연관이 있습니다. 몇가지 드문 경우를 제외하고 for 루프는 항상 동등한 while 루프로 대체될수있습니다.
```c
expr1;
while (expr2) {
    statement
    expr3;
}
```
```c
i = 10;
while (i > 0) {
    printf("T minus %d and counting\n", i);
    i--;
}
```

##### for statements in C99  
첫번째 표현식에 선언을 할수있다.
```c
for (int i = 0; i < n; i++)
    ...
```
i에 대한 선언이 이미 존재하는경우 이 문은 루프 내에서만 사용될 i의 새버전을 만듭니다. for statement에서 선언된 변수는 루프 본문 밖에서 엑세스 할수 없습니다.
```c
for int i = 0, j = 0; i < n; i++)
    ...
```
같은유형은 둘이상도 가능.

the comma operator  
경우에 따라 두개이상의 초기표현식 또는 루프를 통과할때마다 여러 변수를 증가시키는 for statement를 작성할수 있습니다.  
`expr1 , expr2`  
expr1이 평가되고 그 값이 폐기됩니다. expr2가 평가되며 expr2의 값은 전체식으 ㅣ값입니다.

<br>
---
#### exiting from a loop

the `break` statement  
the `continue` statement  
the `goto` statement  
goto는 문이 label을 가지고 있다면 점프할수있다.
label
`identifier : statement`  

`goto identifier;`  

```c
for (d = 2; d < n; d++)
    if (n % d == 0)
        goto done;
done:
if (d < n)
    printf("%d is divisible by %d\n", n, d);
else
    printf("%d is prime\n", n);
```
일반적으로 break, continue로 대부분의 상황을 처리하기에 충분합니다.
하지만 때때로 쓰이는 부분이 있습니다.
```c
while (...) {
    switch (...) {
        ...
        goto loop_done; /* break won't work here */
        ...
    }
}
loop_done: ...
```
중첩된 루프를 종료할 때 유용합니다.

<br>
---
#### the `null` statement
문은 세미콜론을 제외하고 null 일수있습니다.
`i = 0; ; j = 1;`  
이 줄에는 i에 대한 assignment, null statement, j에 대한 assignment 3개의 문이있습니다.
 
무효문장은 주로 한 가지에 도움이 된다. 바디가 비어있는 루프를 쓸때.
```c
for (d = 2; d < n; d++)
    if (n % d == 0)
        break;
```
if 의 조건을 loop's controlling expression으로 이동하면 루프의 바디는 empty할수있습니다.
```c
for (d = 2; d < n && n % d != 0; d++)
    ; /* empty loop body */
```
루프를 통과할때마다 조건 d < n이 먼저 평가된다. 그것이 거짓이면 루프는 종료된다. 그렇지않으면 n % d != 0이 테스트되고 거짓이면 루프가 종료됩니다.

while과 for(;;)무한루프의 성능은 최신 컴파일러라면 차이가 없다.





