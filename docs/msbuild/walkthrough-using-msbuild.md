---
title: 'Przewodnik: Korzystanie z programu MSBuild | Dokumentacja firmy Microsoft'
ms.date: 03/20/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8793501df4e5ab90db5987332394b7420186b6c6
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58567922"
---
# <a name="walkthrough-use-msbuild"></a>Przewodnik: Użyj programu MSBuild

Program MSBuild jest platformę kompilacji firmy Microsoft i programu Visual Studio. Ten przewodnik stanowi wprowadzenie do bloki konstrukcyjne programu MSBuild i pokazuje, jak napisać, modyfikowania i debugowania projektów programu MSBuild. Uzyskasz informacje na temat:

- Tworzenie i manipulowanie pliku projektu.

- Jak korzystać z właściwości kompilacji

- Jak używać elementów kompilacji.

Można uruchomić program MSBuild z programu Visual Studio lub **okna polecenia**. W tym instruktażu utworzysz plik projektu programu MSBuild, za pomocą programu Visual Studio. Edytuj plik projektu w programie Visual Studio i użyj **okna polecenia** do skompilowania projektu i sprawdź wyniki.

## <a name="create-an-msbuild-project"></a>Tworzenie projektu programu MSBuild

 System projektu programu Visual Studio zależy od programu MSBuild. Dzięki temu można łatwo utworzyć nowy plik projektu programu Visual Studio. W tej sekcji utworzysz plik projektu języka Visual C#. Można zamiast tego utworzyć plik projektu w języku Visual Basic. W kontekście tego przewodnika różnica między plikami dwóch projektów jest niewielki.

**Aby utworzyć plik projektu**

1. Otwórz program Visual Studio i Utwórz projekt.

    ::: moniker range=">=vs-2019"
    Typ **Ctrl + Q** aby otworzyć pole wyszukiwania, wpisz **winforms**, następnie wybierz **Tworzenie nowej aplikacji Windows Forms (.NET Framework)**. W oknie dialogowym wybierz **Utwórz**.

    W **nazwa** wpisz `BuildApp`. Wprowadź **lokalizacji** dla rozwiązania, na przykład *D:\\*. Zaakceptuj wartości domyślne **rozwiązania**, **Nazwa rozwiązania** (**BuildApp**), a **Framework**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W lewym okienku **nowy projekt** okna dialogowego rozwiń **Visual C#**   >  **pulpitu Windows**, następnie wybierz **Windows Forms App (. Program .NET Framework)**. Następnie wybierz **OK**.

    W **nazwa** wpisz `BuildApp`. Wprowadź **lokalizacji** dla rozwiązania, na przykład *D:\\*. Zaakceptuj wartości domyślne **Utwórz katalog rozwiązania** (zaznaczone), **Dodaj do kontroli źródła** (nie jest zaznaczone), a **Nazwa rozwiązania** (**BuildApp**).
    ::: moniker-end

1. Kliknij przycisk **OK** lub **Utwórz** do tworzenia pliku projektu.

## <a name="examine-the-project-file"></a>Zapoznaj się z plikiem projektu
 Aby utworzyć plik projektu języka Visual C# w poprzedniej sekcji użyto programu Visual Studio. Plik projektu jest reprezentowana w **Eksploratora rozwiązań** przez węzeł projektu o nazwie BuildApp. Edytor kodu programu Visual Studio można użyć do sprawdzenia pliku projektu.

**Aby zbadać pliku projektu**

1.  W **Eksploratora rozwiązań**, kliknij węzeł projektu **BuildApp**.

2.  W **właściwości** przeglądarki, zwróć uwagę, że **pliku projektu** właściwość *BuildApp.csproj*. Wszystkie pliki projektu są nazywane z sufiksem *proj*. Jeśli została utworzona projekt języka Visual Basic, nazwa pliku projektu będzie *BuildApp.vbproj*.

3.  Kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij przycisk **Zwolnij projekt**.

4.  Ponownie kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij przycisk **Edytuj BuildApp.csproj**.

     Plik projektu zostanie wyświetlony w edytorze kodu.

