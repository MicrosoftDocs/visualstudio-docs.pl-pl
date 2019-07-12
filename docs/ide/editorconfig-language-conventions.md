---
title: Konwencje języka .NET dla wtyczki EditorConfig
ms.date: 06/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0ddb6173095b8d4fd552e108f458a271321511c7
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823304"
---
# <a name="language-conventions"></a>Konwencje języka

Konwencje języka dla wtyczki EditorConfig w programie Visual Studio można podzielić na dwie kategorie:

- [Ustawienia stylu kodu .NET](#net-code-style-settings)

- [Ustawienia stylu kodu C#](#c-code-style-settings)

> [!TIP]
> Aby wyświetlić przykłady kodu w Twoim preferowanym języku programowania, wybierz go za pomocą selektora języka w prawym górnym rogu okna przeglądarki.

## <a name="rule-format"></a>Format reguły

Reguły dla języka konwencje mają następujący format Ogólne:

`option_name = value:severity`

Dla każdego Konwencji języka należy określić wartość, która określa, czy i kiedy preferowany styl. Wiele reguł akceptować wartości `true` (Preferuj ten styl) lub `false` (nie Preferuj kwalifikatora ten styl); inne akceptuje wartości takie jak `when_on_single_line` lub `never`. Druga część reguła określa **ważność**.

### <a name="severity"></a>Ważność

Ważność Konwencji języka określa poziom, na którym do wymuszania tego stylu. W poniższej tabeli wymieniono wartości ważności możliwe i ich skutki:

Ważność | Efekt
:------- | ------
`none` | Nie pokazuj żadnych do użytkownika, gdy zasada ta jest naruszona. Funkcje generowania kodu Generuj kod jednak w przypadku tego stylu. Reguły z `none` ważność nigdy nie pojawiają się w **szybkie akcje i Refaktoryzacje** menu. W większości przypadków to jest uznawany za "wyłączone" lub "ignorowane".
`silent` (również `refactoring` w Visual Studio 2017, wersja, należy zachować 15,8 i nowsze) | Nie pokazuj żadnych do użytkownika, gdy zasada ta jest naruszona. Funkcje generowania kodu Generuj kod jednak w przypadku tego stylu. Reguły z `silent` ważność uczestniczyć w oczyszczania, a także są wyświetlane w **szybkie akcje i Refaktoryzacje** menu.
`suggestion` | W przypadku naruszenia tej reguły stylu wyświetlane użytkownikowi jako sugestię. Sugestie są traktowane jako trzy kropki szarym obszarze pierwsze dwa znaki.
`warning` | W przypadku naruszenia tej reguły stylu Pokaż ostrzeżenia kompilatora.
`error` | W przypadku naruszenia tej reguły stylów, Pokaż błąd kompilatora.

## <a name="net-code-style-settings"></a>Ustawienia stylu kodu .NET

Reguły stylów w tej sekcji dotyczą zarówno C# i Visual Basic.

- ["This." i "Me."](#this-and-me)
  - dotnet\_style\_qualification\_for_field
  - dotnet\_style\_qualification\_for_property
  - dotnet\_style\_qualification\_for_method
  - dotnet\_style\_qualification\_for_event
- [Słowa kluczowe języka zamiast framework wpisz nazwy odwołań do typu](#language-keywords)
  - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
  - polecenia DotNet\_styl\_wstępnie zdefiniowanych\_typu\_dla\_member_access
- [Preferencje modyfikator](#normalize-modifiers)
  - dotnet\_style\_require\_accessibility_modifiers
  - csharp\_preferred\_modifier_order
  - visual\_basic\_preferred\_modifier_order
  - polecenia DotNet\_styl\_tylko do odczytu\_pola
- [Preferencje nawiasów](#parentheses-preferences)
  - polecenia DotNet\_styl\_nawiasów\_w\_arytmetyczne\_binarne\_operatorów
  - polecenia DotNet\_styl\_nawiasów\_w\_innych\_binarne\_operatorów
  - polecenia DotNet\_styl\_nawiasów\_w\_innych\_operatorów
  - polecenia DotNet\_styl\_nawiasów\_w\_relacyjnych\_binarne\_operatorów
- [Preferencje wyrażeń poziom](#expression-level-preferences)
  - dotnet\_style\_object_initializer
  - dotnet\_style\_collection_initializer
  - dotnet\_style\_explicit\_tuple_names
  - polecenia DotNet\_styl\_Preferuj\_wywnioskować\_tuple_names
  - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
  - polecenia DotNet\_styl\_Preferuj\_automatycznie\_właściwości
  - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method
  - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
  - dotnet\_style\_prefer\_conditional\_expression\_over\_return
- ["Null" Sprawdzanie preferencje](#null-checking-preferences)
  - dotnet\_style\_coalesce_expression
  - dotnet\_style\_null_propagation

### <a name="this-and-me"></a>"This." i "Me." Kwalifikatory

Ta reguła styl może zostać zastosowana do pola, właściwości, metody i zdarzenia. Wartość **true** oznacza, że wolisz symbolu kodu, aby być poprzedzony znakami `this.` w języku C# lub `Me.` w języku Visual Basic. Wartość **false** oznacza, że Preferuj element kodu _nie_ do być poprzedzony znakami `this.` lub `Me.`.

Te reguły może się pojawić w *.editorconfig* pliku w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnetstylequalificationforfield"></a>dotnet\_style\_qualification\_for_field

|||
|-|-|
| **Nazwa reguły** | dotnet_style_qualification_for_field |
| **Identyfikator reguły** | IDE0003 i IDE0009 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferuj pola, aby być poprzedzony znakami `this.` w C# lub `Me.` w języku Visual Basic<br /><br />`false` -Preferuj pola _nie_ do być poprzedzony znakami `this.` lub `Me.` |
| **Visual Studio domyślną** | `false:silent` |

Przykłady kodu:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

#### <a name="dotnetstylequalificationforproperty"></a>dotnet\_style\_qualification\_for_property

|||
|-|-|
| **Nazwa reguły** | dotnet_style_qualification_for_property |
| **Identyfikator reguły** | IDE0003 i IDE0009 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferuj właściwości, aby być poprzedzony znakami `this.` w C# lub `Me.` w języku Visual Basic<br /><br />`false` -Preferuj właściwości _nie_ do być poprzedzony znakami `this.` lub `Me.` |
| **Visual Studio domyślną** | `false:silent` |

Przykłady kodu:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

#### <a name="dotnetstylequalificationformethod"></a>dotnet\_style\_qualification\_for_method

|||
|-|-|
| **Nazwa reguły** | dotnet_style_qualification_for_method |
| **Identyfikator reguły** | IDE0003 i IDE0009 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferuj metody służące do być poprzedzony znakami `this.` w C# lub `Me.` w języku Visual Basic.<br /><br />`false` -Preferowanych metod _nie_ do być poprzedzony znakami `this.` lub `Me.`. |
| **Visual Studio domyślną** | `false:silent` |

Przykłady kodu:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

#### <a name="dotnetstylequalificationforevent"></a>dotnet\_style\_qualification\_for_event

|||
|-|-|
| **Nazwa reguły** | dotnet_style_qualification_for_event |
| **Identyfikator reguły** | IDE0003 i IDE0009 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferuj zdarzeń, aby być poprzedzony znakami `this.` w C# lub `Me.` w języku Visual Basic.<br /><br />`false` -Preferuj zdarzenia _nie_ do być poprzedzony znakami `this.` lub `Me.`. |
| **Visual Studio domyślną** | `false:silent` |

Przykłady kodu:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

### <a name="language-keywords"></a>Słowa kluczowe języka zamiast framework wpisz nazwy odwołań do typu

Ta zasada styl mogą być stosowane w przypadku, zmiennych lokalnych, parametrów metod i składowych klasy lub oddzielne zasady do typu wyrażenia dostępu do składowych. Wartość **true** oznacza, że wolisz słowo kluczowe języka (na przykład `int` lub `Integer`) zamiast nazwy typu (na przykład `Int32`) dla typów, które mają słowo kluczowe do ich reprezentacji. Wartość **false** oznacza, że Preferuj nazwę typu, zamiast słowa kluczowego języka.

Te reguły może się pojawić w *.editorconfig* pliku w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnetstylepredefinedtypeforlocalsparametersmembers"></a>dotnet\_style\_predefined\_type\_for\_locals\_parameters_members

|||
|-|-|
| **Nazwa reguły** | dotnet_style_predefined_type_for_locals_parameters_members |
| **Identyfikator reguły** | IDE0012 i IDE0014 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` — Słowo kluczowe języka dla zmiennych lokalnych, parametrów metod i składowych klasy, a nie nazwę typu dla typów, które mają słowo kluczowe do ich reprezentacji Preferuj<br /><br />`false` -Preferuj nazwę typu dla zmiennych lokalnych, parametrów metod i składowych klasy, zamiast słowa kluczowego języka |
| **Visual Studio domyślną** | `true:silent` |

Przykłady kodu:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

#### <a name="dotnetstylepredefinedtypeformemberaccess"></a>polecenia DotNet\_styl\_wstępnie zdefiniowanych\_typu\_dla\_member_access

|||
|-|-|
| **Nazwa reguły** | dotnet_style_predefined_type_for_member_access |
| **Identyfikator reguły** | IDE0013 i IDE0015 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` — Słowo kluczowe języka dla wyrażenia dostępu do składowych, a nie nazwę typu dla typów, które mają słowo kluczowe do ich reprezentacji Preferuj<br /><br />`false` — Nazwa typu dla wyrażenia dostępu do składowych, zamiast słowa kluczowego języka Preferuj |
| **Visual Studio domyślną** | `true:silent` |

Przykłady kodu:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

### <a name="normalize-modifiers"></a>Preferencje modyfikator

Reguły stylów w tej sekcji dotyczą preferencje modyfikator, m.in. wymagające modyfikatory dostępności, określa ona kolejność sortowania modyfikator żądaną i wymagające modyfikatora tylko do odczytu.

Te reguły może się pojawić w *.editorconfig* pliku w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="dotnetstylerequireaccessibilitymodifiers"></a>dotnet\_style\_require\_accessibility_modifiers

|||
|-|-|
| **Nazwa reguły** | dotnet_style_require_accessibility_modifiers |
| **Identyfikator reguły** | IDE0040 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `always` -Preferują modyfikatory dostępności należy określić.<br /><br />`for_non_interface_members` -Preferują modyfikatory dostępności być zadeklarowany z wyjątkiem elementów członkowskich interfejsu publicznego. (To jest taka sama jak **zawsze** i dodano do sprawdzania w przyszłości, gdy C# dodaje domyślnych metod interfejsu.)<br /><br />`never` -Nie Preferuj kwalifikatora modyfikatory dostępności należy określić.<br /><br />`omit_if_default` -Preferują modyfikatory dostępności należy określić z wyjątkiem, jeśli są one modyfikator domyślny. |
| **Visual Studio domyślną** | `for_non_interface_members:silent` |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.5 |

Przykłady kodu:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

#### <a name="csharppreferredmodifierorder"></a>csharp_preferred_modifier_order

|||
|-|-|
| **Nazwa reguły** | csharp_preferred_modifier_order |
| **Identyfikator reguły** | IDE0036 |
| **Właściwe języki** | C# |
| **Wartości** | Co najmniej jeden C# modyfikatorów, takich jak `public`, `private`, i `protected` |
| **Visual Studio domyślną** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.5 |

- Gdy ta reguła ma wartość listy modyfikatorów tak, określonej kolejności.
- Gdy ta reguła jest pominięty z pliku, kolejność modyfikator nie jest preferowane.

Przykłady kodu:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

#### <a name="visualbasicpreferredmodifierorder"></a>visual_basic_preferred_modifier_order

|||
|-|-|
| **Nazwa reguły** | visual_basic_preferred_modifier_order |
| **Identyfikator reguły** | IDE0036 |
| **Właściwe języki** | Visual Basic |
| **Wartości** | Co najmniej jeden modyfikatorów języka Visual Basic, takie jak `Partial`, `Private`, i `Public` |
| **Visual Studio domyślną** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.5 |

- Gdy ta reguła ma wartość listy modyfikatorów tak, określonej kolejności.
- Gdy ta reguła jest pominięty z pliku, kolejność modyfikator nie jest preferowane.

Przykłady kodu:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="dotnetstylereadonlyfield"></a>dotnet_style_readonly_field

|||
|-|-|
| **Nazwa reguły** | dotnet_style_readonly_field |
| **Identyfikator reguły** | IDE0044 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferuje się, że pól powinien być oznaczony przez `readonly` (C#) lub `ReadOnly` (Visual Basic), jeśli są one jedynie nigdy nie przypisano wbudowanych lub wewnątrz konstruktora<br /><br />`false` -Określ Brak preferencji za pośrednictwem tego, czy pola powinien być oznaczony przez `readonly` (C#) lub `ReadOnly` (Visual Basic) |
| **Visual Studio domyślną** | `true:suggestion` |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.7 |

Przykłady kodu:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

### <a name="parentheses-preferences"></a>Preferencje nawiasów

Reguły stylów w tej sekcji dotyczą preferencje nawiasy, łącznie z użyciem nawiasów dla operacji arytmetycznych relacyjna, i inne operatory dwuargumentowe.

Te reguły może się pojawić w *.editorconfig* pliku w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnetstyleparenthesesinarithmeticbinaryoperators"></a>polecenia DotNet\_styl\_nawiasów\_w\_arytmetyczne\_binary_operators

|||
|-|-|
| **Nazwa reguły** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **Identyfikator reguły** | IDE0047 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `always_for_clarity` -Preferuj nawiasów, aby wyjaśnić, operator arytmetyczny (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) pierwszeństwo<br /><br />`never_if_unnecessary` -Wolą ma nawiasy, gdy arytmetyczne — operator (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) pierwszeństwo jest oczywiste |
| **Visual Studio domyślną** | `always_for_clarity:silent` |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.8 |

Przykłady kodu:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

#### <a name="dotnetstyleparenthesesinrelationalbinaryoperators"></a>polecenia DotNet\_styl\_nawiasów\_w\_relacyjnych\_binary_operators

|||
|-|-|
| **Nazwa reguły** | dotnet_style_parentheses_in_relational_binary_operators |
| **Identyfikator reguły** | IDE0047 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `always_for_clarity` -Preferuj nawiasów, aby wyjaśnić, operator relacyjny (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) pierwszeństwo<br /><br />`never_if_unnecessary` -Wolą ma nawiasy, gdy relacyjnych — operator (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) jest oczywiste, pierwszeństwo |
| **Visual Studio domyślną** | `always_for_clarity:silent` |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.8 |

Przykłady kodu:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

#### <a name="dotnetstyleparenthesesinotherbinaryoperators"></a>polecenia DotNet\_styl\_nawiasów\_w\_innych\_binary_operators

|||
|-|-|
| **Nazwa reguły** | dotnet_style_parentheses_in_other_binary_operators |
| **Identyfikator reguły** | IDE0047 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `always_for_clarity` -Preferuj nawiasy w celu wyjaśnienia innych operatora binarnego (`&&`, `||`, `??`) pierwszeństwo<br /><br />`never_if_unnecessary` -Wolą bez nawiasów po innych operatora binarnego (`&&`, `||`, `??`) jest oczywiste, pierwszeństwo |
| **Visual Studio domyślną** | `always_for_clarity:silent` |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.8 |

Przykłady kodu:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

#### <a name="dotnetstyleparenthesesinotheroperators"></a>dotnet\_style\_parentheses\_in\_other_operators

|||
|-|-|
| **Nazwa reguły** | dotnet_style_parentheses_in_other_operators |
| **Identyfikator reguły** | IDE0047 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `always_for_clarity` -Preferuj nawiasów, aby wyjaśnić kolejność wykonywania działań<br /><br />`never_if_unnecessary` -Wolisz nie mieć nawiasy, gdy pierwszeństwo operatorów jest oczywisty |
| **Visual Studio domyślną** | `never_if_unnecessary:silent` |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.8 |

Przykłady kodu:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

### <a name="expression-level-preferences"></a>Preferencje wyrażeń poziom

Styl reguł w tej sekcji dotyczą wyrażenie poziomu preferencjach, łącznie z użyciem inicjatorów obiektów, inicjatory kolekcji, nazwy krotki jawne lub wywnioskowane uprawnienie i wywnioskować typów anonimowych.

Te reguły może się pojawić w *.editorconfig* pliku w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
```

#### <a name="dotnetstyleobjectinitializer"></a>dotnet\_style\_object_initializer

|||
|-|-|
| **Nazwa reguły** | dotnet_style_object_initializer |
| **Identyfikator reguły** | IDE0017 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferuj obiekty mogą zostać zainicjowane przy użyciu inicjatorów obiektów, gdy jest to możliwe<br /><br />`false` -Preferuj obiekty w celu *nie* można zainicjować przy użyciu inicjatory obiektów |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

#### <a name="dotnetstylecollectioninitializer"></a>dotnet\_style\_collection_initializer

|||
|-|-|
| **Nazwa reguły** | dotnet_style_collection_initializer |
| **Identyfikator reguły** | IDE0028 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferuj kolekcji, aby można zainicjować przy użyciu inicjatory kolekcji, jeśli jest to możliwe<br /><br />`false` -Preferuj kolekcje w celu *nie* można zainicjować przy użyciu inicjatory kolekcji |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

#### <a name="dotnetstyleexplicittuplenames"></a>dotnet\_style\_explicit\_tuple_names

|||
|-|-|
| **Nazwa reguły** | dotnet_style_explicit_tuple_names |
| **Identyfikator reguły** | IDE0033 |
| **Właściwe języki** | C# 7.0 + i Visual Basic 15 + |
| **Wartości** | `true` -Wolą nazw krotek ItemX właściwości<br /><br />`false` -Wolą ItemX właściwości nazwy krotki |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

#### <a name="dotnetstylepreferinferredtuplenames"></a>polecenia DotNet\_styl\_Preferuj\_wywnioskować\_tuple_names

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_inferred_tuple_names |
| **Identyfikator reguły** | IDE0037 |
| **Właściwe języki** | C# 7.1 +, jak i Visual Basic 15 + |
| **Wartości** | `true` -Preferuj wywnioskowane nazwy elementów krotki<br /><br />`false` -Preferuj nazwami elementów krotki jawne |
| **Visual Studio domyślną** | `true:suggestion` |
| **Wprowadzono wersji** | Visual Studio 2017 wersja 15.6 |

Przykłady kodu:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

#### <a name="dotnetstylepreferinferredanonymoustypemembernames"></a>dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **Identyfikator reguły** | IDE0037 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferuj wywnioskowane nazwy anonimowych składowych typu<br /><br />`false` -Preferuj jawną nazwy anonimowych składowych typu |
| **Visual Studio domyślną** | `true:suggestion` |
| **Wprowadzono wersji** | Visual Studio 2017 wersja 15.6 |

Przykłady kodu:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

#### <a name="dotnetstylepreferautoproperties"></a>polecenia DotNet\_styl\_Preferuj\_automatycznie\_właściwości

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_auto_properties |
| **Identyfikator reguły** | IDE0032 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferowanie autoproperties za pośrednictwem właściwości za pomocą pola prywatne zapasowy<br /><br />`false` -Preferuj właściwości za pomocą pola prywatne zapasowy przed autoproperties |
| **Visual Studio domyślną** | `true:suggestion` |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.7 |

Przykłady kodu:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

#### <a name="dotnetstylepreferisnullcheckoverreferenceequalitymethod"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **Identyfikator reguły** | IDE0041 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferuj przy użyciu sprawdzania wartości null z dopasowaniem wzorca przez `object.ReferenceEquals`<br /><br />`false` -Preferuj `object.ReferenceEquals` za pośrednictwem sprawdzania wartości null z dopasowaniem wzorca |
| **Visual Studio domyślną** | `true:suggestion` |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.7 |

Przykłady kodu:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```

#### <a name="dotnetstylepreferconditionalexpressionoverassignment"></a>dotnet\_style\_prefer\_conditional\_expression\_over_assignment

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_conditional_expression_over_assignment |
| **Identyfikator reguły** | IDE0045 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferowanie przypisania w usłudze trójargumentowy warunkowe za pośrednictwem if-else, instrukcja<br /><br />`false` -Preferowanie przydziałów za pomocą instrukcji if-else za pośrednictwem trójargumentowy warunkowe |
| **Visual Studio domyślną** | `true:suggestion` |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.8 |

Przykłady kodu:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

#### <a name="dotnetstylepreferconditionalexpressionoverreturn"></a>dotnet\_style\_prefer\_conditional\_expression\_over_return

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_conditional_expression_over_return |
| **Identyfikator reguły** | IDE0046 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferuj instrukcjach return używać trójargumentowy warunkowe za pośrednictwem if-else, instrukcja<br /><br />`false` -Preferuj instrukcjach return użyć instrukcji if-else za pośrednictwem trójargumentowy warunkowe |
| **Visual Studio domyślną** | `true:suggestion` |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.8 |

Przykłady kodu:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

### <a name="null-checking-preferences"></a>Preferencje sprawdzania wartości null

Reguły stylów w tej sekcji dotyczą preferencje sprawdzania wartości null.

Te reguły może się pojawić w *.editorconfig* pliku w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

#### <a name="dotnetstylecoalesceexpression"></a>dotnet\_style\_coalesce_expression

|||
|-|-|
| **Nazwa reguły** | dotnet_style_coalesce_expression |
| **Identyfikator reguły** | IDE0029 |
| **Właściwe języki** | C# i Visual Basic |
| **Wartości** | `true` -Preferuj null wyrażenia łączącego, aby operator trójargumentowy sprawdzanie<br /><br />`false` -Preferuj operator trójargumentowy sprawdzanie wyrażenia łączące wartości null |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

#### <a name="dotnetstylenullpropagation"></a>dotnet\_style\_null_propagation

|||
|-|-|
| **Nazwa reguły** | dotnet_style_null_propagation |
| **Identyfikator reguły** | IDE0031 |
| **Właściwe języki** | C# 6.0 + i Visual Basic 14 + |
| **Wartości** | `true` -Wolą używać operatorów warunkowych działających z wartością null, gdy jest to możliwe<br /><br />`false` -Wolą używać trójargumentowy sprawdzania wartości null, jeśli jest to możliwe |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

## <a name="c-code-style-settings"></a>Ustawienia stylu kodu C#

Reguły stylów w tej sekcji odnoszą się do języka C# tylko.

- [Typy jawne i niejawne](#implicit-and-explicit-types)
  - CSharp\_styl\_var\_dla\_wbudowane\_in_types
  - csharp\_style\_var\_when\_type\_is_apparent
  - CSharp\_styl\_var_elsewhere
- [Elementy członkowskie z wyrażeniem w treści](#expression-bodied-members)
  - csharp\_style\_expression\_bodied_methods
  - csharp\_style\_expression\_bodied_constructors
  - csharp\_style\_expression\_bodied_operators
  - csharp\_style\_expression\_bodied_properties
  - csharp\_style\_expression\_bodied_indexers
  - csharp\_style\_expression\_bodied_accessors
- [Dopasowanie do wzorca](#pattern-matching)
  - CSharp\_styl\_wzorzec\_pasującego\_za pośrednictwem\_jest\_z\_cast_check
  - CSharp\_styl\_wzorzec\_pasującego\_za pośrednictwem\_jako\_z\_null_check
- [Śródwierszowe deklaracje zmiennych](#inlined-variable-declarations)
  - csharp\_style\_inlined\_variable_declaration
- [Preferencje wyrażeń poziom](#expression-level-preferences)
  - csharp\_prefer\_simple\_default_expression
  - CSharp\_styl\_zdekonstruowana\_variable_declaration
  - csharp\_style\_pattern\_local\_over\_anonymous_function
- ["Null" Sprawdzanie preferencje](#null-checking-preferences)
  - csharp\_style\_throw_expression
  - csharp\_style\_conditional\_delegate_call
- [Preferencje bloku kodu](#code-block-preferences)
  - CSharp\_prefer_braces

### <a name="implicit-and-explicit-types"></a>Typy jawne i niejawne

Reguły stylów w tej sekcji dotyczą użytkowania [var](/dotnet/csharp/language-reference/keywords/var) — słowo kluczowe w porównaniu z typem jawnym w deklaracji zmiennej. Ta zasada może dotyczyć oddzielnie wbudowanych typów, gdy typ jest widoczny i w innych miejscach.

Przykład *.editorconfig* pliku:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharpstylevarforbuiltintypes"></a>CSharp\_styl\_var\_dla\_wbudowane\_in_types

|||
|-|-|
| **Nazwa reguły** | csharp_style_var_for_built_in_types |
| **Identyfikator reguły** | IDE0007 i IDE0008 |
| **Właściwe języki** | C#  |
| **Wartości** | `true` -Preferuj `var` służy do deklarowania zmiennych wbudowany system typów, takich jak `int`<br /><br />`false` -Preferuj jawny typ za pośrednictwem `var` deklarowanie zmiennych wbudowany system typów, takich jak `int` |
| **Visual Studio domyślną** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharpstylevarwhentypeisapparent"></a>csharp\_style\_var\_when\_type\_is_apparent

|||
|-|-|
| **Nazwa reguły** | csharp_style_var_when_type_is_apparent |
| **Identyfikator reguły** | IDE0007 i IDE0008 |
| **Właściwe języki** | C#  |
| **Wartości** | `true` -Preferuj `var` kiedy typ jest już Wspomniałem, po prawej stronie wyrażenie deklaracji<br /><br />`false` -Preferuj jawny typ za pośrednictwem `var` kiedy typ jest już Wspomniałem, po prawej stronie wyrażenie deklaracji |
| **Visual Studio domyślną** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharpstylevarelsewhere"></a>CSharp\_styl\_var_elsewhere

|||
|-|-|
| **Nazwa reguły** | csharp_style_var_elsewhere |
| **Identyfikator reguły** | IDE0007 i IDE0008 |
| **Właściwe języki** | C#  |
| **Wartości** | `true` -Preferuj `var` za pośrednictwem typu jawnego we wszystkich przypadkach, jeśli zastąpiona przez inną regułę stylu kodu<br /><br />`false` -Preferuj jawny typ za pośrednictwem `var` we wszystkich przypadkach, jeśli zastąpiona przez inną regułę stylu kodu |
| **Visual Studio domyślną** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>Składowe z wyrażeniem w treści

Reguły stylów w tej sekcji dotyczą użytkowania [elementy członkowskie z wyrażeniem](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) po logikę składa się z pojedynczego wyrażenia. To reguła może zostać zastosowana do metod, konstruktory, operatory, właściwości, indeksatory i metod dostępu.

Przykład *.editorconfig* pliku:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="csharpstyleexpressionbodiedmethods"></a>csharp\_style\_expression\_bodied_methods

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_methods |
| **Identyfikator reguły** | IDE0022 |
| **Właściwe języki** | C# 6.0+  |
| **Wartości** | `true` -Preferuj wyrażeniem elementów członkowskich dla metod<br /><br />`when_on_single_line` -Preferuj wyrażeniem elementów członkowskich dla metod gdy będą one jednym wierszu<br /><br />`false` -Preferuj treści bloku dla metod |
| **Visual Studio domyślną** | `false:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharpstyleexpressionbodiedconstructors"></a>csharp\_style\_expression\_bodied_constructors

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_constructors |
| **Identyfikator reguły** | IDE0021 |
| **Właściwe języki** | C# 7.0+  |
| **Wartości** | `true` -Preferuj wyrażeniem elementów członkowskich dla konstruktorów<br /><br />`when_on_single_line` -Preferuj wyrażeniem elementów członkowskich dla konstruktorów, gdy będą one jednym wierszu<br /><br />`false` -Preferuj treści bloku dla konstruktorów |
| **Visual Studio domyślną** | `false:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharpstyleexpressionbodiedoperators"></a>csharp\_style\_expression\_bodied_operators

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_operators |
| **Identyfikator reguły** | IDE0023 i IDE0024 |
| **Właściwe języki** | C# 7.0+  |
| **Wartości** | `true` -Preferuj wyrażeniem elementów członkowskich dla operatorów<br /><br />`when_on_single_line` -Preferowany wyrażeniem elementów członkowskich dla operatorów podczas będą one jednym wierszu<br /><br />`false` -Preferuj treści bloku dla operatorów |
| **Visual Studio domyślną** | `false:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharpstyleexpressionbodiedproperties"></a>csharp\_style\_expression\_bodied_properties

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_properties |
| **Identyfikator reguły** | IDE0025 |
| **Właściwe języki** | C# 7.0+  |
| **Wartości** | `true` -Preferuj wyrażeniem elementów członkowskich dla właściwości<br /><br />`when_on_single_line` -Preferuj wyrażeniem elementów członkowskich dla właściwości przypadku będą one pojedynczy wiersz<br /><br />`false` -Preferuj treści bloku dla właściwości |
| **Visual Studio domyślną** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharpstyleexpressionbodiedindexers"></a>csharp\_style\_expression\_bodied_indexers

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_indexers |
| **Identyfikator reguły** | IDE0026 |
| **Właściwe języki** | C# 7.0+  |
| **Wartości** | `true` -Preferuj wyrażeniem elementów członkowskich dla indeksatorów<br /><br />`when_on_single_line` -Preferowany wyrażeniem elementów członkowskich dla indeksatorów podczas będą one jednym wierszu<br /><br />`false` -Preferuj treści bloku dla indeksatorów |
| **Visual Studio domyślną** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharpstyleexpressionbodiedaccessors"></a>csharp\_style\_expression\_bodied_accessors

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_accessors |
| **Identyfikator reguły** | IDE0027 |
| **Właściwe języki** | C# 7.0+  |
| **Wartości** | `true` -Preferuj wyrażeniem elementów członkowskich dla metod dostępu<br /><br />`when_on_single_line` -Preferowany wyrażeniem elementów członkowskich dla metod dostępu podczas będą one jednym wierszu<br /><br />`false` -Preferuj treści bloku dla metod dostępu |
| **Visual Studio domyślną** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

### <a name="pattern-matching"></a>Dopasowanie do wzorca

Reguły stylów w tej sekcji dotyczą użytkowania [dopasowywania do wzorca](/dotnet/csharp/pattern-matching) w języku C#.

Przykład *.editorconfig* pliku:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharpstylepatternmatchingoveriswithcastcheck"></a>CSharp\_styl\_wzorzec\_pasującego\_za pośrednictwem\_jest\_z\_cast_check

|||
|-|-|
| **Nazwa reguły** | csharp_style_pattern_matching_over_is_with_cast_check |
| **Identyfikator reguły** | IDE0020 |
| **Właściwe języki** | C# 7.0+  |
| **Wartości** | `true` -Preferuj dopasowywanie do wzorców zamiast `is` wyrażenia z rzutowania typów<br /><br />`false` -Preferuj `is` wyrażenia z rzutowania typów, zamiast dopasowywania do wzorca |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharpstylepatternmatchingoveraswithnullcheck"></a>CSharp\_styl\_wzorzec\_pasującego\_za pośrednictwem\_jako\_z\_null_check

|||
|-|-|
| **Nazwa reguły** | csharp_style_pattern_matching_over_as_with_null_check |
| **Identyfikator reguły** | IDE0019 |
| **Właściwe języki** | C# 7.0+  |
| **Wartości** | `true` -Preferuj dopasowywanie do wzorców zamiast `as` wyrażeń o wartości null kontrole w celu ustalenia, czy jest coś, co jest określonego typu<br /><br />`false` -Preferuj `as` wyrażenia z sprawdzanie wartości null, zamiast dopasowywania do wzorca w celu ustalenia, czy jest coś, co jest określonego typu |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>Śródwierszowe deklaracje zmiennych

Ten styl tego, czy reguła dotyczy `out` zmienne są zadeklarowane wbudowane, czy nie. Począwszy od C# 7, możesz [deklarowanie zmiennej poza na liście argumentów wywołania metody](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), zamiast w oddzielnych deklaracji zmiennej.

#### <a name="csharpstyleinlinedvariabledeclaration"></a>csharp\_style\_inlined\_variable_declaration

|||
|-|-|
| **Nazwa reguły** | csharp_style_inlined_variable_declaration |
| **Identyfikator reguły** | IDE0018 |
| **Właściwe języki** | C# 7.0+  |
| **Wartości** | `true` -Preferuj `out` zmienne, aby być zadeklarowana śródwierszowo na liście argumentów wywołania metody, gdy jest to możliwe<br /><br />`false` -Preferuj `out` zmienne być zadeklarowany przed wywołaniem metody |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Przykład *.editorconfig* pliku:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="expression-level-preferences"></a>Preferencje wyrażeń poziom

Reguły stylów w tej sekcji dotyczą poziomu wyrażenia preferencje, łącznie z użyciem [domyślne wyrażeń](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), śródwierszową zmiennych i funkcji lokalnych za pośrednictwem funkcji anonimowych.

Przykład *.editorconfig* pliku:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="csharpprefersimpledefaultexpression"></a>csharp\_prefer\_simple\_default_expression

Ta zasada styl dotyczy przy użyciu [ `default` dosłownie wyrażenia wartości domyślnych](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) Kiedy kompilator może wywnioskować typ wyrażenia.

|||
|-|-|
| **Nazwa reguły** | csharp_prefer_simple_default_expression |
| **Identyfikator reguły** | IDE0034 |
| **Właściwe języki** | C# 7.1+  |
| **Wartości** | `true` -Preferuj `default` za pośrednictwem `default(T)`<br /><br />`false` -Preferuj `default(T)` za pośrednictwem `default` |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

#### <a name="csharpstyledeconstructedvariabledeclaration"></a>CSharp\_styl\_zdekonstruowana\_variable_declaration

|||
|-|-|
| **Nazwa reguły** | csharp_style_deconstructed_variable_declaration |
| **Identyfikator reguły** | IDE0042 |
| **Właściwe języki** | C# 7.0+  |
| **Wartości** | `true` -Preferuj śródwierszową deklarację zmiennej<br /><br />`false` -Nie Preferuj kwalifikatora dekonstrukcja w deklaracjach zmiennych |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

#### <a name="csharpstylepatternlocaloveranonymousfunction"></a>csharp\_style\_pattern\_local\_over\_anonymous_function

|||
|-|-|
| **Nazwa reguły** | csharp_style_pattern_local_over_anonymous_function |
| **Identyfikator reguły** | IDE0039 |
| **Właściwe języki** | C# 7.0+  |
| **Wartości** | `true` -Preferowanie funkcji lokalnych za pośrednictwem funkcji anonimowych<br /><br />`false` -Preferowanie funkcje anonimowe za pośrednictwem funkcji lokalnych |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

### <a name="null-checking-preferences"></a>Preferencje sprawdzania wartości null

Te reguły dotyczą stylów składni wokół `null` sprawdzania, w tym o korzystaniu z `throw` wyrażeń lub `throw` instrukcji i czy do wykonywania sprawdzania wartości null lub użyć operatora łączącego warunkowego (`?.`) podczas wywoływania [wyrażenia lambda](/dotnet/csharp/lambda-expressions).

Przykład *.editorconfig* pliku:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharpstylethrowexpression"></a>csharp\_style\_throw_expression

|||
|-|-|
| **Nazwa reguły** | csharp_style_throw_expression |
| **Identyfikator reguły** | IDE0016 |
| **Właściwe języki** | C# 7.0+  |
| **Wartości** | `true` -Wolą używać `throw` wyrażeń, zamiast `throw` instrukcji<br /><br />`false` -Wolą używać `throw` instrukcji zamiast `throw` wyrażeń |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharpstyleconditionaldelegatecall"></a>csharp\_style\_conditional\_delegate_call

|||
|-|-|
| **Nazwa reguły** | csharp_style_conditional_delegate_call |
| **Identyfikator reguły** | IDE0041 |
| **Właściwe języki** | C# 6.0+  |
| **Wartości** | `true` -odnoszą się do użycia operatora łączącego warunkowego (`?.`) podczas wywoływania Wyrażenie lambda, zamiast wykonywania o wartości null zaznacz<br /><br />`false` -Chcesz wykonać sprawdzanie wartości null, przed wywołaniem wyrażenia lambda, zamiast korzystać z operatora łączącego warunkowego (`?.`) |
| **Visual Studio domyślną** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Preferencje bloku kodu

Ta zasada styl dotyczy użycia nawiasów klamrowych `{ }` otoczyć bloków kodu.

Przykład *.editorconfig* pliku:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharppreferbraces"></a>CSharp\_Preferuj\_nawiasów klamrowych

|||
|-|-|
| **Nazwa reguły** | csharp_prefer_braces |
| **Identyfikator reguły** | IDE0011 |
| **Właściwe języki** | C# |
| **Wartości** | `true` -Preferuj nawiasów klamrowych, nawet w przypadku jednego wiersza kodu<br /><br />`false` -Preferuj nie nawiasów klamrowych. Jeśli jest to dozwolone |
| **Visual Studio domyślną** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

## <a name="see-also"></a>Zobacz także

- [Konwencje formatowania](editorconfig-formatting-conventions.md)
- [Konwencje nazewnictwa](editorconfig-naming-conventions.md)
- [.NET coding convention ustawienia dla wtyczki EditorConfig](editorconfig-code-style-settings-reference.md)
