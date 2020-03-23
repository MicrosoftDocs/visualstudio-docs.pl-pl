---
title: .NET ustawienia konwencji kodowania Dla EditorConfig
ms.date: 03/17/2020
ms.topic: reference
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 41d183a757aefd198c282ec84cd6cbe0ef37c933
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508956"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Ustawienia konwencji kodowania .NET dla EditorConfig

Można zdefiniować i zachować spójny styl kodu w codebase przy użyciu [editorconfig](../ide/create-portable-custom-editor-options.md) pliku. EditorConfig zawiera kilka podstawowych właściwości `indent_style` formatowania, takich jak i `indent_size`. W programie Visual Studio ustawienia konwencji kodowania .NET można również skonfigurować przy użyciu pliku EditorConfig. Można włączyć lub wyłączyć poszczególne konwencje kodowania .NET i skonfigurować stopień, w jakim każda reguła ma być wymuszana, za pomocą poziomu ważności.

> [!TIP]
> - Podczas definiowania konwencji kodowania w editorconfig pliku, konfigurujesz, jak chcesz [analizatory stylu kodu,](../code-quality/roslyn-analyzers-overview.md) które są wbudowane w programie Visual Studio do analizy kodu. EditorConfig plik jest plik konfiguracyjny dla tych analizatorów.
> - Preferencje stylu kodu dla programu Visual Studio można również ustawić w oknie dialogowym [opcje edytora tekstu.](code-styles-and-code-cleanup.md) Jednak Ustawienia EditorConfig mają pierwszeństwo i preferencje ustawione w **Opcje** nie są skojarzone z określonego projektu.

## <a name="convention-categories"></a>Kategorie konwencji

Istnieją trzy obsługiwane kategorie konwencji kodowania .NET:

- [Konwencje języka](../ide/editorconfig-language-conventions.md)

   Reguły odnoszące się do języka C# lub Visual Basic. Na przykład można określić `var` reguły wokół przy użyciu lub jawne typy podczas definiowania zmiennych lub preferowania elementów członkowskich zabudowanych wyrażenia.

- [Konwencje formatowania](../ide/editorconfig-formatting-conventions.md)

   Zasady dotyczące układu i struktury kodu w celu ułatwienia odczytu. Na przykład można określić reguły wokół nawiasów klamrowych Allman lub preferując spacje w blokach kontrolnych.

- [Konwencje nazewnictwa](../ide/editorconfig-naming-conventions.md)

   Reguły dotyczące nazewnictwa elementów kodu. Na przykład można określić, że `async` metody muszą kończyć się na "Async".

## <a name="example-editorconfig-file"></a>Przykładowy plik EditorConfig

Aby ułatwić rozpoczęcie pracy, oto przykładowy plik *.editorconfig* z opcjami domyślnymi. W programie Visual Studio można wygenerować ten plik i zapisać go w projekcie w **programie Tools** > **Options** > **Text Editor** > [**C#** lub **Basic**] > **Code Style** > **General**. Następnie kliknij przycisk **Generuj plik .editorconfig z ustawień.** Aby uzyskać więcej informacji, zobacz [Preferencje stylu kodu](code-styles-and-code-cleanup.md).

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

# New line preferences
end_of_line = crlf
insert_final_newline = false

#### .NET Coding Conventions ####

# Organize usings
dotnet_separate_import_directive_groups = false
dotnet_sort_system_directives_first = false

# this. and Me. preferences
dotnet_style_qualification_for_event = false:silent
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_property = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent

# Expression-level preferences
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_object_initializer = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_compound_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:suggestion
dotnet_style_prefer_simplified_interpolation = true:suggestion

# Field preferences
dotnet_style_readonly_field = true:suggestion

# Parameter preferences
dotnet_code_quality_unused_parameters = all:suggestion

#### C# Coding Conventions ####

# var preferences
csharp_style_var_elsewhere = false:silent
csharp_style_var_for_built_in_types = false:silent
csharp_style_var_when_type_is_apparent = false:silent

# Expression-bodied members
csharp_style_expression_bodied_accessors = true:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent

# Pattern matching preferences
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_prefer_switch_expression = true:suggestion

# Null-checking preferences
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_prefer_static_local_function = true:suggestion
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:silent

# Code-block preferences
csharp_prefer_braces = true:silent
csharp_prefer_simple_using_statement = true:suggestion

# Expression-level preferences
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
csharp_style_throw_expression = true:suggestion
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
csharp_style_unused_value_expression_statement_preference = discard_variable:silent

# 'using' directive preferences
csharp_using_directive_placement = outside_namespace:silent

#### C# Formatting Rules ####

# New line preferences
csharp_new_line_before_catch = true
csharp_new_line_before_else = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_open_brace = all
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents = true
csharp_indent_case_contents_when_block = true
csharp_indent_labels = one_less_than_current
csharp_indent_switch_labels = true

# Space preferences
csharp_space_after_cast = false
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_after_comma = true
csharp_space_after_dot = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_after_semicolon_in_for_statement = true
csharp_space_around_binary_operators = before_and_after
csharp_space_around_declaration_statements = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_before_comma = false
csharp_space_before_dot = false
csharp_space_before_open_square_brackets = false
csharp_space_before_semicolon_in_for_statement = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_between_square_brackets = false

# Wrapping preferences
csharp_preserve_single_line_blocks = true
csharp_preserve_single_line_statements = true

#### Naming styles ####

# Naming rules

dotnet_naming_rule.interface_should_be_begins_with_i.severity = suggestion
dotnet_naming_rule.interface_should_be_begins_with_i.symbols = interface
dotnet_naming_rule.interface_should_be_begins_with_i.style = begins_with_i

dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.types_should_be_pascal_case.symbols = types
dotnet_naming_rule.types_should_be_pascal_case.style = pascal_case

dotnet_naming_rule.non_field_members_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.non_field_members_should_be_pascal_case.symbols = non_field_members
dotnet_naming_rule.non_field_members_should_be_pascal_case.style = pascal_case

# Symbol specifications

dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.interface.required_modifiers =

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.types.required_modifiers =

dotnet_naming_symbols.non_field_members.applicable_kinds = property, event, method
dotnet_naming_symbols.non_field_members.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.non_field_members.required_modifiers =

# Naming styles

dotnet_naming_style.pascal_case.required_prefix =
dotnet_naming_style.pascal_case.required_suffix =
dotnet_naming_style.pascal_case.word_separator =
dotnet_naming_style.pascal_case.capitalization = pascal_case

dotnet_naming_style.begins_with_i.required_prefix = I
dotnet_naming_style.begins_with_i.required_suffix =
dotnet_naming_style.begins_with_i.word_separator =
dotnet_naming_style.begins_with_i.capitalization = pascal_case
```

> [!NOTE]
> Aby uzyskać więcej informacji na temat obsługiwanych kategorii konwencji kodowania .NET, zobacz [konwencje języka, konwencje](../ide/editorconfig-language-conventions.md) [formatowania](../ide/editorconfig-formatting-conventions.md)i [konwencje nazewnictwa.](../ide/editorconfig-naming-conventions.md)

## <a name="see-also"></a>Zobacz też

- [Szybkie akcje](../ide/quick-actions.md)
- [Tworzenie przenośnych opcji edytora niestandardowego](../ide/create-portable-custom-editor-options.md)
- [Platforma kompilatora .NET "Roslyn" .editorconfig plik](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
- [Plik .NET Compiler Platform Runtime .editorconfig](https://github.com/dotnet/runtime/blob/master/.editorconfig)
