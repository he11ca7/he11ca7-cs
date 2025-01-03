# Функция
Общая форма объявления функции `func` состоит из имени, списка аргументов, списка возвращаемых значений и тела функции:
```go
func name(parameter-list) (result-list) {
	body
}
```

Аргументы функций и результат функции являются локальными переменными. 

Однотипные аргументы могут быть перечислены через запятую.

Список возвращаемых значений может отсутствовать или состоять из одного - в таком случае заключение в скобки необязательно. Переменные списка возвращаемых значений могут быть именованными. В таком случае после `return` не требуется их перечисление.

Примеры:
```go
func AverageAndDiff(a float32, b float32) (avg float32, diff float32) {
	avg = (a + b) / 2
	diff = a - b
	return // <=> return avg, diff
}
func JustPrintNoReturn() {
	println("Hi!")
}
func SumTwo(a, b int) int {

	return a + b
}
var Print = JustPrintNoReturn()
```

# Анонимная функция
Анонимные функции не имеют имени и должны быть вызваны в месте определения:
```go
x, y := func(a, b int) (int, int) {
	return a*a, b+1
}(3, 4)
func() {
	println("x*x + y*y =", x*x + y*y)
}()
```