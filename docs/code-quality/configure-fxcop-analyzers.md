---
title: Konfigurowanie analizatorów FxCop za pomocą editorconfig
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0152ae9f76ea1318f717c41a70d3d46351c9021a
ms.sourcegitcommit: 2bbcba305fd0f8800fd3d9aa16f7647ee27f3a4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2019
ms.locfileid: "68300607"
---
# <a name="configure-fxcop-analyzers"></a>Konfigurowanie analizatorów FxCop

[Analizatory FxCop](install-fxcop-analyzers.md) składają się z najważniejszych reguł "FxCop" z analizy kodu statycznego, przekonwertowane na analizatory Roslyn. Analizatory kodu FxCop można skonfigurować na dwa sposoby:

- [Zestaw reguł](#fxcop-analyzer-rule-sets), który umożliwia włączenie lub wyłączenie reguły i ustawienie ważności dla poszczególnych naruszeń reguł.

- Począwszy od wersji 2.6.3 pakietu NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) , za pomocą [pliku. editorconfig](#editorconfig-file). [Konfigurowalne opcje](fxcop-analyzer-options.md) pozwalają dostroić, które części bazy kodu mają być analizowane.

> [!TIP]
> Aby uzyskać informacje o różnicach między statyczną analizą kodu FxCop i analizatorami FxCop, zobacz temat analizy [FxCop — często zadawane pytania](fxcop-analyzers-faq.md).

## <a name="fxcop-analyzer-rule-sets"></a>Zestawy reguł analizatora FxCop

Jednym ze sposobów konfigurowania analizatorów FxCop jest użycie *zestawu reguł*XML. Zestaw reguł jest grupą reguł analizy kodu, które identyfikują problemy skierowane i określone warunki. Zestawy reguł umożliwiają włączenie lub wyłączenie reguły oraz ustawienie ważności dla poszczególnych naruszeń reguł.

Pakiet NuGet analizatora FxCop zawiera wstępnie zdefiniowane zestawy reguł dla następujących kategorii reguł:

- projekt
- dokumentacja
- utrzymanie
- nazewnictwo
- wydajność
- niezawodność
- zabezpieczenia
- wykorzystanie

Aby uzyskać więcej informacji, zobacz [zestawy reguł dla analizatorów Roslyn](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>Plik EditorConfig

Reguły analizatora można skonfigurować przez dodanie par klucz-wartość do pliku [editorconfig](https://editorconfig.org) . Plik konfiguracji może być [specyficzny dla projektu](#per-project-configuration) lub może być [współużytkowany](#shared-configuration) przez dwa lub więcej projektów.

### <a name="per-project-configuration"></a>Konfiguracja na projekt

Aby włączyć editorconfig konfigurację analizatora dla określonego projektu, Dodaj plik *. editorconfig* do katalogu głównego projektu.

> [!TIP]
> Do projektu można dodać plik. editorconfig, klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierając polecenie **Dodaj** > **nowy element**. W oknie **Dodaj nowy element** wprowadź **editorconfig** w polu wyszukiwania. Wybierz szablon **plik editorconfig (domyślnie)** , a następnie wybierz pozycję **Dodaj**.
>
> ![Dodaj element editorconfig do projektu w programie Visual Studio](media/add-editorconfig-file.png)

Obecnie nie ma żadnych hierarchicznej obsługi dla "łączenia" plików editorconfig, które istnieją na różnych poziomach katalogu, na przykład na poziomie rozwiązania i projektu.

### <a name="shared-configuration"></a>Konfiguracja udostępniona

Można udostępnić plik. editorconfig dla konfiguracji analizatora między co najmniej dwa projekty, ale wymaga to kilku dodatkowych kroków.

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
> Nie można skonfigurować starszych reguł FxCop (statycznej analizy kodu FxCop) przy użyciu pliku. editorconfig.

## <a name="option-scopes"></a>Zakresy opcji

Każdą opcję można skonfigurować dla wszystkich reguł, dla kategorii reguł (na przykład nazewnictwa lub projektowania) lub dla określonej reguły.

### <a name="all-rules"></a>Wszystkie reguły

Składnia służąca do konfigurowania opcji dla wszystkich reguł jest następująca:

|Składnia|Przykład|
|-|-|
| dotnet_code_quality. OptionName = optionvalue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Kategoria reguł

Składnia służąca do konfigurowania opcji dla *kategorii* reguł (na przykład nazewnictwa, projektowania lub wydajności) jest następująca:

|Składnia|Przykład|
|-|-|
| dotnet_code_quality. RuleCategory. optionName = optionvalue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Określona reguła

Składnia służąca do konfigurowania opcji dla określonej reguły jest następująca:

|Składnia|Przykład|
|-|-|
| dotnet_code_quality. RuleId. optionName = optionvalue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>Zobacz także

- [Konfiguracja analizatora](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analizatory FxCop](install-fxcop-analyzers.md)
- [Konwencje kodowania .NET dla EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
