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





















```
