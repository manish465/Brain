---
tags:
  - dsa
---
```Java
class Solution {
    // Lower Bound: First position where arr[i] >= target
    public int lowerBound(int[] arr, int target) {
        int left = 0, right = arr.length;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (arr[mid] >= target) {
                right = mid;  // Move left to find the first occurrence
            } else {
                left = mid + 1;
            }
        }
        return left;  // Position of the first element >= target
    }

    // Upper Bound: First position where arr[i] > target
    public int upperBound(int[] arr, int target) {
        int left = 0, right = arr.length;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (arr[mid] > target) {
                right = mid;  // Move left to find the first greater element
            } else {
                left = mid + 1;
            }
        }
        return left;  // Position of the first element > target
    }
}
```
