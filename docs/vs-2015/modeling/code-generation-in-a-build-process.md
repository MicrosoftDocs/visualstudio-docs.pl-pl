---
title: Generowanie kodu w procesie kompilacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
ms.assetid: 4da43429-2a11-4d7e-b2e0-9e4af7033b5a
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bffaf0bcff0c0fc93201badeb01b95928edc2979
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850712"
---
# <a name="code-generation-in-a-build-process"></a>Generowanie kodu w procesie kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Transformację tekstu można wywołać w ramach procesu kompilacji rozwiązania programu Visual Studio. Istnieją zadania kompilacji, które są przeznaczone do przekształcania tekstu. Zadania kompilacji T4 uruchamiają szablon tekstowy czasu projektowania, a także kompilują szablony tekstowe czasu wykonywania (wstępnie przetworzone).

Istnieją pewne różnice w czynnościach, które mogą wykonać zadania kompilacji, wszystko zależy od użytego aparatu kompilacji. Podczas kompilowania rozwiązania w programie Visual Studio szablon tekstowy może uzyskać dostęp do interfejsu API programu Visual Studio (EnvDTE), jeśli ustawiono atrybut [hostspecific = "true"](../modeling/t4-template-directive.md) . Nie jest to prawdą podczas kompilowania rozwiązania z wiersza poleceń lub po zainicjowaniu kompilacji serwerowej za pomocą Visual Studio. W tych przypadkach kompilację wykonuje MSBuild i użyty zostaje inny host T4.

