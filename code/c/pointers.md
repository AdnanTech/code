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

