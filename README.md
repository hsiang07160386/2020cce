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
第十一周
-----
課堂作業1
```c
#include <stdio.h>
unsigned char c;
typedef unsigned char uchar;
uchar d;
int main()
{
    c='A';
    d=c;
    printf("%c",d);
}
```
課堂作業2
```c
#include <stdio.h>
typedef struct data
{
    char c;
    int ans;
}DATA;
DATA listA;
int main()
{
    listA.c='A';
    listA.ans=1;
    printf("%c %d\n",listA.c,listA.ans);
}
```
課堂作業3
```c
#include <stdio.h>
#include <stdlib.h>
int compare(const void*p1,const void*p2)
{///轉換成整數指標，準心看到的整數
    int d1 = *((int*)p1);
    int d2 = *((int*)p2);
    if(d1>d2) return 1;
    if(d1==d2) return 0;
    if(d1<d2) return -1;
}
int a[10]={4,8,3,7,5,2,9,1,6,10};
int main()
{
    qsort(a,10,sizeof(int),compare);
    for(int i=0;i<10;i++){
        printf("%d ",a[i]);
    }
}
```
課堂作業4-將原本改寫成字串指標
```c
#include <stdio.h>
#include <stdlib.h> //qsort()
#include <string.h> //strcmp()
char name[2000][80];
char others[80];
int compare( const void *p1, const void *p2 )
{//轉成「字串的指標」
	char *s1=(char*)p1;
	char *s2=(char*)p2;
	if(strcmp(s1,s2)>0) return 1;
	if(strcmp(s1,s2)==0) return 0;
	if(strcmp(s1,s2)<0) return -1;
}
int main()
{
	int N;
	scanf("%d", &N);
	for(int i=0; i<N; i++){
		scanf("%s", name[i] );
		gets( others );
	}
	
	qsort( name, N, 80, compare );
	
	printf("%s ", name[0] );//開頭
	int ans=1;
	
	for(int i=0; i<N-1; i++){
		if( strcmp( name[i], name[i+1] ) == 0 ){
			ans++;
		}else{
			printf("%d\n", ans );//結尾		
			printf("%s ", name[i+1] );//新的開頭
			ans=1;
		}
	}
	printf("%d\n", ans );//結尾
}
```
第十二週
---------
課堂作業1 CPE10062
```c
#include <stdio.h>
char line[2000];
int main()
{
	for(int t=0;gets(line);t++){
		int ans[256]={};
		char ascii[256];
		for(int i=0;i<256;i++) ascii[i]=i;
		
		for(int i=0;line[i]!=0;i++){
			char c=line[i];
			ans[c]++;
		}
		for(int i=0;i<256;i++){
			for(int j=i+1;j<256;j++){
				if(ans[i]>ans[j]){
					int temp=ans[i];
					ans[i]=ans[j];
					ans[j]=temp;
					char c=ascii[i];
					ascii[i]=ascii[j];
					ascii[j]=c;
				}
			}
		}
		if(t>0) printf("\n");
		for(int i=0;i<256;i++){
			if(ans[i]>0) printf("%d %d\n",ascii[i],ans[i]);
		}
	}
}
```
課堂作業2 CPE10062完整版
```c
#include <stdio.h>
char line[2000];
int main()
{
	for(int t=0;gets(line);t++){
		int ans[256]={};
		char ascii[256];
		for(int i=0;i<256;i++) ascii[i]=i;
		
		for(int i=0;line[i]!=0;i++){
			char c=line[i];
			ans[c]++;
		}
		for(int i=0;i<256;i++){
			for(int j=i+1;j<256;j++){
				if(ans[i]>ans[j]){
					int temp=ans[i];
					ans[i]=ans[j];
					ans[j]=temp;
					char c=ascii[i];
					ascii[i]=ascii[j];
					ascii[j]=c;
				}
				if(ans[i]==ans[j]&&ascii[i]<ascii[j]){///兩個頻率相同的時候
					int temp=ans[i];
					ans[i]=ans[j];
					ans[j]=temp;
					char c=ascii[i];
					ascii[i]=ascii[j];
					ascii[j]=c;
				}
			}
		}
		if(t>0) printf("\n");
		for(int i=0;i<256;i++){
			if(ans[i]>0) printf("%d %d\n",ascii[i],ans[i]);
		}
	}
}
```
