### 问题描述
假设按照升序排序的数组在预先未知的某个点上进行了旋转。

( 例如，数组 [0,1,2,4,5,6,7] 可能变为 [4,5,6,7,0,1,2] )。

搜索一个给定的目标值，如果数组中存在这个目标值，则返回它的索引，否则返回 -1 。

你可以假设数组中不存在重复的元素。

你的算法时间复杂度必须是 O(log n) 级别。
###问题解释
看题目的话首先想到就是葱头到位先搜首位看看跑到哪里了。
### 代码
```c
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int i;//verctor容器还是一个指针
        int len = nums.size();//数组长度
        int left = 0,right = len -1;//左右的索引
        while (left <= right){//二分查找，这里做的挺不错的
           
           int mid = (left + right)/2;//设置中间的索引
            if(target == nums[mid]) return mid;
            if(nums[mid] >= nums[left]){
                if(target < nums[mid] && target >=nums[left]){

                    right = mid -1;
                }
                else 
                    left = mid + 1;
            }
            else{
                if(target > nums[mid] && target <=nums[right]){
                    left = mid + 1;
                }
                else 
                    right = mid -1;
            }
        }
        return -1;
    }
};
```

