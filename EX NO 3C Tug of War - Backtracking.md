
# EX 3C Tug of War problem - Backtracking.

## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm
1.Start and read the array elements.

2.Calculate the total sum of all elements.

3.If the total sum is odd, return false (cannot partition equally).

4.Use dynamic programming to check if any subset sums to totalSum / 2.

5.If such a subset exists, return true; otherwise, return false.


## Program:
```

import java.util.Scanner;
public class Solution {
    public boolean canPartition(int[] nums) {
        //Type your code here
        if(nums.length==0)
        return false;
        int totalSum=0;
        for(int num:nums){
            totalSum+=num;
        }
        if(totalSum%2!=0)
        return false;
        int subSetSum=totalSum/2;
        boolean[] dp=new boolean[subSetSum+1];
        dp[0]=true;
        for(int curr:nums){
            for(int j=subSetSum;j>=curr;j--){
                dp[j]|=dp[j-curr];
            }
        }
        return dp[subSetSum];
        
        
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
    }
}

```

## Output:

<img width="401" height="232" alt="image" src="https://github.com/user-attachments/assets/25f33a98-9e09-452b-a2e8-113f01e309b1" />


## Result:
The program successfully implemented and the expected output is verified.
