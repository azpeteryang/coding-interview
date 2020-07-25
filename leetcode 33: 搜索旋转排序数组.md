这个想法是，当旋转阵列时，必须有一半的阵列仍处于排序状态。例如6 7 1 2 3 4 5，该顺序从7到1之间的点被破坏了。因此，在执行二进制搜索时，我们可以判断哪个部分是有序的，以及目标是否在该范围内（如果是） ，请继续搜索另一半，如果不能继续搜索另一半。      

```java
public class Solution {
    public int search(int[] nums, int target) {
        int start = 0;
        int end = nums.length - 1;
        while (start <= end){
            int mid = (start + end) / 2;
            if (nums[mid] == target)
                return mid;
        
            if (nums[start] <= nums[mid]){
                 if (target < nums[mid] && target >= nums[start]) 
                    end = mid - 1;
                 else
                    start = mid + 1;
            } 
        
            if (nums[mid] <= nums[end]){
                if (target > nums[mid] && target <= nums[end])
                    start = mid + 1;
                 else
                    end = mid - 1;
            }
        }
        return -1;
    }
}
```
