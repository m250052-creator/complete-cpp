# Arrays Problems

## Easy Problems

### Problem 1: Find the Largest Element in an Array
**Description**: Write a C++ function that returns the largest element from an array of integers.
**Solution**:
```cpp
int findLargest(int arr[], int size) {
    int largest = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] > largest) {
            largest = arr[i];
        }
    }
    return largest;
}
```

### Problem 2: Check if Array is Sorted
**Description**: Write a function that checks if a given array is sorted in ascending order.
**Solution**:
```cpp
bool isSorted(int arr[], int size) {
    for (int i = 1; i < size; i++) {
        if (arr[i] < arr[i - 1]) {
            return false;
        }
    }
    return true;
}
```

### Problem 3: Reverse an Array
**Description**: Write a C++ function to reverse an array.
**Solution**:
```cpp
void reverseArray(int arr[], int size) {
    for (int i = 0; i < size / 2; i++) {
        std::swap(arr[i], arr[size - i - 1]);
    }
}
```

### Problem 4: Count Occurrences of an Element
**Description**: Write a function that counts how many times a given element appears in an array.
**Solution**:
```cpp
int countOccurrences(int arr[], int size, int x) {
    int count = 0;
    for (int i = 0; i < size; i++) {
        if (arr[i] == x) {
            count++;
        }
    }
    return count;
}
```

### Problem 5: Find Minimum and Maximum
**Description**: Write a function to find both the minimum and maximum elements in an array.
**Solution**:
```cpp
void findMinMax(int arr[], int size, int &min, int &max) {
    min = max = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] < min) min = arr[i];
        if (arr[i] > max) max = arr[i];
    }
}
```

### Problem 6: Rotate Array
**Description**: Write a function to rotate the elements of an array to the right by one.
**Solution**:
```cpp
void rotateArray(int arr[], int size) {
    int last = arr[size - 1];
    for (int i = size - 1; i > 0; i--) {
        arr[i] = arr[i - 1];
    }
    arr[0] = last;
}
```

### Problem 7: Merge Two Arrays
**Description**: Write a function to merge two arrays into a single array.
**Solution**:
```cpp
void mergeArrays(int arr1[], int size1, int arr2[], int size2, int result[]) {
    for (int i = 0; i < size1; i++) {
        result[i] = arr1[i];
    }
    for (int i = 0; i < size2; i++) {
        result[size1 + i] = arr2[i];
    }
}
```

### Problem 8: Sum of Elements in an Array
**Description**: Write a function to calculate the sum of all elements in an array.
**Solution**:
```cpp
int sumArray(int arr[], int size) {
    int sum = 0;
    for (int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return sum;
}
```

### Problem 9: Second Largest Element
**Description**: Write a function that returns the second largest element in an array.
**Solution**:
```cpp
int findSecondLargest(int arr[], int size) {
    int largest = INT_MIN, secondLargest = INT_MIN;
    for (int i = 0; i < size; i++) {
        if (arr[i] > largest) {
            secondLargest = largest;
            largest = arr[i];
        } else if (arr[i] > secondLargest && arr[i] < largest) {
            secondLargest = arr[i];
        }
    }
    return secondLargest;
}
```

### Problem 10: Remove Duplicates
**Description**: Write a function to remove duplicate elements from an array.
**Solution**:
```cpp
int removeDuplicates(int arr[], int size) {
    std::set<int> seen;
    int j = 0;
    for (int i = 0; i < size; i++) {
        if (seen.find(arr[i]) == seen.end()) {
            seen.insert(arr[i]);
            arr[j++] = arr[i];
        }
    }
    return j;
}
```

## Medium Problems

### Problem 11: Two Sum
**Description**: Write a function to find indices of the two numbers such that they add up to a specific target.
**Solution**:
```cpp
std::pair<int, int> twoSum(int arr[], int size, int target) {
    std::unordered_map<int, int> map;
    for (int i = 0; i < size; i++) {
        int complement = target - arr[i];
        if (map.find(complement) != map.end()) {
            return {map[complement], i};
        }
        map[arr[i]] = i;
    }
    return {-1, -1}; // Not found
}
```

