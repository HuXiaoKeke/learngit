<center><font color=blue size=7>task_02</font></center>  

***
***

<font color=yellow size=5>**题目一：**</font>  
>代码：
```c
#include<stdio.h>
#define M 1000
int main()
{
	int a[M], b[M];
	int i, j, k, num1, num2;
	char c;
	printf("\n请输入数组1：\n");
	for (i = 0, num1 = 0; true; i++)
	{
		scanf_s("%d", &a[i]);
		c = getchar();
		num1++;
		if (c == '\n')break;
	}
	printf("\n请输入数组2：\n");
	for (i = 0, num2 = 0; true; i++)
	{
		scanf_s("%d", &b[i]);
		c = getchar();
		num2++;
		if (c == '\n')break;
	}
	for (i = 0; i <= num2 - 1; i++)
	{
		for (j = 0; j <= num1 - 1; j++)
		{
			if (b[i] < a[j])
			{
				num1++;
				for (k = num1 - 1; k >= j+1; k--)
				{
					a[k] = a[k - 1];
				}
				a[j] = b[i];
				break;
			}
			if (b[i] == a[j])break;
		}
		if (j > num1 - 1)
		{
			a[j] = b[i];
			num1++;
		}
	}
	printf("\n合并之后的数组为：\n");
	for (i = 0; i <= num1 - 1; i++)
		printf("%d ", a[i]);
	printf("\n\n");
	return 0;
}
```

***

<font color=yellow size=5>**题目二：**</font>  
>代码：
```c
#include <stdio.h>
using namespace std;
#define m 10
struct node
{
	int i;
	struct node* next;
};
node* ChangeToList(int n, int arr[])
{
	struct node* head = new node;
	struct node* former = head;
	for (int i = 0; i < n; i++)
	{
		struct node* p = new node;
		p->i = arr[i];
		former->next = p;
		former = p;
	}
	return head;
}
void dowork(int n, node* p)
{
	for (int i = 0; i < n; i++)
	{
		printf("%d ", i);
		p = p->next;
	}
	printf("\n");
}
int main()
{
	int a[m] = { 1,2,3,4,5,6,7,8,9,10 };
	dowork(m, ChangeToList(m, a)->next);
	return 0;
}
```

***

<font color=yellow size=5>**题目三：**</font>  
>代码：
```c
#include <stdio.h>
using namespace std;
struct node
{
	int i;
	struct node* next;
};
struct node* creatlist(int n)
{
	struct node* head = new struct node;
	struct node* former = head;
	for (int i = 0; i < n; i++)
	{
		struct node* p = new struct node;
		printf("请输入列表中第%d个数据\n", i + 1);
		printf("%d", i);	 
		p->i;
		former->next = p;
		former = p;
		p->next = NULL;
	}
	printf("录入完毕\n");
	return head;
}
struct node* combine(struct node* head1, struct node* head2, int n, int m)
{
	struct node* head = new struct node;
	struct node* pre = head;
	struct node* temp1 = head1->next;
	struct node* temp2 = head2->next;
	for (int i = 0; i < n; i++)
	{
		struct node* p = new struct node;
		p->i = temp1->i;
		temp1 = temp1->next;
		pre->next = p;
		pre = p;
		p->next = NULL;
	}

	for (int i = 0; i < m; i++)
	{

		struct node* p = new struct node;
		p->i = temp2->i;
		temp2 = temp2->next;
		pre->next = p;
		pre = p;
		p->next = NULL;

	}
	return head;
}
struct node* sort(struct node* head, int a)
{
	struct node* pre = head->next;
	for (int i = a; i > 1; i--)
	{
		for (int j = 0; j < a - 1; j++)
		{
			if (pre->i > pre->next->i)
			{
				int temp = pre->next->i;
				pre->next->i = pre->i;
				pre->i = temp;
			}
			pre = pre->next;
		}
		pre = head->next;
	}
	return head;
}
void print(struct node* head, int a)
{
	struct node* temp = head->next;
	for (int i = 0; i < a; i++)
	{
		temp->i;
		printf("%d ", i);
		temp = temp->next;
	}
	printf("\n");
}
int main() {

	struct node* list1 = creatlist(3);
	struct node* list2 = creatlist(4);
	struct node* head = combine(list1, list2, 3, 4);
	print(sort(head, 7), 7);
	return 0;
}
```