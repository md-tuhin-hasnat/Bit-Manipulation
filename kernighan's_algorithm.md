# Counting Set Bit Using Kernighan's Algorithm

### Uses :
Counting the set bits of a number. So far, this is the most efficient method of counting the set bit.
### Now what is set bit?
As we all know, binary numbers have only two digits. These are the numbers 0 and 1. We can generate any number in binary using these two digits. In other words, every number in the binary system is made up of 0's and 1's. 0 is also known as unset bit.  **And set bit is another name for digit 1**.

<p align="center">
  <img src="https://github.com/md-tuhin-hasnat/Bit-Manipulation/blob/main/img/Untitled%20design.png?raw=true" />
</p>

### Now there are two approch of counting
  1. [Traditional Approch](#### 1.Traditional Approch)
  2. [Kernighan's Algorithm Approch](#### 2.Kernighan's Algorithm Approch)

#### 1.Traditional Approch
To understand this approch, we have to know how to convert decimal number to binary. We can convert a decimal number to binary by simply check if the number modulo 2 is 1 or 0. This is the most significent digit. Then the number will be half of the original. This proccess will repeat while number is not equal 0.

#### C++ Code Example
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
#### 2.Kernighan's Algorithm Approch
