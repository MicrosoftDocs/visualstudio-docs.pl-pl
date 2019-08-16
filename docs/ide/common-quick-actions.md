---
title: Typowe szybkie akcje
description: Najpopularniejsze szybkie akcje dla C# i Visual Basic, w tym naprawianie słów kluczowych lub symboli mispelled, rozwiązywanie konfliktów scalania, usuwanie niezbędnych importów, generowanie typów, wprowadzenie zmiennych lokalnych itd.
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
ms.openlocfilehash: 2ceedf18b936c0b1e8553ceb3bb1fdbc75035dfa
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551441"
---
# <a name="common-quick-actions"></a>Typowe szybkie akcje

W sekcjach w tym temacie wymieniono niektóre typowe **szybkie akcje** , które mają zastosowanie zarówno C# do kodu, jak i Visual Basic. Te akcje są *poprawkami kodu* dla diagnostyki kompilatora lub wbudowanymi [analizatorami .NET compiler platform](../code-quality/roslyn-analyzers-overview.md) w programie Visual Studio.

## <a name="actions-that-fix-errors"></a>Akcje, które rozwiązują błędy

Szybkie akcje w tej sekcji rozwiązują błędy w kodzie, które mogłyby spowodować niepowodzenie kompilacji. Gdy szybkie akcje są dostępne w celu naprawienia błędu w wierszu kodu, ikona wyświetlana na marginesie lub pod czerwoną zygzakem to żarówka z czerwonym znakiem "x".

