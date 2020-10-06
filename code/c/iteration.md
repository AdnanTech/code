# Iteration

* General form of a for loop: for \(init, condition, count\) { code }
* 
{% tabs %}
{% tab title="For" %}
{% code title="iterationFor.c" %}
```c
/***********************************************************************
* iterationFor.c
* CLI application that shows how for loops work
* Adnan Quisar
* October 2020
* ********************************************************************/

#include <stdio.h>

void iterationTestingOne(void);
void iterationTestingTwo(void);
void iterationTestingThree(void);
void iterationTestingFour(void);

int main(void)
{
    iterationTestingOne();
    printf("\n");
    iterationTestingTwo();
    printf("\n");
    iterationTestingThree();
    printf("\n");
    iterationTestingFour();
    return 0;                    
}

/* function to show how for loops work */
void iterationTestingOne(void)
{
    int x;
    for (x = 3; x > 0; x--)
    {
        printf("x = %d\n", x);
    }
}

/* function to show how for loops work */
void iterationTestingTwo(void)
{
    int i;
    while( i < 5 ) 
	{
        printf( "i = %d\n", i);
        i++;  
    }
}

/* function to show how for loops work */
void iterationTestingThree(void)
{
    int i, j = 10, sum;
    for( i = 0, sum = 0; i < 5; i++, j-- )
    {
        sum += i * j;
        printf("sum = %d\n", sum);
    }           
}

/* function to show how for loops work */
void iterationTestingFour(void)
{
    int x, sum=0, i;
    
    /* initialization  */
    for(x = 1; x <= 10; ++x) 
    /* Ask user 10 times(i.e. x takes 10 integers)  */
    {
        printf("Enter #%d: ",x); 
        scanf("%d",&i); 
        sum = sum + i;
    } 
    printf("Total Sum of 10 numbers = %d\n",sum); 
}
```
{% endcode %}
{% endtab %}

{% tab title="While" %}
{% code title="iterationWhile.c" %}
```c
/***********************************************************************
* iterationWhile.c
* CLI application that shows how while loops work
* Adnan Quisar
* October 2020
* ********************************************************************/

#include <stdio.h>

void iterationTestingOne(void);
void iterationTestingTwo(void);
void iterationTestingThree(void);
void iterationTestingFour(void);

int main(void)
{
    iterationTestingOne();
    printf("\n");
    iterationTestingTwo();
    printf("\n");
    iterationTestingThree();
    printf("\n");
    iterationTestingFour();
    return 0;                    
}

/* function to show how while loops work */
void iterationTestingOne(void)
{
    int count=0;
    while (count <= 3)
    {
        printf("%d ", count);
        count++;
    }
}

/* function to show how while loops work */
void iterationTestingTwo(void)
{
    int i=1, j=1;
    while (i <= 7|| j <= 3)
    {
        printf("%d %d\n",i, j);
        i++;
        j++;
    }
}

/* function to show how while loops work */
void iterationTestingThree(void)
{
    int i=0;
    do
    {
        printf("while vs do-while\n");
    }
    while(i == 1);
        printf("Out of loop");
}

/* function to show how while loops work */
void iterationTestingFour(void)
{
    int i=0;
    while(i == 1)
    {
        printf("while vs do-while");
    }
    printf("Out of loop");
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

