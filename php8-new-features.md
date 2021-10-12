# PHP8 new features

## Typing
### Mixed Values
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


### Union Types
We already can type-hint arrays of objects with different object types.
What if we could type-hint a function argument with different types ? What if we could do the same for return values ?
UNION TYPES allow to type-hint functions arguments and return values with two or more types.

`public function invitesALaSoiree(): array | string`

`{`

` ...`

` return $nomDeLaSeuleInviteeOuNomsDesInvitees;`

`}`


*The function can either return a string or an array*

UNION TYPES can be `null`. Actually, using `null` in a union type expression that contains another type is like using a question mark in front of the same type.
UNION TYPES can't work with `void` since it's not a return type.
