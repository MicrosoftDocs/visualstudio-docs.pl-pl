---
title: Konwencje języka .NET dla EditorConfig
ms.date: 03/31/2020
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0c06d6c16082a8300092e36b9bbed126c66f8af4
ms.sourcegitcommit: 334024a43477290ecc610e70c80a0f772787a7d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80528029"
---
# <a name="language-conventions"></a>Konwencje języka

Konwencje języka editorConfig w programie Visual Studio należą do dwóch kategorii: te, które mają zastosowanie do języka Visual Basic i C#oraz te, które są specyficzne dla języka C#. Konwencje języka wpływają na sposób, w jaki używane są różne aspekty języka programowania, na przykład modyfikatory i nawiasy.

> [!TIP]
> - Aby wyświetlić przykłady kodu w preferowanym języku programowania, wybierz go za pomocą selektora języka w prawym górnym rogu okna przeglądarki.
>
>   ![Kontrolka selektora języka kodu](media/code-language-picker.png)
>
> - Użyj łącza **w tym artykule,** aby przejść do różnych sekcji strony.

## <a name="rule-format"></a>Format reguły

Reguły konwencji językowych mają następujący ogólny format:

`option_name = value:severity`

Dla każdej konwencji języka należy określić wartość, która definiuje, czy lub kiedy preferować styl. Wiele reguł akceptuje `true` wartość (preferuj `false` ten styl) lub (nie preferuje tego stylu). Inne reguły akceptują wartości, takie jak `when_on_single_line` lub `never`. Druga część reguły określa [ważność](#severity-levels).

::: moniker range=">=vs-2019"

> [!NOTE]
> Ponieważ konwencje języka są wymuszane przez analizatory, można również ustawić ich ważność przy użyciu domyślnej składni konfiguracji dla analizatorów. Składnia przyjmuje formę `dotnet_diagnostic.<rule ID>.severity = <severity>`, na `dotnet_diagnostic.IDE0040.severity = silent`przykład . Aby uzyskać więcej informacji, zobacz [Ustawianie ważności reguły w pliku EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file).

::: moniker-end

## <a name="severity-levels"></a>Poziomy ważności

Ważność konwencji języka określa poziom, na którym ma być wymuszany ten styl. W poniższej tabeli wymieniono możliwe wartości ważności i ich skutki:

Ważność | Efekt
:------- | ------
`error` | Po naruszeniu tej reguły stylu pokaż błąd kompilatora.
`warning` | Po naruszeniu tej reguły stylu, pokaż ostrzeżenie kompilatora.
`suggestion` | Po naruszeniu tej reguły stylu pokaż ją użytkownikowi jako sugestię. Sugestie są wyświetlane jako trzy szare kropki pod dwoma pierwszymi znakami.
`silent` | Nie pokazuj niczego użytkownikowi, gdy ta reguła zostanie naruszona. Funkcje generowania kodu generują jednak kod w tym stylu. Reguły `silent` z ważnością uczestniczą w oczyszczaniu i pojawiają się w menu **Szybkie akcje i Refaktoryzowania.**
`none` | Nie pokazuj niczego użytkownikowi, gdy ta reguła zostanie naruszona. Funkcje generowania kodu generują jednak kod w tym stylu. Reguły `none` z ważnością nigdy nie są wyświetlane w menu **Szybkie akcje i Refaktoryzowania.** W większości przypadków jest to uważane za "wyłączone" lub "ignorowane".

::: moniker range=">=vs-2019"

## <a name="automatically-configure-code-styles"></a>Automatyczne konfigurowanie stylów kodu

Począwszy od programu Visual Studio 2019 w wersji 16.3, można skonfigurować reguły stylu kodu z menu żarówki [Szybkie akcje](quick-actions.md) po wystąpieniu naruszenia stylu.

Aby zmienić konwencję stylu kodu:

1. Umieść wskaźnik myszy na fali w edytorze, a następnie otwórz wyświetlenie menu żarówki. Wybierz **pozycję Konfiguruj lub wygaszaj problemy** > **Konfigurowanie \<identyfikatora reguły> stylu kodu**.

   ![Konfigurowanie stylu kodu z menu żarówki w programie Visual Studio](media/vs-2019/configure-code-style.png)

2. W tym miejscu wybierz jedną z opcji stylu kodu.

   ![Konfigurowanie ustawienia stylu kodu](media/vs-2019/configure-code-style-setting.png)

   Visual Studio dodaje lub modyfikuje ustawienie konfiguracji w editorconfig pliku, jak pokazano w polu podglądu.

Aby zmienić ważność naruszenia stylu kodu, wykonaj te same czynności, ale wybierz pozycję **Konfiguruj \<identyfikator reguły> ważności** zamiast **Konfigurowania \<identyfikatora reguły> stylu kodu**. Aby uzyskać więcej informacji, zobacz [Automatyczne konfigurowanie ważności reguły](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity).

::: moniker-end

## <a name="net-code-style-settings"></a>Ustawienia stylu kodu .NET

Reguły stylu w tej sekcji mają zastosowanie zarówno do języka C# i Visual Basic.

- ["To." i "Ja".](#this-and-me)
  - kwalifikacje\_\_w\_stylu dotnet for_field
  - kwalifikacje\_\_w\_stylu dotnet for_property
  - kwalifikacje\_\_w\_stylu dotnet for_method
  - kwalifikacje\_\_w\_stylu dotnet for_event
- [Słowa kluczowe języka zamiast nazw typów framework dla odwołań do typów](#language-keywords)
  - Wstępnie\_zdefiniowany\_\_typ\_stylu dotnet dla\_lokalnych\_parameters_members
  - Wstępnie\_zdefiniowany\_\_typ\_stylu dotnet dla\_member_access
- [Preferencje modyfikatora](#normalize-modifiers)
  - styl\_\_dotnet\_wymaga accessibility_modifiers
  - visual\_\_basic\_preferowany modifier_order
  - styl dotnet\_\_tylko\_pole
- [Preferencje nawiasów](#parentheses-preferences)
  - nawiasy\_stylu\_dotnet\_\_w arytmetycznych\_operatorach binarnych\_
  - nawiasy\_stylu\_dotnet\_\_w\_\_innych operatorach binarnych
  - nawiasy\_stylu\_dotnet\_\_w\_innych operatorach
  - nawiasy\_stylu\_dotnet\_\_w\_relacyjnych operatorach binarnych\_
- [Preferencje na poziomie wyrażenia](#expression-level-preferences)
  - object_initializer w\_\_stylu dotnet
  - collection_initializer w\_\_stylu dotnet
  - jawne\_\_tuple_names\_w stylu dotnet
  - styl\_\_dotnet\_preferuje\_wywnioskowane tuple_names
  - \_styl\_dotnet\_preferuje\_\_wywnioskowane typu anonimowego\_member_names
  - styl\_\_dotnet\_\_preferuje właściwości auto
  - \_styl\_dotnet\_\_preferuje\_\_to\_\_sprawdzanie wartości null\_w metodzie równości odwołań
  - \_Styl\_dotnet\_preferuje\_\_wyrażenie warunkowe\_niż przypisanie
  - \_styl\_dotnet\_preferuje\_\_wyrażenie warunkowe\_niż zwracanie
  - styl\_\_dotnet\_\_preferuje przypisanie złożone
- [Preferencje sprawdzania wartości "Null"](#null-checking-preferences)
  - coalesce_expression w\_\_stylu dotnet
  - null_propagation w\_\_stylu dotnet
  - \_styl\_dotnet\_\_preferuje\_\_to\_\_sprawdzanie wartości null\_w metodzie równości odwołań

### <a name="this-and-me-qualifiers"></a><a name="this-and-me"></a>"To." i "Ja". Kwalifikatory

Tę regułę stylu można zastosować do pól, właściwości, metod lub zdarzeń. Wartość **true** oznacza wolą symbol kodu być poprzedzone `this.` w `Me.` języku C# lub visual basic. Wartość **false** oznacza wolą element kodu _nie_ być `this.` poprzedzone lub `Me.`.

Reguły te mogą pojawić się w pliku *.editorconfig* w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>kwalifikacje\_\_w\_stylu dotnet for_field

|||
|-|-|
| **Nazwa reguły** | dotnet_style_qualification_for_field |
| **Identyfikator zasady** | IDE0003 i IDE0009 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj pola, `this.` które mają `Me.` być poprzedzone w języku C# lub visual basic<br /><br />`false`- Preferuj _pola,_ aby `this.` nie były poprzedzone`Me.` |
| **Domyślna wartość programu Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_property"></a>kwalifikacje\_\_w\_stylu dotnet for_property

|||
|-|-|
| **Nazwa reguły** | dotnet_style_qualification_for_property |
| **Identyfikator zasady** | IDE0003 i IDE0009 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj właściwości, które `this.` mają być `Me.` poprzedzone w języku C# lub visual basic<br /><br />`false`- Preferuj _właściwości,_ które `this.` nie są poprzedzone lub`Me.` |
| **Domyślna wartość programu Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_method"></a>kwalifikacje\_\_w\_stylu dotnet for_method

|||
|-|-|
| **Nazwa reguły** | dotnet_style_qualification_for_method |
| **Identyfikator zasady** | IDE0003 i IDE0009 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj metody, `this.` które mają `Me.` być poprzedzone w języku C# lub visual basic.<br /><br />`false`- Preferuj _metody,_ aby `this.` `Me.`nie być poprzedzone lub . |
| **Domyślna wartość programu Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_event"></a>kwalifikacje\_\_w\_stylu dotnet for_event

|||
|-|-|
| **Nazwa reguły** | dotnet_style_qualification_for_event |
| **Identyfikator zasady** | IDE0003 i IDE0009 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj zdarzenia, `this.` które mają `Me.` być poprzedzone w języku C# lub visual basic.<br /><br />`false`- Preferuj _wydarzenia,_ aby `this.` `Me.`nie były poprzedzone lub . |
| **Domyślna wartość programu Visual Studio** | `false:silent` |

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

### <a name="language-keywords-instead-of-framework-type-names-for-type-references"></a><a name="language-keywords"></a>Słowa kluczowe języka zamiast nazw typów framework dla odwołań do typów

Tę regułę stylu można zastosować do zmiennych lokalnych, parametrów metody i elementów członkowskich klasy lub jako osobnej reguły, aby wpisać wyrażenia dostępu do elementów członkowskich. Wartość **true** oznacza preferować słowo kluczowe `int` języka `Integer`(na przykład lub ) zamiast `Int32`nazwy typu (na przykład) dla typów, które mają słowo kluczowe do reprezentowania ich. Wartość **false** oznacza preferować nazwę typu zamiast słowa kluczowego języka.

Reguły te mogą pojawić się w pliku *.editorconfig* w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>Wstępnie\_zdefiniowany\_\_typ\_stylu dotnet dla\_lokalnych\_parameters_members

|||
|-|-|
| **Nazwa reguły** | dotnet_style_predefined_type_for_locals_parameters_members |
| **Identyfikator zasady** | IDE0012 i IDE0014 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj słowo kluczowe języka dla zmiennych lokalnych, parametrów metody i członków klasy, zamiast nazwy typu, dla typów, które mają słowo kluczowe do ich reprezentowania<br /><br />`false`- Preferuj nazwę typu dla zmiennych lokalnych, parametrów metody i członków klasy, zamiast słowa kluczowego języka |
| **Domyślna wartość programu Visual Studio** | `true:silent` |

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

#### <a name="dotnet_style_predefined_type_for_member_access"></a>Wstępnie\_zdefiniowany\_\_typ\_stylu dotnet dla\_member_access

|||
|-|-|
| **Nazwa reguły** | dotnet_style_predefined_type_for_member_access |
| **Identyfikator zasady** | IDE0013 i IDE0015 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj słowo kluczowe języka dla wyrażeń dostępu członka, zamiast nazwy typu, dla typów, które mają słowo kluczowe do reprezentowania ich<br /><br />`false`- Preferuj nazwę typu dla wyrażeń dostępu członka, zamiast słowa kluczowego języka |
| **Domyślna wartość programu Visual Studio** | `true:silent` |

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

### <a name="modifier-preferences"></a><a name="normalize-modifiers"></a>Preferencje modyfikatora

Reguły stylu w tej sekcji dotyczą preferencji modyfikatora, w tym wymaganie modyfikatorów ułatwień dostępu, określanie żądanej kolejności sortowania modyfikatora i wymaganie modyfikatora tylko do odczytu.

Reguły te mogą pojawić się w pliku *.editorconfig* w następujący sposób:

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

#### <a name="dotnet_style_require_accessibility_modifiers"></a>styl\_\_dotnet\_wymaga accessibility_modifiers

|||
|-|-|
| **Nazwa reguły** | dotnet_style_require_accessibility_modifiers |
| **Identyfikator zasady** | IDE0040 ( IDE0040 ) |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `always`- Preferuj modyfikatory ułatwień dostępu, które mają być określone.<br /><br />`for_non_interface_members`- Preferuj modyfikatory ułatwień dostępu, które mają być zadeklarowane, z wyjątkiem elementów członkowskich interfejsu publicznego. (Jest to taka sama jak **zawsze** i został dodany do przyszłości proofing jeśli C# dodaje domyślne metody interfejsu.)<br /><br />`never`- Nie należy preferować modyfikatorów ułatwień dostępu do określenia.<br /><br />`omit_if_default`- Preferuj modyfikatory ułatwień dostępu do określenia, chyba że są one domyślnym modyfikatorem. |
| **Domyślna wartość programu Visual Studio** | `for_non_interface_members:silent` |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.5 |

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
| **Identyfikator zasady** | IDE0036 |
| **Odpowiednie języki** | C# |
| **Wartości** | Co najmniej jeden modyfikator `public`języka `private`C#, taki jak , , i`protected` |
| **Domyślna wartość programu Visual Studio** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.5 |

- Gdy ta reguła jest ustawiona na listę modyfikatorów, preferuj określoną kolejność.
- Po pominięciu tej reguły w pliku nie należy preferować kolejności modyfikatorów.

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
| **Identyfikator zasady** | IDE0036 |
| **Odpowiednie języki** | Visual Basic |
| **Wartości** | Co najmniej jeden modyfikator `Partial`języka `Private`Visual Basic, taki jak , i`Public` |
| **Domyślna wartość programu Visual Studio** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.5 |

- Gdy ta reguła jest ustawiona na listę modyfikatorów, preferuj określoną kolejność.
- Po pominięciu tej reguły w pliku nie należy preferować kolejności modyfikatorów.

Przykłady kodu:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="visual_basic_style_unused_value_expression_statement_preference"></a>visual_basic_style_unused_value_expression_statement_preference

|||
|-|-|
| **Nazwa reguły** | visual_basic_style_unused_value_expression_statement_preference |
| **Identyfikator zasady** | IDE0058 |
| **Odpowiednie języki** | Visual Basic |
| **Wartości** | `unused_local_variable:silent` |
| **Domyślna wartość programu Visual Studio** | `unused_local_variable:silent` |

Przykłady kodu:

```vb
' visual_basic_style_unused_value_expression_statement_preference = unused_local_variable:silent

Dim unused = Computation()
```

#### <a name="visual_basic_style_unused_value_assignment_preference"></a>visual_basic_style_unused_value_assignment_preference

|||
|-|-|
| **Nazwa reguły** | visual_basic_style_unused_value_assignment_preference |
| **Identyfikator zasady** | IDE0059 |
| **Odpowiednie języki** | Visual Basic |
| **Wartości** | `unused_local_variable:silent` |
| **Domyślna wartość programu Visual Studio** | `unused_local_variable:silent` |

Przykłady kodu:

```vb
' visual_basic_style_unused_value_assignment_preference = unused_local_variable:suggestion

Dim unused = Computation()
Dim x = 1;
```

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|||
|-|-|
| **Nazwa reguły** | dotnet_style_readonly_field |
| **Identyfikator zasady** | IDE0044 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj, aby `readonly` pola były `ReadOnly` oznaczone (C#) lub (Visual Basic), jeśli są one przypisane tylko w linii lub wewnątrz konstruktora<br /><br />`false`- Określ, czy pola mają `readonly` być oznaczone `ReadOnly` (C#) lub (Visual Basic) |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |

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

Reguły stylu w tej sekcji dotyczą preferencji w nawiasach, w tym użycia nawiasów dla operatorów arytmetycznych, relacyjnych i innych operatorów binarnych.

Reguły te mogą pojawić się w pliku *.editorconfig* w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>nawiasy\_stylu\_dotnet\_\_w binary_operators\_arytmetycznych

|||
|-|-|
| **Nazwa reguły** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **Identyfikator zasady** | IDE0047 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `always_for_clarity`- Preferuj nawiasy do wyjaśnienia operatora`*` `/`arytmetycznego `<<` `>>`( `&` `^`, `|` `%`, , `+`, `-`, , , , , , ),<br /><br />`never_if_unnecessary`- Wolą nie mieć nawiasów, gdy operator`*`arytmetyczny ( `>>` `&`, `^` `/`, `%` `+`, `-`, , `<<`, , , , , `|`) pierwszeństwo jest oczywiste |
| **Domyślna wartość programu Visual Studio** | `always_for_clarity:silent` |
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

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>nawiasy\_stylu\_dotnet\_\_w\_binary_operators relacyjnej

|||
|-|-|
| **Nazwa reguły** | dotnet_style_parentheses_in_relational_binary_operators |
| **Identyfikator zasady** | IDE0047 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `always_for_clarity`- Preferuj nawiasy do wyjaśnienia`>` `<`operatora `<=` `>=`relacyjnego ( , `is`, , , `as`, , `==`, , `!=`) pierwszeństwo<br /><br />`never_if_unnecessary`- Wolą nie mieć nawiasów, gdy`>`operator `<` `<=`relacyjny ( , , `>=`, `is`, `as`, , `==`, , `!=`) pierwszeństwo jest oczywiste |
| **Domyślna wartość programu Visual Studio** | `always_for_clarity:silent` |
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

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>nawiasy\_stylu\_dotnet\_\_w\_innych binary_operators

|||
|-|-|
| **Nazwa reguły** | dotnet_style_parentheses_in_other_binary_operators |
| **Identyfikator zasady** | IDE0047 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `always_for_clarity`- Preferuj nawiasy, aby`&&`wyjaśnić `||` `??`inne operator binarny ( , , ) pierwszeństwo<br /><br />`never_if_unnecessary`- Wolą nie mieć nawiasów, gdy`&&`inny `||` `??`operator binarny ( , , ) pierwszeństwo jest oczywiste |
| **Domyślna wartość programu Visual Studio** | `always_for_clarity:silent` |
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

#### <a name="dotnet_style_parentheses_in_other_operators"></a>nawiasy\_stylu\_dotnet\_\_w other_operators

|||
|-|-|
| **Nazwa reguły** | dotnet_style_parentheses_in_other_operators |
| **Identyfikator zasady** | IDE0047 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `always_for_clarity`- Preferuj nawiasy, aby wyjaśnić pierwszeństwo operatora<br /><br />`never_if_unnecessary`- Wolisz nie mieć nawiasów, gdy pierwszeństwo operatora jest oczywiste |
| **Domyślna wartość programu Visual Studio** | `never_if_unnecessary:silent` |
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

### <a name="expression-level-preferences"></a>Preferencje na poziomie wyrażenia

Reguły stylu w tej sekcji dotyczą preferencji na poziomie wyrażenia, w tym użycie inicjatorów obiektów, inicjatorów kolekcji, jawnych lub wywnioskowane nazwy krotek i wywnioskować typy anonimowe.

Reguły te mogą pojawić się w pliku *.editorconfig* w następujący sposób:

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

#### <a name="dotnet_style_object_initializer"></a>object_initializer w\_\_stylu dotnet

|||
|-|-|
| **Nazwa reguły** | dotnet_style_object_initializer |
| **Identyfikator zasady** | IDE0017 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj obiekty, które mają być inicjowane za pomocą inicjatorów obiektów, gdy jest to możliwe<br /><br />`false`- Preferuj *obiekty,* aby nie były inicjowane przy użyciu inicjatorów obiektów |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_collection_initializer"></a>collection_initializer w\_\_stylu dotnet

|||
|-|-|
| **Nazwa reguły** | dotnet_style_collection_initializer |
| **Identyfikator zasady** | IDE0028 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj kolekcje, które mają być inicjowane przy użyciu inicjatorów kolekcji, gdy jest to możliwe<br /><br />`false`- Preferuj *kolekcje,* aby nie były inicjowane przy użyciu inicjatorów kolekcji |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_explicit_tuple_names"></a>jawne\_\_tuple_names\_w stylu dotnet

|||
|-|-|
| **Nazwa reguły** | dotnet_style_explicit_tuple_names |
| **Identyfikator zasady** | IDE0033 |
| **Odpowiednie języki** | C# 7.0+ i Visual Basic 15+ |
| **Wartości** | `true`- Preferuj nazwy krotek do właściwości ItemX<br /><br />`false`- Preferuj właściwości ItemX, aby śledzić nazwy |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>styl\_\_dotnet\_preferuje\_wywnioskowane tuple_names

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_inferred_tuple_names |
| **Identyfikator zasady** | IDE0037 |
| **Odpowiednie języki** | C# 7.1+ i Visual Basic 15+ |
| **Wartości** | `true`- Preferuj wywnioskowane nazwy elementów krotki<br /><br />`false`- Preferuj jawne nazwy elementów krotki |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.6 |

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

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>\_styl\_dotnet\_preferuje\_\_wywnioskowane typu anonimowego\_member_names

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **Identyfikator zasady** | IDE0037 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj wywnioskowane nazwy członków typu anonimowego<br /><br />`false`- Preferuj jawne nazwy członków typu anonimowego |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.6 |

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

#### <a name="dotnet_style_prefer_auto_properties"></a>styl\_\_dotnet\_\_preferuje właściwości auto

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_auto_properties |
| **Identyfikator zasady** | IDE0032 ( IDE0032 ) |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj właściwości autoproperty niż właściwości z prywatnymi polami podkładowymi<br /><br />`false`- Preferuj właściwości z prywatnymi polami podkładu nad właściwościami autoprowłaściwczymi |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |

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

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>\_styl\_dotnet\_\_preferuje\_\_to\_\_sprawdzanie wartości null\_w metodzie równości odwołań

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **Identyfikator zasady** | IDE0041 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj użycie czeku zerowego z dopasowaniem wzoru`object.ReferenceEquals`<br /><br />`false`- `object.ReferenceEquals` Preferuj kontrolę zerową z dopasowaniem wzoru |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>\_Styl\_dotnet\_preferuje\_wyrażenie warunkowe\_over_assignment

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_conditional_expression_over_assignment |
| **Identyfikator zasady** | IDE0045 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj zadania z trójskładnikowym warunkowym nad instrukcją if-else<br /><br />`false`- Preferuj zadania z oświadczeniem if-else nad trójskładnikowym warunkowym |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |
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

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>\_Styl\_dotnet\_preferuje\_wyrażenie warunkowe\_over_return

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_conditional_expression_over_return |
| **Identyfikator zasady** | IDE0046 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj zwrot instrukcji używać trójskładnikowego warunkowego na if-else instrukcji<br /><br />`false`- Preferuj zwrot instrukcji użyć if-else instrukcji na trójskładnik warunkowe |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |
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

#### <a name="dotnet_style_prefer_compound_assignment"></a>styl\_\_dotnet\_\_preferuje przypisanie złożone

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_compound_assignment |
| **Identyfikator zasady** | IDE0054 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj [wyrażenia przypisania złożonego](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment)<br /><br />`false`- Nie preferuj złożonych wyrażeń przypisania |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

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

Reguły te mogą pojawić się w pliku *.editorconfig* w następujący sposób:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
```

#### <a name="dotnet_style_coalesce_expression"></a>coalesce_expression w\_\_stylu dotnet

|||
|-|-|
| **Nazwa reguły** | dotnet_style_coalesce_expression |
| **Identyfikator zasady** | IDE0029 |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `true`- Preferuj wyrażenia scalania null do trójskładnikowego sprawdzania operatora<br /><br />`false`- Preferuj trójskładnikowego operatora sprawdzania wyrażeń zerowych |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_null_propagation"></a>null_propagation w\_\_stylu dotnet

|||
|-|-|
| **Nazwa reguły** | dotnet_style_null_propagation |
| **Identyfikator zasady** | IDE0031 |
| **Odpowiednie języki** | C# 6.0+ i Visual Basic 14+ |
| **Wartości** | `true`- Wolisz używać operatora warunkowego null, gdy jest to możliwe<br /><br />`false`- W miarę możliwości wolisz używać trójskładnikowej kontroli zerowej |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

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

### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>\_styl\_dotnet\_\_preferuje\_\_to\_\_sprawdzanie wartości null\_w metodzie równości odwołań

|||
|-|-|
| **Nazwa reguły** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **Identyfikator zasady** | IDE0041 |
| **Odpowiednie języki** | C# 6.0+ i Visual Basic 14+ |
| **Wartości** | `true`- Prefer jest null sprawdzić metodę równości odwołania<br /><br />`false`- Preferuj metodę równości odwołania nad jest sprawdzenie null |
| **Domyślna wartość programu Visual Studio** | `true:silent` |

## <a name="net-code-quality-settings"></a>Ustawienia jakości kodu .NET

Reguły jakości w tej sekcji dotyczą kodu języka C# i visual basic. Są one używane do konfigurowania analizatorów kodu, które są wbudowane w zintegrowane środowisko programistyczne programu Visual Studio (IDE). Aby uzyskać informacje na temat konfigurowania analizatorów FxCop za pomocą pliku EditorConfig, zobacz [Konfigurowanie analizatorów FxCop](../code-quality/configure-fxcop-analyzers.md).

- [Preferencje parametrów](#parameter-preferences)
  - jakość kodu\_\_dotnet\_\_nieużywane parametry

### <a name="parameter-preferences"></a>Preferencje parametrów

Zasady jakości w tej sekcji dotyczą parametrów metody.

Reguły te mogą pojawić się w pliku *.editorconfig* w następujący sposób:

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>jakość kodu\_\_dotnet\_\_nieużywane parametry

|||
|-|-|
| **Nazwa reguły** | dotnet_code_quality_unused_parameters |
| **Identyfikator zasady** | IDE0060 ( IDE0060 ) |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wartości** | `all`- Oznaczanie metod z dowolną dostępnością, która zawiera nieużywane parametry<br /><br />`non_public`- Oznaczanie tylko metod niepublicznych zawierających nieużywane parametry |
| **Domyślna wartość programu Visual Studio** | `all:suggestion` |

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

## <a name="c-code-style-settings"></a>Ustawienia stylu kodu języka C#

Reguły stylu w tej sekcji mają zastosowanie tylko do języka C#.

- [Typy niejawne i jawne](#implicit-and-explicit-types)
  - csharp\_\_style\_\_var\_dla zbudowanych in_types
  - csharp\_\_style\_\_var\_po wpisaniu is_apparent
  - var_elsewhere w\_\_stylu csharp
- [Składowe z wyrażeniem w treści](#expression-bodied-members)
  - wyrażenie\_stylu\_\_csharp bodied_methods
  - wyrażenie\_stylu\_\_csharp bodied_constructors
  - wyrażenie\_stylu\_\_csharp bodied_operators
  - wyrażenie\_stylu\_\_csharp bodied_properties
  - wyrażenie\_stylu\_\_csharp bodied_indexers
  - wyrażenie\_stylu\_\_csharp bodied_accessors
  - wyrażenie\_stylu\_\_csharp bodied_lambdas
  - wyrażenie\_stylu\_\_csharp\_zabudowane local_functions
- [Dopasowywanie wzoru](#pattern-matching)
  - csharp\_\_styl\_\_wzór\_\_dopasowania\_ponad jest z cast_check
  - wzorzec\_\_\_stylu\_csharp dopasowując się\_jak\_w\_przypadku null_check
- [Deklaracje zmiennych inlined](#inlined-variable-declarations)
  - csharp\_\_stylu inlined\_variable_declaration
- [Preferencje na poziomie wyrażenia](#c-expression-level-preferences)
  - csharp\_\_wolą\_proste default_expression
- [Preferencje sprawdzania wartości "Null"](#c-null-checking-preferences)
  - throw_expression w\_\_stylu csharp
  - delegate_call\_warunkowe\_\_w stylu csharp
- [Preferencje modyfikatora](#normalize-modifiers) \_-csharp preferowane\_modifier_order
- [Preferencje bloków kodu](#code-block-preferences)
  - \_prefer_braces
- [Nieużywane preferencje wartości](#unused-value-preferences)
  - csharp\_\_styl nieużywane\_wyrażenie\_\_wartości statement_preference
  - nieużywanych\_\_wartości\_w stylu\_csharp assignment_preference
- [Preferencje indeksu i zakresu](#index-and-range-preferences)
  - styl\_\_csharp\_preferuje index_operator
  - styl\_\_csharp\_preferuje range_operator
- [Różne preferencje](#miscellaneous-preferences)
  - styl\_\_csharp zdekonstruowany\_variable_declaration
  - wzorzec\_\_\_stylu\_csharp lokalny na\_anonymous_function
  - csharp\_\_za\_pomocą umieszczania dyrektywy
  - csharp\_\_preferuje\_statyczne local_function
  - csharp\_\_wolą\_proste using_statement
  - styl\_\_csharp\_preferuje switch_expression

### <a name="implicit-and-explicit-types"></a>Typy niejawne i jawne

Reguły stylu w tej sekcji dotyczą użycia słowa kluczowego [var](/dotnet/csharp/language-reference/keywords/var) w porównaniu z typem jawnym w deklaracji zmiennej. Ta reguła może być stosowana oddzielnie do typów wbudowanych, gdy typ jest widoczny i gdzie indziej.

Przykład *pliku .editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharp_style_var_for_built_in_types"></a>csharp\_\_style\_\_var\_dla zbudowanych in_types

|||
|-|-|
| **Nazwa reguły** | csharp_style_var_for_built_in_types |
| **Identyfikator zasady** | IDE0007 i IDE0008 |
| **Odpowiednie języki** | C#  |
| **Wartości** | `true`- `var` Prefer służy do deklarowania zmiennych z wbudowanymi typami systemowymi, takimi jak`int`<br /><br />`false`- Preferuj `var` jawny typ, aby zadeklarować zmienne z wbudowanymi typami systemowymi, takimi jak`int` |
| **Domyślna wartość programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>csharp\_\_style\_\_var\_po wpisaniu is_apparent

|||
|-|-|
| **Nazwa reguły** | csharp_style_var_when_type_is_apparent |
| **Identyfikator zasady** | IDE0007 i IDE0008 |
| **Odpowiednie języki** | C#  |
| **Wartości** | `true`- `var` Preferuj, gdy typ jest już wymieniony po prawej stronie wyrażenia deklaracji<br /><br />`false`- Preferuj `var` jawny typ, gdy typ jest już wymieniony po prawej stronie wyrażenia deklaracji |
| **Domyślna wartość programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>var_elsewhere w\_\_stylu csharp

|||
|-|-|
| **Nazwa reguły** | csharp_style_var_elsewhere |
| **Identyfikator zasady** | IDE0007 i IDE0008 |
| **Odpowiednie języki** | C#  |
| **Wartości** | `true`- `var` Preferuj jawny typ we wszystkich przypadkach, chyba że zostanie zastąpiony przez inną regułę stylu kodu<br /><br />`false`- Preferuj `var` jawny typ we wszystkich przypadkach, chyba że zostanie zastąpiony przez inną regułę stylu kodu |
| **Domyślna wartość programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>Składowe z wyrażeniem w treści

Reguły stylu w tej sekcji dotyczą użycia [elementów członkowskich zabudowanych wyrażenia,](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) gdy logika składa się z pojedynczego wyrażenia. Ta reguła może być stosowana do metod, konstruktorów, operatorów, właściwości, indeksatorów i akcesorów.

Przykład *pliku .editorconfig:*

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

#### <a name="csharp_style_expression_bodied_methods"></a>wyrażenie\_stylu\_\_csharp bodied_methods

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_methods |
| **Identyfikator zasady** | IDE0022 |
| **Odpowiednie języki** | C# 6.0+  |
| **Wartości** | `true`- Preferuj obiekty wyrażeń dla metod<br /><br />`when_on_single_line`- Preferuj obiekty wyrażeń dla metod, gdy będą one jednym wierszem<br /><br />`false`- Preferuj obiekty blokowe dla metod |
| **Domyślna wartość programu Visual Studio** | `false:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>wyrażenie\_stylu\_\_csharp bodied_constructors

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_constructors |
| **Identyfikator zasady** | IDE0021 |
| **Odpowiednie języki** | C# 7.0+ |
| **Wartości** | `true`- Preferuj obiekty wyrażeń dla konstruktorów<br /><br />`when_on_single_line`- Preferuj obiekty wyrażeń dla konstruktorów, gdy będą one jednym wierszem<br /><br />`false`- Preferuj obiekty blokowe dla konstruktorów |
| **Domyślna wartość programu Visual Studio** | `false:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>wyrażenie\_stylu\_\_csharp bodied_operators

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_operators |
| **Identyfikator zasady** | IDE0023 i IDE0024 |
| **Odpowiednie języki** | C# 7.0+ |
| **Wartości** | `true`- Preferuj obiekty wyrażeń dla operatorów<br /><br />`when_on_single_line`- Preferuj obiekty wyrażeń dla operatorów, gdy będą one jednym wierszem<br /><br />`false`- Preferuj obiekty blokowe dla operatorów |
| **Domyślna wartość programu Visual Studio** | `false:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharp_style_expression_bodied_properties"></a>wyrażenie\_stylu\_\_csharp bodied_properties

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_properties |
| **Identyfikator zasady** | IDE0025 |
| **Odpowiednie języki** | C# 7.0+ |
| **Wartości** | `true`- Preferuj obiekty wyrażeń dla właściwości<br /><br />`when_on_single_line`- Preferuj obiekty wyrażeń dla właściwości, gdy będą one jednym wierszem<br /><br />`false`- Preferuj obiekty blokowe dla właściwości |
| **Domyślna wartość programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>wyrażenie\_stylu\_\_csharp bodied_indexers

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_indexers |
| **Identyfikator zasady** | IDE0026 |
| **Odpowiednie języki** | C# 7.0+ |
| **Wartości** | `true`- Preferuj obiekty wyrażeń dla indeksatorów<br /><br />`when_on_single_line`- Preferuj obiekty wyrażeń dla indeksatorów, gdy będą one jednym wierszem<br /><br />`false`- Preferuj obiekty blokowe dla indeksatorów |
| **Domyślna wartość programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>wyrażenie\_stylu\_\_csharp bodied_accessors

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_accessors |
| **Identyfikator zasady** | IDE0027 |
| **Odpowiednie języki** | C# 7.0+ |
| **Wartości** | `true`- Preferuj obiekty wyrażeń dla akcesorów<br /><br />`when_on_single_line`- Preferuj obiekty wyrażeń dla akcesorów, gdy będą one jednym wierszem<br /><br />`false`- Preferuj korpusy blokowe dla akcesorów |
| **Domyślna wartość programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>wyrażenie\_stylu\_\_csharp bodied_lambdas

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_lambdas |
| **Identyfikator zasady** | IDE0053 |
| **Wartości** | `true`- Preferuj ciała wyrazu dla lambdas<br /><br />`when_on_single_line`- Preferuj ciała ekspresji dla lambdów, gdy będą one jednym wierszem<br /><br />`false`- Preferuj korpusy blokowe dla lambdas |
| **Domyślna wartość programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>wyrażenie\_stylu\_\_csharp\_zabudowane local_functions

Począwszy od języka C# 7.0, C# obsługuje [funkcje lokalne](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Funkcje lokalne są metody prywatne typu, które są zagnieżdżone w innym elementem członkowskim.

|||
|-|-|
| **Nazwa reguły** | csharp_style_expression_bodied_local_functions |
| **Identyfikator zasady** | IDE0061 |
| **Odpowiednie języki** | C# 7.0+ |
| **Wartości** | `true`- Preferuj obiekty wyrażeń dla funkcji lokalnych<br /><br />`when_on_single_line`- Preferuj obiekty wyrażeń dla funkcji lokalnych, gdy będą one jednym wierszem<br /><br />`false`- Preferuj obiekty blokowe dla funkcji lokalnych |
| **Domyślna wartość programu Visual Studio** | `false:silent` |

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

Reguły stylu w tej sekcji dotyczą użycia [dopasowania wzorca](/dotnet/csharp/pattern-matching) w języku C#.

Przykład *pliku .editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>csharp\_\_styl\_\_wzór\_\_dopasowania\_ponad jest z cast_check

|||
|-|-|
| **Nazwa reguły** | csharp_style_pattern_matching_over_is_with_cast_check |
| **Identyfikator zasady** | IDE0020 ( IDE0020 ) |
| **Odpowiednie języki** | C# 7.0+ |
| **Wartości** | `true`- Preferuj dopasowywanie wzorca `is` zamiast wyrażeń z rzutowaniami typu<br /><br />`false`- `is` Preferuj wyrażenia z rzutowaniami zamiast dopasowywania wzorca |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>wzorzec\_\_\_stylu\_csharp dopasowując się\_jak\_w\_przypadku null_check

|||
|-|-|
| **Nazwa reguły** | csharp_style_pattern_matching_over_as_with_null_check |
| **Identyfikator zasady** | IDE0019 |
| **Odpowiednie języki** | C# 7.0+ |
| **Wartości** | `true`- Preferuj dopasowywanie wzorców zamiast `as` wyrażeń z zerowymi czekami, aby ustalić, czy coś jest określonego typu<br /><br />`false`- `as` Preferuj wyrażenia z sprawdzaniem wartości null zamiast dopasowywania wzorców, aby ustalić, czy coś jest określonego typu |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>Deklaracje zmiennych inlined

Ta reguła `out` stylu dotyczy tego, czy zmienne są zadeklarowane w linii, czy nie. Począwszy od języka C# 7, można [zadeklarować zmienną out na liście argumentów wywołania metody,](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument)a nie w deklaracji oddzielnej zmiennej.

#### <a name="csharp_style_inlined_variable_declaration"></a>csharp\_\_stylu inlined\_variable_declaration

|||
|-|-|
| **Nazwa reguły** | csharp_style_inlined_variable_declaration |
| **Identyfikator zasady** | IDE0018 |
| **Odpowiednie języki** | C# 7.0+ |
| **Wartości** | `true`- `out` Preferuj zmienne, które mają być zadeklarowane w linii argumentów wywołania metody, jeśli to możliwe<br /><br />`false`- `out` Preferuj zmienne, które mają być zadeklarowane przed wywołaniem metody |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Przykład *pliku .editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="c-expression-level-preferences"></a>Preferencje na poziomie wyrażenia języka C#

Reguły stylu w tej sekcji dotyczą preferencji na poziomie wyrażenia.

Przykład *pliku .editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>csharp\_\_wolą\_proste default_expression

Ta reguła stylu dotyczy używania [ `default` literału dla domyślnych wyrażeń wartości,](/dotnet/csharp/language-reference/operators/default#default-literal) gdy kompilator może wywnioskować typ wyrażenia.

|||
|-|-|
| **Nazwa reguły** | csharp_prefer_simple_default_expression |
| **Identyfikator zasady** | IDE0034 ( IDE0034 ) |
| **Odpowiednie języki** | C# 7.1+  |
| **Wartości** | `true`- `default` Wolą ponad`default(T)`<br /><br />`false`- `default(T)` Wolą ponad`default` |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>Preferencje sprawdzania wartości null w języku C#

Te reguły stylu dotyczą `null` składni wokół `throw` sprawdzania, `throw` w tym przy użyciu wyrażeń lub instrukcji, oraz`?.`tego, czy należy sprawdzić wartość null, czy użyć operatora parzyskowania warunkowego ( ) podczas wywoływania [wyrażenia lambda](/dotnet/csharp/lambda-expressions).

Przykład *pliku .editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>throw_expression w\_\_stylu csharp

|||
|-|-|
| **Nazwa reguły** | csharp_style_throw_expression |
| **Identyfikator zasady** | IDE0016 |
| **Odpowiednie języki** | C# 7.0+ |
| **Wartości** | `true`- Wolą `throw` używać wyrażeń `throw` zamiast instrukcji<br /><br />`false`- Wolą `throw` używać instrukcji `throw` zamiast wyrażeń |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>delegate_call\_warunkowe\_\_w stylu csharp

|||
|-|-|
| **Nazwa reguły** | csharp_style_conditional_delegate_call |
| **Identyfikator zasady** | IDE0041 |
| **Odpowiednie języki** | C# 6.0+  |
| **Wartości** | `true`- odnoszą się do używania operatora`?.`warunkowego scalania ( ) podczas wywoływania wyrażenia lambda, zamiast sprawdzania wartości null<br /><br />`false`- Preferuj przeprowadzenie sprawdzania wartości null przed wywołaniem wyrażenia lambda, zamiast`?.`używać operatora warunkowego scalania ( ) |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Preferencje bloków kodu

Ta reguła stylu dotyczy używania `{ }` nawiasów klamrowych do otaczania bloków kodu.

Przykład *pliku .editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharp_prefer_braces"></a>csharp\_\_preferuje aparaty ortodontyczne

|||
|-|-|
| **Nazwa reguły** | csharp_prefer_braces |
| **Identyfikator zasady** | IDE0011 |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`- Preferuj kręcone szelki nawet dla jednej linii kodu<br /><br />`false`- Nie preferuj kręconych szelki, jeśli jest to dozwolone<br /><br />`when_multiline`- Preferuj kręcone szelki na wielu liniach |
| **Domyślna wartość programu Visual Studio** | `true:silent` |

Przykłady kodu:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

### <a name="unused-value-preferences"></a>Nieużywane preferencje wartości

Te reguły stylu dotyczą nieużywanych wyrażeń i przypisań wartości.

Przykład *pliku .editorconfig:*

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
| **Identyfikator zasady** | IDE0058 |
| **Odpowiednie języki** | C# |
| **Wartości** | `discard_variable`- Wolisz przypisać nieużywane wyrażenie do [odrzucenia](/dotnet/csharp/discards) <br /><br />`unused_local_variable`- Wolisz przypisać nieużywane wyrażenie do zmiennej lokalnej |
| **Domyślna wartość programu Visual Studio** | `discard_variable:silent` |

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
| **Identyfikator zasady** | IDE0059 |
| **Odpowiednie języki** | C# |
| **Wartości** | `discard_variable`- Wolisz używać [odrzutu](/dotnet/csharp/discards) podczas przypisywania wartości, która nie jest używana<br /><br />`unused_local_variable`- Wolisz używać zmiennej lokalnej podczas przypisywania wartości, która nie jest używana |
| **Domyślna wartość programu Visual Studio** | `discard_variable:suggestion` |

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

Te reguły stylu dotyczą użycia operatorów indeksu i zakresu, które są dostępne w języku C# 8.0 i nowszych.

Przykład *pliku .editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>styl\_\_csharp\_preferuje index_operator

|||
|-|-|
| **Nazwa reguły** | csharp_style_prefer_index_operator |
| **Identyfikator zasady** | IDE0056 |
| **Odpowiednie języki** | C# 8.0+ |
| **Wartości** | `true`- Wolą używać `^` operatora przy obliczaniu indeksu od końca kolekcji<br /><br />`false`- Nie należy używać `^` operatora przy obliczaniu indeksu od końca kolekcji |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_style_prefer_index_operator = true
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[^1];

// csharp_style_prefer_index_operator = false
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[names.Length - 1];
```

#### <a name="csharp_style_prefer_range_operator"></a>styl\_\_csharp\_preferuje range_operator

|||
|-|-|
| **Nazwa reguły** | csharp_style_prefer_range_operator |
| **Identyfikator zasady** | IDE0057 |
| **Odpowiednie języki** | C# 8.0+ |
| **Wartości** | `true`- Wolisz używać `..` operatora zakresu podczas wyodrębniania "plasterka" kolekcji<br /><br />`false`- Nie należy używać operatora `..` zakresu podczas wyodrębniania "plasterka" kolekcji |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

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

Ta sekcja zawiera różne reguły stylu.

Przykład *pliku .editorconfig:*

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

#### <a name="csharp_style_deconstructed_variable_declaration"></a>styl\_\_csharp zdekonstruowany\_variable_declaration

|||
|-|-|
| **Nazwa reguły** | csharp_style_deconstructed_variable_declaration |
| **Identyfikator zasady** | IDE0042 ( IDE0042 ) |
| **Odpowiednie języki** | C# 7.0+ |
| **Wartości** | `true`- Preferuj zdekonstruowany deklarację zmiennej<br /><br />`false`- Nie preferuj dekonstrukcji w deklaracjach zmiennych |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

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

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>wzorzec\_\_\_stylu\_csharp lokalny na\_anonymous_function

Począwszy od języka C# 7.0, C# obsługuje [funkcje lokalne](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Funkcje lokalne są metody prywatne typu, które są zagnieżdżone w innym elementem członkowskim.

|||
|-|-|
| **Nazwa reguły** | csharp_style_pattern_local_over_anonymous_function |
| **Identyfikator zasady** | IDE0039 |
| **Odpowiednie języki** | C# 7.0+ |
| **Wartości** | `true`- Preferuj funkcje lokalne niż funkcje anonimowe<br /><br />`false`- Preferuj funkcje anonimowe niż funkcje lokalne |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

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

#### <a name="csharp_using_directive_placement"></a>csharp\_\_za pomocą directive_placement

|||
|-|-|
| **Nazwa reguły** | csharp_using_directive_placement |
| **Identyfikator zasady** | IDE0065 |
| **Odpowiednie języki** | C# |
| **Wartości** | `outside_namespace`- `using` Preferuj, aby dyrektywy były umieszczane poza przestrzenią nazw<br /><br />`inside_namespace`- `using` Preferuj, aby dyrektywy były umieszczane wewnątrz przestrzeni nazw |
| **Domyślna wartość programu Visual Studio** | `outside_namespace:silent` |

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

#### <a name="csharp_prefer_static_local_function"></a>csharp\_\_preferuje\_statyczne local_function

|||
|-|-|
| **Nazwa reguły** | csharp_prefer_static_local_function |
| **Identyfikator zasady** | IDE0062 ( IDE0062 ) |
| **Odpowiednie języki** | C# 8.0+ |
| **Wartości** | `true`- Preferuj, aby funkcje lokalne były oznaczane`static`<br /><br />`false`- Nie preferuj oznaczania funkcji lokalnych`static` |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

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

#### <a name="csharp_prefer_simple_using_statement"></a>csharp\_\_wolą\_proste using_statement

|||
|-|-|
| **Nazwa reguły** | csharp_prefer_simple_using_statement |
| **Identyfikator zasady** | IDE0063 |
| **Odpowiednie języki** | C# 8.0+ |
| **Wartości** | `true`- Wolą używać *prostego* `using` oświadczenia<br /><br />`false`- Nie woluj używać *prostego* `using` oświadczenia |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |

Przykłady kodu:

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>styl\_\_csharp\_preferuje switch_expression

|||
|-|-|
| **Nazwa reguły** | csharp_style_prefer_switch_expression |
| **Identyfikator zasady** | IDE0066 |
| **Odpowiednie języki** | C# 8.0+ |
| **Wartości** | `true`- Wolą używać `switch` wyrażenia (wprowadzone z C# 8.0)<br /><br />`false`- Wolą używać [instrukcji przełącznika](/dotnet/csharp/language-reference/keywords/switch) |
| **Domyślna wartość programu Visual Studio** | `true:suggestion` |
| **Wprowadzona wersja** |  Program Visual Studio 2019 w wersji 16.2  |

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

## <a name="see-also"></a>Zobacz też

- [Konwencje formatowania](editorconfig-formatting-conventions.md)
- [Konwencje nazewnictwa](editorconfig-naming-conventions.md)
- [Ustawienia konwencji kodowania .NET dla EditorConfig](editorconfig-code-style-settings-reference.md)