Oznacza to, że nie można uzyskać dostępu do takich elementów, jak nazwy plików projektu, w taki sam sposób podczas kompilacji szablonu tekstu w MSBuild. Można jednak [przekazać informacje o środowisku do szablonów tekstowych i procesorów dyrektywy przy użyciu parametrów kompilacji](#parameters).

## <a name="configure-your-machines"></a><a name="buildserver"></a> Konfigurowanie maszyn

Aby włączyć zadania kompilacji na komputerze deweloperskim, zainstaluj [zestaw SDK modelowania dla programu Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148).

Jeśli [serwer kompilacji](https://msdn.microsoft.com/library/788443c3-0547-452e-959c-4805573813a9) działa na komputerze, na którym nie zainstalowano programu Visual Studio, Skopiuj następujące pliki do komputera kompilacji z komputera deweloperskiego. Zastąp najnowsze numery wersji dla "*".

- $ (ProgramFiles) \MSBuild\Microsoft\VisualStudio\v *. 0 \ TextTemplating

  - Microsoft. VisualStudio. TextTemplating. Sdk. host. * .0.dll

  - Microsoft.TextTemplating.Build.Tasks.dll

  - Microsoft.TextTemplating.targets

- $ (ProgramFiles) \Microsoft Visual Studio *. 0 \ VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft. VisualStudio. TextTemplating. * .0.dll

  - Microsoft. VisualStudio. TextTemplating. Interfaces. * .0.dll (kilka plików)

  - Microsoft. VisualStudio. TextTemplating. VSHost. * .0.dll

- $ (ProgramFiles) \Microsoft Visual Studio *. 0 \ Common7\IDE\PublicAssemblies\

  - Microsoft. VisualStudio. TextTemplating. Modeling. * .0.dll

## <a name="to-edit-the-project-file"></a>Aby edytować plik projektu

Konieczna jest edycja pliku projektu, aby skonfigurować niektóre funkcje programu MSBuild.

W Eksploratorze rozwiązań wybierz pozycję **Zwolnij** z menu kontekstowego projektu. Pozwala to na edycję pliku .csproj lub .vbproj w edytorze XML.

Po zakończeniu edycji wybierz pozycję **Załaduj ponownie**.

## <a name="import-the-text-transformation-targets"></a>Importowanie obiektów docelowych przekształcenia tekstu

W pliku .vbproj lub .csproj znajdź taki wiersz:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- oraz

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Po tym wierszu wstaw import szablonu tekstu:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version – defaults to 10: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transforming-templates-in-a-build"></a>Przekształcanie szablonów podczas kompilacji

Istnieje kilka właściwości, które można wstawić do pliku projektu, aby móc kontrolować zadanie przekształcenia:

- Należy uruchomić zadanie przekształceń na początku każdej kompilacji:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Zastąp pliki, które są tylko do odczytu, ponieważ np. nie zostały wyewidencjonowane:

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- Za każdym razem przekształcaj każdy szablon:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     Domyślnie, zadanie programu MSBuild T4 odtwarza plik wyjściowy, jeżeli jest starszy niż jego plik szablonu, a także wszystkie pliki, które są dołączone, lub wszystkie pliki, które zostały wcześniej odczytane przez szablon lub przez procesor dyrektywy, którego używa szablon. Zwróć uwagę, że jest to o wiele bardziej rozbudowany test zależności, niż test używany przez polecenie Transform All Templates w programie Visual Studio, który jedynie porównuje daty szablonu i pliku wyjściowego.

Aby wykonać tylko przekształcenia tekstu w projekcie, należy wywołać zadanie TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Aby przekształcić określony szablon tekstowy:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

Można używać symboli wieloznacznych w TransformFile:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Kontrola źródła

Nie ma żadnych szczególnych wbudowanych funkcji integracji z systemem kontroli źródła. Można jednak dodać własne rozszerzenia, na przykład aby wyewidencjonować i zaewidencjonować wygenerowany plik. Domyślnie zadanie przekształcenia tekstu pozwala uniknąć zastąpienia pliku, który jest oznaczony jako tylko do odczytu, i po napotkaniu takiego pliku zostanie zarejestrowany błąd na liście błędów Visual Studio, a zadanie się nie powiedzie.

Aby określić, że pliki tylko do odczytu powinny być zastąpione, wstaw tę właściwość:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

O ile nie dostosujesz kroku przetwarzania końcowego, zastąpienie pliku spowoduje, że na liście błędów zostanie zarejestrowane ostrzeżenie.

## <a name="customizing-the-build-process"></a>Dostosowywanie procesu kompilacji

Transformacja tekstu ma miejsce przed innymi zadaniami w procesie kompilacji. Można zdefiniować zadania, które są wywoływane przed przekształceniem i po nim, ustawiając właściwości `$(BeforeTransform)` i `$(AfterTransform)` :

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
  </PropertyGroup>
  <Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
  </Target>
  <Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
  </Target>
```

W programie `AfterTransform` można odwoływać się do list plików:

- GeneratedFiles — lista plików zapisanych przez proces. Dla tych plików, które zastąpią istniejące pliki tylko do odczytu, %(GeneratedFiles.ReadOnlyFileOverwritten) będzie prawdziwe. Pliki te można wyewidencjonować z kontroli źródła.

- NonGeneratedFiles — lista plików tylko do odczytu, które nie zostały nadpisane.

  Na przykład, można zdefiniować zadanie do wyewidencjonowania GeneratedFiles.

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath i OutputFileName

Właściwości te są stosowane tylko przez program MSBuild. Nie wpływają one na generowanie kodu w programie Visual Studio. Przekierowują one wygenerowany plik wyjściowy do innego folderu lub pliku. Folder docelowy musi już istnieć.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Przydatny folder do przekierowania to `$(IntermediateOutputPath).`

Jeśli zostanie określona nazwa pliku wyjściowego, będzie ona miała wyższy priorytet nad rozszerzeniem określonym w dyrektywie wyjścia w szablonach.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Określenie OutputFileName lub OutputFilePath nie jest zalecane, jeśli przekształcany jest również szablon wewnątrz VS przy użyciu Transform All, lub uruchamiany jest generator pojedynczego pliku. Ostatecznie uzyskasz różne ścieżki do plików, w zależności od tego, jak uruchamiane jest przekształcenie. Może to być bardzo mylące.

## <a name="adding-reference-and-include-paths"></a>Dodawanie odwołania i ścieżek dołączania

Host ma domyślny zestaw ścieżek wyszukiwania zestawów, do których odwołują się szablony. Aby dodać do tego zestawu:

```
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Aby ustawić foldery, w których będą wyszukiwane pliki nagłówkowe, należy dostarczyć listę oddzieloną średnikami. Zwykle dodaje się je do istniejącej listy folderów.

```
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="pass-build-context-data-into-the-templates"></a><a name="parameters"></a> Przekaż dane kontekstu kompilacji do szablonów

Można ustawić wartości parametrów w pliku projektu. Na przykład można przekazać właściwości kompilacji i [zmienne środowiskowe](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

W szablonie tekstowym Ustaw `hostspecific` w dyrektywie Template. Aby uzyskać wartości, użyj dyrektywy [Parameter](../modeling/t4-parameter-directive.md) :

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

## <a name="using-project-properties-in-assembly-and-include-directives"></a><a name="msbuild"></a> Korzystanie z właściwości projektu w dyrektywach Assembly i include

Makra Visual Studio, takie jak $(SolutionDir), nie działają w MSBuild. Zamiast tego można użyć właściwości projektu.

Wyedytuj plik .csproj lub .vbproj, aby zdefiniować właściwość projektu. Ten przykład definiuje właściwość o nazwie `myLibFolder` :

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

Teraz możesz korzystać ze swojej właściwości projektu w dyrektywach zestawu i dołączania:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

 Te dyrektywy pobierają wartości z T4parameterValues zarówno w hostach MSBuild, jak i Visual Studio.

## <a name="q--a"></a>Pytania i odpowiedzi

**Dlaczego warto przetwarzać szablony na serwerze kompilacji? Zostały już przekształcone szablony w programie Visual Studio przed zapisaniem mojego kodu.**

Jeżeli zaktualizujesz dołączony plik lub inny plik odczytany przez szablon, Visual Studio nie przekształci pliku automatycznie. Przekształcanie szablonów w ramach kompilacji zapewnia, że wszystko jest aktualne.

**Jakie są inne opcje przekształcania szablonów tekstowych?**

- [Narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) można używać w skryptach poleceń. W większości przypadków program MSBuild jest łatwiejszy w użyciu.

- [Wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)

- [Szablony tekstu czasu projektowania](../modeling/design-time-code-generation-by-using-t4-text-templates.md) są przekształcane przez program Visual Studio.

- [Szablony tekstu czasu wykonywania](../modeling/run-time-text-generation-with-t4-text-templates.md) są przekształcane w czasie wykonywania w aplikacji.

## <a name="read-more"></a>Dowiedz się więcej

Dobrą wskazówkę znajdziesz w szablonie T4 MSbuild, $(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets

- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)
- [Visual Studio Wizualizacja i Modeling SDK](https://www.visualstudio.com/)
- [Oleg Sych: zrozumienie aparatu T4: integracja z programem MSBuild](https://github.com/olegsych/T4Toolbox)
