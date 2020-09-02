---
title: 'Przewodnik: Tworzenie pliku projektu MSBuild od podstaw | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eb49e6c51c1e51d002683099797d940cb2d24556
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682364"
---
# <a name="walkthrough-creating-an-msbuild-project-file-from-scratch"></a>Wskazówki: tworzenie pliku projektu MSBuild od zera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Języki programowania, które są przeznaczone dla .NET Framework używają plików projektu MSBuild do opisywania i kontrolowania procesu kompilacji aplikacji. W przypadku tworzenia pliku projektu programu MSBuild przy użyciu programu Visual Studio odpowiedni kod XML zostanie automatycznie dodany do pliku. Warto jednak zapoznać się z tematem sposobu organizowania kodu XML i sposobu jego zmiany w celu sterowania kompilacją.  
  
 Aby uzyskać informacje na temat tworzenia pliku projektu dla projektu języka C++, zobacz [MSBuild (Visual C++)](https://msdn.microsoft.com/library/7a1be7ff-0312-4669-adf2-5f5bf507d560).  
  
 W tym instruktażu przedstawiono sposób przyrostowego tworzenia podstawowego pliku projektu przy użyciu tylko edytora tekstu. W tym przewodniku opisano następujące kroki:  
  
- Utwórz minimalny plik źródłowy aplikacji.  
  
- Utwórz minimalny plik projektu programu MSBuild.  
  
- Zwiększ wartość zmiennej środowiskowej PATH, aby uwzględnić MSBuild.  
  
- Skompiluj aplikację przy użyciu pliku projektu.  
  
- Dodaj właściwości, aby kontrolować kompilację.  
  
- Kontroluj kompilację przez zmianę wartości właściwości.  
  
- Dodaj cele do kompilacji.  
  
- Kontroluj kompilację, określając elementy docelowe.  
  
- Kompiluj przyrostowo.  
  
  W tym instruktażu pokazano, jak skompilować projekt w wierszu polecenia i przejrzeć wyniki. Aby uzyskać więcej informacji na temat programu MSBuild i sposobu uruchamiania programu MSBuild w wierszu polecenia, zobacz [Przewodnik: używanie programu MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
  Aby ukończyć przewodnik, musisz mieć zainstalowaną .NET Framework (w wersji 2,0, 3,5, 4,0 lub 4,5), ponieważ zawiera on MSBuild i kompilator Visual C#, które są wymagane dla tego przewodnika.  
  
## <a name="creating-a-minimal-application"></a>Tworzenie minimalnej aplikacji  
 W tej sekcji pokazano, jak utworzyć minimalny plik źródłowy aplikacji Visual C# przy użyciu edytora tekstu.  
  
#### <a name="to-create-the-minimal-application"></a>Aby utworzyć minimalną aplikację  
  
1. W wierszu polecenia przejdź do folderu, w którym chcesz utworzyć aplikację, na przykład \Moje Documents \ lub \Desktop \\ .  
  
2. Wpisz **MD HelloWorld** , aby utworzyć podfolder o nazwie \HelloWorld \\ .  
  
3. Wpisz **CD HelloWorld** , aby przejść do nowego folderu.  
  
4. Uruchom Notatnik lub inny edytor tekstu, a następnie wpisz następujący kod.  
  
    ```  
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
  
5. Zapisz ten plik kodu źródłowego i nadaj mu nazwę Helloworld.cs.  
  
6. Skompiluj aplikację, wpisując **HelloWorld.cs CSC** w wierszu polecenia.  
  
7. Przetestuj aplikację, wpisując **HelloWorld** w wierszu polecenia.  
  
     **Witaj, świecie!** powinien być wyświetlony komunikat.  
  
8. Usuń aplikację, wpisując **del helloworld.exe** w wierszu polecenia.  
  
## <a name="creating-a-minimal-msbuild-project-file"></a>Tworzenie minimalnego pliku projektu programu MSBuild  
 Teraz, gdy masz minimalny plik źródłowy aplikacji, możesz utworzyć minimalny plik projektu do skompilowania aplikacji. Ten plik projektu zawiera następujące elementy:  
  
- Wymagany węzeł główny `Project` .  
  
- `ItemGroup`Węzeł, który zawiera elementy elementu.  
  
- Element elementu, który odwołuje się do pliku źródłowego aplikacji.  
  
- `Target`Węzeł zawierający zadania, które są wymagane do skompilowania aplikacji.  
  
- `Task`Element, aby uruchomić kompilator Visual C# w celu skompilowania aplikacji.  
  
#### <a name="to-create-a-minimal-msbuild-project-file"></a>Aby utworzyć minimalny plik projektu MSBuild  
  
1. W edytorze tekstów Zastąp istniejący tekst, używając następujących dwóch wierszy:  
  
   ```  
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   </Project>  
   ```  
  
2. Wstaw ten `ItemGroup` węzeł jako element podrzędny `Project` węzła:  
  
   ```  
   <ItemGroup>  
     <Compile Include="helloworld.cs" />  
   </ItemGroup>  
   ```  
  
    Zwróć uwagę, że `ItemGroup` zawiera już element Item.  
  
3. Dodaj `Target` węzeł jako element podrzędny `Project` węzła. Nadaj nazwę węzłowi `Build` .  
  
   ```  
   <Target Name="Build">  
   </Target>  
   ```  
  
4. Wstaw ten element zadania jako element podrzędny `Target` węzła:  
  
   ```  
   <Csc Sources="@(Compile)"/>  
   ```  
  
5. Zapisz ten plik projektu i nazwij go HelloWorld. csproj.  
  
   Minimalny plik projektu powinien wyglądać podobnie do następującego:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <Csc Sources="@(Compile)"/>    
  </Target>  
</Project>  
```  
  
 Zadania w miejscu docelowym kompilacji są wykonywane sekwencyjnie. W takim przypadku zadanie kompilatora Visual C# `Csc` jest jedynym zadaniem. Oczekuje ono listy plików źródłowych do skompilowania, a następnie jest określona przez wartość `Compile` elementu. `Compile`Element odwołuje się tylko do jednego pliku źródłowego, HelloWorld.cs.  
  
> [!NOTE]
> W elemencie Item można użyć symbolu wieloznacznego gwiazdki (*), aby odwołać się do wszystkich plików mających rozszerzenie nazwy pliku. cs w następujący sposób:  
>   
> `<Compile Include="*.cs" />`  
>   
> Nie zaleca się jednak używania symboli wieloznacznych, ponieważ sprawia, że debugowanie i selektywne ukierunkowanie są trudniejsze, jeśli pliki źródłowe są dodawane lub usuwane.  
  
## <a name="extending-the-path-to-include-msbuild"></a>Rozszerzanie ścieżki w celu uwzględnienia programu MSBuild  
 Aby można było uzyskać dostęp do programu MSBuild, należy zwiększyć zmienną środowiskową PATH, aby uwzględnić folder .NET Framework.  
  
#### <a name="to-add-msbuild-to-your-path"></a>Aby dodać MSBuild do ścieżki  
  
- Począwszy od Visual Studio 2013 można znaleźć MSBuild.exe w folderze MSBuild ( `%ProgramFiles%\MSBuild` w 32-bitowym systemie operacyjnym lub `%ProgramFiles(x86)%\MSBuild` w 64-bitowym systemie operacyjnym).  
  
     W wierszu polecenia wpisz **set path =% Path%;%PROGRAMFILES%\MSBuild** lub **Set PATH =% Path%;% ProgramFiles (x86)% \ MSBuild**.  
  
     Alternatywnie, jeśli masz zainstalowany program Visual Studio, możesz użyć **wiersza polecenia programu Visual Studio**, który ma ścieżkę obejmującą folder programu MSBuild.  
  
## <a name="using-the-project-file-to-build-the-application"></a>Używanie pliku projektu do kompilowania aplikacji  
 Teraz, aby skompilować aplikację, należy użyć pliku projektu, który właśnie został utworzony.  
  
#### <a name="to-build-the-application"></a>Aby skompilować aplikację  
  
1. W wierszu polecenia wpisz **MSBuild HelloWorld. csproj/t: build**.  
  
     Powoduje to kompilację docelowej kompilacji pliku projektu HelloWorld przez wywołanie kompilatora Visual C# w celu utworzenia aplikacji HelloWorld.  
  
2. Przetestuj aplikację, wpisując polecenie **HelloWorld**.  
  
     **Witaj, świecie!** powinien być wyświetlony komunikat.  
  
> [!NOTE]
> Aby zobaczyć więcej szczegółów na temat kompilacji, zwiększ poziom szczegółowości. Aby ustawić poziom szczegółowości na "szczegółowy", wpisz jedno z tych poleceń w wierszu polecenia:  
>   
> **MSBuild HelloWorld. csproj/t: build/verbosity.: Detailed**  
  
## <a name="adding-build-properties"></a>Dodawanie właściwości kompilacji  
 Możesz dodać właściwości kompilacji do pliku projektu, aby w większym stopniu kontrolować kompilację. Teraz Dodaj następujące właściwości:  
  
- `AssemblyName`Właściwość określająca nazwę aplikacji.  
  
- `OutputPath`Właściwość określająca folder, w którym ma znajdować się aplikacja.  
  
#### <a name="to-add-build-properties"></a>Aby dodać właściwości kompilacji  
  
1. Usuń istniejącą aplikację, wpisując **del helloworld.exe** w wierszu polecenia.  
  
2. W pliku projektu, Wstaw ten `PropertyGroup` element tuż po elemencie otwierającym `Project` :  
  
   ```  
   <PropertyGroup>  
     <AssemblyName>MSBuildSample</AssemblyName>  
     <OutputPath>Bin\</OutputPath>  
   </PropertyGroup>  
   ```  
  
3. Dodaj to zadanie do elementu docelowego kompilacji tuż przed `Csc` zadaniem:  
  
   ```  
   <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />  
   ```  
  
    `MakeDir`Zadanie tworzy folder, który jest nazwany przez `OutputPath` Właściwość, pod warunkiem, że folder o tej nazwie nie istnieje.  
  
4. Dodaj ten `OutputAssembly` atrybut do `Csc` zadania:  
  
   ```  
   <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
   ```  
  
    Powoduje to wygenerowanie przez kompilator języka Visual C# zestawu, który jest nazwany przez `AssemblyName` Właściwość i umieszczenie go w folderze, który jest nazwany przez `OutputPath` Właściwość.  
  
5. Zapisz zmiany.  
  
   Plik projektu powinien teraz wyglądać podobnie do następującego kodu:  
  
```  
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
> Zalecamy dodanie ogranicznika ścieżki odwróconej kreski ułamkowej ( \\ ) na końcu nazwy folderu, gdy zostanie on określony w `OutputPath` elemencie, zamiast dodawać go w `OutputAssembly` atrybucie `Csc` zadania. Zatem  
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
  
## <a name="testing-the-build-properties"></a>Testowanie właściwości kompilacji  
 Teraz można skompilować aplikację przy użyciu pliku projektu, w którym użyto właściwości kompilacji do określenia folderu wyjściowego i nazwy aplikacji.  
  
#### <a name="to-test-the-build-properties"></a>Aby przetestować właściwości kompilacji  
  
1. W wierszu polecenia wpisz **MSBuild HelloWorld. csproj/t: build**.  
  
     Spowoduje to utworzenie folderu \Bin\, a następnie wywołanie kompilatora Visual C# w celu utworzenia aplikacji aplikację MSBuildSample i umieszczenie jej w folderze \Bin\.  
  
2. Aby sprawdzić, czy folder \Bin\ został utworzony i czy zawiera aplikację aplikację MSBuildSample, wpisz **dir bin**.  
  
3. Przetestuj aplikację, wpisując **Bin\MSBuildSample**.  
  
     **Witaj, świecie!** powinien być wyświetlony komunikat.  
  
## <a name="adding-build-targets"></a>Dodawanie celów kompilacji  
 Następnie Dodaj dwa elementy docelowe do pliku projektu w następujący sposób:  
  
- Czysty element docelowy, który usuwa stare pliki.  
  
- Obiekt docelowy odbudowywania, który używa `DependsOnTargets` atrybutu, aby wymusić uruchomienie czystego zadania przed zadaniem kompilacji.  
  
  Teraz, gdy masz wiele obiektów docelowych, możesz ustawić cel kompilacji jako domyślny element docelowy.  
  
#### <a name="to-add-build-targets"></a>Aby dodać cele kompilacji  
  
1. W pliku projektu, Dodaj te dwa obiekty docelowe tuż po elemencie docelowym kompilacji:  
  
   ```  
   <Target Name="Clean" >  
     <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
   </Target>  
   <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
   ```  
  
    Czysty obiekt docelowy wywołuje zadanie usuwania, aby usunąć aplikację. Cel ponownego kompilowania nie jest uruchamiany, dopóki nie zostanie uruchomiony zarówno czysty element docelowy, jak i element docelowy kompilacji. Mimo że miejsce docelowe odbudowywania nie ma żadnych zadań, powoduje, że jest uruchamiany czysty element docelowy przed elementem docelowym kompilacji.  
  
2. Dodaj ten `DefaultTargets` atrybut do otwierającego `Project` elementu:  
  
   ```  
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   ```  
  
    Ustawia cel kompilacji jako domyślny element docelowy.  
  
   Plik projektu powinien teraz wyglądać podobnie do następującego kodu:  
  
```  
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
  
## <a name="testing-the-build-targets"></a>Testowanie elementów docelowych kompilacji  
 W celu przetestowania tych funkcji w pliku projektu można wykonać nowe cele kompilacji:  
  
- Kompilowanie kompilacji domyślnej.  
  
- Ustawianie nazwy aplikacji w wierszu polecenia.  
  
- Usuwanie aplikacji przed skompilowaniem innej aplikacji.  
  
- Usuwanie aplikacji bez tworzenia innej aplikacji.  
  
#### <a name="to-test-the-build-targets"></a>Aby przetestować cele kompilacji  
  
1. W wierszu polecenia wpisz **MSBuild HelloWorld. csproj/p: AssemblyName = Greetings**.  
  
     Ponieważ przełącznik **/t** nie został użyty do jawnego ustawienia obiektu docelowego, program MSBuild uruchamia domyślny element docelowy kompilacji. Przełącznik **/p** zastępuje `AssemblyName` Właściwość i przekazuje ją nowej wartości `Greetings` . Powoduje to utworzenie nowej aplikacji Greetings.exe w folderze \Bin\.  
  
2. Aby sprawdzić, czy folder \Bin\ zawiera zarówno aplikację aplikację MSBuildSample, jak i nową aplikację Greetings, wpisz **dir bin**.  
  
3. Przetestuj aplikację Greetings, wpisując **Bin\Greetings**.  
  
     **Witaj, świecie!** powinien być wyświetlony komunikat.  
  
4. Usuń aplikację aplikację MSBuildSample, wpisując polecenie **MSBuild HelloWorld. csproj/t: Clean**.  
  
     Spowoduje to uruchomienie czystego zadania, aby usunąć aplikację, która ma domyślną `AssemblyName` wartość właściwości `MSBuildSample` .  
  
5. Usuń aplikację Greetings, wpisując polecenie **MSBuild HelloWorld. csproj/t: Clean/p: AssemblyName = Greetings**.  
  
     Spowoduje to uruchomienie czystego zadania w celu usunięcia aplikacji, która ma daną wartość właściwości **AssemblyName** `Greetings` .  
  
6. Aby sprawdzić, czy folder \Bin\ jest teraz pusty, wpisz polecenie **dir bin**.  
  
7. Wpisz **MSBuild**.  
  
     Chociaż nie określono pliku projektu, MSBuild kompiluje plik HelloWorld. csproj, ponieważ w bieżącym folderze istnieje tylko jeden plik projektu. Powoduje to utworzenie aplikacji aplikację MSBuildSample w folderze \Bin\.  
  
     Aby sprawdzić, czy folder \Bin\ zawiera aplikację aplikację MSBuildSample, wpisz **dir bin**.  
  
## <a name="building-incrementally"></a>Kompilowanie przyrostowe  
 Można powiedzieć, że program MSBuild ma tworzyć obiekty docelowe tylko wtedy, gdy pliki źródłowe lub docelowe, od których zależy element docelowy, zostały zmienione. MSBuild używa sygnatury czasowej pliku, aby określić, czy został zmieniony.  
  
#### <a name="to-build-incrementally"></a>Aby kompilować przyrostowo  
  
1. W pliku projektu Dodaj te atrybuty do otwierającego elementu docelowego kompilacji:  
  
    ```  
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"  
    ```  
  
     Oznacza to, że element docelowy kompilacji zależy od plików wejściowych, które są określone w `Compile` grupie elementów, i że docelowy wynik jest plikiem aplikacji.  
  
     Utworzony element docelowy kompilacji powinien wyglądać podobnie do następującego kodu:  
  
    ```  
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">  
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
    </Target>  
    ```  
  
2. Przetestuj element docelowy kompilacji, wpisując **MSBuild/v: d** w wierszu polecenia.  
  
     Należy pamiętać, że HelloWorld. csproj jest domyślnym plikiem projektu i że kompilacja jest domyślnym obiektem docelowym.  
  
     Przełącznik **/v: d** określa pełny opis procesu kompilacji.  
  
     Powinny być wyświetlane następujące wiersze:  
  
     **Pomijanie elementu docelowego "Kompilacja", ponieważ wszystkie pliki wyjściowe są aktualne w odniesieniu do plików wejściowych.**  
  
     **Pliki wejściowe: HelloWorld.cs**  
  
     **Pliki wyjściowe: BinMSBuildSample.exe**  
  
     Program MSBuild pomija miejsce docelowe kompilacji, ponieważ żadne pliki źródłowe nie uległy zmianie od czasu ostatniego skompilowania aplikacji.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono plik projektu, który kompiluje [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikację i rejestruje komunikat zawierający nazwę pliku wyjściowego.  
  
### <a name="code"></a>Kod  
  
```csharp  
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
  
### <a name="comments"></a>Komentarze  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono plik projektu, który kompiluje [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] aplikację i rejestruje komunikat zawierający nazwę pliku wyjściowego.  
  
### <a name="code"></a>Kod  
  
```vb  
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
 Program Visual Studio może automatycznie wykonywać większość pracy, która jest wyświetlana w tym instruktażu. Aby dowiedzieć się, jak używać programu Visual Studio do tworzenia, edytowania, kompilowania i testowania plików projektów programu MSBuild, zobacz [Przewodnik: korzystanie z programu MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
## <a name="see-also"></a>Zobacz też  
[Omówienie programu MSBuild](msbuild.md)  
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