### Problem 12: Max Consecutive Ones
**Description**: Given a binary array, find the maximum number of consecutive 1s in it.
**Solution**:
```cpp
int findMaxConsecutiveOnes(std::vector<int>& nums) {
    int maxCount = 0, currentCount = 0;
    for (int num : nums) {
        currentCount = (num == 1) ? currentCount + 1 : 0;
        maxCount = std::max(maxCount, currentCount);
    }
    return maxCount;
}
```

### Problem 13: Best Time to Buy and Sell Stock
**Description**: Given an array where the ith element is the price of a given stock on day i, return the maximum profit you can achieve.
**Solution**:
```cpp
int maxProfit(std::vector<int>& prices) {
    int maxProfit = 0, minPrice = prices[0];
    for (int price : prices) {
        if (price < minPrice) {
            minPrice = price;
        } else if (price - minPrice > maxProfit) {
            maxProfit = price - minPrice;
        }
    }
    return maxProfit;
}
```

### Problem 14: Move Zeroes
**Description**: Given an array, move all zeroes to the end without changing the order of non-zero elements.
**Solution**:
```cpp
void moveZeroes(std::vector<int>& nums) {
    int j = 0;
    for (int i = 0; i < nums.size(); i++) {
        if (nums[i] != 0) {
            nums[j++] = nums[i];
        }
    }
    for (; j < nums.size(); j++) {
        nums[j] = 0;
    }
}
```

### Problem 15: Product of Array Except Self
**Description**: Given an array nums of n integers where n > 1, return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].
**Solution**:
```cpp
std::vector<int> productExceptSelf(std::vector<int>& nums) {
    int n = nums.size();
    std::vector<int> answer(n);
    int leftProduct = 1;
    for (int i = 0; i < n; i++) {
        answer[i] = leftProduct;
        leftProduct *= nums[i];
    }
    int rightProduct = 1;
    for (int i = n - 1; i >= 0; i--) {
        answer[i] *= rightProduct;
        rightProduct *= nums[i];
    }
    return answer;
}
```

## Hard Problems

### Problem 16: Group Anagrams
**Description**: Given an array of strings, group anagrams together.
**Solution**:
```cpp
std::vector<std::vector<std::string>> groupAnagrams(std::vector<std::string>& strs) {
    std::unordered_map<std::string, std::vector<std::string>> anagrams;
    for (std::string str : strs) {
        std::string key = str;
        std::sort(key.begin(), key.end());
        anagrams[key].push_back(str);
    }
    std::vector<std::vector<std::string>> result;
    for (auto& pair : anagrams) {
        result.push_back(pair.second);
    }
    return result;
}
```

### Problem 17: Longest Increasing Subsequence
**Description**: Given an integer array, return the length of the longest strictly increasing subsequence.
**Solution**:
```cpp
int lengthOfLIS(std::vector<int>& nums) {
    std::vector<int> dp(nums.size(), 1);
    for (int i = 1; i < nums.size(); i++) {
        for (int j = 0; j < i; j++) {
            if (nums[i] > nums[j]) {
                dp[i] = std::max(dp[i], dp[j] + 1);
            }
        }
    }
    return *std::max_element(dp.begin(), dp.end());
}
```

### Problem 18: Container With Most Water
**Description**: Given n non-negative integers a1, a2, ..., an, where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines that together with the x-axis forms a container that holds the most water.
**Solution**:
```cpp
int maxArea(std::vector<int>& height) {
    int left = 0, right = height.size() - 1, maxArea = 0;
    while (left < right) {
        int area = std::min(height[left], height[right]) * (right - left);
        maxArea = std::max(maxArea, area);
        if (height[left] < height[right]) {
            left++;
        } else {
            right--;
        }
    }
    return maxArea;
}
```

### Problem 19: Find First and Last Position of Element in Sorted Array
**Description**: Given an array of integers sorted in ascending order, find the starting and ending position of a given target value.
**Solution**:
```cpp
std::vector<int> searchRange(std::vector<int>& nums, int target) {
    std::vector<int> result(2, -1);
    int left = 0, right = nums.size() - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] < target) {
            left = mid + 1;
        } else if (nums[mid] > target) {
            right = mid - 1;
        } else {
            // Found target, look for boundaries
            int start = mid, end = mid;
            while (start >= 0 && nums[start] == target) start--;
            while (end < nums.size() && nums[end] == target) end++;
            result[0] = start + 1;
            result[1] = end - 1;
            return result;
        }
    }
    return result;
}
```

