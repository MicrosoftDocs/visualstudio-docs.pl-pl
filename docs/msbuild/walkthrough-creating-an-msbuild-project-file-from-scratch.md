---
title: 'Przewodnik: Tworzenie pliku projektu MSBuild od podstaw | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44c93b0c9a651bd23c34179bc9e21fcd77bad15f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052274"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>Przewodnik: Tworzenie pliku projektu MSBuild od podstaw
Języki programowania, które obsługują program .NET Framework używają plików projektu MSBuild do opisywania i kontrolowania procesu tworzenia aplikacji. Gdy używasz programu Visual Studio do tworzenia pliku projektu programu MSBuild, właściwy XML jest automatycznie dodawany do pliku. Jednak może okazać się pomocne w zrozumieniu, w jaki sposób XML jest zorganizowany i jak mogą zmienić go, aby kontrolować kompilację.

 Aby dowiedzieć się, jak tworzenie pliku projektu dla projektu w języku C++, zobacz [MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp).

 W tym instruktażu przedstawiono sposób przyrostowego tworzenia podstawowego pliku projektu za pomocą edytora tekstu. Instruktaż obejmuje następujące kroki:

1. Utwórz minimalny plik źródłowy aplikacji.

2. Utwórz minimalny plik projektu MSBuild.

3. Rozszerz zmienną środowiskową PATH, aby uwzględnić MSBuild.

4. Kompiluj aplikację przy użyciu pliku projektu.

5. Dodaj właściwości do kontrolowania kompilacji.

6. Steruj kompilacją przez zmianę wartości właściwości.

7. Dodawanie elementów docelowych do kompilacji.

8. Steruj kompilacją przez określenie obiektów docelowych.

9. Kompiluj przyrostowo.

W tym przewodniku przedstawiono sposób budowania projektu w wierszu polecenia i przeglądania wyników. Aby uzyskać więcej informacji na temat MSBuild i sposobach uruchamiania MSBuild w wierszu polecenia, zobacz [instruktażu: Użyj programu MSBuild](../msbuild/walkthrough-using-msbuild.md).

Aby ukończyć Instruktaż, musisz mieć .NET Framework (wersja 2.0, 3.5, 4.0 lub 4.5) zainstalowane, ponieważ zawiera on MSBuild i kompilator Visual C#, które są wymagane do instruktażu.

## <a name="create-a-minimal-application"></a>Tworzenie minimalnej aplikacji
 W tej sekcji przedstawiono sposób tworzenia minimalne Visual C# plik źródłowy aplikacji przy użyciu typu text editor.

#### <a name="to-create-the-minimal-application"></a>Aby utworzyć minimalną aplikację

1. W wierszu polecenia przejdź do folderu, w którym chcesz utworzyć aplikację, na przykład *\My dokumenty\\*  lub *\Desktop\\*.

2. Typ **md HelloWorld** utworzyć podfolder o nazwie *\HelloWorld\\*.

3. Typ **cd HelloWorld** można zmienić do nowego folderu.

4. Otwórz Notatnik lub inny edytor tekstu, a następnie wpisz poniższy kod.

    ```csharp
    using System;

    class HelloWorld
    {
        static void Main()
        {
    #if DebugConfig
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");
    #endif

            Console.WriteLine("Hello, world!");
        }
    }
    ```

5. Zapisz ten plik źródłowy kodu i nadaj mu *Helloworld.cs*.

6. Kompiluj aplikację wpisując **csc helloworld.cs** w wierszu polecenia.

7. Przetestuj aplikację wpisując **helloworld** w wierszu polecenia.

     **Witaj, świecie!** powinien zostać wyświetlony komunikat.

8. Usuń aplikację wpisując **del helloworld.exe** w wierszu polecenia.

## <a name="create-a-minimal-msbuild-project-file"></a>Utwórz minimalny plik projektu MSBuild
 Teraz, gdy minimalny plik źródłowy aplikacji, można utworzyć minimalny plik projektu do skompilowania aplikacji. Ten plik projektu zawiera następujące elementy:

- Wymagany katalog główny `Project` węzła.

- `ItemGroup` Węzeł zawiera elementy jednostki.

- Element jednostki odwołujący się do pliku źródłowego aplikacji.

- A `Target` węzła zawiera zadania, które są wymagane do kompilowania aplikacji.

- A `Task` element, aby uruchomić kompilator Visual C# do kompilowania aplikacji.

