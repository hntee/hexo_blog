title: test
date: 2014-03-06 11:16:03
tags: markdown

---
# An exhibit of Markdown

This note demonstrates some of what [Markdown][1] is capable of doing.

*Note: Feel free to play with this page. Unlike regular notes, this doesn't automatically save itself.*
<!-- more -->
## Basic formatting

网页配色的文章在网络上很多，甚至有些泛滥，稍微关注过的同学应该都知道“色轮”、“色卡”等辅助性配色工具，但那更多都是从印刷介质上的色彩系统延伸出来的，不完全适用于网页，甚至造成很大的局限，比如你会较真的通过色轮来选用网页色彩吗？再比如通过下面提供的配色组合，你能自由的应对一个又一个的类型相若的网页设计需求吗？

网页配色的文章在网络上很多，甚至有些泛滥，稍微关注过的同学应该都知道“色轮”、“色卡”等辅助性配色工具，但那更多都是从印刷介质上的色彩系统延伸出来的，不完全适用于网页，甚至造成很大的局限，比如你会较真的通过色轮来选用网页色彩吗？再比如通过下面提供的配色组合，你能自由的应对一个又一个的类型相若的网页设计需求吗？ This *can be **nested** like* so.

## Lists

### Ordered list

1. Item 1
2. A second item
3. Number 3
4. Ⅳ

<code> [lang:language] </code>

*Note: the fourth item uses the Unicode character for [Roman numeral four][2].*

### Unordered list

* An item
* Another item
* Yet another item
* And there's more...

## Paragraph modifiers

{%codeblock lang:c %}
#include <stdio.h>
#define max 9
#define true 1
#define false 0
#define datatype int


typedef struct
{
	datatype data[max];
	int front;
	int rear;
	int size;
}SeqQueue;

void initQueue(SeqQueue * Q)
{
	Q->front = 0;
	Q->rear = 0; 
	Q->size = 0;
}

int isEmpty(SeqQueue * Q)
{
	// if (Q->front == Q->rear)
	// 	return true;
	// else 
	// 	return false;
	return Q->size;
}

datatype deQueue(SeqQueue * Q)
{
	datatype x;
	if(isEmpty(Q))
	{
		printf("the queue is empty!\n");
		return false;
	}
	else
	{
		x = Q->data[Q->front];
		Q->front = (Q->front + 1) % max; 
		Q->size--;
		return x;
	}
}
void enQueue(SeqQueue * Q, datatype x)
{
 
	
		Q->data[Q->rear] = x;
		Q->rear = (Q->rear+1) % max;  
		Q->size++;
	
}


void tmp(int i[max][max])
{
	printf("%d\n", i[1][1]);
}

void printarray(int * result)
{
	int i;
	for(i = 0; i < max; i++)
		printf("%d\t", result[i]);
	printf("\n");		


}

void printQueue(SeqQueue * Q)
{
	printarray(Q->data);
}

void division(int R[max][max], int n, int * result, SeqQueue * Q)
{
	int e, j, k;
	int clash[max];


	int pre = n;
	int group = 0;
	// initQueue(Q);

	for(e = 0; e < n; e++)
		enQueue(Q, e);
	
	// printf("%d\n%d\n", Q->front+1,Q->rear);
	printf("dddd%d\n", Q->size);
	// while(!isEmpty(Q))
	int m = 2;
	while(m--)
	{
		printf("%s\n", "ok");
		datatype i = deQueue(Q);
		printQueue(Q);
		printf("Q->size:%d\n", Q->size);
		if(i < pre)
		{
			group++;
			for(j = 0; j < n; j++)
				clash[j] = 0;
		}
		if(clash[i] == 0)
		{
			result[i] = group;
			for(k = 0; k < n; k++)
				clash[k] += R[i][k];
		}
		else
			enQueue(Q, i);
		pre = i;
		printarray(result);

	}

}


int main()
{
	// int e = 1;int n = 8;
	SeqQueue * Q;
	initQueue(Q);


	// printf("%d\n", isEmpty(Q));
	// printf("%s\n", "ok");
	// enQueue(Q, 1);
	// enQueue(Q, 2);
	// printf("%d\n", deQueue(Q));
	// printf("%d\n", deQueue(Q));
	
	int i;
	int result[max];
	result[1] = 124;
	int R[max][max] = {
				        {0, 1, 0, 0, 0, 1, 0, 0, 0},
				    	{1, 0, 0, 0, 1, 1, 0, 1, 1},
				 		{0, 0, 0, 0, 0, 1, 1, 0, 0},
				 		{0, 0, 0, 0, 1, 0, 0, 0, 1},
				 		{0, 1, 0, 1, 0, 0, 1, 0, 1},
				 		{1, 1, 1, 0, 0, 0, 1, 0, 0},
				 		{0, 0, 1, 0, 1, 1, 0, 0, 0},
				 		{0, 1, 0, 0, 0, 0, 0, 0, 0},
				 		{0, 1, 0, 1, 1, 0, 0, 0, 0} 
					};




	division(R, max, result, Q);

	// for(i = 0; i < max; i++)
	// 	printf("the result is: %d\n", result[i]);			
	return 0;
}
	
{%endcodeblock%}
You can also make `inline code` to add code into other things.

### Quote

> Here is a quote. What this is should be self explanatory. Quotes are automatically indented when they are used.

## Headings

There are six levels of headings. They correspond with the six levels of HTML headings. You've probably noticed them already in the page. Each level down uses one more hash character.

### Headings *can* also contain **formatting**

### They can even contain `inline code`

Of course, demonstrating what headings look like messes up the structure of the page.

I don't recommend using more than three or four levels of headings here, because, when you're smallest heading isn't too small, and you're largest heading isn't too big, and you want each size up to look noticeably larger and more important, there there are only so many sizes that you can use.

## URLs

URLs can be made in a handful of ways:

* A named link to [MarkItDown][3]. The easiest way to do these is to select what you want to make a link and hit `Ctrl+L`.
* Another named link to [MarkItDown](http://www.markitdown.net/)
* Sometimes you just want a URL like <http://www.markitdown.net/>.

## Horizontal rule

A horizontal rule is a line that goes across the middle of the page.

---

It's sometimes handy for breaking things up.

## Images

Markdown can also contain images. I'll need to add something here sometime.

## Finally

There's actually a lot more to Markdown than this. See the official [introduction][4] and [syntax][5] for more information. However, be aware that this is not using the official implementation, and this might work subtly differently in some of the little things.


  [1]: http://daringfireball.net/projects/markdown/
  [2]: http://www.fileformat.info/info/unicode/char/2163/index.htm
  [3]: http://www.markitdown.net/
  [4]: http://daringfireball.net/projects/markdown/basics
  [5]: http://daringfireball.net/projects/markdown/syntax
