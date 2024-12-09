# Тип
Общая форма объявления типа `type` состоит из имени и подлежащего типа:
```go
type name underlying_type
```

Возможно объединение объявлений.

Тип и его подлежащий тип являются принципиально разными типами. Для типов с одним и тем же подлежащим типом недоступны арифметические и логические операции без явного приведения типов.
```go
type Celsius float64  
type Fahrenheit float64  
  
func main()  {  
    var cel Celsius = 10
    var fah Fahrenheit = Fahrenheit(cel*9/5 + 32)
}
```

Приведение одного типа к другому не меняет значение переменной в памяти и его представление; делает изменение смысла (типа) явным.

```go
type (
	MyInt int
	Age   int
	Text  string
)

type IntPtr *int
type Book struct{author, title string; pages int}
type Convert func(in0 int, in1 bool)(out0 int, out1 string)
type StringArray [5]string
type StringSlice []string

func f() {
	type PersonAge map[string]int
	type MessageQueue chan string
	type Reader interface{Read([]byte) int}
}
```

См. [[002 struct|struct]].
# Псевдоним типа
Общая форма объявления псевдонима (алиаса) типа `type` состоит из имени и подлежащего типа:
```go
type name = underlying_type
```

В отличие от типов, алиас типа не создаёт отдельный тип, а лишь вводит его альтернативное название.

Возможно объединение объявлений.