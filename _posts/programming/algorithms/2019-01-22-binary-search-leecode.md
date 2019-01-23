---
layout: article
title:  "「LeetCode」 二分查找"
date:   2019-01-22 8:37:40 +0800
key: binary-search-leetcode-20190122
aside:
  toc: true
category: [Algorithms, AlgSearch, LeetCode]
---

>要求：待搜索序列有序；  

[二分查找解读](/algorithms/algsearch/2019/01/21/binary-search.html)

## 一、 有序移位数组·查找
有序移位数组：数组源于一个升序整数数组(i.e., 0 1 2 4 5 6 7)，所有元素循环移动 n 位(i.e.,4 5 6 7 0 1 2)； n 未知；  

### 1. [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
ID 33：在一个不含重复元素的有序移位数组中搜索一个数，找到则返回下标，找不到返回 -1；要求时间复杂度为  O(log n)；       
>**Input**: nums = [4,5,6,7,0,1,2], target = 0  
**Output**: 4  

- 根据时间复杂度可知，需用二分查找，且：
  - 该数组可以分为两段，两段分别为升序；  
  - 后半部分小于前半部分，所以其实很容易判断出 mid 在哪一部分；  
- 原生的二分查找，左右两个哨兵移动的条件自始至终不变；本题的难点就在于，左右两个哨兵移动的条件需根据 target 处在左半段还是右半段而有所不同；     

