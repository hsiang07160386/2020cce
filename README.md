課堂考試
---------
```c
#include <stdio.h>
int main()
{
  int a,b,ans;
  scanf("%d%d",&a,&b);
  for(int i=1;i<=a;i++)
  {
    if(a%i==0 && b%i==0) ans=i;
  }
  printf("%d %d",a/ans,b/ans);
}
```
課堂教的
--------
利用指標*p1改變位址n1
```c
#include <stdio.h>
int main()
{
  int n1=10,n2=20,n3=30;
  printf("n1:%d n2:%d n3:%d\n",n1,n2,n3);
  int *p1=&n1;
  *p1=200;
  printf("n1:%d n2:%d n3:%d\n",n1,n2,n3);
  
  return 0;
}
```
利用指標*p1改變位址n1，增加*p2指標改變n3
```c
#include <stdio.h>
int main()
{
  int n1=10,n2=20,n3=30;
  printf("n1:%d n2:%d n3:%d\n",n1,n2,n3);
  
  int *p1=&n1;
  *p1=200;
  printf("n1:%d n2:%d n3:%d\n",n1,n2,n3);
  
  int *p2=&n3;
  *p2=300;
  printf("n1:%d n2:%d n3:%d\n",n1,n2,n3);
  
  return 0;
```
指標*p2叛逃改存在p1裡面的東西
```c
#include <stdio.h>
int main()
{
  int n1=10,n2=20,n3=30;
  printf("n1:%d n2:%d n3:%d\n",n1,n2,n3);
  
  int *p1=&n1;
  *p1=200;
  printf("n1:%d n2:%d n3:%d\n",n1,n2,n3);
  
  int *p2=&n3;
  *p2=300;
  printf("n1:%d n2:%d n3:%d\n",n1,n2,n3);
  
  p2=p1;
  *p2=400;
  printf("n1:%d n2:%d n3:%d\n",n1,n2,n3);
  
  return 0;
```
用陣列表示
```c
#include <stdio.h>
int main()
{
    int n[3]={10,20,30};
    printf("n[0]:%d n[1]:%d n[2]:%d\n",n[0],n[1],n[2]);

    int *p1=&n[0];
    *p1=200;
    printf("n[0]:%d n[1]:%d n[2]:%d\n",n[0],n[1],n[2]);

    int *p2=&n[2];
    *p2 =300;
    printf("n[0]:%d n[1]:%d n[2]:%d\n",n[0],n[1],n[2]);

    p2=p1;
    *p2=400;
    printf("n[0]:%d n[1]:%d n[2]:%d\n",n[0],n[1],n[2]);

    return 0;
}
```
第四周
-----
```c
#include <stdio.h>
struct DATA{///宣告
    float x,y,z;///定義裡面
} point1 ;
struct DATA points[5];
///point1是變數，長得像DATA
///DATA裡面有x,y,z
int main()
{
    for(int i=0;i<5;i++){
        points[i].x=i*10;
        points[i].y=20;
        points[i].z=0;
        printf("%f %f %f\n",points[i].x,points[i].y,points[i].z);
    }
}
```
