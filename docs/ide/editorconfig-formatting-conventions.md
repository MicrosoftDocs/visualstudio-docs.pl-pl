---
title: Konwencje formatowania platformy .NET dla EditorConfig
ms.date: 07/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ccebfc38d5170920fe3f3c37ee77aabaf660a3b8
ms.sourcegitcommit: 8562a337cc9f674c756a4a0b2c7e288ebd61b51e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345668"
---
# <a name="formatting-conventions"></a>Konwencje formatowania

Konwencje formatowania dla EditorConfig dla programu Visual Studio należą do następujących kategorii:

- [Ustawienia formatowania platformy .NET](#net-formatting-settings)

- [C#ustawienia formatowania](#c-formatting-settings)

## <a name="rule-format"></a>Format reguły

Reguły dla Konwencji formatowania mają następujący format:

`rule_name = value`

W przypadku wielu reguł należy określić jeden `true` (Preferuj ten styl) lub `false` (nie Preferuj tego stylu) dla `value`. W przypadku innych reguł należy określić wartość taką jak `flush_left` lub `before_and_after` , aby opisać, kiedy i gdzie należy zastosować regułę. Nie określisz ważności.

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

#### <a name="dotnetsortsystemdirectivesfirst"></a>dotnet\_sort\_system\_directives_first

|||
|-|-|
| **Nazwa reguły** | dotnet_sort_system_directives_first |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true` - Sortowanie System.* `using` dyrektywy alfabetycznie i umieścić je przed innymi za pomocą dyrektywy.<br /><br />`false` - Należy umieszczać System.* `using` dyrektyw przed innymi `using` dyrektywy. |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="dotnetseparateimportdirectivegroups"></a>grupy\_dyrektywy\_\_dotyczącejimportowaniaoddzielnychdotnet\_

|||
|-|-|
| **Nazwa reguły** | dotnet_separate_import_directive_groups |
| **Odpowiednie języki** | C# i Visual Basic |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15.5 |
| **Wartości** | `true`— Należy umieścić pusty wiersz między `using` grupami dyrektyw.<br /><br />`false`— Nie umieszczaj pustego wiersza między `using` grupami dyrektyw. |
| **Domyślne dla programu Visual Studio** | `false` |

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

## <a name="c-formatting-settings"></a>C#ustawienia formatowania

Reguły formatowania w tej sekcji mają zastosowanie tylko do C# kodu.

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

#### <a name="csharpnewlinebeforeopenbrace"></a>CSharp\_nowy\_wierszprzed\_open_brace\_

Ta zasada `{` ma wpływ na to, czy otwierający nawias klamrowy powinien być umieszczony w tym samym wierszu co poprzedni kod, czy w nowym wierszu. Dla tej reguły należy określić **wszystkie**, **Brak**lub co najmniej jeden element kodu, taki jak **metody** lub **Właściwości**, aby określić, kiedy ta reguła ma być stosowana. Aby określić wiele elementów kodu, rozdziel je przecinkami (,).

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_open_brace |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `all`-Wymagaj nawiasów klamrowych w nowym wierszu dla wszystkich wyrażeń (styl "Allman").<br /><br />`none`-Wymagaj nawiasów klamrowych w tym samym wierszu dla wszystkich wyrażeń ("K & R").<br /><br />`accessors`, `anonymous_methods` `anonymous_types` ,`indexers`,,,, ,`object_collection_array_initializers`,,, ,`types`— Wymagaj nawiasów klamrowych, aby znajdować się w nowym wierszu dla `properties` `local_functions` `lambdas` `control_blocks` `events` `methods` określony element kodu (styl "Allman"). |
| **Domyślne dla programu Visual Studio** | `all` |

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

#### <a name="csharpnewlinebeforeelse"></a>CSharp\_nowy\_wierszbefore_else\_

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_else |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`-Umieść `else` instrukcje w nowym wierszu.<br /><br />`false`-Umieść `else` instrukcje w tym samym wierszu. |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="csharpnewlinebeforecatch"></a>CSharp\_nowy\_wierszbefore_catch\_

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_catch |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`-Umieść `catch` instrukcje w nowym wierszu.<br /><br />`false`-Umieść `catch` instrukcje w tym samym wierszu. |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="csharpnewlinebeforefinally"></a>CSharp\_nowy\_wierszbefore_finally\_

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_finally |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`-Wymagaj `finally` instrukcji w nowym wierszu po nawiasie zamykającym.<br /><br />`false`-Wymagaj `finally` instrukcji w tym samym wierszu co zamykający nawias klamrowy. |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="csharpnewlinebeforemembersinobjectinitializers"></a>CSharp\_nowy\_wierszprzedelementami\_członkowskimi\_wobject_initializers\_\_

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_members_in_object_initializers |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`-Wymagane składowe inicjatorów obiektów muszą znajdować się w osobnych wierszach<br /><br />`false`-Wymagane składowe inicjatorów obiektów powinny znajdować się w tym samym wierszu |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="csharpnewlinebeforemembersinanonymoustypes"></a>CSharp\_nowy\_wierszprzedelementami\_członkowskimi\_wanonymous_types\_\_

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_members_in_anonymous_types |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`-Wymagaj elementów członkowskich typu anonimowego w osobnych wierszach<br /><br />`false`-Wymagane składowe typów anonimowych mogą znajdować się w tym samym wierszu |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="csharpnewlinebetweenqueryexpressionclauses"></a>csharp_new_line_between_query_expression_clauses

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_between_query_expression_clauses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`-Wymagaj elementów klauzul wyrażeń zapytania w osobnych wierszach<br /><br />`false`-Wymagaj elementów klauzul wyrażeń zapytania, aby znajdować się w tym samym wierszu |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="csharpindentcasecontents"></a>CSharp\_wcięcie\_case_contents

|||
|-|-|
| **Nazwa reguły** | csharp_indent_case_contents |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`— Wcięcie `switch` zawartości przypadku<br /><br />`false`-Nie Wetnij `switch` zawartości wielkości liter |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="csharpindentswitchlabels"></a>CSharp\_wcięcie\_switch_labels

|||
|-|-|
| **Nazwa reguły** | csharp_indent_switch_labels |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`-Wcięcia `switch` etykiet<br /><br />`false`— Nie Wetnij `switch` etykiet |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="csharpindentlabels"></a>CSharp\_indent_labels

|||
|-|-|
| **Nazwa reguły** | csharp_indent_labels |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `flush_left`-Etykiety są umieszczane w kolumnie z lewej strony<br /><br />`one_less_than_current`-Etykiety są umieszczane w jednym z niższych wcięć w bieżącym kontekście<br /><br />`no_change`-Etykiety są umieszczane w tym samym powiększeniu co bieżący kontekst |
| **Domyślne dla programu Visual Studio** | `no_change` |

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

#### <a name="csharpindentblockcontents"></a>csharp_indent_block_contents

|||
|-|-|
| **Nazwa reguły** | csharp_indent_block_contents |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` - <br /><br />`false` -  |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="csharpindentbraces"></a>csharp_indent_braces

|||
|-|-|
| **Nazwa reguły** | csharp_indent_braces |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` - <br /><br />`false` -  |
| **Domyślne dla programu Visual Studio** | `false` |

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

#### <a name="csharpindentcasecontentswhenblock"></a>csharp_indent_case_contents_when_block

|||
|-|-|
| **Nazwa reguły** | csharp_indent_case_contents_when_block |
| **Odpowiednie języki** | C# |
| **Wartości** | `true` - <br /><br />`false` -  |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="csharpspaceaftercast"></a>CSharp\_miejsca\_after_cast

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_cast |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`-Umieść znak spacji między rzutem a wartością<br /><br />`false`-Usuń odstęp między rzutem a wartością |
| **Domyślne dla programu Visual Studio** | `false` |

Przykłady kodu:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharpspaceafterkeywordsincontrolflowstatements"></a>csharp_space_after_keywords_in_control_flow_statements

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_keywords_in_control_flow_statements |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`-Umieść znak spacji po słowie kluczowym w instrukcji przepływu sterowania, takiej jak `for` pętla<br /><br />`false`-Usuń spację po słowie kluczowym w instrukcji przepływu sterowania, `for` takiej jak pętla |
| **Domyślne dla programu Visual Studio** | `true` |

Przykłady kodu:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharpspacebetweenparentheses"></a>csharp_space_between_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `control_flow_statements`-Umieść miejsce między nawiasami instrukcji przepływu sterowania<br /><br />`expressions`-Miejsce między nawiasami wyrażenia<br /><br />`type_casts`-Umieść miejsce między nawiasami w rzutach typu |
| **Domyślne dla programu Visual Studio** | `false` |

Jeśli pominięto tę regułę lub użyjesz wartości innej niż `control_flow_statements`, `expressions`lub `type_casts`, to ustawienie nie jest stosowane.

Przykłady kodu:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharpspacebeforecolonininheritanceclause"></a>CSharp\_spację\_\_przed\_dwukropkiemw\_inheritance_clause

|||
|-|-|
| **Nazwa reguły** | csharp_space_before_colon_in_inheritance_clause |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,7 |
| **Wartości** | `true`-Umieść znak spacji przed dwukropkiem dla baz lub interfejsów w deklaracji typu<br /><br />`false`-Usuń spację przed dwukropkiem dla baz lub interfejsów w deklaracji typu |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="csharpspaceaftercolonininheritanceclause"></a>CSharp\_spację\_\_po\_dwukropkuw\_inheritance_clause

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_colon_in_inheritance_clause |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,7 |
| **Wartości** | `true`-Umieść znak spacji po dwukropku dla baz lub interfejsów w deklaracji typu<br /><br />`false`-Usuń spację po dwukropku dla podstaw lub interfejsów w deklaracji typu |
| **Domyślne dla programu Visual Studio** | `true` |

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

#### <a name="csharpspacearoundbinaryoperators"></a>CSharp\_miejsce\_wokółbinary_operators\_

|||
|-|-|
| **Nazwa reguły** | csharp_space_around_binary_operators |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,7 |
| **Wartości** | `before_and_after`-Wstaw spację przed i po operatorze Binary<br /><br />`none`-Usuń odstępy przed i po operatorze Binary<br /><br />`ignore`-Ignoruj odstępy dookoła operatorów binarnych |
| **Domyślne dla programu Visual Studio** | `before_and_after` |

Jeśli pominięto tę regułę lub używasz wartości innej niż `before_and_after`, `none`lub `ignore`, ustawienie nie jest stosowane.

Przykłady kodu:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharpspacebetweenmethoddeclarationparameterlistparentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`-Umieść znak spacji po nawiasie otwierającym i przed nawiasem zamykającym listy parametrów deklaracji metody<br /><br />`false`-Usuń znaki spacji po nawiasie otwierającym i przed nawiasem zamykającym listy parametrów deklaracji metody |
| **Domyślne dla programu Visual Studio** | `false` |

Przykłady kodu:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharpspacebetweenmethoddeclarationemptyparameterlistparentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,7 |
| **Wartości** | `true`-Wstaw odstęp wewnątrz nawiasów listy pustych parametrów dla deklaracji metody<br /><br />`false`-Usuń spację w nawiasach listy pustych parametrów dla deklaracji metody |
| **Domyślne dla programu Visual Studio** | `false` |

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

#### <a name="csharpspacebetweenmethoddeclarationnameandopenparenthesis"></a>csharp_space_between_method_declaration_name_and_open_parenthesis

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`-Umieść znak spacji między nazwą metody i nawiasem otwierającym w deklaracji metody<br /><br />`false`-Usuń znaki spacji między nazwą metody i nawiasem otwierającym w deklaracji metody |
| **Domyślne dla programu Visual Studio** | `false` |

Przykłady kodu:

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharpspacebetweenmethodcallparameterlistparentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_call_parameter_list_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`-Umieść znak spacji po nawiasie otwierającym i przed nawiasem zamykającym wywołania metody<br /><br />`false`-Usuń znaki spacji po nawiasie otwierającym i przed nawiasem zamykającym wywołania metody |
| **Domyślne dla programu Visual Studio** | `false` |

Przykłady kodu:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharpspacebetweenmethodcallemptyparameterlistparentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,7 |
| **Wartości** | `true`-Wstaw odstęp wewnątrz nawiasów listy pustych argumentów<br /><br />`false`-Usuń spację w nawiasach listy pustych argumentów |
| **Domyślne dla programu Visual Studio** | `false` |

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

#### <a name="csharpspacebetweenmethodcallnameandopeningparenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,7 |
| **Wartości** | `true`-Wstaw spację między nazwą wywołania metody i nawiasem otwierającym<br /><br />`false`-Usuń spację między nazwą wywołania metody i nawiasem otwierającym |
| **Domyślne dla programu Visual Studio** | `false` |

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

#### <a name="csharpspaceaftercomma"></a>csharp_space_after_comma

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_comma |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`-Wstaw odstęp po przecinku<br /><br />`false`-Usuń spację po przecinku |
| **Domyślne dla programu Visual Studio** | `true` |

Przykłady kodu:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharpspacebeforecomma"></a>csharp_space_before_comma

|||
|-|-|
| **Nazwa reguły** | csharp_space_before_comma |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`-Wstaw odstęp przed przecinkiem<br /><br />`false`-Usuń odstęp przed przecinkiem |
| **Domyślne dla programu Visual Studio** | `false` |

Przykłady kodu:

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharpspaceafterdot"></a>csharp_space_after_dot

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_dot |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`-Wstaw odstęp po kropce<br /><br />`false`-Usuń odstęp po kropce |
| **Domyślne dla programu Visual Studio** | `false` |

Przykłady kodu:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharpspacebeforedot"></a>csharp_space_before_dot

|||
|-|-|
| **Nazwa reguły** | csharp_space_before_dot |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`-Wstaw odstęp przed kropką <br /><br />`false`-Usuń odstęp przed kropką |
| **Domyślne dla programu Visual Studio** | `false` |

Przykłady kodu:

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharpspaceaftersemicoloninforstatement"></a>csharp_space_after_semicolon_in_for_statement

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_semicolon_in_for_statement |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`-Wstaw odstęp po każdym średniku w `for` instrukcji<br /><br />`false`-Usuń odstęp po każdym średniku w `for` instrukcji |
| **Domyślne dla programu Visual Studio** | `true` |

Przykłady kodu:

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharpspacebeforesemicoloninforstatement"></a>csharp_space_before_semicolon_in_for_statement

|||
|-|-|
| **Nazwa reguły** | csharp_space_before_semicolon_in_for_statement |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`-Wstawiaj spację przed każdym średnikiem w `for` instrukcji <br /><br />`false`-Usuń odstęp przed każdym średnikiem w `for` instrukcji |
| **Domyślne dla programu Visual Studio** | `false` |

Przykłady kodu:

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharpspacearounddeclarationstatements"></a>csharp_space_around_declaration_statements

|||
|-|-|
| **Nazwa reguły** | csharp_space_around_declaration_statements |
| **Odpowiednie języki** | C# |
| **Wartości** | `ignore`— Nie usuwaj dodatkowych znaków spacji w instrukcjach deklaracji<br /><br />`false`-Usuń dodatkowe znaki spacji w instrukcjach deklaracji |
| **Domyślne dla programu Visual Studio** | `false` |

Przykłady kodu:

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharpspacebeforeopensquarebrackets"></a>csharp_space_before_open_square_brackets

|||
|-|-|
| **Nazwa reguły** | csharp_space_before_open_square_brackets |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`-Wstaw spację przed otwierającymi nawiasami kwadratowymi`[` <br /><br />`false`-Usuń spację przed otwierającymi nawiasami kwadratowymi`[` |
| **Domyślne dla programu Visual Studio** | `false` |

Przykłady kodu:

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharpspacebetweenemptysquarebrackets"></a>csharp_space_between_empty_square_brackets

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_empty_square_brackets |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`-Wstaw odstęp między pustymi nawiasami kwadratowymi`[ ]` <br /><br />`false`-Usuń odstęp między pustymi nawiasami kwadratowymi`[]` |
| **Domyślne dla programu Visual Studio** | `false` |

Przykłady kodu:

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharpspacebetweensquarebrackets"></a>csharp_space_between_square_brackets

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_square_brackets |
| **Odpowiednie języki** | C# |
| **Wartości** | `true`-Wstaw znaki spacji w niepustych nawiasach kwadratowych`[ 0 ]` <br /><br />`false`-Usuń spacje w nawiasach kwadratowych, które nie są puste`[0]` |
| **Domyślne dla programu Visual Studio** | `false` |

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

#### <a name="csharppreservesinglelinestatements"></a>csharp_preserve_single_line_statements

|||
|-|-|
| **Nazwa reguły** | csharp_preserve_single_line_statements |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`-Pozostaw instrukcje i deklaracje składowych w tym samym wierszu<br /><br />`false`— Pozostaw instrukcje i deklaracje składowych w różnych wierszach |
| **Domyślne dla programu Visual Studio** | `true` |

Przykłady kodu:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharppreservesinglelineblocks"></a>csharp_preserve_single_line_blocks

|||
|-|-|
| **Nazwa reguły** | csharp_preserve_single_line_blocks |
| **Odpowiednie języki** | C# |
| **Wprowadzona wersja** | Visual Studio 2017 w wersji 15,3 |
| **Wartości** | `true`— Pozostaw blok kodu w pojedynczym wierszu<br /><br />`false`— Pozostaw blok kodu w osobnych wierszach |
| **Domyślne dla programu Visual Studio** | `true` |

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

## <a name="see-also"></a>Zobacz także

- [Konwencje językowe](editorconfig-language-conventions.md)
- [Konwencje nazewnictwa](editorconfig-naming-conventions.md)
- [.NET coding convention ustawienia dla wtyczki EditorConfig](editorconfig-code-style-settings-reference.md)
