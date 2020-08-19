# Combination Sum

Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.

The same repeated number may be chosen from candidates unlimited number of times.

Note:

All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.

Example 1:

Input: candidates = [2,3,6,7], target = 7,
A solution set is:
[
  [7],
  [2,2,3]
]

Example 2:

Input: candidates = [2,3,5], target = 8,
A solution set is:
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]

## 출처 : https://leetcode.com/problems/combination-sum/

<pre><code>
public List<List<Integer>> combinationSum(int[] candidates, int target) {
        ans = new ArrayList<List<Integer>>();
        list = new ArrayList<>();
        targetValue = target;

        if(candidates.length == 0) {
            ans.add(list);
            return ans;
        }

        Arrays.sort(candidates);
        go(candidates, 0, 0);

        return ans;
    }

    private void go(int[] arr, int lo, int curValue) {
        if(curValue == targetValue) {
            ans.add(new ArrayList<Integer>(list));
            return;
        }

        for(int i = lo; i < arr.length; i++) {
            if(curValue + arr[i] <= targetValue) {
                list.add(arr[i]);
                go(arr, i, curValue + arr[i]);
                list.remove(list.size() - 1);
            } else
                break;
        }
    }
</code></pre>

