# LEETCODE-Trie-440
Let's go through a dry run of the given code step by step with an example input.

### Problem Context:
The function `findKthNumber` is trying to find the **k-th smallest number** in the range `[1, n]` in **lexicographical order**.

### Example Input:
Let’s take `n = 13` and `k = 2`. We are trying to find the 2nd smallest number in lexicographical order between 1 and 13.

#### Initial Setup:
- `ans = 1`: This is the current candidate for the k-th number.
- `i = 1`: This keeps track of how many numbers have been counted in the lexicographical order so far.

### First Iteration of the Loop:
- **`gap = getGap(ans, ans + 1, n)`**:
  - `ans = 1`, `ans + 1 = 2`, `n = 13`.
  - Now calculate the gap between `1` and `2` in the lexicographical tree:
    
    **getGap(1, 2, 13)**:
    - `gap = 0`
    - Initially `a = 1`, `b = 2`
    - In the first level of the tree, we have numbers between 1 and 2: 1 (so gap += 1).
    - Now `a *= 10` becomes 10, and `b *= 10` becomes 20.
    - At the next level, we have numbers between 10 and 13: 10, 11, 12, 13 (so gap += 4).
    - `a = 100` exceeds `n = 13`, so the while loop terminates.
    - **Total gap = 5**.
  
  Now we check if `i + gap <= k`:
  - `i = 1`, `gap = 5`, `k = 2`.
  - Since `1 + 5 > 2`, this means that the 2nd number is still within the subtree starting with 1.
  - So, we move deeper into the subtree by setting `ans = 1 * 10 = 10`.
  - Now `i = 2` since we have considered one more number.

### Exit Condition:
- Now `i == k` (both are 2), so we stop the loop and return the current value of `ans`, which is `10`.

### Final Answer:
The 2nd smallest number in lexicographical order between 1 and 13 is **10**.
