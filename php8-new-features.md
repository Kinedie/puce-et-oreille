# PHP8 new features

## Typing
### Mixed Values
Values can be : integers, strings, booleans, floats, arrays, callables, resources, objects, or null.
With PHP8, functions can return `mixed` values, ie any available type AND null.
It can't be nullable / nulled (triggers Fatal Error).

```php
public function queFaireCesoir(): mixed
{
	$plan = '';

	if ('' === $this->meteo){
		$plan = 'rester au lit';
	} else {
		$plan = 2;
	}

	return $plan;
}
```

### Union Types
We already can type-hint arrays of objects with different object types.
What if we could type-hint a function argument with different types ? What if we could do the same for return values ?
UNION TYPES allow to type-hint functions arguments and return values with two or more types.

```php
public function invitesALaSoiree(): array | string
{
	...
	return $nomDeLaSeuleInviteeOuNomsDesInvitees;
}
```

*// The function can either return a string or an array*

UNION TYPES can be `null`. Actually, using `null` in a union type expression that contains another type is like using a question mark in front of the same type.
UNION TYPES can't work with `void` since it's not a return type.


### Stringable Interfaces
When a class defines a `__toString()` method, it automatically implements the STRINGABLE INTERFACE.
#### Using an object as a string
```php
class Pet
{
	public string $cuteName;

	public function __toString()
	{
		return $this->cuteName;
	}
}

function statePetName(string|Stringable $petName)
{
	return 'Hi, my name is - chika chika - ' . $petName;
}

$neighbourlyPuppy = new Pet();
$neighbourlyPuppy->cuteName = 'Gina';

$truc = statePetName($neighbourlyPuppy);

echo $truc;
```

*// returns 'Hi, my name is - chika chika - Gina' since $neighbourlyPuppy owns a* `__toString` *method / is Stringable*


## Syntax
### Nullsafe operator
If/else statements are at the core of programming.

A handful of comparison operators shorthands which run like If/else statements with subtleties  :
- Ternary operator
- "Elvis operator"
- Null coalescing operator
- Null coalescing assignment operator

#### The ternary operator shortens if/else statements.
```php
$catPowers = $minette->getWhiskersLength() ? $minette->displayCatPowers() : null;
```

#### The "Elvis operator" (introduced in PHP 5.3) is a ternary operator shorthand. It checks if the condition is true.
*// ELVIS OPERATOR checks if Minette's whiskersLength have been assigned a value*

```php
$minette->getWhiskersLength() ?: $minette->setWhiskersLength(10);
```

#### The Null coalescing operator
*// NULL COALESCING behaves like "isset" native method : is variable declared AND not null ?*

```php
$lengthOfWhiskers = $minette->getWhiskersLength() ?? 10;
```

#### Null coalescing assignment operator (introduced in PHP 7.4) assigns a value to a variable.
*// NULL COALESCING ASSIGNMENT OPERATOR checks if* `$features['fur']` *is assigned.*

*// if not, the fallback value will be assigned to* `$features['fur']`*.*

```php
$features['fur'] ??= 'brown';
```

#### New in PHP 8 : Null safe operator
PHP 8.0 introduces the new NULL SAFE OPERATOR. It's another comparison shorthand.
With the new NULL SAFE OPERATOR, we can apply the NULL COALESCING OPERATOR on methods.

```php
$minetteSLeftPawCuteName = $minette->getLeftPaw()?->getCuteNickname();
```

*// equals to* :`$minetteSLeftPaw ? $minetteSLeftPaw->getCuteNickname() : null;`

We can also chain the comparisons, as in `$awesomeHuman->account?->subreddit?->getTitle()`.


## OOP
### Constructor Property Promotion
In classes with constructors, properties definition is repetitive and increases work time.
Property Promotion solves this problem by  initializing the properties directly inside the Constructor.

```php
public function __construct
(
	public string $sender,
    public int $numberOfItems
) {}
```

It's a shorthand of the usual property / service initialization. The lightened constructor is parsed and transformed into the classical syntax before being compiled.


Another DX enhancement, Property Promotion is especially useful while coding Value Objects or DTOs (most of the classes in a project).
But its flexibility and its lightness increases the productivity in any given context.

#### While Promoted, Properties don't have to be type-hinted.
```php
public function __construct
(
	public string $sender,
	public $numberOfItems,
	public bool $isFull,
) {}
```

#### Mixed syntax is allowed
```php
public bool $isFull;

public function __construct
(
	public bool $isFull,
	public int $numberOfItems,
) {
	$this->isFull = $isFull;
}
```

#### It is still possible to assign a default value to a Propery while Promoted
```php
public function __construct
(
	public bool $isFull,
	public int $numberOfItems = 1,
) {}
```

#### Doc comments are supported and can be added within promoted properties
```php
public function __construct
(
	public bool $isFull,
	/** @var int */
	public $numberOfItems,
) {}
```

#### Attributes are supported too
```php
public bool $isFull

public function __construct
(
	#[LovListener]
	bool $isFull,
	public $numberOfItems = 1,
) {}
```



Properties **can't be promoted in Abstract classes constructors, nor Interfaces constructors.
But it is allowed in Traits**
