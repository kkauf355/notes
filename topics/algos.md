# Big-O notation
Describes the complexity of an algorithm in terms of time and space

## O(1) Constant Time
For all inputs to our algorithm there is only and will always be only one operation required
    E.x.
    Find an element of an array (arr[0])

## O(n) Linear
For all inputs to our algorithm there will be one operation per input
    E.x.
    Find a book in the library by checking every book
    For loop - sum all numbers in the array

## O(n^2) N squared
    E.x.
    Nested for loops

## O(log n) Log Time
As you loop your operations are halved
    E.x.
    Divide and concuer
    

# Useful Algorithms

## Gauss's Theorem O(1)
Summing function for a sorted, contiguous array of integers taht start with 1
n * (n + 1) / 2

## Dummy data

```javascript
let data = [
    { id: 1, name: "a" },
    { id: 2, name: "b" },
    { id: 3, name: "c" },
    { id: 4, name: "d" },
    { id: 5, name: "e" },
];
```

## Shuffle array

```javascript
function shuffleArray(array) {
    for (var i = array.length - 1; i > 0; i--) {
        var j = Math.floor(Math.random() * (i + 1));
        var temp = array[i];
        array[i] = array[j];
        array[j] = temp;
    }
    return array;
}

let shuffled = shuffleArray(data);
console.log(shuffled);
```

## Sort array

```javascript
// true desc, false asc
let dynamicSort = function (field, reverse, primer) {
    let key = primer
        ? function (x) {
              return primer(x[field]);
          }
        : function (x) {
              return x[field];
          };

    reverse = !reverse ? 1 : -1;

    return function (a, b) {
        return (a = key(a)), (b = key(b)), reverse * ((a > b) - (b > a));
    };
};

let sorted = data.sort(dynamicSort("id", false));
console.log(sorted);
```
