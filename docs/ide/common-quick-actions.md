---
title: Typowe szybkie akcje
description: Najpopularniejsze szybkie akcje dla języka C# i Visual Basic, w tym naprawianie błędnie napisanych słów kluczowych lub symboli, rozwiązywanie konfliktów scalania, usuwanie niezbędnych importów, generowanie typów, wprowadzanie zmiennych lokalnych itp.
ms.date: 03/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: db7a3a550f6bfc1250679eeefa0ba3ec6291eef0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585525"
---
# <a name="common-quick-actions"></a>Typowe szybkie akcje

Sekcje w tym temacie lista niektórych typowych **szybkich akcji,** które mają zastosowanie zarówno do kodu Języka C# i Visual Basic. Te akcje są *poprawki kodu* dla diagnostyki kompilatora lub wbudowanych [analizatorów platformy kompilatora .NET](../code-quality/roslyn-analyzers-overview.md) w programie Visual Studio.

## <a name="actions-that-fix-errors"></a>Akcje naprawiają błędy

Szybkie akcje w tej sekcji naprawić błędy w kodzie, które mogłyby spowodować kompilacji nie powiedzie się. Gdy szybkie akcje są dostępne, aby naprawić błąd w wierszu kodu, ikona, która jest wyświetlana na marginesie lub pod czerwoną falitwą, to żarówka z czerwonym "x".

