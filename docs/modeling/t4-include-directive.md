---
title: Dyrektywa T4 Include
description: 'Dowiedz się, że w szablonie tekstowym w programie Visual Studio możesz dołączyć tekst z innego pliku za pomocą @include dyrektywy > < # #.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 825beee156c3de0e29e561817663c0f7731840dc
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363656"
---
# <a name="t4-include-directive"></a>Dyrektywa T4 Include

W szablonie tekstowym w programie Visual Studio można dołączyć tekst z innego pliku za pomocą `<#@include#>` dyrektywy. Dyrektywy można umieścić `include` w dowolnym miejscu w szablonie tekstowym przed blokiem funkcji pierwszej klasy `<#+ ... #>` . Dołączone pliki mogą również zawierać `include` dyrektywy i inne dyrektywy. To pozwala na udostępnianie kodu szablonu i standardowych wzorców tekstu szablonu między szablonami.

## <a name="using-include-directives"></a>Używanie dyrektyw Include

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` może być bezwzględny lub względny w stosunku do bieżącego pliku szablonu.

   Ponadto określone rozszerzenia programu Visual Studio mogą określać własne katalogi do wyszukiwania plików dołączanych. Na przykład jeśli zainstalowano zestaw SDK wizualizacji i modelowania (narzędzia DSL), następujący folder zostanie dodany do listy dołączania: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates` .

   Te dodatkowe foldery dołączania mogą zależeć od rozszerzenia dołączanego pliku. Na przykład narzędzia DSL Tools folder są dostępne tylko dla dołączania plików, które mają rozszerzenie pliku `.tt`

- `filePath` może zawierać zmienne środowiskowe z ograniczeniami "%". Na przykład:

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- Nazwa dołączonego pliku nie musi używać rozszerzenia `".tt"` .

   Możesz chcieć użyć innego rozszerzenia, takiego jak `".t4"` dla dołączonych plików. Jest to spowodowane tym, że po dodaniu `.tt` pliku do projektu program Visual Studio automatycznie ustawia jego właściwość **niestandardowego narzędzia** na `TextTemplatingFileGenerator` . Zwykle nie chcesz, żeby dołączone pliki były przekształcane indywidualnie.

   Z drugiej strony należy pamiętać, że w niektórych przypadkach rozszerzenie pliku wpływa na to, w których dodatkowych folderach będą wyszukiwane dołączane pliki. Może to być ważne, gdy masz dołączony plik, który zawiera inne pliki.

- Dołączona zawartość jest przetwarzana prawie tak, jakby była częścią dołączającego szablonu tekstu. Można jednak dołączyć plik, który zawiera blok funkcji klasy, `<#+...#>` nawet jeśli `include` po dyrektywie następuje zwykły tekst i standardowe bloki sterujące.

- Użyj `once="true"` , aby upewnić się, że szablon jest uwzględniany tylko raz, nawet jeśli jest wywoływany z więcej niż jednego pliku dołączania.

   Ta funkcja ułatwia tworzenie biblioteki fragmentów kodu T4 wielokrotnego użytku, które można dołączyć do programu, bez obaw, że niektóre inne fragmenty kodu zostały już zawarte.  Załóżmy na przykład, że masz bibliotekę bardzo szczegółowych fragmentów, które zajmują się przetwarzaniem szablonów i generowaniem kodu w języku C#.  Z kolei są one używane przez inne narzędzia specyficzne dla zadań, takie jak generowanie wyjątków, których można następnie użyć z dowolnego szablonu specyficznego dla aplikacji. Jeśli narysujesz wykres zależności, zobaczysz, że niektóre wstawki kodu programu byłyby dołączone kilka razy. Ale `once` parametr uniemożliwia późniejsze dołączenia.

  **MyTextTemplate.tt:**

```
<#@ output extension=".txt" #>
Output message 1 (from top template).
<#@ include file="TextFile1.t4"#>
Output message 5 (from top template).
<#
   GenerateMessage(6); // defined in TextFile1.t4
   AnotherGenerateMessage(7); // defined in TextFile2.t4
#>
```

 **Textplik1. T4:**

```
   Output Message 2 (from included file).
<#@ include file="TextFile2.t4" #>
   Output Message 4 (from included file).
<#+ // Start of class feature control block.
void GenerateMessage(int n)
{
#>
   Output Message <#= n #> (from GenerateMessage method).
<#+
}
#>
```

 **TextFile2. T4:**

```
        Output Message 3 (from included file 2).
<#+ // Start of class feature control block.
void AnotherGenerateMessage(int n)
{
#>
       Output Message <#= n #> (from AnotherGenerateMessage method).
<#+
}
#>
```

 **Powstały wygenerowany plik MyTextTemplate.txt:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).
```

## <a name="using-project-properties-in-msbuild-and-visual-studio"></a><a name="msbuild"></a> Korzystanie z właściwości projektu w MSBuild i Visual Studio
 Mimo że można użyć makr programu Visual Studio, takich jak $ (SolutionDir), w dyrektywie include nie działają one w programie MSBuild. Aby przekształcić szablony w komputerze kompilacji, musisz użyć właściwości projektu.

 Wyedytuj plik .csproj lub .vbproj, aby zdefiniować właściwość projektu. Ten przykład definiuje właściwość o nazwie `myIncludeFolder` :

```xml
<!-- Define a project property, myIncludeFolder: -->
<PropertyGroup>
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myIncludeFolder">
      <Value>$(myIncludeFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 Teraz można używać właściwości projektu w szablonach tekstowych, które są prawidłowo przekształcane w Visual Studio i MSBuild:

```
<#@ include file="$(myIncludeFolder)\defs.tt" #>
```
