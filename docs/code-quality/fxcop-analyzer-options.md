---
title: Opcje konfiguracji analizatora jakości kodu platformy .NET
ms.date: 09/23/2019
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0370688b53e87cf6ea1f5079d2e5c706777dd0c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88706571"
---
# <a name="rule-scope-options-for-net-code-quality-analyzers"></a>Opcje zakresu reguł dla analizatorów jakości kodu platformy .NET

Niektóre reguły analizatora jakości kodu platformy .NET umożliwiają udoskonalenie części bazy kodu, do których mają być stosowane. Ta strona zawiera listę dostępnych opcji konfiguracji zakresu, ich wartości dopuszczalne i reguły, do których mogą być stosowane. Aby użyć tych opcji, należy określić je w [pliku EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

> [!TIP]
> Aby wyświetlić pełną listę dostępnych opcji, zobacz ten [plik analizatora Configuration.MD](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md). Oto przykład sposobu udokumentowania opcji w pliku *Configuration.MD analizatora* :
>
> Nazwa opcji: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Wartości opcji: wartości całkowite \
> Wartość domyślna: specyficzne dla każdej konfigurowalnej reguły ("100000" domyślnie dla większości reguł) \
> Przykład: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Która część powierzchni interfejsu API do przeanalizowania | `public`<br/>`internal` lub `friend`<br/>`private`<br/>`all`<br/><br/>Rozdziel wiele wartości przecinkami (,) | `public` | [CA1000](ca1000.md) [CA1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Czy ignorować metody asynchroniczne, które nie zwracają wartości | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> W wersji 2.6.3 i wcześniejszej części pakietu analizatora ta opcja została nazwana `skip_async_void_methods` .

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Określa, czy wykluczyć z reguły [parametry typu](/dotnet/csharp/programming-guide/generics/generic-type-parameters) o pojedynczym znaku, na przykład `S` w `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> W wersji 2.6.3 i wcześniejszej części pakietu analizatora ta opcja została nazwana `allow_single_letter_type_parameters` .

## <a name="output_kind"></a>output_kind

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Określa, że kod w projekcie, który generuje ten typ zestawu, powinien być analizowany | Co najmniej jedno pole <xref:Microsoft.CodeAnalysis.OutputKind> wyliczenia<br/><br/>Rozdziel wiele wartości przecinkami (,) | Wszystkie rodzaje danych wyjściowych | [CA2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Określa wymagane Modyfikatory dla interfejsów API, które powinny być analizowane | Jedna lub więcej wartości z poniższej dozwolonej tabeli modyfikatorów<br/><br/>Rozdziel wiele wartości przecinkami (,) | Zależy od każdej reguły | [CA1802](ca1802.md) |

| Dozwolony modyfikator | Podsumowanie |
| --- | --- |
| `none` | Brak wymagania modyfikatora |
| `static` lub `Shared` | Musi być zadeklarowana jako "static" ("Shared" w Visual Basic) |
| `const` | Musi być zadeklarowany jako "const" |
| `readonly` | Musi być zadeklarowany jako "ReadOnly" |
| `abstract` | Musi być zadeklarowany jako "abstract" |
| `virtual` | Musi być zadeklarowana jako "Virtual" |
| `override` | Musi być zadeklarowany jako "override" |
| `sealed` | Musi być zadeklarowany jako "Sealed" |
| `extern` | Musi być zadeklarowany jako "extern" |
| `async` | Musi być zadeklarowany jako "Async" |

## <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Czy pominąć analizę dla `this` parametru metod rozszerzenia | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Nazwy metod sprawdzania poprawności sprawdzenia wartości null, które weryfikują argumenty przekazane do metody, są inne niż null. | Dozwolone formaty nazw metod (oddzielone przecinkami `|` ):<br/> -Tylko nazwa metody (zawiera wszystkie metody o nazwie, niezależnie od typu zawierającego lub przestrzeni nazw)<br/> — W pełni kwalifikowane nazwy w [formacie identyfikatora dokumentacji](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu, z opcjonalnym `M:` prefiksem | Brak | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Nazwy dodatkowych metod formatowania ciągu | Dozwolone formaty nazw metod (oddzielone przecinkami `|` ):<br/> -Tylko nazwa metody (zawiera wszystkie metody o nazwie, niezależnie od typu zawierającego lub przestrzeni nazw)<br/> — W pełni kwalifikowane nazwy w [formacie identyfikatora dokumentacji](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu, z opcjonalnym `M:` prefiksem | Brak | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Nazwy typów, takie jak typ i wszystkie jego typy pochodne, są wykluczone na potrzeby analizy | Dozwolone formaty nazw symboli (oddzielone przecinkami `|` ):<br/> -Tylko nazwa typu (obejmuje wszystkie typy z nazwą, niezależnie od typu zawierającego lub przestrzeni nazw)<br/> — W pełni kwalifikowane nazwy w [formacie identyfikatora dokumentacji](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu, z opcjonalnym `T:` prefiksem | Brak | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Nazwy symboli, które są wykluczone na potrzeby analizy | Dozwolone formaty nazw symboli (oddzielone przecinkami `|` ):<br/> -Tylko nazwa symbolu (zawiera wszystkie symbole z nazwą, niezależnie od typu zawierającego lub przestrzeni nazw)<br/> — W pełni kwalifikowane nazwy w [formacie identyfikatora dokumentacji](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu. Każda nazwa symbolu wymaga prefiksu rodzaju symboli, takiego jak "M:" prefix dla metod, "T:" prefiksu dla typów, "N:" prefiksu dla przestrzeni nazw itd.<br/> - `.ctor` dla konstruktorów i `.cctor` dla konstruktorów statycznych | Brak | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Nazwy symboli, które są niedozwolone w kontekście analizy | Dozwolone formaty nazw symboli (oddzielone przecinkami `|` ):<br/> -Tylko nazwa symbolu (zawiera wszystkie symbole z nazwą, niezależnie od typu zawierającego lub przestrzeni nazw)<br/> — W pełni kwalifikowane nazwy w [formacie identyfikatora dokumentacji](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu. Każda nazwa symbolu wymaga prefiksu rodzaju symboli, takiego jak "M:" prefix dla metod, "T:" prefiksu dla typów, "N:" prefiksu dla przestrzeni nazw itd.<br/> - `.ctor` dla konstruktorów i `.cctor` dla konstruktorów statycznych | Brak | [CA1031](ca1031.md) |