[C 示例](#rotated_sorted_arr_c)（[详细工程](https://github.com/smartadpole/OnlineJudge/blob/master/LeetCode/id33_Search_in_Rotated_Sorted_Array.cpp)），    

### 2. [Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)  
ID 81：在一个含重复元素的有序移位数组中搜索一个数，找到则返回 true，找不到返回 false；  
>**Input**: nums = [2,5,6,0,0,1,2], target = 0  
**Output**: true

上一题的基础上，加入了重复元素，因此打破了两侧数组单调递增的特性；  
1. 若重复元素出现在两个子序列内部也没什么，「Search in Rotated Sorted Array」方案就可以解决；   
2. 就怕同时出现在左序列起、右序列止；因为此时判断 mid 落在左序列还是右序列出现困难；例如 [1,3,1,1,1]；  

解决：将情形 2 转化为 情形 1 即可——只处理单侧；当前值与边界值相等时，该边界处的哨兵向另一侧单步移动，直至当前子序列单增，此时重复元素只出现在单侧，即情形 1；  
以左序列为例；当 num[mid] == num[low]，low = low + 1 即可，其他照旧，最终左序列会是单增；  

[C 示例](#rotated_sorted_arr2_c)（[详细工程](https://github.com/smartadpole/OnlineJudge/blob/master/LeetCode/id81_Search_in_Rotated_Sorted_Array_II.cpp)），    

### 3. [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
ID 153：返回数组（不含重复元素的有序移位数组）中的最小元素；       
>**Input**: [3,4,5,1,2]   
**Output**: 1    

准确地说是找到该移动数组左右两段的交界点；  

[C 示例](#rotated_sorted_arr_find_min_c)（[详细工程](https://github.com/smartadpole/OnlineJudge/blob/master/LeetCode/id153_Find_Minimum_in_Rotated_Sorted_Array.cpp)），    

### 4. [Find Minimum in Rotated Sorted Array II](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/)
ID 154：返回数组（含重复元素的有序移位数组）中的最小元素；       
>**Input**: [3,4,4,1,2]   
**Output**: 1    

与「Search in Rotated Sorted Array II」思路一样，把左侧子序列处理成单调递增即可——num[mid] == num[low] 时左哨兵右移一位；  

[C 示例](#rotated_sorted_arr_find_min2_c)（[详细工程](https://github.com/smartadpole/OnlineJudge/blob/master/LeetCode/id154_Find_Minimum_in_Rotated_Sorted_Array_II.cpp)），    


## 二、 猜数问题
（374题）  
这种题目一般是说找到里面特定的数字，这个数字是确定存在的，所以肯定会有一个一定匹配的问题,所以一般我们在判断条件中把 if(r[mid] == target) 单独提出来；  

>We are playing the Guess Game. The game is as follows: I pick a number from 1 to n. You have to guess which number I picked. Every time you guess wrong, I'll tell you whether the number is higher or lower. You call a pre-defined API guess(int num) which returns 3 possible results (-1, 1, or 0): -1 : My number is lower 1 : My number is higher 0 : Congrats! You got it!  
Example: n = 10, I pick 6. Return 6.  

1. **分析**  
- 一是你要理解my的含义，它的my是指的出题人，而我们是解题人，所以如果返回-1，说明它的数小，我们猜的数大，这里一定要理解！  
- 这是一个经典的二分题目，很容易套用二分查找的公式写出来  
- 因为int mid = (st + ed) / 2;可能会由于（st+ed）产生溢出；
所以，为了解决这个问题，推荐把mid的写法写成下面的格式：`int mid = st + (ed - st) / 2;`  

[C++ 示例](#guess_num_cpp)  

## 四、 找位置
（35题）  
这类题目一般是说找到一个数它应该在数组中的位置，就是完整的套用框架；  
>


1. **分析**  

## 五、 找边界
（34题）  
这类题目有点麻烦，它需要用两次分别找左右边界。这里就需要考虑里面可能有和目标数相同的数。这时候就要特别注意是使用 <= 还是 <，而在找右边界的时候，需要移动 ed,这时候 mid 在原来的基础要+1（看注意3）  

Given a sorted array of integers, find the starting and ending position of a given target value. Your algorithm's runtime complexity must be in the order of O(log n). If the target is not found in the array, return [-1, -1].  
>For example, Given [5, 7, 7, 8, 8, 10] and target value 8, return [3, 4].  


1. **分析**  
题目里给了提示要求时间上必须是O(logN)，那么暗示了这要用二分去做。 范围搜索也就是要确定一个上确界，一个下确界；  
分别都可以用二分去找；  
- 左边界  
二分的话主要有以下几种情况，我们定义成3个基本规则：
Rule 1. A[mid] < target ，这时候说明还可以向右，st = mid+1 Rule 2. A[mid] > target ， 这时候说明应该在左边，ed = mid-1 Rule 3. A[mid] == target ，这时候既可以左移，也可以不移动，ed = mid
因为作为二分，最后肯定是在2个数中选一个然后停止循环（while(st < ed)）。 考虑下面几种情况，假设 target=5：（在两个数的情况下mid = st）
case 1: [3 5] (A[st] = target > A[ed])
case 2: [5 7] (A[st] = target < A[ed])
case 3: [5 5] (A[st] = target = A[ed])
case 4: [3 7] (A[st] < target < A[ed])
case 5: [3 4] (A[st] < A[ed] < target)
case 6: [6 7] (target < A[st] < A[ed])
情况3就是Rule1的情况，st = mid + 1就行。 对于情况2-3这时候，我们只要 ed = mid就行了，其实也就是把Rule 2 和Rule 3合并成了
Rule 2*. A[mid] >= target， ed = mid
所以case 1-3 最后停止条件都是A[st] = A[ed] = target
对于case 4-6 都是A[st] != target，可以直接退出
- 右边界  
找到了左边的边界后就好办了，右边的边界只用同理操作就行了。 而且因为找到了左边的边界，实际上就不存在比target小的数了。
这里，我们让mid偏向右边
mid = (st + ed)/2 + 1;
然后主要控制ed移动就可以了。

[C++ 示例](#search_range_cpp)  

## 典型应用
### 1. 求最优解问题
>求满足某个条件C(x)的最小的x  

对于任意满足C(x)的x如果所有x'>=x也满足C(x')的话，就可以用二分查找来求得最小的x；  
首先我们将区间的左端点初始化为不满足C(x)的值，右端点初始化为满足C(x)的值。然后每次取中点mid=(lb+ub)/2,判断C(mid)是否满足并缩小范围，直到(lb,ub]足够小为止。最后ub就是要求的最小值；  
同理，最大化的问题也可以用同样的方法求解；  

1） **假定一个解并判断是否可行**  
有N条绳子，他们长度分别为Li。如果从它们中切割出K条长度相同的绳子的话，这K条绳子每条最长能有多长？答案保留到小数点后2位；限制条件：
  - 1<= N <= 10000  
  - 1<= K <= 10000  
  - 1<= Li <= 100000

2） **分析**
令条件为 C(x)= 可以得到 K 条长度为x的绳子，则问题变为求满足 C(x) 条件的最大的 x；在区间初始化时，令下界为lb=0，上界为ub=INF；  
转化：  
由于长度为Li 的绳子最多可以切出floor(Li/x)段长度为x的绳子，因此 C(x)=(floor(Li/x)的总和是否大于或者等于K)  

3） **二分查找的结束判定**  
在输出小数的问题中，一般都会制定允许的误差范围或者制定输出中小数点后面的位数。有必要设置合理的结束条件来满足精度的要求；  
在上面的程序中，我们制定循环次数作为终止条件。1次循环可以吧区间范围缩小一半，100次循环则可以达到10的-30次幂的精度范围，基本是没有问题的；  

[C++ 示例](#optimum_solution_cpp)  

### 2. 最大化平均值
>有n个物品的重量和价值分别是wi和vi。从中选出k个物品使得单位重量的价值最大；  
限制条件：  
- 1<= k <= n <= 10^4
- 1<= wi,vi <= 10^6  

1） **分析**

[C++ 示例](#maximizing_average_cpp)  



-------------------  
 End
{:.warning}  



## 附录
### A 示例
<span id="rotated_sorted_arr_c">**1. Search in Rotated Sorted Array C 示例**</span>   

```c
int Search(const int* nums, const int numsSize, const int target)
{
    int low = 0, high = numsSize-1, mid = -1;
    while(low <= high)
    {
        mid = low + ((high - low) >> 1);
        if (nums[mid] < target)
        {
            if (nums[mid] < nums[low] && target > nums[numsSize-1]) // right sub array
            {
                high = mid -1;
            }
            else
            {
                low = mid + 1;
            }
        }
        else if (nums[mid] > target)
        {
            if (nums[mid] > nums[numsSize-1] && nums[numsSize-1] >= target) // left sub array
            {
                low = mid + 1;
            }
            else
            {
                high = mid -1;
            }
        }
        else
        {
            return mid;
        }
    }
    return -1;
}
```

<span id="rotated_sorted_arr_c">**2. Search in Rotated Sorted Array II C 示例**</span>   

```c
int Search(const int* nums, const int numsSize, const int target)
{
    int low = 0, high = numsSize-1, mid = -1;
    while(low <= high)
    {
        mid = low + ((high - low) >> 1);

        if (target == nums[mid])
        {
            return true;
        }
        else if (nums[mid] == nums[low])
        {
            ++low;
            continue;
        }
//        else if (nums[mid] == nums[high])  // work as <else if (nums[mid] == nums[low])>
//        {
//            --high;
//            continue;
//        }

        if (nums[mid] < target)
        {
            if (nums[mid] < nums[low]   // right sub array
                    && target > nums[high])
            {
                high = mid -1;
            }
            else
            {
                low = mid + 1;
            }
        }
        else if (nums[mid] > target)
        {
            if (nums[mid] > nums[high]   // left sub array
                    && nums[high] >= target)
            {
                low = mid + 1;
            }
            else
            {
                high = mid -1;
            }
        }
    }
    return false;
}
```

<span id="rotated_sorted_arr_find_min_c">**3. Find Minimum in Rotated Sorted Array C 示例**</span>   

```c
int FindMin(const int* nums, const int numsSize)
{
  if (1 == numsSize
          || nums[0] < nums[numsSize - 1])
  {
      return nums[0];
  }

  int low = 0, high = numsSize-1;

  while(low <= high)
  {
      int mid = low + ((high - low)>>1);

      if (nums[low] > nums[high])
      {
          if (nums[mid] < nums[low])  // right sub array
          {
              high = mid;
          }
          else    // left sub array
          {
              low = mid + 1;
          }
      }
      else    // ascending order
      {
          return nums[low];
      }
  }

  return nums[high];
}
```


<span id="rotated_sorted_arr_find_min2_c">**4. Find Minimum in Rotated Sorted Array II C 示例**</span>   

```c
int FindMin(const int* nums, const int numsSize)
{
  if (1 == numsSize
            || nums[0] < nums[numsSize - 1])
    {
        return nums[0];
    }

    int low = 0, high = numsSize-1;

    while(low <= high)
    {
        int mid = low + ((high - low)>>1);

        if (nums[low] == nums[high])
        {
            ++low;
        }
        else if (nums[low] > nums[high])
        {
            if (nums[mid] < nums[low])  // right sub array
            {
                high = mid;
            }
            else    // left sub array
            {
                low = mid + 1;
            }
        }
        else    // ascending order
        {
            return nums[low];
        }
    }

    return nums[high];
}
```


<span id="optimum_solution_cpp">**4. 求最优解 C++ 示例**</span>   

```c++
#include <iostream>
#include <math.h>
using namespace std;
#define MAX_N 10

int N = 4;
int K = 10;
double L[MAX_N] = {8.02,7.43,4.57,5.39};

bool C(double x)
{
    int num = 0;    
    for(int i=0;i<N;i++)
    {
        num += (int)(L[i]/x);
    }
    return num >= K;
}

void solve()
{
    double lb = 0;
    double ub = 1000;
    for(int i=0;i<100;i++)
    {
        double mid = (lb+ub)/2;
        if(C(mid)) lb = mid;
        else ub = mid;
    }
    cout << floor(ub*100)/100<<endl;
}

int main() {
    solve();
    return 0;
}
```

<span id="maximizing_average_cpp">**4. 最大化平均值 C++ 示例**</span>   

```c++
//input
int n,k;
int w[MAX_N],v[MAX_N];

double y[MAX_N];// v - x * w

bool C(double x)
{
    for(int i=0;i<n;i++){
        y[i] = v[i] - x*w[i];
    }
    sort(y,y+n);
    //compute the sum of top-k number(array y)
    double sum = 0;
    for(int i=0;i<k;i++){
        sum+=y[n-i-1];
    }
    return sum >= 0;
}
void solve()
{
    double lb=0,ub=INF;
    for(int i=0;i<100;i++){
        double mid = (lb+ub)/2;
        if(C(mid))
            lb = mid;
        else
            ub = mid;
    }
    printf("%.2f\n",ub);
}
```

<span id="guess_num_cpp">**5.  猜数问题 C++ 示例**</span>   

```c++
int guessNumber(int n)
{
  int st = 1, ed = n;
  while(st < ed)
  {
      int mid = (st + ed) / 2;
      if(guess(mid) == 0)
          return mid;
      else if(guess(mid) < 0)  // the number is too large
          ed = mid-1;
      else
          st = mid+1;
  }
  return st;
}
```

<span id="search_range_cpp">**6. 找边界 C++ 示例**</span>   

```c++
int[] searchRange(int[] nums, int target)
{
    int [] result = new int [2];
    result[0] = result[1] = -1;
    if(nums.length == 0)
        return result;

    int st = 0, ed = nums.length-1,mid;
    while(st < ed)
    {
        // 寻找左边界
        mid = (st + ed) / 2;
        if (nums[mid] < target)  //保证st不会越过任何等于target的数
        {
            st = mid+1;  //如果当前的数小于我们需要查的数，继续逼近
        } else {       //如果大于等于
            ed = mid;
        }
    }
    if(nums[st] != target)
        return result;
    result[0] = st;
    // 寻找右边界
    ed = nums.length-1;
    while(st < ed)
    {
        mid = (st + ed)/2 + 1; //这里用+1是为了让mid偏向右边
        if(nums[mid] > target)
        {
            ed = mid-1;
        }
        else  //因为st已经确定了，所以这里实际上不会出现比target小的数了，这里实际就是A[mid] == target
        {  
            st = mid;
        }
    }
    result[1] = ed;
    return result;
}
```
<span id="rotated_sorted_arr_cpp">**7.  C++ 示例**</span>   

```c++

```

<span id="rotated_sorted_arr_cpp">**1.  C++ 示例**</span>   

```c++

```