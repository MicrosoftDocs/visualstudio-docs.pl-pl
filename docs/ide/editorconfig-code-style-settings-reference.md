---
title: Ustawienia konwencji kodowania .NET dla EditorConfig
ms.date: 06/14/2018
ms.topic: reference
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 99d83157e2b6d108eb87a701aa8bc05ca2c7b1e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653717"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Ustawienia konwencji kodowania .NET dla EditorConfig

Można zdefiniować i zachować spójny styl kodu w bazie kodu przy użyciu pliku [EditorConfig](../ide/create-portable-custom-editor-options.md) . EditorConfig zawiera kilka podstawowych właściwości formatowania, takich jak `indent_style` i `indent_size`. W programie Visual Studio ustawienia konwencji kodowania .NET można także skonfigurować przy użyciu pliku EditorConfig. Możesz włączyć lub wyłączyć poszczególne konwencje kodowania .NET i skonfigurować stopień, w jakim dana reguła ma być wymuszana, za pośrednictwem poziomu ważności.

> [!TIP]
> - Podczas definiowania konwencji kodowania w pliku EditorConfig, konfigurujesz, w jaki sposób [analizatory stylów kodu](../code-quality/roslyn-analyzers-overview.md) wbudowane w program Visual Studio mają analizować swój kod. Plik EditorConfig jest plikiem konfiguracji dla tych analizatorów.
> - Preferencje stylu kodu dla programu Visual Studio można także ustawić w oknie dialogowym [Opcje edytora tekstu](code-styles-and-code-cleanup.md) . Jednak ustawienia EditorConfig mają pierwszeństwo i preferencji ustawionych w **opcjach** nie są skojarzone z określonym projektem.

## <a name="convention-categories"></a>Kategorie Konwencji

Istnieją trzy obsługiwane kategorie konwencji kodowania .NET:

- [Konwencje językowe](../ide/editorconfig-language-conventions.md)

   Reguły dotyczące języka C# lub Visual Basic. Na przykład można określić reguły dotyczące używania `var` lub typów jawnych podczas definiowania zmiennych lub wstępnego wnioskowania członków w postaci wyrażeń.

- [Konwencje formatowania](../ide/editorconfig-formatting-conventions.md)

   Reguły dotyczące układu i struktury kodu, aby ułatwić ich odczytywanie. Na przykład można określić reguły wokół nawiasów klamrowych Allman lub miejsca, w których są nałożone spacje w blokach sterowania.

- [Konwencje nazewnictwa](../ide/editorconfig-naming-conventions.md)

   Reguły dotyczące nazewnictwa elementów kodu. Na przykład można określić, że metody `async` muszą kończyć się "Async".

## <a name="example-editorconfig-file"></a>Przykładowy plik EditorConfig

Aby ułatwić rozpoczęcie pracy, Oto przykładowy plik *editorconfig* z opcjami domyślnymi:

```ini
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
csharp_space_after_comma = true
csharp_space_after_dot = false

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
- [Tworzenie przenośnych opcji edytora niestandardowego](../ide/create-portable-custom-editor-options.md)
- [.NET Compiler Platform plik editorconfig](https://github.com/dotnet/roslyn/blob/master/.editorconfig)