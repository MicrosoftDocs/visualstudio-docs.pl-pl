---
title: Konwencje języka .NET dla EditorConfig
ms.date: 07/17/2019
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
ms.openlocfilehash: 7b88824e6be7dbb216aa14ca9a22fd692474ec2f
ms.sourcegitcommit: a124076dfd6b4e5aecda4d01984fee7b0c034745
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787418"
---
# <a name="language-conventions"></a>Konwencje języka

Konwencje językowe dla EditorConfig w programie Visual Studio dzielą się na dwie kategorie: te, C#które mają zastosowanie do Visual Basic C# i i tych, które są określone. Konwencje językowe mają wpływ na sposób używania różnych aspektów języka programowania, na przykład modyfikatory i nawiasy.

> [!TIP]
> - **W tym artykule** znajdują się linki umożliwiające przechodzenie do różnych sekcji strony.
> - Aby wyświetlić przykłady kodu w preferowanym języku programowania, wybierz go za pomocą selektora języka w prawym górnym rogu okna przeglądarki.
>
>   ![Kontrolka selektora języka kodu](media/code-language-picker.png)

## <a name="rule-format"></a>Format reguły

Reguły dotyczące konwencji języka mają następujący format ogólny:

`option_name = value:severity`

Dla każdej Konwencji językowej należy określić wartość określającą, czy lub kiedy wolisz styl. `true` Wiele reguł akceptuje wartość (Preferuj ten styl) lub `false` (nie Preferuj tego stylu). inne akceptują wartości, takie jak `when_on_single_line` lub `never`. Druga część reguły określa **ważność**.

### <a name="severity"></a>Ważność

Ważność Konwencji języka określa poziom, na którym należy wymusić ten styl. Poniższa tabela zawiera listę możliwych wartości ważności i ich efektów:

Ważność | Efekt
:------- | ------
`none` | Gdy ta reguła jest naruszona, nie pokazuj niczego użytkownikowi. Funkcje generowania kodu generują kod w tym stylu. Reguły o `none` ważności nigdy nie pojawiają się w menu **szybkie akcje i operacje refaktoryzacji** . W większości przypadków jest to traktowane jako "wyłączone" lub "zignorowane".
`silent`(również `refactoring` w programie Visual Studio 2017 w wersji 15,8 lub nowszej) | Gdy ta reguła jest naruszona, nie pokazuj niczego użytkownikowi. Funkcje generowania kodu generują kod w tym stylu. Reguły o `silent` ważności uczestniczą w oczyszczaniu, jak również w menu **szybkie akcje i refaktoryzacje** .
`suggestion` | Gdy ta reguła stylu zostanie naruszona, Pokaż ją użytkownikowi jako sugestię. Sugestie są wyświetlane jako trzy szare kropki poniżej dwóch pierwszych znaków.
`warning` | Gdy ta reguła stylu jest naruszona, Pokaż Ostrzeżenie kompilatora.
`error` | Gdy ta reguła stylu jest naruszona, Pokaż błąd kompilatora.

## <a name="net-code-style-settings"></a>Ustawienia stylu kodu platformy .NET

Reguły stylu w tej sekcji dotyczą zarówno C# programu, jak i Visual Basic.

