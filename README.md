#include<stdio.h>
#include <stdlib.h>
int r,c,found=0;
void search(char mat[r][c],int i,int j,char word[101],int index)
{
    if(i>=0 && i<r && j>=0 && j<c)
    {
    if(word[index]==NULL)
    {
        found=1;
        return;
    }
    if(mat[i][j]!=word[index]){
        return;
    }
    char backup=mat[i][j];
    mat[i][j]='-';
    search(mat,i,j-1,word,index+1);
    search(mat,i,j+1,word,index+1);
    search(mat,i-1,j,word,index+1);
    search(mat,i+1,j,word,index+1);
    mat[i][j]=backup;
    }
}
int main()
{
 scanf("%d %d",&r,&c);
 char mat[r][c],str[2],word[50];
 for(int i=0;i<r;i++)
 {
    for(int j=0;j<c;j++)
    {
        scanf("%s",str);
        mat[i][j]=str[0];
    }
 }
 scanf("%s",word);
 for(int i=0;i<r;i++)
 {
    for(int j=0;j<c;j++)
    {
        if(mat[i][j]==word[0])
        {
            search(mat,i,j,word,0);
            if(found){
                printf("yes");return;
            }
        }
    }
 }
 printf("no");
 
}
