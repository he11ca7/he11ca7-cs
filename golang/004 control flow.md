# if-else
Общая форма объявления `if-else`:
```go
if InitStatement; Condition {
} else {
}
```
`InitStatement` опционален:
```go
if n := rand.Int(); n%2 == 0 {
	fmt.Println(n, "is an even number.")
} else {
	fmt.Println(n, "is an odd number.")
}

n := rand.Int() % 2 // this n is not the above n
if n % 2 == 0 {
	fmt.Println("An even number.")
}
```
# for
Общая форма объявления `for`:
```go
for InitStatement; Condition; PostStatement {
}
```

Инициализация `InitStatement` выполняется единожды перед запуском цикла.

Условное выражение `Condition` вычисляется перед каждой итерацией.

Последействие `PostStatement` выполняется в конце каждой итерации.

```go
// for-loop
sum := 0
for i := 1; i < 4; i++ {
	sum += i
}
fmt.Println(sum) // 6

// "while-loop"
sum := 1
for sum < 10 {
	sum += sum
}
fmt.Println(sum) // 16

// forever-loop
for {
	fmt.Println("lol")
	break
}
```

>[!WARNING]
>Начиная с Go 1.22, переменная цикла обладает областью видимости итерации вместо области видимости всего цикла.

`continue` прерывает итерацию.
`break` прерывает цикл.

# for-range
Цикл `for-range` применяется для обхода целых чисел, контейнеров и каналов.

Для целых чисел:
```go
// for i := 0; i < anInteger; i++ {}
for i := range anInteger {
}

// for i = 0; i < anInteger; i++ {}
for i = range anInteger {
}
```
# switch-case
Общая форма объявления `switch-case`:
```go
switch InitStatement; CompareOperand {
case CompareOperandList1:
case CompareOperandList2:
...
case CompareOperandListN:
default:
}
```

Выражение переключателя `CompareOperand` должно быть неявно преобразуемо в тип выражений случаев `CompareOperandListN`. Выражения случаев вычисляются сверху-вниз и слева-направо; обход прекращается в случае равенства выражения случая выражению переключателя. Блок `default` может быть объявлен в любой части `switch`.

В случае отсутствия `CompareOperand`, он интерпретируется как `true`.
`InitStatement` опционален.

Выполняется только один `case`, после чего происходит выход из `switch`.
`break` необязателен для выхода из `case`, но может быть использован для прерывания всего `switch`.

`fallthrough` позволяет продолжить выполнение следующего за данным `case` без выхода из `switch`.

Пример:
```go
switch n := rand.Intn(100); n%9 {
case 0:
	fmt.Println(n, "is a multiple of 9.")
case 1, 2, 3:
	fmt.Println(n, "mod 9 is 1, 2 or 3.")
case 4, 5, 6:
	fmt.Println(n, "mod 9 is 4, 5 or 6.")
default:
	fmt.Println(n, "mod 9 is 7 or 8.")
}
```

# goto

`goto` выполняет переход потока выполнения к ярлыку по форме `LabelName:`.
Область видимости ярлыка ограничена лексическим блоком, в котором он объявлен.