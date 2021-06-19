---
title: Generowanie kodu w procesie kompilacji
description: Dowiedz się, jak można wywołać przekształcenie tekstu w ramach procesu kompilacji Visual Studio rozwiązania.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7db1b41df5007678c84be71f34aea110c04348c1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389751"
---
# <a name="invoke-text-transformation-in-the-build-process"></a>Wywoływanie przekształcenia tekstu w procesie kompilacji

[Przekształcanie](../modeling/code-generation-and-t4-text-templates.md) tekstu może być wywoływane w ramach [procesu kompilacji](/azure/devops/pipelines/index) Visual Studio rozwiązania. Istnieją zadania kompilacji, które są przeznaczone do przekształcania tekstu. Zadania kompilacji T4 uruchamiają szablon tekstowy czasu projektowania, a także kompilują szablony tekstowe czasu wykonywania (wstępnie przetworzone).

Istnieją pewne różnice w czynnościach, które mogą wykonać zadania kompilacji, wszystko zależy od użytego aparatu kompilacji. Podczas kompilowania rozwiązania w Visual Studio szablon tekstowy może uzyskać dostęp do interfejsu API usługi Visual Studio (EnvDTE), jeśli ustawiono atrybut [hostspecific="true".](../modeling/t4-template-directive.md) Nie jest to jednak prawdziwe w przypadku kompilowania rozwiązania z wiersza polecenia lub inicjowania kompilacji serwera za pośrednictwem Visual Studio. W tych przypadkach kompilację wykonuje MSBuild i użyty zostaje inny host T4. Oznacza to, że podczas kompilowania szablonu tekstowego przy użyciu programu MSBuild nie można uzyskać dostępu do takich rzeczy jak nazwy plików projektu. Można jednak przekazać informacje [o środowisku do szablonów tekstowych](#parameters)i procesorów dyrektyw przy użyciu parametrów kompilacji .

## <a name="configure-your-machines"></a><a name="buildserver"></a> Konfigurowanie maszyn

Aby włączyć zadania kompilacji na komputerze dewelopera, zainstaluj zestaw SDK modelowania dla Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Jeśli [serwer kompilacji](/azure/devops/pipelines/agents/agents) działa na komputerze, który nie ma zainstalowanego Visual Studio, skopiuj następujące pliki na komputer kompilacji z komputera dewelopera:

- %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VisualStudio\v16.0\TextTemplating

  - Microsoft.VisualStudio.TextTemplating.Sdk.Host.15.0.dll
  - Microsoft.TextTemplating.Build.Tasks.dll
  - Microsoft.TextTemplating.targets

- %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft.VisualStudio.TextTemplating.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.Interfaces.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.VSHost.15.0.dll

- %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\IDE\PublicAssemblies

  - Microsoft.VisualStudio.TextTemplating.Modeling.15.0.dll

> [!TIP]
> Jeśli podczas uruchamiania obiektów docelowych kompilacji TextTemplating na serwerze kompilacji otrzymasz plik dla metody Microsoft.CodeAnalysis, upewnij się, że zestawy Roslyn znajdują się w katalogu o nazwie `MissingMethodException` *Roslyn,* który jest w tym samym katalogu co plik wykonywalny kompilacji (na przykład *msbuild.exe*).

## <a name="edit-the-project-file"></a>Edytowanie pliku projektu

Edytuj plik projektu, aby skonfigurować niektóre funkcje w programie MSBuild, na przykład importując docelowe przekształcenia tekstu.

W **Eksplorator rozwiązań** wybierz pozycję **Unload (Zwolnij)** z menu projektu dostępnego po kliknięciu prawym przyciskiem myszy. Pozwala to na edycję pliku .csproj lub .vbproj w edytorze XML. Po zakończeniu edycji wybierz pozycję **Załaduj ponownie**.

## <a name="import-the-text-transformation-targets"></a>Importowanie docelowych przekształceń tekstu

W pliku .vbproj lub .csproj znajdź taki wiersz:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- lub —

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

     Domyślnie zadanie T4 MSBuild ponownie generuje plik wyjściowy, jeśli jest starszy niż:

     - plik szablonu
     - wszystkie pliki, które są dołączone
     - wszystkie pliki, które zostały wcześniej odczytane przez szablon lub przez procesor dyrektywy, z których korzysta

     Jest to bardziej zaawansowany test zależności niż  używany przez polecenie Przekształć wszystkie szablony w Visual Studio, które porównuje tylko daty szablonu i pliku wyjściowego.

Aby wykonać tylko przekształcenia tekstu w projekcie, należy wywołać zadanie TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Aby przekształcić określony szablon tekstowy:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

Można używać symboli wieloznacznych w TransformFile:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Kontrola źródła

Nie ma żadnych szczególnych wbudowanych funkcji integracji z systemem kontroli źródła. Można jednak dodać własne rozszerzenia, na przykład aby wyewidencjonać i zaewidencjonać wygenerowany plik. Domyślnie zadanie przekształcania tekstu pozwala uniknąć nadpisania pliku, który jest oznaczony jako tylko do odczytu. Po napotkaniu takiego pliku na liście błędów jest rejestrowany Visual Studio błąd, a zadanie kończy się niepowodzeniem.

Aby określić, że pliki tylko do odczytu powinny być zastąpione, wstaw tę właściwość:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

O ile nie dostosujesz kroku przetwarzania postprocesowego, ostrzeżenie zostanie zarejestrowane na liście błędów, gdy plik zostanie zastąpiony.

## <a name="customize-the-build-process"></a>Dostosowywanie procesu kompilacji

Transformacja tekstu ma miejsce przed innymi zadaniami w procesie kompilacji. Zadania wywoływane przed przekształceniem i po nim można zdefiniować, ustawiając właściwości `$(BeforeTransform)` i `$(AfterTransform)` :

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

W `AfterTransform` pliku można odwoływać się do list plików:

- GeneratedFiles — lista plików zapisanych przez proces. W przypadku plików, które przesłoniły istniejące pliki tylko do `%(GeneratedFiles.ReadOnlyFileOverwritten)` odczytu, wartość będzie mieć wartość true. Pliki te można wyewidencjonować z kontroli źródła.

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

Przydatnym folderem do przekierowywania jest `$(IntermediateOutputPath)` .

Jeśli określisz nazwę pliku wyjściowego, ma pierwszeństwo przed rozszerzeniem określonym w dyrektywie output w szablonach.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Określanie parametru OutputFileName lub OutputFilePath nie jest zalecane, jeśli przekształcasz  również szablony wewnątrz Visual Studio za pomocą funkcji Przekształć wszystko lub uruchamiasz generator pojedynczego pliku. W zależności od sposobu wyzwolenia przekształcenia będą dostępne różne ścieżki plików. Może to być mylące.

## <a name="add-reference-and-include-paths"></a>Dodawanie ścieżek odwołania i dołączania

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

W szablonie tekstowym ustaw `hostspecific` w dyrektywie template. Użyj dyrektywy [parameter,](../modeling/t4-parameter-directive.md) aby uzyskać wartości:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

W procesorze dyrektywy można wywołać [ITextTemplatingEngineHost.ResolveParameterValue:](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\))

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` pobiera dane tylko `T4ParameterValues` wtedy, gdy używasz programu MSBuild. Podczas przekształcania szablonu przy użyciu Visual Studio parametry mają wartości domyślne.

## <a name="use-project-properties-in-assembly-and-include-directives"></a><a name="msbuild"></a> Używanie właściwości projektu w dyrektywach assembly i include

Visual Studio makra, takie **jak $(SolutionDir),** nie działają w programie MSBuild. Zamiast tego można użyć właściwości projektu.

Edytuj plik *csproj* lub *vbproj,* aby zdefiniować właściwość projektu. W tym przykładzie zdefiniowano właściwość **o nazwie myLibFolder**:

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

**Dlaczego warto przekształcać szablony na serwerze kompilacji? Szablony zostały już przekształcone w Visual Studio przed zaewidencjonowanie kodu.**

Jeśli zaktualizujemy dołączony plik lub inny plik odczytany przez szablon, Visual Studio plik nie zostanie automatycznie przekształcony. Przekształcanie szablonów w ramach kompilacji zapewnia, że wszystko jest aktualne.

**Jakie inne opcje przekształcania szablonów tekstowych są dostępne?**

- Narzędzie [TextTransform może](../modeling/generating-files-with-the-texttransform-utility.md) być używane w skryptach poleceń. W większości przypadków łatwiej jest używać programu MSBuild.

- [Wywoływanie przekształcenia tekstu w rozszerzeniu Visual Studio .](../modeling/invoking-text-transformation-in-a-vs-extension.md)

- [Szablony tekstowe czasu projektowania](../modeling/design-time-code-generation-by-using-t4-text-templates.md) są przekształcane przez Visual Studio.

- [Szablony tekstowe czasu uruchamiania są](../modeling/run-time-text-generation-with-t4-text-templates.md) przekształcane w czasie rzeczywistym w aplikacji.

## <a name="see-also"></a>Zobacz też

::: moniker range="vs-2017"

- W szablonie T4 MSbuild można znaleźć dobre wskazówki na stronie `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

::: moniker range=">=vs-2019"

- W szablonie T4 MSbuild można znaleźć dobre wskazówki na stronie `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)
