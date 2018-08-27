##Bit manipulation:
具体推倒见[Bit manipulation](https://www.hackerearth.com/practice/basic-programming/bit-manipulation/basics-of-bit-manipulation/tutorial/) 
###Bitwise operators:
  - **NOT(~)**  
Bitwise NOT is an unary operator that flips the bits of the number i.e., if the ith bit is 0, it will change it to 1 and vice versa.
0变1,1变0

  - **AND(&)**
Bitwise AND is a binary operator that operates on two equal-length bit patterns. If both bits in the compared position of the bit patterns are 1, the bit in the resulting bit pattern is 1, otherwise 0.
都是1结果为1，否则为0

  - **OR（|）**
 Bitwise OR is also a binary operator that operates on two equal-length bit patterns, similar to bitwise AND. If both bits in the compared position of the bit patterns are 0, the bit in the resulting bit pattern is 0, otherwise 1.
都是0为0，否则为1

  - **XOR（^）**
Bitwise XOR also takes two equal-length bit patterns. If both bits in the compared position of the bit patterns are 0 or 1, the bit in the resulting bit pattern is 0, otherwise 1.
都是0或1才是0，否则是1

  - **Left shift(<<)**
Left shift operator is a binary operator which shift the some number of bits, in the given bit pattern, to the left and append 0 at the end. Left shift is equivalent to multiplying the bit pattern with  ( if we are shifting k bits ).
1 << 1 = 2 = 2<sup>1</sup>
1 << 2 = 4 = 2<sup>2</sup>
1 << 3 = 8 = 2<sup>3</sup>
1 << 4 = 16 = 2<sup>4</sup>
…
1 << n = 2<sup>n</sup>
相当于在1的后面加n个0；

  - **Right shift(>>)**
  Right shift operator is a binary operator which shift the some number of bits, in the given bit pattern, to the right and append 1 at the end. Right shift is equivalent to dividing the bit pattern with 2<sup>k</sup> ( if we are shifting k bits ).
  4 >> 1 = 2
  6 >> 1 = 3
  5 >> 1 = 2
  16 >> 4 = 1

  - **Local Shift vs Arithmetic Shift**
  Arithmetic shift keep the sign bit.
  Local shift (>>>), Arithmetic shift (>>).
![Local shift vs Arithmetic shift](/img/Local_shift_vs_Arithmetic_shift.JPG)

***

###Example of bit manipulation
1. 判断N是不是power of 2.
如果N是power of 2的话，binary representation of N应该是只有1个1,1的右边都为0.而N-1应该是除了最左边的1变为0，右边都为1（进位前）
N = 4 = (100)<sub>2</sub>
N - 1 = 3 = (011)<sub>2</sub>
N & (N-1) = (100)<sub>2</sub> & (011)<sub>2</sub> = (000)<sub>2</sub>
**N & (N-1)** 结果为0则是power of 2，如果不是0则不是power of 2.
```
return x && (x & (x - 1)); // 0 也不是power of 2.
```

***

2. count the number of ones in the binary representation of the given number
继承1中，N和N-1可以判断rightmost 1,循环几次说明有几个1.
```
while(n) { //当 n = 0 时停止
  n = n & (n - 1);
  count++;
}
return count;
```
Time Complexity: O(K), K is the number of one in the binary form of the given number.

***

3. check if ith (starting from 0) bit is set or not (1 or not) in the binary form of the given number.
`&`当都为1时才等于1，构建一个2<sup>i</sup>的数，这个数只有在ith为1，其余都为0，用这个数与N AND，如果结果为非零数，这ith是1，否者ith为0. 2<sup>i</sup>的另一个写法是1 << i.
```
if(N & (1 << i)) return true; //当为非零
else return false;
```

***

4. How to generate all the possible subsets of a subsets
对于一个有N个数的set，它有2<sup>N</sup>个subset，因为每个element都有存在、不存在于subset中的情况（1 或 0）。
A = {a,b,c},就有000，001,010,011...2<sup>3</sup> = 8种情况
```
for (int i = 0; i < (1 << N); i++) { //有2^N个组合，找出2^N的binary form。
  for (int j = 0; j < N; j++) { //scan binary form中的每一位
    if (i & (1 << j)) { //如果jth位为1，则表示jth element存在这个subset中，print out。
      print A[j];
    }
  }
  print '\n';
}
```

***

5. Find the largest power of 2 (most significant bit in binary form), which is less than or equal to the given number N.
找到一个数中最左边的1. 比如(10101)<sub>2</sub> = 21 中最左边的1.
如果将所有位数都变为1，则为：
(11111)<sub>2</sub>
= 31
= 2<sup>5</sup> - 1
= 2<sup>4</sup> + 2<sup>4</sup> - 1
= 2 x  2<sup>4</sup> - 1
这里2<sup>4</sup>的power 4也就是答案。
设将所有bit都变为1后的值是T，则
T = 2 * x - 1,
x为答案most significant bit.
使用以下可以将16 bit的integer全部set为1，这个方法也可继续延伸为32bit或64 bit integer。
N = N | (N >> 1);
N = N | (N >> 2);
N = N | (N >> 4);
N = N | (N >> 8);
具体推倒见[Bit manipulation](https://www.hackerearth.com/practice/basic-programming/bit-manipulation/basics-of-bit-manipulation/tutorial/)
code为：
```
//1. 将所有bit变为1
N = N | (N >> 1);
N = N | (N >> 2);
N = N | (N >> 4);
N = N | (N >> 8);
//2.根据T = 2<sup>i</sup> * 2 - 1 求出2<sup>i</sup>
return (N + 1) / 2;  //或者(N + 1) >> 1
```

***

###Tricks:
1. x ^ (x & (x - 1)) 得到最右边的1.
例：(1010)<sub>2</sub> 经过这个运算后得到结果(0010)<sub>2</sub>.
2. x & (-x) 也同样得到最右边的1.
-x的算法：
补码：原码-->反码--> + 1
例：5的原码000101，反码为111010，补码为111011.
则111011即为-5的表达方式。
3. x | (1 << n) 返回将x中第n位bit变为1.
例：x = 10 = (1010)<sub>2</sub>, n = 2,最后的结果为(1110)<sub>2</sub>.
