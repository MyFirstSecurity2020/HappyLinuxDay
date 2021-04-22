# 範例學習C 程式設計
```
本單元規劃以 範例  快速引導學生掌握基礎 C 程式語法
更多完整內容仍需參考學習資源或買書學習
```

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
#
```

```
## while loop ==> 計算n!
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
