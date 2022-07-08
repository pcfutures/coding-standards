# PC Futures Coding Standards

## Examples are written in PHP, but should be followed for all relevant languages

### Import statements should be grouped by location & type

Groups include and should be in the following order:

1. Third party modules (vendor/node_modules)
2. Absolute imports
3. Relative imports
4. Aliased imports

:x: Incorrect:

```php
use Illuminate\Database\Eloquent\Relations\BelongsToMany;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Support\Collection;
use App\Models\Traits\SoftDeletes\SoftDeletes;
use ReflectionMethod;
use Illuminate\Database\Eloquent\Relations\MorphToMany;
use ReflectionClass;
use Carbon\Carbon;
use App\Models\HistoryPivotChangeAttribute;
use App\Models\History;
use Auth;
```

:heavy_check_mark: Correct:

```php
use Illuminate\Database\Eloquent\Relations\BelongsToMany;
use Illuminate\Database\Eloquent\Relations\MorphToMany;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Support\Collection;

use App\Models\Traits\SoftDeletes\SoftDeletes;
use App\Models\HistoryPivotChangeAttribute;
use App\Models\History;

use ReflectionMethod;
use ReflectionClass;
use Carbon\Carbon;
use Auth;
```

### Import statements should be ordered by length in descending order:

:x: Incorrect:

```php
use Illuminate\Database\Eloquent\Relations\BelongsToMany;
use Illuminate\Database\Eloquent\Relations\MorphMany;
use Illuminate\Database\Eloquent\Relations\MorphToMany;
```

:heavy_check_mark: Correct:

```php
use Illuminate\Database\Eloquent\Relations\BelongsToMany;
use Illuminate\Database\Eloquent\Relations\MorphToMany;
use Illuminate\Database\Eloquent\Relations\MorphMany;
```

### Code should be indented by 4 spaces

:x: Incorrect:

```php
function add(int $x, int $y): int {
  return $x + $y;
}
```

:heavy_check_mark: Correct:

```php
function add(int $x, int $y): int {
    return $x + $y;
}
```

### Curly brackets should appear on the same line as statements

:x: Incorrect:

```php
function add(int $x, int $y): int
{
    return $x + $y;
}
```

:heavy_check_mark: Correct:

```php
function add(int $x, int $y): int {
    return $x + $y;
}
```

### Line breaks should be used to separate functionality differences

:x: Incorrect:

```php
function add(int $x, int $y): int {
    $result = $x + $y;
    return $result;
}
function subtract(int $x, int $y): int {
    $result = $x - $y;
    return $result;
}
```

:heavy_check_mark: Correct:

```php
function add(int $x, int $y): int {
    $result = $x + $y;

    return $result;
}

function subtract(int $x, int $y): int {
    $result = $x - $y;

    return $result;
}
```

### Variables and functions should be typed

:x: Incorrect:

```php
function add($x, $y) {
    return $x + $y;
}
```

:heavy_check_mark: Correct:

```php
function add(int $x, int $y): int {
    return $x + $y;
}
```

### Single quotes should be preferred over double quotes

:x: Incorrect:

```php
function appendGreeting(string $name): string {
    return "Hey there, " . $name;
}
```

:heavy_check_mark: Correct:

```php
function appendGreeting(string $name): string {
    return 'Hey there, ' . $name;
}
```

### Spaces should be used to separate words and symbols

:x: Incorrect:

```php
$str='hello'+'world';
```

:heavy_check_mark: Correct:

```php
$str = 'hello' + 'world';
```

### Math operators should ONLY be used for mathematical operations

:x: Incorrect:

```php
$arr = ['hello'] + ['world'];

$str = 'hello' + 'world';
```

:heavy_check_mark: Correct:

```php
$arr = array_merge(['hello'], ['world']);

$str = 'hello' . 'world';
```

### Inline if statements are ONLY allowed if they're used as Guard Clauses

:x: Incorrect:

```php
function validate(mixed $x): bool {
    if (is_null($x)) return false;
    elseif (is_string($x) return false;
    else return true;
}
```

:heavy_check_mark: Correct:

```php
function validate(mixed $x): bool {
    if (is_null($x)) return false;
    if (is_string($x)) return false;

    return true;
}
```

### Variables, keys and functions should be camelCased

:x: Incorrect:

```php
function validate_a_variable(mixed $the_value): bool {
    $is_valid = true;

    if (is_string($the_value)) {
        $is_valid = false;
    };

    return $is_valid;
}
```

:heavy_check_mark: Correct:

```php
function validateAVariable(mixed $theValue): bool {
    $isValid = false;

    if (is_string($theValue)) {
        $isValid = true;
    };

    return $isValid;
}
```

### Global constants should be used instead of magic numbers

:x: Incorrect:

```php
function calculateCircumference(float $radius): float {
    return 2 * 3.141592654 * $radius;
}
```

:heavy_check_mark: Correct:

```php
const PI = 3.141592654;

function calculateCircumference(float $radius): float {
    return 2 * PI * $radius;
}
```

### Global constants should be CAPS_CASE

:x: Incorrect:

```php
const pi = 3.141592654;

function calculateCircumference(float $radius): float {
    return 2 * pi * $radius;
}
```

:heavy_check_mark: Correct:

```php
const PI = 3.141592654;

function calculateCircumference(float $radius): float {
    return 2 * PI * $radius;
}
```

### SQL column names should be snake_cased

:x: Incorrect:

```php
$table->string('firstName');
```

:heavy_check_mark: Correct:

```php
$table->string('first_name');
```

### Secret values (passwords, salts, encryption keys) should NEVER be committed to GitHub and should be stored in an environment (.env) file

:x: Incorrect:

```php
$secret = 'secret_value';
```

:heavy_check_mark: Correct:

```php
$secret = config('app.secret_value');
```
