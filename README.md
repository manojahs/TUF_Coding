# TUF_Coding
```
Find the largest element in an array
------------------------------------------

int[] array = { 1, 2, 4, 5, 6, 7, 8, 9, 10, 11, 21, 12, 13, 14, 15, 16, 17, 18, 19, 20 };


int max = array[0];
for (int i = 1; i < array.Length; i++)
{
    if (array[i] > max)
    {
        max = array[i];
    }
}

Console.WriteLine($"Largest element: {max}");

Find the 2nd Largest value in an array
---------------------------------------
int[] array = { 1, 2, 4, 5, 6, 7, 8, 9, 10, 11, 21, 12, 13, 14, 15, 16, 17, 18, 19, 20 };

int largest = array[0];
int secondLargest = array[0];

for (int i = 1; i < array.Length; i++)
{
    if (array[i] > largest)
    {
        secondLargest = largest;
        largest = array[i];
    }
    else if (array[i] > secondLargest && array[i] != largest)
    {
        secondLargest = array[i];
    }
}

Console.WriteLine("The largest number is: " + largest);
Console.WriteLine("The second largest number is: " + secondLargest);

Check the array is it sorted or not
--------------------------------------

int[] array = { 1,3,2};

Console.WriteLine( checkArray(array));

 static bool checkArray(int[] array)
{
   
for (int i = 0; i < array.Length-1; i++)
{
    if (array[i] > array[i + 1])
        return false;
}

return true;
}


Remove Duplicates
----------------------
int[] sortedArray = { 2, 2,  3, 4, 4, 5, 6, 6, 7 };

int[] uniqueSorted = RemoveDuplicates(sortedArray);
Console.WriteLine("Unique elements in sorted array:");
foreach (var item in uniqueSorted)
{
    Console.Write(item + " ");
}

// Removes duplicates from a sorted array
static int[] RemoveDuplicates(int[] arr)
{
    if (arr.Length == 0)
        return new int[0];
     List<int> result = new List<int> { arr[0] };
    for (int i = 1; i < arr.Length; i++)
    {
        if (arr[i] != arr[i - 1])
            result.Add(arr[i]);
    }
     return result.ToArray();
}

--2 sum array
int[] nums = { 2, 7, 11, 15 };
int target = 9;
int[] result = TwoSum(nums, target);

Console.WriteLine($"Indices: {result[0]}, {result[1]}");  // Output: Indices: 0, 1


public int[] TwoSum(int[] nums, int target) 
{
    Dictionary<int, int> map = new Dictionary<int, int>();

    for (int i = 0; i < nums.Length; i++) 
    {
        int complement = target - nums[i];
        if (map.ContainsKey(complement)) 
        {
            return new int[] { map[complement], i };
        }
        map[nums[i]] = i;
    }
    return new int[0]; // if no solution found
}

--Frequncy of duplicate character count
using System;
class Program
{
    static void Main()
    {
        string[] a = { "Black", "Brown", "Black","Yellow","Yellow" };

        Dictionary<string,int> keyValuePairs = new Dictionary<string,int>();
        foreach(var v in a)
        {
            //if (keyValuePairs.ContainsKey(v))
            //{
            //    keyValuePairs[v]++;
            //}
            //else
            //{
            //    {
            //        keyValuePairs[v] = 1;
            //    }
            //}

            keyValuePairs[v] = keyValuePairs.GetValueOrDefault(v ,0) + 1;
        }

       var vss= keyValuePairs.OrderByDescending(x => x.Key).Where(a => a.Value > 1).Select(a => a.Key);
        

        foreach(var vs in vss)
        {
            Console.WriteLine(vs);

        }

    }
}

Balanced or not
----------------

using System;
using System.Collections.Generic;

class Program
{
    // Function to check if brackets are balanced
    public static bool IsBalanced(string input)
    {
        Stack<char> stack = new Stack<char>();

        foreach (char c in input)
        {
            // If opening bracket → push
            if (c == '{' || c == '[' || c == '(')
            {
                stack.Push(c);
            }
            // If closing bracket → check
            else if (c == '}' || c == ']' || c == ')')
            {
                if (stack.Count == 0)
                    return false; // No opening for this closing

                char top = stack.Pop(); // last opened

                // Mismatch check
                if ((c == '}' && top != '{') ||
                    (c == ']' && top != '[') ||
                    (c == ')' && top != '('))
                {
                    return false; // Wrong pair
                }
            }
        }

        // At the end, stack must be empty
        return stack.Count == 0;
    }

    // Main method
    public static void Main()
    {
        string[] tests = { "([]{})", "([)]", "((()))", "{[()]}", "(]" };

        foreach (var test in tests)
        {
            bool result = IsBalanced(test);
            Console.WriteLine($"{test} -> {(result ? "Balanced" : "Not Balanced")}");
        }
    }
}


//fizz buzz problem
-----------------

using System.Text;

var dict = new Dictionary<int, string>()
{
    {3,"Fizz"},
    {5,"Buzz"},
    {11,"Eleven"},
    {7,"Seven"}
};

for (int i = 1; i <= 100; i++)
{
   string res = string.Empty;
    foreach (var item in dict)
    {
        if (i % item.Key == 0)
        {
            res = res+""+item.Value;
        }
    }

    if (res.Length == 0)
    {
        res =i.ToString();
    }

    Console.WriteLine(res.ToString());
}

Find the longest subarray length with unique values inside a given array.
---------------------------------------------------------------------------

using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        int[] arr = { 1, 2, 3, 1, 2 };
        Console.WriteLine("Longest length = " + LongestUniqueSubarray(arr));

        string s = "abcdabcbb";
        Console.WriteLine("Longest substring length = " + LongestUniqueSubstring(s));
    }

    static int LongestUniqueSubarray(int[] arr)
    {
        HashSet<int> set = new HashSet<int>();
        int left = 0, maxLen = 0;

        for (int right = 0; right < arr.Length; right++)
        {
            while (set.Contains(arr[right]))
            {
                set.Remove(arr[left]);
                left++;
            }

            set.Add(arr[right]);
            maxLen = Math.Max(maxLen, right - left + 1);
        }

        return maxLen;
    }



    static int LongestUniqueSubstring(string s)
    {
        HashSet<char> set = new HashSet<char>();
        int left = 0, maxLen = 0;

        for (int right = 0; right < s.Length; right++)
        {
            while (set.Contains(s[right]))
            {
                set.Remove(s[left]);
                left++;
            }

            set.Add(s[right]);
            maxLen = Math.Max(maxLen, right - left + 1);
        }

        return maxLen;
    }
}

Fib using Recursion but it takes 2 of n and its very slow
----------------------------------------
using System;
class Program
{
    static int Fibonacci(int n)
    {
        if (n == 0) return 0;   // base case
        if (n == 1) return 1;   // base case

        // recursive case
        return Fibonacci(n - 1) + Fibonacci(n - 2);
    }

    static void Main()
    {
        int n = 10; // print first 10 numbers
        Console.WriteLine($"Fibonacci series up to {n} terms:");

        for (int i = 0; i < n; i++)
        {
            Console.Write(Fibonacci(i) + " ");
        }
    }
}

OR O(n)
-----------
using System;
using System.Collections.Generic;

class Program
{
    static Dictionary<int, int> memo = new Dictionary<int, int>();
    static int Fibonacci(int n)
    {
        if (n == 0) return 0;
        if (n == 1) return 1;

        // Check cache
        if (memo.ContainsKey(n))
            return memo[n];

        // Compute and store in cache
        int result = Fibonacci(n - 1) + Fibonacci(n - 2);
        memo[n] = result;
        return result;
    }

    static void Main()
    {
        int n = 10; // print first 10 Fibonacci numbers
        Console.WriteLine($"Fibonacci series up to {n} terms:");
        for (int i = 0; i < n; i++)
        {
            Console.Write(Fibonacci(i) + " ");
        }
    }
}

Using Iteration 0(n)
-------------------
using System;

class Program
{
    static void FibonacciIterative(int n)
    {
        int a = 0, b = 1, c;


        for (int i = 0; i < n; i++)
        {
            Console.Write(a + " ");
            c = a + b;    
            a = b;        
            b = c;
        }
    }

    static void Main()
    {
        int n = 10; // print first 10 Fibonacci numbers
        Console.WriteLine($"Fibonacci series up to {n} terms:");
        FibonacciIterative(n);
    }
}

Rotate the array using recursrion (Left and Right by k element) - Sliding Window
---------------------------------------------------------------------------------

using System;

class Program
{
    // Reverse helper
    static void Reverse(int[] arr, int start, int end)
    {
        while (start < end)
        {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }

    // Left Rotate by k
    static void LeftRotate(int[] arr, int k)
    {
        int n = arr.Length;
        k = k % n; // handle k > n

        Reverse(arr, 0, n - 1);     // Step 1: reverse first k     [7,6,5,4,3,2,1] 
        Reverse(arr, 0, n-k-1);  //(0,4)   // Step 2: reverse rest          [3,4,5,6,7,2,1]
        Reverse(arr, n-k, n-1); 
    }

    // Right Rotate by k
    static void RightRotate(int[] arr, int k)
    {
        int n = arr.Length;
        k = k % n;

        Reverse(arr, 0, n - 1);         // Step 1: reverse entire array
        Reverse(arr, 0, k - 1);         // Step 2: reverse first k
        Reverse(arr, k, n - 1);         // Step 3: reverse rest
    }

    static void PrintArray(int[] arr)
    {
        foreach (var num in arr)
            Console.Write(num + " ");
        Console.WriteLine();
    }

    static void Main()
    {
        int[] arr1 = { 1, 2, 3, 4, 5, 6, 7 };

        Console.WriteLine("Original Array:");
        PrintArray(arr1);

        LeftRotate(arr1, 2);  // Rotate left by 2
        Console.WriteLine("After Left Rotate by 2:");
        PrintArray(arr1);

        RightRotate(arr1, 2); // Rotate right by 2 (brings back original)
        Console.WriteLine("After Right Rotate by 2:");
        PrintArray(arr1);
    }
}

Using Iteration Method
-------------------------

using System;

class Program
{
    static string LeftRotate(int[] arr, int k)
    {
        int n = arr.Length;
        k = k % n;  // Handle k > n
        int[] rotated = new int[n];

        // Copy into new rotated array
        for (int i = 0; i < n; i++)
        {
            rotated[i] = arr[(i + k) % n]; // shift left
        }

        return string.Join(" ", rotated);
    }

    static string RightRotate(int[] arr, int k)
    {
        int n = arr.Length;
        k = k % n;
        int[] rotated = new int[n];

        for (int i = 0; i < n; i++)
        {
            rotated[(i + k) % n] = arr[i]; // shift right
        }

        return string.Join(" ", rotated);
    }

    static void Main()
    {
        int[] arr = { 1, 2, 3, 4, 5 };

        Console.WriteLine("Original: " + string.Join(" ", arr));

        string leftRotated = LeftRotate(arr, 2);
        Console.WriteLine("Left Rotate by 2: " + leftRotated);

        string rightRotated = RightRotate(arr, 2);
        Console.WriteLine("Right Rotate by 2: " + rightRotated);
    }
}


Find the Length ,Sum and Longest subarray in the given array without repeatative
----------------------------------------------------------------------------------


using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        int[] arr = { 1, 2, 3, 1, 2, 9, 5, 7, 4, 8, 3 };
        LongestUniqueSubarray(arr);
    }

    static void LongestUniqueSubarray(int[] arr)
    {
        var set = new SortedSet<int>();
        int left = 0;
        int sum = 0;
        int maxLength = 0;


        for (int right = 0; right < arr.Length; right++)
        {
            while (set.Contains(arr[right]))
            {
                set.Remove(arr[left]);
                left++;
            }

            set.Add(arr[right]);
 
            maxLength = Math.Max(maxLength, right - left + 1);
        }
        int n = set.Count;
        int[] result = new int[n];
        foreach (var item in set)
        {
            sum += item;
        }


        Console.WriteLine("substring values are " + string.Join(", ", set));
        Console.WriteLine("Sum of substring is " + sum);
        Console.WriteLine("Length of substring is " + maxLength);

    }


}


Reverse a word in a sentence
-----------------------------

class Program
{
    static void Main()
    {
        string value = "Manoj is the SE at Aurigo";
        foreach(var item in value.Split(' '))
        {
            ReverseString(item);
        }
    }

    public static void ReverseString(string values)
    {
        for(int i =values.Length-1;i>=0;i--)
        {
            Console.Write(values[i]+"");
        }
        Console.Write(" ");
    }
}








```
