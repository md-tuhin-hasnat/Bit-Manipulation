# Counting Set Bit Using Kernighan's Algorithm

### Uses :
Counting the set bits of a number. So far, this is the most efficient method of counting the set bit.
### Now what is set bit?
As we all know, binary numbers have only two digits. These are the numbers 0 and 1. We can generate any number in binary using these two digits. In other words, every number in the binary system is made up of 0's and 1's. 0 is also known as unset bit.  **And set bit is another name for digit 1**.

<p align="center">
  <img src="https://github.com/md-tuhin-hasnat/Bit-Manipulation/blob/main/img/Untitled%20design.png?raw=true" />
</p>

### Now there are two approch of counting
  1. [Traditional Approch](https://github.com/md-tuhin-hasnat/Bit-Manipulation/edit/main/kernighan's_algorithm.md#1traditional-approch)
  2. [Kernighan's Algorithm Approch](https://github.com/md-tuhin-hasnat/Bit-Manipulation/edit/main/kernighan's_algorithm.md#2kernighans-algorithm-approch)

#### 1.Traditional Approch
To understand this approach, we must first understand how to convert decimal numbers to binary numbers. We can convert a decimal number to binary by simply determining whether the modulo 2 value is 1 or 0. This is the least significant digit. The number must then be divided by two. This procedure will be repeated as long as the number is not equal to zero. We can simply count how many 1s are in this binary number after converting it. In the example below, the answer is 3.

<p align="center">
  <img src="https://github.com/md-tuhin-hasnat/Bit-Manipulation/blob/main/img/Untitled%20design%20(1).png?raw=true" />
</p>

#### C++ Code Example (Traditional)
```C++
#include <bits/stdc++.h>
using namespace std;
int main(){
	int n,count = 0;
	cin>>n;
	while(n > 0){
		if (n%2==1)
		{
			count++;
		}
		n /= 2;
	}
	cout<<count<<"\n";
	return 0;
}
```
##### Input:
		22
##### Output:
		3
		
#### Why not Traditional way?
In this approach, we must check each and every digit of a binary number in order to count the set bit. In 32 bit ***"int"*** veriable ***0*** is written by ***00000000000000000000000000000000***. If we want to count the set bit, we must check 32 individual digits to see if they are ***1*** or not. Is there, however, a smart algorithm that can reduce the complexity? Here comes the femous Kernighan's algorithm.
#### 2.Kernighan's Algorithm Approch
In this approach, we must first understand what bit masking is. A mask specifies which bits should be kept and which should be cleared. The act of applying a mask to a value is known as masking. We need to mask the rightmost set bit in this application. The question now is, why? and how so?

We can directly terget the right most set bit by RMSBM or(Right most set bit Masking). Now, if we can replace this bit with an unset bit or 0, we can get the second rightmost set bit. This procedure will be repeated until the leftmost set bit is set to 0.
#### We can replace RMSB with 0 by subtracting RMSBM.
<p align="center">
  <img src="https://github.com/md-tuhin-hasnat/Bit-Manipulation/blob/main/1%200%200%201%201%200.png?raw=true" />
</p>

#### How to can mask Right most set bit?
We can find the mask by using binary and (&) operations on a number with the 2s complement of itself. Now what is 2's compliment? It is simply the binary representation of a negative number. For example, 2's compliment of **"n"** is the binary form of **"-n"**. Now **n `&` -n** is the right most set bit mask.

After that, We can replace the Right most Set Bit to **0** by subtracting **n `&` -n** from **n** . Ex: **n = n `-` (n `&` -n)**.

In **C++** it is **`n -= n&(-n)`**

This operation will repeat untill all digit is **0**. And the the number of repeatation is equal to the number of set bit in that numebr.
#### C++ Code Example (Kernighan's Algorithm)
```C++
#include <bits/stdc++.h>
using namespace std;
int main(){
	long long int n,count = 0;
	cin>>n;
	while(n > 0){
		count++;
		n -= (n&(-n));
	}
	cout<<count;
	return 0;
}

```
##### Input:
		22
##### Output:
		3
		
#### Beginer Level Problem related to this algorithm
1. [Raising Bacteria](https://codeforces.com/problemset/problem/579/A) <- Codeforces
2. [Kernighan's Algorithm Test](https://www.pepcoding.com/resources/data-structures-and-algorithms-in-java-levelup/bit-manipulation/kernighans-algo-official/ojquestion) <- Pepcoding
