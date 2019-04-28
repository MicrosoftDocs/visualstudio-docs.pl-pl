---
title: Generowanie kodu w procesie kompilacji
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 07f7c91c74961fa846abb70637f358de59d0eb94
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62424054"
---
# <a name="code-generation-in-a-build-process"></a>Generowanie kodu w procesie kompilacji

[Transformacja tekstu](../modeling/code-generation-and-t4-text-templates.md) mogą być wywoływane jako część [proces kompilacji](/azure/devops/pipelines/index) rozwiązania Visual Studio. Istnieją zadania kompilacji, które są przeznaczone do przekształcania tekstu. Zadania kompilacji T4 uruchamiają szablon tekstowy czasu projektowania, a także kompilują szablony tekstowe czasu wykonywania (wstępnie przetworzone).

Istnieją pewne różnice w czynnościach, które mogą wykonać zadania kompilacji, wszystko zależy od użytego aparatu kompilacji. Podczas kompilowania rozwiązania w programie Visual Studio szablon tekstowy może uzyskać dostęp do API Visual Studio (EnvDTE), gdy [hostspecific = "true"](../modeling/t4-template-directive.md) ma ustawioną wartość atrybutu. Ale nie jest to prawdą podczas kompilowania rozwiązania z wiersza polecenia lub po zainicjowaniu kompilacji serwerowej za pomocą programu Visual Studio. W tych przypadkach kompilację wykonuje MSBuild i użyty zostaje inny host T4.

Oznacza to, że nie masz dostępu do elementów, takich jak nazwy plików projektu w taki sam sposób podczas kompilacji szablonu tekstu w MSBuild. Można jednak [przekazać informacje o środowisku do szablonów tekstowych i procesorów dyrektyw przy użyciu parametrów kompilacji](#parameters).

## <a name="buildserver"></a> Konfigurowanie maszyn

Aby włączyć zadania kompilacji na komputerze deweloperskim, należy zainstalować zestaw Modeling SDK for Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Jeśli [serwer kompilacji](/azure/devops/pipelines/agents/agents) uruchomienia na komputerze, na którym nie zainstalowano programu Visual Studio, skopiuj następujące pliki do komputera kompilacji z komputera deweloperskiego. Zastąp ostatnich numerów wersji "*".

- $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

    - Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

    - Microsoft.TextTemplating.Build.Tasks.dll

    - Microsoft.TextTemplating.targets

- $(ProgramFiles)\Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

    - Microsoft.VisualStudio.TextTemplating.*.0.dll

    - Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (several files)

    - Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

- $(ProgramFiles)\Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\

    - Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll

## <a name="to-edit-the-project-file"></a>Aby edytować plik projektu

Należy edytować plik projektu, aby skonfigurować niektóre funkcje w programie MSBuild.

W **Eksploratora rozwiązań**, wybierz **zwolnienie** przejdź do menu kliknij prawym przyciskiem myszy w projekcie. Pozwala to na edycję pliku .csproj lub .vbproj w edytorze XML.

Po zakończeniu edycji wybierz **Załaduj ponownie**.

## <a name="import-the-text-transformation-targets"></a>Importowanie obiektów docelowych przekształcenia tekstu

W pliku .vbproj lub .csproj znajdź taki wiersz:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- lub —

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Po tym wierszu wstaw import szablonu tekstu:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">16.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transform-templates-in-a-build"></a>Przekształcanie szablonów podczas kompilacji

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

## <a name="customize-the-build-process"></a>Dostosowywanie procesu kompilacji

Transformacja tekstu ma miejsce przed innymi zadaniami w procesie kompilacji. Można zdefiniować zadania, które są wywoływane przed przekształceniem i po, ustawiając właściwości `$(BeforeTransform)` i `$(AfterTransform)`:

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

W `AfterTransform`, możesz odwoływać się do listy plików:

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

Jest użytecznym folderem do przekierowania `$(IntermediateOutputPath).`

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

Określenie OutputFileName lub OutputFilePath nie jest zalecane, jeśli przekształcany również szablon wewnątrz VS przy użyciu Transform All lub uruchomione jest generator pojedynczego pliku. Ostatecznie uzyskasz różne ścieżki do plików, w zależności od tego, jak uruchamiane jest przekształcenie. Może to być bardzo mylące.

## <a name="add-reference-and-include-paths"></a>Dodawanie odwołania i ścieżek dołączania

Host ma domyślny zestaw ścieżek wyszukiwania zestawów, do których odwołują się szablony. Aby dodać do tego zestawu:

```xml
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Aby ustawić foldery, w których będą wyszukiwane pliki nagłówkowe, należy dostarczyć listę oddzieloną średnikami. Zwykle dodaje się je do istniejącej listy folderów.

```xml
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="parameters"></a> Przekazywanie danych kontekstu kompilacji w szablonach

Można ustawić wartości parametrów w pliku projektu. Na przykład, można przekazać [kompilacji](../msbuild/msbuild-properties.md) właściwości i [zmienne środowiskowe](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

W szablonie tekstu, ustaw `hostspecific` w dyrektywie szablonu. Użyj [parametru](../modeling/t4-parameter-directive.md) dyrektywy do uzyskania wartości:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

W procesorze dyrektywy można wywołać [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` pobiera dane z `T4ParameterValues` tylko kiedy używasz MSBuild. Kiedy przekształcasz szablon przy użyciu Visual Studio, parametry mają wartości domyślne.

## <a name="msbuild"></a> Użyj właściwości projektu w zestawie i dyrektyw include

Makra programu Visual Studio, takich jak **$(SolutionDir)** nie działają w MSBuild. Zamiast tego można użyć właściwości projektu.

Edytuj swoje *.csproj* lub *.vbproj* plik, aby zdefiniować właściwość projektu. Ten przykład definiuje właściwość o nazwie **myLibFolder**:

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

**Dlaczego chcesz przekształcić szablony w serwerze kompilacji? Właśnie przekształciłem szablony w programie Visual Studio przed sprawdzeniem kodu.**

Jeśli zaktualizujesz dołączony plik lub inny plik odczytany przez szablon programu Visual Studio nie przekształci pliku automatycznie. Przekształcanie szablonów w ramach kompilacji zapewnia, że wszystko jest aktualne.

**Co to są inne opcje przekształceń szablonu tekstu?**

- [Narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) można używać w skryptach poleceń. W większości przypadków jest łatwiejszy w obsłudze programu MSBuild.

- [Wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)

- [Szablony tekstu czasu projektowania](../modeling/design-time-code-generation-by-using-t4-text-templates.md) są przekształcane przez program Visual Studio.

- [Szablony tekstowe czasu wykonania](../modeling/run-time-text-generation-with-t4-text-templates.md) są przekształcane w czasie wykonywania w aplikacji.

## <a name="see-also"></a>Zobacz także

::: moniker range="vs-2017"

- W szablonie T4 MSbuild na jest dobrą wskazówkę *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets*

::: moniker-end

::: moniker range=">=vs-2019"

- W szablonie T4 MSbuild na jest dobrą wskazówkę *% ProgramFiles (x86) %\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets*

::: moniker-end

- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)
