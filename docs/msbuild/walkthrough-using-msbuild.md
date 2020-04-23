---
title: 'Przewodnik: Korzystanie z usługi MSBuild | Dokumenty firmy Microsoft'
ms.date: 03/20/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 310fa3b6795a5e340dcd9c7fa40cb27807c132ba
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072544"
---
# <a name="walkthrough-use-msbuild"></a>Instruktaż: Użyj msbuild

MSBuild to platforma kompilacji dla firm Microsoft i Visual Studio. W tym przewodniku przedstawiono do bloków konstrukcyjnych MSBuild i pokazuje, jak pisać, manipulować i debugować projekty MSBuild. Dowiesz się o:

- Tworzenie pliku projektu i manipulowanie nimi.

- Jak korzystać z właściwości kompilacji

- Jak używać elementów kompilacji.

Program MSBuild można uruchomić w programie Visual Studio lub w **oknie polecenia**. W tym instruktażu utworzysz plik projektu MSBuild przy użyciu programu Visual Studio. Edytuj plik projektu w programie Visual Studio i użyj **okna polecenia** do utworzenia projektu i zbadania wyników.

## <a name="create-an-msbuild-project"></a>Tworzenie projektu MSBuild

 System projektu programu Visual Studio jest oparty na msbuild. Ułatwia to tworzenie nowego pliku projektu przy użyciu programu Visual Studio. W tej sekcji należy utworzyć plik projektu języka Visual C#. Zamiast tego można utworzyć plik projektu języka Visual Basic. W kontekście tego przewodnika różnica między dwoma plikami projektu jest niewielka.

**Aby utworzyć plik projektu**

1. Otwórz program Visual Studio i utwórz projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno początkowe. Wpisz **Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **formularze winforms,** a następnie wybierz pozycję **Utwórz nową aplikację Windows Forms App (.NET Framework).** W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.

    W polu **Nazwa** wpisz `BuildApp`. Wprowadź **lokalizację** dla rozwiązania, na przykład *D:\\*. Zaakceptuj ustawienia domyślne dla **rozwiązania,** **nazwy rozwiązania** **(BuildApp)** i **frameworka**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł Pulpit**systemu Windows** **w języku Visual C#** > , a następnie wybierz pozycję **Windows Forms App (.NET Framework).** Następnie wybierz **przycisk OK**.

    W polu **Nazwa** wpisz `BuildApp`. Wprowadź **lokalizację** dla rozwiązania, na przykład *D:\\*. Zaakceptuj ustawienia domyślne dla **opcji Utwórz katalog dla rozwiązania** (zaznaczona), Dodaj do kontroli **źródła** (nie zaznaczona) i **Nazwa rozwiązania** **(BuildApp).**
    ::: moniker-end

1. Kliknij **przycisk OK** lub **Utwórz,** aby utworzyć plik projektu.

## <a name="examine-the-project-file"></a>Sprawdzanie pliku projektu

 W poprzedniej sekcji użyto programu Visual Studio do utworzenia pliku projektu języka Visual C#. Plik projektu jest reprezentowany w **Eksploratorze rozwiązań** przez węzeł projektu o nazwie BuildApp. Edytor kodu programu Visual Studio służy do badania pliku projektu.

**Aby sprawdzić plik projektu**

1. W **Eksploratorze rozwiązań**kliknij węzeł projektu **BuildApp**.

1. W przeglądarce **Właściwości** zwróć uwagę, że właściwość **Plik projektu** to *BuildApp.csproj*. Wszystkie pliki projektu są nazwane z przyrostkiem *proj*. Jeśli utworzono projekt visual basic, nazwa pliku projektu będzie *BuildApp.vbproj*.

1. Kliknij prawym przyciskiem myszy węzeł projektu ponownie, a następnie kliknij polecenie **Edytuj plik BuildApp.csproj**. 

     Plik projektu pojawi się w edytorze kodu.

