# Four Sum
## https://leetcode.com/problems/4sum

Given an array nums of n integers and an integer target, are there elements a, b, c, and d in nums such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.

**Note: The solution set must not contain duplicate quadruplets.**

```
Example:

Given array nums = [1, 0, -1, 0, -2, 2], and target = 0.

A solution set is:
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]
```

## Implementation :

```java
public static List<List<Integer>> fourSum(int[] nums, int target) {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
    	if(nums == null || nums.length < 4)
        	return result;
    	
    	int n = nums.length; 
    	for(int i = 0; i < n - 3; i++) {
    	    for(int j = i + 1; j < n - 2; j++) {
    		for(int k = j + 1; k < n - 1; k++) {
    		    for(int l = k + 1; l < n; l++) {
    			 if((nums[i] + nums[j] + nums[k] + nums[l]) == target ) {
        			addResult(result, new Integer[] {nums[i], nums[j], nums[k], nums[l]});
        			break;
        		   }
    		     }
    		 }
    	    }
    	}
    	
    	return result;
}

private static void addResult(List<List<Integer>> result, Integer[] quadruplet) {
	Set<Integer> fourSum = new HashSet<Integer>(Arrays.asList(quadruplet));
	boolean alredayExists = false;
	for(List<Integer> list: result) {
		Set<Integer> res = new HashSet<Integer>(list);
		if(res.equals(fourSum)) {
		    alredayExists = true;
		    break;
		}
	}
	
	if(!alredayExists) {
	   result.add(Arrays.asList(quadruplet));
	}	
 }
```

The runtime complexity of above implementation is O(n^4) and space complexity is O(1)
```
Runtime Complexity = O(n^4)
Space Complexity   = O(1)
```

