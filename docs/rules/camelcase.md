# Require Camelcase (camelcase)

When it comes to naming variables, styleguides generally fall into one of two camps: camelcased (`variableName`) and underscores(`variable_name`). This rule focuses on using the camelcase approach. If your styleguide calls for camelcasing your variable names, then this rule is for you!

## Rule Details

This rule looks for any underscores (`_`) located within the source code. It ignores leading and trailing underscores and only checks those in the middle of a variable name. If ESLint decides that the variable is a constant (all uppercase), then no warning will be thrown. Otherwise, a warning will be thrown. This rule only flags definitions and assignments but not function calls.

### Options

This rule accepts a single options argument with the following defaults:

```js
{
    "rules": {
        "camelcase": [2, {"properties": "always"}]
    }
}
```

`Properties` can have the following values:

1. `always` is the default and checks all property names
2. `never` does not check property names at all

The following patterns are considered warnings:

```js
var my_favorite_color = "#112C85";

function do_something() {
    // ...
}

obj.do_something = function() {
    // ...
};

var obj = {
	my_pref: 1
};
```

The following patterns are considered okay and do not cause warnings:

```js
var myFavoriteColor   = "#112C85";
var _myFavoriteColor  = "#112C85";
var myFavoriteColor_  = "#112C85";
var MY_FAVORITE_COLOR = "#112C85";
var foo = bar.baz_boom;
var foo = { qux: bar.baz_boom };

obj.do_something();

/*eslint camelcase: [2, {properties: "never"}]*/
var obj = {
	my_pref: 1
};
```

## When Not To Use It

If you have established coding standards using a different naming convention (separating words with underscores), turn this rule off.