![Ikony i menu błędów szybkiej akcji](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Popraw błędny symbol lub słowo kluczowe

Jeśli przypadkowo omyłkowo popełniasz typ lub słowo kluczowe w programie Visual Studio, Ta szybka akcja automatycznie poprawi ją. Te elementy będą widoczne w menu żarówki jako **"Zmień" błędnie*napisane słowo*"na"*Popraw wyraz*** ". Na przykład:

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

| Identyfikator błędu | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS0103, BC30002 | C# i Visual Basic | Visual Studio 2015 Update 2 |

### <a name="resolve-git-merge-conflict"></a>Rozwiąż konflikt scalania git

Te szybkie akcje umożliwiają rozwiązywanie konfliktów scalania git przez "wprowadzenie zmiany", co powoduje usunięcie powodujących konflikt kodów i znaczników.

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
| CS8300, BC37284 | C# i Visual Basic | Visual Studio 2017 w wersji 15,3 |

## <a name="actions-that-remove-unnecessary-code"></a>Akcje, które usuwają zbędny kod

### <a name="remove-unnecessary-usingsimports"></a>Usuń niepotrzebne użycie/Importy

Szybka akcja **Usuń niepotrzebne użycie/Importy** usuwa wszystkie nieużywane `Import` `using` instrukcje i dla bieżącego pliku. Po wybraniu tego elementu nieużywane Importy przestrzeni nazw zostaną usunięte.

| Odpowiednie języki | Obsługiwana wersja |
| -------------------- | ---------------- |
| C# i Visual Basic | Visual Studio 2015 RTW |

### <a name="remove-unnecessary-cast"></a>Usuń niepotrzebne rzutowanie

W przypadku rzutowania typu na inny typ, który nie wymaga rzutowania, **usuwanie** niepotrzebnego elementu szybkiej akcji spowoduje usunięcie niepotrzebnego rzutowania.

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# i Visual Basic | Visual Studio 2015 RTW |

### <a name="remove-unused-variables"></a>Usuń nieużywane zmienne

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# i Visual Basic | Visual Studio 2017 w wersji 15,3 |

### <a name="remove-type-from-default-value-expression"></a>Usuń typ z wyrażenia wartości domyślnej

Ta szybka akcja usuwa typ wartości z wyrażenia wartości domyślnej i używa [literału domyślnego](/dotnet/csharp/language-reference/operators/default#default-literal) , gdy kompilator może wywnioskować typ wyrażenia.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1+ | Visual Studio 2017 w wersji 15,3 |

## <a name="actions-that-add-missing-code"></a>Akcje, które dodają brakujący kod

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Dodaj użycie/Importy dla typów w zestawach referencyjnych, pakietach NuGet lub innych typach w rozwiązaniu

Użycie typów znajdujących się w innych projektach w rozwiązaniu spowoduje automatyczne wyświetlenie szybkiej akcji, jednak inne muszą zostać włączone z poziomu **narzędzi > Opcje C# >** lub **Basic > Advanced** :

- Sugeruj użycie/Importy dla typów w zestawach odwołań
- Sugeruj użycie/Importy dla typów w pakietach NuGet

Jeśli jest włączone, w przypadku użycia typu w przestrzeni nazw, który nie jest obecnie importowany, ale istnieje w zestawie referencyjnym lub pakiecie NuGet, zostanie utworzona instrukcja using/import.

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS0103, BC30451 | C# i Visual Basic| Visual Studio 2015 Update 2 |

### <a name="add-missing-casesdefault-caseboth"></a>Dodaj brakujące przypadki/domyślne przypadki/oba

Podczas tworzenia `switch` instrukcji w C#, lub `Select Case` instrukcji w Visual Basic, można użyć akcji kodowej, aby automatycznie dodać brakujące elementy Case, domyślną instrukcję Case lub obie.

Weź pod uwagę następujące Wyliczenie i `switch` pustą `Select Case` instrukcję:

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

Za pomocą opcji **Dodaj obie** szybkie akcje w brakujących przypadkach i Dodaj przypadek domyślny:

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# i Visual Basic| Visual Studio 2017 w wersji 15,3 |

### <a name="add-null-checks-for-parameters"></a>Dodaj sprawdzanie wartości null dla parametrów

Ta szybka akcja umożliwia dodanie zaewidencjonowania kodu w celu stwierdzenia, czy parametr ma wartość null.

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
| C# i Visual Basic| Visual Studio 2017 w wersji 15,3 |

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
| C# i Visual Basic| Visual Studio 2017 w wersji 15,3 |

### <a name="add-braces"></a>Dodaj nawiasy klamrowe

Szybka akcja Dodaj nawiasy klamrowe zawija nawiasy klamrowe wokół instrukcji `if` jednowierszowych.

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 RTW |

### <a name="add-and-order-modifiers"></a>Modyfikatory dodawania i porządkowania

Te szybkie akcje pomagają organizować modyfikatory, umożliwiając sortowanie istniejących i Dodawanie brakujących modyfikatorów dostępności.

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# i Visual Basic| Visual Studio 2017 w wersji 15.5 |
| IDE0040 | C# i Visual Basic| Visual Studio 2017 w wersji 15.5 |

## <a name="code-transformations"></a>Przekształcenia kodu

### <a name="convert-if-construct-to-switch"></a>Konwertuj konstrukcję "If" na "switch"

Ta szybka akcja umożliwia konwersję konstrukcji **if-then-else** na konstrukcję **Switch** .

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
| C# i Visual Basic| Visual Studio 2017 w wersji 15,3 |

### <a name="convert-to-interpolated-string"></a>Konwertuj na ciąg interpolowany

[Ciągi interpolowane](/dotnet/csharp/language-reference/keywords/interpolated-strings) to prosty sposób wyrażenia ciągów z osadzonymi zmiennymi, podobnie jak Metoda **[String. format](/dotnet/api/system.string.format#overloads)** .  Ta szybka akcja rozpoznaje przypadki, w których ciągi są łączone lub używają **formatu String. format**, i zmienia użycie na ciąg interpolowany.

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
| C#6.0 + i Visual Basic 14 + | Visual Studio 2017 RTW |

### <a name="use-object-initializers"></a>Użyj inicjatorów obiektów

Ta szybka akcja umożliwia korzystanie z [inicjatorów obiektów](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) zamiast wywoływania konstruktora i posiadania dodatkowych wierszy instrukcji przypisania.

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# i Visual Basic | Visual Studio 2017 RTW |

### <a name="use-collection-initializers"></a>Korzystanie z inicjatorów kolekcji

Ta szybka akcja umożliwia korzystanie z [inicjatorów kolekcji](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) zamiast wielu wywołań `Add` metody klasy.

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# i Visual Basic | Visual Studio 2017 RTW |

### <a name="convert-auto-property-to-full-property"></a>Konwertuj Właściwość autoproperty na Właściwość pełna

Ta szybka akcja pozwala skonwertować Właściwość automatyczną na pełną Właściwość i na odwrót.

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
| C# i Visual Basic | Visual Studio 2017 w wersji 15.5 |

### <a name="convert-block-body-to-expression-bodied-member"></a>Konwertuj treść bloku na składowaną w postaci wyrażenia

Ta szybka akcja umożliwia konwertowanie treści bloków na składowe w postaci wyrażeń w przypadku metod, konstruktorów, operatorów, właściwości, indeksatorów i metod dostępu.

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 RTW |

### <a name="convert-anonymous-function-to-local-function"></a>Konwertuj funkcję anonimową na funkcję lokalną

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

### <a name="convert-referenceequals-to-is-null"></a>Konwertuj element "ReferenceEquals" na wartość "is null"

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0041 | C#7.0 + | Visual Studio 2017 w wersji 15.5 |

Ta szybka akcja sugeruje użycie [dopasowania wzorca](/dotnet/csharp/pattern-matching) zamiast ```ReferenceEquals``` wzorca kodowania, jeśli to możliwe.

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0039 | C#7.0 + | Visual Studio 2017 w wersji 15.5 |

### <a name="introduce-pattern-matching"></a>Wprowadź dopasowanie do wzorca

Ta szybka akcja sugeruje użycie [dopasowania wzorca](/dotnet/csharp/pattern-matching) z rzutowania i sprawdzaniem wartości null w C#.

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0020 | C#7.0 + | Visual Studio 2017 RTW |
| IDE0019 | C#7.0 + | Visual Studio 2017 RTW |

### <a name="change-base-for-numeric-literals"></a>Zmień bazę dla literałów liczbowych

Ta szybka akcja umożliwia konwertowanie literału liczbowego z jednego podstawowego systemu liczbowego na inny. Na przykład można zmienić liczbę na szesnastkową lub na format binarny.

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
| C#7.0 + i Visual Basic 14 + | Visual Studio 2017 w wersji 15,3 |

### <a name="insert-digit-separators-into-literals"></a>Wstawianie separatorów cyfr do literałów

Ta szybka akcja pozwala dodać znaki separatora do wartości literału.

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
| C#7.0 + i Visual Basic 14 + | Visual Studio 2017 w wersji 15,3 |

### <a name="use-explicit-tuple-names"></a>Użyj jawnych nazw krotek

Ta szybka akcja określa obszary, w których można używać jawnej nazwy krotki zamiast Item1 —, Item2 — itp.

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0033 | C#7.0 + i Visual Basic 15 + | Visual Studio 2017 RTW |

### <a name="use-inferred-names"></a>Użyj nazw wywnioskowanych

Ta szybka akcja wskazuje, kiedy można uprościć kod, aby używać wywnioskowanych nazw elementów członkowskich w typach anonimowych lub wnioskowania nazw elementów w spójnych kolekcjach.

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | Visual Studio 2017 v. 15.5 |
| IDE0037 | C# 7.1+ | Visual Studio 2017 v. 15.5 |

### <a name="deconstruct-tuple-declaration"></a>Dekonstrukcja deklaracji krotki

Ta szybka akcja umożliwia rozbudowę deklaracji zmiennych krotki.

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

| Identyfikator diagnostyki | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| IDE0042 | C#7.0 + | Visual Studio 2017 v. 15.5 |

### <a name="make-method-synchronous"></a>Zmień metodę na synchroniczną

Przy użyciu `async` słowa kluczowego or `Async` w metodzie, oczekuje się, `await` że wewnątrz tej metody lub `Await` słowo kluczowe jest również używane. Jeśli jednak tak nie jest, zostanie wyświetlona szybka akcja, która umożliwia synchroniczną metodę przez usunięcie `async` słowa `Async` kluczowego or i zmiana typu zwracanego. Użyj opcji " **Utwórz metodę synchroniczną** " z menu szybkie akcje.

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

| Identyfikator błędu | Odpowiednie języki | Obsługiwana wersja |
| ------- | -------------------- | ---------------- |
| CS1998, BC42356 | C# i Visual Basic | Visual Studio 2015 Update 2 |

### <a name="make-method-asynchronous"></a>Ustaw metodę jako asynchroniczną

Przy użyciu `await` słowa kluczowego or `Await` wewnątrz metody, oczekuje się, że `async` Metoda jest oznaczona za pomocą słowa kluczowego `Async` or. Jeśli jednak tak nie jest, zostanie wyświetlona szybka akcja, która powoduje, że metoda asynchronicznie. Użyj opcji " **Utwórz metodę/funkcja asynchroniczna** " z menu szybkie akcje.

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
| CS4032, BC37057 | C# i Visual Basic | Visual Studio 2017 |

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje](../ide/quick-actions.md)
