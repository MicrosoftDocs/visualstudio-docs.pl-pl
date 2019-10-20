---
title: T4 include — dyrektywa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 8c3de9f3-755a-47c5-a30a-65717dcaaac2
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 669be50e11d3bf17d617c361b63f807149dbc823
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658582"
---
# <a name="t4-include-directive"></a>Dyrektywa T4 Include
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W szablonie tekstowym w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] można dołączyć tekst z innego pliku za pomocą dyrektywy `<#@include#>`. Dyrektywy `include` można umieścić w dowolnym miejscu w szablonie tekstu przed blokiem funkcji pierwszej klasy `<#+ ... #>`. Dołączone pliki mogą również zawierać dyrektywy `include` i inne dyrektywy. To pozwala na udostępnianie kodu szablonu i standardowych wzorców tekstu szablonu między szablonami.

## <a name="using-include-directives"></a>Używanie dyrektyw Include

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` może być bezwzględny lub względny w stosunku do bieżącego pliku szablonu.

   Ponadto konkretne rozszerzenia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mogą określać własne katalogi do wyszukiwania plików dołączanych. Na przykład jeśli zainstalowano zestaw SDK wizualizacji i modelowania (narzędzia DSL), następujący folder zostanie dodany do listy dołączania: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.

   Te dodatkowe foldery dołączania mogą zależeć od rozszerzenia dołączanego pliku. Na przykład narzędzia DSL Tools folder są dostępne tylko w przypadku plików, które mają rozszerzenie pliku `.tt`

- `filePath` może zawierać zmienne środowiskowe ograniczone przez "%". Na przykład:

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- Nazwa dołączonego pliku nie musi używać rozszerzenia `".tt"`.

   Możesz chcieć użyć innego rozszerzenia, takiego jak `".t4"` dla dołączonych plików. Jest to spowodowane tym, że podczas dodawania pliku `.tt` do projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie ustawia jego właściwość **niestandardowego narzędzia** na `TextTemplatingFileGenerator`. Zwykle nie chcesz, żeby dołączone pliki były przekształcane indywidualnie.

   Z drugiej strony należy pamiętać, że w niektórych przypadkach rozszerzenie pliku wpływa na to, w których dodatkowych folderach będą wyszukiwane dołączane pliki. Może to być ważne, gdy masz dołączony plik, który zawiera inne pliki.

- Dołączona zawartość jest przetwarzana prawie tak, jakby była częścią dołączającego szablonu tekstu. Można jednak dołączyć plik, który zawiera blok funkcji klasy `<#+...#>` nawet wtedy, gdy po dyrektywie `include` następuje zwykły tekst i standardowe bloki sterujące.

- Użyj `once="true"`, aby upewnić się, że szablon jest uwzględniany tylko raz, nawet jeśli jest wywoływany z więcej niż jednego pliku dołączania.

   Ta funkcja ułatwia tworzenie biblioteki fragmentów kodu T4 wielokrotnego użytku, które można dołączyć do programu, bez obaw, że niektóre inne fragmenty kodu zostały już zawarte.  Załóżmy na przykład, że masz bibliotekę bardzo szczegółowych fragmentów, które zajmują się przetwarzaniem i C# generowaniem szablonu.  Z kolei są one używane przez inne narzędzia specyficzne dla zadań, takie jak generowanie wyjątków, których można następnie użyć z dowolnego szablonu specyficznego dla aplikacji. Jeśli narysujesz wykres zależności, zobaczysz, że niektóre wstawki kodu programu byłyby dołączone kilka razy. Ale `once` parametr uniemożliwia późniejsze dołączenia.

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
<#@include file="TextFile2.t4" #>
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

 **Powstały wygenerowany plik, MyTextTemplate. txt:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).

```

## <a name="msbuild"></a>Korzystanie z właściwości projektu w MSBuild i Visual Studio
 Chociaż można używać makr Visual Studio, takich jak $(SolutionDir), w dyrektywie include, nie działają one w MSBuild. Aby przekształcić szablony w komputerze kompilacji, musisz użyć właściwości projektu.

 Wyedytuj plik .csproj lub .vbproj, aby zdefiniować właściwość projektu. Ten przykład definiuje właściwość o nazwie `myIncludeFolder`:

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
