ajsut (abidibo js unit testing)
===============================

This is a js library to perform unit testing

Provided tests:

- assertion
- group of assertions
- async group of assertions
- performance
- performance with mean and standard deviation

Usage
--------------------------------

Notice! Do not use async group test with assertions, because assertions (assert) are not queued, use tests instead.

Include the provided js and styles

```html
  <script src="ajsut.js" type="text/javascript"></script>   
  <link type="text/css" rel="stylesheet" href="style/ajsut.css" />
```

### Single assertion
```js
  ajsut.assert(condition, 'my condition description');
```

### Group of assertions

```js
ajsut.test('Testing a group of assertions', function() {
  ajsut.assert(window, 'window is defined');
  ajsut.assert(typeof window == 'object', 'window is an object')
})
```

### Group of asyncronous assertions
```js
ajsut.test('Group of async assertions', function() {
  ajsut.pause();
  setTimeout(function() {
    ajsut.assert(this === window , 'the context here is the window object');
    ajsut.assert(1 === 1, 'one is equal to one');
    ajsut.resume();
  }, 1000)
})
```

### Performance
The third parameter is the number of times the function has to be run

```js
ajsut.performance('test performance', function() {
  var d = document.createElement('div');
  return d;
}, 100000);
```

### Performance with mean and standard deviation
The third parameter is the number of times the function has to be run

```js
ajsut.meanPerformance('test performance', function() {
  var d = document.createElement('div');
  return d;
}, 100000);
```
