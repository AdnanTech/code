# Files

## Example 1

{% tabs %}
{% tab title="Raw" %}
```c
#include <stdio.h>
#include <stdlib.h>

#define NUMS 100

int main(void)
{
    FILE *fin;
    FILE *fout;
    int nums[NUMS];
    int i;
    intnoOfNums = 0;
    fin =fopen("nums.txt","r");
    if(!fin)
    {
        puts("Unable to open nums.txt");
        exit(1);
    }
        fout = fopen("copiedNums.txt","w");
    if(!fout)
    {
        puts("Unable to open copiedNums.txt");
        exit(1);
    }
    while(fscanf(fin,"%d",&nums[noOfNums]) == 1)
    {
        noOfNums++;
    }
    fprintf(stdout,"Total numbers read: %d\n\n",noOfNums);
    for(i =0;i <noOfNums;i++)
    {
        fprintf(stdout,"%10d",nums[i]);    /* stdout is the screen */
        fprintf(fout,"%10d",nums[i]);    /* fout is the file */
    }
    fprintf(stdout,"\n\nNumbers copied to copiedNums.txt\n");
    fclose(fin);        /* Close both files */
    fclose(fout);
    return 0;
}
```
{% endtab %}

{% tab title="Refactored" %}
```c
#include <stdio.h>
#include <stdlib.h>
#define NUMS 100

FILE *openFile(charfileName[],charfileMode[]);
int readNums(FILE *input,intnums[]);
void outputNums(FILE *output,intnums[],intsize);

int main(void)
{
    int nums[NUMS];
    intnoOfNums = 0;
    FILE *fin = openFile("nums.txt","r");
    FILE *fout =openFile("copiedNums.txt","w");
    noOfNums =readNums(fin, nums);
    outputNums(fout,nums,noOfNums);
    fclose(fin);    /* Close both files */
    fclose(fout);
    return 0;
}

/* Opens a file using file name and mode */
FILE *openFile(charfileName[], charfileMode[])
{
    FILE *filePointer = fopen(fileName,fileMode);
    if(!filePointer)
    {
        printf("Unable to open %s\n",fileName);
        exit(1);
    }
    return filePointer;
}
    
/* Read numbers from file and store in an array */
int readNums(FILE *input,intnums[])
{
    int noOfNums = 0;
    while(fscanf(input,"%d",&nums[noOfNums])==1)
    {
        noOfNums++;
    }
    fprintf(stdout,"Total numbers read: %d\n\n",noOfNums);
    return noOfNums;
}

/* Output numbers to screen and file */
void outputNums(FILE *output,intnums[], intsize)
{
    int i;
    for(i = 0;i < size; i++)
    {
        fprintf(stdout,"%10d",nums[i]);
        fprintf(output,"%10d",nums[i]);
    }
    fprintf(stdout,"\n\nNumbers copied to copiedNums.txt\n");
}
```
{% endtab %}
{% endtabs %}

## Example 2

{% tabs %}
{% tab title="Create File" %}
```c
#include <stdio.h>
#include <stdlib.h>

#define NAME_LEN 25

FILE *openFile(charfileName[], charfileMode[]);
int getNoOfStudents(void);
void getStudentDataWriteToFile(FILE *fptr);
void emptyBuffer(void);

int main(void)
{
    FILE *fptr = openFile("studentMark.txt","w");
    int noOfStudents = getNoOfStudents();
    while(noOfStudents >0)
    {
        getStudentDataWriteToFile(fptr);
        noOfStudents--;
    }
    fclose(fptr);
    return 0;
}

/* opens a file using a file name */
FILE *openFile(charfileName[],charfileMode[])
{
    FILE *filePointer = fopen(fileName,fileMode);
    if(!filePointer)
    {
        printf("Unable to open %s\n",fileName);
        exit(1);
    }
    return filePointer;
}

/* get number of students from the keyboard */
int getNoOfStudents(void)
{
    int num = 0;
    printf("Enter number of students: ");
    scanf("%d",&num);
    emptyBuffer();
    return num;
}

/* get student data from the keyboard and write to file */
void getStudentDataWriteToFile(FILE *fptr)
{
    char name[NAME_LEN];
    int mark = 0;
    printf("\nEnterstudent name: ");
    scanf("%24[^\n]", name);
    printf("Enter mark        : ");
    scanf("%d",&mark);
    emptyBuffer();
    fprintf(fptr,"%s:%d\n", name, mark);
}

/* Clear any characters up to and including the enter key */
void emptyBuffer(void)
{
    while(getchar()!='\n')
    {
        ;
    }
}
```
{% endtab %}

{% tab title="Read File" %}
```c
#include <stdio.h>
#include <stdlib.h>

struct student
{
    char name[25];
    int mark;
};

int main(void)
{
    FILE *fptr;
    struct student rec[200];
    int noOfStudents = 0;
    fptr = fopen("studentMark.txt","r");
    if(!fptr)
    {
        puts("Unable to open studentMark.txt");
        exit(1);
    }
    while(fscanf(fptr,"%24[^:]:%d\n", rec[noOfStudents].name,&rec[noOfStudents].mark) == 2)
    {
        printf("%-24s %2d\n",rec[noOfStudents].name,rec[noOfStudents].mark);
        noOfStudents++;
    }
    fclose(fptr);
    return 0;
}
```
{% endtab %}
{% endtabs %}

