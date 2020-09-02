---
title: 'Przewodnik: korzystanie z programu MSBuild | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6e77934f8e565800eb4a7a753df4beb3b003fbb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796892"
---
# <a name="walkthrough-using-msbuild"></a>Przewodnik: Korzystanie z programu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild to platforma kompilacji dla programu Microsoft i programu Visual Studio. Ten Instruktaż wprowadza do bloków konstrukcyjnych programu MSBuild i pokazuje, jak pisać, manipulować i debugować projekty MSBuild. Dowiesz się więcej na temat:  
  
- Tworzenie pliku projektu i manipulowanie nim.  
  
- Jak używać właściwości kompilacji  
  
- Jak używać elementów kompilacji.  
  
  Program MSBuild można uruchomić z programu Visual Studio lub z okna poleceń. W tym instruktażu utworzysz plik projektu MSBuild przy użyciu programu Visual Studio. Można edytować plik projektu w programie Visual Studio i użyć okna polecenia do skompilowania projektu i przeanalizowania wyników.  
  
## <a name="creating-an-msbuild-project"></a>Tworzenie projektu MSBuild  
 System projektu programu Visual Studio jest oparty na programie MSBuild. Dzięki temu można łatwo utworzyć nowy plik projektu przy użyciu programu Visual Studio. W tej sekcji utworzysz plik projektu Visual C#. Zamiast tego można utworzyć plik projektu Visual Basic. W kontekście tego instruktażu różnica między dwoma plikami projektu jest niewielka.  
  
#### <a name="to-create-a-project-file"></a>Aby utworzyć plik projektu  
  
1. Otwórz program Visual Studio.  
  
2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.  
  
3. W oknie dialogowym **Nowy projekt** wybierz typ projektu Visual C#, a następnie wybierz szablon **aplikacji Windows Forms** . W polu **Nazwa** wpisz `BuildApp`. Wprowadź **lokalizację** rozwiązania, na przykład `D:\` . Zaakceptuj wartości domyślne dla opcji **Utwórz katalog dla rozwiązania** (wybrane), **Dodaj do kontroli źródła** (nie wybrano) i **nazwę rozwiązania** ( `BuildApp` ).  
  
     Kliknij przycisk **OK** , aby utworzyć plik projektu.  
  
## <a name="examining-the-project-file"></a>Badanie pliku projektu  
 W poprzedniej sekcji użyto programu Visual Studio do utworzenia pliku projektu Visual C#. Plik projektu jest reprezentowany w **Eksplorator rozwiązań** przez węzeł projektu o nazwie BuildApp. Aby przejrzeć plik projektu, można użyć edytora kodu programu Visual Studio.  
  
#### <a name="to-examine-the-project-file"></a>Aby przejrzeć plik projektu  
  
1. W **Eksplorator rozwiązań**kliknij węzeł projektu BuildApp.  
  
2. W przeglądarce **Właściwości** należy zauważyć, że właściwość **pliku projektu** to BuildApp. csproj. Wszystkie pliki projektu mają nazwę z sufiksem "proj". Jeśli utworzono projekt Visual Basic, nazwa pliku projektu byłaby BuildApp. vbproj.  
  
3. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij polecenie **Zwolnij projekt**.  
  
4. Ponownie kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij polecenie **Edytuj BuildApp. csproj**.  
  
     Plik projektu pojawi się w edytorze kodu.  
  
## <a name="targets-and-tasks"></a>Cele i zadania  
 Pliki projektu są plikami w formacie XML z [projektem](../msbuild/project-element-msbuild.md)węzła głównego.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Project ToolsVersion="12.0" DefaultTargets="Build"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Należy określić przestrzeń nazw xmlns w elemencie projektu.  
  
 Prace nad tworzeniem aplikacji są wykonywane z elementami [docelowymi](../msbuild/target-element-msbuild.md) i [zadaniami](../msbuild/task-element-msbuild.md) .  
  
