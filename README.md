![python](https://logos-world.net/wp-content/uploads/2021/10/Python-Logo.png)

# Two Sum

## Description

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

## Example

**Example 1:**

```markdown
Input: nums = [2, 7, 11, 15], target = 9
Output: [0, 1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

Input: nums = [3, 2, 4], target = 6
Output: [1, 2]

Input: nums = [3, 3], target = 6
Output: [0, 1]
```

## Constraints

- `2 <= nums.length <= 10^4`
- `-10^9 <= nums[i] <= 10^9`
- `-10^9 <= target <= 10^9`
- Only one valid answer exists.

## Intuition

Find the sum of each value with every other value, but not with itself, through iteration.

## Approach

### Approach 1

The first approach is to use a nested loop to sum each number with every other number in the list and check if it equals the target value.

### Approach 2

The second approach is to find the complement of each value in the list from the target value and look for the result in a dictionary. This dictionary is filled with key-value pairs during each iteration.

## Complexity

### Approach 1

**Time Complexity:**

- The outer loop runs `n` times, where `n` is the length of `nums`.
- The inner loop also runs `n` times for each iteration of the outer loop.
- Thus, the total number of iterations is `n * n`, resulting in a time complexity of `O(n^2)`.

**Space Complexity:**

- The space complexity is `O(1)` because we are only using a fixed amount of extra space for `ind_list`, regardless of the input size.

### Approach 2

**Time Complexity:**

- The loop runs `n` times, where `n` is the length of `nums`.
- Checking if `complement` is in `hash_map` and inserting a new key-value pair both take `O(1)` time on average.
- Therefore, the total time complexity is `O(n)`.

**Space Complexity:**

- We are using a hash map (`hash_map`) to store up to `n` key-value pairs.
- Thus, the space complexity is `O(n)`.

``` python3
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        
        # approach 1
        # ind_list = []
        # for i in range(len(nums)):
        #     for j in range(len(nums)):
        #         if i != j and nums[i] + nums[j] == target:
        #             ind_list = [i, j]
        # return ind_list
        
        # approach 2
        hash_map = {}
        ind_list = []
        for i in range(len(nums)):
            complement = target - nums[i]
            if complement in hash_map:
                ind_list = [hash_map[complement], i]
                return ind_list3
            hash_map[nums[i]] = i
        return ind_list
```
## Installation

To run the code, ensure you have Python installed on your system. Save the code in a `.py` file and execute it using a Python interpreter.

## Usage

To use the function, create an instance of the `Solution` class and call the `twoSum` method with your list of `nums` and the `target` value.

## Example
```
nums = [2, 7, 11, 15]
target = 9
solution = Solution()
print(solution.twoSum(nums, target))  # Output: [0, 1]
```

## Contributing
If you'd like to contribute, please fork the repository and use a feature branch. Pull requests are warmly welcome.

## Acknowledgements
Thanks to the open-source community for providing helpful resources and inspiration. Special thanks to [LeetCode](https://leetcode.com) for the platform and resources.

# LeetCode Submission
You can view my LeetCode submission for this problem [here](https://leetcode.com/problems/two-sum/solutions/5491009/python-sum-of-two-solution)
