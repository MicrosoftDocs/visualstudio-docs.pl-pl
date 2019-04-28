---
title: .NET coding convention ustawienia dla wtyczki EditorConfig
ms.date: 06/14/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: kuhlenh
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3cdd9f0b46c578f713b7f2af2940f4d7742df19a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557219"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>.NET coding convention ustawienia dla wtyczki EditorConfig

Można definiować i obsługa styl kodu zgodne w Twojej bazy kodu z użyciem [EditorConfig](../ide/create-portable-custom-editor-options.md) pliku. Polecenia EditorConfig obejmuje kilka podstawowych właściwości formatowania, takie jak `indent_style` i `indent_size`. W programie Visual Studio można również skonfigurować przy użyciu pliku EditorConfig ustawienia Konwencji kodowania .NET. Można włączyć lub wyłączyć poszczególne .NET konwencje kodowania i skonfigurować stopień, w którym chcesz każdą regułę wymuszane za pośrednictwem jej poziom ważności.

> [!TIP]
> - Podczas definiowania Konwencji kodowania w pliku .editorconfig, którą konfigurujesz, jak chcesz [analizatory stylu kodu](../code-quality/roslyn-analyzers-overview.md) wbudowanych w program Visual Studio do analizowania kodu. W pliku .editorconfig jest plik konfiguracyjny dla tych analizatorów.
> - Kod preferencji stylu programu Visual Studio można również ustawić [Opcje edytora tekstowego](code-styles-and-quick-actions.md) okna dialogowego. Jednak ustawienia w pliku .editorconfig wziąć pierwszeństwo i preferencje ustawione w **opcje** nie są skojarzone z określonym projektem.

