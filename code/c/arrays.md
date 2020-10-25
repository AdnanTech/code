# Arrays

## Arrays

An **array** is a collection of data items, all of the same type, accessed using a common name. Arrays are declared as a fixed length.

{% tabs %}
{% tab title="simpleArray" %}
{% code title="simpleArray.c" %}
```c
/***********************************************************************
* simpleArray.c
* CLI application that shows an example of arrays
* Adnan Quisar
* Version 1
* ********************************************************************/

#include <stdio.h>
 
int main ()
{
   int n[10]; /* n is an array of 10 integers */
   int i, j;
 
   /* initialize elements of array n to 0 */         
   for (i = 0; i < 10; i++ )
   {
      n[i] = i + 100; /* set element at location i to i + 100 */
   }
   
   /* output each array element's value */
   for (j = 0; j < 10; j++ )
   {
      printf("Element[%d] = %d\n", j, n[j] );
   }
 
   return 0;
}

/* Result
Element[0] = 100
Element[1] = 101
Element[2] = 102
Element[3] = 103
Element[4] = 104
Element[5] = 105
Element[6] = 106
Element[7] = 107
Element[8] = 108
Element[9] = 109
*/
```
{% endcode %}
{% endtab %}

{% tab title="avgTemperature" %}
{% code title="avgTemperature" %}
```c
/***********************************************************************
* avgTemperature.c
* CLI application that calculates the average temperature for a week
* Adnan Quisar
* Version 1
* ********************************************************************/

#include <stdio.h>
#define WEEK 7

void getTemperatures(int temps[]);

double calculateAverage(int temperature[]);

int main(void)
{
    int temper[WEEK];                /* Array declaration */
    getTemperatures(temper);        /* temper is a pointer to the array */
    printf("\nAverage is %.1f.\n\n", calculateAverage(temper));
    return 0;
}

/* Populates array of temperatures ie temper in main.
* Normal parameters are passed by value but array parameters are
* passed by reference */
void getTemperatures(int temps[])
{
    int day;
    for(day = 0; day < WEEK; day++)
    {
        printf("Enter temperature for day %d: ", day);
        scanf("%d",&temps[day]);
    }
}

/* calculates average temperature */
double calculateAverage(inttemperature[])
{
    int day;
    doublesum = 0;
    for(day = 0; day < WEEK; day++)
    {
        sum += temperature[day];
    }
    return sum / WEEK;
}
```
{% endcode %}
{% endtab %}

{% tab title="passingStrings" %}
{% code title="passingStrings" %}
```c
/***********************************************************************
* passingStrings.c
* CLI application that passes an array of characters (string) to a 
* function and prints it to the consoles
* Adnan Quisar
* Version 1
* ********************************************************************/

#include <stdio.h>
#include <string.h>
#include <ctype.h>

void sort(char *strings[], int n);

int main()
{
    char *string_database[4]={'\0'};
    string_database[0]="Florida";
    string_database[1]="Oregon";
    string_database[2]="California";
    string_database[3]="Georgia";
    sort(string_database, 4);
    return 0;
}

void sort(char *strings[], int n)
{
    int i;
    for (i = 0; i < n; i++)
    {
        printf("String %d: %s\n", i, strings[i]);
    }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Passing Array Examples

{% tabs %}
{% tab title="Passing some values from an array" %}
```c
#include <stdio.h>

int main()
{
    int ageArray[] = {2, 8, 4, 12};

    // Passing second and third elements to display()
    display(ageArray[1], ageArray[2]); 
    return 0;
}

void display(int age1, int age2)
{
    printf("%d\n", age1);
    printf("%d\n", age2);
}

```
{% endtab %}

{% tab title="Passing an Unsized Array" %}
```c
#include <stdio.h>
float calculateSum(float age[]);

int main() {
    float result, age[] = {23.4, 55, 22.6, 3, 40.5, 18};

    // age array is passed to calculateSum()
    result = calculateSum(age); 
    printf("Result = %.2f", result);
    return 0;
}

