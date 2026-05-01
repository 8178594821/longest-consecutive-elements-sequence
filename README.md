# longest-consecutive-elements-sequence

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.
Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: Longest sequence = [1,2,3,4]

Sab elements ko HashSet me daal do
Sirf wahi number se sequence start karo jiska previous number (num-1) exist nahi karta
Fir aage count karo (num+1, num+2, …)


Complexity	Value
Time	O(n)
Space	O(n)

code 
class Solution {
    public int longestConsecutive(int[] nums) {
        HashSet<Integer> set = new HashSet<>();

        for (int num : nums) {
            set.add(num);
        }
        
        int longest = 0;
        
        for (int num : set) {
            
            if (!set.contains(num - 1)) {
                
                int currentNum = num;
                int currentStreak = 1;
                
                
                while (set.contains(currentNum + 1)) {
                    currentNum++;
                    currentStreak++;
                }
                
                longest = Math.max(longest, currentStreak);
            }
        }
        
        return longest;
    }
}
Dry Run code
nums = [100,4,200,1,3,2]
set = {1,2,3,4,100,200}

Start from 1 → sequence: 1→2→3→4 → length = 4
Start from 100 → length = 1
Start from 200 → length = 1

Max = 4

If you found this helpful, give this repo a ⭐ and follow for more DSA solutions 🚀