- [Kwalifikatory "this." i "Me."](#this-and-me)
  - dotnet\_style\_qualification\_for_field
  - dotnet\_style\_qualification\_for_property
  - dotnet\_style\_qualification\_for_method
  - dotnet\_style\_qualification\_for_event
- [Słowa kluczowe języka zamiast nazw typów struktur dla odwołań typu](#language-keywords)
  - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
  - wstępnie\_zdefiniowany\_Typ\_styludotnet dla\_member_access\_
- [Preferencje modyfikatora](#normalize-modifiers)
  - dotnet\_style\_require\_accessibility_modifiers
  - csharp\_preferred\_modifier_order
  - preferowany\_\_modifier_order\_języka Visual Basic
  - pole\_stylu\_dotnet\_tylko do odczytu
- [Preferencje nawiasów](#parentheses-preferences)
  - \_\_nawiasy\_stylu dotnet w\_okrągłychOperatoryarytmetyczne\_\_
  - \_nawiasy\_styludotnet\_\_w innychoperatorachbinarnych\_\_
  - \_nawiasy\_styludotnet\_winnych\_operatorach\_
  - \_nawiasy\_\_stylu dotnetw\_relacyjnych\_operatorachbinarnych\_
- [Preferencje poziomu wyrażenia](#expression-level-preferences)
  - dotnet\_style\_object_initializer
  - dotnet\_style\_collection_initializer
  - jawny\_\_tuple_namesstylu\_dotnet
  - styl\_dotnet\_Preferuj\_tuple_nameswnioskowane\_
  - styl\_dotnet\_Preferuj\_wywnioskowany\_typanonimowy\_member_names\_
  - styl\_dotnet\_Preferuj\_właściwościautoproperties\_
  - \_preferowany\_styldotnet\_to sprawdzeniewartościnull\_względem\_metody równości\_odwołań\_\_\_
  - styl\_dotnetPreferuj\_wyrażeniewarunkowe\_nad\_przypisaniem\_\_
  - dotnet\_style\_prefer\_conditional\_expression\_over\_return
  - styl\_dotnet\_Preferujprzypisanie\_złożone\_
- [Preferencje sprawdzania wartości "null"](#null-checking-preferences)
  - dotnet\_style\_coalesce_expression
  - dotnet\_style\_null_propagation

### <a name="this-and-me"></a>"This" i "Me". kwalifikatory

Ta reguła stylu może być stosowana do pól, właściwości, metod lub zdarzeń. Wartość **prawda** oznacza, że symbol kodu ma być poprzedzony `this.` w C# lub `Me.` w Visual Basic. Wartość **false** oznacza, że element kodu _nie_ powinien być `this.` poprzedzony lub. `Me.`

Te reguły mogą pojawić się w pliku *. editorconfig* w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>dotnet\_style\_qualification\_for_field

|||
|-|-|
| **Nazwa reguły** | dotnet_style_qualification_for_field |
| **Identyfikator reguły** | IDE0003 i IDE0009 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`— Preferuj pola, które mają być poprzedzone `this.` w C# lub `Me.` w Visual Basic<br /><br />`false`— Preferuj pola , do których `this.` nie ma być poprzedzone lub`Me.` |
| **Domyślne dla programu Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_property"></a>dotnet\_style\_qualification\_for_property

|||
|-|-|
| **Nazwa reguły** | dotnet_style_qualification_for_property |
| **Identyfikator reguły** | IDE0003 i IDE0009 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj właściwości, które mają być poprzedzone `this.` w C# lub `Me.` w Visual Basic<br /><br />`false`— Preferuj właściwości , dla których `this.` nie ma być poprzedzone lub`Me.` |
| **Domyślne dla programu Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_method"></a>dotnet\_style\_qualification\_for_method

|||
|-|-|
| **Nazwa reguły** | dotnet_style_qualification_for_method |
| **Identyfikator reguły** | IDE0003 i IDE0009 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj metody, które mają być poprzedzone `this.` funkcją C# in `Me.` lub in Visual Basic.<br /><br />`false`-Preferuj metody `this.` , które nie powinny być poprzedzone lub `Me.`. |
| **Domyślne dla programu Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_event"></a>dotnet\_style\_qualification\_for_event

|||
|-|-|
| **Nazwa reguły** | dotnet_style_qualification_for_event |
| **Identyfikator reguły** | IDE0003 i IDE0009 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`— Preferuj zdarzenia, które mają być poprzedzone `this.` w C# programie `Me.` lub w Visual Basic.<br /><br />`false`-Preferuj zdarzenia `this.` , które nie powinny być poprzedzone lub `Me.`. |
| **Domyślne dla programu Visual Studio** | `false:silent` |

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

### <a name="language-keywords"></a>Słowa kluczowe języka zamiast nazw typów struktur dla odwołań typu

Tę regułę stylu można zastosować do zmiennych lokalnych, parametrów metody i elementów członkowskich klasy albo jako osobną regułę do wpisywania wyrażeń dostępu do składowych. Wartość **true** oznacza preferowanie słowa kluczowego language (na przykład `int` lub `Integer`) zamiast nazwy typu (na przykład `Int32`) dla typów, które mają słowo kluczowe do reprezentowania. Wartość **false** oznacza preferowanie nazwy typu zamiast słowa kluczowego języka.

Te reguły mogą pojawić się w pliku *. editorconfig* w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>dotnet\_style\_predefined\_type\_for\_locals\_parameters_members

|||
|-|-|
| **Nazwa reguły** | dotnet_style_predefined_type_for_locals_parameters_members |
| **Identyfikator reguły** | IDE0012 i IDE0014 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj słowo kluczowe Language dla zmiennych lokalnych, parametrów metod i składowych klasy, a nie nazwy typu, dla typów, które mają słowo kluczowe do reprezentowania<br /><br />`false`-Preferuj nazwę typu dla zmiennych lokalnych, parametrów metod i składowych klasy, zamiast słowa kluczowego language |
| **Domyślne dla programu Visual Studio** | `true:silent` |

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

#### <a name="dotnet_style_predefined_type_for_member_access"></a>wstępnie\_zdefiniowany\_Typ\_styludotnet dla\_member_access\_

|||
|-|-|
| **Nazwa reguły** | dotnet_style_predefined_type_for_member_access |
| **Identyfikator reguły** | IDE0013 i IDE0015 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj słowo kluczowe Language dla wyrażeń dostępu do składowych, zamiast nazwy typu, dla typów, które mają słowo kluczowe do reprezentowania<br /><br />`false`-Preferuj nazwę typu dla wyrażeń dostępu do składowych zamiast słowa kluczowego language |
| **Domyślne dla programu Visual Studio** | `true:silent` |

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

### <a name="normalize-modifiers"></a>Preferencje modyfikatora

Reguły stylu w tej sekcji dotyczą preferencji modyfikatora, w tym wymaganie modyfikatorów dostępności, określanie odpowiedniej kolejności sortowania modyfikatora i wymaganie modyfikatora tylko do odczytu.

Te reguły mogą pojawić się w pliku *. editorconfig* w następujący sposób:

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

#### <a name="dotnet_style_require_accessibility_modifiers"></a>dotnet\_style\_require\_accessibility_modifiers

|||
|-|-|
| **Nazwa reguły** | dotnet_style_require_accessibility_modifiers |
| **Identyfikator reguły** | IDE0040 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `always`-Preferuj Modyfikatory dostępności do określenia.<br /><br />`for_non_interface_members`-Preferuj Modyfikatory dostępności, które mają być zadeklarowane z wyjątkiem publicznych elementów członkowskich interfejsu. (Jest to taka sama jak **zawsze** i została dodana do przyszłego sprawdzenia w przypadku C# dodania domyślnych metod interfejsu).<br /><br />`never`-Nie Preferuj modyfikatorów dostępności, które mają być określone.<br /><br />`omit_if_default`-Preferuj Modyfikatory dostępności, chyba że są modyfikatorem domyślnym. |
| **Domyślne dla programu Visual Studio** | `for_non_interface_members:silent` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.5 |

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

#### <a name="csharp_preferred_modifier_order"></a>csharp_preferred_modifier_order

|||
|-|-|
| **Nazwa reguły** | csharp_preferred_modifier_order |
| **Identyfikator reguły** | IDE0036 |
| **Odpowiednie języki** | C# |
| **Wartości** | Co najmniej jeden C# modyfikator, taki jak `public`, `private`, i`protected` |
| **Domyślne dla programu Visual Studio** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.5 |

- Gdy ta reguła jest ustawiona na listę modyfikatorów, Preferuj określoną kolejność.
- Gdy ta reguła zostanie pominięta z pliku, nie Preferuj kolejności modyfikatorów.

Przykłady kodu:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

#### <a name="visual_basic_preferred_modifier_order"></a>visual_basic_preferred_modifier_order

|||
|-|-|
| **Nazwa reguły** | visual_basic_preferred_modifier_order |
| **Identyfikator reguły** | IDE0036 |
| **Odpowiednie języki** | Visual Basic |
| **Wartości** | Co najmniej jeden modyfikator Visual Basic, taki jak `Partial`, `Private`, i`Public` |
| **Domyślne dla programu Visual Studio** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.5 |

- Gdy ta reguła jest ustawiona na listę modyfikatorów, Preferuj określoną kolejność.
- Gdy ta reguła zostanie pominięta z pliku, nie Preferuj kolejności modyfikatorów.

Przykłady kodu:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|||
|-|-|
| **Nazwa reguły** | dotnet_style_readonly_field |
| **Identyfikator reguły** | IDE0044 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj pola, które powinny być oznaczone `readonly` jakoC#() `ReadOnly` lub (Visual Basic), jeśli są tylko kiedykolwiek przypisywać wbudowane lub wewnątrz konstruktora<br /><br />`false`-Określ brak preferencji dla pól, które powinny być oznaczone `readonly` znakami ( `ReadOnly` C#) lub (Visual Basic) |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,7 |

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

Reguły stylu w tej sekcji dotyczą preferencji nawiasów, w tym użycia nawiasów dla arytmetycznych, relacyjnych i innych operatorów binarnych.

Te reguły mogą pojawić się w pliku *. editorconfig* w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>\_nawiasy\_styludotnet\_wbinary_operatorsarytmetycznym\_\_

|||
|-|-|
| **Nazwa reguły** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **Identyfikator reguły** | IDE0047 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `always_for_clarity`— Preferuj nawiasy, aby wyjaśnić pierwszeństwo`*`operatorów `/`arytmetycznych `+`( `-` `%`, `<<`,,, `^`, `|`, `>>` `&`,,)<br /><br />`never_if_unnecessary`-Preferuj nie zawierać nawiasów, gdy operator arytmetyczny`*`( `/` `%`, `>>` `+` `-`,,, `<<`,, `&` `^`,, `|`,) pierwszeństwo jest oczywiste |
| **Domyślne dla programu Visual Studio** | `always_for_clarity:silent` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.8 |

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

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>\_nawiasy\_styludotnet\_wbinary_operatorsrelacyjnym\_\_

|||
|-|-|
| **Nazwa reguły** | dotnet_style_parentheses_in_relational_binary_operators |
| **Identyfikator reguły** | IDE0047 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `always_for_clarity`— Preferuj nawiasy, aby wyjaśnić pierwszeństwo`>`operatorów relacyjnych `>=`( `is`, `as` `==` `<`, `<=` `!=`,,,,)<br /><br />`never_if_unnecessary`-Preferuj nie zawierać nawiasów, gdy pierwszeństwo operatorów`>`relacyjnych `<=`( `>=`, `is` `==` `<` `as` `!=`,,,,,) jest oczywiste |
| **Domyślne dla programu Visual Studio** | `always_for_clarity:silent` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.8 |

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

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>\_nawiasy\_styludotnet\_w innychbinary_operators\_\_

|||
|-|-|
| **Nazwa reguły** | dotnet_style_parentheses_in_other_binary_operators |
| **Identyfikator reguły** | IDE0047 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `always_for_clarity`-Preferuj nawiasy, aby wyjaśnić inny priorytet binarny `||`( `??``&&`,,)<br /><br />`never_if_unnecessary`-Preferuj nie zawierać nawiasów, gdy pierwszeństwo operatora binarnego `||`( `??``&&`,,) jest oczywiste |
| **Domyślne dla programu Visual Studio** | `always_for_clarity:silent` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.8 |

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

#### <a name="dotnet_style_parentheses_in_other_operators"></a>dotnet\_style\_parentheses\_in\_other_operators

|||
|-|-|
| **Nazwa reguły** | dotnet_style_parentheses_in_other_operators |
| **Identyfikator reguły** | IDE0047 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `always_for_clarity`-Preferuj nawiasy, aby wyjaśnić pierwszeństwo operatorów<br /><br />`never_if_unnecessary`-Preferuj nie zawierać nawiasów, gdy pierwszeństwo operatora jest oczywiste |
| **Domyślne dla programu Visual Studio** | `never_if_unnecessary:silent` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.8 |

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

### <a name="expression-level-preferences"></a>Preferencje poziomu wyrażenia

Reguły stylu w tej sekcji dotyczą preferencji na poziomie wyrażenia, w tym używania inicjatorów obiektów, inicjatorów kolekcji, jawnych lub wywnioskowanych nazw krotek oraz wywnioskowanych typów anonimowych.

Te reguły mogą pojawić się w pliku *. editorconfig* w następujący sposób:

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
dotnet_style_prefer_compound_assignment = true:suggestion
```

#### <a name="dotnet_style_object_initializer"></a>dotnet\_style\_object_initializer

|||
|-|-|
| **Nazwa reguły** | dotnet_style_object_initializer |
| **Identyfikator reguły** | IDE0017 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj obiekty do zainicjowania przy użyciu inicjatorów obiektów, gdy jest to możliwe<br /><br />`false`-Preferuj obiekty, które *nie* mogą być inicjowane przy użyciu inicjatorów obiektów |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_collection_initializer"></a>dotnet\_style\_collection_initializer

|||
|-|-|
| **Nazwa reguły** | dotnet_style_collection_initializer |
| **Identyfikator reguły** | IDE0028 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj kolekcje do zainicjowania przy użyciu inicjatorów kolekcji, gdy jest to możliwe<br /><br />`false`-Preferuj kolekcje, których *nie* można zainicjować przy użyciu inicjatorów kolekcji |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_explicit_tuple_names"></a>jawny\_\_tuple_namesstylu\_dotnet

|||
|-|-|
| **Nazwa reguły** | dotnet_style_explicit_tuple_names |
| **Identyfikator reguły** | IDE0033 |
| **Odpowiednie języki** | C#7.0 + i Visual Basic 15 + |
| **Wartości** | `true`-Preferuj nazwy krotek do ItemX właściwości<br /><br />`false`-Preferuj właściwości ItemX do nazw krotek |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>styl\_dotnet\_Preferuj\_tuple_nameswnioskowane\_

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_inferred_tuple_names |
| **Identyfikator reguły** | IDE0037 |
| **Odpowiednie języki** | C#7.1 + i Visual Basic 15 + |
| **Wartości** | `true`-Preferuj wywnioskowane nazwy elementów krotki<br /><br />`false`-Preferuj jawne nazwy elementów krotki |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2017 wersja 15.6 |

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

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>styl\_dotnet\_Preferuj\_wywnioskowany\_typanonimowy\_member_names\_

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **Identyfikator reguły** | IDE0037 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj wywnioskowane nazwy anonimowych elementów członkowskich typu<br /><br />`false`-Preferuj jawne nazwy anonimowych elementów członkowskich typu |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2017 wersja 15.6 |

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

#### <a name="dotnet_style_prefer_auto_properties"></a>styl\_dotnet\_Preferuj\_właściwościautoproperties\_

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_auto_properties |
| **Identyfikator reguły** | IDE0032 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj właściwości autoproperties względem właściwości z prywatnymi polami zapasowymi<br /><br />`false`-Preferuj właściwości z prywatnymi polami zapasowymi przy użyciu właściwości autoproperties |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,7 |

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

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>\_preferowany\_styldotnet\_to sprawdzeniewartościnull\_względem\_metody równości\_odwołań\_\_\_

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **Identyfikator reguły** | IDE0041 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj przy użyciu sprawdzenia wartości null z dopasowaniem do wzorca`object.ReferenceEquals`<br /><br />`false`-Preferuj `object.ReferenceEquals` w przypadku sprawdzenia wartości null z dopasowaniem do wzorca |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,7 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>dotnet\_style\_prefer\_conditional\_expression\_over_assignment

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_conditional_expression_over_assignment |
| **Identyfikator reguły** | IDE0045 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj przypisania za pomocą elementu Trzyelementowy w instrukcji if-else<br /><br />`false`-Preferuj przypisania z instrukcją if-else w przypadku elementu "Trzyelementowy" |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.8 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>dotnet\_style\_prefer\_conditional\_expression\_over_return

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_conditional_expression_over_return |
| **Identyfikator reguły** | IDE0046 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj instrukcje Return, aby używać elementu Trzyelementowy w instrukcji if-else<br /><br />`false`-Preferuj instrukcje Return, aby użyć instrukcji if-else w przypadku elementu "Trzyelementowy" |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.8 |

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

#### <a name="dotnet_style_prefer_compound_assignment"></a>styl\_dotnet\_Preferujprzypisanie\_złożone\_

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_compound_assignment |
| **Identyfikator reguły** | IDE0054 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj wyrażenia [złożonego przypisania](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment)<br /><br />`false`-Nie Preferuj wyrażeń przypisania złożonego |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// dotnet_style_prefer_compound_assignment = true
x += 1;

// dotnet_style_prefer_compound_assignment = false
x = x + 1;
```

```vb
' dotnet_style_prefer_compound_assignment = true
x += 1

' dotnet_style_prefer_compound_assignment = false
x = x + 1
```

### <a name="null-checking-preferences"></a>Preferencje sprawdzania wartości null

Reguły stylu w tej sekcji dotyczą preferencji sprawdzania wartości null.

Te reguły mogą pojawić się w pliku *. editorconfig* w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

#### <a name="dotnet_style_coalesce_expression"></a>dotnet\_style\_coalesce_expression

|||
|-|-|
| **Nazwa reguły** | dotnet_style_coalesce_expression |
| **Identyfikator reguły** | IDE0029 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`-Preferuj wyrażenia łączenia wartości null do sprawdzania operatora Trzyelementowy<br /><br />`false`-Preferuj sprawdzanie łączenia operatora Trzyelementowy z wyrażeniami łączącymi wartości null |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_null_propagation"></a>dotnet\_style\_null_propagation

|||
|-|-|
| **Nazwa reguły** | dotnet_style_null_propagation |
| **Identyfikator reguły** | IDE0031 |
| **Odpowiednie języki** | C#6.0 + i Visual Basic 14 + |
| **Wartości** | `true`-Preferuj użycie operatora warunkowego null, gdy jest to możliwe<br /><br />`false`-Woli użyć sprawdzania wartości null w przypadku, gdy jest to możliwe |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

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

## <a name="net-code-quality-settings"></a>Ustawienia jakości kodu platformy .NET

Reguły jakości w tej sekcji dotyczą zarówno C# kodu, jak i Visual Basic. Są one używane do konfigurowania analizatorów kodu wbudowanych w zintegrowane środowisko programistyczne (IDE) programu Visual Studio. Informacje o konfigurowaniu analizatorów FxCop za pomocą pliku EditorConfig można znaleźć w temacie [Configure FxCop analizators](../code-quality/configure-fxcop-analyzers.md).

- [Preferencje parametrów](#parameter-preferences)
  - parametry\_nieużywanej\_\_jakości\_kodu dotnet

### <a name="parameter-preferences"></a>Preferencje parametrów

Reguły jakości w tej sekcji dotyczą parametrów metody.

Te reguły mogą pojawić się w pliku *. editorconfig* w następujący sposób:

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>parametry\_nieużywanej\_\_jakości\_kodu dotnet

|||
|-|-|
| **Nazwa reguły** | dotnet_code_quality_unused_parameters |
| **Identyfikator reguły** | IDE0060 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `all`-Oflaguj metody z dowolnym ułatwieniami dostępu, które zawierają nieużywane parametry<br /><br />`non_public`-Oflaguj tylko metody niepubliczne, które zawierają nieużywane parametry |
| **Domyślne dla programu Visual Studio** | `all:suggestion` |

Przykłady kodu:

```csharp
// dotnet_code_quality_unused_parameters = all:suggestion
public int GetNum() { return 1; }

// dotnet_code_quality_unused_parameters = non_public:suggestion
public int GetNum(int arg1) { return 1; }
```

```vb
' dotnet_code_quality_unused_parameters = all:suggestion
Public Function GetNum()
    Return 1
End Function

' dotnet_code_quality_unused_parameters = non_public:suggestion
Public Function GetNum(arg1 As Integer)
    Return 1
End Function
```

## <a name="c-code-style-settings"></a>C#Ustawienia stylu kodu

Reguły stylu w tej sekcji mają zastosowanie tylko do C# programu.

- [Typy niejawne i jawne](#implicit-and-explicit-types)
  - CSharp\_—\_WARIANCJA\_stylu dla\_skompilowanej\_in_types
  - CSharp\_—\_WARIANCJA\_stylu gdy\_typis_apparent\_
  - CSharp\_style\_var_elsewhere
- [Elementy członkowskie z wyrażeniem w treści](#expression-bodied-members)
  - csharp\_style\_expression\_bodied_methods
  - csharp\_style\_expression\_bodied_constructors
  - csharp\_style\_expression\_bodied_operators
  - csharp\_style\_expression\_bodied_properties
  - \_wyrażenie\_CSharpstyle\_bodied_indexers
  - csharp\_style\_expression\_bodied_accessors
  - \_wyrażenie\_CSharpstyle\_bodied_lambdas
  - wyrażenie\_\_styluCSharplocal_functions\_\_
- [Dopasowanie do wzorca](#pattern-matching)
  - dopasowanie\_wzorcastylu\_CSharpzcast_check\_\_\_\_\_
  - dopasowanie\_\_wzorcastyluCSharp\_wporównaniu\_z\_null_check\_\_
- [Wbudowane deklaracje zmiennych](#inlined-variable-declarations)
  - csharp\_style\_inlined\_variable_declaration
- [Preferencje poziomu wyrażenia](#c-expression-level-preferences)
  - CSharp\_Preferuj\_prostedefault_expression\_
- [Preferencje sprawdzania wartości "null"](#c-null-checking-preferences)
  - csharp\_style\_throw_expression
  - csharp\_style\_conditional\_delegate_call
- [Preferencje bloku kodu](#code-block-preferences)
  - CSharp\_prefer_braces
- [Nieużywane preferencje wartości](#unused-value-preferences)
  - \_nieużywane\_wyrażeniewartościw\_styluCSharpstatement_preference\_\_
  - \_nieużywanawartość\_\_CSharp\_stylu assignment_preference
- [Preferencje indeksu i zakresu](#index-and-range-preferences)
  - styl\_CSharp\_Preferujindex_operator\_
  - styl\_CSharp\_Preferujrange_operator\_
- [Różne preferencje](#miscellaneous-preferences)
  - dekonstrukcja\_\_variable_declaration\_w stylu CSharp
  - csharp\_style\_pattern\_local\_over\_anonymous_function
  - CSharp\_przy\_użyciu\_umieszczania dyrektywy
  - CSharp\_Preferuj\_statycznelocal_function\_
  - CSharp\_Preferuj\_prosteusing_statement\_
  - styl\_CSharp\_Preferujswitch_expression\_

### <a name="implicit-and-explicit-types"></a>Typy niejawne i jawne

Reguły stylu w tej sekcji dotyczą użycia słowa kluczowego [var](/dotnet/csharp/language-reference/keywords/var) zamiast typu jawnego w deklaracji zmiennej. Tę regułę można zastosować osobno do typów wbudowanych, gdy typ jest widoczny, i w innym miejscu.

Przykładowy plik *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharp_style_var_for_built_in_types"></a>CSharp\_—\_WARIANCJA\_stylu dla\_skompilowanej\_in_types

|||
|-|-|
| **Nazwa reguły** | csharp_style_var_for_built_in_types |
| **Identyfikator reguły** | IDE0007 i IDE0008 |
| **Odpowiednie języki** | C#  |
| **Wartości** | `true`-Preferuj `var` służy do deklarowania zmiennych przy użyciu wbudowanych typów systemu, takich jak`int`<br /><br />`false`-Preferuj jawny typ `var` do deklarowania zmiennych przy użyciu wbudowanych typów systemu, takich jak`int` |
| **Domyślne dla programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>CSharp\_—\_WARIANCJA\_stylu gdy\_typis_apparent\_

|||
|-|-|
| **Nazwa reguły** | csharp_style_var_when_type_is_apparent |
| **Identyfikator reguły** | IDE0007 i IDE0008 |
| **Odpowiednie języki** | C#  |
| **Wartości** | `true`-Preferuj `var` , gdy typ jest już wymieniony po prawej stronie wyrażenia deklaracji<br /><br />`false`-Preferuj jawny typ `var` w przypadku, gdy typ jest już wymieniony po prawej stronie wyrażenia deklaracji |
| **Domyślne dla programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>CSharp\_style\_var_elsewhere

|||
|-|-|
| **Nazwa reguły** | csharp_style_var_elsewhere |
| **Identyfikator reguły** | IDE0007 i IDE0008 |
| **Odpowiednie języki** | C#  |
| **Wartości** | `true`— Preferuj `var` przez jawne typy we wszystkich przypadkach, chyba że zostaną zastąpione przez inną regułę w stylu kodu<br /><br />`false`-Preferuj jawny typ `var` we wszystkich przypadkach, chyba że jest zastępowany przez inną regułę w stylu kodu |
| **Domyślne dla programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>Składowe z wyrażeniem w treści

Reguły stylu w tej sekcji dotyczą użycia [składowych wyrażeń](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) , gdy logika składa się z jednego wyrażenia. Ta reguła może być stosowana do metod, konstruktorów, operatorów, właściwości, indeksatorów i metody dostępu.

Przykładowy plik *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
```

#### <a name="csharp_style_expression_bodied_methods"></a>csharp\_style\_expression\_bodied_methods

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_methods |
| **Identyfikator reguły** | IDE0022 |
| **Odpowiednie języki** | C# 6.0+  |
| **Wartości** | `true`-Preferuj treści wyrażenia dla metod<br /><br />`when_on_single_line`-Preferuj treści wyrażenia dla metod, gdy będą one pojedynczym wierszem<br /><br />`false`-Preferuj treści bloku dla metod |
| **Domyślne dla programu Visual Studio** | `false:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>csharp\_style\_expression\_bodied_constructors

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_constructors |
| **Identyfikator reguły** | IDE0021 |
| **Odpowiednie języki** | C#7.0 + |
| **Wartości** | `true`-Preferuj treści wyrażenia dla konstruktorów<br /><br />`when_on_single_line`-Preferuj treści wyrażeń dla konstruktorów, gdy będą one jednym wierszem<br /><br />`false`-Preferuj treści bloku dla konstruktorów |
| **Domyślne dla programu Visual Studio** | `false:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>csharp\_style\_expression\_bodied_operators

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_operators |
| **Identyfikator reguły** | IDE0023 i IDE0024 |
| **Odpowiednie języki** | C#7.0 + |
| **Wartości** | `true`-Preferuj treści wyrażenia dla operatorów<br /><br />`when_on_single_line`-Preferowane treści wyrażenia dla operatorów, gdy będą one pojedynczym wierszem<br /><br />`false`-Preferuj treści bloku dla operatorów |
| **Domyślne dla programu Visual Studio** | `false:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharp_style_expression_bodied_properties"></a>csharp\_style\_expression\_bodied_properties

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_properties |
| **Identyfikator reguły** | IDE0025 |
| **Odpowiednie języki** | C#7.0 + |
| **Wartości** | `true`-Preferuj treści wyrażenia dla właściwości<br /><br />`when_on_single_line`— Preferuj treści wyrażenia dla właściwości, gdy będą one pojedynczym wierszem<br /><br />`false`-Preferuj treści bloku dla właściwości |
| **Domyślne dla programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>\_wyrażenie\_CSharpstyle\_bodied_indexers

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_indexers |
| **Identyfikator reguły** | IDE0026 |
| **Odpowiednie języki** | C#7.0 + |
| **Wartości** | `true`-Preferuj treści wyrażeń dla indeksatorów<br /><br />`when_on_single_line`-Preferuj treści wyrażeń dla indeksatorów, gdy będą one jednym wierszem<br /><br />`false`-Preferuj treści bloku dla indeksatorów |
| **Domyślne dla programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>csharp\_style\_expression\_bodied_accessors

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_accessors |
| **Identyfikator reguły** | IDE0027 |
| **Odpowiednie języki** | C#7.0 + |
| **Wartości** | `true`-Preferuj treści wyrażenia dla metod dostępu<br /><br />`when_on_single_line`-Preferuj treści wyrażenia dla metod dostępu, gdy będą one pojedynczym wierszem<br /><br />`false`-Preferuj treści bloku dla metod dostępu |
| **Domyślne dla programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>\_wyrażenie\_CSharpstyle\_bodied_lambdas

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_lambdas |
| **Identyfikator reguły** | IDE0053 |
| **Wartości** | `true`-Preferuj treści wyrażeń dla wyrażeń lambda<br /><br />`when_on_single_line`-Preferuj treści wyrażeń dla wyrażeń lambda, gdy będą one pojedynczym wierszem<br /><br />`false`-Preferuj treści bloku dla wyrażeń lambda |
| **Domyślne dla programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>wyrażenie\_\_styluCSharplocal_functions\_\_

Począwszy od C# 7,0, C# obsługuje [funkcje lokalne](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Funkcje lokalne są prywatnymi metodami typu, które są zagnieżdżone w innym elemencie członkowskim.

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_local_functions |
| **Identyfikator reguły** | IDE0061 |
| **Odpowiednie języki** | C#7.0 + |
| **Wartości** | `true`-Preferuj treści wyrażeń dla funkcji lokalnych<br /><br />`when_on_single_line`-Preferuj treści wyrażeń dla funkcji lokalnych, gdy będą one jednym wierszem<br /><br />`false`-Preferuj treści bloku dla funkcji lokalnych |
| **Domyślne dla programu Visual Studio** | `false:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_local_functions = true
void M()
{
    Hello();
    void Hello() => Console.WriteLine("Hello");
}

// csharp_style_expression_bodied_local_functions = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

### <a name="pattern-matching"></a>Dopasowanie do wzorca

Reguły stylu w tej sekcji dotyczą użycia [dopasowania wzorca](/dotnet/csharp/pattern-matching) w C#.

Przykładowy plik *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>dopasowanie\_wzorcastylu\_CSharpzcast_check\_\_\_\_\_

|||
|-|-|
| **Nazwa reguły** | csharp_style_pattern_matching_over_is_with_cast_check |
| **Identyfikator reguły** | IDE0020 |
| **Odpowiednie języki** | C#7.0 + |
| **Wartości** | `true`-Preferuj Dopasowywanie wzorców zamiast `is` wyrażeń z rzutowania typu<br /><br />`false`-Preferuj `is` wyrażenia z rzutowania typu zamiast dopasowania do wzorca |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>dopasowanie\_\_wzorcastyluCSharp\_wporównaniu\_z\_null_check\_\_

|||
|-|-|
| **Nazwa reguły** | csharp_style_pattern_matching_over_as_with_null_check |
| **Identyfikator reguły** | IDE0019 |
| **Odpowiednie języki** | C#7.0 + |
| **Wartości** | `true`-Preferuj Dopasowywanie wzorców zamiast `as` wyrażeń z sprawdzeniami null, aby określić, czy coś jest określonego typu<br /><br />`false`-Preferuj `as` wyrażenia z kontrolami null zamiast dopasowywania do wzorca, aby określić, czy coś jest określonego typu |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>Wbudowane deklaracje zmiennych

Ta zasada stylu ma wpływ `out` na to, czy zmienne są zadeklarowane wewnętrznie, czy nie. Począwszy od C# 7, można zadeklarować [zmienną out na liście argumentów wywołania metody](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), a nie w oddzielnej deklaracji zmiennej.

#### <a name="csharp_style_inlined_variable_declaration"></a>csharp\_style\_inlined\_variable_declaration

|||
|-|-|
| **Nazwa reguły** | csharp_style_inlined_variable_declaration |
| **Identyfikator reguły** | IDE0018 |
| **Odpowiednie języki** | C#7.0 + |
| **Wartości** | `true`-Preferuj `out` zmienne, które mają być zadeklarowane jako wbudowane na liście argumentów wywołania metody, jeśli jest to możliwe<br /><br />`false`-Preferuj `out` zmienne, które mają być zadeklarowane przed wywołaniem metody |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Przykładowy plik *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="c-expression-level-preferences"></a>C#Preferencje poziomu wyrażenia

Reguły stylu w tej sekcji dotyczą preferencji na poziomie wyrażenia.

Przykładowy plik *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>CSharp\_Preferuj\_prostedefault_expression\_

Ta zasada stylu ma wpływ na używanie [ `default` literału dla wyrażeń wartości domyślnych](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) , gdy kompilator może wywnioskować typ wyrażenia.

|||
|-|-|
| **Nazwa reguły** | csharp_prefer_simple_default_expression |
| **Identyfikator reguły** | IDE0034 |
| **Odpowiednie języki** | C# 7.1+  |
| **Wartości** | `true`— Preferuj `default``default(T)`<br /><br />`false`— Preferuj `default(T)``default` |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>C#Preferencje sprawdzania wartości null

Te reguły stylu `null` dotyczą składni wokół sprawdzania, w tym używania `throw` wyrażeń lub `throw` instrukcji, oraz czy należy wykonać sprawdzenie wartości null lub użyć operatora łączenia warunkowego (`?.`) podczas wywoływania elementu [ wyrażenie lambda](/dotnet/csharp/lambda-expressions).

Przykładowy plik *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>csharp\_style\_throw_expression

|||
|-|-|
| **Nazwa reguły** | csharp_style_throw_expression |
| **Identyfikator reguły** | IDE0016 |
| **Odpowiednie języki** | C#7.0 + |
| **Wartości** | `true`-Woli używać `throw` wyrażeń `throw` zamiast instrukcji<br /><br />`false`-Woli użyć `throw` instrukcji `throw` zamiast wyrażeń |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>csharp\_style\_conditional\_delegate_call

|||
|-|-|
| **Nazwa reguły** | csharp_style_conditional_delegate_call |
| **Identyfikator reguły** | IDE0041 |
| **Odpowiednie języki** | C# 6.0+  |
| **Wartości** | `true`-Odwołaj się do użycia operatora łączenia warunkowego`?.`() podczas wywoływania wyrażenia lambda, zamiast przeprowadzania sprawdzenia wartości null<br /><br />`false`-Woli wykonać sprawdzenie wartości null przed wywołaniem wyrażenia lambda zamiast przy użyciu operatora łączenia warunkowego (`?.`) |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Preferencje bloku kodu

Ta reguła stylu dotyczy użycia nawiasów klamrowych `{ }` do otaczania bloków kodu.

Przykładowy plik *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharp_prefer_braces"></a>CSharp\_Preferuj\_nawiasy klamrowe

|||
|-|-|
| **Nazwa reguły** | csharp_prefer_braces |
| **Identyfikator reguły** | IDE0011 |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`-Preferuj nawiasy klamrowe nawet dla jednego wiersza kodu<br /><br />`false`-Preferuj brak nawiasów klamrowych, jeśli są dozwolone |
| **Domyślne dla programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

### <a name="unused-value-preferences"></a>Nieużywane preferencje wartości

Te reguły stylu dotyczą nieużywanych wyrażeń i przypisań wartości.

Przykładowy plik *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_unused_value_expression_statement_preference = discard_variable:silent
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
```

#### <a name="csharp_style_unused_value_expression_statement_preference"></a>csharp_style_unused_value_expression_statement_preference

|||
|-|-|
| **Nazwa reguły** | csharp_style_unused_value_expression_statement_preference |
| **Identyfikator reguły** | IDE0058 |
| **Odpowiednie języki** | C# |
| **Wartości** | `discard_variable`-Preferuj, aby przypisać nieużywane wyrażenie do [odrzucenia](/dotnet/csharp/discards) <br /><br />`unused_local_variable`-Preferuj, aby przypisać nieużywane wyrażenie do zmiennej lokalnej |
| **Domyślne dla programu Visual Studio** | `discard_variable:silent` |

Przykłady kodu:

```csharp
// Original code:
System.Convert.ToInt32("35");

// After code fix for IDE0058:

// csharp_style_unused_value_expression_statement_preference = discard_variable
_ = System.Convert.ToInt32("35");

// csharp_style_unused_value_expression_statement_preference = unused_local_variable
var unused = Convert.ToInt32("35");
```

#### <a name="csharp_style_unused_value_assignment_preference"></a>csharp_style_unused_value_assignment_preference

|||
|-|-|
| **Nazwa reguły** | csharp_style_unused_value_assignment_preference |
| **Identyfikator reguły** | IDE0059 |
| **Odpowiednie języki** | C# |
| **Wartości** | `discard_variable`-Preferuj użycie odrzucenia [](/dotnet/csharp/discards) podczas przypisywania wartości, która nie jest używana<br /><br />`unused_local_variable`-Woli użyć zmiennej lokalnej przy przypisywaniu wartości, która nie jest używana |
| **Domyślne dla programu Visual Studio** | `discard_variable:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_unused_value_assignment_preference = discard_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    _ = wordCount.TryGetValue(searchWord, out var count);
    return count;
}

// csharp_style_unused_value_assignment_preference = unused_local_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    var unused = wordCount.TryGetValue(searchWord, out var count);
    return count;
}
```

### <a name="index-and-range-preferences"></a>Preferencje indeksu i zakresu

Te reguły stylu dotyczą użycia operatorów indeks i zakres, które są dostępne w C# 8,0 i nowszych.

Przykładowy plik *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>styl\_CSharp\_Preferujindex_operator\_

|||
|-|-|
| **Nazwa reguły** | csharp_style_prefer_index_operator |
| **Identyfikator reguły** | IDE0056 |
| **Odpowiednie języki** | C#8.0 + |
| **Wartości** | `true`-Woli użyć `^` operatora podczas obliczania indeksu na końcu kolekcji<br /><br />`false`-Nie woli używać `^` operatora podczas obliczania indeksu na końcu kolekcji |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_prefer_index_operator = true
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[^1];

// csharp_style_prefer_index_operator = false
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[names.Length - 1];
```

#### <a name="csharp_style_prefer_range_operator"></a>styl\_CSharp\_Preferujrange_operator\_

|||
|-|-|
| **Nazwa reguły** | csharp_style_prefer_range_operator |
| **Identyfikator reguły** | IDE0057 |
| **Odpowiednie języki** | C#8.0 + |
| **Wartości** | `true`-Woli użyć operatora `..` zakresu podczas wyodrębniania "wycinka" kolekcji<br /><br />`false`-Nie Preferuj do używania operatora `..` zakresu podczas wyodrębniania "wycinka" kolekcji |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_prefer_range_operator = true
string sentence = "the quick brown fox";
var sub = sentence[0..^4];

// csharp_style_prefer_range_operator = false
string sentence = "the quick brown fox";
var sub = sentence.Substring(0, sentence.Length - 4);
```

### <a name="miscellaneous-preferences"></a>Różne preferencje

Ta sekcja zawiera różne reguły stylów.

Przykładowy plik *. editorconfig* :

```ini
# CSharp code style settings:
[*.cs]
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_using_directive_placement = outside_namespace:silent
csharp_prefer_static_local_function = true:suggestion
csharp_prefer_simple_using_statement = true:suggestion
csharp_style_prefer_switch_expression = true:suggestion
```

#### <a name="csharp_style_deconstructed_variable_declaration"></a>dekonstrukcja\_\_variable_declaration\_w stylu CSharp

|||
|-|-|
| **Nazwa reguły** | csharp_style_deconstructed_variable_declaration |
| **Identyfikator reguły** | IDE0042 |
| **Odpowiednie języki** | C#7.0 + |
| **Wartości** | `true`-Preferuj niekonstruowaną deklarację zmiennej<br /><br />`false`-Nie Preferuj dekonstrukcji w deklaracjach zmiennych |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

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

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>csharp\_style\_pattern\_local\_over\_anonymous_function

Począwszy od C# 7,0, C# obsługuje [funkcje lokalne](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Funkcje lokalne są prywatnymi metodami typu, które są zagnieżdżone w innym elemencie członkowskim.

|||
|-|-|
| **Nazwa reguły** | csharp_style_pattern_local_over_anonymous_function |
| **Identyfikator reguły** | IDE0039 |
| **Odpowiednie języki** | C#7.0 + |
| **Wartości** | `true`-Preferuj funkcje lokalne w porównaniu z funkcjami anonimowymi<br /><br />`false`-Preferuj anonimowe funkcje w ramach funkcji lokalnych |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

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

#### <a name="csharp_using_directive_placement"></a>CSharp\_przy\_użyciu directive_placement

|||
|-|-|
| **Nazwa reguły** | csharp_using_directive_placement |
| **Identyfikator reguły** | IDE0065 |
| **Odpowiednie języki** | C# |
| **Wartości** | `outside_namespace`-Preferuj `using` dyrektywy, które mają być umieszczone poza przestrzenią nazw<br /><br />`inside_namespace`-Preferuj `using` dyrektywy do umieszczenia w przestrzeni nazw |
| **Domyślne dla programu Visual Studio** | `outside_namespace:silent` |

Przykłady kodu:

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{
    ...
}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
    ...
}
```

#### <a name="csharp_prefer_static_local_function"></a>CSharp\_Preferuj\_statycznelocal_function\_

|||
|-|-|
| **Nazwa reguły** | csharp_prefer_static_local_function |
| **Identyfikator reguły** | IDE0062 |
| **Odpowiednie języki** | C#8.0 + |
| **Wartości** | `true`-Preferuj funkcje lokalne do oznaczenia`static`<br /><br />`false`-Nie Preferuj funkcji lokalnych do oznaczenia`static` |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_prefer_static_local_function = true
void M()
{
    Hello();
    static void Hello()
    {
        Console.WriteLine("Hello");
    }
}

// csharp_prefer_static_local_function = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

#### <a name="csharp_prefer_simple_using_statement"></a>CSharp\_Preferuj\_prosteusing_statement\_

|||
|-|-|
| **Nazwa reguły** | csharp_prefer_simple_using_statement |
| **Identyfikator reguły** | IDE0063 |
| **Odpowiednie języki** | C#8.0 + |
| **Wartości** | `true`-Woli użyć prostej `using` instrukcji<br /><br />`false`-Nie wolisz używać *prostej* `using` instrukcji |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>styl\_CSharp\_Preferujswitch_expression\_

|||
|-|-|
| **Nazwa reguły** | csharp_style_prefer_switch_expression |
| **Identyfikator reguły** | IDE0066 |
| **Odpowiednie języki** | C#8.0 + |
| **Wartości** | `true`-Preferuj użycie `switch` wyrażenia (wprowadzone z C# 8,0)<br /><br />`false`-Woli użyć [instrukcji switch](/dotnet/csharp/language-reference/keywords/switch) |
| **Domyślne dla programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2019 w wersji 16,2 |

Przykłady kodu:

```csharp
// csharp_style_prefer_switch_expression = true
return x switch
{
    1 => 1 * 1,
    2 => 2 * 2,
    _ => 0,
};

// csharp_style_prefer_switch_expression = false
switch (x)
{
    case 1:
        return 1 * 1;
    case 2:
        return 2 * 2;
    default:
        return 0;
}
```

## <a name="see-also"></a>Zobacz także

- [Konwencje formatowania](editorconfig-formatting-conventions.md)
- [Konwencje nazewnictwa](editorconfig-naming-conventions.md)
- [.NET coding convention ustawienia dla wtyczki EditorConfig](editorconfig-code-style-settings-reference.md)
