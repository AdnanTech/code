# Selection

A **selection** is used to make decisions on code to executre, depending on information such as a boolean condition being true or false

{% tabs %}
{% tab title="calcIf" %}
{% code title="calcIf.c" %}
```c
/***********************************************************************
* calcIf.c
* CLI application that operates as a simple calculator using if statements
* Version 1
* Adnan Quisar
* ********************************************************************/
#include <stdio.h>

void title(void);

_Bool testOperator(double num1,char op,double num2);

int main(void)
{
	_Bool loop = 1;
	double num1 = 0;
	double num2 = 0;
	char op ='x';
	title();
	while(loop)
	{
		printf("Enter number, operator, number: ");
		scanf("%lf %c %lf",&num1, &op, &num2);
		loop = testOperator(num1, op, num2);
	}
	printf("Program ended. Press enter to exit.");
	getchar();
	return0;
}

/* Display title */
void title(void)
{
	printf("Simple Calculator\n");
	printf("=================\n\n");
}

/* Test operator to select appropriate calculation and display
the answer and return true. If the operator is unknown return
false */
_Bool testOperator(double num1,char op,double num2)
{
	printf("%g %c %g = ",num1, op, num2);
	if(op == '+')
	{
		printf("%g",num1 + num2);
	}
	else if(op =='-')
	{
		printf("%g", num1 - num2);
	}
	else if(op =='*' ||op =='x' ||op =='X')
	{
	printf("%g",num1 * num2);
	}
	else if(op =='/' && num2 !=0)
	{
	printf("%g",num1 / num2);
	}
	else
	{
	return 0;
	}
	printf("\n\n");
	return 1;
}
```
{% endcode %}
{% endtab %}

{% tab title="calcSwitch" %}
```c
/***********************************************************************
* calcSwitch.c
* CLI application that operates as a simple calculator using
* switch case statements
* Version 1
* Adnan Quisar
* ********************************************************************/
#include <stdio.h>

void title(void);

_Bool testOperator(double num1,char op,double num2);

int main(void)
{
	_Bool loop = 1;
	double num1 = 0;
	double num2 = 0;
	char op ='x';
	title();
	while(loop)
	{
		printf("Enter number, operator, number: ");
		scanf("%lf %c %lf",&num1, &op, &num2);
		loop = testOperator(num1, op, num2);
	}
	printf("Program ended. Press enter to exit.");
	getchar();
	return0;
}

/* Display title */
void title(void)
{
	printf("Simple Calculator\n");
	printf("=================\n\n");
}

/* Test operator to select appropriate calculation and display
the answer and return true. If the operator is unknown return
false */
_Bool testOperator(double num1,char op,double num2)
{
	printf("%g %c %g = ",num1, op, num2);
	switch(op)
	{
		case '+':
			printf("%g",num1 + num2);
			break;
		case '-':
			printf("%g",num1 - num2);
			break;
		case '*':
		case'x':
		case'X':
			printf("%g",num1 * num2);
			break;
		case '/':
			if(num2 != 0)
			{
				printf("%g",num1 / num2);
			}
			break;
		default:
		return 0;
	}
	printf("\n\n");
	return 1;
}
```
{% endtab %}

{% tab title="wordCounter" %}
```c
/***********************************************************************
* wordCount.c
* CLI applicaiton that counts characters and words in a phrase 
* that are input from the keyboard.
* Version 1
* Adnan Quisar
**********************************************************************/

#include <stdio.h>

int main(void)
{
	int charcnt =0;
	int wordcnt =0;
	char ch;
	puts("Type in a phrase:");
	while((ch =getchar()) != '\n')			/* read chars until <enter> */
	{
		charcnt++;								/* count chars */
		if(ch ==' ')							/* if space */
		{
			wordcnt++;							/* count words */
		}
	}
	printf("\nCharacter count is %d", charcnt);
	printf("\nWord count is %d", wordcnt +1);
	return 0;
}
```
{% endtab %}
{% endtabs %}