float calculateSum(float age[]) {

  float sum = 0.0;

  for (int i = 0; i < 6; ++i) {
		sum += age[i];
  }
```
{% endtab %}

{% tab title="Passing an Array with Pointers" %}
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void sort(char *strings[], int n);

int main()
{
    char *string_database[4]={'\0'};
    string_database[0]="Florida";
    string_database[1]="Oregon";
    string_database[2]="California";
    string_database[3]="Georgia";
    sort(string_database, 4);
    return 0;
}

void sort(char *strings[], int n)
{
    int i;
    for (i = 0; i < n; i++)
    {
        printf("String %d: %s\n", i, strings[i]);
    }
}
```
{% endtab %}

{% tab title="Passing 2D Arrays" %}
```c
#include <stdio.h>

void displayNumbers(int num[2][2]);

int main()
{
    int num[2][2];
    printf("Enter 4 numbers:\n");
    for (int i = 0; i < 2; ++i)
        for (int j = 0; j < 2; ++j)
            scanf("%d", &num[i][j]);

    // passing multi-dimensional array to a function
    displayNumbers(num);
    return 0;
}

void displayNumbers(int num[2][2])
{
    printf("Displaying:\n");
    for (int i = 0; i < 2; ++i) {
        for (int j = 0; j < 2; ++j) {
           printf("%d\n", num[i][j]);
        }
    }
}
```
{% endtab %}
{% endtabs %}

## More complex Array Examples

{% tabs %}
{% tab title="Plotting Graphs \(2d array\)" %}
{% code title="graphPlottingArrays.c" %}
```c
/***********************************************************************
* graphPlottingArrays.c
* Plot coordinates on a grid using a 2 dimensional array
* Adnan Quisar
* October 2020
* ********************************************************************/

#include <stdio.h>
#define HEIGHT 5
#define WIDTH 10

void fillMatrixWithDots(charmatrix[][WIDTH]);
void playGame(charmatrix[][WIDTH]);
void displayMatrix(charmatrix[][WIDTH]);

int main(void)
{
    char matrix[HEIGHT][WIDTH];
    fillMatrixWithDots(matrix);
    printf("Enter coordinates in form x, y (4, 2).\n");
    printf("Use negative numbers to quit.\n");
    playGame(matrix);
    return 0;
}

/* Fill each cell with a dot */
void fillMatrixWithDots(charmatrix[][WIDTH])
{
    int x, y;
    for(y =0;y <HEIGHT;y++)        /* For each row */
    {
        for(x =0;x <WIDTH;x++)        /* and each column */
        {
            matrix[y][x]='.';    /* fill each cell with a dot */
        }
    }
}

/* Get next move */
void playGame(charmatrix[][WIDTH])
{
    int x, y;
    fillMatrixWithDots(matrix);
    printf("Enter coordinates in form x, y (4, 2).\n");
    printf("Use negative numbers to quit.\n");
    while(x >=0)            /* Until negative ... */
    {
        displayMatrix(matrix);
        printf("Coordinates: ");
        scanf("%d,%d",&x,&y);
        if((x >-1) && (x <WIDTH) && (y >-1) && (y <HEIGHT))
        {
            matrix[y][x]='\xB0';        /* Only if valid coordinates */
        }
    }
}

/* Display result of game so far */
void displayMatrix(charmatrix[][WIDTH])
{
    int x, y;
    for(y = 0;y < HEIGHT; y++)        /* For each row */
    {
        for(x = 0;x < WIDTH; x++)    /* and each column */
        {
            printf("%c ",matrix[y][x]);    /* display cell */
        }
        printf("\n");
    }
}
```
{% endcode %}
{% endtab %}

{% tab title="Calculating change" %}
{% code title="calculateChange.c" %}
```c
/***********************************************************************
* calculateChange.c
* Calculate coinage
* Demonstrate initialising arrays and operator sizeof
* Using 4.56 with doubles shows rounding errors
* Adnan Quisar
* October 2020
* ********************************************************************/

#include <stdio.h>

int main(void)
{
    int table[] = {50,20,10,5,2,1};
    int index, pence, quantity, maxIndex;
    doublepounds;
    printf("Enter amount in pounds and pence: ");
    scanf("%lf",&pounds);        /* Maybe rounding errors */
    pence = pounds *100;    /* Rounding errors increased */
    printf("pence = %d\n\n", pence);
    maxIndex = sizeoftable / sizeoftable[0];    /* No of array slots */
    for(index = 0;index < maxIndex; index++)
    {
        quantity = pence / table[index];
        pence %= table[index];
        printf("%2d %2dp coin(s)\n", quantity, table[index]);
    }
    return 0;
}
```
{% endcode %}
{% endtab %}

{% tab title="" %}
{% code title="averageTemperature.c" %}
```c
/***********************************************************************
* averageTemperature.c
* Averages arbitrary number of temperatures and checks for array
* overflow
* Adnan Quisar
* October 2020
* ********************************************************************/

#include <stdio.h>
#include <ctype.h>                                   /* For isdigit() */
#include <stdlib.h>                                     /* For atof() */
#define MAXDAYS 31

int getTemps(floattemps[]);
float calcAvg(floattemps[], intnoDays);
void emptyBuffer(void);

int main(void)
{
    float temper[MAXDAYS];
    intdays = 0;
    days = getTemps(temper);
    printf("\nAverage is %.2f\n\n", calcAvg(temper,days));
    return 0;
}    
/* Populates array of temperatures */
int getTemps(floattemps[])
{
    charinput[5];
    intday = 0;
    printf("Type a letter to exit program.\n");
    do
    {
        printf("Enter temperature for day %d: ", day +1);
        scanf("%4s",input);        /* 4 characters only extracted */
        emptyBuffer();            /* Ignore any extra characters */
        if(isdigit(input[0]))    /* If first character is digit */
        {
        temps[day++] = atof(input);  /* convert str in float */
        }
        if(day == MAXDAYS)        /* Check for full temperature table */
        {
            printf("Maximum number of temperatures entered.\n");
            break;
            }
    }while(isdigit(input[0]));    /* Repeat if 1st char is digit */
    return day;
}

/* Calculate  average temperature */
float calcAvg(floattemps[], intnoDays)
{
    floatsum = 0.0f; intday = 0;
    for(day = 0; day < noDays; day++)
    {
        sum += temps[day];
    }
    return sum / noDays;
}

/* Empty the keyboard buffer */
void emptyBuffer(void)
{
    while(getchar()!='\n')
    {
    ;
    }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

