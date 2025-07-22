class Solution {
    public int[] maxNumber(int[] nums1, int[] nums2, int k) {
        int[] best = new int[k];
        int m = nums1.length, n = nums2.length;

        int start = Math.max(0, k - n), end = Math.min(k, m);

        for (int i = start; i <= end; i++) {
            int[] part1 = pickMax(nums1, i);
            int[] part2 = pickMax(nums2, k - i);
            int[] candidate = merge(part1, part2);
            if (greater(candidate, 0, best, 0)) {
                best = candidate;
            }
        }
        return best;
    }

    // Step 1: Pick max subsequence of length t from nums
    private int[] pickMax(int[] nums, int t) {
        int[] stack = new int[t];
        int top = -1, drop = nums.length - t;
        for (int num : nums) {
            while (top >= 0 && drop > 0 && stack[top] < num) {
                top--; drop--;
            }
            if (top + 1 < t) {
                stack[++top] = num;
            } else {
                drop--;
            }
        }
        return stack;
    }

    // Step 2: Merge two arrays into the largest lexicographical order
    private int[] merge(int[] a, int[] b) {
        int[] res = new int[a.length + b.length];
        int i = 0, j = 0, r = 0;
        while (i < a.length || j < b.length) {
            if (greater(a, i, b, j)) {
                res[r++] = i < a.length ? a[i++] : b[j++];
            } else {
                res[r++] = j < b.length ? b[j++] : a[i++];
            }
        }
        return res;
    }

    // Step 3: Lexicographical comparison between a[i:] and b[j:]
    private boolean greater(int[] a, int i, int[] b, int j) {
        while (i < a.length && j < b.length && a[i] == b[j]) {
            i++; j++;
        }
        return j == b.length || (i < a.length && a[i] > b[j]);
    }
}
