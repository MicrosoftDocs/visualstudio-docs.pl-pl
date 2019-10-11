---
title: Opcje konfiguracji analizatora FxCop
ms.date: 09/23/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c6eb32357998f0867b00a5ef0e9119c3c357ed1b
ms.sourcegitcommit: b23d73c86ec7720c4cd9a58050860bc559623a3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72172744"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>Opcje zakresu reguł dla analizatorów FxCop

Niektóre reguły analizatora FxCop umożliwiają udoskonalanie części bazy kodu, do których powinny być stosowane. Ta strona zawiera listę dostępnych opcji konfiguracji zakresu, ich wartości dopuszczalne i reguły, do których mogą być stosowane. Aby użyć tych opcji, należy określić je w [pliku EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

Te opcje konfiguracji są dostępne od wersji 2.6.3 pakietu NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) .

> [!TIP]
> Aby zapoznać się z pełną listą opcji dostępnych dla danej wersji pakietu FxCopAnalyzers, zapoznaj się z plikiem *analizatora Configuration.MD* w folderze *Dokumentacja* pakietu. Plik znajduje się w lokalizacji *% USERPROFILE% \\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers @ no__t-2 @ no__t-3version @ no__t-4\documentation\Analyzer Configuration.MD*. Ten plik dokumentacji konfiguracji jest dołączony do każdej wersji pakietu, począwszy od wersji 2.6.5. Oto przykład sposobu udokumentowania opcji w pliku *Configuration.MD analizatora* :
>
> Nazwa opcji: `sufficient_IterationCount_for_weak_KDF_algorithm` @ no__t-1
> Wartości opcji: wartości całkowite \
> Wartość domyślna: Specyficzne dla każdej konfigurowalnej reguły ("100000" domyślnie dla większości reguł) \
> Przykład: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Która część powierzchni interfejsu API do przeanalizowania | `public`<br/>`internal` lub `friend`<br/>`private`<br/>`all`<br/><br/>Rozdziel wiele wartości przecinkami (,) | `public` | [CA1000](ca1000-do-not-declare-static-members-on-generic-types.md)<br/>[CA1003](ca1003-use-generic-event-handler-instances.md)<br/>[CA1008](ca1008-enums-should-have-zero-value.md)<br/>[CA1010](ca1010-collections-should-implement-generic-interface.md)<br/>[CA1012](ca1012-abstract-types-should-not-have-constructors.md)<br/>[CA1024](ca1024-use-properties-where-appropriate.md)<br/>[CA1027](ca1027-mark-enums-with-flagsattribute.md)<br/>[CA1028](ca1028-enum-storage-should-be-int32.md)<br/>[CA1030](ca1030-use-events-where-appropriate.md)<br/>[CA1036](ca1036-override-methods-on-comparable-types.md)<br/>[CA1040](ca1040-avoid-empty-interfaces.md)<br/>[CA1041](ca1041-provide-obsoleteattribute-message.md)<br/>[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md)<br/>[CA1044](ca1044-properties-should-not-be-write-only.md)<br/>[CA1051](ca1051-do-not-declare-visible-instance-fields.md)<br/>[CA1052](ca1052-static-holder-types-should-be-sealed.md)<br/>[CA1054](ca1054-uri-parameters-should-not-be-strings.md)<br/>[CA1055](ca1055-uri-return-values-should-not-be-strings.md)<br/>[CA1056](ca1056-uri-properties-should-not-be-strings.md)<br/>[CA1058](ca1058-types-should-not-extend-certain-base-types.md)<br/>[CA1063](ca1063-implement-idisposable-correctly.md)<br/>[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md)<br/>[CA1710](ca1710-identifiers-should-have-correct-suffix.md)<br/>[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md)<br/>[CA1714](ca1714-flags-enums-should-have-plural-names.md)<br/>[CA1715](ca1715-identifiers-should-have-correct-prefix.md)<br/>[CA1716](ca1716-identifiers-should-not-match-keywords.md)<br/>[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md)<br/>[CA1720](ca1720-identifiers-should-not-contain-type-names.md)<br/>[CA1721](ca1721-property-names-should-not-match-get-methods.md)<br/>[CA1725](ca1725-parameter-names-should-match-base-declaration.md)<br/>[CA1802](ca1802-use-literals-where-appropriate.md)<br/>[CA1815](ca1815-override-equals-and-operator-equals-on-value-types.md)<br/>[CA1819](ca1819-properties-should-not-return-arrays.md)<br/>[CA2217](ca2217-do-not-mark-enums-with-flagsattribute.md)<br/>[CA2225](ca2225-operator-overloads-have-named-alternates.md)<br/>[CA2226](ca2226-operators-should-have-symmetrical-overloads.md)<br/>[CA2231](ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)<br/>[CA2234](ca2234-pass-system-uri-objects-instead-of-strings.md) |

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Czy ignorować metody asynchroniczne, które nie zwracają wartości | `true`<br/>`false` | `false` | [CA2007](ca2007-do-not-directly-await-task.md) |

> [!NOTE]
> W wersji 2.6.3 i wcześniejszej części pakietu analizatora ta opcja miała nazwę `skip_async_void_methods`.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Określa, czy wykluczyć z reguły [parametry typu](/dotnet/csharp/programming-guide/generics/generic-type-parameters) z pojedynczym znakiem, na przykład `S` w `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715-identifiers-should-have-correct-prefix.md) |

> [!NOTE]
> W wersji 2.6.3 i wcześniejszej części pakietu analizatora ta opcja miała nazwę `allow_single_letter_type_parameters`.

## <a name="output_kind"></a>output_kind

| Opis | Dozwolone wartości | Wartość domyślna | Konfigurowalne reguły |
| - | - | - | - |
| Określa, że kod w projekcie, który generuje ten typ zestawu, powinien być analizowany | Co najmniej jedno pole wyliczenia <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Rozdziel wiele wartości przecinkami (,) | Wszystkie rodzaje danych wyjściowych | [CA2007](ca2007-do-not-directly-await-task.md) |