- Zadanie jest najmniejszą jednostką pracy, innymi słowy, "atom" kompilacji. Zadania są niezależnymi składnikami wykonywalnymi, które mogą mieć dane wejściowe i wyjściowe. W pliku projektu nie ma aktualnie przywoływanych zadań ani ich nie zdefiniowano. Do pliku projektu można dodać zadania w poniższych sekcjach. Aby uzyskać więcej informacji, zobacz temat [zadania](../msbuild/msbuild-tasks.md) .  
  
- Obiekt docelowy jest nazwaną sekwencją zadań. Na końcu pliku projektu znajdują się dwa obiekty docelowe, które są obecnie ujęte w komentarze HTML: BeforeBuild i AfterBuild.  
  
  ```  
  <Target Name="BeforeBuild">  
  </Target>  
  <Target Name="AfterBuild">  
  </Target>  
  ```  
  
   Aby uzyskać więcej informacji, zobacz temat [targets](../msbuild/msbuild-targets.md) .  
  
  Węzeł projektu ma opcjonalny atrybut DefaultTargets —, który wybiera domyślny cel do skompilowania. w tym przypadku kompilacja.  
  
```  
<Project ToolsVersion="12.0" DefaultTargets="Build" ...  
```  
  
 Element docelowy kompilacji nie jest zdefiniowany w pliku projektu. Zamiast tego jest zaimportowany z pliku Microsoft. CSharp. targets przy użyciu elementu [Import](../msbuild/import-element-msbuild.md) .  
  
```  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 Importowane pliki są efektywnie umieszczane w pliku projektu wszędzie tam, gdzie się znajdują.  
  
 Program MSBuild śledzi elementy docelowe kompilacji i gwarantuje, że każdy element docelowy nie jest zbudowany więcej niż raz.  
  
## <a name="adding-a-target-and-a-task"></a>Dodawanie obiektu docelowego i zadania  
 Dodaj element docelowy do pliku projektu. Dodaj zadanie do obiektu docelowego, które drukuje komunikat.  
  
#### <a name="to-add-a-target-and-a-task"></a>Aby dodać obiekt docelowy i zadanie  
  
1. Dodaj te wiersze do pliku projektu zaraz po instrukcji import:  
  
   ```  
   <Target Name="HelloWorld">  
   </Target>  
   ```  
  
    Spowoduje to utworzenie obiektu docelowego o nazwie HelloWorld. Należy zauważyć, że obsługa IntelliSense jest obsługiwana podczas edytowania pliku projektu.  
  
2. Dodaj wiersze do elementu docelowego HelloWorld, aby sekcja wynikowa wyglądała następująco:  
  
   ```  
   <Target Name="HelloWorld">  
     <Message Text="Hello"></Message>  <Message Text="World"></Message>  
   </Target>  
   ```  
  
3. Zapisz plik projektu.  
  
   Zadanie jest jednym z wielu zadań, które są dostarczane z programem MSBuild. Aby uzyskać pełną listę dostępnych zadań i informacji o użyciu, zobacz [Dokumentacja zadania](../msbuild/msbuild-task-reference.md).  
  
   Zadanie Message przyjmuje wartość ciągu atrybutu Text jako dane wejściowe i wyświetla go na urządzeniu wyjściowym. Obiekt docelowy HelloWorld wykonuje zadanie komunikatu dwa razy: najpierw, aby wyświetlić "Hello", a następnie wyświetlić "World".  
  
## <a name="building-the-target"></a>Kompilowanie elementu docelowego  
 Uruchom narzędzie MSBuild z **wiersza polecenia programu Visual Studio** , aby skompilować element docelowy HelloWorld zdefiniowany powyżej. Użyj przełącznika wiersza polecenia/Target lub/t, aby wybrać element docelowy.  
  
> [!NOTE]
> Odwołujemy się do **wiersza polecenia programu Visual Studio** jako **okna polecenia** w poniższych sekcjach.  
  
#### <a name="to-build-the-target"></a>Aby skompilować element docelowy  
  
1. Kliknij przycisk **Start**, a następnie kliknij pozycję **Wszystkie programy**. Znajdź i kliknij **wiersz polecenia programu Visual Studio** w folderze **Visual Studio Tools** .  
  
2. W oknie polecenia przejdź do folderu zawierającego plik projektu, w tym przypadku D:\BuildApp\BuildApp.  
  
3. Uruchom program MSBuild przy użyciu przełącznika polecenia/t: HelloWorld. Spowoduje to wybranie i kompilację elementu docelowego HelloWorld:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4. Przejrzyj dane wyjściowe w **okno polecenie**. Powinny być widoczne dwie linie "Hello" i "World":  
  
    ```  
    Hello  
    World  
    ```  
  
> [!NOTE]
> Jeśli zamiast tego zobaczysz, `The target "HelloWorld" does not exist in the project` prawdopodobnie zapomniano zapisać plik projektu w edytorze kodu. Zapisz plik i spróbuj ponownie.  
  
 Przez przemienne między edytorem kodu a oknem polecenia można zmienić plik projektu i szybko zobaczyć wyniki.  
  
> [!NOTE]
> Jeśli uruchamiasz program MSBuild bez przełącznika polecenia/t, MSBuild kompiluje element docelowy określony przez atrybut DefaultTarget elementu projektu, w tym przypadku "Kompilacja". Spowoduje to kompilację BuildApp.exe aplikacji Windows Forms.  
  
## <a name="build-properties"></a>Właściwości kompilacji  
 Właściwości kompilacji to pary nazwa-wartość, które kierują kompilację. Kilka właściwości kompilacji jest już zdefiniowanych u góry pliku projektu:  
  
```  
<PropertyGroup>  
...  
  <ProductVersion>10.0.11107</ProductVersion>  
  <SchemaVersion>2.0</SchemaVersion>  
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>  
  <OutputType>WinExe</OutputType>  
