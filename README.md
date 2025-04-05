Q1 =  how to find the second smallest value in array in javascript?

solution = Method 1: Using Sorting

function findSecondSmallest(arr) {
  const uniqueSorted = [...new Set(arr)].sort((a, b) => a - b);
  return uniqueSorted.length >= 2 ? uniqueSorted[1] : null;
}

console.log(findSecondSmallest([5, 1, 2, 1, 3])); // Output: 2

explaination - 
new Set(arr) removes duplicates.

.sort((a, b) => a - b) sorts in ascending order.

[1] gets the second element.


Method 2: Without Sorting (Efficient for large arrays)

function findSecondSmallest(arr) {
  let min = Infinity;
  let secondMin = Infinity;

  for (let num of arr) {
    if (num < min) {
      secondMin = min;
      min = num;
    } else if (num < secondMin && num !== min) {
      secondMin = num;
    }
  }

  return secondMin !== Infinity ? secondMin : null;
}

console.log(findSecondSmallest([5, 1, 2, 1, 3])); // Output: 2

explaination - 

This approach avoids sorting and works in O(n) time.

It handles duplicates and finds the second distinct smallest value.



 Method 3: Using Math.min + filter

 function findSecondSmallest(arr) {
  const min = Math.min(...arr);
  const filtered = arr.filter(num => num !== min);
  return filtered.length ? Math.min(...filtered) : null;
}

console.log(findSecondSmallest([5, 1, 2, 1, 3])); // Output: 2

explaination - 
First, we find the smallest using Math.min.

Then we filter out all occurrences of that smallest value.

Finally, we find the min of the remaining values.




Q - 2 Find the third smallest distinct number:

function findThirdSmallest(arr) {
  let min = Infinity;
  let secondMin = Infinity;
  let thirdMin = Infinity;

  for (let num of arr) {
    if (num < min) {
      thirdMin = secondMin;
      secondMin = min;
      min = num;
    } else if (num > min && num < secondMin) {
      thirdMin = secondMin;
      secondMin = num;
    } else if (num > secondMin && num < thirdMin) {
      thirdMin = num;
    }
  }

  return thirdMin !== Infinity ? thirdMin : null;
}

console.log(findThirdSmallest([5, 1, 2, 1, 3])); // Output: 3


explaination - 
What's happening here:
We track the smallest, second smallest, and third smallest distinct numbers.

We make sure not to treat duplicates as different values.

The conditions:

num < min → shift all three values down.

num > min && num < secondMin → shift secondMin to thirdMin.

num > secondMin && num < thirdMin → update thirdMin.




Q3-  how to find the second largest value in array?

Method 1: Without sorting (Efficient way)

function findSecondLargest(arr) {
  let max = -Infinity;
  let secondMax = -Infinity;

  for (let num of arr) {
    if (num > max) {
      secondMax = max;
      max = num;
    } else if (num < max && num > secondMax) {
      secondMax = num;
    }
  }

  return secondMax !== -Infinity ? secondMax : null;
}

console.log(findSecondLargest([5, 1, 2, 7, 3])); // Output: 5



Method 2: With sorting (Simpler, less efficient for big arrays)

function findSecondLargest(arr) {
  const uniqueSorted = [...new Set(arr)].sort((a, b) => b - a);
  return uniqueSorted.length >= 2 ? uniqueSorted[1] : null;
}

console.log(findSecondLargest([5, 1, 2, 7, 3])); // Output: 5


Method 3: Using Math.max and filter

function findSecondLargest(arr) {
  const max = Math.max(...arr);
  const filtered = arr.filter(num => num !== max);
  return filtered.length ? Math.max(...filtered) : null;
}

console.log(findSecondLargest([5, 1, 2, 7, 3])); // Output: 5


