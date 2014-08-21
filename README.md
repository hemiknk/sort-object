# sort-object [![NPM version](https://badge.fury.io/js/sort-object.png)](http://badge.fury.io/js/sort-object)

> Sort the keys in an object.

## Install
#### Install with [npm](npmjs.org)

```bash
npm i sort-object --save
```

## Usage

```js
var sortObj = require('sort-object');
```

By default, the keys on an object will be sorted in descending order:

```js
console.log(sortObj({a: 1, c: 2, b: 3}));
//=> {a: 1, b: 3, c: 2}
```

The second param can be an object of `options` OR an array of `keys`:

**object**

```js
console.log(sortObj({a: 1, c: 2, b: 3}, {keys: ['a', 'b']}));
//=> {a: 1, b: 3}
```

**array**

```js
console.log(sortObj({a: 1, c: 2, b: 3}, ['a', 'c']));
//=> {a: 1, c: 2}
```

## Options

* `keys` {Array} The returned object will contain only the specified keys, in the same order.
* `sort` {Function} Sort function to sort the keys using JavaScript's `.sort()` method.
* `sortOrder` {String} Valid values are `desc` or `asc`, case insensitive.
* `sortBy` {String} Sort function that is passed the entire object, rather than just the keys - as with the `.sort()` method.

### options.keys

Create a new object with only the given keys.

```js
var o = {a: 1, c: 2, e: 5, d: 4, b: 3};
console.log(sortObj(o, {keys: ['a', 'b']}));

//=> {a: 1, b: 3}
```

### options.sort

Function to be passed to javascript's `.sort()` method:

```js
var o = {a: 1, c: 2, e: 5, d: 4, b: 3};
var obj = sortObj(o, {
  sort: function (a, b) {
    return a < b ? -1 : 1;
  }
});
console.log(obj);
//=> {a: 1, b: 3, c: 2, d: 4, e: 5}
```

### options.sortOrder

Valid values are `desc` or `asc`, case insensitive:

```js
var o = {a: 1, c: 2, e: 5, d: 4, b: 3};
console.log(sortObj(o, {sortOrder: 'ASC'}));
//=> {e: 5, d: 4, c: 3, b: 2, a: 1}
```

### options.sortBy

Function that returns an array of keys to sort by:

```js
var old = {one: 'aa', two: 'bc', three: 'ab'};
var o = sortObj(old, {
  sortBy: function (obj) {
    var arr = [];
    Object.keys(obj).filter(function(key) {
      if (/^a/.test(obj[key])) arr.push(key);
    });
    return arr.reverse();
  }
});
//=> {three: 'ab', one: 'aa'}
```

## Author

**Brian Woodward**
 
+ [github/doowb](https://github.com/doowb)
+ [twitter/doowb](http://twitter.com/doowb) 

## License
Copyright (c) 2014 Brian Woodward, contributors.  
Released under the MIT license

***

_This file was generated by [verb-cli](https://github.com/assemble/verb-cli) on August 21, 2014._