...  
</PropertyGroup>  
```  
  
 Wszystkie właściwości są elementami podrzędnymi elementów właściwości. Nazwa właściwości jest nazwą elementu podrzędnego, a wartość właściwości jest element tekstowy elementu podrzędnego. Przykład:  
  
```  
<TargetFrameworkVersion>v12.0</TargetFrameworkVersion>  
```  
  
 definiuje właściwość o nazwie TargetFrameworkVersion, podając ją jako wartość ciągu "v 12".  
  
 Właściwości kompilacji można ponownie zdefiniować w dowolnym momencie. Jeśli użytkownik  
  
```  
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
```  
  
 pojawia się w dalszej części pliku projektu lub w pliku zaimportowanego później w pliku projektu, a następnie TargetFrameworkVersion przyjmuje nową wartość "v 3.5".  
  
## <a name="examining-a-property-value"></a>Badanie wartości właściwości  
 Aby uzyskać wartość właściwości, należy użyć następującej składni, gdzie PropertyName jest nazwą właściwości:  
  
```  
$(PropertyName)  
```  
  
 Użyj tej składni do sprawdzenia niektórych właściwości w pliku projektu.  
  
#### <a name="to-examine-a-property-value"></a>Aby przejrzeć wartość właściwości  
  
1. W edytorze kodu Zastąp element docelowy HelloWorld tym kodem:  
  
    ```  
    <Target Name="HelloWorld">  
      <Message Text="Configuration is $(Configuration)" />  
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />  
    </Target>  
    ```  
  
2. Zapisz plik projektu.  
  
3. W **oknie polecenia**wpisz i wykonaj ten wiersz:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4. Sprawdź dane wyjściowe. Powinny być widoczne te dwie linie (wersja .NET Framework może się różnić):  
  
    ```  
    Configuration is Debug  
    MSBuildToolsPath is C:\Program Files\MSBuild\12.0\bin  
    ```  
  
> [!NOTE]
> Jeśli te wiersze nie są widoczne, prawdopodobnie zapomniano zapisać plik projektu w edytorze kodu. Zapisz plik i spróbuj ponownie.  
  
### <a name="conditional-properties"></a>Właściwości warunkowe  
 Wiele właściwości, takich jak konfiguracja, jest zdefiniowana warunkowo, to oznacza, że atrybut Condition jest wyświetlany w elemencie właściwości. Właściwości warunkowe są zdefiniowane lub definiowane ponownie tylko wtedy, gdy warunek ma wartość "true". Należy zauważyć, że niezdefiniowane właściwości otrzymują wartość domyślną pustego ciągu. Przykład:  
  
```  
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 oznacza "Jeśli nie zdefiniowano jeszcze właściwości konfiguracji, zdefiniuj ją i nadaj jej wartość" debug ".  
  
 Prawie wszystkie elementy MSBuild mogą mieć atrybut Condition. Aby uzyskać więcej informacji na temat używania atrybutu Condition, zobacz [warunki](../msbuild/msbuild-conditions.md).  
  