## <a name="targets-and-tasks"></a>Elementy docelowe i zadania

Pliki projektu są pliki w formacie XML z węzłem głównym [projektu](../msbuild/project-element-msbuild.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Należy określić przestrzeni nazw xmlns w elemencie projektu. Jeśli `ToolsVersion` znajduje się w nowym projekcie, musi być "15.0".

Pracy tworzenia aplikacji odbywa się za pomocą [docelowej](../msbuild/target-element-msbuild.md) i [zadań](../msbuild/task-element-msbuild.md) elementów.

- Zadanie jest najmniejsza jednostka pracy, innymi słowy, "atom" kompilacji. Zadania są niezależne wykonywalnego składniki, które mogą mieć dane wejściowe i wyjściowe. Nie ma żadnych zadań, lub obecnie odwołuje się określona w pliku projektu. Dodaj zadania do pliku projektu, w poniższych sekcjach. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md) tematu.

- Obiekt docelowy jest nazwane sekwencji zadań. Aby uzyskać więcej informacji, zobacz [cele](../msbuild/msbuild-targets.md) tematu.

Domyślny element docelowy nie jest zdefiniowany w pliku projektu. Zamiast tego jest określona w projektach zaimportowane. [Importu](../msbuild/import-element-msbuild.md) element określa importowany projektów. Na przykład w projekcie języka C#, domyślny element docelowy jest importowany z pliku *Microsoft.CSharp.targets*.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

Zaimportowane pliki skutecznie są wstawiane do pliku projektu, wszędzie tam, gdzie występuje do nich.

> [!NOTE]
> Niektórych typach projektów, takich jak .NET Core, użyj uproszczonego schematu z `Sdk` atrybutu zamiast `ToolsVersion`. Te projekty mają niejawnego importu i różne domyślne wartości atrybutów.

Program MSBuild śledzi obiekty docelowe kompilacji i gwarantuje, że każdego obiektu docelowego jest stworzone z nie więcej niż raz.

## <a name="add-a-target-and-a-task"></a>Dodaj obiekt docelowy i zadania

 Dodanie elementu docelowego w pliku projektu. Dodaj zadanie do docelowego, który wyświetla komunikat.

**Aby dodać element docelowy i zadania**

1. Dodaj następujące wiersze do pliku projektu, zaraz po instrukcję importu:

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

     Spowoduje to utworzenie obiektu docelowego o nazwie HelloWorld. Należy zauważyć, że masz obsługę funkcji IntelliSense podczas edycji pliku projektu.

2. Dodaj wiersze do docelowego HelloWorld tak, aby wynikową sekcję wygląda następująco:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3. Zapisz plik projektu.

Zadanie komunikatu jest jednym z wielu zadań, które jest dostarczany za pomocą narzędzia MSBuild. Aby uzyskać pełną listę dostępnych zadań i informacje o użyciu, zobacz [zadania, odwołanie](../msbuild/msbuild-task-reference.md).

Zadanie komunikatu przyjmuje wartość ciągu atrybutu tekstu jako danych wejściowych i wyświetla je na urządzeniu wyjściowym. Docelowy HelloWorld wykonuje zadanie komunikatu dwa razy: najpierw po to, aby wyświetlić "Hello", a następnie, aby wyświetlić "World".

## <a name="build-the-target"></a>Tworzenie obiektu docelowego

 Uruchom program MSBuild z **wiersz polecenia dla deweloperów** dla programu Visual Studio do tworzenia pod kątem HelloWorld zdefiniowanych powyżej. Użyj - docelowego lub -t przełącznik wiersza polecenia do wybierz docelową.

> [!NOTE]
>  Będziemy nazywać **wiersz polecenia dla deweloperów** jako **okna polecenia** w poniższych sekcjach.

**Aby zbudować obiekt docelowy**

