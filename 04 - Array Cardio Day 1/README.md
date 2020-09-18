# 04 - Array Cardio Day 1

## Achievement

This part is mainly to help you familiar with several basic methods of `Array`. There are two iterative methods (filter and map) defined by Es5. These iterative methods have only one feature: run a given function for each item of the array, but have different results according to the different iteration methods used.

The document provides an `inventor` array for initial operation. Based on this array, you can practice various methods of array. Please open HTML and view the output results in the console.




## Console

We often use `console.log()` as output in console. However, there is an amazing way to output a table:

```js
console.table(table name)
```

![avatar](https://s1.ax1x.com/2020/09/15/wyJ2PH.png)



## Process guidance

1. Filter 16 century born inventors 
2. Show their last names and first names 
3. Sort them by date of birth 
4. Calculate how old all the inventors have lived in total 
5. Sort them by how long they have lived 
6. Filter out a title that contains a word in a web page 
7. Sort inventors by surname 
8. Count the number of items in the array




## Related knowledge

### [filter](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

Filtering operation is a bit like the `select` statement in SQL. Ouput the component array whose running result is true.

```js
const __fifteen = inventors.filter(function(inventor) {
  if (inventor.year >= 1500 && inventor.year < 1600 ) {
	  return true;
  } else {
      return false;
  }
});
console.table(__fifteen);
```

The arrow function has been mentioned previously. It can be simplified with following codes:

```js
const fifteen = inventors.filter(inventor =>(inventor.year >= 1500 && inventor.year < 1600));
console.table(fifteen);
```





### [map](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

Map: process each element in the array and return a new array with processed elements.

```js
// name in inventors
const fullNames = inventors.map(inventor => inventor.first + ' ' + inventor.last);
```




### [sort](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

By default, `Array.prototype.sort()` will sort the array in ascending order as a string (10 before 2), but sort can also take a function as an argument. Therefore, when sorting numbers, you need to set a comparison function yourself. Examples are as follows:

```js
const __ordered = inventors.sort((a, b) => (a > b) ? 1 : -1);
console.table(__ordered);
```


### Combine filter and map

```js
const cate = document.querySelectorAll('.subject-list h2 a');
  const book = links
			.map(link => link.title)
            .filter(title => title.includes('CSS'));
```

### [reduce](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

This is a method of merging arrays. It takes a function as an argument (this function can be understood as an accumulator). It will traverse all the elements in array, then calculate a final return value, which is the first parameter of the accumulator. Examples shown as follows:

```js
[0,1,2,3,4].reduce(function(previousValue, currentValue, index, array){
  return previousValue + currentValue;
});
```

We need to count the values of each elememts in a given array. We can use this method to store the static information into a new object in the accumulator, and finally return the static value.

```js
 const data = ['car', 'car', 'truck', 'truck', 'bike', 'walk', 'car', 'van', 'bike', 'walk', 'car', 'van', 'car', 'truck' ];
  const reduce = data.reduce( (obj, item) => {
	  if( !obj[item]  ) {
		  obj[item] = 0;
	  }
		  obj[item]++;
		  return obj;
  }, {});
  console.log(reduce);
  ```

