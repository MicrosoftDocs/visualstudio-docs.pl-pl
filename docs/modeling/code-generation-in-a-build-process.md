---
title: Generowanie kodu w procesie kompilacji
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: af0039fb8c945062bc19fa647b477c40c44d5346
ms.sourcegitcommit: a876fcc75321f9c30729121cae83f400973f9d9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2020
ms.locfileid: "92298202"
---
# <a name="invoke-text-transformation-in-the-build-process"></a>Wywołaj transformację tekstu w procesie kompilacji

[Transformację tekstu](../modeling/code-generation-and-t4-text-templates.md) można wywołać w ramach [procesu kompilacji](/azure/devops/pipelines/index) rozwiązania programu Visual Studio. Istnieją zadania kompilacji, które są przeznaczone do przekształcania tekstu. Zadania kompilacji T4 uruchamiają szablon tekstowy czasu projektowania, a także kompilują szablony tekstowe czasu wykonywania (wstępnie przetworzone).

Istnieją pewne różnice w czynnościach, które mogą wykonać zadania kompilacji, wszystko zależy od użytego aparatu kompilacji. Podczas kompilowania rozwiązania w programie Visual Studio szablon tekstowy może uzyskać dostęp do interfejsu API programu Visual Studio (EnvDTE), jeśli ustawiono atrybut [hostspecific = "true"](../modeling/t4-template-directive.md) . Ale to nie jest prawdziwe w przypadku kompilowania rozwiązania z wiersza polecenia lub po zainicjowaniu kompilacji serwera za pomocą programu Visual Studio. W tych przypadkach kompilację wykonuje MSBuild i użyty zostaje inny host T4. Oznacza to, że nie można uzyskać dostępu do elementów, takich jak nazwy plików projektu w taki sam sposób, jak w przypadku kompilowania szablonu tekstowego przy użyciu programu MSBuild. Można jednak [przekazać informacje o środowisku do szablonów tekstowych i procesorów dyrektywy przy użyciu parametrów kompilacji](#parameters).

## <a name="configure-your-machines"></a><a name="buildserver"></a> Konfigurowanie maszyn

Aby włączyć zadania kompilacji na komputerze deweloperskim, Zainstaluj zestaw SDK modelowania dla programu Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Jeśli [serwer kompilacji](/azure/devops/pipelines/agents/agents) działa na komputerze, na którym nie zainstalowano programu Visual Studio, Skopiuj następujące pliki do komputera kompilacji z komputera deweloperskiego:

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VisualStudio\v16.0\TextTemplating

  - Microsoft.VisualStudio.TextTemplating.Sdk.Host.15.0.dll
  - Microsoft.TextTemplating.Build.Tasks.dll
  - Microsoft.TextTemplating.targets

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft.VisualStudio.TextTemplating.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.Interfaces.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.VSHost.15.0.dll

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\IDE\PublicAssemblies

  - Microsoft.VisualStudio.TextTemplating.Modeling.15.0.dll

> [!TIP]
> Jeśli otrzymasz `MissingMethodException` metodę Microsoft. CodeAnalysis podczas uruchamiania elementów docelowych kompilacji TextTemplating na serwerze kompilacji, upewnij się, że zestawy Roslyn znajdują się w katalogu o nazwie *Roslyn* , który znajduje się w tym samym katalogu, co plik wykonywalny kompilacji (na przykład *msbuild.exe*).

## <a name="edit-the-project-file"></a>Edytuj plik projektu

Edytuj plik projektu, aby skonfigurować niektóre funkcje programu MSBuild, na przykład importując elementy docelowe transformacji tekstu.

W **Eksplorator rozwiązań**wybierz pozycję **Zwolnij** z menu dostępnego po kliknięciu prawym przyciskiem myszy projektu. Pozwala to na edycję pliku .csproj lub .vbproj w edytorze XML. Po zakończeniu edycji wybierz pozycję **Załaduj ponownie**.

## <a name="import-the-text-transformation-targets"></a>Importuj cele transformacji tekstu

W pliku .vbproj lub .csproj znajdź taki wiersz:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- oraz

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Po tym wierszu wstaw import szablonu tekstu:

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

## <a name="transform-templates-in-a-build"></a>Przekształcanie szablonów w kompilacji

Istnieje kilka właściwości, które można wstawić do pliku projektu, aby móc kontrolować zadanie przekształcenia:

- Należy uruchomić zadanie przekształceń na początku każdej kompilacji:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Zastąp pliki, które są tylko do odczytu, na przykład ponieważ nie są wyewidencjonowane:

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

     Domyślnie zadanie programu MSBuild firmy T4 ponownie generuje plik wyjściowy, jeśli jest starszy niż:

     - plik szablonu
     - wszystkie pliki, które są uwzględnione
     - wszystkie pliki, które wcześniej były odczytywane przez szablon lub przez procesor dyrektywy, którego używa

     Jest to bardziej wydajny test zależności, niż jest używany przez polecenie **Przekształć wszystkie szablony** w programie Visual Studio, które porównuje daty szablonu i pliku wyjściowego.

Aby wykonać tylko przekształcenia tekstu w projekcie, należy wywołać zadanie TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Aby przekształcić określony szablon tekstowy:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

Można używać symboli wieloznacznych w TransformFile:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Kontrola źródła

Nie ma żadnych szczególnych wbudowanych funkcji integracji z systemem kontroli źródła. Można jednak dodać własne rozszerzenia, na przykład, aby wyewidencjonować i zaewidencjonować wygenerowany plik. Domyślnie zadanie przekształcania tekstu zapobiega zastąpieniu pliku, który jest oznaczony jako tylko do odczytu. Gdy taki plik zostanie napotkany, błąd jest rejestrowany w Lista błędów programu Visual Studio, a zadanie zakończy się niepowodzeniem.

Aby określić, że pliki tylko do odczytu powinny być zastąpione, wstaw tę właściwość:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

Jeśli nie dostosowano kroku dostosujesz, ostrzeżenie zostanie zarejestrowane w Lista błędów, gdy plik zostanie nadpisany.

## <a name="customize-the-build-process"></a>Dostosuj proces kompilacji

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

- GeneratedFiles — lista plików zapisanych przez proces. Dla tych plików, które zastąpiły istniejące pliki tylko do odczytu, `%(GeneratedFiles.ReadOnlyFileOverwritten)` będą spełnione. Pliki te można wyewidencjonować z kontroli źródła.

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

Przydatnym folderem do przekierowania jest `$(IntermediateOutputPath)` .

Jeśli określisz nazwę pliku wyjściowego, ma pierwszeństwo przed rozszerzeniem określonym w dyrektywie Output w szablonach.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Określenie elementu OutputFileName lub OutputFilePath nie jest zalecane, jeśli są również transformacje szablony w programie Visual Studio przy użyciu **transformacji All** lub uruchamiania generatora pojedynczego pliku. W zależności od sposobu, w jaki Wyzwalasz transformację, będziesz kończyć się różnymi ścieżkami plików. Może to być mylące.

## <a name="add-reference-and-include-paths"></a>Dodaj odwołania i ścieżki dołączania

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

## <a name="pass-build-context-data-into-the-templates"></a><a name="parameters"></a> Przekaż dane kontekstu kompilacji do szablonów

Można ustawić wartości parametrów w pliku projektu. Na przykład można przekazać właściwości [kompilacji](../msbuild/msbuild-properties.md) i [zmienne środowiskowe](../msbuild/how-to-use-environment-variables-in-a-build.md):

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

W procesorze dyrektywy można wywołać [ITextTemplatingEngineHost. ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` Pobiera dane z `T4ParameterValues` tylko wtedy, gdy używasz programu MSBuild. Gdy przekształcasz szablon przy użyciu programu Visual Studio, parametry mają wartości domyślne.

## <a name="use-project-properties-in-assembly-and-include-directives"></a><a name="msbuild"></a> Korzystanie z właściwości projektu w dyrektywach Assembly i include

Makra programu Visual Studio, takie jak **$ (SolutionDir)** , nie działają w programie MSBuild. Zamiast tego można użyć właściwości projektu.

Edytuj plik *. csproj* lub *. vbproj* , aby zdefiniować właściwość projektu. Ten przykład definiuje właściwość o nazwie **myLibFolder**:

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

W przypadku zaktualizowania dołączonego pliku lub innego pliku odczytanego przez szablon program Visual Studio nie przekształca pliku automatycznie. Przekształcanie szablonów w ramach kompilacji gwarantuje, że wszystko jest aktualne.

**Jakie są inne opcje przekształcania szablonów tekstowych?**

- [Narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) można używać w skryptach poleceń. W większości przypadków łatwiejsze jest korzystanie z programu MSBuild.

- [Wywołaj transformację tekstu w rozszerzeniu programu Visual Studio](../modeling/invoking-text-transformation-in-a-vs-extension.md).

- [Szablony tekstu czasu projektowania](../modeling/design-time-code-generation-by-using-t4-text-templates.md) są przekształcane przez program Visual Studio.

- [Szablony tekstu w czasie wykonywania](../modeling/run-time-text-generation-with-t4-text-templates.md) są przekształcane w czasie wykonywania w aplikacji.

## <a name="see-also"></a>Zobacz też

::: moniker range="vs-2017"

- Dobrym wskazówkami w szablonie programu MSbuild T4 w `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

::: moniker range=">=vs-2019"

- Dobrym wskazówkami w szablonie programu MSbuild T4 w `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

- [Napisz szablon tekstowy T4](../modeling/writing-a-t4-text-template.md)