![Ikona i menu błędu Szybkie akcje](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Poprawianie błędnie napisanego symbolu lub słowa kluczowego

Jeśli przypadkowo błędnie wpiszesz typ lub słowo kluczowe w programie Visual Studio, ta szybka akcja automatycznie poprawi go za Ciebie. Te elementy zostaną wyświetlone w menu żarówki jako **"Zmień "\<błędnie\<napisane słowo>' na ' poprawne słowo>'"**. Przykład:

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

| Identyfikator błędu | Odpowiednie języki |
| - | - |
| CS0103, BC30002 | C# i Visual Basic |

### <a name="resolve-git-merge-conflict"></a>Rozwiązywanie konfliktu scalania git

Te szybkie akcje umożliwiają rozwiązywanie konfliktów scalania git przez "podjęcie zmiany", co usuwa kod i znaczniki powodujące konflikt.

```csharp
// Before
private void MyMethod()
{
    if (false)
    {

    }
}

// Take changes from 'HEAD'

// After
private void MyMethod()
{
    if (true)
    {

    }
}
```

| Identyfikator błędu | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS8300, BC37284 | C# i Visual Basic | Visual Studio 2017 w wersji 15.3 i nowszej |

## <a name="actions-that-remove-unnecessary-code"></a>Akcje usuwane z niepotrzebnego kodu

### <a name="remove-unnecessary-usingsimports"></a>Usuwanie niepotrzebnych użycia/importów

Szybka akcja **Usuń niepotrzebne użycie/Importuje** wszystkie `using` nieużywane i `Import` dyrektywy dla bieżącego pliku. Po wybraniu tego elementu nieużywane importowanie obszaru nazw zostanie usunięte.

| Odpowiednie języki | Obsługiwana wersja |
| - | - |
| C# i Visual Basic | Visual Studio 2015 i nowsze |

### <a name="remove-unnecessary-cast"></a>Usuń niepotrzebne odlewane

Jeśli zostanie rzutować typ na inny typ, który nie wymaga rzutu, element **Usuń niepotrzebną szybką** akcję rzutuje, usuwa niepotrzebne rzuty.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0004 ( IDE0004 ) | C# i Visual Basic | Visual Studio 2015 i nowsze |

### <a name="remove-unused-variables"></a>Usuwanie nieużywanych zmiennych

Ta szybka akcja umożliwia usunięcie zmiennych, które zostały zadeklarowane, ale nigdy nie były używane w kodzie.

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# i Visual Basic | Visual Studio 2017 w wersji 15.3 i nowszej |

### <a name="remove-type-from-default-value-expression"></a>Usuwanie typu z domyślnego wyrażenia wartości

Ta szybka akcja usuwa typ wartości z domyślnego wyrażenia wartości i używa [domyślnego literału,](/dotnet/csharp/language-reference/operators/default#default-literal) gdy kompilator może wywnioskować typ wyrażenia.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0034 ( IDE0034 ) | C# 7.1+ | Visual Studio 2017 w wersji 15.3 i nowszej |

## <a name="actions-that-add-missing-code"></a>Akcje, które dodają brakujący kod

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Dodawanie użycia/importu dla typów w zestawach referencyjnych, pakietach NuGet lub innych typach w rozwiązaniu

Korzystanie z typów znajdujących się w innych projektach w rozwiązaniu spowoduje automatyczne wyświetlenie szybkiej akcji, jednak inne muszą być włączone na karcie **Narzędzia > opcje > C#** lub Podstawowe > **Zaawansowane:**

- Sugerowanie użycia/importu dla typów w złożeniach referencyjnych
- Sugerowanie użycia/importu dla typów w pakietach NuGet

Gdy jest włączona, jeśli używasz typu w obszarze nazw, który obecnie nie jest importowany, ale istnieje w zestawie odwołań lub pakiecie NuGet, zostanie utworzona dyrektywa using lub import.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

' After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

| Identyfikator diagnostyczny | Odpowiednie języki |
| - | - |
| CS0103, BC30451 | C# i Visual Basic|

### <a name="add-missing-casesdefault-caseboth"></a>Dodaj brakujące sprawy/przypadek domyślny/oba

Podczas tworzenia `switch` instrukcji w języku `Select Case` C#lub instrukcji w języku Visual Basic, można użyć akcji kodu, aby automatycznie dodać brakujące elementy sprawy, domyślną instrukcję case lub oba te elementy.

Należy wziąć pod uwagę następujące `switch` `Select Case` wyliczenie i puste lub instrukcji:

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

Użycie **funkcji Dodaj obie** szybkie działanie wypełnia brakujące przypadki i dodaje przypadek domyślny:

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0010 ( IDE0010 ) | C# i Visual Basic| Visual Studio 2017 w wersji 15.3 i nowszej |

### <a name="add-null-checks-for-parameters"></a>Dodawanie kontroli wartości null dla parametrów

Ta szybka akcja umożliwia dodanie zaewidencjonowania kodu, aby stwierdzić, czy parametr ma wartość null.

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

| Odpowiednie języki | Obsługiwana wersja |
| -------------------- | ---------------- |
| C# i Visual Basic| Visual Studio 2017 w wersji 15.3 i nowszej |

### <a name="add-argument-name"></a>Dodaj nazwę argumentu

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

| Odpowiednie języki | Obsługiwana wersja |
| -------------------- | ---------------- |
| C# i Visual Basic| Visual Studio 2017 w wersji 15.3 i nowszej |

### <a name="add-braces"></a>Dodawanie nawiasów klamrowych

Add nawiasy klamrowe Szybka akcja otacza `if` nawiasy klamrowe wokół instrukcji jednowierszowych.

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true)
{
    return "hello,world";
}
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 i nowsze |

### <a name="add-and-order-modifiers"></a>Modyfikatory dodawania i zamawiania

Te szybkie akcje pomagają organizować modyfikatory, umożliwiając sortowanie istniejących i dodawanie brakujących modyfikatorów ułatwień dostępu.

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```

```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# i Visual Basic| Visual Studio 2017 w wersji 15.5 i nowszej |
| IDE0040 ( IDE0040 ) | C# i Visual Basic| Visual Studio 2017 w wersji 15.5 i nowszej |

## <a name="code-transformations"></a>Przekształcenia kodu

### <a name="convert-if-construct-to-switch"></a>Konwertuj konstrukcję "if" na "switch"

Ta szybka akcja umożliwia konwertowanie konstrukcji **if-then-else** na konstrukcję **przełącznika.**

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

| Odpowiednie języki | Obsługiwana wersja |
| -------------------- | ---------------- |
| C# i Visual Basic| Visual Studio 2017 w wersji 15.3 i nowszej |

### <a name="convert-to-interpolated-string"></a>Konwersja na ciąg interpolowany

[Interpolowane ciągi](/dotnet/csharp/language-reference/keywords/interpolated-strings) są łatwym sposobem wyrażania ciągów ze zmiennymi osadzonymi, podobnymi do metody **[String.Format.](/dotnet/api/system.string.format#overloads)**  Ta szybka akcja rozpoznaje przypadki, w których ciągi są łączone lub przy użyciu **String.Format**i zmienia użycie na interpolowany ciąg.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

| Odpowiednie języki | Obsługiwana wersja |
| -------------------- | ---------------- |
| C# 6.0+ i Visual Basic 14+ | Visual Studio 2017 i nowsze |

### <a name="use-object-initializers"></a>Używanie inicjatorów obiektów

Ta szybka akcja umożliwia użycie [inicjatorów obiektów,](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) a nie wywoływanie konstruktora i posiadanie dodatkowych wierszy instrukcji przypisania.

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```

```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# i Visual Basic | Visual Studio 2017 i nowsze |

### <a name="use-collection-initializers"></a>Użyj inicjatorów kolekcji

Ta szybka akcja umożliwia użycie [inicjatorów kolekcji,](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) a nie wielu wywołań do `Add` metody klasy.

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```

```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# i Visual Basic | Visual Studio 2017 i nowsze |

### <a name="convert-auto-property-to-full-property"></a>Konwertowanie właściwości auto na pełną właściwość

Ta szybka akcja umożliwia konwersję właściwości auto do pełnej właściwości i odwrotnie.

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; }
}
```

```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property
```

| Odpowiednie języki | Obsługiwana wersja |
| -------------------- | ---------------- |
| C# i Visual Basic | Visual Studio 2017 w wersji 15.5 i nowszej |

### <a name="convert-block-body-to-expression-bodied-member"></a>Konwertowanie obiektu bloku na element członkowski zabudowany wyrażeniami

Ta szybka akcja umożliwia konwertowanie obiektów bloków na elementy członkowskie zabudowane wyrażeniami dla metod, konstruktorów, operatorów, właściwości, indeksatorów i akcesorów.

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 i nowsze |

### <a name="convert-anonymous-function-to-local-function"></a>Konwertowanie funkcji anonimowej na funkcję lokalną

Ta szybka akcja konwertuje funkcje anonimowe na funkcje lokalne.

```csharp
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}
```

### <a name="convert-referenceequals-to-is-null"></a>Konwertuj 'ReferenceEquals' na "jest null"

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0+ | Visual Studio 2017 w wersji 15.5 i nowszej |

Ta szybka akcja sugeruje użycie [dopasowywania wzorców,](/dotnet/csharp/pattern-matching) a nie ```ReferenceEquals``` szyku kodowania, jeśli to możliwe.

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0+ | Visual Studio 2017 w wersji 15. i później |

### <a name="introduce-pattern-matching"></a>Wprowadzanie dopasowywania wzorów

Ta szybka akcja sugeruje użycie [dopasowania wzorca](/dotnet/csharp/pattern-matching) z rzutowania i null kontroli w języku C#.

```csharp
// Before
if (o is int)
{
    var i = (int)o;
    ...
}

