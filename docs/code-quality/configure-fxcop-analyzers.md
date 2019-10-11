---
title: Konfigurowanie analizatorów FxCop za pomocą editorconfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 62dd64dfe4e801f91731b1ed569e3a809156d0d1
ms.sourcegitcommit: b23d73c86ec7720c4cd9a58050860bc559623a3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72172788"
---
# <a name="configure-fxcop-analyzers"></a>Konfigurowanie analizatorów FxCop

[Pakiet analizatorów FxCop](install-fxcop-analyzers.md) składa się z najważniejszych reguł "FxCop" ze starszej analizy przekonwertowanej na .NET compiler platform analizatory kodu. W przypadku niektórych reguł FxCop można uściślić, które części bazy kodu powinny być stosowane za poorednictwem [konfigurowalnych opcji](fxcop-analyzer-options.md). Każda opcja jest określona przez dodanie pary klucz-wartość do pliku [EditorConfig](https://editorconfig.org) . Plik konfiguracji może być [specyficzny dla projektu](#per-project-configuration) lub może być [współużytkowany](#shared-configuration) przez dwa lub więcej projektów.

> [!TIP]
> Dodaj plik. editorconfig do projektu, klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierając pozycję **dodaj** **nowy element** > . W oknie **Dodaj nowy element** wprowadź **editorconfig** w polu wyszukiwania. Wybierz szablon **plik editorconfig (domyślnie)** , a następnie wybierz pozycję **Dodaj**.
>
> ![Dodawanie pliku editorconfig do projektu w programie Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Aby uzyskać informacje o konfigurowaniu ważności reguły (na przykład, czy jest to błąd czy ostrzeżenie), zobacz [Ustawianie ważności reguły w pliku EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Można też wybrać jeden z wbudowanych [plików EditorConfig lub zestawów reguł](analyzer-rule-sets.md) , aby szybko włączyć lub wyłączyć kategorię reguł.

::: moniker-end

Pozostała część tego artykułu zawiera opis ogólnej składni [opcji, które ograniczają,](fxcop-analyzer-options.md) gdzie są stosowane reguły FxCop.

> [!NOTE]
> Nie można skonfigurować starszych reguł FxCop przy użyciu pliku EditorConfig. Aby uzyskać informacje o różnicach między starszymi analizami i analizatorami FxCop, zobacz sekcję [analizatory FxCop — często zadawane pytania](fxcop-analyzers-faq.md).

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

## <a name="per-project-configuration"></a>Konfiguracja na projekt

Aby włączyć konfigurację analizatora opartego na EditorConfig dla określonego projektu, Dodaj plik *. EditorConfig* do katalogu głównego projektu.

Obecnie nie ma żadnych hierarchicznej obsługi dla "łączenia" plików editorconfig, które istnieją na różnych poziomach katalogu, na przykład na poziomie rozwiązania i projektu.

## <a name="shared-configuration"></a>Konfiguracja udostępniona

Można udostępnić plik. editorconfig do konfiguracji analizatora FxCop między co najmniej dwa projekty, ale wymaga to kilku dodatkowych kroków.

1. Zapisz plik *. editorconfig* w wspólnej lokalizacji.

2. Utwórz plik *. props* o następującej zawartości:

   ```xml
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <SkipDefaultEditorConfigAsAdditionalFile>true</SkipDefaultEditorConfigAsAdditionalFile>
     </PropertyGroup>
     <ItemGroup Condition="Exists('<your path>\.editorconfig')" >
       <AdditionalFiles Include="<your path>\.editorconfig" />
     </ItemGroup>
   </Project>
   ```

3. Dodaj wiersz do pliku *. csproj* lub *. vbproj* , aby zaimportować plik *. props* , który został utworzony w poprzednim kroku. Ten wiersz musi być umieszczony przed wszystkimi wierszami, które zaimportują Analizator FxCop *. props* Files. Na przykład, jeśli plik. props ma nazwę *editorconfig. props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Załaduj ponownie projekt.

> [!NOTE]
> Dowolnie udostępniona lokalizacja pliku EditorConfig ma zastosowanie tylko do konfigurowania zakresu niektórych reguł analizatora FxCop. W przypadku innych ustawień, takich jak ważność reguły, ogólne ustawienia edytora i styl kodu, plik EditorConfig musi zawsze być umieszczony w folderze projektu lub folderze nadrzędnym.

## <a name="see-also"></a>Zobacz także

- [Opcje zakresu reguł dla analizatorów FxCop](fxcop-analyzer-options.md)
- [Konfiguracja analizatora](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analizatory FxCop](install-fxcop-analyzers.md)
- [Konwencje kodowania .NET dla EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
