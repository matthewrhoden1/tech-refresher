
# Big O Notation

One thing I always forget about is Big O notation. I don't have a super strong math background, so this stuff isn't intuitive for me. If you're not familiar here's the typical Big O's that come up in interviews.

| Big O Notation | Description |
| --- | --- |
| $O(1)$ | Constant space. The memory used does not depend on the input size. |
| $O(log n)$ | Logarithmic space. Often seen in algorithms like binary search or divide-and-conquer. |
| $O(n)$ | Linear space. Memory grows proportionally with the input size (e.g., creating a new list). |
| $O(n log ⁡n)$ | Typical of algorithms that combine input data hierarchically (e.g., mergesort's temporary storage). |
| $O(n^2)$	| Quadratic space. Seen in algorithms using 2D arrays or storing pairwise relationships. |
| $O(2^n)$	| Exponential space. Seen in brute-force or exhaustive search algorithms (e.g., power set generation). |

## $log(n)$ vs $n log(n)$

![image](https://github.com/user-attachments/assets/3db252ec-6e4e-4750-84d2-7c862c817f22)

The graph shows the growth rates of $log⁡(n)$ and $n log⁡(n)$ as the input size n increases.

## $log⁡(n)$

Grows very slowly, even for large n.

Examples:
- For $n=10$: $log⁡(10)$≈3.32 (base 2).
- For $n=1000$: $log⁡(1000)≈9.97$.

Typical use case: Binary search, where the input size is halved at each step.

## $n log⁡(n)$:

Combines a linear growth (nn) with logarithmic growth (log⁡(n)log(n)).

Examples:
- For $n=10$: $n log⁡(n)≈33.2$.
- For $n=1000$: $n log⁡(n)≈9970$.

Typical use case: Divide-and-conquer algorithms like mergesort or heapsort.

**Key Differences**

$log⁡(n)$ grows very slowly, making it efficient in algorithms with many input divisions.
$n log⁡(n)$ grows faster because it scales linearly with n, making it suitable for sorting and hierarchical data processing.

## $O(n^2)$	vs $O(2^n)$	

![image](https://github.com/user-attachments/assets/babbfd50-e615-4cac-b909-68a1790a6821)

The graph shows the growth rates of $O(n^2)$ and $O(2^n)$ as the input size n increases.

## $O(n^2)$	

Grows quadratically with the input size n.

Examples:
- For $n=10$: $n^2=100$.
- For $n=20$: $n2=400$.

Typical use case: Algorithms that compare every pair of elements, such as bubble sort or calculating all pairwise distances.

## $O(2^n)$	

Grows exponentially, meaning it doubles for every increase in n.

Examples:
- For $n=10$: $2^n=1024$.
- For $n=20$: $2^n=1,048,5762$.

Typical use case: Exhaustive search algorithms (e.g., generating all subsets or solving combinatorial problems).

Key Differences:

$O(n^2)$: Growth is manageable for moderate n but becomes inefficient for very large inputs.
$O(2^n)$: Growth is extremely rapid, making it impractical for even relatively small n (e.g., n>20n>20).

## Time and SPACE complexity

Big O notation is actually used for both time and space complexity. So you will need to keep both of these in mind when thinking about an algorithm to implement.

Something to keep in mind when thinking of space is also how it's going to be used.

Temporary Memory vs. Input Size:

Temporary memory includes:
 - Auxiliary data structures.
 - Variables for intermediate computations.
 - Stack space for recursion.

Input memory is the memory used to store the input data itself.

## Quiz! (Answers Below)

1. Classify each of these code samples with a given Big O:

```csharp
// A
var n = arr.Length;

for (var i = 0; i < n - 1; i++)
{
    for (var j = 0; j < n - i - 1; j++)
    {
        if (arr[j] > arr[j + 1])
        {
            var temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
        }
    }
}

// B
var sorted = Array.Sort(arr);

// C
var valueFound = dict[value];
```

2. Order these from best to worst performance:
- A. $O(n log ⁡n)$
- B. $O(1)$ 
- C. $O(2^n)$
- D. $O(log n)$
- E. $O(n^2)$
- F. $O(n)$

3. What kind of temporary memory is used in these sudo functions:
   
```csharp
// A
var sort = (int[] arr) => { 
  var n = arr.Length;
  
  for (var i = 0; i < n - 1; i++)
  {
      for (var j = 0; j < n - i - 1; j++)
      {
          if (arr[j] > arr[j + 1])
          {
              var temp = arr[j];
              arr[j] = arr[j + 1];
              arr[j + 1] = temp;
          }
      }
  }
}

// B
(inputArray) => {
  var dictionary = new();

  foreach(var element in inputArray) {
     if(dictionary.ContainsKey(element)) {
        return true;
     }
     dictionary.Add(element);
   }

  return false;
}

// C
int Factorial(int n)
{
    // Base case: factorial of 0 or 1 is 1
    if (n == 0 || n == 1)
        return 1;

    // Recursive case
    return n * Factorial(n - 1);
}
```




























# Answers

1. A: $O(n^2)$ B: $O(n log(n))$ C: $O(1)$
2. B, F, D, A, E, C
3. A: variables B: variables and auxiliary C: stack space, variables
