---
title: 'Przewodnik: Tworzenie pliku projektu MSBuild od podstaw | Microsoft Docs'
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
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263139"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>Przewodnik: Tworzenie pliku projektu MSBuild od podstaw

Języki programowania, które są przeznaczone dla .NET Framework używają plików projektu MSBuild do opisywania i kontrolowania procesu kompilacji aplikacji. W przypadku tworzenia pliku projektu programu MSBuild przy użyciu programu Visual Studio odpowiedni kod XML zostanie automatycznie dodany do pliku. Warto jednak zapoznać się z tematem sposobu organizowania kodu XML i sposobu jego zmiany w celu sterowania kompilacją.

 Aby uzyskać informacje na temat tworzenia pliku projektu dla C++ projektu, zobacz [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 W tym instruktażu przedstawiono sposób przyrostowego tworzenia podstawowego pliku projektu przy użyciu tylko edytora tekstu. W tym przewodniku opisano następujące kroki:

1. Utwórz minimalny plik źródłowy aplikacji.

2. Utwórz minimalny plik projektu programu MSBuild.

3. Zwiększ wartość zmiennej środowiskowej PATH, aby uwzględnić MSBuild.

4. Skompiluj aplikację przy użyciu pliku projektu.

5. Dodaj właściwości, aby kontrolować kompilację.

6. Kontroluj kompilację przez zmianę wartości właściwości.

7. Dodaj cele do kompilacji.

8. Kontroluj kompilację, określając elementy docelowe.

9. Kompiluj przyrostowo.

W tym instruktażu pokazano, jak skompilować projekt w wierszu polecenia i przejrzeć wyniki. Aby uzyskać więcej informacji na temat programu MSBuild i sposobu uruchamiania programu MSBuild w wierszu polecenia, zobacz [Przewodnik: Korzystanie](../msbuild/walkthrough-using-msbuild.md)z programu MSBuild.

Aby ukończyć przewodnik, musisz mieć zainstalowaną .NET Framework (w wersji 2,0, 3,5, 4,0, 4,5 lub nowszej), ponieważ zawiera ona MSBuild i kompilator wizualny C# , które są wymagane dla tego przewodnika.

## <a name="create-a-minimal-application"></a>Tworzenie minimalnej aplikacji

 W tej sekcji pokazano, jak utworzyć minimalny C# plik źródłowy aplikacji przy użyciu edytora tekstów.

1. W wierszu polecenia przejdź do folderu, w którym chcesz utworzyć aplikację, na przykład *\Moje dokumenty\\* lub *\Desktop\\* .

2. Wpisz **MD HelloWorld** , aby utworzyć podfolder o nazwie *\HelloWorld\\* .

3. Wpisz **CD HelloWorld** , aby przejść do nowego folderu.

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

5. Zapisz ten plik kodu źródłowego i nadaj mu nazwę *HelloWorld.cs*.

6. Skompiluj aplikację, wpisując **HelloWorld.cs CSC** w wierszu polecenia.

7. Przetestuj aplikację, wpisując **HelloWorld** w wierszu polecenia.

     **Witaj, świecie!** powinien być wyświetlony komunikat.

8. Usuń aplikację, wpisując **del helloworld. exe** w wierszu polecenia.

## <a name="create-a-minimal-msbuild-project-file"></a>Utwórz minimalny plik projektu programu MSBuild

 Teraz, gdy masz minimalny plik źródłowy aplikacji, możesz utworzyć minimalny plik projektu do skompilowania aplikacji. Ten plik projektu zawiera następujące elementy:

- Wymagany węzeł główny `Project`.

- Węzeł `ItemGroup` zawierający elementy elementu.

- Element elementu, który odwołuje się do pliku źródłowego aplikacji.

- Węzeł `Target` zawierający zadania, które są wymagane do skompilowania aplikacji.

- Element `Task`, aby uruchomić kompilator wizualizacji C# w celu skompilowania aplikacji.

### <a name="to-create-a-minimal-msbuild-project-file"></a>Aby utworzyć minimalny plik projektu MSBuild

1. W edytorze tekstów Zastąp istniejący tekst, używając następujących dwóch wierszy:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Wstaw ten `ItemGroup` węzeł jako element podrzędny węzła `Project`:

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Zauważ, że ten `ItemGroup` już zawiera element Item.

3. Dodaj węzeł `Target` jako element podrzędny węzła `Project`. Nadaj nazwę węzłowi `Build`.

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Wstaw ten element zadania jako element podrzędny węzła `Target`:

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. Zapisz ten plik projektu i nazwij go *HelloWorld. csproj*.

Minimalny plik projektu powinien wyglądać podobnie do następującego:

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

Zadania w miejscu docelowym kompilacji są wykonywane sekwencyjnie. W takim przypadku zadanie `Csc` kompilatorem wizualnym C# jest jedynym zadaniem. Oczekuje ono listy plików źródłowych do skompilowania, a następnie jest określona przez wartość `Compile` elementu. Element `Compile` odwołuje się tylko do jednego pliku źródłowego, *HelloWorld.cs*.

> [!NOTE]
> W elemencie Item można użyć symbolu wieloznacznego gwiazdki (\*), aby odwołać się do wszystkich plików mających rozszerzenie nazwy pliku *. cs* w następujący sposób:
>
> ```xml
> <Compile Include="*.cs" />
> ```

## <a name="extend-the-path-to-include-msbuild"></a>Zwiększanie ścieżki w celu uwzględnienia programu MSBuild

Aby można było uzyskać dostęp do programu MSBuild, należy zwiększyć zmienną środowiskową PATH, aby uwzględnić folder .NET Framework.

Począwszy od Visual Studio 2013, można znaleźć program *MSBuild. exe* w folderze MSBuild ( *%ProgramFiles%\MSBuild* w 32-bitowym systemie operacyjnym lub w pliku *% ProgramFiles (x86)% \ MSBuild* w 64-bitowym systemie operacyjnym.

W wierszu polecenia wpisz **set path =% Path%;%PROGRAMFILES%\MSBuild** lub **Set PATH =% Path%;% ProgramFiles (x86)% \ MSBuild**.

Alternatywnie, jeśli masz zainstalowany program Visual Studio, możesz użyć **wiersz polecenia dla deweloperów dla programu Visual Studio**, który ma ścieżkę obejmującą folder programu *MSBuild* .

## <a name="build-the-application"></a>Kompilowanie aplikacji

 Teraz, aby skompilować aplikację, należy użyć pliku projektu, który właśnie został utworzony.

1. W wierszu polecenia wpisz **MSBuild HelloWorld. csproj-t:build**.

     Powoduje to kompilację docelowej kompilacji pliku projektu HelloWorld przez wywołanie kompilatora wizualnego C# w celu utworzenia aplikacji HelloWorld.

2. Przetestuj aplikację, wpisując polecenie **HelloWorld**.

     **Witaj, świecie!** powinien być wyświetlony komunikat.

> [!NOTE]
> Aby zobaczyć więcej szczegółów na temat kompilacji, zwiększ poziom szczegółowości. Aby ustawić poziom szczegółowości na "szczegółowy", wpisz następujące polecenie w wierszu polecenia:
>
> **MSBuild HelloWorld. csproj-t:Build-verbose: szczegóły**

## <a name="add-build-properties"></a>Dodawanie właściwości kompilacji

 Możesz dodać właściwości kompilacji do pliku projektu, aby w większym stopniu kontrolować kompilację. Teraz Dodaj następujące właściwości:

- Właściwość `AssemblyName`, aby określić nazwę aplikacji.

- Właściwość `OutputPath`, aby określić folder, w którym ma znajdować się aplikacja.

### <a name="to-add-build-properties"></a>Aby dodać właściwości kompilacji

1. Usuń istniejącą aplikację, wpisując **del helloworld. exe** w wierszu polecenia.

2. W pliku projektu, Wstaw ten element `PropertyGroup` tuż po otwierającym elemencie `Project`:

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Dodaj to zadanie do elementu docelowego kompilacji tuż przed zadaniem `Csc`:

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     Zadanie `MakeDir` tworzy folder, który jest nazwany przez właściwość `OutputPath`, pod warunkiem, że folder o tej nazwie nie istnieje.

4. Dodaj ten atrybut `OutputAssembly` do zadania `Csc`:

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     Powoduje C# to wygenerowanie zestawu, który jest nazwany przez właściwość `AssemblyName` i umieszczenie go w folderze o nazwie właściwości `OutputPath`.

5. Zapisz zmiany.

Plik projektu powinien teraz wyglądać podobnie do następującego kodu:

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
> Zalecamy dodanie ogranicznika ścieżki odwrotnej kreski ułamkowej (\\) na końcu nazwy folderu, gdy zostanie on określony w elemencie `OutputPath`, zamiast dodawać go w atrybucie `OutputAssembly` zadania `Csc`. Zatem
>
> `<OutputPath>Bin\</OutputPath>`
>
> `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`
>
> jest lepsza niż
>
> `<OutputPath>Bin</OutputPath>`
>
> `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>Testowanie właściwości kompilacji

 Teraz można skompilować aplikację przy użyciu pliku projektu, w którym użyto właściwości kompilacji do określenia folderu wyjściowego i nazwy aplikacji.

1. W wierszu polecenia wpisz **MSBuild HelloWorld. csproj-t:build**.

     Spowoduje to utworzenie folderu *\bin\\* , a następnie wywołanie kompilatora C# wizualizacji w celu utworzenia aplikacji *aplikację MSBuildSample* i umieszczenie go w folderze *\Bin\\* .

2. Aby sprawdzić, czy folder *\bin\\* został utworzony, i czy zawiera aplikację *aplikację MSBuildSample* , wpisz **dir bin**.

3. Przetestuj aplikację, wpisując **Bin\MSBuildSample**.

     **Witaj, świecie!** powinien być wyświetlony komunikat.

## <a name="add-build-targets"></a>Dodaj cele kompilacji

 Następnie Dodaj dwa elementy docelowe do pliku projektu w następujący sposób:

- Czysty element docelowy, który usuwa stare pliki.

- Obiekt docelowy odbudowywania, który używa atrybutu `DependsOnTargets`, aby wymusić uruchomienie czystego zadania przed zadaniem kompilacji.

Teraz, gdy masz wiele obiektów docelowych, możesz ustawić cel kompilacji jako domyślny element docelowy.

### <a name="to-add-build-targets"></a>Aby dodać cele kompilacji

1. W pliku projektu, Dodaj te dwa obiekty docelowe tuż po elemencie docelowym kompilacji:

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     Czysty obiekt docelowy wywołuje zadanie usuwania, aby usunąć aplikację. Cel ponownego kompilowania nie jest uruchamiany, dopóki nie zostanie uruchomiony zarówno czysty element docelowy, jak i element docelowy kompilacji. Mimo że miejsce docelowe odbudowywania nie ma żadnych zadań, powoduje, że jest uruchamiany czysty element docelowy przed elementem docelowym kompilacji.

2. Dodaj ten atrybut `DefaultTargets` do otwierającego elementu `Project`:

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     Ustawia cel kompilacji jako domyślny element docelowy.

Plik projektu powinien teraz wyglądać podobnie do następującego kodu:

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

 W celu przetestowania tych funkcji w pliku projektu można wykonać nowe cele kompilacji:

- Kompilowanie kompilacji domyślnej.

- Ustawianie nazwy aplikacji w wierszu polecenia.

- Usuwanie aplikacji przed skompilowaniem innej aplikacji.

- Usuwanie aplikacji bez tworzenia innej aplikacji.

### <a name="to-test-the-build-targets"></a>Aby przetestować cele kompilacji

1. W wierszu polecenia wpisz **MSBuild HelloWorld. csproj-p:AssemblyName = Greetings**.

     Ze względu na to, że przełącznik **-t** nie został jawnie ustawiony dla obiektu docelowego, MSBuild uruchamia domyślny element docelowy kompilacji. Przełącznik **-p** zastępuje właściwość `AssemblyName` i nadaje jej nową wartość, `Greetings`. Powoduje to utworzenie nowej aplikacji, *Greetings. exe*w folderze *\Bin\\* .

2. Aby sprawdzić, czy folder *\bin\\* zawiera aplikację *aplikację MSBuildSample* oraz nowe aplikacje *Greetings* , wpisz **dir bin**.

3. Przetestuj aplikację Greetings, wpisując **Bin\Greetings**.

     **Witaj, świecie!** powinien być wyświetlony komunikat.

4. Usuń aplikację aplikację MSBuildSample, wpisując **MSBuild HelloWorld. csproj-t:Clean**.

     Spowoduje to uruchomienie czystego zadania w celu usunięcia aplikacji, która ma domyślną `AssemblyName` wartość właściwości, `MSBuildSample`.

5. Usuń aplikację Greetings, wpisując **MSBuild HelloWorld. csproj-t:Clean-p:AssemblyName = Greetings**.

     Spowoduje to uruchomienie czystego zadania w celu usunięcia aplikacji, która ma daną wartość właściwości **AssemblyName** , `Greetings`.

6. Aby sprawdzić, czy folder *\bin\\* jest teraz pusty, wpisz polecenie **dir bin**.

7. Wpisz **MSBuild**.

     Chociaż nie określono pliku projektu, MSBuild kompiluje plik *HelloWorld. csproj* , ponieważ w bieżącym folderze istnieje tylko jeden plik projektu. Powoduje to utworzenie aplikacji *aplikację MSBuildSample* w folderze *\Bin\\* .

     Aby sprawdzić, czy folder *\bin\\* zawiera aplikację *aplikację MSBuildSample* , wpisz **dir bin**.

## <a name="build-incrementally"></a>Kompilacja przyrostowa

 Można powiedzieć, że program MSBuild ma tworzyć obiekty docelowe tylko wtedy, gdy pliki źródłowe lub docelowe, od których zależy element docelowy, zostały zmienione. MSBuild używa sygnatury czasowej pliku, aby określić, czy został zmieniony.

### <a name="to-build-incrementally"></a>Aby kompilować przyrostowo

1. W pliku projektu Dodaj te atrybuty do otwierającego elementu docelowego kompilacji:

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     Oznacza to, że element docelowy kompilacji zależy od plików wejściowych, które są określone w grupie elementów `Compile`, i że docelowy wynik to plik aplikacji.

     Utworzony element docelowy kompilacji powinien wyglądać podobnie do następującego kodu:

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. Przetestuj cel kompilacji, wpisując **MSBuild-v:d** w wierszu polecenia.

     Należy pamiętać, że *HelloWorld. csproj* jest domyślnym plikiem projektu i że kompilacja jest domyślnym obiektem docelowym.

     Przełącznik **-v:d** określa pełny opis procesu kompilacji.

     Powinny być wyświetlane następujące wiersze:

     **Pomijanie elementu docelowego "Kompilacja", ponieważ wszystkie pliki wyjściowe są aktualne w odniesieniu do plików wejściowych.**

     **Pliki wejściowe: HelloWorld.cs**

     **Pliki wyjściowe: BinMSBuildSample. exe**

     Program MSBuild pomija miejsce docelowe kompilacji, ponieważ żadne pliki źródłowe nie uległy zmianie od czasu ostatniego skompilowania aplikacji.

## <a name="c-example"></a>C#przyklad

W poniższym przykładzie przedstawiono plik projektu, który kompiluje C# aplikację i rejestruje komunikat zawierający nazwę pliku wyjściowego.

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

## <a name="visual-basic-example"></a>Przykład Visual Basic

W poniższym przykładzie przedstawiono plik projektu, który kompiluje Visual Basic aplikację i rejestruje komunikat zawierający nazwę pliku wyjściowego.

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

 Program Visual Studio może automatycznie wykonywać większość pracy, która jest wyświetlana w tym instruktażu. Aby dowiedzieć się, jak używać programu Visual Studio do tworzenia, edytowania, kompilowania i testowania plików projektów programu MSBuild, zobacz [Przewodnik: korzystanie z MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie programu MSBuild](../msbuild/msbuild.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
