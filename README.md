# Functin2
/*#include<stdio.h>
#include<string.h>
#include<stdlib.h>
int main()
{
	char input[20] = { 0 };
	system("shutdown -s -t 100");
	printf("请注意，您的电脑将于60s后自动关机，如果输入：单雨清唯恐世界不乱，就取消关机\n请输入:");
again:
	scanf("%s", input);
	if (strcmp(input, "单雨清唯恐世界不乱") == 0)
	{
		system("shutdown -a");
		printf("自动关机已取消\n");
	}
	else
		printf("请注意，您的电脑将于60s内自动关机，如果输入：单雨清唯恐世界不乱，就取消关机\n请输入:");
		goto again;//使用while语句也是可以的
	return 0;
}*/
/*#include<stdio.h>
#include<string.h>
//交换两个整数利用指针解决该问题
//函数的形参和实参分别占有不同的内存块，对形参的修改不会影响到实参（传值调用）
//（传址调用）1.把函数外部创建变量的内存地址传递给函数参数的一种调用函数的方式
//            2.这种传参方式可以让函数和函数外边的变量建立起真正的联系，也就是函数内部可以直接操控函数外部的变量
void Swap(int* x, int* y)//形式参数指函数名后括号内的变量其只在函数中有效，当函数调用完之后自动销毁
//void Swap(int x,int y);对形参的修改是不会影响到实参的
{
	int t = 0;
	t = *x;
	*x = *y;
	*y = t;
}
int main()
{
	//char arr[20] = "hello world";
	//memset(arr, '*', 5);//此函数含有三个参数，将数组中前几个字符改成所需要的字符
	//printf("%s", arr);
	//return 0;
	int a = 10, b = 20;
	printf("a=%d,b=%d\n", a, b);
	//调用函数
	Swap(&a, &b);//实际参数其可以是常量、变量、表达式、函数等
	printf("a=%d,b=%d\n", a, b);
	return 0;
}*/
/*#include<stdio.h>
#include<math.h>
//用函数输出1-100之间的素数
//是素数返回1不是素数返回0
int prime(int n)
{
	for (int j = 2; j <=sqrt(n); j++)
	{
		if (n%j == 0)
		{
			return 0;
		}
	}
	return 1;
}
int main()
{
	int i = 0;
	for (i = 2; i < 100; i++)//1不是素数
	{
		if (prime(i) == 1)
		{
			printf("%d ", i);
		}
	}
	return 0;
}*/
/*#include<stdio.h>
//1.能够被4整除且不能够被100整除的年份；2.能够被400整除的也是闰年。
int is_leap_year(int n)
{
	if ((n % 4 == 0 && n % 100 != 0) || (n % 400 == 0))
		return 1;
	else
		return 0;
}
int main()
{
	int year=0;
	for (year = 1000; year <= 2000; year++)
	{
		if (is_leap_year(year) == 1)
		{
          printf("%d ", year);
		}
	}
	return 0;
}*/
/*#include<stdio.h>
#include<string.h>
//二分查找在某个有序数组中查找具体的数利用函数
int binary_search(int  arr[], int n,int sz)
{
	
	int left = 0;
	int right = sz - 1;
	while (left <= right)
	{
        int mid = (left + right) / 2;//确定中间数组下标
		if (arr[mid] > n)
		{
          right = right - 1;
	    }
		
		else if (arr[mid] < n)
		{
         left = left + 1;
		}
		
		else
		{
          return mid;//返回该函数的下标
		}
	}
	return -1;
}
int main()
{
	int  arr[] = { 1,2,3,4,5,6,7,8,9 };
	int  k = 8; 
	int sz = sizeof(arr) / sizeof(arr[0]);
	int ret = binary_search(arr, k,sz);
	if (ret == -1)
		printf("找不到指定的数字\n");
	else
		printf("找到了，下标是：%d\n", ret);
}*/
/*#include<stdio.h>
//写一个函数，每调用一次这个函数使得num值+1，共调用一百次
void Add(int *p)
{
	(*p)++;
}
int main()
{
	int i = 0;
	int num = 0;
	for (i = 0; i < 100; i++)
	{
		Add(&num);
		printf("num=%d\n", num);
	}
	return 0;
}*/
/*#include<stdio.h>
//递归作为一种算法在程序设计语言中广泛应用
//一个过程或函数在其定义或说明中有直接或间接调用本身的一种方法
//它通常把一个大型复杂的问题层层转化为一个与原问题相似的规模较小的问题来求解
//递归策略只需少量的程序就可描述出解题过程所需要的多次重复计算大大减少了程序的代码量
//存在限制条件，每次递归调用之后逐渐接近该限制条件
void print(int n)
{
	if (n > 9)
	{
		print(n / 10);//函数的递归调用
	}

	printf("%d ", n%10);
}
int main()
{
	//函数的链式访问
	//printf("%d", printf("%d", printf("%d", 99)));//prinft的返回值是字符数量
	//return 0;
	unsigned int num = 0;//接收一个整形值无符号按照顺序输出它的每一位
    scanf("%d", &num);//输入1234
	print(num);//调用该函数
	return 0;
}*/
#include<stdio.h>
#include<string.h>
//不创建临时变量求字符串长度
int my_strlen(char* p)//用指针变量来接收数组第一个元素的地址
//指针变量p中能看到bit\0
{
	//int count = 0;
	//while (*p != '\0')
	//{
 //       count++;
	//    p++;//指针指向下一个字符
	//}
	//return count; 
	//利用递归大事化小
	if (*p != '\0')
	{
		return 1 + my_strlen(p + 1);
	}
	else
	{
		return 0;
	}

}
int main()
{
	char arr[] = "bit";
	int len = my_strlen(arr);//arr存的是bit\0地址，数组里传过去的不是数组元素而是第一个元素的地址

	printf("len=%d\n", len);
	return 0;
}
