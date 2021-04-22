# 範例學習C 程式設計
```
本單元規劃以 範例  快速引導學生掌握基礎 C 程式語法
更多完整內容仍需參考學習資源或買書學習
```

![階段式學習C程式設計 綱要](階段式學習C程式設計.md)


```
有興趣的同學也可以 參加 
APCS-大學程式設計先修檢測
https://apcs.csie.ntnu.edu.tw/

TOI 臺灣國際資訊奧林匹亞競賽
Taiwan Olympiad in Informatics
請參考網站說明 https://toi.csie.ntnu.edu.tw/
```

```
持續編修中
```
# 1.輸出入
```
#include <stdio.h>
 
/* 註解語法  */ 

int main()
{
    printf("Hello, CTFer! \n");
    return 0;
}
```
```
https://pydoing.blogspot.com/2010/07/c-stdio.html
```

## 【字元】輸出入 ==> getchar(), putchar()
```
#include <stdio.h>
 
int main( )
{
   int c;
 
   printf( "Enter a value :");
   c = getchar( );
 
   printf( "\nYou entered: ");
   putchar( c );
   printf( "\n");
   return 0;
}
```
## 【字串】輸出入  ==> gets(),  puts()
```
#include <stdio.h>
 
int main( )
{
   char str[100];
 
   printf( "Enter a value :");
   gets( str );
 
   printf( "\nYou entered: ");
   puts( str );
   return 0;
}
```

# 5.迴圈 
```
for   
while     
do.. while
```
## for loop(迴圈)  ==> 計算n!
```
#include <stdio.h>

int main(void)
{
	int n;
	int total = 1;
	int i;

	scanf("%d", &n);

	for(i = 1; i <= 10; i++)
		total *= i;

	printf("the result is %d\n", total);

	return 0;
}
```
## while loop ==> 計算n!
```
#include <stdio.h>

int main(void)
{
	int n;
	int mul = 1;
	int i;

	scanf("%d", &n);
	
	i = 1;
	while(i <= n)
	{
		mul *= i;
		i++;
	};

	printf("the result is %d\n", mul);

	return 0;
}
```
## do ..while .. ==> 計算n!
```
//do_while
#include <stdio.h>

int main(void)
{
	int n;
	int mul = 1;
	int i;

	scanf("%d", &n);
	
	i = 1;
	do{
		mul *= i;
		i++;
	}while(i <= n);

	printf("the result is %d\n", mul);

	return 0;
}
```
# 6.函數

```
#include <stdio.h>
 
int ifactorial(int z)
{
	int mul = 1, i = 1;
	while(i <= z)
	{
		mul *= i;
		i++;
	};
	return mul;
}

int  main()
{
    int i = 4;
    printf("%d 的階乘為%d\n", i, ifactorial(i));
    return 0;
}
```

## 遞迴函數 ==> 計算n!
```
#include <stdio.h>
 
double factorial(unsigned int i)
{
   if(i <= 1)
      return 1;
   else   return i * factorial(i - 1);
}

int  main()
{
    int i = 15;
    printf("%d 的階乘為%f\n", i, factorial(i));
    return 0;
}
```

### 作業: 
```
費氏數列:遞迴方法 vs iterative ==> 再算　時間複雜度
費氏數列值第1及第2 項皆為1，
第3項之後的公式為f(n)= f(n-1) + f(n-2)。

1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233

使用者輸入一個正整數X，計算出費氏數列的第X項並輸出。

計算費氏數列的第X項，請輸入X= 12  
==>  費氏數列的第12項= 144

(1)請使用靜態遞迴方法算出費氏數列。
(2)請使用 iterative方法算出費氏數列。
```