1. Otwórz **okna polecenia**.

   (System Windows 10) W polu wyszukiwania na pasku zadań, należy uruchomić, wpisując nazwę narzędzia, takie jak `dev` lub `developer command prompt`. Wyświetlenie listy zainstalowanych aplikacji spełniających kryteria wyszukiwania.

   Jeśli potrzebujesz ręcznie znaleźć, plik jest *LaunchDevCmd.bat* w *< folder instalacji programu Visual Studio\>\<wersji > \Common7\Tools* folderu.

2. W oknie polecenia przejdź do folderu zawierającego plik projektu, w tym przypadku *D:\BuildApp\BuildApp*.

3. Msbuild wykonywania za pomocą polecenia przełącznika - t: HelloWorld. Wybiera i tworzy element docelowy HelloWorld:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Sprawdź dane wyjściowe w **okna polecenia**. Powinny zostać wyświetlone dwa wiersze "Hello" i "World":

    ```
    Hello
    World
    ```

> [!NOTE]
>  Jeśli zamiast tego zostanie wyświetlony `The target "HelloWorld" does not exist in the project` , a następnie prawdopodobnie, że nie można zapisać pliku projektu w edytorze kodu. Zapisz plik i spróbuj ponownie.

 Przez przełączanie między Edytorem kodu a oknie wiersza polecenia, można zmienić w pliku projektu i szybko wyświetlić wyniki.

## <a name="build-properties"></a>Właściwości kompilacji

 Właściwości kompilacji są pary nazwa wartość, które przeprowadzą kompilacji. Kilka właściwości kompilacji są już zdefiniowane w górnej części pliku projektu:

```xml
<PropertyGroup>
...
  <ProductVersion>10.0.11107</ProductVersion>
  <SchemaVersion>2.0</SchemaVersion>
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>
  <OutputType>WinExe</OutputType>
...
</PropertyGroup>
```

 Wszystkie właściwości są elementami podrzędnymi PropertyGroup elementów. Nazwa właściwości jest nazwą elementu podrzędnego, a wartość właściwości jest elementem tekstu elementu podrzędnego. Na przykład

```xml
<TargetFrameworkVersion>v15.0</TargetFrameworkVersion>
```

 Definiuje właściwość o nazwie TargetFrameworkVersion, nadając mu wartość ciągu "15.0".

 Tworzenie właściwości mogą być zmieniane w dowolnym momencie. IF

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 pojawi się później w pliku projektu lub w pliku później zaimportowane w pliku projektu, a następnie TargetFrameworkVersion pobiera nową wartość "3.5".

## <a name="examine-a-property-value"></a>Sprawdź wartość właściwości
 Aby uzyskać wartość właściwości, należy użyć następującej składni, gdzie PropertyName jest nazwa właściwości:

```xml
$(PropertyName)
```

 Aby sprawdzić niektóre właściwości w pliku projektu, należy użyć następującej składni.

**Aby sprawdzić wartość właściwości**

1. W edytorze kodu Zastąp element docelowy HelloWorld ten kod:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

2. Zapisz plik projektu.

