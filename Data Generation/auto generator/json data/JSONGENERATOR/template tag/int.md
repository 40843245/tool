# template tag
## int
### syntax
```
int(min?,max?)
```
### intro

It generates a random integer value.

It supports optional arguments to specify a range.

> [!CAUTION]
> Be aware of argument one passed. There are no exception or error when argument is invalid. 
> 
> It handles the argument in the following way.
>
> 1. In int invocation, if the first argument is greater than or equal to. It will swap. Considering first argument before swapping as the argument named `max` and second argument before swapping as the argument named `min`. (See example 2)
> 2. If there are exactly one argument passed, the passed argument will be considered as `max` argument, and it will always generate the integer given the passed argument. (See example 4)
> 3. If there are no argument passed, it will always generate an integer from `(-1)*2^(16-1)` to `*2^(16-1) -1` since the `Integer` type in computer science take 2 Bytes (= 16 bits). (See example 5)

### example 
#### example 1
```
{
  "result": "int(3,10)"
}
```
##### output
The output may be

```
{
  "result": "9"
}
```

or

```
{
  "result": "3"
}
```

#### example 2
##### code
```
{
  "result": "int(5,2)"
}
```

##### output
```
{
  "result": "4"
}
```

#### example 3
##### code
The output may be

```
{
  "result": "int(-3,2)"
}
```

##### output
The output may be

```
{
  "result": "-1"
}
```

#### example 4
##### code
```
{
  "result": "int(2)"
}
```

##### output
The output may be

```
{
  "result": "2"
}
```

#### example 5
##### code
```
{
  "result": "int()"
}
```

##### output 
The output may be

```
{
  "result": "-766105"
}
```

or

```
{
  "result": "-388814"
}
```

or 

```
{
  "result": "-256324"
}
```