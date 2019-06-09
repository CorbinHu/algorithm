```java
package com.hbc.text;

public class BinarySearch {
    public static void main(String[] args) {
        int[] nums = {2, 4, 5, 6, 9};
//        int[] nums = {0, 1, 1, 1, 1};

        int target = 7;
        int local = findEqual(nums, target);
        local = findGt(nums,target);
        System.out.println(local);
    }

    // 需查找和目标值完全相等的数
    private static int findEqual(int[] nums, int target) {
        int left = 0, right = nums.length - 1;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) return mid;
            else if (nums[mid] < target) left = mid+1;
            else right = mid;
        }
        return -1;
    }

    // 查找第一个不小于(大于或等于)目标值的数，可变形为查找最后一个小于目标值的数
    private static int findGe(int[] nums, int target) {
        int left=0,right = nums.length-1;
        while(left<right){
            int mid = left+(right-left)/2;
            if (nums[mid]<target) left = mid+1;
            else right=mid;
        }
        if (nums[right]>=target) return right;
        else return -1;
    }

    // 查找第一个大于目标值的数，可变形为查找最后一个不大于目标值的数
    private static int findGt(int[] nums, int target) {
        int left=0,right = nums.length-1;
        while(left<right){
            int mid = left+(right-left)/2;
            if (nums[mid]<=target) left = mid+1;
            else right=mid;
        }
        if (nums[right]>target) return right;
        else return -1;
    }

}


```
