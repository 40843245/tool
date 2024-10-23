# template tags
## repeat
### syntax
```
repeat(min?,max?)
```
### intro
It can be only used in the array.

It repeats the second argument within the array. 

The second argument within the array can be a json object. 

The first argument in repeat invocation -- `min` represents the minimum time (exclusive) it will repeat.

The second argument in repeat invocation -- `max` represents the minimum time (inclusive) it will repeat.

```
min < x <= max

where x is the number of time it will repeat.
```

> [!NOTE]
> A json object can be (but not limited to) a `string`, an `array`, a `map`.

In the repeat invocation, it supports an optional argument to specify a maximum number of times to repeat. 

Max value is 300.

Example Usage

```
repeat( )
```

```
repeat( 5)
```

```
repeat( 1, 5)
```

> [!CAUTION]
> Be aware of argument one passed. There are no exception or error when argument is invalid. 
> 
> It handles the argument in the following way.
>
> 1. In repeat invocation, if the first argument is greater than or equal to. It will swap. Considering first argument before swapping as the argument named `max` and second argument before swapping as the argument named `min`. (See example 3)
> 2. If the `max` argument is nonpostive (i.e. zero or negative) it will generate an empty array (i.e with zero elements). (See example 3, example 4, example 7 and example 9)
> 3. If there are exactly one argument passed, the passed argument will be considered as `max` argument. (See example 5)
> 4. If there are no argument passed, it will always generate the second element in array from zero to many times. (See example 10)


### examples
#### example1
##### code

```
{
  "result": [
    "repeat(3,10)",
    "2"
  ]
}
```

##### output
The output may be

```
{
  "result": [
    "2",
    "2",
    "2"
  ]
}
```

or

```
{
  "result": [
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2"
  ]
}
```

#### example 2
##### code
```
{
  "result": [
    "repeat(1,1)",
    "2"
  ]
}
```
##### output
The output may be

```
{
  "result": [
    "2",
    "2"
  ]
}
```

#### example 3
##### code
```
{
  "result": [
    "repeat(1,0)",
    "2"
  ]
}
```
##### output
The output may be

```
{
  "result": [
    "2"
  ]
}
```

#### example 4
##### code
```
{
  "result": [
    "repeat(0,0)",
    "2"
  ]
}
```

##### output
The output may be

```
{
  "result": []
}
```

#### example 5
The following code will generate json data which `result` key has exactly three elements. 

##### code
```
{
  "result": [
    "repeat(3)",
    {
      "name": {
        "first": "firstName()",
        "middle": "middleName()",
        "last": "lastName()"
      }
    }
  ]
}
```

##### output
The output may be

```
{
  "result": [
    {
      "name": {
        "first": "Giles",
        "middle": "Hayden",
        "last": "VonRueden"
      }
    },
    {
      "name": {
        "first": "Johnathon",
        "middle": "Kai",
        "last": "Gerhold"
      }
    },
    {
      "name": {
        "first": "Megane",
        "middle": "Drew",
        "last": "Hagenes"
      }
    }
  ]
}
```

#### example 6
##### code
```
{
  "result": [
    "repeat(3)",
    "2"
  ]
}
```

##### output
The output may be 

```
{
  "result": [
    "2",
    "2",
    "2"
  ]
}
```

#### example 7
##### code
```
{
  "result": [
    "repeat(-1)",
    "2"
  ]
}
```
##### output
```
{
  "result": []
}
```

#### example 8
##### code
```
{
  "result": [
    "repeat(-1,9)",
    "2"
  ]
}
```

#### output
The output may be

```
{
  "result": []
}
```

#### example 9
##### code
```
{
  "result": [
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2"
  ]
}
```

##### output
The output may be

```
{
  "result": [
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2"
  ]
}
```

or

```
{
  "result": [
    "2"
  ]
}
```

#### example 10
##### code
```
{
  "result": [
    "repeat()",
    "2"
  ]
}
```

##### output
The output may be

```
{
  "result": [
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2"
  ]
}
```

or

```
{
  "result": [
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2"
  ]
}
```

or

```
{
  "result": [
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2",
    "2"
  ]
}
```