3. Z **okna polecenia**, wprowadź i wykonuje ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zbadaj dane wyjściowe. Powinny zostać wyświetlone następujące dwa wiersze (.NET Framework w wersji mogą się różnić):

    ```
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

> [!NOTE]
>  Jeśli nie widzisz te wiersze następnie prawdopodobnie, że nie można zapisać pliku projektu w edytorze kodu. Zapisz plik i spróbuj ponownie.

### <a name="conditional-properties"></a>Właściwości warunkowych

 Zdefiniowano wiele właściwości, takich jak konfiguracja warunkowo, oznacza to, że atrybut warunku pojawia się w elemencie właściwości. Warunkowe właściwości są zdefiniowane lub zdefiniować jej ponownie tylko wtedy, gdy wyrażenie zwróci wartość "true". Należy pamiętać, że podane są niezdefiniowanymi właściwościami domyślna wartość pustego ciągu. Na przykład

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 oznacza, że "Jeśli nie została jeszcze zdefiniowana właściwość konfiguracji, zdefiniuj go i nadaj mu wartość"Debugowanie"".

 Niemal wszystkie elementy programu MSBuild może mieć atrybutu warunku. Aby uzyskać więcej dyskusję na temat przy użyciu atrybutu warunku, zobacz [warunki](../msbuild/msbuild-conditions.md).

### <a name="reserved-properties"></a>Właściwości zastrzeżone

 Program MSBuild rezerwuje niektóre nazwy właściwości do przechowywania informacji o pliku projektu oraz pliki binarne programu MSBuild. MSBuildToolsPath znajduje się przykład właściwości zastrzeżonych. Właściwości zastrzeżone są przywoływane przy użyciu notacji $, podobnie jak inne właściwości. Aby uzyskać więcej informacji, zobacz [jak: Odwołanie do nazwy lub lokalizacji pliku projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) i [MSBuild zarezerwowane i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md).

### <a name="environment-variables"></a>Zmienne środowiskowe

 Możesz odwoływać się zmiennych środowiskowych w plikach projektu taki sam sposób, jak właściwości kompilacji. Na przykład aby użyć zmiennej środowiskowej PATH w pliku projektu, należy użyć składni $(Path). Jeśli projekt zawiera definicję właściwości, która ma taką samą nazwę jako zmienną środowiskową, właściwość w projekcie zastępuje wartość zmiennej środowiskowej. Aby uzyskać więcej informacji, zobacz [jak: Użycie zmiennych środowiskowych w kompilacji](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Ustawianie właściwości w wierszu polecenia

 Właściwości mogą być określone w wierszu polecenia za pomocą - lub -p właściwości przełącznik wiersza polecenia. Wartości właściwości odebranych w wierszu polecenia zastępują wartości właściwości ustawione w projekcie plików i zmiennymi środowiskowymi.

**Aby ustawić wartość właściwości z wiersza polecenia**

1.  Z **okna polecenia**, wprowadź i wykonuje ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

2.  Zbadaj dane wyjściowe. Powinien zostać wyświetlony ten wiersz:

    ```
    Configuration is Release.
    ```

Program MSBuild tworzy właściwość konfiguracji i nadaje mu wartość "Wersja".

## <a name="special-characters"></a>Znaki specjalne

 Niektóre znaki mają specjalne znaczenie w plikach projektu programu MSBuild. Przykłady te znaki średnikami (;) i gwiazdki (*). Aby można było używać tych znaków specjalnych jako literały w pliku projektu, muszą one być określone za pomocą składni %\<xx >, gdzie \<xx > reprezentuje wartości szesnastkowej znaku ASCII.

 Zmień zadanie komunikatu, aby wyświetlić wartość właściwości konfiguracji przy użyciu znaków specjalnych, aby był bardziej czytelny.

**Aby użyć znaków specjalnych w zadaniu wiadomości**

1. W edytorze kodu Zastąp zarówno do zadań komunikat ten wiersz:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

2. Zapisz plik projektu.

3. Z **okna polecenia**, wprowadź i wykonuje ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zbadaj dane wyjściowe. Powinien zostać wyświetlony ten wiersz:

    ```
    $(Configuration) is "Debug"
    ```

Aby uzyskać więcej informacji, zobacz [znaki specjalne MSBuild](../msbuild/msbuild-special-characters.md).

## <a name="build-items"></a>Tworzenie elementów

 Element to fragment informacji, zwykle nazwę pliku, który jest używany jako dane wejściowe do systemu kompilacji. Na przykład kolekcję elementów reprezentujących pliki źródłowe mogą być przekazywane do zadania o nazwie kompilacji, aby skompilować je do zestawu.

 Wszystkie elementy są elementami podrzędnymi ItemGroup elementów. Nazwa elementu jest nazwą elementu podrzędnego, a wartość elementu jest wartością atrybutu Uwzględnij elementu podrzędnego. Wartości elementów o takiej samej nazwie są zbierane w typy elementów o takiej nazwie.  Na przykład

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

 Definiuje grupy elementów zawierających dwa elementy. Typ elementu kompilacji ma dwie wartości: *Plik program.cs* i *Properties\AssemblyInfo.cs*.

 Poniższy kod tworzy tego samego typu elementu, deklarując oba pliki w jednym atrybucie Include, rozdzielając je średnikiem.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).

> [!NOTE]
>  Ścieżki plików są względne wobec folderu zawierającego plik projektu programu MSBuild.

## <a name="examine-item-type-values"></a>Sprawdź wartości typu elementu

 Aby uzyskać wartości typu elementu, należy użyć następującej składni, gdzie ItemType to nazwa typu elementu:

```xml
@(ItemType)
```

 Użyj następującej składni, aby sprawdzić typ elementu kompilacji w pliku projektu.

**Aby sprawdzić wartości typu elementu**

1. W edytorze kodu Zastąp zadanie docelowe HelloWorld ten kod:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

2. Zapisz plik projektu.

3. Z **okna polecenia**, wprowadź i wykonuje ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zbadaj dane wyjściowe. Powinien zostać wyświetlony ten długi wiersz:

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

Wartości typu elementu są oddzielone średnikami domyślne.

Aby zmienić separator typ elementu, użyj następującej składni, gdzie ItemType jest typ elementu, a separatorem jest co najmniej jeden znak oddzielający ciąg:

```xml
@(ItemType, Separator)
```

Zmień zadanie komunikatu do używania znaki powrotu karetki i wiersz źródła danych (% 0A %0 D) aby wyświetlić kompilacji elementów, jeden na wiersz.

**Aby wyświetlić typ elementu wartości jeden na wiersz**

1.  W edytorze kodu Zastąp zadanie komunikatu ten wiersz:

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2.  Zapisz plik projektu.

3.  Z **okna polecenia**, wprowadź i wykonuje ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Zbadaj dane wyjściowe. Powinny zostać wyświetlone następujące wiersze:

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Obejmują wykluczania i symboli wieloznacznych
 Można używać symboli wieloznacznych "*","\*\*", i "?" za pomocą atrybutu Include, aby dodać elementy do typu elementu. Na przykład

```xml
<Photos Include="images\*.jpeg" />
```

 dodaje wszystkie pliki z rozszerzeniem pliku *JPEG* w *obrazów* folderu do typu elementu zdjęcia, podczas gdy

```xml
<Photos Include="images\**.jpeg" />
```

 dodaje wszystkie pliki z rozszerzeniem pliku *JPEG* w *obrazów* folder i wszystkie jego podfoldery do typu elementu zdjęcia. Aby uzyskać więcej przykładów, zobacz [jak: Wybieranie plików do kompilacji](../msbuild/how-to-select-the-files-to-build.md).

 Należy zauważyć, że podaną elementów dodanych do typu elementu. Na przykład

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 Tworzy typ elementu o nazwie zdjęcie zawierający wszystkie pliki w *obraz* folder z rozszerzeniem pliku albo *JPEG* lub *.gif*. Jest to równoważne następujący wiersz:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Element można wykluczyć z typem elementu z atrybutem wykluczania. Na przykład

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 dodaje wszystkie pliki z rozszerzeniem pliku *.cs* kompilacji typu elementu, z wyjątkiem plików których nazwy zawierają ciąg *projektanta*. Aby uzyskać więcej przykładów, zobacz [jak: Wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).

Ten atrybut wykluczania dotyczy tylko elementy dodane przez atrybut Include w pozycji elementu, który zawiera oba te. Na przykład

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

nie wyklucza pliku *Form1.cs*, który został dodany w poprzedniej pozycji elementu.

**Do dołączania i wykluczania elementów**

1. W edytorze kodu Zastąp zadanie komunikatu ten wiersz:

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2. Dodaj tę grupę elementu zaraz po Import element:

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3. Zapisz plik projektu.

4. Z **okna polecenia**, wprowadź i wykonuje ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5. Zbadaj dane wyjściowe. Powinien zostać wyświetlony ten wiersz:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Metadane elementu
 Elementy może zawierać metadane oraz informacje zebrane z atrybutów dołączania i wykluczania. Te metadane może służyć przez zadania, które wymagają więcej informacji na temat elementów niż tylko wartości elementu.

 Metadane elementu jest zadeklarowany w pliku projektu poprzez utworzenie elementu o nazwie metadanych jako element podrzędny elementu. Element może mieć zero lub więcej wartości metadanych. Na przykład następujący element CSFile ma metadane kultury z wartością "Fr":

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Aby uzyskać wartości metadanych typu elementu, użyj następującej składni, gdzie ItemType jest nazwa typu elementu, a MetaDataName to nazwa metadanych:

```xml
%(ItemType.MetaDataName)
```

**Aby zbadać metadane elementu**

1. W edytorze kodu Zastąp zadanie komunikatu ten wiersz:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2. Zapisz plik projektu.

3. Z **okna polecenia**, wprowadź i wykonuje ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zbadaj dane wyjściowe. Powinny zostać wyświetlone następujące wiersze:

    ```
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

