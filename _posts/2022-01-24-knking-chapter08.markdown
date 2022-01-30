---
title: "knking-chapter08"
excerpt: ""

toc: true
toc_sticky: true
toc_label: 목차

breadcrumbs: true

categories:
   - 
tags:
   - 

date: "2022-01-24 23:43:53 +0900"
---
<br>
---
### array
지금까지는 scalar 변수들을 살펴봤습니다. c는 aggregate 변수도 지원합니다.  
array 와 structures가 있습니다.

<br>
---
#### one dimensional arrays
`int a[10];`  
```c
#define N 10
...
int a[N];
```

array subscripting  
```c
for (i = 0; i < N; i++)
    a[i] = 0;           /* clears a */
```
```c
for (i = 0; i < N; i++)
    scanf("%d", &a[i]); /* reads data into a*/
```
```c
for (i = 0; i < N; i++)
    sum += a[i];        /* sums the elements of a */
```

```c
int a[10], i;

for (i = 1; i <= 10; i++)
    a[i] = 0;
```
*stack smashing detected*  

array initialization  





































