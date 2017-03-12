# Maximum-Subsequence-Sum
Given a sequence of KK integers { N_1N
​1
​​ , N_2N
​2
​​ , ..., N_KN
​K
​​  }. A continuous subsequence is defined to be { N_iN
​i
​​ , N_{i+1}N
​i+1
​​ , ..., N_jN
​j
​​  } where 1 \le i \le j \le K1≤i≤j≤K. The Maximum Subsequence is the continuous subsequence which has the largest sum of its elements. For example, given sequence { -2, 11, -4, 13, -5, -2 }, its maximum subsequence is { 11, -4, 13 } with the largest sum being 20.
Now you are supposed to find the largest sum, together with the first and the last numbers of the maximum subsequence.
Input Specification:

Each input file contains one test case. Each case occupies two lines. The first line contains a positive integer KK (\le 10000≤10000). The second line contains KK numbers, separated by a space.
Output Specification:

For each test case, output in one line the largest sum, together with the first and the last numbers of the maximum subsequence. The numbers must be separated by one space, but there must be no extra space at the end of a line. In case that the maximum subsequence is not unique, output the one with the smallest indices ii and jj (as shown by the sample case). If all the KK numbers are negative, then its maximum sum is defined to be 0, and you are supposed to output the first and the last numbers of the whole sequence.
Code As follows
using the algorithm of 在线选择
#include<stdio.h>
int main(){
	int k;
	scanf("%d",&k); 
	int a[k];
	for(int i=0;i<k;i++){
		scanf("%d",&a[i]);//按顺序读数列到数组a中 
	}
	int Max=0,This=0;//求和变量 
	int start=0,end=k-1;//开头结尾变量 
	int len=0,Mlen=0;//子列长度变量 
	int i=0;//循环变量 
	int count=0;//用来排除全是负数无法按要求输出的计数变量 
	for(i=0;i<k;i++){
		if(a[i]<0){
			count++;
		}
	}
	if(count==k){//数列全是负数的话直接输出a[0]和a[k-1] 
	}
	else{
		for(i=0;i<k;i++){
		This+=a[i];
		if(This>Max){ 
			Max=This;
			end=i;//把最大和的终点记下了 
			Mlen=len;//最大列长度记下来 （等于当前计数长度） 
		}
		len++;
		if(This<0){
			This=0;
			len=0;//抛弃子列时，计数长度也清零 
		}
	}
	start=end-Mlen;//修正起始点 
	}
	printf("%d ",Max);//输出和以及空格 
	printf("%d ",a[start]);//输出 起点处值和空格 
	printf("%d",a[end]);// 输出 终点处值没空格 
	return 0;
}

