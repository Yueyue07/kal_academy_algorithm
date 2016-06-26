# Week 10 June 26th Class Notes

## Bits Manipulation

**Decimal Number converts to Binary Number**
> Convert 13 to Binary Number

```
1) 13 % 2 = 1;  13 / 2 = 6
2) 6 % 2 = 0 ;  6 / 2 = 3
3) 3 % 2 = 1 ;  3 / 2 = 1
4) 1 % 2 = 1 ;  1 / 2 = 0

result: 1101
verification: 1 * 2^3 + 1 * 2^2 + 0 + 1 * 2^1 = 8 + 4 + 1 = 13
```


## Binary Operators

**&** :
```
4 & 2 = 0

4: 0100
2: 0010
&: 0000
result: 0
```
----

**|** :
```
4 | 2 = 6

4: 0100
2: 0010
|: 0110
result: 2^2 + 2 = 6
```
----

**^**
```
4 ^ 2 = 6

4: 0100
2: 0010
^: 0110

5 ^ 3 = 6

5: 0101
3: 0011
^: 0110

```
----
**~**
```
 ~4 = 11
 4: 0100
 ~: 1011
 result: 8 + 0 + 2 + 1 = 11
```

**Collect Selection of Options**
> Multiple Options Select Results through Bit Manipulation

```
option1: select 0: 2^0  0001
option2: select 1: 2^1  0010
option3: select 2: 2^2  0100
option4:        

step1:

option1: 0001
option2: 0010
|      : 0011
option2: 0100
|      : 0111
result : 2^2 + 2^1 + 1 = 7


collectionResult(7)

step2:
Decide which option is chosen

result:   0111
option1:  0001
&:        0001  select

result:   0111
option2:  0010
&:        0010  select

result:   0111
option3:  0100
&:        0100  select


result:   0111
option4:  1000
&:        0000  
```
