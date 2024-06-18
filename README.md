# LEETCODE-Array-826
To dry run the `maxProfitAssignment` method, we'll go through each step of the method, explaining what happens with sample inputs. Let's consider the following example inputs:

- `difficulty = [2, 4, 6, 8]`
- `profit = [10, 20, 30, 40]`
- `worker = [5, 9, 1, 7]`

### Step-by-Step Execution:

1. **Initialization**:
   ```java
   int ans = 0;
   List<Pair<Integer, Integer>> jobs = new ArrayList<>();
   ```

2. **Populate the jobs list**:
   - For `i = 0`: jobs.add(new Pair<>(2, 10));
   - For `i = 1`: jobs.add(new Pair<>(4, 20));
   - For `i = 2`: jobs.add(new Pair<>(6, 30));
   - For `i = 3`: jobs.add(new Pair<>(8, 40));
   
   The jobs list now contains: `[(2, 10), (4, 20), (6, 30), (8, 40)]`.

3. **Sort the jobs list by difficulty**:
   ```java
   Collections.sort(jobs, Comparator.comparing(Pair::getKey));
   ```
   The jobs list remains sorted as: `[(2, 10), (4, 20), (6, 30), (8, 40)]` (already sorted).

4. **Sort the worker array**:
   ```java
   Arrays.sort(worker);
   ```
   The sorted worker array is: `[1, 5, 7, 9]`.

5. **Initialize variables for the loop**:
   ```java
   int i = 0;
   int maxProfit = 0;
   ```

6. **Iterate over each worker**:
   ```java
   for (final int w : worker) {
   ```

   - **Worker `w = 1`**:
     - The inner loop doesn't execute as `w < jobs.get(0).getKey() (1 < 2)`.
     - `maxProfit` remains 0.
     - `ans += maxProfit` -> `ans = 0`.

   - **Worker `w = 5`**:
     - Inner loop:
       - For `i = 0`: `5 >= 2`, `maxProfit = max(0, 10) = 10`, increment `i`.
       - For `i = 1`: `5 >= 4`, `maxProfit = max(10, 20) = 20`, increment `i`.
     - Loop ends as `5 < jobs.get(2).getKey() (5 < 6)`.
     - `ans += maxProfit` -> `ans = 20`.

   - **Worker `w = 7`**:
     - Inner loop:
       - For `i = 2`: `7 >= 6`, `maxProfit = max(20, 30) = 30`, increment `i`.
     - Loop ends as `7 < jobs.get(3).getKey() (7 < 8)`.
     - `ans += maxProfit` -> `ans = 50`.

   - **Worker `w = 9`**:
     - Inner loop:
       - For `i = 3`: `9 >= 8`, `maxProfit = max(30, 40) = 40`, increment `i`.
     - Loop ends as there are no more jobs.
     - `ans += maxProfit` -> `ans = 90`.

7. **Return the result**:
   ```java
   return ans; // ans = 90
   ```

### Summary:

For the given input:

- `difficulty = [2, 4, 6, 8]`
- `profit = [10, 20, 30, 40]`
- `worker = [5, 9, 1, 7]`

The method computes the maximum profit that can be assigned to the workers and returns `90`. This is achieved by sorting the jobs and workers, and then iterating through the workers to assign them the highest possible profit based on their ability.
