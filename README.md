#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>

#include<assert.h>


strcpy是把src指向的内容拷贝放进dest指向的空间中
本质上讲，希望dest指向的内容被修改，src指向的内容不被修改

char* my_strcpy(char* dest, const char* src)

{

	assert(dest != NULL && src != NULL);//断言
	char* ret = dest;
	while (*dest++ = *src++)
	{
		;
	}
	return ret;//返回目标空间的起始地址
  
}
int main()

{

	char arr1[20] = "xxxxxxxxxx";
	char arr2[] = "hello";
    //1.目标空间的起始地址 2.源空间的起始地址
	printf("%s\n", my_strcpy(arr1, arr2));//返回值做了printf的参数，这就是链式访问
  
	return 0;
  
}

extern - 声明外部符号
size_t - unsigned int 
size_t my_strlen(const char* str)

{

	assert(str != NULL);//assert(str)
	size_t count = 0;
	while (*str++ != '\0')
	{
		count++;
	}
	return count;
  
}
int main()

{

	char arr[20] = "hello bit";
	printf("%d ", my_strlen(arr));
	return 0;
}

15 - 00001111
15%2=1
15/2=7%2=1;00000111 ....
int NumberOf1(int n)

{

	int count = 0;
	while (n)
	{
		if (n % 2 == 1)
		{
			count++;
		}
		n /= 2;
	}
	return count;
}
int NumberOf1(int n)

{

	int count = 0;
	int i = 0;
	for (i = 0; i < 32; i++)
	{
		if (((n >> 1) & 1) == 1)
		{
			count++;
		}
	}
	return count;
}
int NumberOf1(int n)

{

	int count = 0;
	int i = 0;
	while (n)
	{
		n = n & (n - 1);
		count++;
	}
	return count;
}
int main()

{

	int n = 0;
	scanf("%d", &n);
	int ret = NumberOf1(n);
	printf("%d ", ret);
  
	return 0;
  
}


写一个代码判断一个数字是不是二的n次方
2的n次方的数字，二进制中只有一个1
k&(k-1)==0

int main()

{

	int m = 0;
	int n = 0;
	scanf("%d %d", &m, &n);
	int a = m ^ n;
    int count = 0;
	while (a)
	{
		a = a & (a - 1);
		count++;
	}
	printf("%d\n", count);
	return 0;
  
}

int main()

{

	int m = 0;
	int n = 0;
	scanf("%d %d", &m, &n);
	int i = 0;
	int count = 0;
	for (i = 0; i < 32; i++)
	{
		if (((m >> i) & 1) != ((n >> i) & 1))
		{
			count++;
		}
	}
	printf("%d\n", count);
	return 0;
}

int main()

{

	int i = 0;
	int n = 0;
	scanf("%d", &n);
	//打印偶数位
	for (i = 31; i >= 1; i -= 2)
	{
		printf("%d ", (n >> i) & 1);
	}
	printf("\n");
	//打印奇数位
	for (i = 30; i >= 0; i -= 2)
	{
		printf("%d ", (n >> i) & 1);
	}
	return 0;
  
}

int main()

{

	int a = 3;
	int b = 5;
	printf("a=%d b=%d\n", a, b);
	a = a + b;
	b = a - b;
	a = a - b;
	printf("a=%d b=%d\n", a, b);
	return 0;
  
}

int main()

{

	int a = 30;
	int b = 50;
	printf("a=%d b=%d\n", a, b);
	a = a ^ b;
	b = a ^ b;//a ^ b ^ b
	a = a ^ b;//a ^ a ^ b
	printf("a=%d b=%d\n",  a, b);
	return 0;
  
}


//最小公倍数
int main()

{

	int a = 0;
	int b = 0;
	scanf("%d %d", &a, &b);
	int i = 1;
	for (i = 1; ; i++)
	{
		if (a * i % b == 0)
		{
			printf("%d\n", a * i);
			break;
		}
    
	}

	//int m = a > b ? a : b;
	//while (1)
	//{
	//	if (m % a == 0 && m % b == 0)
	//	{
	//		printf("%d\n", m);
	//		break;
	//	}
	//	m++;
	//}
	return 0;
}

//辗转相除法求最小公约，最大公倍
int main()

{

	int a = 0;
	int b = 0;
	int x = 0;
	int y = 0;
	scanf("%d %d", &a, &b);
	x = a;
	y = b;
	if (a < b)
	{
		int temp = b;
		b = a;
		a = temp;
	}
	int n = a % b;
	while (n != 0)
	{
		a = b;
		b = n;
		n = a % b;
	}
	printf("最小公倍数：%d,最大公约数：%d\n", x * y / b, b);
	return 0;
  
}

#include<stdio.h>

#include<string.h>

void reverse(char* left,char* right)

{

	while (left < right)
	{
		char tmp = 0;
		tmp = *left;
		*left = *right;
		*right = tmp;
		left++;
		right--;
	}
}
int main()

{

	I like beijing.
	char arr[100] = { 0 };
	gets_s(arr);
	int len = strlen(arr);
	//三步翻转法
	//1.字符串整体反转
	//.gnijieb ekil I
	reverse(arr,arr+len-1);
	//2.每个单词逆序
	char* start = arr;
	while (*start)
	{
		char* end = start;
		while (*end != ' ' && *end != '\0')
		{
			end++;
		}
		//逆序一个单词
		reverse(start, end - 1);
		if (*end == ' ')
			start = end + 1;
		else
			start = end;
	}
	printf("%s\n", arr);
  
	return 0;
  
}
