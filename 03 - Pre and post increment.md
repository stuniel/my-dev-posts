## While loop

### Syntax

```
while (condition)
  statement
```

### Examples:

#### Inside condition

```js
let i = 0

while (i < 3) {
  console.log(i)
  i++
}
// 0
// 1
// 2
```
Using pre-increment operator inside condition:

```js
let i = -1

while (++i < 3) {
  console.log(i)
}
// 0
// 1
// 2
```
