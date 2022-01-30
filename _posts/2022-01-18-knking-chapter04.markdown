---
title: "knking chapter04"
excerpt: "챕터4 키워드 정리"

toc: true
toc_sticky: true
toc_label: 목차

breadcrumbs: true

categories:
   - c
tags:
   - [KNK]

date: "2022-01-18 20:51:50 +0900"
---
---
### expressions

<br>
#### arithmetic operator(산술연산자)

- unary  
    `+-`

<br>
--- 
#### assignment operator(할당연산자)
- 
    수학의 연산자는 피연산자를 수정하지 않는다. ex) i + j 는 i 와 j 를 더하는것.  
    c의 연산자중 일부는 피연산자를 수정한다. 할당연산자.  
    i = 0 은 0이 i에 할당된다.  
    `i = j = k = 0` >> `i = (j = (k = 0))`
    
    조심
    ```c
    int i;
    float f;

    f = i = 33.3f
    ```
    f에는 33.0이 할당된다.  

l-value(left value)  
식이 아니며 메모리에 저장된 객체. 상수나 계산의 결과가 아니다.  
변수는 l-value. 10또는 2와 같은 식은 아니다. 
이 시점에서 변수만 우리가 알고있는 l-value  

복합할당  
```c
i = i + 2;
```  
`+=` `-=` `*=` `/=` `%=`  
`v += e` 와 `v = v + e` 는 동등하지않다. 연산자 우선순위 문제.
`i *= j + k` 는 `i = i * j + k`

<br>
--- 
#### increment / decrement operator  
`i += 1;`  

prefix operator
```c
i = 1;
printf("i is %d\n", ++i); /* prints "i is 2" */
printf("i is %d\n", i);   /* prints "i is 2" */
```

postfix operator
```c
i = 1;
printf("i is %d\n", i++); /* prints "i is 1" */
printf("i is %d\n", i);   /* prints "i is 2" */
```
postfix 는 다음 문이 실행되기 전에 증가한다고 생각.  
보충  
c 표준은 시퀸스포인트 개념을 사용. 피연산자의 저장된 값은 이전 시퀸스 포인트와 다음 시퀸스 포인트 사이에서 업데이트 되어야 한다.  
c에는 다양한 시퀸스포인트가 있고 식문의 끝이 한 예이다. 식문이 끝날떄까지 모든 증분밑감소가 수행되어야 한다. 이 조건이 충족될때까지 다음문은 실행될수 없다.

특정한 연산자 또한 시퀸스 포인트가 있고 함수호출도 마찬가지이다. 함수호출의 인수들은 호출이 형성되기전에 완전히 평가되어야한다. 

#### expression evaluation  

<br>
---
#### expression statements

`++i`



<br>
--- 
####
left-value 는 현재 변수.  
right-value 는 변수옆의 표현식. right-value 라는 말대신 expression 사용  

v += e 와 v = v + e 가 다른이유  
v가 두변 평가된다. 
- ex 
    ```c
    a[i++] += 2 
    a[i++] = a[i++] + 2
    ```
    

표현식의 값은 폐기된다.  
`i + 1;`는 계산되지만 저장되지않고 폐기된다.  
`i = 1;`또한 마찬가지. 오른쪽 1 식은 i를 수정하고 폐기된다.
