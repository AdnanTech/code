# Strings Functions

## Inputting strings: gets\(\), fgets\(\), puts\(\), scanf\(\)

```c
#include <stdio.h>
#define LIM 11

voidemptyBuffer(void);

int main(void)
{
    char fullname[LIM];
    
    /* gets() was the traditional way to get string input. It is now
    * considered bad practice as it has no overflow protection. */
    puts("Type: Fred Smith");
    gets(fullname);        /* Now dropped from the latest standard */
    printf("Using gets(): %s\n\n", fullname);
    /* The fgets() function protects against array overflow. It takes
    * a line of text from a file. It will stop if the array is full. */
    puts("Type: Fred Smith");
    fgets(fullname, sizeof(fullname), stdin);
    emptyBuffer();
    printf("Using fgets(): %s\n\n", fullname);
    /* %s takes in the first word only and can guard against overflow.*/
    puts("Type: Fred Smith");
    scanf("%10s",fullname);        /* 10 is array size -1 */
    emptyBuffer();
    printf("Using scanf() with %%10s: %s\n\n", fullname);
    /* %[set of characters] stops when input character not is set.
    * %[^set of characters] stops when input character is in set. */
    puts("Type: Fred Smith");scanf("%10[^\n]", fullname);    /* 10 is array size -1 */
    emptyBuffer();
    printf("Using scanf() with %%10[^\\n]: %s\n\n", fullname);
    return 0;
}

/* Ignore all characters up to and including the enter key */
void emptyBuffer(void)
{
    while(getchar()!='\n')
    {
        ;
    }
}
```

## Custom scanf\(\)

Not recommended, although possible.

```c
#include <stdio.h>
#define LIM 11

void mygetstring(charinput[]);
void emptyBuffer(void);

int main(void)
{
    char fullname[LIM];
    puts("Type: Fred Smith");
    mygetstring(fullname);
    printf("Using user defined function mygetstring(): %s\n\n", fullname);
    return 0;
}

/* Stores all characters up to end of line and terminates with '\0' */
void mygetstring(charinput[])
{
    int index = 0;
    while((input[index]=getchar())!='\n')
    {
        index++;
        if(index ==LIM)
        {
            index--;
            emptyBuffer();
            break;
        }
    }
    input[index] = '\0';        /* Overwrites enter key with NULL */
}

/* Ignore all chars up to and including the enter key */
void emptyBuffer(void)
{
    while(getchar()!='\n')
    {
        ;
    }
}
```

## Comparing Strings using a custom function

```c
#include <stdio.h>
int equalString(charname1[], charname2[]);

int main(void)
{
    char name1[]={'F','r','e','d','\0'};
    char name2[]="Fred";
    printf("name1: %s\n", name1);
    printf("name2: %s\n\n", name2);
    if(name1 ==name2)
    {
        printf("name1 == name2 Equal!\n\n");    /* false */
    }
    else
    {
        printf("name1 == name2 Not equal!\n\n");    /* true */
    }
    printf("but\n\n");
    if(equalString(name1,name2))
    {
        printf("equalString(name1, name2) gives Equal!\n\n");    /* true */
    }
    else
    {                        /* false */
    printf("equalString(name1, name2) gives Not equal!\n\n");
    }
    return 0;
}

/* To check equality, compare each character in turn */
int equalString(charname1[], charname2[])
{
    int index = 0;
    _Bool equal =1;        /* set equal to true */
    do
        {
        if(name1[index]!= name2[index])    /* if characters not equal, */
        {
            equal = 0;    /* set equal to false */
        }
    }while(name1[index++]!='\0');
    return equal;
}
```

## &lt;string.h&gt; header file

### strcpy\(\) 1

strcpy\(\) deletes a character based on it's position in a string.

```c
#include <stdio.h>
#include <string.h>                       /* Header file for strcpy() */

int main(void)
{
    char string[81];
    int position;
    printf("Type string: ");
    scanf("%80[^\n]", string);
    printf("Enter delete position: ");
    scanf("%d",&position);        
    /* Overwrites char at position with char at position + 1 and
    * continues to end of string. */
    strcpy(&string[position], &string[position+1]);
    puts(string);
    return 0;
}
```

### itoa\(\)

itoa\(\) converts a number into a string of a specific number base.

