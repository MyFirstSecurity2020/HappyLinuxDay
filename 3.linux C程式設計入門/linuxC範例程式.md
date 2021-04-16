# 範例學習C 程式設計
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
