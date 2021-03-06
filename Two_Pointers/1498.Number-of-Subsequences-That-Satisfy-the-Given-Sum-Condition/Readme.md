### 1498.Number-of-Subsequences-That-Satisfy-the-Given-Sum-Condition

因为这题考察的是subsequence，我们选取的元素其实和顺序无关，所以我们可以将nums排个序。好处是任何subsquece的最小值都在前面，最大值在后面。

我们遍历每个元素nums[i]，假想它是subsequence的最小值，那么我们可以容易确定可选的最大值nums[j]：只要从j=n-1往左移，找到第一个满足```nums[i]+nums[j]<=target```的元素j。确定了最大值和最小值，此时区间[i+1:j]内部的所有元素都可选可不选。所以我们的结论是：如果最小值是nums[i]，那么合法的子序列数目是```2^(j-i)```.

我们考察下一个i的时候，j必然只能在之前的位置继续往左移。所以这是一个双指针模式，用o(N)时间就可以搜寻所有的{i,j}配对。对于每对{i,j}我们都将子序列的数目累加起来。

此外，我们还预处理得到一个数组power[k]来存储所有```2^k % M```的值供使用。