### <a name="reserved-properties"></a>Właściwości zastrzeżone  
 Program MSBuild rezerwuje nazwy właściwości w celu przechowywania informacji o pliku projektu i plikach binarnych programu MSBuild. MSBuildToolsPath jest przykładem zastrzeżonej właściwości. Właściwości zastrzeżone są przywoływane w notacji $, podobnie jak każda inna właściwość. Aby uzyskać więcej informacji, zobacz [jak: odwoływanie się do nazwy lub lokalizacji pliku projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) oraz [Właściwości zastrzeżonych i dobrze znanych programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
### <a name="environment-variables"></a>Zmienne środowiskowe  
 Można odwoływać się do zmiennych środowiskowych w plikach projektu w taki sam sposób, jak właściwości kompilacji. Na przykład, aby użyć zmiennej środowiskowej PATH w pliku projektu, należy użyć $ (Path). Jeśli projekt zawiera definicję właściwości, która ma taką samą nazwę jak zmienna środowiskowa, właściwość w projekcie przesłania wartość zmiennej środowiskowej. Aby uzyskać więcej informacji, zobacz [jak: używać zmiennych środowiskowych w kompilacji](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
## <a name="setting-properties-from-the-command-line"></a>Ustawianie właściwości z wiersza polecenia  
 Właściwości można definiować w wierszu polecenia przy użyciu przełącznika wiersza polecenia/property lub/p. Wartości właściwości odebrane z wartości właściwości Zastąp wiersz polecenia ustawionymi w pliku projektu i zmiennych środowiskowych.  
  
#### <a name="to-set-a-property-value-from-the-command-line"></a>Aby ustawić wartość właściwości z wiersza polecenia  
  
1. W **oknie polecenia**wpisz i wykonaj ten wiersz:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld /p:Configuration=Release  
   ```  
  
2. Sprawdź dane wyjściowe. Powinien zostać wyświetlony następujący wiersz:  
  
   ```  
   Configuration is Release.  
   ```  
  
   Program MSBuild tworzy właściwość Configuration i nadaje jej wartość "Release".  
  
## <a name="special-characters"></a>Znaki specjalne  
 Niektóre znaki mają specjalne znaczenie w plikach projektu MSBuild. Przykłady tych znaków obejmują średniki (;) i gwiazdki (*). Aby można było używać tych znaków specjalnych jako literałów w pliku projektu, muszą one być określone przy użyciu składni% XX, gdzie XX reprezentuje wartość szesnastkową ASCII znaku.  
  
 Zmień zadanie, aby wyświetlić wartość właściwości Configuration ze znakami specjalnymi, aby zwiększyć czytelność.  
  
#### <a name="to-use-special-characters-in-the-message-task"></a>Aby użyć znaków specjalnych w zadaniu komunikatu  
  
1. W edytorze kodu Zastąp oba zadania komunikatów tym wierszem:  
  
   ```  
   <Message Text="%24(Configuration) is %22$(Configuration)%22" />  
   ```  
  
2. Zapisz plik projektu.  
  
3. W **oknie polecenia**wpisz i wykonaj ten wiersz:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Sprawdź dane wyjściowe. Powinien zostać wyświetlony następujący wiersz:  
  
   ```  
   $(Configuration) is "Debug"  
   ```  
  
   Aby uzyskać więcej informacji, zobacz [znaki specjalne programu MSBuild](../msbuild/msbuild-special-characters.md).  
  
## <a name="build-items"></a>Kompiluj elementy  
 Element jest częścią informacji, zazwyczaj nazwą pliku, która jest używana jako dane wejściowe systemu kompilacji. Na przykład Kolekcja elementów reprezentujących pliki źródłowe może zostać przeniesiona do zadania o nazwie Kompiluj, aby skompilować je do zestawu.  
  
 Wszystkie elementy są elementami podrzędnymi elementów Item. Nazwa elementu jest nazwą elementu podrzędnego, a wartość elementu jest wartością atrybutu Include elementu podrzędnego. Wartości elementów o tej samej nazwie są zbierane w typach elementów o tej samej nazwie.  Przykład:  
  
```  
<ItemGroup>  
    <Compile Include="Program.cs" />  
    <Compile Include="Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 definiuje grupę elementów zawierającą dwa elementy. Kompilacja typu elementu ma dwie wartości: "Program.cs" i "Properties\AssemblyInfo.cs".  
  
 Poniższy kod tworzy ten sam typ elementu przez zadeklarowanie obu plików w jednym atrybucie include, rozdzielone średnikami.  
  
```  
<ItemGroup>  
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).  
  
> [!NOTE]
> Ścieżki plików są względne wobec folderu zawierającego plik projektu MSBuild.  
  
## <a name="examining-item-type-values"></a>Badanie wartości typu elementu  
 Aby uzyskać wartości typu elementu, użyj następującej składni, gdzie ItemType jest nazwą typu elementu:  
  
```  
@(ItemType)  
```  
  
 Użyj tej składni, aby przeanalizować typ elementu kompilacji w pliku projektu.  
  
#### <a name="to-examine-item-type-values"></a>Aby przeanalizować wartości typu elementu  
  
1. W edytorze kodu Zastąp zadanie docelowe HelloWorld tym kodem:  
  
   ```  
   <Target Name="HelloWorld">  
     <Message Text="Compile item type contains @(Compile)" />  
   </Target>  
   ```  
  
2. Zapisz plik projektu.  
  
3. W **oknie polecenia**wpisz i wykonaj ten wiersz:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Sprawdź dane wyjściowe. Powinna zostać wyświetlona linia długa:  
  
   ```  
   Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs  
   ```  
  
   Wartości typu elementu są domyślnie oddzielone średnikami.  
  
   Aby zmienić separator typu elementu, użyj następującej składni, gdzie ItemType jest typem elementu, a separatorem jest ciąg składający się z co najmniej jednego rozdzielającego znaku:  
  
```  
@(ItemType, Separator)  
```  
  
 Zmień zadanie, aby użyć powrotu karetki i wysuwu wiersza (% 0A% 0D), aby wyświetlić elementy kompilacji jeden na wiersz.  
  
#### <a name="to-display-item-type-values-one-per-line"></a>Aby wyświetlić wartości typu elementu jeden na wiersz  
  
1. W edytorze kodu Zastąp zadanie komunikatu tym wierszem:  
  
    ```  
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />  
    ```  
  
2. Zapisz plik projektu.  
  
3. W **oknie polecenia**wpisz i wykonaj ten wiersz:  
  
     `msbuild buildapp.csproj /t:HelloWorld`  
  
4. Sprawdź dane wyjściowe. Powinny zostać wyświetlone następujące wiersze:  
  
    ```  
    Compile item type contains Form1.cs  
    Form1.Designer.cs  
    Program.cs  
    Properties\AssemblyInfo.cs  
    Properties\Resources.Designer.cs  
    Properties\Settings.Designer.cs  
    ```  
  
### <a name="include-exclude-and-wildcards"></a>Include, Exclude i symboli wieloznacznych  
 Możesz użyć symboli wieloznacznych "*", " \* \* " i "?" z atrybutem include, aby dodać elementy do typu elementu. Przykład:  
  
```  
<Photos Include="images\*.jpeg" />  
```  
  
 dodaje wszystkie pliki z rozszerzeniem pliku ". jpeg" w folderze images do typu elementu photos, a  
  
```  
<Photos Include="images\**.jpeg" />  
```  
  
 dodaje wszystkie pliki z rozszerzeniem pliku ". jpeg" w folderze Obrazy i wszystkie jego podfoldery do typu elementu photos. Aby uzyskać więcej przykładów, zobacz [jak to zrobić: Wybierz pliki do skompilowania](../msbuild/how-to-select-the-files-to-build.md).  
  
 Zwróć uwagę, że jako że elementy są deklarowane, są dodawane do typu elementu. Przykład:  
  
```  
<Photos Include="images\*.jpeg" />  
<Photos Include="images\*.gif" />  
```  
  
 Tworzy typ elementu o nazwie Photo zawierający wszystkie pliki w folderze Image z rozszerzeniem pliku ". jpeg" lub ". gif". Jest to równoznaczne z następującym wierszem:  
  
```  
<Photos Include="images\*.jpeg;images\*.gif" />  
```  
  
 Można wykluczyć element z typu elementu z atrybutem Exclude. Przykład:  
  
```  
<Compile Include="*.cs" Exclude="*Designer*">  
```  
  
 dodaje wszystkie pliki z plikiem Extension". cs do typu elementu kompilacji, z wyjątkiem plików, których nazwy zawierają ciąg" Projektant ". Aby uzyskać więcej przykładów, zobacz [How to: wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).  
  
 Atrybut Exclude ma wpływ tylko na elementy dodane przez atrybut Include w elemencie Item, który je zawiera. Przykład:  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 nie wykluczają Form1.cs pliku, który został dodany w poprzednim elemencie elementu.  
  
##### <a name="to-include-and-exclude-items"></a>Aby uwzględnić i wykluczyć elementy  
  
1. W edytorze kodu Zastąp zadanie komunikatu tym wierszem:  
  
    ```  
    <Message Text="Compile item type contains @(XFiles)" />  
    ```  
  
2. Dodaj tę grupę elementów tuż po elemencie import:  
  
    ```  
    <ItemGroup>  
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />  
    </ItemGroup>  
    ```  
  
3. Zapisz plik projektu.  
  
4. W **oknie polecenia**wpisz i wykonaj ten wiersz:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
5. Sprawdź dane wyjściowe. Powinien zostać wyświetlony następujący wiersz:  
  
    ```  
    Compile item type contains Form1.cs;Program.cs;Properties/Resources.resx  
    ```  
  
## <a name="item-metadata"></a>Metadane elementu  
 Elementy mogą zawierać metadane oprócz informacji zebranych z atrybutów dołączania i wykluczania. Te metadane mogą być używane przez zadania, które wymagają więcej informacji o elementach niż tylko wartość elementu.  
  
 Metadane elementu są zadeklarowane w pliku projektu przez utworzenie elementu o nazwie metadanych jako elementu podrzędnego elementu. Element może mieć zero lub więcej wartości metadanych. Na przykład następujący element CSFile ma metadane kultury o wartości "fr":  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Aby uzyskać wartość metadanych typu elementu, należy użyć następującej składni, gdzie ItemType jest nazwą typu elementu, a metadataname jest nazwą metadanych:  
  
```  
%(ItemType.MetaDataName)  
```  
  
#### <a name="to-examine-item-metadata"></a>Aby przeanalizować metadane elementu  
  
1. W edytorze kodu Zastąp zadanie komunikatu tym wierszem:  
  
   ```  
   <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />  
   ```  
  
2. Zapisz plik projektu.  
  
3. W **oknie polecenia**wpisz i wykonaj ten wiersz:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Sprawdź dane wyjściowe. Powinny zostać wyświetlone następujące wiersze:  
  
   ```  
   Compile.DependentUpon:  
   Compile.DependentUpon: Form1.cs  
   Compile.DependentUpon: Resources.resx  
   Compile.DependentUpon: Settings.settings  
   ```  
  
   Zwróć uwagę, jak fraza "Kompiluj. DependentUpon" występuje kilka razy. Użycie metadanych o tej składni w elemencie docelowym powoduje wystąpienie "wsadowe". Przetwarzanie wsadowe oznacza, że zadania w ramach elementu docelowego są wykonywane raz dla każdej unikatowej wartości metadanych. Jest to odpowiednik skryptu programu MSBuild w typowej konstrukcji programowania "pętla for". Aby uzyskać więcej informacji, zobacz Tworzenie [pakietów wsadowych](../msbuild/msbuild-batching.md).  
  
### <a name="well-known-metadata"></a>Dobrze znane metadane  
 Za każdym razem, gdy element zostanie dodany do listy elementów, do tego elementu są przypisane pewne dobrze znane metadane. Na przykład,% (filename) zwraca nazwę pliku dowolnego elementu. Aby uzyskać pełną listę dobrze znanych metadanych, zobacz [dobrze znane metadane elementu](../msbuild/msbuild-well-known-item-metadata.md).  
  
##### <a name="to-examine-well-known-metadata"></a>Aby sprawdzać dobrze znane metadane  
  
1. W edytorze kodu Zastąp zadanie komunikatu tym wierszem:  
  
   ```  
   <Message Text="Compile Filename: %(Compile.Filename)" />  
   ```  
  
2. Zapisz plik projektu.  
  
3. W **oknie polecenia**wpisz i wykonaj ten wiersz:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Sprawdź dane wyjściowe. Powinny zostać wyświetlone następujące wiersze:  
  
   ```  
   Compile Filename: Form1  
   Compile Filename: Form1.Designer  
   Compile Filename: Program  
   Compile Filename: AssemblyInfo  
   Compile Filename: Resources.Designer  
   Compile Filename: Settings.Designer  
   ```  
  
   Porównując dwa przykłady powyżej, można zobaczyć, że chociaż nie każdy element w typie elementu kompilacji ma metadane DependentUpon, wszystkie elementy mają dobrze znane metadane filename.  
  
### <a name="metadata-transformations"></a>Przekształcenia metadanych  
 Listy elementów mogą być przekształcane na listy nowych elementów. Aby przekształcić listę elementów, należy użyć następującej składni, gdzie ItemType jest nazwą typu elementu, a metadataname jest nazwą metadanych:  
  
```  
@(ItemType -> '%(MetadataName)')  
```  
  
 Na przykład lista elementów plików źródłowych może być przekształcana do kolekcji plików obiektów przy użyciu wyrażenia takiego jak `@(SourceFiles -> '%(Filename).obj')` . Aby uzyskać więcej informacji, zobacz [transformacje](../msbuild/msbuild-transforms.md).  
  
##### <a name="to-transform-items-using-metadata"></a>Aby przekształcić elementy przy użyciu metadanych  
  
1. W edytorze kodu Zastąp zadanie komunikatu tym wierszem:  
  
   ```  
   <Message Text="Backup files: @(Compile->'%(filename).bak')" />  
   ```  
  
2. Zapisz plik projektu.  
  
3. W **oknie polecenia**wpisz i wykonaj ten wiersz:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Sprawdź dane wyjściowe. Powinien zostać wyświetlony następujący wiersz:  
  
   ```  
   Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak  
   ```  
  
   Zwróć uwagę, że metadane wyrażone w tej składni nie powodują przetwarzania wsadowego.  
  
## <a name="whats-next"></a>Co dalej?  
 Aby dowiedzieć się, jak utworzyć prosty plik projektu w jednym kroku, wypróbuj [Przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
## <a name="see-also"></a>Zobacz też
[Omówienie programu MSBuild](msbuild.md)  
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