>[!NOTE]
> W przypadku niektórych typów projektów, takich jak C++, należy zwolnić projekt (kliknij prawym przyciskiem myszy plik projektu i wybierz **pozycję Zwolnij projekt),** zanim będzie można otworzyć i edytować plik projektu.

## <a name="targets-and-tasks"></a>Cele i zadania

Pliki projektu są plikami w formacie XML z węzłem głównym [Project](../msbuild/project-element-msbuild.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Nowsze .NET Core (SDK stylu) projekty mają `Sdk` atrybut.

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Jeśli projekt nie jest projektem w stylu SDK, należy określić obszar nazw xmlns w projekcie elementu. Jeśli `ToolsVersion` jest obecny w nowym projekcie, musi to być "15.0".

Praca tworzenia aplikacji odbywa się za pomocą elementów [docelowych](../msbuild/target-element-msbuild.md) i [zadań.](../msbuild/task-element-msbuild.md)

- Zadanie jest najmniejszą jednostką pracy, innymi słowy "atomem" kompilacji. Zadania są niezależnymi składnikami wykonywalnymi, które mogą mieć dane wejściowe i wyjściowe. W pliku projektu nie ma obecnie żadnych zadań, do których istnieją odwołania lub zdefiniowane. Zadania są dodawanye do pliku projektu w poniższych sekcjach. Aby uzyskać więcej informacji, zobacz temat [Zadania.](../msbuild/msbuild-tasks.md)

- Obiekt docelowy to nazwana sekwencja zadań. Aby uzyskać więcej informacji, zobacz temat [Obiekty docelowe.](../msbuild/msbuild-targets.md)
- [może to być nazwana sekwencja zadań, ale krytycznie, reprezentuje coś do zbudowania lub zrobienia, więc powinien być zdefiniowany w sposób zorientowany na cel]

Domyślny obiekt docelowy nie jest zdefiniowany w pliku projektu. Zamiast tego jest określony w importowanych projektach. Import [Import](../msbuild/import-element-msbuild.md) Element określa importowane projekty. Na przykład w projekcie języka C# domyślny obiekt docelowy jest importowany z pliku *Microsoft.CSharp.targets*.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

Importowane pliki są skutecznie wstawiane do pliku projektu, gdziekolwiek się do nie odwołują.

W projcts stylu SDK nie widać tego elementu importu, ponieważ atrybut SDK powoduje, że ten plik ma być importowany niejawnie.

MSBuild śledzi obiekty docelowe kompilacji i gwarantuje, że każdy obiekt docelowy jest zbudowany nie więcej niż jeden raz.

## <a name="add-a-target-and-a-task"></a>Dodawanie obiektu docelowego i zadania

 Dodaj obiekt docelowy do pliku projektu. Dodaj zadanie do obiektu docelowego, które drukuje wiadomość.

**Aby dodać obiekt docelowy i zadanie**

1. Dodaj te wiersze do pliku projektu, zaraz po instrukcji Importuj:

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

    Spowoduje to utworzenie obiektu docelowego o nazwie HelloWorld. Należy zauważyć, że masz obsługę IntelliSense podczas edytowania pliku projektu.

2. Dodaj wiersze do obiektu docelowego HelloWorld, tak aby wynikowa sekcja wyglądała następująco:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3. Zapisz plik projektu.

Message Zadanie jest jednym z wielu zadań, które są dostarczane z MSBuild. Aby uzyskać pełną listę dostępnych zadań i informacji o użytkowaniu, zobacz [Odwołanie do zadania](../msbuild/msbuild-task-reference.md).

Message Zadanie przyjmuje wartość ciągu text atrybutu jako dane wejściowe i wyświetla go na urządzeniu wyjściowym (lub zapisuje go do jednego lub więcej dzienników, jeśli dotyczy). Cel HelloWorld wykonuje zadanie Message dwa razy: najpierw wyświetlić "Hello", a następnie wyświetlić "Świat".

## <a name="build-the-target"></a>Zbuduj cel

Jeśli spróbujesz skompilować ten projekt z programu Visual Studio, nie będzie tworzyć cel, który został zdefiniowany. To dlatego, że Visual Studio wybiera domyślny obiekt docelowy, który jest nadal w pliku *.targets* importowane.

Uruchom MSBuild z **wiersza polecenia dewelopera** dla programu Visual Studio, aby utworzyć cel HelloWorld zdefiniowane powyżej. Użyj przełącznika wiersza polecenia -target lub -t, aby wybrać obiekt docelowy.

> [!NOTE]
> Będziemy odnosić się do **wiersza polecenia dewelopera** jako **okna polecenia** w poniższych sekcjach.

**Aby zbudować cel:**

1. Otwórz **okno polecenia**.

   (Windows 10) W polu wyszukiwania na pasku zadań zacznij wpisywać nazwę `dev` `developer command prompt`narzędzia, na przykład lub . Spowoduje to wyświetlenie listy zainstalowanych aplikacji, które pasują do wzorca wyszukiwania.

   Jeśli chcesz znaleźć go ręcznie, plik jest *LaunchDevCmd.bat* w *<visualstudio\>\<wersji folderu instalacyjnego>\Common7\Tools* folderu.

2. W oknie polecenia przejdź do folderu zawierającego plik projektu, w tym przypadku *D:\BuildApp\BuildApp.*

3. Uruchom msbuild za `-t:HelloWorld`pomocą przełącznika poleceń . Spowoduje to wybranie i zbudowanie celu HelloWorld:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Sprawdź dane wyjściowe w **oknie Polecenia**. Powinny być widoczne dwie linie "Hello" i "World":

    ```output
    Hello
    World
    ```

> [!NOTE]
> Jeśli zamiast tego `The target "HelloWorld" does not exist in the project` widzisz, prawdopodobnie zapomniałeś zapisać plik projektu w edytorze kodu. Zapisz plik i spróbuj ponownie.

 Zmieniając edytor kodu i okno polecenia, można zmienić plik projektu i szybko zobaczyć wyniki.

## <a name="build-properties"></a>Właściwości kompilacji

 Właściwości kompilacji są pary nazwa wartość, które prowadzą kompilacji. W górnej części pliku projektu zdefiniowano już kilka właściwości kompilacji:

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

 Wszystkie właściwości są elementami podrzędnymi propertygroup elementów. Nazwa właściwości jest nazwą elementu podrzędnego, a wartość właściwości jest elementem tekstowym elementu podrzędnego. Na przykład:

```xml
<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
```

 definiuje właściwość o nazwie TargetFrameworkVersion, nadając jej wartość ciągu "v4.5".

 Właściwości kompilacji mogą być ponownie zdefiniowane w dowolnym momencie. Jeśli użytkownik

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 pojawia się później w pliku projektu lub w pliku zaimportowanym później w pliku projektu, a następnie TargetFrameworkVersion przyjmuje nową wartość "v3.5".

## <a name="examine-a-property-value"></a>Sprawdzanie wartości właściwości

 Aby uzyskać wartość właściwości, należy użyć następującej `PropertyName` składni, gdzie jest nazwa właściwości:

```xml
$(PropertyName)
```

Ta składnia służy do badania niektórych właściwości w pliku projektu.

**Aby sprawdzić wartość właściwości**

1. Z edytora kodu zastąp cel HelloWorld tym kodem:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

1. Zapisz plik projektu.

1. Z **okna polecenia**wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Zbadaj dane wyjściowe. Powinny być widoczne te dwa wiersze (twoja wersja programu .NET Framework może się różnić):

    ::: moniker range=">=vs-2019"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2019\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end
    ::: moniker range="vs-2017"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end

### <a name="conditional-properties"></a>Właściwości warunkowe

Wiele właściwości, `Configuration` takich jak są zdefiniowane `Condition` warunkowo, oznacza to, że atrybut pojawia się w elemencie właściwości. Właściwości warunkowe są definiowane lub ponownie definiowane tylko wtedy, gdy warunek ma wartość "true". Należy zauważyć, że niezdefiniowane właściwości są podane domyślną wartość pustego ciągu. Na przykład:

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

oznacza "Jeśli właściwość Configuration nie została jeszcze zdefiniowana, zdefiniuj ją i nadaj jej wartość 'Debug'".

Prawie wszystkie elementy MSBuild może mieć Condition atrybut. Aby uzyskać więcej dyskusji na temat korzystania z atrybutu Condition, zobacz [Warunki](../msbuild/msbuild-conditions.md).

### <a name="reserved-properties"></a>Właściwości zarezerwowane

MSBuild zastrzega sobie niektóre nazwy właściwości do przechowywania informacji o pliku projektu i plikach binarnych MSBuild. MSBuildToolsPath jest przykładem właściwości zarezerwowane. Zastrzeżone właściwości są odwoływane z notacją $ jak każda inna właściwość. Aby uzyskać więcej informacji, zobacz [Jak: Odwoływać się do nazwy lub lokalizacji pliku projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) i [MSBuild zastrzeżonych i dobrze znanych właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md).

### <a name="environment-variables"></a>Zmienne środowiskowe

Zmienne środowiskowe w plikach projektu można odwoływać się w taki sam sposób, jak właściwości kompilacji. Na przykład, aby użyć zmiennej środowiskowej PATH w pliku projektu, użyj $(Path). Jeśli projekt zawiera definicję właściwości, która ma taką samą nazwę jak zmienna środowiskowa, właściwość w projekcie zastępuje wartość zmiennej środowiskowej. Aby uzyskać więcej informacji, zobacz [Jak: Używanie zmiennych środowiskowych w kompilacji](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Ustawianie właściwości z wiersza polecenia

Właściwości mogą być definiowane w wierszu polecenia za pomocą przełącznika wiersza polecenia -property lub -p. Wartości właściwości otrzymane z wiersza polecenia zastępują wartości właściwości ustawione w pliku projektu i zmiennych środowiskowych.

**Aby ustawić wartość właściwości z wiersza polecenia:**

1. Z **okna polecenia**wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

1. Zbadaj dane wyjściowe. Powinieneś zobaczyć ten wiersz:

    ```output
    Configuration is Release.
    ```

MSBuild tworzy Configuration właściwości i nadaje jej wartość "Release".

## <a name="special-characters"></a>Znaki specjalne

Niektóre znaki mają specjalne znaczenie w plikach projektu MSBuild. Przykładami tych znaków są średniki (;) i gwiazdki (*). Aby użyć tych znaków specjalnych jako literałów w pliku projektu, muszą być\<określone przy użyciu składni % xx>, gdzie \<xx> reprezentuje ascii szesnastkowej wartości znaku.

Zmień message zadanie, aby wyświetlić wartość Configuration właściwości ze znakami specjalnymi, aby uczynić go bardziej czytelnym.

**Aby użyć znaków specjalnych w zadaniu Wiadomość:**

1. Z edytora kodu zastąp oba zadania wiadomości tym wierszem:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

1. Zapisz plik projektu.

1. Z **okna polecenia**wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Zbadaj dane wyjściowe. Powinieneś zobaczyć ten wiersz:

    ```output
    $(Configuration) is "Debug"
    ```

Aby uzyskać więcej informacji, zobacz [MSBuild znaki specjalne](../msbuild/msbuild-special-characters.md).

## <a name="build-items"></a>Buduj przedmioty

Element jest fragmentem informacji, zazwyczaj nazwa pliku, który jest używany jako dane wejściowe do systemu kompilacji. Na przykład kolekcja elementów reprezentujących pliki źródłowe mogą być przekazywane do zadania o nazwie Compile do kompilacji ich do zestawu.

Wszystkie elementy są elementami podrzędnymi itemGroup elementów. Nazwa elementu jest nazwą elementu podrzędnego, a wartość elementu jest wartością atrybutu Include elementu podrzędnego. Wartości elementów o tej samej nazwie są zbierane do typów elementów o tej nazwie.  Na przykład:

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

definiuje grupę towarów zawierającą dwa elementy. Typ elementu Compile ma dwie wartości: *Program.cs* i *Właściwości\AssemblyInfo.cs*.

Poniższy kod tworzy ten sam typ elementu, deklarując oba pliki w jednym atrybutie Include, oddzielone średnikiem.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md).

> [!NOTE]
> Ścieżki plików są względem folderu zawierającego plik projektu MSBuild, nawet jeśli plik projektu jest importowanym plikiem projektu. Istnieje kilka wyjątków od tego, takich jak podczas korzystania [z importu](import-element-msbuild.md) i [usingTask](usingtask-element-msbuild.md) elementów.

## <a name="examine-item-type-values"></a>Sprawdzanie wartości typu towaru

 Aby uzyskać wartości typu elementu, należy użyć następującej składni, gdzie ItemType jest nazwą typu elementu:

```xml
@(ItemType)
```

Ta składnia służy do sprawdzania typu elementu kompilacji w pliku projektu.

**Aby sprawdzić wartości typu towaru:**

1. Z edytora kodu zastąp zadanie docelowe HelloWorld tym kodem:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

1. Zapisz plik projektu.

1. Z **okna polecenia**wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Zbadaj dane wyjściowe. Powinieneś zobaczyć tę długą linię:

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

Wartości typu towaru są domyślnie oddzielone średnikami.

Aby zmienić separator typu elementu, należy użyć następującej składni, gdzie ItemType jest typem elementu, a separator jest ciągiem jednego lub więcej znaków oddzielających:

```xml
@(ItemType, Separator)
```

Zmień zadanie Wiadomość, aby używać zwrotów karetki i kanałów informacyjnych wierszy (%0A%0D) do wyświetlania elementów kompilacji po jednym na wiersz.

**Aby wyświetlić wartości typu elementu po jednym na wiersz**

1. W edytorze kodu zastąp zadanie Wiadomość tym wierszem:

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2. Zapisz plik projektu.

3. Z **okna polecenia**wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zbadaj dane wyjściowe. Powinny być widoczne następujące wiersze:

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Uwzględnij, Wyklucz i symbole wieloznaczne

 Symbole wieloznaczne "*",\*\*" " i "?" z atrybutem Dołącz można dodawać elementy do typu elementu. Na przykład:

```xml
<Photos Include="images\*.jpeg" />
```

 dodaje wszystkie pliki z rozszerzeniem pliku *.jpeg* w folderze *obrazy* do typu elementu Zdjęcia,

```xml
<Photos Include="images\**\*.jpeg" />
```

 dodaje wszystkie pliki z rozszerzeniem pliku *.jpeg* w folderze *obrazów* i wszystkich jego podfolderach do typu elementu Zdjęcia. Aby uzyskać więcej przykładów, zobacz [Jak: Wybierz pliki do utworzenia](../msbuild/how-to-select-the-files-to-build.md).

 Należy zauważyć, że jako elementy są zadeklarowane są dodawane do typu towaru. Na przykład:

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 tworzy typ elementu o nazwie Zdjęcie zawierający wszystkie pliki w folderze *obrazów* z rozszerzeniem pliku *jpeg* lub *gif*. Jest to równoważne następującej linii:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Element można wykluczyć z typu elementu za pomocą atrybutu Wyklucz. Na przykład:

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 dodaje wszystkie pliki z rozszerzeniem pliku *.cs* do typu elementu Kompilacja, z wyjątkiem plików, których nazwy zawierają ciąg *Projektant*. Aby uzyskać więcej przykładów, zobacz [Jak: Wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).

Atrybut Wyklucz wpływa tylko na elementy dodane przez atrybut Include w elemencie elementu, który zawiera je oba. Na przykład:

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

nie wyklucza *pliku Form1.cs*, który został dodany w poprzednim elemencie elementu.

**Aby uwzględnić i wykluczyć elementy**

1. W edytorze kodu zastąp zadanie Wiadomość tym wierszem:

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2. Dodaj tę grupę elementów zaraz po elemencie importu:

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3. Zapisz plik projektu.

4. Z **okna polecenia**wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5. Zbadaj dane wyjściowe. Powinieneś zobaczyć ten wiersz:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Metadane elementu

 Elementy mogą zawierać metadane oprócz informacji zebranych z atrybutów Uwzględnij i Wyklucz. Te metadane mogą być używane przez zadania, które wymagają więcej informacji o elementach niż tylko wartość elementu.

 Metadane elementu jest zadeklarowany w pliku projektu przez utworzenie elementu o nazwie metadanych jako element podrzędny elementu. Element może mieć zero lub więcej wartości metadanych. Na przykład następujący element CSFile ma metadane kultury o wartości "Fr":

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Aby uzyskać wartość metadanych typu elementu, należy użyć następującej składni, gdzie ItemType jest nazwą typu elementu, a MetaDataName jest nazwą metadanych:

```xml
%(ItemType.MetaDataName)
```

**Aby sprawdzić metadane elementu:**

1. W edytorze kodu zastąp zadanie Wiadomość tym wierszem:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2. Zapisz plik projektu.

3. Z **okna polecenia**wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zbadaj dane wyjściowe. Powinny być widoczne następujące wiersze:

    ```output
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

Zwróć uwagę, jak wyrażenie "Compile.DependentUpon" pojawia się kilka razy. Użycie metadanych z tą składnią w obrębie obiektu docelowego powoduje "przetwarzanie wsadowe". Przetwarzanie wsadowe oznacza, że zadania w obrębie obiektu docelowego są wykonywane raz dla każdej unikatowej wartości metadanych. Jest to odpowiednik skryptu MSBuild wspólnej konstrukcji programowania "for loop". Aby uzyskać więcej informacji, zobacz [Batching](../msbuild/msbuild-batching.md).

### <a name="well-known-metadata"></a>Dobrze znane metadane

 Za każdym razem, gdy element jest dodawany do listy elementów, ten element jest przypisywany niektórych dobrze znanych metadanych. Na przykład wartość %(Nazwa pliku) zwraca nazwę pliku dowolnego elementu. Aby uzyskać pełną listę dobrze znanych metadanych, zobacz [Znane metadane elementu](../msbuild/msbuild-well-known-item-metadata.md).

**Aby zbadać dobrze znane metadane:**

1. W edytorze kodu zastąp zadanie Wiadomość tym wierszem:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2. Zapisz plik projektu.

3. Z **okna polecenia**wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zbadaj dane wyjściowe. Powinny być widoczne następujące wiersze:

    ```output
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

Porównując dwa powyższe przykłady, widać, że chociaż nie każdy element w typie elementu kompilacji ma metadane DependentUpon, wszystkie elementy mają dobrze znane metadane nazwy pliku.

### <a name="metadata-transformations"></a>Przekształcenia metadanych

 Listy elementów można przekształcić w nowe listy elementów. Aby przekształcić listę elementów, należy użyć \<następującej składni, gdzie ItemType> \<jest nazwą typu elementu i MetadataName> jest nazwą metadanych:

```xml
@(ItemType -> '%(MetadataName)')
```

Na przykład listę elementów plików źródłowych można przekształcić w zbiór `@(SourceFiles -> '%(Filename).obj')`plików obiektów przy użyciu wyrażenia typu . Aby uzyskać więcej informacji, zobacz [Przekształcenia](../msbuild/msbuild-transforms.md).

**Aby przekształcić elementy przy użyciu metadanych:**

1. W edytorze kodu zastąp zadanie Wiadomość tym wierszem:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2. Zapisz plik projektu.

3. Z **okna polecenia**wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zbadaj dane wyjściowe. Powinieneś zobaczyć ten wiersz:

    ```output
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Należy zauważyć, że metadane wyrażone w tej składni nie powoduje przetwarzania wsadowego.

## <a name="next-steps"></a>Następne kroki

 Aby dowiedzieć się, jak utworzyć prosty plik projektu krok po kroku, wypróbuj [przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie usługi MSBuild](../msbuild/msbuild.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
