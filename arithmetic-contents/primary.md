### 算法入门篇

+ 现在开始， 走上算法之路。

#### 1.  从排序数组中删除重复项

+ **题目**：给定一个排序数组，你需要在**原地**删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的                新长度。（不要使用额外的数组空间，你必须在**原地修改输入数组**并在使用 O(1) 额外空间的条件下完成。）
+ **要点**
  + 不要使用额外的数组空间， 即空间条件为O(1)
  + 数组已经排序好
+ **思路**：  因为不允许使用额外数组的空间，所以采用覆盖的方法。 

~~~javascript
// 采用双指针， 例如[1,1,2,2] fast指向往后走， 当遇到和slow指向的数组不相同的时候， slow指针＋1， 并且用fast指向的值覆盖。
let removeDuplicates = function(nums) {
    const length = nums.length
    if(length == 0) return 0
    let slow = 0
    for(let fast = 1; fast < length; fast++) {
        if(nums[slow] !== nums[fast]) {
            slow++
            nums[slow] = nums[fast]
        }
    }
    return slow + 1
};
~~~



### 2.买卖股票最佳时机Ⅱ

+ 给定一个数组，它的第 *i* 个元素是一支给定股票第 *i* 天的价格。设计一个算法来计算你所能获取的最大利润。你可以尽可能地完成更多的交易（多次买卖一支股票）。`注意：你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。`
+ 思路： 根据贪心算法思想， 局部最优整合 即成为整体最优解， 后一天的价格比前一天高， 即可买入卖出。

~~~ javascript
function maxProfit(prices) {
	var maxprofit = 0
	for(let i = 1; i < prices.length; ++i){
		if (prices[i] > prices[i - 1]) {
			maxprofit += prices[i] - prices[i - 1]
		}
	}
	return maxprofit
}
~~~



