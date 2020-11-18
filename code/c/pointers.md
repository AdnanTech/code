# Pointers

A **pointer** is a variable whose value is the address of another variable, i.e., direct address of the memory location.

{% tabs %}
{% tab title="Code" %}
{% code title="pointers.c" %}
```c
#include <stdio.h>

int main ()
{

   int  var = 20;   /* actual variable declaration */
   int  *ip;        /* pointer variable declaration */

   ip = &var;  /* store address of var in pointer variable*/

   printf("Address of var variable: %x\n", &var  );

   /* address stored in pointer variable */
   printf("Address stored in ip variable: %x\n", ip );

   /* access the value using the pointer */
   printf("Value of *ip variable: %d\n", *ip );

   return 0;
}
```
{% endcode %}
{% endtab %}

{% tab title="Result" %}
```
Address of var variable: c95d8844
Address stored in ip variable: c95d8844
Value of *ip variable: 20
```
{% endtab %}
{% endtabs %}

## Example

Two programs that will yield a different result, as passing the pointers means you are passing by reference. Whereas 

{% tabs %}
{% tab title="Without Pointers" %}
```text
#include <stdio.h>

void given2(int xx,int yy);

int main(void)
{
    int x =4 , y = 7;
    
    given2(x, y);    /* pass by value ie copies */
    printf("x is %d, y is %d\n\n",x,y);
    return 0;
}

/* Copies of x and y are passed to xx and yy respectively */
void given2(int xx,int yy)
{
    xx += 2;        /* xx and yy are changed but not x or y */
    yy +=3;
}
```
{% endtab %}

{% tab title="With Pointers" %}
```
#include <stdio.h>

void rets2(int *xx, int *yy);

int main(void)
{
    int x = 4, y = 7;
    rets2(&x ,&y);    /* pass by reference */
    printf("x is %d, y is %d\n\n", x, y);
    return 0;
}

/* Addresses of x and y are passed to the pointers xx and yy*/
void rets2(int *xx,int *yy)
{
    /* change the values of dereferenced xx and dereferenced yy */
    *xx += 2;        /* change the values of x and y */
    *yy += 3;
}
```
{% endtab %}
{% endtabs %}

## Example 2

Array notation with and without pointers

{% tabs %}
{% tab title="Without Pointers" %}
```c
#include <stdio.h>

int main(void)
{
    intnums[]= { 92,81,70,69,58 };
    int i;
    intnoOfInts = sizeof(nums)/sizeof(nums[0]);
    for(i =0; i <noOfInts; i++)
    {
        printf("%d\t", nums[i]);
    }
    printf("\n\n");
    return 0;
}
```
{% endtab %}

{% tab title="With Pointers" %}
```c
#include <stdio.h>

int main(void)
{
    int nums[]= { 92,81,70,69,58 };
    int i;
    intnoOfInts = sizeof(nums)/sizeof(nums[0]);
    for(i =0; i < noOfInts; i++)
    {    /* The [] notation has been replaced by pointer arithmetic */
        printf("%d\t",*(nums +i));
    }
    printf("\n\n");
    return 0;
}
```
{% endtab %}

{% tab title="Pointer allocated to var" %}
```c
#include <stdio.h>

in tmain(void)
{
    int nums[]= { 92,81,70,69,58 };
    int i;
    int *ptr = nums;
    int noOfInts = sizeof(nums) / sizeof(nums[0]);
    for(i =0; i < noOfInts; i++)
    {
        /* Used a dereferenced pointer, then increment the pointer */
        printf("%d\t", *(ptr++));
    }
    printf("\n\n");
    return 0;
}
```
{% endtab %}
{% endtabs %}

## Example 3

Showing the types of pointer notation as well as the format specifier for a pointer

```text
#include <stdio.h>

int main(void)
{
    int x = 4,y = 7;    /* Normal variables */
    int *xptr, *yptr;    /* Pointers */
    
    printf("x starts at %4d \t y starts at %4d\n", x, y);
    xptr = &x;    /* Pointer assigned the address of x */
    yptr = &y;
    *xptr +=7;    /* Dereferenced pointer, so 7 is added to x */
    *yptr += 7;
    
    printf("\nAfterthe dereferenced pointer access:\n\n");
    printf("x now is %7d \t y now is %7d\n", x, y);
    printf("xptr is %p \t yptr is %p\n", xptr, yptr);
    printf("*xptr is %7d \t *yptr is %7d\n\n", *xptr, *yptr);
    return 0;
}
```