### Problem 20: Majority Element
**Description**: Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊n/2⌋ times.
**Solution**:
```cpp
int majorityElement(std::vector<int>& nums) {
    int candidate = nums[0], count = 1;
    for (int i = 1; i < nums.size(); i++) {
        if (nums[i] == candidate) {
            count++;
        } else if (--count == 0) {
            candidate = nums[i];
            count = 1;
        }
    }
    return candidate;
}
```

## Hardest Problems

### Problem 21: 3Sum
**Description**: Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.
**Solution**:
```cpp
std::vector<std::vector<int>> threeSum(std::vector<int>& nums) {
    std::sort(nums.begin(), nums.end());
    std::vector<std::vector<int>> result;
    for (int i = 0; i < nums.size(); i++) {
        if (i > 0 && nums[i] == nums[i - 1]) continue;
        int left = i + 1, right = nums.size() - 1;
        while (left < right) {
            int sum = nums[i] + nums[left] + nums[right];
            if (sum < 0) left++;
            else if (sum > 0) right--;
            else {
                result.push_back({nums[i], nums[left], nums[right]});
                while (left < right && nums[left] == nums[left + 1]) left++;
                while (left < right && nums[right] == nums[right - 1]) right--;
                left++;
                right--;
            }
        }
    }
    return result;
}
```

### Problem 22: Insert Interval
**Description**: Given a collection of intervals, insert a new interval into the intervals (merge if necessary).
**Solution**:
```cpp
std::vector<Interval> insert(std::vector<Interval>& intervals, Interval newInterval) {
    std::vector<Interval> merged;
    int i = 0;
    while (i < intervals.size() && intervals[i].end < newInterval.start) {
        merged.push_back(intervals[i++]);
    }
    while (i < intervals.size() && intervals[i].start <= newInterval.end) {
        newInterval.start = std::min(newInterval.start, intervals[i].start);
        newInterval.end = std::max(newInterval.end, intervals[i].end);
        i++;
    }
    merged.push_back(newInterval);
    while (i < intervals.size()) {
        merged.push_back(intervals[i++]);
    }
    return merged;
}
```

### Problem 23: Longest Consecutive Sequence
**Description**: Given an unsorted array of integers, find the length of the longest consecutive elements sequence.
**Solution**:
```cpp
int longestConsecutive(std::vector<int>& nums) {
    std::unordered_set<int> numSet(nums.begin(), nums.end());
    int longestStreak = 0;
    for (int num : numSet) {
        if (!numSet.count(num - 1)) {
            int currentNum = num;
            int currentStreak = 1;
            while (numSet.count(currentNum + 1)) {
                currentNum++;
                currentStreak++;
            }
            longestStreak = std::max(longestStreak, currentStreak);
        }
    }
    return longestStreak;
}
```

### Problem 24: Car Fleet
**Description**: There are n cars going to the same destination along a one-lane road. The destination is target miles away. Each car i has a speed of speed[i] miles per hour and initial position position[i] miles towards the target. Return the total number of car fleets that will arrive at the destination.
**Solution**:
```cpp
int carFleet(int target, std::vector<int>& position, std::vector<int>& speed) {
    std::vector<std::pair<double, double>> cars;
    for (int i = 0; i < position.size(); i++) {
        cars.push_back({position[i], (target - position[i]) / (double)speed[i]});
    }
    std::sort(cars.rbegin(), cars.rend());
    int fleets = 0;
    double curTime = 0;
    for (auto& car : cars) {
        if (car.second > curTime) {
            fleets++;
            curTime = car.second;
        }
    }
    return fleets;
}
```

### Problem 25: Kth Largest Element in an Array
**Description**: Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.
**Solution**:
```cpp
int findKthLargest(std::vector<int>& nums, int k) {
    std::priority_queue<int, std::vector<int>, std::greater<int>> minHeap;
    for (int num : nums) {
        minHeap.push(num);
        if (minHeap.size() > k) {
            minHeap.pop();
        }
    }
    return minHeap.top();
}
```

