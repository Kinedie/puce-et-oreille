# PHP8 new features

## Typing
### Mixed
Values can be : integers, strings, booleans, floats, arrays, callables, resources, objects, or null.
With PHP8, functions can return `mixed` values, ie any available type AND null.
It can't be nullable / nulled (triggers Fatal Error).

`public function queFaireCeSoir(): mixed`

`{`

`  $plan = '';`
  
`  if ('' === $this->meteo){`

`    $plan = 'rester au lit';`

`  } else {`

`    $plan = 2;`

`  };`
  
`  return $plan;`

`  }`


### Union Type