#### <a name="to-create-a-minimal-msbuild-project-file"></a>Aby utworzyć plik projektu minimalnego MSBuild

1. W edytorze tekstów należy zastąpić istniejący tekst za pomocą tych dwóch linijek:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Wstaw ten `ItemGroup` węzła jako element podrzędny `Project` węzła:

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Zwróć uwagę że `ItemGroup` zawiera już element pozycji.

3. Dodaj `Target` węzła jako element podrzędny `Project` węzła. Nazwij węzeł `Build`.

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Wstaw ten element zadania jako element podrzędny `Target` węzła:

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. Zapisz ten plik projektu i nadaj mu nazwę *Helloworld.csproj*.

Plik projektu minimalnego powinien przypominać następujący kod:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <Csc Sources="@(Compile)"/>  
  </Target>
</Project>
```

Zadania w lokalizacji docelowej kompilacji są wykonywane sekwencyjnie. W tym przypadku kompilator Visual C# `Csc` zadania jest jedynym zadaniem. Oczekuje listy plików źródłowych do kompilowania i jest określony przez wartość `Compile` elementu. `Compile` Element odwołuje się tylko do jednego pliku źródłowego *Helloworld.cs*.

> [!NOTE]
>  W pozycji elementu, można użyć znaku wieloznacznego gwiazdki (\*) Aby odwołać wszystkie pliki, które mają *.cs* plikiem, w następujący sposób:
>
>  `<Compile Include="*.cs" />`
>
>  Jednak firma Microsoft nie zaleca się stosowania symboli wieloznacznych ponieważ sprawia, że debugowanie i selektywne ukierunkowanie jest trudniejsze, jeżeli pliki źródłowe są dodawane lub usuwane.

## <a name="extend-the-path-to-include-msbuild"></a>Rozszerzanie ścieżki, aby uwzględnić MSBuild
 Aby korzystać z programu MSBuild, należy rozszerzyć zmienną środowiskową PATH, aby dołączyć folder .NET Framework.

#### <a name="to-add-msbuild-to-your-path"></a>Aby dodać programu MSBuild do ścieżki

- Począwszy od programu Visual Studio 2013, możesz znaleźć *MSBuild.exe* w folderze programu MSBuild (*%ProgramFiles%\MSBuild* na 32-bitowym systemie operacyjnym lub *% ProgramFiles (x86) %\MSBuild*na 64-bitowym systemie operacyjnym).

     W wierszu polecenia wpisz **Ustaw PATH=%PATH%;%ProgramFiles%\MSBuild** lub **Ustaw ŚCIEŻKĘ = % PATH %; % ProgramFiles (x86) %\MSBuild**.

     Alternatywnie, jeśli masz zainstalowany program Visual Studio, można użyć **Visual Studio Command Prompt**, który zawiera ścieżkę, która obejmuje *MSBuild* folderu.

## <a name="use-the-project-file-to-build-the-application"></a>Tworzenie aplikacji przy użyciu pliku projektu
 Teraz Aby skompilować aplikację, należy użyć pliku projektu, który został utworzony.

#### <a name="to-build-the-application"></a>Aby skompilować aplikację

1. W wierszu polecenia wpisz **msbuild helloworld.csproj - t: tworzenie**.

     To skompiluje kompilację docelową projektu HelloWorld wywołując kompilator Visual C# do tworzenia aplikacji Helloworld.

2. Przetestuj aplikację wpisując **helloworld**.

     **Witaj, świecie!** powinien zostać wyświetlony komunikat.

> [!NOTE]
>  Więcej szczegółów na temat kompilacji można zobaczyć, zwiększając poziom szczegółowości. Aby ustawić poziom szczegółowości "szczegółowe", wpisz następujące polecenie w wierszu polecenia:
>
>  **Program MSBuild helloworld.csproj - t: kompilacja — poziom szczegółowości: szczegółowe**

## <a name="add-build-properties"></a>Dodawanie właściwości kompilacji
 Można dodać właściwości kompilacji do pliku projektu, aby dalej kontrolować kompilację. Teraz dodaj następujące właściwości:

- `AssemblyName` Właściwość, aby określić nazwę aplikacji.

- `OutputPath` Właściwości w celu określenia folderu zawierającego aplikację.

#### <a name="to-add-build-properties"></a>Aby dodać właściwości kompilacji

1. Usuń istniejącą aplikację, wpisując **del helloworld.exe** w wierszu polecenia.

2. W pliku projektu, Wstaw `PropertyGroup` elementu tuż po otwarciu `Project` elementu:

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Dodaj to zadanie do docelowej kompilacji tuż przed `Csc` zadań:

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     `MakeDir` Zadanie tworzy folder, który jest nazwany przez `OutputPath` właściwości, pod warunkiem, że żaden folder o tej nazwie obecnie istnieje.

4. Dodaj tę `OutputAssembly` atrybutu `Csc` zadań:

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     To powoduje, że kompilator Visual C# produkuje zestawu, który jest nazwany przez `AssemblyName` właściwość i umieść go w folderze, który jest nazwany przez `OutputPath` właściwości.

5. Zapisz zmiany.

Plik projektu minimalnego powinien teraz przypominać następujący kod:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
</Project>
```

