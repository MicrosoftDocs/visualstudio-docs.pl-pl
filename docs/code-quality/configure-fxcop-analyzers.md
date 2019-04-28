---
title: Konfigurowanie analizatory FxCop analizujące kod przy użyciu pliku editorconfig
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ac751b7ec130b6bfbb18752c02b491b6c342f172
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816934"
---
# <a name="configure-fxcop-analyzers"></a>Konfigurowanie analizatory FxCop analizujące kod

[Analizatory FxCop analizujące kod](install-fxcop-analyzers.md) składają się z najważniejszych reguły "FxCop" ze statycznej analizy kodu, przekonwertować analizatorów Roslyn. Analizatory kodu FxCop analizujące kod można skonfigurować na dwa sposoby:

- Za pomocą [zestaw reguł](#fxcop-analyzer-rule-sets), które pozwala włączyć lub wyłączyć regułę i ustaw ważności dla poszczególnych reguł naruszenia.

- Począwszy od wersji 2.6.3 [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) za pośrednictwem pakietu NuGet [pliku .editorconfig](#editorconfig-file). [Konfigurowalne opcje](fxcop-analyzer-options.md) uściślić części, które umożliwiają Twojej bazy kodu do analizy.

> [!TIP]
> Aby uzyskać informacje o różnicach między FxCop statycznej analizy kodu i analizatory FxCop analizujące kod, zobacz [analizatory FxCop analizujące kod często zadawane pytania dotyczące](fxcop-analyzers-faq.md).

## <a name="fxcop-analyzer-rule-sets"></a>Zestawy reguł analizatora programu FxCop

Jednym ze sposobów konfigurowania analizatory FxCop analizujące kod jest za pomocą XML *zestaw reguł*. Zestaw reguł jest grupowania reguł analizy kodu, które identyfikują docelowe problemy i określone warunki. Zestawy reguł pozwalają włączyć lub wyłączyć regułę i ustaw ważności dla poszczególnych reguł naruszenia.

Pakiet NuGet analizatora FxCop zawiera zestawy wstępnie zdefiniowanych reguł dla następujących kategorii:

- projekt
- dokumentacja
- utrzymanie
- nazewnictwo
- wydajność
- niezawodność
- zabezpieczenia
- wykorzystanie

Aby uzyskać więcej informacji, zobacz [zestawów reguł na potrzeby analizatorów Roslyn](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>Plik wtyczki EditorConfig

Można skonfigurować zasady działania analizatora, dodając pary klucz wartość do [.editorconfig](https://editorconfig.org) pliku. Plik konfiguracji może być [specyficzne dla projektu](#per-project-configuration) lub może być [udostępnionego](#shared-configuration) między dwóch lub więcej projektów.

### <a name="per-project-configuration"></a>Konfiguracja dla projektu

Aby włączyć configuration analyzer na podstawie pliku .editorconfig dla określonego projektu, Dodaj *.editorconfig* plik do katalogu głównego projektu.

> [!TIP]
> Pliku .editorconfig można dodać do projektu, klikając prawym przyciskiem myszy nad projektem w **Eksploratora rozwiązań** i wybierając polecenie **Dodaj** > **nowy element**. W **Dodaj nowy element** oknie wprowadź **editorconfig** w polu wyszukiwania. Wybierz **editorconfig pliku (ustawienie domyślne)** szablonu i wybierz polecenie **Dodaj**.
>
> ![Dodaj element editorconfig do projektu programu Visual Studio](media/add-editorconfig-file.png)

Obecnie nie jest hierarchiczna obsługiwane dla plików .editorconfig "łączenie", który istnieje na poziomach innego katalogu, na przykład poziom rozwiązania i projektu.

### <a name="shared-configuration"></a>Konfiguracja udostępniona

Możesz udostępnić pliku .editorconfig dla analizatora konfiguracji między dwóch lub więcej projektów, ale wymaga pewnych dodatkowych kroków.

1. Zapisz *.editorconfig* do wspólnej lokalizacji.

2. Tworzenie *.props* pliku o następującej zawartości:

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

3. Dodaj wiersz, aby Twoje *.csproj* lub *.vbproj* plik do zaimportowania *.props* pliku utworzonego w poprzednim kroku. Ten wiersz musi być umieszczony przed wszystkie wiersze, które importują analizatora FxCop *.props* plików. Na przykład, jeśli plik .props nosi nazwę *editorconfig.props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Ponownie Załaduj projekt.

> [!NOTE]
> Starszych reguł programu FxCop (statycznej analizy kodu programu FxCop) nie można skonfigurować przy użyciu pliku editorconfig.

## <a name="option-scopes"></a>Opcja zakresów

Każdą opcję można skonfigurować dla wszystkich reguł, kategoria reguł (na przykład nazewnictwa lub projektu) lub określonej reguły.

### <a name="all-rules"></a>Wszystkie reguły

Składnia służąca do konfigurowania opcji dla wszystkich reguł jest następująca:

|Składnia|Przykład|
|-|-|
| dotnet_code_quality. OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Kategoria reguły

Składnia służąca do konfigurowania opcji *kategorii* reguł (na przykład nazewnictwa, projektu lub wydajność) jest w następujący sposób:

|Składnia|Przykład|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Określonej reguły

Składnia służąca do konfigurowania opcji określonej reguły jest następująca:

|Składnia|Przykład|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>Zobacz także

- [Analyzer configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analizatory FxCop analizujące kod](install-fxcop-analyzers.md)
