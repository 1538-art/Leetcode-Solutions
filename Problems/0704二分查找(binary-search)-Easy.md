# 二分查找(binary-search)

> Easy

## 题目

给定一个 `n` 个元素有序的（升序）整型数组 `nums` 和一个目标值 `target` ，写一个函数搜索 `nums` 中的 `target`，如果目标值存在返回下标，否则返回 `-1`。


### 示例 1
```
输入: nums = [-1,0,3,5,9,12], target = 9
输出: 4
解释: 9 出现在 nums 中并且下标为 4
```
### 示例 2
```
输入: nums = [-1,0,3,5,9,12], target = 2
输出: -1
解释: 2 不存在 nums 中因此返回 -1
```
### 提示

1. 你可以假设 `nums` 中的所有元素是不重复的。
2. `n` 将在 `[1, 10000]`之间。
3. `nums` 的每个元素都将在 `[-9999, 9999]`之间。

Related Topics
- 数组
- 二分查找

- 👍 1531
- 👎 0

## 已给代码

```c
int search(int* nums, int numsSize, int target){
  
}
```
## 解析

**这道题目的前提是数组为有序数组**，同时题目还强调**数组中无重复元素**，因为一旦有重复元素，使用二分查找法返回的元素下标可能不是唯一的，这些都是使用二分法的前提条件，当大家看到题目描述满足如上条件的时候，可要想一想是不是可以用二分法了。

```c
int search(int* nums, int numsSize, int target){
    int left = 0;
    int right = numsSize-1;
    int middle = 0;
    //若left小于等于right，说明区间中元素不为0
    while(left<=right) {
        //更新查找下标middle的值
        middle = (left+right)/2;
        //此时target可能会在[left,middle-1]区间中
        if(nums[middle] > target) {
            right = middle-1;
        } 
        //此时target可能会在[middle+1,right]区间中
        else if(nums[middle] < target) {
            left = middle+1;
        } 
        //当前下标元素等于target值时，返回middle
        else if(nums[middle] == target){
            return middle;
        }
    }
    //若未找到target元素，返回-1
    return -1;
}
```