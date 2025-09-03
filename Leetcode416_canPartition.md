/*
Time Complexity : O(m⋅n), where m is the subSetSum, and n is the number of array elements. The time complexity is the same as Approach 3.

Space Complexity: O(m), As we use an array of size m to store the result of subproblems.
*/

class Solution {
    public boolean canPartition(int[] nums) {
        if (nums.length == 0) {
            return false;
        }
        // return true of false. 
        // Break the list. into two Halfs. 
        int totalSum = 0;
        for (int num : nums) {
            totalSum += num;
        }
        if (totalSum % 2 != 0) {
            return false;
        }
        int subSetSum = totalSum / 2; // you are splitting the sum.
        boolean dp[] = new boolean[subSetSum + 1];
        dp[0] = true;
        for (int curr : nums) {
            for (int j = subSetSum; j >= curr; j--) {
                dp[j] |= dp[j - curr];
            }
        }
        return dp[subSetSum];
    }
}
