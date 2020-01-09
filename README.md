# Four Sum
## https://leetcode.com/problems/4sum


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
		if(result.size() == 0) {
			result.add(Arrays.asList(quadruplet));
		}
		
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