> [!NOTE]
>  Firma Microsoft zaleca dodanie ukośnik odwrotny (\\) separator ścieżki na końcu nazwy folderu, w przypadku określenia `OutputPath` elementu, zamiast dodawania go w `OutputAssembly` atrybutu `Csc` zadania. W związku z tym,
>
>  `<OutputPath>Bin\</OutputPath>`
>
>  `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`
>
>  jest lepsze niż
>
>  `<OutputPath>Bin</OutputPath>`
>
>  `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>Testowanie właściwości kompilacji
 Teraz można skompilować aplikację przy użyciu pliku projektu użyto właściwości kompilacji do określenia nazwy folderu i aplikacji danych wyjściowych.

#### <a name="to-test-the-build-properties"></a>Aby przetestować właściwości kompilacji

1. W wierszu polecenia wpisz **msbuild helloworld.csproj - t: tworzenie**.

     Spowoduje to utworzenie *\Bin\\*  folder, a następnie wywołuje kompilatora Visual C#, aby utworzyć *MSBuildSample* aplikacji i umieszcza go w *\Bin\\* folderu.

2. Aby sprawdzić, czy *\Bin\\*  folder został utworzony, oraz że zawiera on *MSBuildSample* aplikacji, należy wpisać **katalog Bin**.

3. Przetestuj aplikację wpisując **Bin\MSBuildSample**.

     **Witaj, świecie!** powinien zostać wyświetlony komunikat.

## <a name="add-build-targets"></a>Dodaj obiekty docelowe kompilacji
 Następnie dodaj jeszcze dwa obiekty docelowe do pliku projektu:

- Oczyść element docelowy usuwa stare pliki.

- Element docelowy ponownej kompilacji, który używa `DependsOnTargets` atrybutu, aby wymusić czystą zadania do uruchomienia przed zadaniem kompilacji.

Teraz, gdy masz wiele elementów docelowych, można ustawić element docelowy kompilacji jako domyślnego obiektu docelowego.

#### <a name="to-add-build-targets"></a>Aby dodać obiekty docelowe kompilacji

1. W pliku projektu należy dodać dwa obiekty docelowe po docelowej kompilacji:

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     Czyste miejsce docelowe wywołuje zadanie Usuń do usunięcia aplikacji. Miejsce docelowe powtórnej kompilacji nie jest możliwe, dopóki nie uruchomiono zarówno czystego miejsce docelowego i celu kompilacji. Chociaż miejsce docelowe powtórnej kompilacji nie ma zadań, powoduje uruchomienie czyszczenia miejsca docelowego przed jego kompilacją.

2. Dodaj tę `DefaultTargets` atrybutu do otwarcia `Project` elementu:

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     To ustawienie docelowej kompilacji jako domyślnego obiektu docelowego.

Plik projektu minimalnego powinien teraz przypominać następujący kod:

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Clean" >
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
</Project>
```

## <a name="test-the-build-targets"></a>Testowanie obiektów docelowych kompilacji
 Możesz skorzystać z nowych celów kompilacji do badania tych funkcji w pliku projektu:

- Kompilowanie domyślnej kompilacji.

- Ustawianie nazwy aplikacji, w tym celu w wierszu polecenia.

- Usuwanie aplikacji przed kompilacją innej aplikacji.

- Usuwanie aplikacji bez kompilacji innej aplikacji.

#### <a name="to-test-the-build-targets"></a>Aby przetestować obiekty docelowe kompilacji

1. W wierszu polecenia wpisz **msbuild helloworld.csproj - p: AssemblyName = Greetings**.

     Ponieważ nie użyto **-t** do jawnego ustawienia celu, MSBuild uruchamia domyślny element docelowy kompilacji. **-P** przełączanie przesłania `AssemblyName` właściwość i nadaje jej nową wartość `Greetings`. Powoduje to, że nową aplikację, *Greetings.exe*, zostały utworzone w *\Bin\\*  folderu.

