# Javascript


## Console

```javascript
// see list of available methods
console.log(console);

// assert a boolean and only log if true
console.assert(bool, 'user not logged in');

// add braces to vars to show labels
console.log({foo, bar});

// show a table instead of just labels
console.table({foo, bar})

// goup things together with a label
console.groupCollapsed('does not work');

// but obj in a drop down
console.dir(obj);

// increment a counter
console.count('clicks');

// start and log a timer
console.time();
//...do some things
console.timeLog();

// show a stack trace
console.trace('stack trace')

// add CSS styling
console.log('%c Javascript is beautiful', 'color:pink; font-weight: bold;');
```

## Other
airbnb style guide
https://github.com/airbnb/javascript