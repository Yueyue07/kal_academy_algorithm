# Week 4 May 14th Class Notes

## dictionary
> dictionary from hash table

**steps**:
1. hashcode(key), key is string and hashcode return a unique integer -2^31 ~ 2^31

2. abs(step1) 0 ~ 2^31  

3. step2 % size of array (reminder < size of array; size of array is prime number)

**summary of dictionary**:
1. collision chance is 20% if array.length is prime number

2. computation will be heavy if change the size of array
