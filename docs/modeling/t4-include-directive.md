---
title: Dyrektywa T4 Include
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 4a4b4f111776dc083e4c29ae7944b1f61762fe07
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963754"
---
# <a name="t4-include-directive"></a>Dyrektywa T4 Include

W szablonie tekstowym w programie Visual Studio, można dołączyć tekst z innego pliku za pomocą `<#@include#>` dyrektywy. Możesz umieścić `include` dyrektywy w dowolnym miejscu w szablonie tekstu przed blokiem funkcji pierwszej klasy `<#+ ... #>`. Dołączone pliki mogą również zawierać `include` dyrektywy oraz inne dyrektywy. To pozwala na udostępnianie kodu szablonu i standardowych wzorców tekstu szablonu między szablonami.

## <a name="using-include-directives"></a>Używanie dyrektyw Include

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` może być ścieżką bezwzględną, lub względną do bieżącego pliku szablonu.

   Dodatkowo określone rozszerzenia programu Visual Studio można określić własne katalogi do wyszukiwania plików dołączanych. Na przykład jeśli zainstalowano wizualizacji i modelowania SDK (narzędzia DSL), następujący folder zostanie dodany do listy dołączania: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.

   Te dodatkowe foldery dołączania mogą zależeć od rozszerzenia dołączanego pliku. Na przykład narzędzia DSL zawierają folder jest dostępna wyłącznie dla plików, które mają rozszerzenie pliku `.tt`

- `filePath` może zawierać zmienne środowiskowe oddzielane znaku z "%". Na przykład:

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- Nazwa dołączanego pliku nie ma używać rozszerzenia `".tt"`.

   Warto użyć innego rozszerzenia, takie jak `".t4"` dla dołączonych plików. Jest to spowodowane dodając `.tt` plik do projektu programu Visual Studio automatycznie ustawia jego **narzędzie niestandardowe** właściwość `TextTemplatingFileGenerator`. Zwykle nie chcesz, żeby dołączone pliki były przekształcane indywidualnie.

   Z drugiej strony należy pamiętać, że w niektórych przypadkach rozszerzenie pliku wpływa na to, w których dodatkowych folderach będą wyszukiwane dołączane pliki. Może to być ważne, gdy masz dołączony plik, który zawiera inne pliki.

- Dołączona zawartość jest przetwarzana prawie tak, jakby była częścią dołączającego szablonu tekstu. Jednakże można dołączyć plik, który zawiera blok funkcji klasy `<#+...#>` nawet wtedy, gdy `include` dyrektywy następuje zwykły tekst i standardowe bloki sterujące.

- Użyj `once="true"` zapewnienie, że szablon jest uwzględniany tylko raz, nawet wtedy, gdy jest wywoływany z więcej niż jednego pliku dołączonego.

   Ułatwia to funkcja łatwy do utworzenia biblioteki wielokrotnego użytku wstawek T4, zawierających w będą bez konieczności martwienia się, że niektóre fragment kodu ma już one dołączone.  Na przykład załóżmy, że istnieje biblioteka bardzo szczegółowych fragmentów, które zajmują się języka C# generowania i przetwarzania szablonu.  Z kolei są one używane przez niektóre narzędzia bardziej specyficzne dla zadania, takie jak generowanie wyjątków, które następnie można użyć z dowolnego szablonu bardziej specyficzne dla aplikacji. Jeśli narysujesz wykres zależności, zobaczysz, że niektóre wstawki kodu programu byłyby dołączone kilka razy. Ale `once` parametru uniemożliwia późniejsze.

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

 **TextFile1.t4:**

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

 **TextFile2.t4:**

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

 **Wynikowy wygenerowany plik MyTextTemplate.txt:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).
```

## <a name="msbuild"></a> Korzystanie z właściwości projektu w MSBuild i Visual Studio
 Chociaż można używać makr Visual Studio, takich jak $ (solutiondir), w dyrektywie include, nie działają one w MSBuild. Aby przekształcić szablony w komputerze kompilacji, musisz użyć właściwości projektu.

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