2. Aby sprawdzić, czy *\Bin\\*  folder zawiera zarówno *MSBuildSample* aplikacji, a nowe *Greetings* aplikacji, należy wpisać **katalog Bin** .

3. Przetestuj aplikację Greetings wpisując **Bin\Greetings**.

     **Witaj, świecie!** powinien zostać wyświetlony komunikat.

4. Usuń aplikację MSBuildSample wpisując **msbuild helloworld.csproj -t: wyczyść**.

     To uruchamia zadanie czysty, aby usunąć aplikację, która ma domyślne `AssemblyName` wartość właściwości `MSBuildSample`.

5. Usuń aplikację Greetings wpisując **msbuild helloworld.csproj -t: czyszczenie - p: AssemblyName = Greetings**.

     To uruchamia zadanie czysty, aby usunąć aplikację, która ma danego **AssemblyName** wartość właściwości `Greetings`.

6. Aby sprawdzić, czy *\Bin\\*  folderu jest pusta, typem teraz **katalog Bin**.

7. Typ **msbuild**.

     Mimo że nie określono pliku projektu, MSBuild tworzy *helloworld.csproj* pliku, ponieważ istnieje tylko jeden plik projektu w bieżącym folderze. Powoduje to, że *MSBuildSample* aplikacji, które zostały utworzone w *\Bin\\*  folderu.

     Aby sprawdzić, czy *\Bin\\*  folder zawiera *MSBuildSample* aplikacji, należy wpisać **katalog Bin**.

## <a name="build-incrementally"></a>Kompilacja przyrostowa
 Możesz przekazać MSBuild kompilować obiekt docelowy tylko wtedy, gdy zostały zmienione pliki źródłowe lub pliki docelowe, które zależy obiekt docelowego. Program MSBuild używa sygnatura czasowa pliku, aby ustalić, czy został zmieniony.

#### <a name="to-build-incrementally"></a>Aby kompilować przyrostowo

1. W pliku projektu należy dodać te atrybuty do otwarcia docelowej kompilacji:

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     Określa, że cel kompilacji zależy od plików wejściowych, które są określone w `Compile` grupy elementów, a celem danych wyjściowych jest plik aplikacji.

     Wynikowa kompilacja docelowa powinna przypominać następujący kod:

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. Przetestuj kompilację docelową wpisując **msbuild - v: d** w wierszu polecenia.

     Należy pamiętać, że *helloworld.csproj* jest domyślnym plikiem projektu, a tej kompilacji domyślnego obiektu docelowego.

     **- V: d** przełącznik określa pełny opis procesu kompilacji.

     Powinny być wyświetlane następujące wiersze:

     **Pomijanie elementu docelowego "Kompilacja", ponieważ wszystkie pliki wyjściowe są aktualne w odniesieniu do plików wejściowych.**

     **Pliki wejściowe: HelloWorld.cs**

     **Pliki wyjściowe: BinMSBuildSample.exe**

     Program MSBuild pomija element docelowy kompilacji, ponieważ żaden z plików źródłowych zmieniły się od czasu ostatniej kompilacji aplikacji.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis
 Poniższy przykład pokazuje plik projektu, który kompiluje [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji i rejestruje wiadomość, która zawiera nazwę pliku wyjściowego.

### <a name="code"></a>Kod

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files of type CSFile -->
        <CSC
            Sources = "@(CSFile)"
            OutputAssembly = "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis
 Poniższy przykład pokazuje plik projektu, który kompiluje [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] aplikacji i rejestruje wiadomość, która zawiera nazwę pliku wyjściowego.

### <a name="code"></a>Kod

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldVB</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <VBFile Include = "consolehwvb1.vb"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual Basic compilation using input files of type VBFile -->
        <VBC
            Sources = "@(VBFile)"
            OutputAssembly= "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the VBC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </VBC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="whats-next"></a>Co dalej?
 Program Visual Studio automatycznie może wykonać większość zadań, która jest wyświetlana w tym przewodniku. Aby dowiedzieć się, jak używać programu Visual Studio do tworzenia, edytowania, kompilowania i testowania plików projektowych programu MSBuild, zobacz [instruktażu: Użyj programu MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="see-also"></a>Zobacz także
- [Przegląd MSBuild](../msbuild/msbuild.md)
- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)