## Treating files as strings

### sscanf\(\)

```c
#include<stdio.h>

int main(void)
{
    char packedDataInAString[]=
    "the Great Cholesterol Con,"
    "Dr Malcolm Kendrick,John Blake Publishing Ltd,2007,7.99,"
    "978-1-84454-610-7";
    
    char title[35] = "";
    char author[35] = "";
    char publisher[35] = "";
    int year = 0;
    double price =0.0;
    char isbn[20]= "";
    sscanf(packedDataInAString,
        "%[^,],%[^,],%[^,],%d,%lf,%[^,]",
        title,author,publisher,&year,&price,isbn);
    printf("A great book \"%s\".\n\n", packedDataInAString);
    printf("The book \"%s\" by %s\n",title,author);
    printf("is published by %s in %d.\n\n",publisher,year);
    printf("Price: %c%.2f.\n\n",156, price);
    printf("ISBN: %s\n\n",isbn);
    return 0;
}
```

### sprintf\(\)

```c
#include<stdio.h>

int main()
{
    char target[50] = "";
    char firstName[]= "John";
    charinitial ='F';
    charlastName[] ="Kennedy";
    int bday =29;
    int bmonth = 5;
    int byear = 1917;
    int dday =22;
    int dmonth =11;
    int dyear =1963;
    printf("\nPresident: %s %c %s\n",firstName,initial,lastName);
    printf("Born: %02d/%02d/%d\n",bday,bmonth,byear);
    printf("Died: %02d/%02d/%d\n",dday,dmonth,dyear);
    sprintf(target,"%s %c %s %02d/%02d/%d-%02d/%02d/%d",
        firstName,initial,lastName,bday,bmonth,byear,dday,dmonth,dyear);
    printf("\nAll in one string\n");
    printf("The value in the target string is: %s.\n",target);
    return 0;
}
```

## Complex Program Example

```c
#include <stdio.h>
#include <stdlib.h>
#include <conio.h>                               /* non-ANSI standard */
#include <string.h>

void enterPin(char inputPin[]);
_Bool isValidPin(char inputPin[],char pin[]);
FILE *openFile(char fileName[],char fileMode[]);
void printFile(FILE *input);

int main(void)
{
    FILE *fp;
    char pin[]="1234";
    char inputPin[]="0000";
    while(!isValidPin(inputPin,pin))
    {
        enterPin(inputPin);
    }
    fp = openFile("abc.txt","r");
    printFile(fp);
    fclose(fp);
    return 0;
}

/* enter pin hiding entered characters */
void enterPin(char inputPin[])
{
    int i;
    printf("Enter pin: ");
    for(i = 0;i < 4; i++)
    {
        inputPin[i] = getch();
        /* getch() is non-ANSI standard */
        putchar('*');
    }
    inputPin[i]='\0';
}

/* return true if pins are equal else return false */
_Bool isValidPin(char inputPin[],char pin[])
{
    if(strcmp(pin,inputPin)!=0)
    {
        printf("\nERROR -Invalid pin\n");
        return 0;
    }return 1;
}

/* opens a file using a file name */
FILE *openFile(char fileName[],char fileMode[])
{
    FILE *filePointer = fopen(fileName,fileMode);
    if(!filePointer)
    {
        printf("Unable to open %s\n",fileName);
        exit(1);
    }
    return filePointer;
}

/* read each file line and display on screen */
void printFile(FILE *input)
{
    char line[81];
    puts("\n");
    while(fscanf(input,"%80[^\n]%*c", line) == 1)
    {
        printf("%s\n",line);
    }
}
```

## Reading binary dumps

```c
#include <stdio.h>
#include <stdlib.h>

void openFile(char filename[],char modeOp[],char mode[], int errNo);
void countCharacters(FILE *fp,char mode[]);

int main(void)
{
    char filename[30];
    printf("Enter filename: ");
    scanf("%s", filename);
    openFile(filename,"r","Text", 1);
    openFile(filename,"rb","Binary",2);
    return 0;
}

/* Open in either text or binary and count chars */
void openFile(char filename[],char modeOp[],char mode[],int errNo)
{
    FILE *fp;
    if(!(fp =fopen(filename, modeOp)))
    {
        printf("Can't open file %s.\n", filename);
        exit(errNo);
    }
    countCharacters(fp, mode);
    fclose(fp);
}

/* Count characters in file */
void countCharacters(FILE *inputFile,char mode[])
{
    char ch;
    int charCount = 0;
    int returnCount = 0;
    int lineCount = 0;
    while(fscanf(inputFile,"%c", &ch) == 1)
    {
        charCount++;
        /* Count characters */
        if(ch =='\r')
        {
            returnCount++;
            /* Count CRs */
        }
        else if(ch =='\n')
        {
            lineCount++;
            /* Count LFs */
        }
    }
    printf("File contains %d chars, %d CRs and %d LFs when opened in"" %s mode.\n",
                charCount, returnCount, lineCount, mode);
}
```

