# strip-comments [![NPM version](https://badge.fury.io/js/strip-comments.svg)](http://badge.fury.io/js/strip-comments)


> Strip comments from code. Removes both line comments and/or block comments, with options to leave protected comments unharmed.

## Install
#### Install with [npm](npmjs.org):

```bash
npm i strip-comments --save-dev
```

## Run tests

```bash
npm test
```

## Usage

```js
var strip = require('strip-comments');
console.log(strip('Hey! // foo'));
//=> 'Hey !';
```

## API
### [strip](index.js#L28)

Strip all comments

* `str` **{String}**: file contents or string to strip.    
* `opts` **{Object}**: options are passed to `.block`, and `.line`    
* `returns` **{String}**: String without comments.  

**Example:**

```js
console.log(strip("foo // this is a comment\n/* me too */"));
//=> 'foo'
```


### [.block](index.js#L45)

Strip only block comments, optionally leaving protected comments (e.g. `/*!`) intact.

* `str` **{String}**: file content or string to strip to    
* `opts` **{Object}**: if `safe:true`, strip only comments that do not start with `/*!` or `/**!`    
* `returns` **{String}**: String without block comments.  

**Example:**

```js
console.log(strip("foo // this is a comment\n/* me too */"));
//=> 'foo // this is a comment\n'
```


### [.line](index.js#L66)

Strip only line comments

* `str` **{String}**: file content or string to strip to    
* `opts` **{Object}**: if `safe:true`, strip all that not starts with `//!`    
* `returns` **{String}**: String without line comments.  

**Example:**

```js
console.log(strip("foo /* me too */"));
//=> 'foo'
```


## CLI
> The CLI, yeah. For now not supports `safe:true` option.  
You can see CLI [tests](./test/test.js#L189), [fixture used](./test/fixtures/strip-comments.js), [actual](./test/actual) and [expected](./test/expected) output files `strip-comments-*.js`

### [stripComments](cli.js)

- `-i`|`--input` <filepath> input file
- `-o`|`--output` <filepath> output file
- `-s`|`--strip` [method] available values are "all", "block" and "line", default "all"

```bash
$ stripComments --input <filepath> --output <filepath> --strip [method]
$ stripComments --input index.js --output stripped.js --strip all
```

## Author

**Jon Schlinkert**
 
+ [github/jonschlinkert](https://github.com/jonschlinkert)
+ [twitter/jonschlinkert](http://twitter.com/jonschlinkert) 

## License
Copyright (c) 2014 Jon Schlinkert, contributors.  
Released under the MIT license

***

_This file was generated by [verb-cli](https://github.com/assemble/verb-cli) on September 02, 2014._