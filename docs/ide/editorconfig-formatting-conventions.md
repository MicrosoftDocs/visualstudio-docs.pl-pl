---
title: Konwencje formatowania platformy .NET dla EditorConfig
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
ms.openlocfilehash: 0490912683fd683398c89e8e69b62dd3824ee04b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533474"
---
# <a name="formatting-conventions"></a>Konwencje formatowania

Konwencje formatowania dla EditorConfig dla programu Visual Studio należą do następujących kategorii:

- [Ustawienia formatowania platformy .NET](#net-formatting-settings)

- [Ustawienia formatowania języka C#](#c-formatting-settings)

## <a name="rule-format"></a>Format reguły

Reguły dla Konwencji formatowania mają następujący format:

`rule_name = value`

W przypadku wielu reguł należy określić jeden `true` (Preferuj ten styl) lub `false` (nie Preferuj tego stylu) dla `value` . W przypadku innych reguł należy określić wartość taką jak `flush_left` lub, `before_and_after` aby opisać, kiedy i gdzie należy zastosować regułę. Nie określisz ważności.

## <a name="net-formatting-settings"></a>Ustawienia formatowania platformy .NET

Reguły formatowania w tej sekcji dotyczą kodu C# i Visual Basic.

- [Organizuj użycia](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Organizuj dyrektywy using

Te reguły formatowania dotyczą sortowania i wyświetlania `using` dyrektyw i `Imports` instrukcji.

Przykładowy plik *. editorconfig* :

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a>\_ \_ directives_first systemu sortowania \_ dotnet

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | dotnet_sort_system_directives_first |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Sortuj dyrektywy System. * `using` w porządku alfabetycznym i umieść je przed innymi przy użyciu dyrektyw.<br /><br />`false` -Nie umieszczaj dyrektyw system. * `using` przed innymi `using` dyrektywami. |

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

#### <a name="dotnet_separate_import_directive_groups"></a>\_ \_ \_ grupy dyrektywy dotyczącej importowania oddzielnych dotnet \_

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | dotnet_separate_import_directive_groups |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.5 |
| **Wartości** | `true` — Należy umieścić pusty wiersz między `using` grupami dyrektyw.<br /><br />`false` — Nie umieszczaj pustego wiersza między `using` grupami dyrektyw. |

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

Reguły formatowania w tej sekcji dotyczą tylko kodu w języku C#.

- [Opcje nowego wiersza](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Opcje wcięć](#indentation-options)
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

### <a name="new-line-options"></a>Opcje nowego wiersza

Te reguły formatowania dotyczą korzystania z nowych wierszy do formatowania kodu.

Przykładowy plik *. editorconfig* :

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

#### <a name="csharp_new_line_before_open_brace"></a>CSharp \_ Nowy \_ wiersz \_ przed \_ open_brace

Ta zasada ma wpływ na to, czy otwierający nawias klamrowy `{` powinien być umieszczony w tym samym wierszu co poprzedni kod, czy w nowym wierszu. Dla tej reguły należy określić **wszystkie**, **Brak**lub co najmniej jeden element kodu, taki jak **metody** lub **Właściwości**, aby określić, kiedy ta reguła ma być stosowana. Aby określić wiele elementów kodu, rozdziel je przecinkami (,).

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_new_line_before_open_brace |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `all` -Wymagaj nawiasów klamrowych w nowym wierszu dla wszystkich wyrażeń (styl "Allman").<br /><br />`none` -Wymagaj nawiasów klamrowych w tym samym wierszu dla wszystkich wyrażeń ("K&R").<br /><br />`accessors`,,,,,,,,,, `anonymous_methods` `anonymous_types` `control_blocks` `events` `indexers` `lambdas` `local_functions` `methods` `object_collection_array_initializers` `properties` , `types` — Wymagaj nawiasów klamrowych, aby znajdować się w nowym wierszu dla określonego elementu kodu (styl "Allman"). |

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

#### <a name="csharp_new_line_before_else"></a>CSharp \_ Nowy \_ wiersz \_ before_else

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_new_line_before_else |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Umieść `else` instrukcje w nowym wierszu.<br /><br />`false` -Umieść `else` instrukcje w tym samym wierszu. |

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

#### <a name="csharp_new_line_before_catch"></a>CSharp \_ Nowy \_ wiersz \_ before_catch

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_new_line_before_catch |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Umieść `catch` instrukcje w nowym wierszu.<br /><br />`false` -Umieść `catch` instrukcje w tym samym wierszu. |

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

#### <a name="csharp_new_line_before_finally"></a>CSharp \_ Nowy \_ wiersz \_ before_finally

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_new_line_before_finally |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Wymagaj `finally` instrukcji w nowym wierszu po nawiasie zamykającym.<br /><br />`false` -Wymagaj `finally` instrukcji w tym samym wierszu co zamykający nawias klamrowy. |

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

#### <a name="csharp_new_line_before_members_in_object_initializers"></a>CSharp \_ Nowy \_ wiersz \_ przed \_ elementami członkowskimi \_ w \_ object_initializers

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_new_line_before_members_in_object_initializers |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Wymagane składowe inicjatorów obiektów muszą znajdować się w osobnych wierszach<br /><br />`false` -Wymagane składowe inicjatorów obiektów powinny znajdować się w tym samym wierszu |

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

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a>CSharp \_ Nowy \_ wiersz \_ przed \_ elementami członkowskimi \_ w \_ anonymous_types

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_new_line_before_members_in_anonymous_types |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Wymagaj elementów członkowskich typu anonimowego w osobnych wierszach<br /><br />`false` -Wymagane składowe typów anonimowych mogą znajdować się w tym samym wierszu |

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

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_new_line_between_query_expression_clauses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Wymagaj elementów klauzul wyrażeń zapytania w osobnych wierszach<br /><br />`false` -Wymagaj elementów klauzul wyrażeń zapytania, aby znajdować się w tym samym wierszu |

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

### <a name="indentation-options"></a>Opcje wcięć

Te reguły formatowania dotyczą użycia wcięć do formatowania kodu.

Przykładowy plik *. editorconfig* :

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

#### <a name="csharp_indent_case_contents"></a>CSharp \_ wcięcie \_ case_contents

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_indent_case_contents |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` — Wcięcie `switch` zawartości przypadku<br /><br />`false` -Nie Wetnij `switch` zawartości wielkości liter |

- Gdy ta reguła ma **wartość true**, i.
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

#### <a name="csharp_indent_switch_labels"></a>CSharp \_ wcięcie \_ switch_labels

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_indent_switch_labels |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Wcięcia `switch` etykiet<br /><br />`false` — Nie Wetnij `switch` etykiet |

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

#### <a name="csharp_indent_labels"></a>CSharp \_ indent_labels

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_indent_labels |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `flush_left` -Etykiety są umieszczane w kolumnie z lewej strony<br /><br />`one_less_than_current` -Etykiety są umieszczane w jednym z niższych wcięć w bieżącym kontekście<br /><br />`no_change` -Etykiety są umieszczane w tym samym powiększeniu co bieżący kontekst |

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

|Właściwość|Wartość|
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

|Właściwość|Wartość|
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

|Właściwość|Wartość|
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

Przykładowy plik *. editorconfig* :

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

#### <a name="csharp_space_after_cast"></a>CSharp \_ \_ after_cast miejsca

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_after_cast |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Umieść znak spacji między rzutem a wartością<br /><br />`false` -Usuń odstęp między rzutem a wartością |

Przykłady kodu:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a>csharp_space_after_keywords_in_control_flow_statements

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_after_keywords_in_control_flow_statements |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Umieść znak spacji po słowie kluczowym w instrukcji przepływu sterowania, takiej jak `for` Pętla<br /><br />`false` -Usuń spację po słowie kluczowym w instrukcji przepływu sterowania, takiej jak `for` Pętla |

Przykłady kodu:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a>csharp_space_between_parentheses

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_between_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `control_flow_statements` -Umieść miejsce między nawiasami instrukcji przepływu sterowania<br /><br />`expressions` -Miejsce między nawiasami wyrażenia<br /><br />`type_casts` -Umieść miejsce między nawiasami w rzutach typu |

Jeśli pominięto tę regułę lub użyjesz wartości innej niż `control_flow_statements` , `expressions` lub `type_casts` , to ustawienie nie jest stosowane.

Przykłady kodu:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a>CSharp \_ spację \_ przed \_ dwukropkiem \_ w \_ inheritance_clause

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_before_colon_in_inheritance_clause |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true` -Umieść znak spacji przed dwukropkiem dla baz lub interfejsów w deklaracji typu<br /><br />`false` -Usuń spację przed dwukropkiem dla baz lub interfejsów w deklaracji typu |

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

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a>CSharp \_ spację \_ po \_ dwukropku \_ w \_ inheritance_clause

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_after_colon_in_inheritance_clause |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true` -Umieść znak spacji po dwukropku dla baz lub interfejsów w deklaracji typu<br /><br />`false` -Usuń spację po dwukropku dla podstaw lub interfejsów w deklaracji typu |

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

#### <a name="csharp_space_around_binary_operators"></a>CSharp \_ miejsce \_ dookoła \_ binary_operators

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_around_binary_operators |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `before_and_after` -Wstaw spację przed i po operatorze Binary<br /><br />`none` -Usuń odstępy przed i po operatorze Binary<br /><br />`ignore` -Ignoruj odstępy dookoła operatorów binarnych |

Jeśli pominięto tę regułę lub używasz wartości innej niż `before_and_after` , `none` lub `ignore` , ustawienie nie jest stosowane.

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

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Umieść znak spacji po nawiasie otwierającym i przed nawiasem zamykającym listy parametrów deklaracji metody<br /><br />`false` -Usuń znaki spacji po nawiasie otwierającym i przed nawiasem zamykającym listy parametrów deklaracji metody |

Przykłady kodu:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true` -Wstaw odstęp wewnątrz nawiasów listy pustych parametrów dla deklaracji metody<br /><br />`false` -Usuń spację w nawiasach listy pustych parametrów dla deklaracji metody |

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

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` -Umieść znak spacji między nazwą metody i nawiasem otwierającym w deklaracji metody<br /><br />`false` -Usuń znaki spacji między nazwą metody i nawiasem otwierającym w deklaracji metody |

Przykłady kodu:

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_between_method_call_parameter_list_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Umieść znak spacji po nawiasie otwierającym i przed nawiasem zamykającym wywołania metody<br /><br />`false` -Usuń znaki spacji po nawiasie otwierającym i przed nawiasem zamykającym wywołania metody |

Przykłady kodu:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true` -Wstaw odstęp wewnątrz nawiasów listy pustych argumentów<br /><br />`false` -Usuń spację w nawiasach listy pustych argumentów |

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

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true` -Wstaw spację między nazwą wywołania metody i nawiasem otwierającym<br /><br />`false` -Usuń spację między nazwą wywołania metody i nawiasem otwierającym |

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

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_after_comma |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` -Wstaw odstęp po przecinku<br /><br />`false` -Usuń spację po przecinku |

Przykłady kodu:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a>csharp_space_before_comma

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_before_comma |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` -Wstaw odstęp przed przecinkiem<br /><br />`false` -Usuń odstęp przed przecinkiem |

Przykłady kodu:

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a>csharp_space_after_dot

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_after_dot |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` -Wstaw odstęp po kropce<br /><br />`false` -Usuń odstęp po kropce |

Przykłady kodu:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a>csharp_space_before_dot

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_before_dot |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` -Wstaw odstęp przed kropką <br /><br />`false` -Usuń odstęp przed kropką |

Przykłady kodu:

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a>csharp_space_after_semicolon_in_for_statement

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_after_semicolon_in_for_statement |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` -Wstaw odstęp po każdym średniku w `for` instrukcji<br /><br />`false` -Usuń odstęp po każdym średniku w `for` instrukcji |

Przykłady kodu:

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a>csharp_space_before_semicolon_in_for_statement

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_before_semicolon_in_for_statement |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` -Wstawiaj spację przed każdym średnikiem w `for` instrukcji <br /><br />`false` -Usuń odstęp przed każdym średnikiem w `for` instrukcji |

Przykłady kodu:

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a>csharp_space_around_declaration_statements

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_around_declaration_statements |
| **Odpowiednie języki** | C# |
| **Wartości** | `ignore` — Nie usuwaj dodatkowych znaków spacji w instrukcjach deklaracji<br /><br />`false` -Usuń dodatkowe znaki spacji w instrukcjach deklaracji |

Przykłady kodu:

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a>csharp_space_before_open_square_brackets

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_before_open_square_brackets |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` -Wstaw spację przed otwierającymi nawiasami kwadratowymi `[` <br /><br />`false` -Usuń spację przed otwierającymi nawiasami kwadratowymi `[` |

Przykłady kodu:

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a>csharp_space_between_empty_square_brackets

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_between_empty_square_brackets |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` -Wstaw odstęp między pustymi nawiasami kwadratowymi `[ ]` <br /><br />`false` -Usuń odstęp między pustymi nawiasami kwadratowymi `[]` |

Przykłady kodu:

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a>csharp_space_between_square_brackets

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_space_between_square_brackets |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` -Wstaw znaki spacji w niepustych nawiasach kwadratowych `[ 0 ]` <br /><br />`false` -Usuń spacje w nawiasach kwadratowych, które nie są puste `[0]` |

Przykłady kodu:

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a>Opcje zawijania

Te reguły formatowania dotyczą korzystania z pojedynczych wierszy w oddzielnym wierszu dla instrukcji i bloków kodu.

Przykładowy plik *. editorconfig* :

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a>csharp_preserve_single_line_statements

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_preserve_single_line_statements |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` -Pozostaw instrukcje i deklaracje składowych w tym samym wierszu<br /><br />`false` — Pozostaw instrukcje i deklaracje składowych w różnych wierszach |

Przykłady kodu:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a>csharp_preserve_single_line_blocks

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_preserve_single_line_blocks |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017, wersja 15.3 |
| **Wartości** | `true` — Pozostaw blok kodu w pojedynczym wierszu<br /><br />`false` — Pozostaw blok kodu w osobnych wierszach |

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

Ta reguła formatowania ma wpływ na użycie dyrektyw using umieszczonych wewnątrz i poza obszarem nazw.

Przykładowy plik *. editorconfig* :

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a>csharp_using_directive_placement

|Właściwość|Wartość|
|-|-|
| **Nazwa reguły** | csharp_using_directive_placement |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2019 w wersji 16.1 |
| **Wartości** | `outside_namespace` -Pozostaw dyrektywy using poza obszarem nazw<br /><br />`inside_namespace` -Pozostaw dyrektywy using w przestrzeni nazw |

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
