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
