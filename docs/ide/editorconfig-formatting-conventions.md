---
title: Konwencje formatowania .NET dla EditorConfig
ms.date: 04/02/2020
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 136744514e5e2e49ec92a443ac590eb5cc34418a
ms.sourcegitcommit: c3b6af7367bef67a02c37404534229b935f713a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80892765"
---
# <a name="formatting-conventions"></a>Konwencje formatowania

Konwencje formatowania dla EditorConfig for Visual Studio należą do następujących kategorii:

- [Ustawienia formatowania .NET](#net-formatting-settings)

- [Ustawienia formatowania języka C#](#c-formatting-settings)

## <a name="rule-format"></a>Format reguły

Reguły konwencji formatowania mają następujący format:

`rule_name = value`

W przypadku wielu reguł `true` należy określić opcję `false` (preferuj ten `value`styl) lub (nie preferuj tego stylu) dla pliku . W przypadku innych reguł należy `flush_left` określić wartość, taką jak lub `before_and_after` opisać, kiedy i gdzie zastosować regułę. Nie określasz ważności.

## <a name="net-formatting-settings"></a>Ustawienia formatowania .NET

Reguły formatowania w tej sekcji dotyczą kodu języka C# i języka Visual Basic.

- [Organizowanie użycia](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Organizowanie przy użyciu dyrektyw

Te reguły formatowania dotyczą sortowania i wyświetlania `using` dyrektyw i `Imports` instrukcji.

Przykład *pliku .editorconfig:*

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a>directives_first systemu\_\_\_sortowania dotnet

|||
|-|-|
| **Nazwa reguły** | dotnet_sort_system_directives_first |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- Sortuj `using` dyrektywy systemowe.* alfabetycznie i umieść je przed innymi dyrektywami.<br /><br />`false`- Nie umieszczaj `using` dyrektyw systemowych.* przed innymi `using` dyrektywami. |

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

#### <a name="dotnet_separate_import_directive_groups"></a>grupy\_oddzielnych\_\_dyrektyw\_importowych dotnet

|||
|-|-|
| **Nazwa reguły** | dotnet_separate_import_directive_groups |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.5 |
| **Wartości** | `true`- Umieść pustą `using` linię między grupami dyrektyw.<br /><br />`false`- Nie należy umieszczać `using` pustej linii między grupami dyrektyw. |

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

## <a name="c-formatting-settings"></a>Ustawienia formatowania języka C#

Reguły formatowania w tej sekcji dotyczą tylko kodu języka C#.

- [Opcje nowej linii](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Opcje wcięcie](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
  - csharp_indent_block_contents
  - csharp_indent_braces
  - csharp_indent_case_contents_when_block
- [Opcje odstępów](#spacing-options)
  - csharp_space_after_cast
  - csharp_space_after_keywords_in_control_flow_statements
  - csharp_space_between_parentheses
  - csharp_space_before_colon_in_inheritance_clause
  - csharp_space_after_colon_in_inheritance_clause
  - csharp_space_around_binary_operators
  - csharp_space_between_method_declaration_parameter_list_parentheses
  - csharp_space_between_method_declaration_empty_parameter_list_parentheses
  - csharp_space_between_method_declaration_name_and_open_parenthesis
  - csharp_space_between_method_call_parameter_list_parentheses
  - csharp_space_between_method_call_empty_parameter_list_parentheses
  - csharp_space_between_method_call_name_and_opening_parenthesis
  - csharp_space_after_comma
  - csharp_space_before_comma
  - csharp_space_after_dot
  - csharp_space_before_dot
  - csharp_space_after_semicolon_in_for_statement
  - csharp_space_before_semicolon_in_for_statement
  - csharp_space_around_declaration_statements
  - csharp_space_before_open_square_brackets
  - csharp_space_between_empty_square_brackets
  - csharp_space_between_square_brackets
- [Opcje zawijania](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks
- [Korzystanie z opcji dyrektywy](#using-directive-options) 
  - csharp_using_directive_placement

### <a name="new-line-options"></a>Opcje nowej linii

Te reguły formatowania dotyczą używania nowych wierszy do formatowania kodu.

Przykład *pliku .editorconfig:*

```ini
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

#### <a name="csharp_new_line_before_open_brace"></a>csharp\_\_nowa\_\_linia przed open_brace

Ta reguła dotyczy tego, czy otwarty nawias klamrowy `{` powinien być umieszczony w tym samym wierszu co poprzedni kod, czy w nowym wierszu. Dla tej reguły należy określić **wszystkie**, **brak**lub jeden lub więcej elementów kodu, takich jak **metody** lub **właściwości,** aby zdefiniować, kiedy ta reguła ma być stosowana. Aby określić wiele elementów kodu, oddziel je przecinkiem (,).

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_open_brace |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `all`- Wymagaj, aby nawiasy klamrowe były w nowym wierszu dla wszystkich wyrażeń (styl "Allman").<br /><br />`none`- Wymagaj, aby nawiasy klamrowe były w tym samym wierszu dla wszystkich wyrażeń ("K&R").<br /><br />`accessors`, `anonymous_methods` `anonymous_types`, `control_blocks` `events`, `indexers` `lambdas`, `local_functions` `methods`, `object_collection_array_initializers` `properties`, `types` , , , , - Wymagaj, aby nawiasy klamrowe były w nowym wierszu dla określonego elementu kodu (styl "Allman"). |

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

#### <a name="csharp_new_line_before_else"></a>csharp\_\_nowa\_linia before_else

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_else |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- `else` Umieść instrukcje w nowym wierszu.<br /><br />`false`- `else` Umieść instrukcje w tym samym wierszu. |

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

#### <a name="csharp_new_line_before_catch"></a>csharp\_\_nowa\_linia before_catch

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_catch |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- `catch` Umieść instrukcje w nowym wierszu.<br /><br />`false`- `catch` Umieść instrukcje w tym samym wierszu. |

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

#### <a name="csharp_new_line_before_finally"></a>csharp\_\_nowa\_linia before_finally

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_finally |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- `finally` Wymagaj instrukcji, aby być w nowym wierszu po nawiasie klamrowym zamknięcia.<br /><br />`false`- `finally` Wymagaj instrukcji, aby być w tym samym wierszu co nawias zamykający. |

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

#### <a name="csharp_new_line_before_members_in_object_initializers"></a>csharp\_\_nowej\_\_linii\_\_przed członkami w object_initializers

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_members_in_object_initializers |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- Wymagaj, aby elementy inicjatorów obiektów były w oddzielnych wierszach<br /><br />`false`- Wymagaj, aby członkowie inicjatorów obiektów znajdować się w tym samym wierszu |

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

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a>csharp\_\_nowej\_\_linii\_\_przed członkami w anonymous_types

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_members_in_anonymous_types |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- Wymagaj, aby członkowie anonimowych typów znajdować się w oddzielnych wierszach<br /><br />`false`- Wymagaj, aby członkowie anonimowych typów znajdować się w tym samym wierszu |

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

#### <a name="csharp_new_line_between_query_expression_clauses"></a>csharp_new_line_between_query_expression_clauses

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_between_query_expression_clauses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- Wymagaj, aby elementy klauzul wyrażenia kwerendy były w oddzielnych wierszach<br /><br />`false`- Wymagaj, aby elementy klauzul wyrażenia zapytania były w tym samym wierszu |

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

### <a name="indentation-options"></a>Opcje wcięcie

Te reguły formatowania dotyczą użycia wcięci do formatowania kodu.

Przykład *pliku .editorconfig:*

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharp_indent_case_contents"></a>case_contents\_wcięcie\_csharp

|||
|-|-|
| **Nazwa reguły** | csharp_indent_case_contents |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- Zawartość `switch` wcięcie wielkości liter<br /><br />`false`- Nie wcięcie `switch` treści wielkości liter |

- Gdy ta reguła jest ustawiona na **true**, i.
- Gdy ta reguła jest ustawiona na **false**, d.

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

#### <a name="csharp_indent_switch_labels"></a>switch_labels\_wcięcie\_csharp

|||
|-|-|
| **Nazwa reguły** | csharp_indent_switch_labels |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- Etykiety `switch` wcięcie<br /><br />`false`- Nie wcięć `switch` etykiet |

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

#### <a name="csharp_indent_labels"></a>\_indent_labels

|||
|-|-|
| **Nazwa reguły** | csharp_indent_labels |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `flush_left`- Etykiety są umieszczane w lewej kolumnie<br /><br />`one_less_than_current`- Etykiety są umieszczane w jednym mniejszym wcięcie do bieżącego kontekstu<br /><br />`no_change`- Etykiety są umieszczane w tym samym tiret co bieżący kontekst |

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

#### <a name="csharp_indent_block_contents"></a>csharp_indent_block_contents

|||
|-|-|
| **Nazwa reguły** | csharp_indent_block_contents |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` - <br /><br />`false` -  |

Przykłady kodu:

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_braces"></a>csharp_indent_braces

|||
|-|-|
| **Nazwa reguły** | csharp_indent_braces |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` - <br /><br />`false` -  |

Przykłady kodu:

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_case_contents_when_block"></a>csharp_indent_case_contents_when_block

|||
|-|-|
| **Nazwa reguły** | csharp_indent_case_contents_when_block |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` - <br /><br />`false` -  |

Przykłady kodu:

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a>Opcje odstępów

Te reguły formatowania dotyczą używania znaków spacji do formatowania kodu.

Przykład *pliku .editorconfig:*

```ini
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharp_space_after_cast"></a>after_cast\_kosmiczna\_csharp

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_cast |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- Umieść znak spacji między rzutem a wartością<br /><br />`false`- Usuń spację między rzutem a wartością |

Przykłady kodu:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a>csharp_space_after_keywords_in_control_flow_statements

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_keywords_in_control_flow_statements |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- Umieść znak spacji po słowie słowa `for` kluczowego w instrukcji przepływu sterowania, takiej jak pętla<br /><br />`false`- Usuń miejsce po słowie słowa `for` kluczowego w instrukcji przepływu sterowania, takiej jak pętla |

Przykłady kodu:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a>csharp_space_between_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `control_flow_statements`- Umieść odstęp między nawiasami instrukcji przepływu sterowania<br /><br />`expressions`- Umieść odstęp między nawiasami wyrażeń<br /><br />`type_casts`- Umieść odstęp między nawiasami w rzutkach typu |

Jeśli ta reguła zostanie pominięta `control_flow_statements`lub `expressions`zostanie `type_casts`użyta wartość inna niż , lub , ustawienie nie zostanie zastosowane.

Przykłady kodu:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a>csharp\_\_przestrzeń\_\_przed\_dwukropek w inheritance_clause

|||
|-|-|
| **Nazwa reguły** | csharp_space_before_colon_in_inheritance_clause |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true`- Umieść znak spacji przed dwukropkiem dla baz lub interfejsów w deklaracji typu<br /><br />`false`- Usuń miejsce przed dwukropkiem dla baz lub interfejsów w deklaracji typu |

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

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a>csharp\_\_przestrzeń\_\_po\_dwukropku w inheritance_clause

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_colon_in_inheritance_clause |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true`- Umieść znak spacji po dwukropku dla baz lub interfejsów w deklaracji typu<br /><br />`false`- Usuń miejsce po dwukropku dla baz lub interfejsów w deklaracji typu |

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

#### <a name="csharp_space_around_binary_operators"></a>przestrzeń\_\_csharp\_wokół binary_operators

|||
|-|-|
| **Nazwa reguły** | csharp_space_around_binary_operators |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `before_and_after`- Wstaw spację przed i po operatorze binarnym<br /><br />`none`- Usuń spacje przed i po operator binarny<br /><br />`ignore`- Ignoruj spacja wokół operatorów binarnych |

Jeśli ta reguła zostanie pominięta lub `before_and_after` `none`użyjesz wartości innej niż , lub `ignore`, ustawienie nie zostanie zastosowane.

Przykłady kodu:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- Umieść znak spacji po nawiasie otwierającym i przed nawiasem zamykającym listę parametrów deklaracji metody<br /><br />`false`- Usuń znaki spacji po nawiasie otwierającym i przed nawiasem zamykającym listę parametrów deklaracji metody |

Przykłady kodu:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true`- Wstawianie miejsca w pustych nawiasach listy parametrów dla deklaracji metody<br /><br />`false`- Usuwanie miejsca w pustych nawiasach listy parametrów dla deklaracji metody |

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

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a>csharp_space_between_method_declaration_name_and_open_parenthesis

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`- Umieść znak spacji między nazwą metody a nawiasem otwierającym w deklaracji metody<br /><br />`false`- Usuń znaki spacji między nazwą metody a nawiasem otwierającym w deklaracji metody |

Przykłady kodu:

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_call_parameter_list_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- Umieść znak spacji po nawiasie otwierającym i przed nawiasem zamykającym wywołanie metody<br /><br />`false`- Usuń znaki spacji po nawiasie otwierającym i przed nawiasem zamykającym wywołanie metody |

Przykłady kodu:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true`- Wstawianie miejsca w nawiasach pustej listy argumentów<br /><br />`false`- Usuwanie miejsca w pustych nawiasach listy argumentów |

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

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true`- Wstaw odstęp między nazwą wywołania metody a nawiasem otwarcia<br /><br />`false`- Usuń spację między nazwą wywołania metody i nawiasem otwarcia |

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

#### <a name="csharp_space_after_comma"></a>csharp_space_after_comma

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_comma |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`- Włóż spację po przecinkom<br /><br />`false`- Usuń miejsce po przecinkom |

Przykłady kodu:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a>csharp_space_before_comma

|||
|-|-|
| **Nazwa reguły** | csharp_space_before_comma |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`- Wstaw spację przed przecinkiem<br /><br />`false`- Usuń miejsce przed przecinkiem |

Przykłady kodu:

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a>csharp_space_after_dot

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_dot |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`- Wstaw spację po kroju<br /><br />`false`- Usuń spację po krosnie |

Przykłady kodu:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a>csharp_space_before_dot

|||
|-|-|
| **Nazwa reguły** | csharp_space_before_dot |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`- Wstaw spację przed kropką <br /><br />`false`- Usuń miejsce przed kropką |

Przykłady kodu:

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a>csharp_space_after_semicolon_in_for_statement

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_semicolon_in_for_statement |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`- Wstaw spację po `for` każdym średnikowym w instrukcji<br /><br />`false`- Usuń miejsce po każdym `for` średnik w instrukcji |

Przykłady kodu:

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a>csharp_space_before_semicolon_in_for_statement

|||
|-|-|
| **Nazwa reguły** | csharp_space_before_semicolon_in_for_statement |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`- Wstaw spację przed `for` każdym średnikiem w instrukcji <br /><br />`false`- Usuń miejsce przed każdym `for` średnikiem w instrukcji |

Przykłady kodu:

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a>csharp_space_around_declaration_statements

|||
|-|-|
| **Nazwa reguły** | csharp_space_around_declaration_statements |
| **Odpowiednie języki** | C# |
| **Wartości** | `ignore`- Nie usuwaj dodatkowych znaków spacji w instrukcjach deklaracji<br /><br />`false`- Usuń dodatkowe znaki spacji w instrukcjach deklaracji |

Przykłady kodu:

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a>csharp_space_before_open_square_brackets

|||
|-|-|
| **Nazwa reguły** | csharp_space_before_open_square_brackets |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`- Włóż przestrzeń przed otwarciem wsporników kwadratowych`[` <br /><br />`false`- Usuń miejsce przed otwarciem nawiasów kwadratowych`[` |

Przykłady kodu:

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a>csharp_space_between_empty_square_brackets

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_empty_square_brackets |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`- Wstaw przestrzeń między pustymi nawiasami kwadratowymi`[ ]` <br /><br />`false`- Usuń przestrzeń między pustymi nawiasami kwadratowymi`[]` |

Przykłady kodu:

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a>csharp_space_between_square_brackets

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_square_brackets |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`- Wstaw znaki spacji w niepustych nawiasach kwadratowych`[ 0 ]` <br /><br />`false`- Usuń znaki spacji w niepustych nawiasach kwadratowych`[0]` |

Przykłady kodu:

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a>Opcje zawijania

Te reguły formatowania dotyczą użycia pojedynczych wierszy w porównaniu z oddzielnymi wierszami dla instrukcji i bloków kodu.

Przykład *pliku .editorconfig:*

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a>csharp_preserve_single_line_statements

|||
|-|-|
| **Nazwa reguły** | csharp_preserve_single_line_statements |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- Zostaw instrukcje i deklaracje członkowskie w tym samym wierszu<br /><br />`false`- Zostaw instrukcje i deklaracje członkowskie w różnych wierszach |

Przykłady kodu:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a>csharp_preserve_single_line_blocks

|||
|-|-|
| **Nazwa reguły** | csharp_preserve_single_line_blocks |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true`- Zostaw blok kodu w jednym wierszu<br /><br />`false`- Zostaw blok kodu na oddzielnych liniach |

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

### <a name="using-directive-options"></a>Korzystanie z opcji dyrektywy

Ta reguła formatowania dotyczy użycia za pomocą dyrektyw umieszczanych wewnątrz i poza obszarem nazw.

Przykład *pliku .editorconfig:*

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a>csharp_using_directive_placement

|||
|-|-|
| **Nazwa reguły** | csharp_using_directive_placement |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2019 w wersji 16.1 |
| **Wartości** | `outside_namespace`- Zostaw za pomocą dyrektyw poza obszarem nazw<br /><br />`inside_namespace`- Zostaw za pomocą dyrektyw wewnątrz obszaru nazw |

Przykłady kodu:

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{

}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
}
```

## <a name="see-also"></a>Zobacz też

- [Konwencje języka](editorconfig-language-conventions.md)
- [Konwencje nazewnictwa](editorconfig-naming-conventions.md)
- [Ustawienia konwencji kodowania .NET dla EditorConfig](editorconfig-code-style-settings-reference.md)
