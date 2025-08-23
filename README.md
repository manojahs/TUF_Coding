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

















```
