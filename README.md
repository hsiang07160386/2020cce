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
第三周
------
利用*p來改變陣列裡的數值，p+2則是a[2]在往後數兩個
```c
#include <stdio.h>
int a[5]={0,10,20,30,40};
int main()
{
  for(int i=0;i<5;i++){
    printf("%d\n",a[i]);
  }
  printf("\n");
  int *p=&a[2];
  *p=222;
  for(int i=0;i<5;i++){
    printf("%d\n",a[i]);
  }
  printf("\n");
  p=p+2;
  *p=666;
  for(int i=0;i<5;i++){
    printf("%d\n",a[i]);
  }
}
```
利用void printAll()的函示庫來輸出
p--則是將p+2的位置往前一位在改變裡面的數
```c
#include <stdio.h>
int a[5]={0,10,20,30,40};
void printAll()
{
  for(int i=0;i<5;i++){
    printf("%d ",a[i]);
  }
  printf("\n");
}
int main()
{
  int *p=&a[2];
  *p=222;
  printAll();
  
  p=p+2;
  *p=666;
  printAll();
  
  p--;
  *p=555;
  printAll();
}
```
```c
#include <stdio.h>
#include <stdlib.h>
int a[10];
int main()
{
  int b[10];
  int *p=(int*)malloc(sizeof(int)*10);
  return 0;
}
```
第四周
------
```c
#include <stdio.h>
struct DATA{
  float x,y,z;
}a,b;
struct DATA c,d;
int main()
{
  struct DATA e;
  struct DATA f={1,2,3};
  
  printf("%f %f %f\n",a.x,a.y,a.z);
  printf("%f %f %f\n",b.x,b.y,b.z);
  printf("%f %f %f\n",c.x,c.y,c.z);
  printf("%f %f %f\n",d.x,d.y,d.z);
  printf("%f %f %f\n",e.x,e.y,e.z);
  printf("%f %f %f\n",f.x,f.y,f.z);
}
```
第七周
------
課堂考試-字串排序
```c
#include <stdio.h>
#include <string.h>
char a[100][10];
char temp[10];
int main()
{
	int n;
	scanf("%d",&n);
	for(int i=0;i<n;i++){
		scanf("%s",a[i]);
	}
	
	for(int i=0;i<n;i++){
		for(int j=i+1;j<n;j++){
			if(strcmp(a[i],a[j])>0){
				strcpy(temp,a[i]);
				strcpy(a[i],a[j]);
				strcpy(a[j],temp);
			}
		}
	}
	for(int i=0;i<n;i++){
		printf("%s\n",a[i]);
	}
}
```
字串排序-利用qsort改寫
```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
char a[100][10];
int compare(const void *p1,const void *p2)
{
	char *s1=(char*)p1;
	char *s2=(char*)p2;
	return strcmp(s1,s2);
}
int main()
{
	int n;
	scanf("%d",&n);
	for(int i=0;i<n;i++){
		scanf("%s",a[i]);
	}
	qsort(a,n,10,compare);
	for(int i=0;i<n;i++){
		printf("%s\n",a[i]);
	}
}
```
第八周
-----
10226
```c
#include <string.h>
#include <stdlib.h>
char tree[10000000][32];
int compare(const void *p1,const void *p2)
{
	return strcmp((char*)p1,(char*)p2);
}
int main()
{
	int T;
	scanf("%d\n\n",&T);
	int N=0;
	for(int i=0;  ;i++){
		char*now=gets(tree[i]);
		if(now==NULL){
			N=i;
			break;
		}
		if(strcmp(tree[i],"")==0){
			N=i;
			break;
		}
	}
	qsort(tree,N,32,compare);
	printf("%s ",tree[0]);
	int ans=1;
	for(int i=0;i<N-1;i++){
		if(strcmp(tree[i],tree[i+1])!=0){
			printf("%d\n",ans);
			printf("%s ",tree[i+1]);
			ans=1;
		}else ans++;
	}
	printf("%.4f\n",100*ans/(float)N);
}
```
