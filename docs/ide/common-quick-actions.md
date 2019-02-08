---
title: Typowe szybkie akcje
ms.date: 03/28/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f6f8872fa9acb2ca79010a87168c629dcbc3ac6e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932940"
---
# <a name="common-quick-actions"></a>Typowe szybkie akcje

Sekcje w tym temacie listy niektóre typowe **szybkie akcje** które mają zastosowanie do kodu w językach C# i Visual Basic. Te akcje są *poprawki kodu* diagnostyki kompilatora lub wbudowane [analizatory platformie kompilatora .NET](../code-quality/roslyn-analyzers-overview.md) w programie Visual Studio.

## <a name="actions-that-fix-errors"></a>Akcje, które naprawić błędy

Szybkie akcje w tej sekcji naprawić błędy w kodzie, które mogłyby spowodować niepowodzenie kompilacji. Gdy szybkie akcje są dostępne naprawić błąd w wierszu kodu, ikony, który jest wyświetlany na marginesie lub poniżej czerwona fala jest ikona żarówki z czerwonym znakiem "x" na nim.

![Ikona błędu usługi szybkie akcje i menu](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Popraw błędnie symboli lub słowo kluczowe

W przypadku błędnego wpisania przypadkowo typu lub słowa kluczowego w programie Visual Studio, tej szybkiej akcji automatycznie skoryguje go dla Ciebie. Zostaną wyświetlone te elementy w menu żarówka w postaci **"Zmień"*błędnie napisane słowa*"to"*poprawić wyraz*"**. Na przykład:

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

| Identyfikator błędu | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS0103, BC30002 | C# i Visual Basic | Visual Studio 2015 Update 2 |

### <a name="resolve-git-merge-conflict"></a>Rozwiąż konflikt scalania w usłudze git

Te szybkie akcje umożliwiają rozwiązywanie konfliktów scalania git przez "Trwa zmianie", który usuwa kod powodujący konflikt i znaczników.

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

| Identyfikator błędu | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS8300, BC37284 | C# i Visual Basic | Visual Studio 2017 w wersji 15.3 |

## <a name="actions-that-remove-unnecessary-code"></a>Akcje, które usuń zbędny kod

### <a name="remove-unnecessary-usingsimports"></a>Usuń niepotrzebne użycia/Importy

**Usuń zbędne deklaracje Using/Importy** szybka akcja usuwa wszelkie niewykorzystane `using` i `Import` instrukcji dla bieżącego pliku. Po zaznaczeniu tego elementu są usuwane importowanej nieużywanych przestrzeni nazw.

| Właściwe języki | Obsługiwana wersja |
| -------------------- | ---------------- |
| C# i Visual Basic | Visual Studio 2015 RTW |

### <a name="remove-unnecessary-cast"></a>Usuń niepotrzebne rzutowanie

Jeśli rzutowanie typu na inny typ, który nie wymaga rzutowania **usuwanie niepotrzebnego rzutowania** szybka akcja elementu usuwa niepotrzebnego rzutowania.

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# i Visual Basic | Visual Studio 2015 RTW |

### <a name="remove-unused-variables"></a>Usuń nieużywane zmienne

To szybka akcja umożliwia usunięcie zmienne zadeklarowane, ale nigdy nie jest używana w kodzie.

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# i Visual Basic | Visual Studio 2017 w wersji 15.3 |

### <a name="remove-type-from-default-value-expression"></a>Usuwanie typu wyrażenie wartości domyślnej

To szybka akcja usuwa typ wartości z wyrażenie wartości domyślnej i używa [domyślnego literału](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) Kiedy kompilator może wywnioskować typ wyrażenia.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1+ | Visual Studio 2017 w wersji 15.3 |

## <a name="actions-that-add-missing-code"></a>Akcje, które należy dodać brakujące kod

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Dodaj dyrektywy Using/Import dla typów odwołań do zestawów, pakietów NuGet lub innych typów w rozwiązaniu

Przy użyciu typy i znajdują się w innych projektach w rozwiązaniu wyświetli szybka akcja automatycznie, ale inne muszą być włączone z **Narzędzia > Opcje > C#** lub **podstawowe > Zaawansowane** karty:

- Sugeruj dyrektywy Using/dyrektywy Import dla typów w zestawach referencyjnych
- Sugeruj dyrektywy Using/dyrektywy Import dla typów w pakietach NuGet

Po włączeniu, jeśli używasz typu w przestrzeni nazw, która obecnie nie jest zaimportowane, ale istnieje odwołanie do zestawu lub pakietu NuGet, instrukcji przy użyciu przełącznika/import zostanie utworzony.

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

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS0103, BC30451 | C# i Visual Basic| Visual Studio 2015 Update 2 |

### <a name="add-missing-casesdefault-caseboth"></a>Dodaj brakujące przypadki/domyślny zarówno case

Podczas tworzenia `switch` instrukcji w języku C# lub `Select Case` instrukcji w języku Visual Basic, akcji kodu można użyć do automatycznego dodawania brakujące elementy wielkości liter i/lub instrukcji case domyślne.

Należy wziąć pod uwagę następujące wyliczenie i puste `switch` lub `Select Case` instrukcji:

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

Za pomocą **dodać oba** szybka akcja wypełni brakujące przypadki i dodaje przypadek domyślny:

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# i Visual Basic| Visual Studio 2017 w wersji 15.3 |

### <a name="add-null-checks-for-parameters"></a>Dodaj sprawdzenia wartości null dla parametrów

To szybka akcja umożliwia dodawanie sprawdzenie w kodzie, aby sprawdzić, czy parametr ma wartość null.

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

| Właściwe języki | Obsługiwana wersja |
| -------------------- | ---------------- |
| C# i Visual Basic| Visual Studio 2017 w wersji 15.3 |

### <a name="add-argument-name"></a>Dodaj nazwę argumentu

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

| Właściwe języki | Obsługiwana wersja |
| -------------------- | ---------------- |
| C# i Visual Basic| Visual Studio 2017 w wersji 15.3 |

### <a name="add-braces"></a>Dodaj nawiasy klamrowe

Dodaj nawiasy klamrowe szybkie działanie otacza nawiasów klamrowych otaczających jednowierszowego `if` instrukcji.

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 RTW |

### <a name="add-and-order-modifiers"></a>Dodaj i kolejność modyfikatorów

Te szybkie akcje pomagają organizować modyfikatorów, dzięki któremu można sortować, istniejące oraz Dodaj brakujące modyfikatory dostępności.

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# i Visual Basic| Visual Studio 2017 w wersji 15.5 |
| IDE0040 | C# i Visual Basic| Visual Studio 2017 w wersji 15.5 |

## <a name="code-transformations"></a>Przekształcenia kodu

### <a name="convert-if-construct-to-switch"></a>Konstrukcja Konwertuj "if" na "switch"

To szybka akcja umożliwia konwertowanie **if-then-else** konstrukcji **Przełącz** konstruowania.

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

| Właściwe języki | Obsługiwana wersja |
| -------------------- | ---------------- |
| C# i Visual Basic| Visual Studio 2017 w wersji 15.3 |

### <a name="convert-to-interpolated-string"></a>Konwertuj na ciąg interpolowany

[Ciągi interpolowane](/dotnet/csharp/language-reference/keywords/interpolated-strings) to łatwy sposób express ciągi zawierające osadzone zmienne, podobnie jak **[String.Format](/dotnet/api/system.string.format#overloads)** metody.  Rozpoznaje, przypadki, gdzie ciągi są połączone lub przy użyciu tej szybkiej akcji **String.Format**oraz zmian użycie w ciągu interpolowanym.

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

| Właściwe języki | Obsługiwana wersja |
| -------------------- | ---------------- |
| C# 6.0 + i Visual Basic 14 + | Visual Studio 2017 RTW |

### <a name="use-object-initializers"></a>Użyj inicjatorów obiektów

To szybka akcja umożliwia użycie [inicjatorach obiektów](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) zamiast wywoływania konstruktora i masz dodatkowe wiersze instrukcji przypisania.

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# i Visual Basic | Visual Studio 2017 RTW |

### <a name="use-collection-initializers"></a>Użyj inicjatory kolekcji

To szybka akcja umożliwia korzystanie z [inicjatory kolekcji](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) zamiast wielu wywołań `Add` metody klasy.

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# i Visual Basic | Visual Studio 2017 RTW |

### <a name="convert-auto-property-to-full-property"></a>Konwertuj właściwości automatycznej na pełną właściwość

To szybka akcja umożliwia konwertowanie właściwości automatycznej na pełną właściwość i na odwrót.

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

| Właściwe języki | Obsługiwana wersja |
| -------------------- | ---------------- |
| C# i Visual Basic | Visual Studio 2017 w wersji 15.5 |

### <a name="convert-block-body-to-expression-bodied-member"></a>Konwertuj treści bloku do elementu członkowskiego z wyrażeniem w treści

To szybka akcja umożliwia konwertowanie treści bloku na składniki wyrażeniem w treści metody, konstruktory, operatory, właściwości, indeksatory i metod dostępu.

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 RTW |

### <a name="convert-anonymous-function-to-local-function"></a>Konwertuj funkcję anonimowych do funkcji lokalnej

Funkcje lokalne tej szybkiej akcji konwertuje funkcjami anonimowymi.

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

### <a name="convert-referenceequals-to-is-null"></a>Konwertuj "ReferenceEquals" na "is null"

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0+ | Visual Studio 2017 w wersji 15.5 |

Tej szybkiej akcji sugeruje użycie [dopasowywania do wzorca](/dotnet/csharp/pattern-matching) zamiast ```ReferenceEquals``` kodowania wzorzec, gdzie to możliwe.

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0+ | Visual Studio 2017 w wersji 15.5 |

### <a name="introduce-pattern-matching"></a>Wprowadzenie dopasowywania do wzorca

Tej szybkiej akcji sugeruje użycie [dopasowywania do wzorca](/dotnet/csharp/pattern-matching) rzutowania i sprawdzanie wartości null w języku C#.

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0020 | C# 7.0+ | Visual Studio 2017 RTW |
| IDE0019 | C# 7.0+ | Visual Studio 2017 RTW |

### <a name="change-base-for-numeric-literals"></a>Podstawa zmiany w literałach numerycznych

To szybka akcja umożliwia Konwertuj literał liczbowy z jednego systemu liczbowego podstawowego na inny. Na przykład użytkownik może zmienić numer szesnastkowym lub format binarny.

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

| Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| C# 7.0 + i Visual Basic 14 + | Visual Studio 2017 w wersji 15.3 |

### <a name="insert-digit-separators-into-literals"></a>Wstawianie separatory cyfr literałów

To szybka akcja umożliwia dodawanie znaki separatora w wartości literału.

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

| Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| C# 7.0 + i Visual Basic 14 + | Visual Studio 2017 w wersji 15.3 |

### <a name="use-explicit-tuple-names"></a>Używanie jawnych nazw krotek

Tej szybkiej akcji identyfikuje obszary, w którym można jawną nazwę krotki zamiast item1 — item2 —, itp.

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0 + i Visual Basic 15 + | Visual Studio 2017 RTW |

### <a name="use-inferred-names"></a>Użyj nazwy wywnioskowanego

Tej szybkiej akcji wykazuje, gdy kod może być uproszczone do użycia wywnioskowane nazwy elementów członkowskich typów anonimowych lub wywnioskowane nazwy elementów w spójnych kolekcjach.

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | Visual Studio 2017 v. 15.5 |
| IDE0037 | C# 7.1+ | Visual Studio 2017 v. 15.5 |

### <a name="deconstruct-tuple-declaration"></a>Dekonstruować krotki deklaracji

To szybka akcja umożliwia dekonstrukcja krotki deklaracje zmiennych.

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

| Identyfikator diagnostyczny | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0042 | C# 7.0+ | Visual Studio 2017 v. 15.5 |

### <a name="make-method-synchronous"></a>Oznaczanie metody synchroniczne

Korzystając z `async` lub `Async` — słowo kluczowe dla metody, można oczekiwać, że wewnątrz tej metody `await` lub `Await` — słowo kluczowe jest również używany. Jeśli jednak nie jest to przypadek, szybka akcja pojawia się, dzięki której metoda synchroniczna, usuwając `async` lub `Async` — słowo kluczowe i zmiany zwracanego typu. Użyj **oznaczanie synchroniczne metody** opcję z menu Szybkie akcje.

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

| Identyfikator błędu | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS1998, BC42356 | C# i Visual Basic | Visual Studio 2015 Update 2 |

### <a name="make-method-asynchronous"></a>Wprowadź metody asynchroniczne

Korzystając z `await` lub `Await` — słowo kluczowe w metodzie, oczekuje się, że metoda jest oznaczona atrybutem `async` lub `Async` — słowo kluczowe. Jednak jeśli nie jest to przypadek, szybka akcja wyświetlany jest sprawia, że metody asynchronicznej. Użyj **Ustaw metody/funkcję asynchroniczną** opcję z menu Szybkie akcje.

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

| Identyfikator błędu | Właściwe języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS4032, BC37057 | C# i Visual Basic | Visual Studio 2017 |

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje](../ide/quick-actions.md)