Na końcu tego artykułu zawiera [przykładowy plik pliku .editorconfig](#example-editorconfig-file).

## <a name="convention-categories"></a>Kategorie Konwencji

Istnieją trzy obsługiwane .NET kodowania Konwencji kategorie:

- [Style kodu języka](#language-code-styles)

   Reguły dotyczące języka C# lub Visual Basic. Na przykład można określić zasady dotyczące korzystania z `var` lub jawnych typów podczas definiowania zmiennych i preferowanie elementy członkowskie z wyrażeniem.

- [Konwencje formatowania](#formatting-conventions)

   Zasady dotyczące układu i strukturę kodu w celu ułatwienia odczytu. Na przykład można określić zasady wokół Allman nawiasów klamrowych lub preferowanie miejsca do magazynowania w bloki sterujące.

- [Konwencje nazewnictwa](../ide/editorconfig-naming-conventions.md)

   Zasady dotyczące nazw elementów kodu. Na przykład można określić które `async` metody musi kończyć się "Async".

## <a name="language-code-styles"></a>Style kodu języka

Reguły dla języka kodu style mają następujący format:

`options_name = false|true : none|silent|suggestion|warning|error`

Dla każdej reguły stylu kodu języka, należy określić **true** (Preferuj ten styl) lub **false** (nie Preferuj kwalifikatora ten styl), a **ważność**. Ważność określa poziom wymuszania dla tego stylu.

W poniższej tabeli wymieniono wartości ważności możliwe i ich skutki:

Ważność | Efekt
:------- | ------
`none` | Nie pokazuj żadnych do użytkownika, gdy zasada ta jest naruszona. Funkcje generowania kodu Generuj kod jednak w przypadku tego stylu. Reguły z `none` ważność nigdy nie pojawiają się w **szybkie akcje i Refaktoryzacje** menu. W większości przypadków to jest uznawany za "wyłączone" lub "ignorowane".
`silent` (również `refactoring` w programie Visual Studio 2017 wersja 15.8) | Nie pokazuj żadnych do użytkownika, gdy zasada ta jest naruszona. Funkcje generowania kodu Generuj kod jednak w przypadku tego stylu. Reguły z `silent` ważność uczestniczyć w oczyszczania, a także są wyświetlane w **szybkie akcje i Refaktoryzacje** menu.
`suggestion` | W przypadku naruszenia tej reguły stylu wyświetlane użytkownikowi jako sugestię. Sugestie są traktowane jako trzy kropki szarym obszarze pierwsze dwa znaki.
`warning` | W przypadku naruszenia tej reguły stylu Pokaż ostrzeżenia kompilatora.
`error` | W przypadku naruszenia tej reguły stylów, Pokaż błąd kompilatora.

Na poniższej liście przedstawiono dopuszczalne języka ustawienia stylu kodu:

- Ustawienia stylu kodu .NET
    - ["This." i "Me."](#this_and_me)
        - dotnet\_style\_qualification\_for_field
        - dotnet\_style\_qualification\_for_property
        - dotnet\_style\_qualification\_for_method
        - dotnet\_style\_qualification\_for_event
    - [Słowa kluczowe języka zamiast framework wpisz nazwy odwołań do typu](#language_keywords)
        - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
        - polecenia DotNet\_styl\_wstępnie zdefiniowanych\_typu\_dla\_member_access
    - [Preferencje modyfikator](#normalize_modifiers)
        - dotnet\_style\_require\_accessibility_modifiers
        - csharp\_preferred\_modifier_order
        - visual\_basic\_preferred\_modifier_order
        - polecenia DotNet\_styl\_tylko do odczytu\_pola
    - [Preferencje nawiasów](#parentheses)
        - polecenia DotNet\_styl\_nawiasów\_w\_arytmetyczne\_binarne\_operatorów
        - polecenia DotNet\_styl\_nawiasów\_w\_innych\_binarne\_operatorów
        - polecenia DotNet\_styl\_nawiasów\_w\_innych\_operatorów
        - polecenia DotNet\_styl\_nawiasów\_w\_relacyjnych\_binarne\_operatorów
    - [Preferencje wyrażeń poziom](#expression_level)
        - dotnet\_style\_object_initializer
        - dotnet\_style\_collection_initializer
        - dotnet\_style\_explicit\_tuple_names
        - polecenia DotNet\_styl\_Preferuj\_wywnioskować\_tuple_names
        - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
        - polecenia DotNet\_styl\_Preferuj\_automatycznie\_właściwości
        - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method
        - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
        - dotnet\_style\_prefer\_conditional\_expression\_over\_return
    - ["Null" Sprawdzanie preferencje](#null_checking)
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
- Ustawienia stylu kodu C#
    - [Typy jawne i niejawne](#implicit-and-explicit-types)
        - CSharp\_styl\_var\_dla\_wbudowane\_in_types
        - csharp\_style\_var\_when\_type\_is_apparent
        - CSharp\_styl\_var_elsewhere
    - [Elementy członkowskie z wyrażeniem w treści](#expression_bodied_members)
        - csharp\_style\_expression\_bodied_methods
        - csharp\_style\_expression\_bodied_constructors
        - csharp\_style\_expression\_bodied_operators
        - csharp\_style\_expression\_bodied_properties
        - csharp\_style\_expression\_bodied_indexers
        - csharp\_style\_expression\_bodied_accessors
    - [Dopasowanie do wzorca](#pattern_matching)
        - CSharp\_styl\_wzorzec\_pasującego\_za pośrednictwem\_jest\_z\_cast_check
        - CSharp\_styl\_wzorzec\_pasującego\_za pośrednictwem\_jako\_z\_null_check
    - [Śródwierszowe deklaracje zmiennych](#inlined_variable_declarations)
        - csharp\_style\_inlined\_variable_declaration
    - [Preferencje wyrażeń poziom](#expression_level_csharp)
        - csharp\_prefer\_simple\_default_expression
        - CSharp\_styl\_zdekonstruowana\_variable_declaration
        - csharp\_style\_pattern\_local\_over\_anonymous_function
    - ["Null" Sprawdzanie preferencje](#null_checking_csharp)
        - csharp\_style\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [Preferencje bloku kodu](#code_block)
        - CSharp\_prefer_braces

### <a name="net-code-style-settings"></a>Ustawienia stylu kodu .NET

Reguły stylów w tej sekcji dotyczą zarówno C# i Visual Basic. Aby wyświetlić przykłady kodu w Twoim preferowanym języku programowania, wybierz go z listy rozwijanej **języka** menu w prawym górnym rogu okna przeglądarki.

#### <a name="this_and_me"></a>"This." i "Me." Kwalifikatory

Ta zasada stylu (reguła IDE0003 identyfikatorów i IDE0009) mogą być stosowane do pola, właściwości, metody i zdarzenia. Wartość **true** oznacza, że wolisz symbolu kodu, aby być poprzedzony znakami `this.` w języku C# lub `Me.` w języku Visual Basic. Wartość **false** oznacza, że Preferuj element kodu _nie_ do być poprzedzony znakami `this.` lub `Me.`.

W poniższej tabeli przedstawiono nazwy reguł, dotyczy języków programowania i wartości domyślne:

| Nazwa zasady | Właściwe języki | Wartość domyślna w usłudze Visual Studio |
| ----------- | -------------------- | ----------------------|
| dotnet_style_qualification_for_field | C# i Visual Basic | false:silent |
| dotnet_style_qualification_for_property | C# i Visual Basic | false:silent |
| dotnet_style_qualification_for_method | C# i Visual Basic | false:silent |
| dotnet_style_qualification_for_event | C# i Visual Basic | false:silent |

**dotnet\_style\_qualification\_for_field**

- Gdy ta reguła jest ustawiona na **true**, pola, aby być poprzedzony znakami Preferuj `this.` w języku C# lub `Me.` w języku Visual Basic.
- Gdy ta reguła jest ustawiona na **false**, Preferuj pola _nie_ do być poprzedzony znakami `this.` lub `Me.`.

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

**dotnet\_style\_qualification\_for_property**

- Gdy ta reguła jest ustawiona na **true**, preferowane właściwości, aby być poprzedzony znakami `this.` w języku C# lub `Me.` w języku Visual Basic.
- Gdy ta reguła jest ustawiona na **false**, Preferuj właściwości _nie_ do być poprzedzony znakami `this.` lub `Me.`.

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

**dotnet\_style\_qualification\_for_method**

- Gdy ta reguła jest ustawiona na **true**, Preferuj metody służące do być poprzedzony znakami `this.` w języku C# lub `Me.` w języku Visual Basic.
- Gdy ta reguła jest ustawiona na **false**, preferuje metod _nie_ do być poprzedzony znakami `this.` lub `Me.`.

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

**dotnet\_style\_qualification\_for_event**

- Gdy ta reguła jest ustawiona na **true**, Preferuj zdarzeń, aby być poprzedzony znakami `this.` w języku C# lub `Me.` w języku Visual Basic.
- Gdy ta reguła jest ustawiona na **false**, Preferuj zdarzenia _nie_ do być poprzedzony znakami `this.` lub `Me.`.

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

Te reguły może się pojawić w *.editorconfig* pliku w następujący sposób:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords"></a>Słowa kluczowe języka zamiast framework wpisz nazwy odwołań do typu

Ta zasada styl mogą być stosowane w przypadku, zmiennych lokalnych, parametrów metod i składowych klasy lub oddzielne zasady do typu wyrażenia dostępu do składowych. Wartość **true** oznacza, że wolisz słowo kluczowe języka (na przykład `int` lub `Integer`) zamiast nazwy typu (na przykład `Int32`) dla typów, które mają słowo kluczowe do ich reprezentacji. Wartość **false** oznacza, że Preferuj nazwę typu, zamiast słowa kluczowego języka.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguł, dotyczy języków programowania i wartości domyślne:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Visual Studio domyślną |
| --------- | ------- | -------------------- | ----------------------|
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 i IDE0014 | C# i Visual Basic | true:silent |
| dotnet_style_predefined_type_for_member_access | IDE0013 i IDE0015 | C# i Visual Basic | true:silent |

**dotnet\_style\_predefined\_type\_for\_locals\_parameters_members**

- Gdy ta reguła jest ustawiona na **true**Preferuj słowem kluczowym języka dla zmiennych lokalnych, parametrów metod i klas członków, a nie nazwę typu dla typów, które mają słowo kluczowe do ich reprezentacji.
- Gdy ta reguła jest ustawiona na **false**Preferuj nazwę typu dla zmiennych lokalnych, parametrów metod i klas członków, zamiast słowa kluczowego języka.

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

**dotnet\_style\_predefined\_type\_for\_member_access**

- Gdy ta reguła jest ustawiona na **true**, Preferuj słowem kluczowym języka dla wyrażenia dostępu do składowych, a nie nazwę typu dla typów, które mają słowo kluczowe do ich reprezentacji.
- Gdy ta reguła jest ustawiona na **false**, Preferuj Nazwa typu dla wyrażenia dostępu do składowych, zamiast słowa kluczowego języka.

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

Te reguły może się pojawić w *.editorconfig* pliku w następujący sposób:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="normalize_modifiers"></a>Preferencje modyfikator

Reguły stylów w tej sekcji dotyczą preferencje modyfikator, m.in. wymagające modyfikatory dostępności, określa ona kolejność sortowania modyfikator żądaną i wymagające modyfikatora tylko do odczytu.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguł, dotyczy języków programowania, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Visual Studio domyślną | Visual Studio 2017 w wersji |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| dotnet_style_require_accessibility_modifiers | IDE0040 | C# i Visual Basic | for_non_interface_members:silent | 15.5 |
| csharp_preferred_modifier_order | IDE0036 | C# | extern publiczną, prywatną, chronionych, wewnętrzne, statyczne, zastąpienie nowego, wirtualnego, abstract, sealed, tylko do odczytu, async:silent niebezpieczne, nietrwałe, | 15.5 |
| visual_basic_preferred_modifier_order | IDE0036 | Visual Basic | Częściowe, domyślny, Private, chronione publiczne, Friend, NotOverridable, możliwym do zastąpienia, MustOverride, przeciążenia, przesłonięć, MustInherit NotInheritable, statyczna, udostępniony, cieni, tylko do odczytu, WriteOnly, wymiar, Const, WithEvents, rozszerzanie i zwężanie niestandardowego, Async:silent | 15.5 |
| dotnet_style_readonly_field | IDE0044 | C# i Visual Basic | true:suggestion | 15.7 |

**dotnet\_style\_require\_accessibility_modifiers**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| zawsze | Preferuj modyfikatory dostępności należy określić |
| for\_non\_interface_members | Preferuj modyfikatory dostępności być zadeklarowany z wyjątkiem elementów członkowskich interfejsu publicznego. (To jest taka sama jak **zawsze** i dodano do sprawdzania w przyszłości, gdy C# dodaje domyślnych metod interfejsu.) |
| nigdy nie | Nie Preferuj kwalifikatora modyfikatory dostępności należy określić |
| omit_if_default | Preferuj modyfikatory dostępności należy określić z wyjątkiem, jeśli są one modyfikator domyślny |

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

**csharp_preferred_modifier_order**

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

**visual_basic_preferred_modifier_order**

- Gdy ta reguła ma wartość listy modyfikatorów tak, określonej kolejności.
- Gdy ta reguła jest pominięty z pliku, kolejność modyfikator nie jest preferowane.

Przykłady kodu:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

**dotnet_style_readonly_field**

- Gdy ta reguła jest ustawiona na **true**, preferuje się, że pól powinien być oznaczony przez `readonly` (C#) lub `ReadOnly` (Visual Basic), jeśli są one jedynie nigdy nie przypisano wbudowanych lub wewnątrz konstruktora.
- Gdy ta reguła jest ustawiona na **false**, określić Brak preferencji za pośrednictwem tego, czy pola powinien być oznaczony przez `readonly` (C#) lub `ReadOnly` (Visual Basic).

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

Te reguły może się pojawić w *.editorconfig* pliku w następujący sposób:

```EditorConfig
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

#### <a name="parentheses"></a>Preferencje nawiasów

Reguły stylów w tej sekcji dotyczą preferencje nawiasy, łącznie z użyciem nawiasów dla operacji arytmetycznych relacyjna, i inne operatory dwuargumentowe.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguł, dotyczy języków programowania, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Visual Studio domyślną | Visual Studio 2017 w wersji |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_parentheses_in_arithmetic_binary_operators | IDE0047 | C# i Visual Basic | always_for_clarity:silent | 15.8 |
| dotnet_style_parentheses_in_relational_binary_operators | IDE0047 | C# i Visual Basic | always_for_clarity:silent | 15.8 |
| dotnet_style_parentheses_in_other_binary_operators | IDE0047 | C# i Visual Basic | always_for_clarity:silent | 15.8 |
| dotnet_style_parentheses_in_other_operators | IDE0047 | C# i Visual Basic | never_if_unnecessary:silent | 15.8 |

**polecenia DotNet\_styl\_nawiasów\_w\_arytmetyczne\_binary_operators**

- Gdy ta reguła jest ustawiona na **always_for_clarity**, Preferuj nawiasów, aby wyjaśnić, operator arytmetyczny (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) pierwszeństwo.
- Gdy ta reguła jest ustawiona na **never_if_unnecessary**, wolą ma nawiasy, gdy arytmetyczne — operator (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) jest oczywiste, pierwszeństwo.

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

**polecenia DotNet\_styl\_nawiasów\_w\_relacyjnych\_binary_operators**

- Gdy ta reguła jest ustawiona na **always_for_clarity**, Preferuj nawiasów, aby wyjaśnić, operator relacyjny (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) pierwszeństwo.
- Gdy ta reguła jest ustawiona na **never_if_unnecessary**, wolą ma nawiasy, gdy relacyjnych — operator (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) jest oczywiste, pierwszeństwo.

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

**polecenia DotNet\_styl\_nawiasów\_w\_innych\_binary_operators**

- Gdy ta reguła jest ustawiona na **always_for_clarity**, Preferuj nawiasy w celu wyjaśnienia innych operatora binarnego (`&&`, `||`, `??`) pierwszeństwo.
- Gdy ta reguła jest ustawiona na **never_if_unnecessary**, wolą bez nawiasów po innych operatora binarnego (`&&`, `||`, `??`) jest oczywiste, pierwszeństwo.

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

**dotnet\_style\_parentheses\_in\_other_operators**

- Gdy ta reguła jest ustawiona na **always_for_clarity**, Preferuj nawiasów, aby wyjaśnić kolejność wykonywania działań.
- Gdy ta reguła jest ustawiona na **never_if_unnecessary**, łatwiej jest nie mieć nawiasy, gdy pierwszeństwo operatorów jest oczywiste.

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

Te reguły może się pojawić w *.editorconfig* pliku w następujący sposób:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="expression_level"></a>Preferencje wyrażeń poziom

Styl reguł w tej sekcji dotyczą wyrażenie poziomu preferencjach, łącznie z użyciem inicjatorów obiektów, inicjatory kolekcji, nazwy krotki jawne lub wywnioskowane uprawnienie i wywnioskować typów anonimowych.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguł, dotyczy języków programowania, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Visual Studio domyślną | Visual Studio 2017 w wersji |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_object_initializer | IDE0017 | C# i Visual Basic | true:suggestion | Pierwsza wersja |
| dotnet_style_collection_initializer | IDE0028 | C# i Visual Basic | true:suggestion | Pierwsza wersja |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0 + i Visual Basic 15 + | true:suggestion | Pierwsza wersja |
| dotnet_style_prefer_inferred_tuple_names | IDE0037 | C# 7.1 +, jak i Visual Basic 15 + | true:suggestion | 15.6 |
| dotnet_style_prefer_inferred_anonymous_type_member_names | IDE0037 | C# i Visual Basic | true:suggestion | 15.6 |
| dotnet_style_prefer_auto_properties | IDE0032 | C# i Visual Basic | true:silent | 15.7 |
| dotnet_style_prefer_is_null_check_over_reference_equality_method | IDE0041 | C# i Visual Basic | true:suggestion | 15.7 |
| dotnet_style_prefer_conditional_expression_over_assignment | IDE0045 | C# i Visual Basic | true:silent | 15.8 |
| dotnet_style_prefer_conditional_expression_over_return | IDE0046 | C# i Visual Basic | true:silent | 15.8 |

**dotnet\_style\_object_initializer**

- Gdy ta reguła jest ustawiona na **true**, Preferuj obiekty mogą zostać zainicjowane przy użyciu inicjatorów obiektów, gdy jest to możliwe.
- Gdy ta reguła jest ustawiona na **false**, Preferuj obiekty w celu *nie* można zainicjować przy użyciu inicjatorów obiektów.

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

**dotnet\_style\_collection_initializer**

- Gdy ta reguła jest ustawiona na **true**, Preferuj kolekcji, aby można zainicjować przy użyciu inicjatory kolekcji, jeśli jest to możliwe.
- Gdy ta reguła jest ustawiona na **false**, Preferuj kolekcje w celu *nie* można zainicjować przy użyciu inicjatory kolekcji.

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

**dotnet\_style\_explicit\_tuple_names**

- Gdy ta reguła jest ustawiona na **true**, wolisz nazw krotek ItemX właściwości.
- Gdy ta reguła jest ustawiona na **false**, Preferuj właściwości ItemX do nazw krotek.

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

**dotnet\_style\_prefer\_inferred\_tuple_names**

- Gdy ta reguła jest ustawiona na **true**, Preferuj wywnioskowane nazwy elementów krotki.
- Gdy ta reguła jest ustawiona na **false**, Preferuj nazwami elementów krotki jawnego.

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

**dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names**

- Gdy ta reguła jest ustawiona na **true**, Preferuj wywnioskowane nazwy anonimowych składowych typu.
- Gdy ta reguła jest ustawiona na **false**, Preferuj jawną nazwy anonimowych składowych typu.

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

**polecenia DotNet\_styl\_Preferuj\_automatycznie\_właściwości**

- Gdy ta reguła jest ustawiona na **true**, preferowanie autoproperties za pośrednictwem właściwości za pomocą pola prywatne zapasowy.
- Gdy ta reguła jest ustawiona na **false**, Preferuj właściwości za pomocą pola prywatne zapasowy przed autoproperties.

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

**dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method**

- Gdy ta reguła jest ustawiona na **true**, Preferuj przy użyciu sprawdzania wartości null z dopasowaniem wzorca przez obiekt. ReferenceEquals.
- Gdy ta reguła jest ustawiona na **false**, Preferuj obiektu. ReferenceEquals za pośrednictwem sprawdzania wartości null z dopasowaniem wzorca.

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

**dotnet\_style\_prefer\_conditional\_expression\_over_assignment**

- Gdy ta reguła jest ustawiona na **true**, preferowanie przypisania w usłudze trójargumentowy warunkowe za pośrednictwem instrukcji if else.
- Gdy ta reguła jest ustawiona na **false**, preferowanie przydziałów za pomocą instrukcji if-else za pośrednictwem trójargumentowy warunkowe.

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

**dotnet\_style\_prefer\_conditional\_expression\_over_return**

- Gdy ta reguła jest ustawiona na **true**, Preferuj instrukcjach return używać trójargumentowy warunkowe za pośrednictwem if-else, instrukcja.
- Gdy ta reguła jest ustawiona na **false**, Preferuj instrukcjach return użyć instrukcji if-else za pośrednictwem trójargumentowy warunkowe.

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

Te reguły może się pojawić w *.editorconfig* pliku w następujący sposób:

```EditorConfig
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

#### <a name="null_checking"></a>Preferencje sprawdzania wartości null

Reguły stylów w tej sekcji dotyczą preferencje sprawdzania wartości null.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguł, dotyczy języków programowania, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Visual Studio domyślną | Visual Studio 2017 w wersji |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_coalesce_expression | IDE0029 | C# i Visual Basic | true:suggestion | Pierwsza wersja |
| dotnet_style_null_propagation | IDE0031 | C# 6.0 + i Visual Basic 14 + | true:suggestion | Pierwsza wersja |

**dotnet\_style\_coalesce_expression**

- Gdy ta reguła jest ustawiona na **true**, Preferuj null wyrażenia łączącego, aby operator trójargumentowy sprawdzania.
- Gdy ta reguła jest ustawiona na **false**, Preferuj operator trójargumentowy sprawdzanie wyrażenia łączące wartości null.

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

**dotnet\_style\_null_propagation**

- Gdy ta reguła jest ustawiona na **true**, wolą używać operatorów warunkowych działających z wartością null, gdy jest to możliwe.
- Gdy ta reguła jest ustawiona na **false**, wolą używać trójargumentowy sprawdzania wartości null, jeśli jest to możliwe.

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

Te reguły może się pojawić w *.editorconfig* pliku w następujący sposób:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

### <a name="c-code-style-settings"></a>Ustawienia stylu kodu C#

Reguły stylów w tej sekcji odnoszą się do języka C# tylko.

#### <a name="implicit-and-explicit-types"></a>Typy jawne i niejawne

Reguły stylów w tej sekcji (reguła IDE0007 identyfikatorów i IDE0008) dotyczą użytkowania [var](/dotnet/csharp/language-reference/keywords/var) — słowo kluczowe w porównaniu z typem jawnym w deklaracji zmiennej. Ta zasada może dotyczyć oddzielnie wbudowanych typów, gdy typ jest widoczny i w innych miejscach.

W poniższej tabeli przedstawiono nazwy reguł, dotyczy języków programowania i wartości domyślne:

| Nazwa zasady | Właściwe języki | Visual Studio domyślną |
| ----------- | -------------------- | ----------------------|
| csharp_style_var_for_built_in_types | C# | true:silent |
| csharp_style_var_when_type_is_apparent | C# | true:silent |
| csharp_style_var_elsewhere | C# | true:silent |

**csharp\_style\_var\_for\_built\_in_types**

- Gdy ta reguła jest ustawiona na **true**, Preferuj `var` służy do deklarowania zmiennych wbudowany system typów, takich jak `int`.
- Gdy ta reguła jest ustawiona na **false**, Preferuj jawny typ za pośrednictwem `var` deklarowanie zmiennych wbudowany system typów, takich jak `int`.

Przykłady kodu:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**csharp\_style\_var\_when\_type\_is_apparent**

- Gdy ta reguła jest ustawiona na **true**, Preferuj `var` kiedy typ jest już Wspomniałem, po prawej stronie wyrażenie deklaracji.
- Gdy ta reguła jest ustawiona na **false**, Preferuj jawny typ za pośrednictwem `var` kiedy typ jest już Wspomniałem, po prawej stronie wyrażenie deklaracji.

Przykłady kodu:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**

- Gdy ta reguła jest ustawiona na **true**, Preferuj `var` za pośrednictwem typu jawnego we wszystkich przypadkach, jeśli zastąpiona przez inną regułę stylu kodu.
- Gdy ta reguła jest ustawiona na **false**, Preferuj jawny typ za pośrednictwem `var` we wszystkich przypadkach, jeśli zastąpiona przez inną regułę stylu kodu.

Przykłady kodu:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="expression_bodied_members"></a>Elementy członkowskie z wyrażeniem

Reguły stylów w tej sekcji dotyczą użytkowania [elementy członkowskie z wyrażeniem](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) po logikę składa się z pojedynczego wyrażenia. To reguła może zostać zastosowana do metod, konstruktory, operatory, właściwości, indeksatory i metod dostępu.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguł, wersje językowe odpowiednie, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Visual Studio domyślną | Visual Studio 2017 w wersji |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0+ | false:silent | 15.3 |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0+ | false:silent | 15.3 |
| csharp_style_expression_bodied_operators | IDE0023 i IDE0024 | C# 7.0+ | false:silent | 15.3 |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0+ | true:silent | 15.3 |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0+ | true:silent | 15.3 |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0+ | true:silent | 15.3 |

**csharp\_style\_expression\_bodied_methods**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| true | Preferuj wyrażeniem elementów członkowskich dla metod |
| when_on_single_line | Preferuj wyrażeniem elementów członkowskich dla metod, gdy będą one jednym wierszu |
| false | Preferuj treści bloku dla metod |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

**csharp\_style\_expression\_bodied_constructors**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| true | Preferuj wyrażeniem elementów członkowskich dla konstruktorów |
| when_on_single_line | Preferuj wyrażeniem elementów członkowskich dla konstruktorów, gdy będą one jednym wierszu |
| false | Preferuj treści bloku dla konstruktorów |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

**csharp\_style\_expression\_bodied_operators**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| true | Preferuj wyrażeniem elementów członkowskich dla operatorów |
| when_on_single_line | Preferuj wyrażeniem elementów członkowskich dla operatorów, gdy będą one jednym wierszu |
| false | Preferuj treści bloku dla operatorów |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

**csharp\_style\_expression\_bodied_properties**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| true | Preferuj wyrażeniem elementów członkowskich dla właściwości |
| when_on_single_line | Preferuj wyrażeniem elementów członkowskich dla właściwości, gdy będą one jednym wierszu |
| false | Preferuj treści bloku dla właściwości |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

**csharp\_style\_expression\_bodied_indexers**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| true | Preferuj wyrażeniem elementów członkowskich dla indeksatorów |
| when_on_single_line | Preferuj wyrażeniem elementów członkowskich dla indeksatorów, gdy będą one jednym wierszu |
| false | Preferuj treści bloku dla indeksatorów |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

**csharp\_style\_expression\_bodied_accessors**

Ta reguła akceptuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| true | Preferuj wyrażeniem elementów członkowskich dla metod dostępu |
| when_on_single_line | Preferuj wyrażeniem elementów członkowskich dla metod dostępu, gdy będą one jednym wierszu |
| false | Preferuj treści bloku dla metod dostępu |

Przykłady kodu:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="pattern_matching"></a>Dopasowanie wzorca

Reguły stylów w tej sekcji dotyczą użytkowania [dopasowywania do wzorca](/dotnet/csharp/pattern-matching) w języku C#.

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguł, wersje językowe odpowiednie i wartości domyślne:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Visual Studio domyślną |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0+ | true:suggestion |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0+ | true:suggestion |

**csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check**

- Gdy ta reguła jest ustawiona na **true**, Preferuj dopasowywanie do wzorców zamiast `is` wyrażenia z typu rzutowania.
- Gdy ta reguła jest ustawiona na **false**, Preferuj `is` wyrażenia z rzutowania typów, zamiast dopasowywania do wzorca.

Przykłady kodu:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**

- Gdy ta reguła jest ustawiona na **true**, Preferuj dopasowywanie do wzorców zamiast `as` wyrażeń o wartości null kontrole w celu ustalenia, czy jest coś, co jest określonego typu.
- Gdy ta reguła jest ustawiona na **false**, Preferuj `as` wyrażenia z sprawdzanie wartości null, zamiast dopasowywania do wzorca w celu ustalenia, czy jest coś, co jest określonego typu.

Przykłady kodu:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations"></a>Śródwierszowe deklaracje zmiennych

Ten styl tego, czy reguła dotyczy `out` zmienne są zadeklarowane wbudowane, czy nie. Począwszy od C# 7, możesz [deklarowanie zmiennej poza na liście argumentów wywołania metody](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), zamiast w oddzielnych deklaracji zmiennej.

W poniższej tabeli przedstawiono nazwy reguły, identyfikator reguły, wersje językowe odpowiednie i wartości domyślne:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Visual Studio domyślną |
| --------- | -------- | -------------------- | ----------------------|
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0+ | true:suggestion |

**csharp\_style\_inlined\_variable_declaration**

- Gdy ta reguła jest ustawiona na **true**, Preferuj `out` zmienne, aby być zadeklarowana śródwierszowo na liście argumentów wywołania metody, gdy jest to możliwe.
- Gdy ta reguła jest ustawiona na **false**, Preferuj `out` zmienne być zadeklarowany przed wywołaniem metody.

Przykłady kodu:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp"></a>Preferencje wyrażeń poziom

Reguły stylów w tej sekcji dotyczą poziomu wyrażenia preferencje, łącznie z użyciem [domyślne wyrażeń](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), śródwierszową zmiennych i funkcji lokalnych za pośrednictwem funkcji anonimowych.

W poniższej tabeli przedstawiono nazwy reguły, identyfikator reguły, wersje językowe odpowiednie, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Visual Studio domyślną | Visual Studio 2017 w wersji |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1+ | true:suggestion | 15.3 |
| csharp_style_deconstructed_variable_declaration | IDE0042 | C# 7.0+ | true:suggestion | 15.5 |
| csharp_style_pattern_local_over_anonymous_function | IDE0039 | C# 7.0+ | true:suggestion | 15.5 |

**csharp\_prefer\_simple\_default_expression**

Ta zasada styl dotyczy przy użyciu [ `default` dosłownie wyrażenia wartości domyślnych](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) Kiedy kompilator może wywnioskować typ wyrażenia.

- Gdy ta reguła jest ustawiona na **true**, Preferuj `default` za pośrednictwem `default(T)`.
- Gdy ta reguła jest ustawiona na **false**, Preferuj `default(T)` za pośrednictwem `default`.

Przykłady kodu:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

**csharp\_style\_deconstructed\_variable_declaration**

- Gdy ta reguła jest ustawiona na **true**, Preferuj śródwierszową deklarację zmiennej.
- Gdy ta reguła jest ustawiona na **false**, nie Preferuj kwalifikatora dekonstrukcja w deklaracjach zmiennych.

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

**csharp\_style\_pattern\_local\_over\_anonymous_function**

- Gdy ta reguła jest ustawiona na **true**, preferowanie funkcji lokalnych za pośrednictwem funkcji anonimowych.
- Gdy ta reguła jest ustawiona na **false**, preferowanie funkcje anonimowe za pośrednictwem funkcji lokalnych.

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

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="null_checking_csharp"></a>"Null" Sprawdzanie preferencje

Te reguły dotyczą stylów składni wokół `null` sprawdzania, w tym o korzystaniu z `throw` wyrażeń lub `throw` instrukcji i czy do wykonywania sprawdzania wartości null lub użyć operatora łączącego warunkowego (`?.`) podczas wywoływania [wyrażenia lambda](/dotnet/csharp/lambda-expressions).

W poniższej tabeli przedstawiono nazwy reguł, identyfikatory reguł, wersje językowe odpowiednie i wartości domyślne:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Visual Studio domyślną |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_throw_expression | IDE0016 | C# 7.0+ | true:suggestion |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0+ | true:suggestion |

**csharp\_style\_throw_expression**

- Gdy ta reguła jest ustawiona na **true**, wolą używać `throw` wyrażeń, zamiast `throw` instrukcji.
- Gdy ta reguła jest ustawiona na **false**, wolą używać `throw` instrukcji zamiast `throw` wyrażenia.

Przykłady kodu:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**

- Gdy ta reguła jest ustawiona na **true**, wolą używać łączącego operator warunkowy (`?.`) podczas wywoływania Wyrażenie lambda, zamiast wykonywania o wartości null zaznacz.
- Gdy ta reguła jest ustawiona na **false**, aby wykonać sprawdzanie wartości null, przed wywołaniem wyrażenia lambda, zamiast korzystać z operatora warunkowego łączącego (`?.`).

Przykłady kodu:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block"></a>Preferencje bloku kodu

Ta zasada styl dotyczy użycia nawiasów klamrowych `{ }` otoczyć bloków kodu.

W poniższej tabeli przedstawiono nazwy reguły, identyfikator reguły, wersje językowe odpowiednie, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Identyfikator reguły | Właściwe języki | Visual Studio domyślną | Visual Studio 2017 w wersji |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_braces | IDE0011 | C# | true:silent | 15.3 |

**CSharp\_Preferuj\_nawiasów klamrowych**

- Gdy ta reguła jest ustawiona na **true**, Preferuj nawiasów klamrowych, nawet w przypadku jednego wiersza kodu.
- Gdy ta reguła jest ustawiona na **false**, Preferuj nie nawiasów klamrowych, jeśli jest to dozwolone.

Przykłady kodu:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

## <a name="formatting-conventions"></a>Konwencje formatowania

Większość reguł konwencje formatowania mają następujący format:

`rule_name = false|true`

Możesz określić **true** (Preferuj ten styl) lub **false** (nie Preferuj kwalifikatora ten styl). Nie określaj ważność. Dla kilku reguł, a nie wartość PRAWDA lub FAŁSZ należy określić inne wartości, które opisują, kiedy i gdzie stosować regułę.

Na poniższej liście przedstawiono reguły formatowania Konwencji dostępne w programie Visual Studio:

- Ustawienia formatowania platformy .NET
    - [Organizuj użycia](#usings)
        - dotnet_sort_system_directives_first
        - dotnet_separate_import_directive_groups
- Ustawienia formatowania C#
    - [Opcje nowego wiersza](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [Opcje wcięć](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [Opcje odstępów](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
        - csharp_space_before_colon_in_inheritance_clause
        - csharp_space_after_colon_in_inheritance_clause
        - csharp_space_around_binary_operators
        - csharp_space_between_method_declaration_empty_parameter_list_parentheses
        - csharp_space_between_method_call_name_and_opening_parenthesis
        - csharp_space_between_method_call_empty_parameter_list_parentheses
    - [Opcje opakowywania](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>Ustawienia formatowania platformy .NET

Reguły formatowania w tej sekcji mają zastosowanie do języka C# i Visual Basic.

#### <a name="usings"></a>Organizuj użycia

Ta reguła formatowania dotyczy położenie Microsoft. i System.* przy użyciu dyrektywy w odniesieniu do innych za pomocą dyrektywy.

W poniższej tabeli przedstawiono nazwy reguły, właściwe języki, wartość domyślna i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Właściwe języki | Visual Studio domyślną | Visual Studio 2017 w wersji |
| ----------- | -------------------- | ----------------------| ---------------- |
| dotnet_sort_system_directives_first | C# i Visual Basic | true | 15.3 |
| dotnet_separate_import_directive_groups | C# i Visual Basic | false | 15.5 |

**dotnet\_sort\_system\_directives_first**

- Gdy ta reguła jest ustawiona na **true**Microsoft. i System.* dyrektywy using alfabetycznie sortować i je umieścić przed innymi deklaracje Using.
- Gdy ta reguła jest ustawiona na **false**, nie należy umieszczać Microsoft. i System.* przy użyciu dyrektyw przed innymi za pomocą dyrektywy.

Przykłady kodu:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

Przykład *.editorconfig* pliku:

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
```

**polecenia DotNet\_oddzielnych\_zaimportować\_dyrektywy\_grup**

- Gdy ta reguła jest ustawiona na **true**, umieść pusty wiersz między grupy dyrektywy using.
- Gdy ta reguła jest ustawiona na **false**, nie należy umieszczać pusty wiersz między grupy dyrektywy using.

Przykłady kodu:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

Przykład *.editorconfig* pliku:

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_separate_import_directive_groups = true
```

### <a name="c-formatting-settings"></a>Ustawienia formatowania C#

Reguły formatowania w tej sekcji dotyczą tylko kodu C#.

#### <a name="newline"></a>Opcje nowego wiersza

Te reguły formatowania dotyczą stosowania nowych wierszy w celu formatowania kodu.

W poniższej tabeli przedstawiono "nowy wiersz" nazwy reguł właściwe języki, wartości domyślne, a najpierw obsługiwaną wersję programu Visual Studio:

| Nazwa zasady | Właściwe języki | Visual Studio domyślną | Visual Studio 2017 w wersji |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_new_line_before_open_brace | C# | wszystkie | 15.3 |
| csharp_new_line_before_else | C# | true | 15.3 |
| csharp_new_line_before_catch | C# | true | 15.3 |
| csharp_new_line_before_finally | C# | true | 15.3 |
| csharp_new_line_before_members_in_object_initializers | C# | true | 15.3 |
| csharp_new_line_before_members_in_anonymous_types | C# | true | 15.3 |
| csharp_new_line_between_query_expression_clauses | C# | true | 15.3 |

**CSharp\_nowe\_wiersza\_przed\_open_brace**

Ta zasada dotyczy czy otwierający nawias klamrowy `{` należy umieścić w tym samym wierszu, jak kod powyżej, lub w nowym wierszu. Dla tej reguły nie określono **true** lub **false**. Zamiast tego należy określić **wszystkich**, **Brak**, lub jeden lub więcej kodu, elementy takie jak **metody** lub **właściwości**, aby zdefiniować, kiedy ta reguła powinna być stosowane. Pełną listę dopuszczalnych wartości zostały przedstawione w poniższej tabeli:

| Wartość | Opis
| ------------- |:-------------|
| metody dostępu, anonymous_methods, anonymous_types, control_blocks, zdarzenia, indeksatory, wyrażenia lambda, local_functions, metody, object_collection_array_initializers, właściwości, typy.<br>(Dla wielu typów, należy oddzielić ','). | Wymagane nawiasy klamrowe w nowym wierszu dla elementów określony kod (znany także jako "Allman" stylu) |
| wszystkie | Wymagane nawiasy klamrowe w nowym wierszu dla wszystkich wyrażeń ("Allman" stylu) |
| brak | Wymagane nawiasy klamrowe, aby być w tym samym wierszu, aby uzyskać wszystkie wyrażenia ("K & R") |

Przykłady kodu:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**CSharp\_nowe\_wiersza\_before_else**

- Gdy ta reguła jest ustawiona na **true**, umieść `else` instrukcji w nowym wierszu.
- Gdy ta reguła jest ustawiona na **false**, umieść `else` instrukcji w tym samym wierszu.

Przykłady kodu:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**csharp\_new\_line\_before_catch**

- Gdy ta reguła jest ustawiona na **true**, umieść `catch` instrukcji w nowym wierszu.
- Gdy ta reguła jest ustawiona na **false**, umieść `catch` instrukcji w tym samym wierszu.

Przykłady kodu:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**CSharp\_nowe\_wiersza\_before_finally**

- Gdy ta reguła jest ustawiona na **true**, wymagają `finally` instrukcji jako po zamykający nawias klamrowy w nowym wierszu.
- Gdy ta reguła jest ustawiona na **false**, wymagają `finally` instrukcji w tym samym wierszu co zamykającego nawiasu klamrowego.

Przykłady kodu:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**CSharp\_nowe\_wiersza\_przed\_członków\_w\_object_initializers**

- Gdy ta reguła jest ustawiona na **true**, wymagają członkowie inicjatorów obiektów w osobnych wierszach.
- Gdy ta reguła jest ustawiona na **false**, wymagają członkowie inicjatorów obiektów na tym samym wierszu.

Przykłady kodu:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**CSharp\_nowe\_wiersza\_przed\_członków\_w\_anonymous_types**

- Gdy ta reguła jest ustawiona na **true**, wymagają składowe typów anonimowych w osobnych wierszach.
- Gdy ta reguła jest ustawiona na **false**, wymagają składowe typów anonimowych, w tym samym wierszu.

Przykłady kodu:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**

- Gdy ta reguła jest ustawiona na **true**, wymagają elementy klauzule wyrażenia zapytania w osobnych wierszach.
- Gdy ta reguła jest ustawiona na **false**, wymagają elementy klauzule wyrażenia zapytania w tym samym wierszu.

Przykłady kodu:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="indent"></a>Opcje wcięć

Te reguły formatowania dotyczą użytkowania wcięcia w celu formatowania kodu.

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Właściwe języki | Visual Studio domyślną | Visual Studio 2017 w wersji |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_indent_case_contents | C# | true | 15.3 |
| csharp_indent_switch_labels | C# | true | 15.3 |
| csharp_indent_labels | C# | no_change | 15.3 |

**csharp\_indent\_case_contents**

- Gdy ta reguła jest ustawiona na **true**, wcięcia `switch` zamierzone, Zapisz zawartość.
- Gdy ta reguła jest ustawiona na **false**, nie twórz wcięcie `switch` zamierzone, Zapisz zawartość.

Przykłady kodu:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent\_switch_labels**

- Gdy ta reguła jest ustawiona na **true**, wcięcia `switch` etykiety.
- Gdy ta reguła jest ustawiona na **false**, nie twórz wcięcie `switch` etykiety.

Przykłady kodu:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent_labels**

Ta zasada nie akceptuje **true** lub **false** wartość; zamiast tego przyjmuje wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:----------- |
| flush_left | Etykiety są umieszczane w skrajnej lewej kolumnie |
| one_less_than_current | Etykiety są umieszczane w jednej mniej wcięcie bieżącego kontekstu |
| no_change | Etykiety są umieszczane w tej samej wcięcie jako bieżący kontekst |

Przykłady kodu:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="spacing"></a>Opcje odstępów

Te reguły formatowania dotyczy użycia znaków spacji do formatowania kodu.

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Właściwe języki | Visual Studio domyślną | Visual Studio 2017 w wersji |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_space_after_cast | C# | false | 15.3 |
| csharp_space_after_keywords_in_control_flow_statements | C# | true | 15.3 |
| csharp_space_between_method_declaration_parameter_list_parentheses | C# | false | 15.3 |
| csharp_space_between_method_call_parameter_list_parentheses | C# | false | 15.3 |
| csharp_space_between_parentheses | C# | false | 15.3 |
| csharp_space_before_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_after_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_around_binary_operators | C# | before_and_after | 15.7 |
| csharp_space_between_method_declaration_empty_parameter_list_parentheses | C# | false | 15.7 |
| csharp_space_between_method_call_name_and_opening_parenthesis | C# | false | 15.7 |
| csharp_space_between_method_call_empty_parameter_list_parentheses | C# | false | 15.7 |

**csharp\_space\_after_cast**

- Gdy ta reguła jest ustawiona na **true**, wymagają odstęp między rzutowanie, jak i wartość.
- Gdy ta reguła jest ustawiona na **false**, wymagają _nie_ odstęp między rzutowanie, jak i wartość.

Przykłady kodu:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**

- Gdy ta reguła jest ustawiona na **true**, takich jak wymagać spację po słowem kluczowym w instrukcji przepływu sterowania `for` pętli.
- Gdy ta reguła jest ustawiona na **false**, wymagają _nie_ spację po słowem kluczowym w instrukcji przepływu sterowania, takich jak `for` pętli.

Przykłady kodu:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**

- Gdy ta reguła jest ustawiona na **true**, umieść znak spacji po nawiasie otwierającym, a także przed zamykającym w liście parametrów deklaracji metody.
- Gdy ta reguła jest ustawiona na **false**, nie należy umieszczać znaków spacji po nawiasie otwierającym, a także przed zamykającym w liście parametrów deklaracji metody.

Przykłady kodu:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**

- Gdy ta reguła jest ustawiona na **true**, umieść znak spacji po nawiasie otwierającym, a także przed nawiasem zamykającym wywołania metody.
- Gdy ta reguła jest ustawiona na **false**, nie należy umieszczać znaków spacji po nawiasie otwierającym, a także przed nawiasem zamykającym wywołania metody.

Przykłady kodu:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**

Ta reguła akceptuje co najmniej jednej wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:------------|
| control_flow_statements | Umieść odstęp między nawiasów instrukcji przepływu sterowania |
| wyrażenia | Umieść odstęp między nawiasy, wyrażeń |
| type_casts | Umieść odstęp między nawiasy w rzutowania typów |

Możesz pominąć tę regułę, czy używać wartości innych niż `control_flow_statements`, `expressions`, lub `type_casts`, to ustawienie nie ma zastosowania.

Przykłady kodu:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

**csharp\_space\_before\_colon\_in\_inheritance_clause**

- Gdy ta reguła jest ustawiona na **true**, wymagają spację przed dwukropkiem w przypadku baz lub interfejsy w deklaracji typu.
- Gdy ta reguła jest ustawiona na **false**, wymagają _nie_ spację przed dwukropkiem w przypadku baz lub interfejsy w deklaracji typu.

Przykłady kodu:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

**csharp\_space\_after\_colon\_in\_inheritance_clause**

- Gdy ta reguła jest ustawiona na **true**, wymagają spację po dwukropku w przypadku baz lub interfejsy w deklaracji typu.
- Gdy ta reguła jest ustawiona na **false**, wymagają _nie_ spację po dwukropku w przypadku baz lub interfejsy w deklaracji typu.

Przykłady kodu:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

**CSharp\_miejsca\_wokół\_binary_operators**

Ta reguła akceptuje jednej wartości z poniższej tabeli:

| Wartość | Opis |
| ----- |:------------|
| before_and_after | Wstaw spację przed i po operatora binarnego |
| brak | Usuwaj odstępy przed i po nim operatora binarnego |
| ignoruj | Ignoruj spacje dookoła operatorów dwuargumentowych |

Możesz pominąć tę regułę, czy używać wartości innych niż `before_and_after`, `none`, lub `ignore`, to ustawienie nie ma zastosowania.

Przykłady kodu:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

**csharp_space_between_method_declaration_empty_parameter_list_parentheses**

- Gdy ta reguła jest ustawiona na **true**, Wstaw spację wewnątrz nawiasów listy parametrów empty w deklaracji metody.
- Gdy ta reguła jest ustawiona na **false**, Usuń odstęp wewnątrz nawiasów listy parametrów empty w deklaracji metody.

Przykłady kodu:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_name_and_opening_parenthesis**

- Gdy ta reguła jest ustawiona na **true**, Wstaw spację między nazwę wywołanie metody i nawias otwierający.
- Gdy ta reguła jest ustawiona na **false**, usunąć spację między nazwę wywołanie metody i nawias otwierający.

Przykłady kodu:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_empty_parameter_list_parentheses**

- Gdy ta reguła jest ustawiona na **true**, Wstaw spację wewnątrz nawiasów listy pusty argument.
- Gdy ta reguła jest ustawiona na **false**, Usuń odstęp wewnątrz nawiasów listy pusty argument.

Przykłady kodu:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
```

#### <a name="wrapping"></a>Opcje opakowywania

Te reguły formatowania dotyczą użytkowania pojedynczych wierszy w porównaniu z osobnych wierszach instrukcji i bloków kodu.

W poniższej tabeli przedstawiono nazwy reguł, właściwe języki, wartości domyślne i pierwszej obsługiwanej wersji programu Visual Studio:

| Nazwa zasady | Właściwe języki | Visual Studio domyślną | Visual Studio 2017 w wersji |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_preserve_single_line_statements | C# | true | 15.3 |
| csharp_preserve_single_line_blocks | C# | true | 15.3 |

**csharp_preserve_single_line_statements**

- Gdy ta reguła jest ustawiona na **true**, pozostaw instrukcje i deklaracje składowych w tym samym wierszu.
- Gdy ta reguła jest ustawiona na **false**, pozostaw instrukcje i deklaracje składowych w różnych wierszach.

Przykłady kodu:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

**csharp_preserve_single_line_blocks**

- Gdy ta reguła jest ustawiona na **true**, pozostaw blok kodu w pojedynczym wierszu.
- Gdy ta reguła jest ustawiona na **false**, pozostaw blok kodu w osobnych wierszach.

Przykłady kodu:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

Przykład *.editorconfig* pliku:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="example-editorconfig-file"></a>Przykładowy plik wtyczki EditorConfig

Aby ułatwić Ci rozpoczęcie pracy, w tym miejscu znajduje się przykład *.editorconfig* pliku z opcjami domyślnymi:

```EditorConfig
###############################
# Core EditorConfig Options   #
###############################

root = true

# All files
[*]
indent_style = space

# Code files
[*.{cs,csx,vb,vbx}]
indent_size = 4
insert_final_newline = true
charset = utf-8-bom

###############################
# .NET Coding Conventions     #
###############################

[*.{cs,vb}]
# Organize usings
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = false

# this. preferences
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_property = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_event = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent
dotnet_style_readonly_field = true:suggestion

# Expression-level preferences
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent

###############################
# Naming Conventions          #
###############################

# Style Definitions
dotnet_naming_style.pascal_case_style.capitalization             = pascal_case

# Use PascalCase for constant fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.constant_fields_should_be_pascal_case.symbols  = constant_fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.style    = pascal_case_style
dotnet_naming_symbols.constant_fields.applicable_kinds            = field
dotnet_naming_symbols.constant_fields.applicable_accessibilities  = *
dotnet_naming_symbols.constant_fields.required_modifiers          = const

###############################
# C# Code Style Rules         #
###############################

[*.cs]
# var preferences
csharp_style_var_for_built_in_types = true:silent
csharp_style_var_when_type_is_apparent = true:silent
csharp_style_var_elsewhere = true:silent

# Expression-bodied members
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_accessors = true:silent

# Pattern-matching preferences
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion

# Null-checking preferences
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Expression-level preferences
csharp_prefer_braces = true:silent
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion

###############################
# C# Formatting Rules         #
###############################

# New line preferences
csharp_new_line_before_open_brace = all
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left

# Space preferences
csharp_space_after_cast = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false

# Wrapping preferences
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true

##################################
# Visual Basic Code Style Rules  #
##################################

[*.vb]
# Modifier preferences
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje](../ide/quick-actions.md)
- [Konwencje nazewnictwa platformy .NET dla wtyczki EditorConfig](../ide/editorconfig-naming-conventions.md)
- [Tworzenie przenośnych niestandardowy Edytor opcji](../ide/create-portable-custom-editor-options.md)
- [Platforma kompilatora .NET pliku .editorconfig](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
