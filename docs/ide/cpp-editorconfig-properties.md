---
title: Konwencje formatowania języka C++ w narzędziu EditorConfig
titleSuffix: ''
description: Dowiedz się, jak używać EditorConfig do formatowania kodu C++ w programie Visual Studio.
ms.date: 9/14/2020
author: jureid
ms.author: jureid
manager: jillfra
dev_langs:
- CPP
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- cplusplus
monikerRange: vs-2019
ms.openlocfilehash: f248ede6a4bb45a58d64a346489124462f304a86
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518547"
---
# <a name="c-editorconfig-formatting-conventions"></a>Konwencje formatowania języka C++ w narzędziu EditorConfig

Program Visual Studio C++ formatującego ma bogaty zestaw konfigurowalnych ustawień, które mogą być stosowane globalnie. Aby ustawić ustawienia formatowania języka C++ dla określonego obszaru roboczego, użyj [clangformat](https://clang.llvm.org/docs/ClangFormat.html) lub [EditorConfig](https://editorconfig.org/). Zarówno program Visual Studio, jak i Visual Studio Code ma wbudowaną obsługę EditorConfig dla każdego z globalnych ustawień formatowania programu Visual Studio C++ i ma pierwszeństwo ustawienia EditorConfig. Oznacza to, że można dodać pliki EditorConfig do obszaru roboczego, aby skonfigurować formatowanie języka C++ na bardziej szczegółowym poziomie i wymusić spójny styl kodu dla wszystkich uczestników projektu.

## <a name="c-formatting-conventions"></a>Konwencje formatowania języka C++

Ustawienia EditorConfig formatowania języka C++ są poprzedzone prefiksem `cpp_` . Oto przykład pliku EditorConfig, który może wyglądać następująco:

```ini
[*.{c++,cc,cpp,cxx,h,h++,hh,hpp,hxx,inl,ipp,tlh,tli}]

cpp_indent_case_contents_when_block = true
cpp_new_line_before_open_brace_namespace = same_line
```

Pozostała część tego dokumentu zawiera wszystkie ustawienia formatowania języka EditorConfig C++ obsługiwane przez program Visual Studio i VS Code.

### <a name="indentation-settings"></a>Ustawienia wcięć

**Wcięcie nawiasów klamrowych**

- Nazwa: `cpp_indent_braces`
- Wartości: `true` , `false`

**Wetnij każdy wiersz względnie**

- Nazwa: `cpp_indent_multi_line_relative_to`
- Wartości:
  - `outermost_parenthesis` — Po wpisaniu nowego wiersza zostanie on wcięty względem najbardziej zewnętrznego otwartego nawiasu.
  - `innermost_parenthesis` — Po wpisaniu nowego wiersza zostanie on wcięty względem najbardziej wewnętrznego otwartego nawiasu.
  - `statement_begin` — Po wpisaniu nowego wiersza zostanie on wcięty względem początku bieżącej instrukcji.

**Wyrównaj nowe wiersze w nawiasach, gdy je wpiszę**

- Nazwa: `cpp_indent_within_parentheses`
- Wartości:
  - `align_to_parenthesis` -Wyrównaj zawartość do nawiasu otwierającego.
  - `indent` -Wcięcie nowych wierszy.

**W istniejącym kodzie nie używaj ustawienia do wyrównania nowych wierszy w nawiasach**

- Nazwa: `cpp_indent_preserve_within_parentheses`
- Wartości: `true` , `false`

**Wcięcie zawartości przypadku**

- Nazwa: `cpp_indent_case_contents`
- Wartości: `true` , `false`

**Wcięcie etykiet wielkości liter**

- Nazwa: `cpp_indent_case_labels`
- Wartości: `true` , `false`

**Wcięcia nawiasów klamrowych po instrukcji case**

- Nazwa: `cpp_indent_case_contents_when_block`
- Wartości: `true` , `false`

**Zwiększ wcięcia nawiasów klamrowych wyrażeń lambda używanych jako parametry**

- Nazwa: `cpp_indent_lambda_braces_when_parameter`
- Wartości: `true` , `false`

**Pozycja etykiet przejdź do**

- Nazwa: `cpp_indent_goto_labels`
- Wartości:
  - `one_left` — Jedno wcięcie w lewo
  - `leftmost_column` — Przejdź do kolumny z lewej strony
  - `none` — Pozostaw wcięcie

**Pozycja dyrektyw preprocesora**

- Nazwa: `cpp_indent_preprocessor`
- Wartości:
  - `one_left` — Jedno wcięcie w lewo
  - `leftmost_column` — Przejdź do kolumny z lewej strony
  - `none` — Pozostaw wcięcie

**Wetnij specyfikatory dostępu**

- Nazwa: `cpp_indent_access_specifiers`
- Wartości: `true` , `false`

**Zwiększ wcięcie zawartości przestrzeni nazw**

- Nazwa: `cpp_indent_namespace_contents`
- Wartości: `true` , `false`

**Zachowaj wcięcia komentarzy**

- Nazwa: `cpp_indent_preserve_comments`
- Wartości: `true` , `false`

### <a name="newline-settings"></a>Ustawienia nowego wiersza

**Pozycja klamrowych nawiasów otwierających dla przestrzeni nazw**

- Nazwa: `cpp_new_line_before_open_brace_namespace`
- Wartości:
  - `new_line` — Przenieś do nowego wiersza
  - `same_line` -Kontynuuj w tym samym wierszu, ale Dodaj odstęp przed
  - `ignore` -Nie zmieniaj automatycznie położenia

**Pozycja klamrowych nawiasów otwierających dla typów**

- Nazwa: `cpp_new_line_before_open_brace_type`
- Wartości:
  - `new_line` — Przenieś do nowego wiersza
  - `same_line` -Kontynuuj w tym samym wierszu, ale Dodaj odstęp przed
  - `ignore` -Nie zmieniaj automatycznie położenia

**Pozycja klamrowych nawiasów otwierających dla funkcji**

- Nazwa: `cpp_new_line_before_open_brace_function`
- Wartości:
  - `new_line` — Przenieś do nowego wiersza
  - `same_line` -Kontynuuj w tym samym wierszu, ale Dodaj odstęp przed
  - `ignore` -Nie zmieniaj automatycznie położenia

**Pozycja klamrowych nawiasów otwierających dla bloków sterowania**

- Nazwa: `cpp_new_line_before_open_brace_block`
- Wartości:
  - `new_line` — Przenieś do nowego wiersza
  - `same_line` -Kontynuuj w tym samym wierszu, ale Dodaj odstęp przed
  - `ignore` -Nie zmieniaj automatycznie położenia

**Pozycja klamrowych nawiasów otwierających dla wyrażeń lambda**

- Nazwa: `cpp_new_line_before_open_brace_lambda`
- Wartości:
  - `new_line` — Przenieś do nowego wiersza
  - `same_line` -Kontynuuj w tym samym wierszu, ale Dodaj odstęp przed
  - `ignore` -Nie zmieniaj automatycznie położenia
 
**Umieść nawiasy klamrowe zakresu w osobnych wierszach**

- Nazwa: `cpp_new_line_scope_braces_on_separate_lines`
- Wartości: `true` , `false`

**W przypadku pustych typów Przenieś zamykające nawiasy do tego samego wiersza co otwierające nawiasy klamrowe**

- Nazwa: `cpp_new_line_close_brace_same_line_empty_type`
- Wartości: `true` , `false`

**W przypadku pustych treści funkcji Przenieś zamykające nawiasy do tego samego wiersza co otwierające nawiasy klamrowe**

- Nazwa: `cpp_new_line_close_brace_same_line_empty_function`
- Wartości: `true` , `false`

**Umieść "Catch" i podobne słowa kluczowe w nowym wierszu**

- Nazwa: `cpp_new_line_before_catch`
- Wartości: `true` , `false`

**Umieść element "else" w nowym wierszu**

- Nazwa: `cpp_new_line_before_else`
- Wartości: `true` , `false`

**Umieść element "while" w pętli do-while w nowym wierszu**

- Nazwa: `cpp_new_line_before_while_in_do_while`
- Wartości: `true` , `false`

### <a name="spacing-settings"></a>Ustawienia odstępów

**Odstępy między nazwami funkcji i otwierającymi nawiasami list argumentów**

- Nazwa: `cpp_space_before_function_open_parenthesis`
- Wartości:
  - `insert` — Wstaw spację
  - `remove` -Usuń spacje
  - `ignore` — Nie zmieniaj spacji

**Wstawiaj spację wewnątrz nawiasów listy argumentów**

- `cpp_space_within_parameter_list_parentheses`Wartości nazw: `true` ,`false`

**Wstaw spację między nawiasami, gdy lista argumentów jest pusta**

- Nazwa: `cpp_space_between_empty_parameter_list_parentheses`
- Wartości: `true` , `false`

**Wstaw spację między słowem kluczowym a nawiasem otwierającym w instrukcjach przepływu sterowania**

- Nazwa: `cpp_space_after_keywords_in_control_flow_statements`
- Wartości: `true` , `false`

**Wstawiaj spację wewnątrz nawiasów instrukcji sterującej**

- Nazwa: `cpp_space_within_control_flow_statement_parentheses`
- Wartości: `true` , `false`

**Wstaw spację przed otwierającym nawiasem list argumentów lambda**

- Nazwa: `cpp_space_before_lambda_open_parenthesis`
- Wartości: `true` , `false`

**Wstawiaj spację wewnątrz nawiasów rzutowania w stylu języka C**

- Nazwa: `cpp_space_within_cast_parentheses`
- Wartości: `true` , `false`

**Wstaw spację po nawiasie zamykającym rzutowania w stylu języka C**

- Nazwa: `cpp_space_after_cast_close_parenthesis`
- Wartości: `true` , `false`

**Wstawiaj spację wewnątrz nawiasów wyrażenia ujętego w nawiasy**

- Nazwa: `cpp_space_within_expression_parentheses`
- Wartości: `true` , `false`

**Wstaw spację przed otwierającym nawiasem klamrowym bloków**

- Nazwa: `cpp_space_before_block_open_brace`
- Wartości: `true` , `false`

**Wstaw spację między pustymi nawiasami klamrowymi**

- Nazwa: `cpp_space_between_empty_braces`
- Wartości: `true` , `false`

**Wstaw spację przed otwierającym nawiasem klamrowym na listach jednolite inicjalizacji i inicjatorów**

- Nazwa: `cpp_space_before_initializer_list_open_brace`
- Wartości: `true` , `false`

**Wstaw spację w nawiasach klamrowych jednolitej listy inicjalizacji i inicjatorów**

- Nazwa: `cpp_space_within_initializer_list_braces`
- Wartości: `true` , `false`

**Zachowaj spacje wewnątrz jednolitej inicjalizacji i list inicjatorów**

- Nazwa: `cpp_space_preserve_in_initializer_list`
- Wartości: `true` , `false`

**Wstaw spację przed otwierającymi nawiasami kwadratowymi**

- Nazwa: `cpp_space_before_open_square_bracket`
- Wartości: `true` , `false`

**Wstaw spację w nawiasie kwadratowym**

- Nazwa: `cpp_space_within_square_brackets`
- Wartości: `true` , `false`

**Wstaw odstęp przed pustymi nawiasami kwadratowymi**

- Nazwa: `cpp_space_before_empty_square_brackets`
- Wartości: `true` , `false`

**Wstaw spację między pustymi nawiasami kwadratowymi**

- Nazwa: `cpp_space_between_empty_square_brackets`
- Wartości: `true` , `false`

**Grupuj nawiasy kwadratowe grup wielowymiarowych dla wielowymiarowych tablic**

- Nazwa: `cpp_space_group_square_brackets`
- Wartości: `true` , `false`

**Wstaw spację w nawiasach kwadratowych dla wyrażeń lambda**

- Nazwa: `cpp_space_within_lambda_brackets`
- Wartości: `true` , `false`

**SpaceBetweenEmptyLambdaBrackets**

- Nazwa: `cpp_space_between_empty_lambda_brackets`
- Wartości: `true` , `false`

**Wstaw spację przed przecinkami**

- Nazwa: `cpp_space_before_comma`
- Wartości: `true` , `false`

**Wstaw spację po przecinkach**

- Nazwa: `cpp_space_after_comma`
- Wartości: `true` , `false`

**Usuń odstępy przed i po operatorach składowych**

- Nazwa: `cpp_space_remove_around_member_operators`
- Wartości: `true` , `false`

**Wstaw spację przed dwukropkiem dla instrukcji Base w deklaracjach typu**

- Nazwa: `cpp_space_before_inheritance_colon`
- Wartości: `true` , `false`

**Wstaw spację przed dwukropkiem dla konstruktorów**

- Nazwa: `cpp_space_before_constructor_colon`
- Wartości: `true` , `false`

**Usuń odstęp przed średnikami**

- Nazwa: `cpp_space_remove_before_semicolon`
- Wartości: `true` , `false`

**Wstaw spację po średnikach**

- Nazwa: `cpp_space_after_semicolon`
- Wartości: `true` , `false`

**Usuń odstępy między operatorami jednoargumentowymi i ich operandami**

- Nazwa: `cpp_space_remove_around_unary_operator`
- Wartości: `true` , `false`

**Odstępy dla operatorów binarnych**

- Nazwa: `cpp_space_around_binary_operator`
- Wartości:
  - `insert` — Wstaw spacje przed operatorami binarnymi i po nich.
  - `remove` -Usuń spacje dookoła operatorów binarnych.
  - `ignore` — Nie zmieniaj odstępów wokół operatorów binarnych.

**Odstępy dla operatorów przypisania**

- Nazwa: `cpp_space_around_assignment_operator`
- Wartości:
  - `insert` — Wstaw spacje dookoła operatorów przypisania.
  - `remove` -Usuń spacje dookoła operatorów przypisania.
  - `ignore` — Nie zmieniaj odstępów dookoła operatorów przypisania.

**Wyrównanie wskaźnika/odwołania**

- Nazwa: `cpp_space_pointer_reference_alignment`
- Wartości:
  - `left` -Wyrównaj do lewej.
  - `center` -Wyrównaj do środka.
  - `right` -Wyrównaj do prawej.
  - `ignore` — Pozostaw bez zmian.

**Odstępy dla operatorów warunkowych**

- Nazwa: `cpp_space_around_ternary_operator`
- Wartości:
  - `insert` -Wstawiaj odstępy dookoła operatorów warunkowych.
  - `remove` -Usuń spacje dookoła operatorów warunkowych.
  - `ignore` — Nie zmieniaj odstępów dookoła operatorów warunkowych.

### <a name="wrapping-options"></a>Opcje zawijania

**Opcje zawijania dla bloków**

- Nazwa: `cpp_wrap_preserve_blocks`
- Wartości:
  - `one_liners` — Nie Zawijaj jednowierszowych bloków kodu.
  - `all_one_line_scopes` — Nie Zawijaj bloków kodu, w których otwierające i zamykające nawiasy klamrowe znajdują się w następnym wierszu.
  - `never` -Zawsze stosuj ustawienia nowych linii dla bloków.

## <a name="see-also"></a>Zobacz także

- [EditorConfig.org](https://editorconfig.org/)
- [Obsługa EditorConfig dla usługi językowej](../extensibility/supporting-editorconfig.md)
- [Funkcje edytora kodu](writing-code-in-the-code-and-text-editor.md)