Zwróć uwagę, jak frazę "Compile.DependentUpon" pojawia się wiele razy. Użycie metadanych za pomocą następującej składni w elemencie docelowym powoduje, że "przetwarzanie wsadowe". Przetwarzanie wsadowe oznacza, że w ciągu docelowym wykonywane są zadania raz dla każdej wartości unikatowe metadane. To jest odpowiednikiem skryptu MSBuild typowe "dla pętli" konstrukcji programowania. Aby uzyskać więcej informacji, zobacz [przetwarzania wsadowego](../msbuild/msbuild-batching.md).

### <a name="well-known-metadata"></a>metadane dobrze znanego

 Gdy element zostanie dodany do listy elementów, ten element jest przypisywany niektóre metadane dobrze znanego. Na przykład %(Filename) zwraca nazwę pliku dowolnego elementu. Aby uzyskać pełną listę znanych metadanych, zobacz [metadane dobrze znanego elementu](../msbuild/msbuild-well-known-item-metadata.md).

**Aby zbadać dobrze znanych metadanych**

1. W edytorze kodu Zastąp zadanie komunikatu ten wiersz:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2. Zapisz plik projektu.

3. Z **okna polecenia**, wprowadź i wykonuje ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zbadaj dane wyjściowe. Powinny zostać wyświetlone następujące wiersze:

    ```
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

Przez porównanie dwóch przykładach, można zobaczyć, że chociaż nie każdy element w typie elementu kompilacji ma DependentUpon metadanych, wszystkie elementy mają dobrze znane nazwy pliku metadanych.

### <a name="metadata-transformations"></a>Przekształcenia metadanych

 Element listy może zostać zamieniony na nowy element listy. Przekształcanie listy elementów, należy użyć następującej składni, gdzie \<ItemType > jest nazwą typu elementu i \<MetadataName > jest nazwą metadanych:

```xml
@(ItemType -> '%(MetadataName)')
```

Na przykład element lista plików źródłowych mogą zostać przekształcone na kolekcję plików obiektów za pomocą wyrażenia takie jak `@(SourceFiles -> '%(Filename).obj')`. Aby uzyskać więcej informacji, zobacz [przekształca](../msbuild/msbuild-transforms.md).

**Aby przekształcić elementy przy użyciu metadanych**

1. W edytorze kodu Zastąp zadanie komunikatu ten wiersz:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2. Zapisz plik projektu.

3. Z **okna polecenia**, wprowadź i wykonuje ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zbadaj dane wyjściowe. Powinien zostać wyświetlony ten wiersz:

    ```
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Zwróć uwagę, że metadane wyrażone w tej składni nie powoduje, że przetwarzanie wsadowe.

## <a name="whats-next"></a>Co dalej?

 Informacje na temat tworzenia pliku prostego projektu w jednym kroku w danym momencie, wypróbuj [instruktażu: Tworzenie pliku projektu MSBuild od zera](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

## <a name="see-also"></a>Zobacz także

- [Przegląd MSBuild](../msbuild/msbuild.md)
- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
