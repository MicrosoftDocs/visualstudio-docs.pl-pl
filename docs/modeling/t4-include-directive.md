---
title: Dyrektywa T4 Include
description: 'Dowiedz się, że w szablonie tekstowym w Visual Studio można dołączyć tekst z innego pliku przy użyciu <# @include #> dyrektywy .'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7361d92b05fd6838d20b32ea9f0b3b14530266fa
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386309"
---
# <a name="t4-include-directive"></a>Dyrektywa T4 Include

W szablonie tekstowym Visual Studio można dołączyć tekst z innego pliku przy użyciu `<#@include#>` dyrektywy . Dyrektywy można `include` umieszczać w dowolnym miejscu w szablonie tekstowym przed blokiem funkcji pierwszej klasy `<#+ ... #>` . Dołączone pliki mogą również zawierać `include` dyrektywy i inne dyrektywy. To pozwala na udostępnianie kodu szablonu i standardowych wzorców tekstu szablonu między szablonami.

## <a name="using-include-directives"></a>Używanie dyrektyw Include

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` może być bezwzględne lub względne względem bieżącego pliku szablonu.

   Ponadto określone rozszerzenia Visual Studio mogą określać własne katalogi do wyszukiwania plików dołączanych. Na przykład po zainstalowaniu zestawu SDK wizualizacji i modelowania (DSL Tools) do listy dołączanych zostanie dodany następujący folder: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates` .

   Te dodatkowe foldery dołączania mogą zależeć od rozszerzenia dołączanego pliku. Na przykład folder include narzędzi DSL tools jest dostępny tylko dla plików, które mają rozszerzenie pliku `.tt`

- `filePath` może zawierać zmienne środowiskowe rozdzielone znakiem "%". Na przykład:

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- Nazwa dołączonego pliku nie musi używać rozszerzenia `".tt"` .

   Możesz użyć innego rozszerzenia, na przykład dla `".t4"` dołączonych plików. Dzieje się tak, ponieważ po dodaniu pliku do projektu program Visual Studio automatycznie ustawia jego właściwość `.tt` **Narzędzia** niestandardowego na `TextTemplatingFileGenerator` wartość . Zwykle nie chcesz, żeby dołączone pliki były przekształcane indywidualnie.

   Z drugiej strony należy pamiętać, że w niektórych przypadkach rozszerzenie pliku wpływa na to, w których dodatkowych folderach będą wyszukiwane dołączane pliki. Może to być ważne, gdy masz dołączony plik, który zawiera inne pliki.

- Dołączona zawartość jest przetwarzana prawie tak, jakby była częścią dołączającego szablonu tekstu. Można jednak dołączyć plik zawierający blok funkcji klasy, nawet jeśli po dyrektywie następuje zwykły `<#+...#>` tekst i standardowe bloki `include` sterujące.

- Użyj , aby upewnić się, że szablon jest dołączany tylko raz, nawet jeśli jest wywoływany z więcej `once="true"` niż jednego innego pliku dołączania.

   Ta funkcja ułatwia tworzenie biblioteki fragmentów kodu T4 wielokrotnego użytku, które można dołączyć wielokrotnie, bez obaw, że jakiś inny fragment kodu już je zawiera.  Załóżmy na przykład, że masz bibliotekę bardzo precyzyjnego fragmentu kodu, która zajmuje się przetwarzaniem szablonów i generowaniem kodu C#.  Z kolei są one używane przez niektóre narzędzia bardziej specyficzne dla zadań, takie jak generowanie wyjątków, których można następnie użyć z dowolnego szablonu bardziej specyficznego dla aplikacji. Jeśli narysujesz wykres zależności, zobaczysz, że niektóre wstawki kodu programu byłyby dołączone kilka razy. Jednak parametr `once` zapobiega kolejnym dołączeniam.

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

## <a name="using-project-properties-in-msbuild-and-visual-studio"></a><a name="msbuild"></a> Używanie właściwości projektu w programie MSBuild i Visual Studio
 Mimo że można używać Visual Studio, takich jak $(SolutionDir) w dyrektywie include, nie działają one w programie MSBuild. Aby przekształcić szablony w komputerze kompilacji, musisz użyć właściwości projektu.

 Wyedytuj plik .csproj lub .vbproj, aby zdefiniować właściwość projektu. W tym przykładzie zdefiniowano właściwość o nazwie `myIncludeFolder` :

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