// Use pattern matching

// After
if (o is int i)
{
    ...
}
```

```csharp
// Before
var s = o as string;
if (s != null)
{
    ...
}

// Use pattern matching

// After
if (o is string s)
{
    ...
}
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0020 ( IDE0020 ) | C# 7.0+ | Visual Studio 2017 i nowsze |
| IDE0019 | C# 7.0+ | Visual Studio 2017 i nowsze |

### <a name="change-base-for-numeric-literals"></a>Zmień podstawę literałów liczbowych

Ta szybka akcja umożliwia konwertowanie literału liczbowego z jednego podstawowego systemu liczbowego na inny. Na przykład można zmienić liczbę na szesnastkową lub format binarny.

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```

```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

| Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| C# 7.0+ i Visual Basic 14+ | Visual Studio 2017 w wersji 15.3 i nowszej |

### <a name="insert-digit-separators-into-literals"></a>Wstawianie separatorów cyfr do literałów

Ta szybka akcja umożliwia dodawanie znaków separatora do wartości literału.

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```

```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

| Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| C# 7.0+ i Visual Basic 14+ | Visual Studio 2017 w wersji 15.3 i nowszej |

### <a name="use-explicit-tuple-names"></a>Używanie jawnych nazw krotek

Ta szybka akcja identyfikuje obszary, w których można użyć jawną nazwę krotki, a nie Item1, Item2 itp.

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```

```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0+ i Visual Basic 15+ | Visual Studio 2017 i nowsze |

### <a name="use-inferred-names"></a>Używanie wywnioskowane nazwy

Ta szybka akcja wskazuje, kiedy kod można uprościć, aby użyć wywnioskowanych nazw elementów członkowskich w typach anonimowych lub wywnioskować nazwy elementów w krotek.

```csharp
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```

```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | Visual Studio 2017 w wersji 15.5 i nowszej |
| IDE0037 | C# 7.1+ | Visual Studio 2017 w wersji 15.5 i nowszej |

### <a name="deconstruct-tuple-declaration"></a>Deklaracja zdekonstrukcji krotki

Ta szybka akcja umożliwia dekonstrukcję deklaracji zmiennych krotki.

```csharp
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

| Identyfikator diagnostyczny | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0042 ( IDE0042 ) | C# 7.0+ | Visual Studio 2017 w wersji 15.5 i nowszej |

### <a name="make-method-synchronous"></a>Spraw, aby metoda była synchroniczowa

W przypadku `async` `Async` korzystania z lub słowa kluczowego w metodzie, oczekuje się, że wewnątrz tej metody `await` lub `Await` słowa kluczowego jest również używany. Jednak jeśli tak nie jest, zostanie wyświetlona szybka akcja, która sprawia, `async` że `Async` metoda jest synchroniczowana, usuwając słowo kluczowe lub słowo kluczowe i zmieniając typ zwracany. Użyj opcji **Synchronicznie korzystać** z opcji Make method synchroniczne z menu Szybkie akcje.

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

| Identyfikator błędu | Odpowiednie języki |
| ------- | -------------------- |
| CS1998, BC42356 | C# i Visual Basic |

### <a name="make-method-asynchronous"></a>Spraw, aby metoda była asynchroniza

W przypadku `await` `Await` korzystania z lub słowa kluczowego wewnątrz metody, oczekuje `async` `Async` się, że metoda jest oznaczona lub słowa kluczowego. Jednak jeśli tak nie jest, zostanie wyświetlona szybka akcja, która sprawia, że metoda jest asynchroniczne. Użyj opcji **Zrób metodę/Funkcja asynchronicznie** z menu Szybkie akcje.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

| Identyfikator błędu | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS4032, BC37057 | C# i Visual Basic | Visual Studio 2017 i nowsze |

## <a name="see-also"></a>Zobacz też

- [Szybkie akcje](../ide/quick-actions.md)
