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

