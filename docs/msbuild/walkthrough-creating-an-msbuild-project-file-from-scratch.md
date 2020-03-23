---
title: 'Przewodnik: Tworzenie pliku projektu MSBuild od podstaw | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe9f052c10f31c4db0f8bf09f273be5814ff732
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263139"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>Instruktaż: Tworzenie pliku projektu MSBuild od podstaw

Języki programowania, które są przeznaczone dla programu .NET Framework używają plików projektu MSBuild do opisywania i kontrolowania procesu kompilacji aplikacji. Podczas tworzenia pliku projektu MSBuild za pomocą programu Visual Studio, odpowiedni kod XML jest automatycznie dodawany do pliku. Jednak może okazać się przydatne, aby zrozumieć, jak XML jest zorganizowany i jak można go zmienić, aby kontrolować kompilacji.

 Aby uzyskać informacje dotyczące tworzenia pliku projektu dla projektu języka C++, zobacz [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 W tym przewodniku pokazano, jak utworzyć podstawowy plik projektu przyrostowo, używając tylko edytora tekstu. Przewodnik postępuje poniżej następujące kroki:

1. Utwórz minimalny plik źródłowy aplikacji.

2. Utwórz minimalny plik projektu MSBuild.

3. Rozszerz zmienną środowiskową PATH, aby uwzględnić MSBuild.

4. Tworzenie aplikacji przy użyciu pliku projektu.

5. Dodaj właściwości, aby kontrolować kompilację.

6. Kontroluj kompilację, zmieniając wartości właściwości.

7. Dodaj obiekty docelowe do kompilacji.

8. Kontroluj kompilację, określając obiekty docelowe.

9. Tworzenie przyrostowo.

W tym przewodniku pokazano, jak utworzyć projekt w wierszu polecenia i zbadać wyniki. Aby uzyskać więcej informacji na temat msbuild i jak uruchomić MSBuild w wierszu polecenia, zobacz [Instruktaż: Użyj MSBuild](../msbuild/walkthrough-using-msbuild.md).

Aby ukończyć instruktaż, musisz mieć zainstalowany program .NET Framework (wersja 2.0, 3.5, 4.0, 4.5 lub nowszy), ponieważ zawiera msbuild i kompilator Visual C#, które są wymagane dla instruktażu.

## <a name="create-a-minimal-application"></a>Tworzenie minimalnej aplikacji

 W tej sekcji pokazano, jak utworzyć minimalny plik źródłowy aplikacji Języka C# przy użyciu edytora tekstu.

1. W wierszu polecenia przejdź do folderu, w którym chcesz utworzyć aplikację, na przykład *\Moje\\ dokumenty* lub *\Pulpit\\*.

2. Wpisz **md HelloWorld,** aby utworzyć podfolder o nazwie *\\\HelloWorld*.

3. Wpisz **cd HelloWorld,** aby zmienić na nowy folder.

4. Uruchom Notatnik lub inny edytor tekstu, a następnie wpisz następujący kod.

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

5. Zapisz ten plik kodu źródłowego i nadaj jego nazwę *Helloworld.cs*.

6. Skompiluj aplikację, wpisując **csc helloworld.cs** w wierszu polecenia.

7. Przetestuj aplikację, wpisując **helloworld** w wierszu polecenia.

     **Cześć, świat!** komunikat powinien być wyświetlany.

8. Usuń aplikację, wpisując **del helloworld.exe** w wierszu polecenia.

## <a name="create-a-minimal-msbuild-project-file"></a>Tworzenie minimalnego pliku projektu MSBuild

 Teraz, gdy masz minimalny plik źródłowy aplikacji, można utworzyć minimalny plik projektu do tworzenia aplikacji. Ten plik projektu zawiera następujące elementy:

- Wymagany węzeł `Project` główny.

- Węzeł `ItemGroup` zawierający elementy elementu.

- Element elementu, który odwołuje się do pliku źródłowego aplikacji.

- Węzeł `Target` zawierający zadania, które są wymagane do utworzenia aplikacji.

- Element `Task` do uruchomienia kompilatora języka Visual C# do tworzenia aplikacji.

### <a name="to-create-a-minimal-msbuild-project-file"></a>Aby utworzyć minimalny plik projektu MSBuild

1. W edytorze tekstu zastąp istniejący tekst za pomocą tych dwóch wierszy:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Wstaw `ItemGroup` ten węzeł jako `Project` element podrzędny węzła:

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Należy zauważyć, że to `ItemGroup` już zawiera element elementu.

3. Dodaj `Target` węzeł jako element podrzędny węzła. `Project` Nazwij `Build`węzeł .

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Wstaw ten element zadania jako `Target` element podrzędny węzła:

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. Zapisz ten plik projektu i nazwij go *Helloworld.csproj*.

Minimalny plik projektu powinien przypominać następujący kod:

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

Zadania w celu kompilacji są wykonywane sekwencyjnie. W takim przypadku zadanie kompilatora `Csc` języka Visual C# jest jedynym zadaniem. Oczekuje listy plików źródłowych do skompilowania, a to `Compile` jest podane przez wartość elementu. Element `Compile` odwołuje się tylko do jednego pliku źródłowego, *Helloworld.cs*.

> [!NOTE]
> W elemencie można użyć symbolu wieloznacznego gwiazdki (\*) w celu odwoływania się do wszystkich plików, które mają rozszerzenie nazwy pliku *cs,* w następujący sposób:
>
> ```xml
> <Compile Include="*.cs" />
> ```

## <a name="extend-the-path-to-include-msbuild"></a>Rozszerzanie ścieżki w celu uwzględnienia msbuild

Przed dostępem do usługi MSBuild należy rozszerzyć zmienną środowiskową PATH, aby uwzględnić folder .NET Framework.

Począwszy od programu Visual Studio 2013, program *MSBuild.exe* można znaleźć w folderze MSBuild (*%ProgramFiles%\MSBuild* w 32-bitowym systemie operacyjnym lub w *%ProgramFiles(x86)%\MSBuild* w 64-bitowym systemie operacyjnym).

W wierszu polecenia wpisz **POLECENIE PATH=%PATH%;%ProgramFiles%\MSBuild** lub **ustaw PATH=%PATH%;%ProgramFiles(x86)%\MSBuild**.

Alternatywnie, jeśli masz zainstalowany program Visual Studio, można użyć **wiersza polecenia dewelopera dla programu Visual Studio**, który ma ścieżkę, która zawiera folder *MSBuild.*

## <a name="build-the-application"></a>Kompilowanie aplikacji

 Teraz, aby utworzyć aplikację, użyj pliku projektu, który właśnie został utworzony.

1. W wierszu polecenia wpisz **msbuild helloworld.csproj -t:Build**.

     Spowoduje to utworzenie obiektu docelowego kompilacji pliku projektu Helloworld, wywołując kompilator visual c#, aby utworzyć aplikację Helloworld.

2. Przetestuj aplikację, wpisując **helloworld**.

     **Cześć, świat!** komunikat powinien być wyświetlany.

> [!NOTE]
> Można zobaczyć więcej szczegółów na temat kompilacji, zwiększając poziom szczegółowości. Aby ustawić poziom szczegółowości na "szczegółowe", wpisz to polecenie w wierszu polecenia:
>
> **msbuild helloworld.csproj -t:Build -verbosity:detailed**

## <a name="add-build-properties"></a>Dodawanie właściwości kompilacji

 Można dodać właściwości kompilacji do pliku projektu, aby dalej kontrolować kompilację. Teraz dodaj te właściwości:

- Właściwość, `AssemblyName` aby określić nazwę aplikacji.

- Właściwość `OutputPath` określająca folder zawierający aplikację.

### <a name="to-add-build-properties"></a>Aby dodać właściwości kompilacji

1. Usuń istniejącą aplikację, wpisując **plik del helloworld.exe** w wierszu polecenia.

2. W pliku projektu wstaw ten `PropertyGroup` element `Project` tuż po elemencie otwierającym:

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Dodaj to zadanie do obiektu docelowego kompilacji, `Csc` tuż przed zadaniem:

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     Zadanie `MakeDir` tworzy folder, który jest `OutputPath` nazwany przez właściwość, pod warunkiem, że żaden folder o tej nazwie obecnie istnieje.

4. Dodaj `OutputAssembly` ten atrybut `Csc` do zadania:

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     Nakazuje kompilator visual C# do tworzenia zestawu, `AssemblyName` który jest nazwany przez właściwość i `OutputPath` umieścić go w folderze, który jest nazwany przez właściwość.

5. Zapisz zmiany.

Plik projektu powinien teraz przypominać następujący kod:

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
> Zaleca się dodanie ogranicznika\\ścieżki odwrotnej ( ) na końcu nazwy folderu `OutputPath` po określeniu go `OutputAssembly` w elemencie, zamiast dodawać go w atrybucie `Csc` zadania. Zatem
>
> `<OutputPath>Bin\</OutputPath>`
>
> `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`
>
> jest lepszy niż
>
> `<OutputPath>Bin</OutputPath>`
>
> `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>Testowanie właściwości kompilacji

 Teraz można utworzyć aplikację przy użyciu pliku projektu, w którym użyto właściwości kompilacji, aby określić folder wyjściowy i nazwę aplikacji.

1. W wierszu polecenia wpisz **msbuild helloworld.csproj -t:Build**.

     Spowoduje to utworzenie folderu *\Bin,\\ * a następnie wywołanie kompilatora języka Visual C# w celu utworzenia aplikacji *MSBuildSample* i umieszcza ją w folderze *\Bin.\\ *

2. Aby sprawdzić, czy folder *\\ \Bin* został utworzony i czy zawiera aplikację *MSBuildSample,* wpisz **dir Bin**.

3. Przetestuj aplikację, wpisując **plik Bin\MSBuildSample**.

     **Cześć, świat!** komunikat powinien być wyświetlany.

## <a name="add-build-targets"></a>Dodawanie obiektów docelowych kompilacji

 Następnie dodaj dwa kolejne obiekty docelowe do pliku projektu w następujący sposób:

- Czysty obiekt docelowy, który usuwa stare pliki.

- A Odbuduj `DependsOnTargets` obiekt docelowy, który używa atrybutu, aby wymusić clean zadanie do uruchomienia przed build zadania.

Teraz, gdy masz wiele obiektów docelowych, można ustawić miejsce docelowe kompilacji jako domyślny obiekt docelowy.

### <a name="to-add-build-targets"></a>Aby dodać obiekty docelowe kompilacji

1. W pliku projektu dodaj te dwa obiekty docelowe tuż po docelowych kompilacji:

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     Czysty obiekt docelowy wywołuje zadanie Delete, aby usunąć aplikację. Obiekt docelowy odbudować nie jest uruchamiany, dopóki nie uruchomią się zarówno celu Czyste, jak i docelowe kompilacji. Mimo że miejsce docelowe odbudować nie ma żadnych zadań, powoduje, że clean cel do uruchomienia przed build obiektu docelowego.

2. Dodaj `DefaultTargets` ten atrybut do `Project` elementu otwierającego:

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     Spowoduje to ustawienie obiektu docelowego kompilacji jako domyślnego obiektu docelowego.

Plik projektu powinien teraz przypominać następujący kod:

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

## <a name="test-the-build-targets"></a>Testowanie celów kompilacji

 Można skorzystać z nowych obiektów docelowych kompilacji, aby przetestować te funkcje pliku projektu:

- Tworzenie kompilacji domyślnej.

- Ustawianie nazwy aplikacji w wierszu polecenia.

- Usuwanie aplikacji przed inną aplikacją jest skonsułkowanie.

- Usuwanie aplikacji bez tworzenia innej aplikacji.

### <a name="to-test-the-build-targets"></a>Aby przetestować cele kompilacji

1. W wierszu polecenia wpisz **msbuild helloworld.csproj -p:AssemblyName=Greetings**.

     Ponieważ przełącznik **-t** nie został jawnie ustawiony, msBuild uruchamia domyślny obiekt docelowy kompilacji. Przełącznik **-p** zastępuje `AssemblyName` właściwość i nadaje jej `Greetings`nową wartość, . Powoduje to utworzenie nowej aplikacji *Greetings.exe*w folderze *\Bin.\\ *

2. Aby sprawdzić, czy folder *\\ \Bin* zawiera zarówno aplikację *MSBuildSample, jak* i nową aplikację *Pozdrowienia,* wpisz **dir Bin**.

3. Przetestuj aplikację Pozdrowienia, wpisując **plik Bin\Pozdrowienia**.

     **Cześć, świat!** komunikat powinien być wyświetlany.

4. Usuń aplikację MSBuildSample, wpisując **msbuild helloworld.csproj -t:clean**.

     Spowoduje to uruchomieniu zadania Clean, aby `AssemblyName` usunąć aplikację `MSBuildSample`o domyślnej wartości właściwości , .

5. Usuń aplikację Pozdrowienia, wpisując **msbuild helloworld.csproj -t:clean -p:AssemblyName=Greetings**.

     Spowoduje to uruchomieniu zadania Clean, aby usunąć aplikację, która `Greetings`ma podaną wartość właściwości **AssemblyName,** .

6. Aby sprawdzić, czy folder *\Bin\\ * jest teraz pusty, wpisz **dir Bin**.

7. Wpisz **msbuild**.

     Chociaż plik projektu nie jest określony, MSBuild buduje plik *helloworld.csproj,* ponieważ w bieżącym folderze znajduje się tylko jeden plik projektu. Powoduje to, że aplikacja *MSBuildSample* ma zostać utworzona w folderze *\Bin.\\ *

     Aby sprawdzić, czy folder *\\ \Bin* zawiera aplikację *MSBuildSample,* wpisz **dir Bin**.

## <a name="build-incrementally"></a>Tworzenie przyrostowo

 Można powiedzieć MSBuild do tworzenia obiektu docelowego tylko wtedy, gdy pliki źródłowe lub docelowe, które zależy od obiektu docelowego zostały zmienione. MSBuild używa sygnatury czasowej pliku, aby ustalić, czy został zmieniony.

### <a name="to-build-incrementally"></a>Aby budować przyrostowo

1. W pliku projektu dodaj te atrybuty do otwierającego obiektu docelowego kompilacji:

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     Określa to, że miejsce docelowe kompilacji zależy `Compile` od plików wejściowych, które są określone w grupie elementów i że miejsce docelowe danych wyjściowych jest plikiem aplikacji.

     Wynikowy obiekt docelowy kompilacji powinien przypominać następujący kod:

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. Przetestuj obiekt docelowy kompilacji, wpisując **msbuild -v:d** w wierszu polecenia.

     Należy pamiętać, że *helloworld.csproj* jest domyślnym plikiem projektu, a kompilacja jest domyślnym celem.

     Przełącznik **-v:d** określa pełny opis procesu kompilacji.

     Linie te powinny być wyświetlane:

     **Pomijanie obiektu docelowego "Kompilacja", ponieważ wszystkie pliki wyjściowe są aktualne w odniesieniu do plików wejściowych.**

     **Pliki wejściowe: HelloWorld.cs**

     **Pliki wyjściowe: BinMSBuildSample.exe**

     MSBuild pomija miejsce docelowe kompilacji, ponieważ żaden z plików źródłowych nie uległ zmianie od czasu ostatniego utworzenia aplikacji.

## <a name="c-example"></a>Przykład języka C#

Poniższy przykład przedstawia plik projektu, który kompiluje aplikację Języka C# i rejestruje komunikat zawierający nazwę pliku wyjściowego.

### <a name="code"></a>Code

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

## <a name="visual-basic-example"></a>Przykład języka Visual Basic

W poniższym przykładzie przedstawiono plik projektu, który kompiluje aplikację języka Visual Basic i rejestruje komunikat zawierający nazwę pliku wyjściowego.

### <a name="code"></a>Code

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

 Visual Studio można automatycznie wykonać wiele pracy, która jest pokazana w tym instruktażu. Aby dowiedzieć się, jak używać programu Visual Studio do tworzenia, edytowania, tworzenia i testowania plików projektu MSBuild, zobacz [Instruktaż: Używanie programu MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie usługi MSBuild](../msbuild/msbuild.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
