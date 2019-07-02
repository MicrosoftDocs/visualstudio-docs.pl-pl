---
title: Konwencje formatowania .NET dla wtyczki EditorConfig
ms.date: 06/17/2019
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
ms.openlocfilehash: 340d8ca7f7b578ae952c0b5024cd6962f20a0dff
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2019
ms.locfileid: "67262830"
---
# <a name="formatting-conventions"></a>Konwencje formatowania

Konwencje formatowania dla wtyczki EditorConfig dla programu Visual Studio można podzielić na dwie kategorie:

- [Ustawienia formatowania platformy .NET](#net-formatting-settings)

- [Ustawienia formatowania C#](#c-formatting-settings)

## <a name="rule-format"></a>Format reguły

Zasady konwencje formatowania mają następujący format:

`rule_name = value`

Dla wielu reguł, należy określić albo `true` (Preferuj ten styl) lub `false` (nie Preferuj kwalifikatora ten styl) dla `value`. Dla innych reguł, należy określić wartość taką jak `flush_left` lub `before_and_after` do opisania, kiedy i gdzie stosować regułę. Nie określaj ważność.

## <a name="net-formatting-settings"></a>Ustawienia formatowania platformy .NET

Reguły formatowania w tej sekcji dotyczą C# i kodu języka Visual Basic.

- [Organizuj użycia](#organize-using-directives)
   - dotnet_sort_system_directives_first
   - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Organizowanie dyrektyw using

Te reguły formatowania dotyczą, sortowanie i wyświetlanie `using` dyrektyw i `Imports` instrukcji.

Przykład *.editorconfig* pliku:

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
| **Właściwe języki** | C# i Visual Basic |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` - Sortowanie System.* `using` dyrektywy alfabetycznie i umieścić je przed innymi za pomocą dyrektywy.<br /><br />`false` - Należy umieszczać System.* `using` dyrektyw przed innymi `using` dyrektywy. |
| **Visual Studio domyślną** | `true` |

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

#### <a name="dotnetseparateimportdirectivegroups"></a>polecenia DotNet\_oddzielnych\_zaimportować\_dyrektywy\_grup

|||
|-|-|
| **Nazwa reguły** | dotnet_separate_import_directive_groups |
| **Właściwe języki** | C# i Visual Basic |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.5 |
| **Wartości** | `true` — Umieść pusty wiersz między `using` grupy dyrektywy.<br /><br />`false` -Należy umieszczać pusty wiersz między `using` grupy dyrektywy. |
| **Visual Studio domyślną** | `false` |

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

## <a name="c-formatting-settings"></a>Ustawienia formatowania C#

Reguły formatowania w tej sekcji dotyczą tylko kodu C#.

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
- [Opcje odstępów](#spacing-options)
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
   - csharp_space_after_comma
   - csharp_space_after_dot
- [Opcje opakowywania](#wrap-options)
   - csharp_preserve_single_line_statements
   - csharp_preserve_single_line_blocks

### <a name="new-line-options"></a>Opcje nowego wiersza

Te reguły formatowania dotyczą stosowania nowych wierszy w celu formatowania kodu.

Przykład *.editorconfig* pliku:

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

#### <a name="csharpnewlinebeforeopenbrace"></a>CSharp\_nowe\_wiersza\_przed\_open_brace

Ta zasada dotyczy czy otwierający nawias klamrowy `{` należy umieścić w tym samym wierszu, jak kod powyżej, lub w nowym wierszu. Dla tej reguły, należy określić **wszystkich**, **Brak**, lub jeden lub więcej kodu, elementy takie jak **metody** lub **właściwości**, aby zdefiniować, kiedy ta reguła powinny być stosowane. Aby określić wiele elementów kodu, oddziel je przecinkami (,).

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_open_brace |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `all` — Wymagają nawiasy klamrowe w nowym wierszu dla wszystkich wyrażeń (styl "Allman").<br /><br />`none` — Wymagają klamrowe, aby być w tym samym wierszu, aby uzyskać wszystkie wyrażenia ("K & R").<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` -Wymagane nawiasy klamrowe w nowym wierszu dla element określony kod (styl "Allman"). |
| **Visual Studio domyślną** | `all` |

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

#### <a name="csharpnewlinebeforeelse"></a>CSharp\_nowe\_wiersza\_before_else

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_else |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` — Umieść `else` instrukcji w nowym wierszu.<br /><br />`false` — Umieść `else` instrukcji w tym samym wierszu. |
| **Visual Studio domyślną** | `true` |

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

#### <a name="csharpnewlinebeforecatch"></a>CSharp\_nowe\_wiersza\_before_catch

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_catch |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` — Umieść `catch` instrukcji w nowym wierszu.<br /><br />`false` — Umieść `catch` instrukcji w tym samym wierszu. |
| **Visual Studio domyślną** | `true` |

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

#### <a name="csharpnewlinebeforefinally"></a>CSharp\_nowe\_wiersza\_before_finally

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_finally |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` — Wymagają `finally` instrukcji jako po zamykający nawias klamrowy w nowym wierszu.<br /><br />`false` — Wymagają `finally` instrukcji w tym samym wierszu co zamykającego nawiasu klamrowego. |
| **Visual Studio domyślną** | `true` |

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

#### <a name="csharpnewlinebeforemembersinobjectinitializers"></a>CSharp\_nowe\_wiersza\_przed\_członków\_w\_object_initializers

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_members_in_object_initializers |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` — Wymagają członkowie inicjatorów obiektów w osobnych wierszach<br /><br />`false` — Wymagają członkowie inicjatorów obiektów na tym samym wierszu |
| **Visual Studio domyślną** | `true` |

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

#### <a name="csharpnewlinebeforemembersinanonymoustypes"></a>CSharp\_nowe\_wiersza\_przed\_członków\_w\_anonymous_types

|||
|-|-|
| **Nazwa reguły** | csharp_new_line_before_members_in_anonymous_types |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` — Wymagają składowe typów anonimowych w osobnych wierszach<br /><br />`false` — Wymagają składowe typów anonimowych, w tym samym wierszu |
| **Visual Studio domyślną** | `true` |

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
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` — Wymagają elementy klauzule wyrażenia zapytania, aby wprowadzić w oddzielnych wierszach<br /><br />`false` — Wymagają elementy klauzule wyrażenia zapytania w tym samym wierszu |
| **Visual Studio domyślną** | `true` |

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

Te reguły formatowania dotyczą użytkowania wcięcia w celu formatowania kodu.

Przykład *.editorconfig* pliku:

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="csharpindentcasecontents"></a>csharp\_indent\_case_contents

|||
|-|-|
| **Nazwa reguły** | csharp_indent_case_contents |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` -Wcięcie `switch` zamierzone, Zapisz zawartość<br /><br />`false` -Nie wcięcie `switch` zamierzone, Zapisz zawartość |
| **Visual Studio domyślną** | `true` |

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

#### <a name="csharpindentswitchlabels"></a>csharp\_indent\_switch_labels

|||
|-|-|
| **Nazwa reguły** | csharp_indent_switch_labels |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` -Wcięcie `switch` etykiety<br /><br />`false` -Nie wcięcie `switch` etykiety |
| **Visual Studio domyślną** | `true` |

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

#### <a name="csharpindentlabels"></a>csharp\_indent_labels

|||
|-|-|
| **Nazwa reguły** | csharp_indent_labels |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `flush_left` -Etykiety są umieszczane w skrajnej lewej kolumnie<br /><br />`one_less_than_current` -Etykiety są umieszczane w jednej mniej wcięcie bieżącego kontekstu<br /><br />`no_change` -Etykiety są umieszczane w tej samej wcięcie jako bieżący kontekst |
| **Visual Studio domyślną** | `no_change` |

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

### <a name="spacing-options"></a>Opcje odstępów

Te reguły formatowania dotyczy użycia znaków spacji do formatowania kodu.

Przykład *.editorconfig* pliku:

```ini
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
csharp_space_after_comma = true
csharp_space_after_dot = false
```

#### <a name="csharpspaceaftercast"></a>CSharp\_miejsca\_after_cast

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_cast |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` — Wymagają odstęp między rzutowanie, jak i wartość<br /><br />`false` — Wymagają _nie_ odstęp między rzutowanie, jak i wartość |
| **Visual Studio domyślną** | `false` |

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
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` — Wymagają spację po słowem kluczowym w instrukcji przepływu sterowania takich jak `for` pętli<br /><br />`false` — Wymagają _nie_ spację po słowem kluczowym w instrukcji przepływu sterowania, takich jak `for` pętli |
| **Visual Studio domyślną** | `true` |

Przykłady kodu:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharpspacebetweenmethoddeclarationparameterlistparentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` -Umieścić znak spacji po nawiasie otwierającym, a także przed zamykającym w liście parametrów deklaracji metody<br /><br />`false` -Nie zostanie znaków spacji po nawiasie otwierającym, a także przed zamykającym w liście parametrów deklaracji metody |
| **Visual Studio domyślną** | `false` |

Przykłady kodu:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharpspacebetweenmethodcallparameterlistparentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_call_parameter_list_parentheses |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` -Umieścić znak spacji po nawiasie otwierającym, a także przed nawiasem zamykającym wywołania metody<br /><br />`false` -Nie zostanie znaków spacji po nawiasie otwierającym, a także przed nawiasem zamykającym wywołania metody |
| **Visual Studio domyślną** | `false` |

Przykłady kodu:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharpspacebetweenparentheses"></a>csharp_space_between_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_parentheses |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `control_flow_statements` -Umieścić spację między nawiasów instrukcji przepływu sterowania<br /><br />`expressions` — Umieść odstęp między nawiasy, wyrażeń<br /><br />`type_casts` — Umieść odstęp między nawiasy w rzutowania typów |
| **Visual Studio domyślną** | `false` |

Możesz pominąć tę regułę lub użyć wartości innej niż `control_flow_statements`, `expressions`, lub `type_casts`, to ustawienie nie ma zastosowania.

Przykłady kodu:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharpspacebeforecolonininheritanceclause"></a>csharp\_space\_before\_colon\_in\_inheritance_clause

|||
|-|-|
| **Nazwa reguły** | csharp_space_before_colon_in_inheritance_clause |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true` — Wymagają spację przed dwukropkiem w przypadku baz lub interfejsy w deklaracji typu<br /><br />`false` — Wymagają _nie_ spację przed dwukropkiem w przypadku baz lub interfejsy w deklaracji typu |
| **Visual Studio domyślną** | `true` |

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

#### <a name="csharpspaceaftercolonininheritanceclause"></a>csharp\_space\_after\_colon\_in\_inheritance_clause

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_colon_in_inheritance_clause |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true` — Wymagają spację po dwukropku w przypadku baz lub interfejsów w deklaracji typu<br /><br />`false` — Wymagają _nie_ spację po dwukropku w przypadku baz lub interfejsy w deklaracji typu |
| **Visual Studio domyślną** | `true` |

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

#### <a name="csharpspacearoundbinaryoperators"></a>CSharp\_miejsca\_wokół\_binary_operators

|||
|-|-|
| **Nazwa reguły** | csharp_space_around_binary_operators |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `before_and_after` -Wstaw spację przed i po nim operatora binarnego<br /><br />`none` -Usuń odstępy przed i po operatora binarnego<br /><br />`ignore` -Ignoruj spacje dookoła operatorów dwuargumentowych |
| **Visual Studio domyślną** | `before_and_after` |

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

#### <a name="csharpspacebetweenmethoddeclarationemptyparameterlistparentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true` -Wstaw spację wewnątrz nawiasów listy parametrów empty deklaracji — metoda<br /><br />`false` -Usuń odstęp wewnątrz nawiasów listy parametrów empty deklaracji — metoda |
| **Visual Studio domyślną** | `false` |

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

#### <a name="csharpspacebetweenmethodcallnameandopeningparenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true` -Wstaw spację między nazwę wywołanie metody i nawias otwierający<br /><br />`false` -Usuń spację między nazwę wywołanie metody i nawias otwierający |
| **Visual Studio domyślną** | `false` |

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

#### <a name="csharpspacebetweenmethodcallemptyparameterlistparentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **Nazwa reguły** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.7 |
| **Wartości** | `true` -Wstaw spację wewnątrz nawiasów listy pusty argument<br /><br />`false` -Usuń odstęp wewnątrz nawiasów listy pusty argument |
| **Visual Studio domyślną** | `false` |

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

#### <a name="csharpspaceaftercomma"></a>csharp_space_after_comma

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_comma |
| **Właściwe języki** | C# |
| **Wartości** | `true` -Wstaw spację po przecinku<br /><br />`false` -Usuń miejsca po przecinku |
| **Visual Studio domyślną** | `true` |

Przykłady kodu:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharpspaceafterdot"></a>csharp_space_after_dot

|||
|-|-|
| **Nazwa reguły** | csharp_space_after_dot |
| **Właściwe języki** | C# |
| **Wartości** | `true` -Wstaw odstęp po kropce<br /><br />`false` -Usuń miejsce po kropce |
| **Visual Studio domyślną** | `false` |

Przykłady kodu:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

### <a name="wrap-options"></a>Opcje opakowywania

Te reguły formatowania dotyczą użytkowania pojedynczych wierszy w porównaniu z osobnych wierszach instrukcji i bloków kodu.

Przykład *.editorconfig* pliku:

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
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` -Pozostaw instrukcje i deklaracje składowych w tym samym wierszu<br /><br />`false` -Pozostaw instrukcje i deklaracje składowych w różnych wierszach |
| **Visual Studio domyślną** | `true` |

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
| **Właściwe języki** | C# |
| **Wprowadzono wersji** | Visual Studio 2017 w wersji 15.3 |
| **Wartości** | `true` -Pozostaw blok kodu w pojedynczym wierszu<br /><br />`false` -Pozostaw blok kodu w osobnych wierszach |
| **Visual Studio domyślną** | `true` |

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

- [Konwencje języka](editorconfig-language-conventions.md)
- [Konwencje nazewnictwa](editorconfig-naming-conventions.md)
- [.NET coding convention ustawienia dla wtyczki EditorConfig](editorconfig-code-style-settings-reference.md)