```c
#include <stdio.h>
#include <stdlib.h>                                     /* for itoa() */

int main(void)
{
    int number;
    char string[33];
    printf("Enter a number: ");
    scanf("%d", &number);
    itoa(number,string,2);    /* 2 for binary */
    printf("binary: \t%s\n", string);
    itoa(number,string,8);        /* 8 for octal */
    printf("octal: \t\t%s\n", string);
    itoa(number, string,16);        /* 16 for hexadecimal */
    printf("hexadecimal: \t%s\n", string);
    itoa(number,string,10);        /* 10 for denary */
    printf("denary: \t%s\n", string);
    return 0;
}
```

### strlen\(\)

```c
#include <stdlib.h>
#include <string.h>                                   /* for strlen() */

int main(void)
{
    int number, i;
    char string[33];
    printf("Enter a number: ");
    scanf("%d",&number);
    itoa(number, string,10);
    printf("Your number %s reversed is ", string);
    for(i = strlen(string) - 1; i >= 0; i--)
    {
        printf("%c", string[i]);
    }
    printf("\n\n");
    return 0;
}
```

### strcmp\(\)

```c
#include <stdio.h>
#include <string.h>

in tmain (void)
{
    int returned;
    char str1[]="Fred Jones";
    char str2[]="Freda Smith";
    char str3[]="Fred Jones";
    returned = strcmp(str1, str2);
    printf("returned is %d\n\tso %s comes before %s in lexical ""order.\n\n", returned, str1, str2);
    returned = strcmp(str1, str3);
    printf("returned is %d\n\tso%s is equivalent to %s in lexical ""order.\n\n", returned, str1, str3);
    returned = strcmp(str2, str3);
    printf("returned is %d\n\tso %s and %s not in lexical order.\n\n", returned, str2, str3);
    printf("\n");
    return 0;
}
```

### Combining strcpy\(\) and strcmp\(\)

```c
#include <stdio.h>
#include <string.h>
#define MAX 100
#define LEN 40

int initialise(charlist[][LEN]);
void getName(charname[]);
_Bool isMember(charname[], charlist[][LEN], intnum);
void action(_Bool member);

int main(void)
{
    int numOfMembers = 0;
    intmember =0;            /* set member to false */
    char name[LEN];
    charlist[MAX][LEN];
    numOfMembers = initialise(list);
    getName(name);
    member = isMember(name, list, numOfMembers);
    action(member);
    return 0;
}

/* setup list of members */
int initialise(charlist[][LEN])
{
    int index = 0;
    strcpy(list[index++], "Annie Smith");        /* insert a member */
    strcpy(list[index++], "Becky Jones");
    strcpy(list[index++], "Carol Morgan");
    strcpy(list[index++], "Eve Evans");
    strcpy(list[index++], "Diane Parry");
    return index;            /* return number of members */
}

/* getname limited to 39 characters */
void getName(charname[])
{
    printf("Enter your name: ");
    scanf("%39[^\n]", name);
}

/* check if member */
_Bool isMember(charname[], charlist[][LEN], intnum)
{
    _Bool valid = 0;        /* set valid to false */
    int i;
    for(i =0; i < num; i++)
    {
        if(strcmp(list[i],name) == 0)            /* compare names */
        {
            valid = 1;            /* set valid to true */
            break;
        }
    }
    return valid;
}

/* action taken */
void action(_Bool member)
{
    if(member)
    {
        printf("You may enter, oh honoured one.\n");
    }
    else
    {
        printf("Security!  Remove this person!\n");
    }
}
```

### strcpy\(\) 2

```c
#include <stdio.h>
#include <string.h>

int main(void)
{
    char s1[] = "ABCDEFG";
    char s2[] = "xyz";
    printf("Before strcpy():\n");
    printf("\ts1 = \"%s\", length = %d.\n", s1, (int)strlen(s1));
    printf("\ts2 = [%s], length = %d.\n", s2, (int)strlen(s2));
    strcpy(s1, s2);
    printf("After strcpy():\n");
    printf("\ts1 = [%s], length = %d.\n", s1, (int)strlen(s1));
    printf("\ts2 = [%s], length = %d.\n", s2, (int)strlen(s2));
    printf("\nsizeof s1 is still %d. ", (int)sizeofs1);
    printf("\nsizeof s2 is still %d.\n\n", (int)sizeofs2);
    return 0;
}
```

