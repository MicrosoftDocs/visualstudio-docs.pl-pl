---
title: Konfigurowanie analizatorów jakości kodu platformy .NET przy użyciu editorconfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a131b7d69eec61f9b9106f7a4274b3882c51f0ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800739"
---
# <a name="configure-net-code-quality-analyzers"></a>Konfigurowanie analizatorów jakości kodu platformy .NET

W przypadku niektórych analizatorów jakości kodu platformy .NET (dla których identyfikatory reguł zaczynają się od `CA` ) można uściślić, które części bazy kodu mają być stosowane, za pomocą [konfigurowalnych opcji](fxcop-analyzer-options.md). Każda opcja jest określona przez dodanie pary klucz-wartość do pliku [EditorConfig](https://editorconfig.org) . Plik konfiguracji może być specyficzny dla pliku, projektu, rozwiązania lub całego repozytorium.

> [!TIP]
> Dodaj plik. editorconfig do projektu, klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierając polecenie **Dodaj**  >  **nowy element**. W oknie **Dodaj nowy element** wprowadź **editorconfig** w polu wyszukiwania. Wybierz szablon **plik editorconfig (domyślnie)** , a następnie wybierz pozycję **Dodaj**.
>
> ![Dodawanie pliku editorconfig do projektu w programie Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Aby uzyskać informacje o konfigurowaniu ważności reguły (na przykład, czy jest to błąd czy ostrzeżenie), zobacz [Ustawianie ważności reguły w pliku EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Można też wybrać jeden z wbudowanych [plików EditorConfig lub zestawów reguł](analyzer-rule-sets.md) , aby szybko włączyć lub wyłączyć kategorię reguł.

::: moniker-end

W pozostałej części tego artykułu opisano ogólną składnię [opcji, które](fxcop-analyzer-options.md) są stosowane w przypadku zastosowania analizatorów jakości kodu platformy .NET.

## <a name="option-scopes"></a>Zakresy opcji

Każdą opcję rafinacji można skonfigurować dla wszystkich reguł, dla kategorii reguł (na przykład nazewnictwa lub projektowania) lub dla określonej reguły.

### <a name="all-rules"></a>Wszystkie reguły

Składnia służąca do konfigurowania opcji dla *wszystkich* reguł jest następująca:

|Składnia|Przykład|
|-|-|
| dotnet_code_quality. OptionName = optionvalue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Kategoria reguł

Składnia służąca do konfigurowania opcji dla *kategorii* reguł (na przykład nazewnictwa, projektowania lub wydajności) jest następująca:

|Składnia|Przykład|
|-|-|
| dotnet_code_quality. RuleCategory. optionName = optionvalue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Określona reguła

Składnia służąca do konfigurowania opcji dla *określonej* reguły jest następująca:

|Składnia|Przykład|
|-|-|
| dotnet_code_quality. RuleId. optionName = optionvalue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="enabling-editorconfig-based-configuration"></a>Włączanie konfiguracji opartej na Editorconfig

Konfigurację analizatora opartego na EditorConfig można włączyć dla następujących zakresów:

- Określone dokumenty
- Określone foldery
- Określone projekty
- Określone rozwiązania
- Całe repozytorium

Aby włączyć konfigurację, należy dodać plik *. editorconfig* z opcjami w odpowiednim katalogu. Ten plik może również zawierać wpisy konfiguracji dotyczące ważności diagnostyki opartej na EditorConfig. Więcej informacji można znaleźć [tutaj](use-roslyn-analyzers.md#rule-severity).

## <a name="see-also"></a>Zobacz też

- [Opcje zakresu reguł dla analizatorów jakości kodu platformy .NET](fxcop-analyzer-options.md)
- [Konfiguracja analizatora](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Konwencje kodowania .NET dla EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
