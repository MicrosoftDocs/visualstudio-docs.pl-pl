---
title: Korzystanie z programu MSBuild
description: Poznaj różne części pliku projektu programu MSBuild, w tym elementy, metadane elementów, właściwości, elementy docelowe i zadania.
ms.date: 10/19/2020
ms.topic: conceptual
ms.custom: contperfq2
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b26c13765daf5a82a9961e6509b36e24e18f4e0c
ms.sourcegitcommit: 6b62e09026b6f1446187c905b789645f967a371c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2020
ms.locfileid: "92298546"
---
# <a name="walkthrough-use-msbuild"></a>Przewodnik: korzystanie z programu MSBuild

MSBuild to platforma kompilacji dla programu Microsoft i programu Visual Studio. Ten Instruktaż wprowadza do bloków konstrukcyjnych programu MSBuild i pokazuje, jak pisać, manipulować i debugować projekty MSBuild. Dowiesz się więcej na temat:

- Tworzenie pliku projektu i manipulowanie nim.

- Jak używać właściwości kompilacji

- Jak używać elementów kompilacji.

Program MSBuild można uruchomić z programu Visual Studio lub z **okna poleceń**. W tym instruktażu utworzysz plik projektu MSBuild przy użyciu programu Visual Studio. Można edytować plik projektu w programie Visual Studio i użyć **okna polecenia** do skompilowania projektu i przeanalizowania wyników.

## <a name="install-msbuild"></a>Instalowanie programu MSBuild

::: moniker range="vs-2017"

Jeśli masz program Visual Studio, masz już zainstalowany program MSBuild. Aby zainstalować program MSBuild 15 w systemie, który nie ma programu Visual Studio, przejdź do pozycji [Visual Studio starsze pliki do pobrania](https://visualstudio.microsoft.com/vs/older-downloads/), rozwiń **program Visual Studio 2017** i wybierz przycisk **Pobierz** . Jeśli masz subskrypcję programu Visual Studio, zaloguj się i Znajdź link, aby pobrać najnowszą wersję **narzędzi kompilacji dla programu Visual Studio 2017**. Jeśli nie masz subskrypcji programu Visual Studio, nadal możesz zainstalować najnowszą wersję narzędzi do kompilacji. Na tej stronie Użyj selektora wersji, aby przełączyć się na wersję 2019 strony i postępować zgodnie z instrukcjami instalacji.
::: moniker-end

::: moniker range="vs-2019"
Jeśli masz program Visual Studio, masz już zainstalowany program MSBuild. Program Visual Studio 2019 jest instalowany w folderze instalacyjnym programu Visual Studio. W przypadku typowej instalacji domyślnej w systemie Windows 10 MSBuild.exe znajduje się w folderze instalacji programu *MSBuild\Current\Bin*.

Aby zainstalować program MSBuild w systemie, który nie ma programu Visual Studio, przejdź do strony [pobieranie z programu Visual Studio](https://visualstudio.microsoft.com/downloads/) i przewiń w dół do pozycji **wszystkie pliki do pobrania**, a następnie rozwiń węzeł **narzędzia dla programu Visual Studio 2019**. Zainstaluj **narzędzia kompilacji dla programu Visual Studio 2019**, w tym MSBuild, lub zainstaluj [zestaw .NET Core SDK](/dotnet/core/sdk#acquiring-the-net-core-sdk).

W instalatorze upewnij się, że są zaznaczone narzędzia MSBuild dla używanych obciążeń, a następnie wybierz pozycję **Zainstaluj**.

![Instalowanie programu MSBuild](media/walkthrough-using-msbuild/installation-msbuild-tools.png)

::: moniker-end

## <a name="create-an-msbuild-project"></a>Tworzenie projektu MSBuild

 System projektu programu Visual Studio jest oparty na programie MSBuild. Dzięki temu można łatwo utworzyć nowy plik projektu przy użyciu programu Visual Studio. W tej sekcji utworzysz plik projektu Visual C#. Zamiast tego można utworzyć plik projektu Visual Basic. W kontekście tego instruktażu różnica między dwoma plikami projektu jest niewielka.

**Aby utworzyć plik projektu**

1. Otwórz program Visual Studio i Utwórz projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, wpisz **WinForms**, a następnie wybierz pozycję **utwórz nową aplikację Windows Forms (.NET Framework)**. W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.

    W polu **Nazwa** wpisz `BuildApp`. Wprowadź **lokalizację** rozwiązania, na przykład *D: \\ *. Zaakceptuj wartości domyślne dla **rozwiązania**, **nazwy rozwiązania** (**BuildApp**) i **struktury**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **Visual C#**  >  **Windows Desktop**, a następnie wybierz pozycję **Windows Forms App (.NET Framework)**. Następnie wybierz przycisk **OK**.

    W polu **Nazwa** wpisz `BuildApp`. Wprowadź **lokalizację** rozwiązania, na przykład *D: \\ *. Zaakceptuj wartości domyślne dla opcji **Utwórz katalog dla rozwiązania** (wybrane), **Dodaj do kontroli źródła** (nie wybrano) i **nazwę rozwiązania** (**BuildApp**).
    ::: moniker-end

1. Kliknij przycisk **OK** lub **Utwórz** , aby utworzyć plik projektu.

## <a name="examine-the-project-file"></a>Badanie pliku projektu

 W poprzedniej sekcji użyto programu Visual Studio do utworzenia pliku projektu Visual C#. Plik projektu jest reprezentowany w **Eksplorator rozwiązań** przez węzeł projektu o nazwie BuildApp. Aby przejrzeć plik projektu, można użyć edytora kodu programu Visual Studio.

**Aby przejrzeć plik projektu**

1. W **Eksplorator rozwiązań**kliknij węzeł projektu **BuildApp**.

1. W przeglądarce **Właściwości** należy zauważyć, że właściwość **pliku projektu** to *BuildApp. csproj*. Wszystkie pliki projektu mają nazwę z elementem *proj*. Jeśli utworzono projekt Visual Basic, nazwa pliku projektu byłaby *BuildApp. vbproj*.

1. Ponownie kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij polecenie **Edytuj BuildApp. csproj**. 

     Plik projektu pojawi się w edytorze kodu.

>[!NOTE]
> W przypadku niektórych typów projektów, takich jak C++, należy zwolnić projekt (kliknij prawym przyciskiem myszy plik projektu i wybierz polecenie **Zwolnij projekt**), aby móc otwierać i edytować plik projektu.

## <a name="targets-and-tasks"></a>Cele i zadania

Pliki projektu są plikami w formacie XML z [projektem](../msbuild/project-element-msbuild.md)węzła głównego.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Nowsze projekty platformy .NET Core (zestaw SDK) mają `Sdk` atrybut.

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Jeśli projekt nie jest projektem w stylu zestawu SDK, należy określić przestrzeń nazw xmlns w elemencie projektu. Jeśli `ToolsVersion` jest obecny w nowym projekcie, musi to być "15,0".

Prace nad tworzeniem aplikacji są wykonywane z elementami [docelowymi](../msbuild/target-element-msbuild.md) i [zadaniami](../msbuild/task-element-msbuild.md) .

- Zadanie jest najmniejszą jednostką pracy, innymi słowy, "atom" kompilacji. Zadania są niezależnymi składnikami wykonywalnymi, które mogą mieć dane wejściowe i wyjściowe. W pliku projektu nie ma aktualnie przywoływanych zadań ani ich nie zdefiniowano. Do pliku projektu można dodać zadania w poniższych sekcjach. Aby uzyskać więcej informacji, zobacz temat [zadania](../msbuild/msbuild-tasks.md) .

- Obiekt docelowy jest nazwaną sekwencją zadań. Aby uzyskać więcej informacji, zobacz temat [targets](../msbuild/msbuild-targets.md) .
- [może to być nazwana sekwencja zadań, ale w sposób krytyczny reprezentuje coś do skompilowania lub wykonania, dlatego należy je zdefiniować w sposób zorientowany na cele]

Domyślny element docelowy nie jest zdefiniowany w pliku projektu. Zamiast tego jest określony w importowanych projektach. Element [Import](../msbuild/import-element-msbuild.md) określa importowane projekty. Na przykład w projekcie w języku C# domyślny element docelowy jest importowany z pliku *Microsoft. CSharp. targets*.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

Importowane pliki są efektywnie umieszczane w pliku projektu wszędzie tam, gdzie się znajdują.

W projektach w stylu zestawu SDK nie widzisz tego elementu importowania, ponieważ atrybut SDK powoduje, że ten plik zostanie zaimportowany niejawnie.

Program MSBuild śledzi elementy docelowe kompilacji i gwarantuje, że każdy element docelowy nie jest zbudowany więcej niż raz.

## <a name="add-a-target-and-a-task"></a>Dodawanie obiektu docelowego i zadania

 Dodaj element docelowy do pliku projektu. Dodaj zadanie do obiektu docelowego, które drukuje komunikat.

**Aby dodać obiekt docelowy i zadanie**

1. Dodaj te wiersze do pliku projektu zaraz po instrukcji import:

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

    Spowoduje to utworzenie obiektu docelowego o nazwie HelloWorld. Należy zauważyć, że obsługa IntelliSense jest obsługiwana podczas edytowania pliku projektu.

2. Dodaj wiersze do elementu docelowego HelloWorld, aby sekcja wynikowa wyglądała następująco:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3. Zapisz plik projektu.

Zadanie jest jednym z wielu zadań, które są dostarczane z programem MSBuild. Aby uzyskać pełną listę dostępnych zadań i informacji o użyciu, zobacz [Dokumentacja zadania](../msbuild/msbuild-task-reference.md).

Zadanie przyjmuje wartość ciągu atrybutu Text jako dane wejściowe i wyświetla je na urządzeniu wyjściowym (lub zapisuje je w co najmniej jednym dzienniku, jeśli ma zastosowanie). Obiekt docelowy HelloWorld wykonuje zadanie komunikatu dwa razy: najpierw, aby wyświetlić "Hello", a następnie wyświetlić "World".

## <a name="build-the-target"></a>Kompilowanie elementu docelowego

Próba skompilowania projektu z programu Visual Studio nie spowoduje skompilowania zdefiniowanego obiektu docelowego. Dzieje się tak, ponieważ program Visual Studio wybiera domyślny element docelowy, który jest nadal używany w zaimportowanym pliku *targets* .

Uruchom program MSBuild z **wiersz polecenia dla deweloperów** programu Visual Studio, aby utworzyć element docelowy HelloWorld zdefiniowany powyżej. Użyj przełącznika wiersza polecenia-Target lub-t, aby wybrać element docelowy.

> [!NOTE]
> Odwołujemy się do **wiersz polecenia dla deweloperów** jako **okna poleceń** w poniższych sekcjach.

**Aby skompilować obiekt docelowy:**

1. Otwórz **okno wiersza polecenia**.

   (System Windows 10) W polu wyszukiwania na pasku zadań Zacznij wpisywać nazwę narzędzia, na przykład `dev` lub `developer command prompt` . Spowoduje to wyświetlenie listy zainstalowanych aplikacji, które pasują do Twojego wzorca wyszukiwania.

   Jeśli chcesz je znaleźć ręcznie, plik jest *LaunchDevCmd.bat* w folderze *<VisualStudio instalacyjny folder \> \<version> \Common7\Tools* .

2. W oknie polecenia przejdź do folderu zawierającego plik projektu, w tym przypadku *D:\BuildApp\BuildApp*.

3. Uruchom narzędzie MSBuild przy użyciu przełącznika polecenia `-t:HelloWorld` . Spowoduje to wybranie i kompilację elementu docelowego HelloWorld:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Przejrzyj dane wyjściowe w **okno polecenie**. Powinny być widoczne dwie linie "Hello" i "World":

    ```output
    Hello
    World
    ```

> [!NOTE]
> Jeśli zamiast tego zobaczysz, `The target "HelloWorld" does not exist in the project` prawdopodobnie zapomniano zapisać plik projektu w edytorze kodu. Zapisz plik i spróbuj ponownie.

 Przez przemienne między edytorem kodu a oknem polecenia można zmienić plik projektu i szybko zobaczyć wyniki.

## <a name="build-properties"></a>Właściwości kompilacji

 Właściwości kompilacji to pary nazwa-wartość, które kierują kompilację. Kilka właściwości kompilacji jest już zdefiniowanych u góry pliku projektu:

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

 Wszystkie właściwości są elementami podrzędnymi elementów właściwości. Nazwa właściwości jest nazwą elementu podrzędnego, a wartość właściwości jest element tekstowy elementu podrzędnego. Przykład:

```xml
<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
```

 definiuje właściwość o nazwie TargetFrameworkVersion, podając ją jako wartość ciągu "v 4.5".

 Właściwości kompilacji można ponownie zdefiniować w dowolnym momencie. Jeśli użytkownik

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 pojawia się w dalszej części pliku projektu lub w pliku zaimportowanego później w pliku projektu, a następnie TargetFrameworkVersion przyjmuje nową wartość "v 3.5".

## <a name="examine-a-property-value"></a>Sprawdzanie wartości właściwości

 Aby uzyskać wartość właściwości, należy użyć następującej składni, gdzie `PropertyName` jest nazwą właściwości:

```xml
$(PropertyName)
```

Użyj tej składni do sprawdzenia niektórych właściwości w pliku projektu.

**Aby przejrzeć wartość właściwości**

1. W edytorze kodu Zastąp element docelowy HelloWorld tym kodem:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

1. Zapisz plik projektu.

1. W **oknie polecenia**wpisz i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Sprawdź dane wyjściowe. Powinny być widoczne te dwie linie (wersja .NET Framework może się różnić):

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

Wiele właściwości, takich jak `Configuration` są zdefiniowane warunkowo, to oznacza, że `Condition` atrybut jest wyświetlany w elemencie właściwości. Właściwości warunkowe są zdefiniowane lub definiowane ponownie tylko wtedy, gdy warunek ma wartość "true". Należy zauważyć, że niezdefiniowane właściwości otrzymują wartość domyślną pustego ciągu. Przykład:

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

oznacza "Jeśli nie zdefiniowano jeszcze właściwości konfiguracji, zdefiniuj ją i nadaj jej wartość" debug ".

Prawie wszystkie elementy MSBuild mogą mieć atrybut Condition. Aby uzyskać więcej informacji na temat używania atrybutu Condition, zobacz [warunki](../msbuild/msbuild-conditions.md).

### <a name="reserved-properties"></a>Właściwości zastrzeżone

Program MSBuild rezerwuje nazwy właściwości w celu przechowywania informacji o pliku projektu i plikach binarnych programu MSBuild. MSBuildToolsPath jest przykładem zastrzeżonej właściwości. Właściwości zastrzeżone są przywoływane w notacji $, podobnie jak każda inna właściwość. Aby uzyskać więcej informacji, zobacz [jak: odwoływanie się do nazwy lub lokalizacji pliku projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) oraz [Właściwości zastrzeżonych i dobrze znanych programu MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

### <a name="environment-variables"></a>Zmienne środowiskowe

Można odwoływać się do zmiennych środowiskowych w plikach projektu w taki sam sposób, jak właściwości kompilacji. Na przykład, aby użyć zmiennej środowiskowej PATH w pliku projektu, należy użyć $ (Path). Jeśli projekt zawiera definicję właściwości, która ma taką samą nazwę jak zmienna środowiskowa, właściwość w projekcie przesłania wartość zmiennej środowiskowej. Aby uzyskać więcej informacji, zobacz [jak: używać zmiennych środowiskowych w kompilacji](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Ustawianie właściwości z wiersza polecenia

Właściwości można definiować w wierszu polecenia przy użyciu przełącznika wiersza polecenia-property lub-p. Wartości właściwości odebrane z wartości właściwości Zastąp wiersz polecenia ustawionymi w pliku projektu i zmiennych środowiskowych.

**Aby ustawić wartość właściwości z wiersza polecenia:**

1. W **oknie polecenia**wpisz i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

1. Sprawdź dane wyjściowe. Powinien zostać wyświetlony następujący wiersz:

    ```output
    Configuration is Release.
    ```

Program MSBuild tworzy właściwość Configuration i nadaje jej wartość "Release".

## <a name="special-characters"></a>Znaki specjalne

Niektóre znaki mają specjalne znaczenie w plikach projektu MSBuild. Przykłady tych znaków obejmują średniki (;) i gwiazdki (*). Aby można było używać tych znaków specjalnych jako literałów w pliku projektu, muszą one być określone przy użyciu składni% \<xx> , gdzie \<xx> reprezentuje wartość szesnastkową ASCII znaku.

Zmień zadanie, aby wyświetlić wartość właściwości Configuration ze znakami specjalnymi, aby zwiększyć czytelność.

**Aby użyć znaków specjalnych w zadaniu komunikatu:**

1. W edytorze kodu Zastąp oba zadania komunikatów tym wierszem:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

1. Zapisz plik projektu.

1. W **oknie polecenia**wpisz i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Sprawdź dane wyjściowe. Powinien zostać wyświetlony następujący wiersz:

    ```output
    $(Configuration) is "Debug"
    ```

Aby uzyskać więcej informacji, zobacz [znaki specjalne programu MSBuild](../msbuild/msbuild-special-characters.md).

## <a name="build-items"></a>Kompiluj elementy

Element jest częścią informacji, zazwyczaj nazwą pliku, która jest używana jako dane wejściowe systemu kompilacji. Na przykład Kolekcja elementów reprezentujących pliki źródłowe może zostać przeniesiona do zadania o nazwie Kompiluj, aby skompilować je do zestawu.

Wszystkie elementy są elementami podrzędnymi elementów Item. Nazwa elementu jest nazwą elementu podrzędnego, a wartość elementu jest wartością atrybutu Include elementu podrzędnego. Wartości elementów o tej samej nazwie są zbierane w typach elementów o tej samej nazwie.  Przykład:

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

definiuje grupę elementów zawierającą dwa elementy. Kompilacja typu elementu ma dwie wartości: *program.cs* i *Properties\AssemblyInfo.cs*.

Poniższy kod tworzy ten sam typ elementu przez zadeklarowanie obu plików w jednym atrybucie include, rozdzielone średnikami.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).

> [!NOTE]
> Ścieżki plików są względne wobec folderu zawierającego plik projektu programu MSBuild, nawet jeśli plik projektu jest zaimportowanym plikiem projektu. Istnieje kilka wyjątków, na przykład w przypadku używania elementów [Import](import-element-msbuild.md) i [UsingTask](usingtask-element-msbuild.md) .

## <a name="examine-item-type-values"></a>Badanie wartości typu elementu

 Aby uzyskać wartości typu elementu, użyj następującej składni, gdzie ItemType jest nazwą typu elementu:

```xml
@(ItemType)
```

Użyj tej składni, aby przeanalizować typ elementu kompilacji w pliku projektu.

**Aby przejrzeć wartości typu elementu:**

1. W edytorze kodu Zastąp zadanie docelowe HelloWorld tym kodem:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

1. Zapisz plik projektu.

1. W **oknie polecenia**wpisz i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Sprawdź dane wyjściowe. Powinna zostać wyświetlona linia długa:

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

Wartości typu elementu są domyślnie oddzielone średnikami.

Aby zmienić separator typu elementu, użyj następującej składni, gdzie ItemType jest typem elementu, a separatorem jest ciąg składający się z co najmniej jednego rozdzielającego znaku:

```xml
@(ItemType, Separator)
```

Zmień zadanie, aby użyć powrotu karetki i wysuwu wiersza (% 0A% 0D), aby wyświetlić elementy kompilacji jeden na wiersz.

**Aby wyświetlić wartości typu elementu jeden na wiersz**

1. W edytorze kodu Zastąp zadanie komunikatu tym wierszem:

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2. Zapisz plik projektu.

3. W **oknie polecenia**wpisz i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

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

```xml
<Photos Include="images\*.jpeg" />
```

 dodaje wszystkie pliki z rozszerzeniem pliku *JPEG* w folderze *obrazy* do typu elementu zdjęcia, podczas gdy

```xml
<Photos Include="images\**\*.jpeg" />
```

 dodaje wszystkie pliki z rozszerzeniem pliku *JPEG* w folderze *obrazy* i wszystkie jego podfoldery do typu elementu zdjęcia. Aby uzyskać więcej przykładów, zobacz [jak to zrobić: Wybierz pliki do skompilowania](../msbuild/how-to-select-the-files-to-build.md).

 Zwróć uwagę, że jako że elementy są deklarowane, są dodawane do typu elementu. Przykład:

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 Tworzy typ elementu o nazwie Photo zawierający wszystkie pliki w folderze *images* z rozszerzeniem pliku *JPEG* lub *GIF*. Jest to równoznaczne z następującym wierszem:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Można wykluczyć element z typu elementu z atrybutem Exclude. Przykład:

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 dodaje wszystkie pliki z rozszerzeniem pliku *CS* do typu elementu kompilacji, z wyjątkiem plików, których nazwy zawierają *projektanta*ciągów. Aby uzyskać więcej przykładów, zobacz [How to: wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).

Atrybut Exclude ma wpływ tylko na elementy dodane przez atrybut Include w elemencie Item, który je zawiera. Przykład:

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

nie wykluczają *Form1.cs*pliku, który został dodany w poprzednim elemencie elementu.

**Aby uwzględnić i wykluczyć elementy**

1. W edytorze kodu Zastąp zadanie komunikatu tym wierszem:

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2. Dodaj tę grupę elementów tuż po elemencie import:

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3. Zapisz plik projektu.

4. W **oknie polecenia**wpisz i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5. Sprawdź dane wyjściowe. Powinien zostać wyświetlony następujący wiersz:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Metadane elementu

 Elementy mogą zawierać metadane oprócz informacji zebranych z atrybutów dołączania i wykluczania. Te metadane mogą być używane przez zadania, które wymagają więcej informacji o elementach niż tylko wartość elementu.

 Metadane elementu są zadeklarowane w pliku projektu przez utworzenie elementu o nazwie metadanych jako elementu podrzędnego elementu. Element może mieć zero lub więcej wartości metadanych. Na przykład następujący element CSFile ma metadane kultury o wartości "fr":

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Aby uzyskać wartość metadanych typu elementu, należy użyć następującej składni, gdzie ItemType jest nazwą typu elementu, a metadataname jest nazwą metadanych:

```xml
%(ItemType.MetaDataName)
```

**Aby przeanalizować metadane elementu:**

1. W edytorze kodu Zastąp zadanie komunikatu tym wierszem:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2. Zapisz plik projektu.

3. W **oknie polecenia**wpisz i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Sprawdź dane wyjściowe. Powinny zostać wyświetlone następujące wiersze:

    ```output
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

Zwróć uwagę, jak fraza "Kompiluj. DependentUpon" występuje kilka razy. Użycie metadanych o tej składni w elemencie docelowym powoduje wystąpienie "wsadowe". Przetwarzanie wsadowe oznacza, że zadania w ramach elementu docelowego są wykonywane raz dla każdej unikatowej wartości metadanych. Jest to odpowiednik skryptu programu MSBuild w typowej konstrukcji programowania "pętla for". Aby uzyskać więcej informacji, zobacz Tworzenie [pakietów wsadowych](../msbuild/msbuild-batching.md).

### <a name="well-known-metadata"></a>Dobrze znane metadane

 Za każdym razem, gdy element zostanie dodany do listy elementów, do tego elementu są przypisane pewne dobrze znane metadane. Na przykład,% (filename) zwraca nazwę pliku dowolnego elementu. Aby uzyskać pełną listę dobrze znanych metadanych, zobacz [dobrze znane metadane elementu](../msbuild/msbuild-well-known-item-metadata.md).

**Aby sprawdzać dobrze znane metadane:**

1. W edytorze kodu Zastąp zadanie komunikatu tym wierszem:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2. Zapisz plik projektu.

3. W **oknie polecenia**wpisz i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Sprawdź dane wyjściowe. Powinny zostać wyświetlone następujące wiersze:

    ```output
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

Porównując dwa przykłady powyżej, można zobaczyć, że chociaż nie każdy element w typie elementu kompilacji ma metadane DependentUpon, wszystkie elementy mają dobrze znane metadane filename.

### <a name="metadata-transformations"></a>Przekształcenia metadanych

 Listy elementów mogą być przekształcane na listy nowych elementów. Aby przekształcić listę elementów, użyj następującej składni, gdzie \<ItemType> jest nazwą typu elementu i \<MetadataName> jest nazwą metadanych:

```xml
@(ItemType -> '%(MetadataName)')
```

Na przykład lista elementów plików źródłowych może być przekształcana do kolekcji plików obiektów przy użyciu wyrażenia takiego jak `@(SourceFiles -> '%(Filename).obj')` . Aby uzyskać więcej informacji, zobacz [transformacje](../msbuild/msbuild-transforms.md).

**Aby przekształcić elementy przy użyciu metadanych:**

1. W edytorze kodu Zastąp zadanie komunikatu tym wierszem:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2. Zapisz plik projektu.

3. W **oknie polecenia**wpisz i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Sprawdź dane wyjściowe. Powinien zostać wyświetlony następujący wiersz:

    ```output
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Zwróć uwagę, że metadane wyrażone w tej składni nie powodują przetwarzania wsadowego.

## <a name="next-steps"></a>Następne kroki

 Aby dowiedzieć się, jak utworzyć prosty plik projektu w jednym kroku, wypróbuj [Przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie programu MSBuild](../msbuild/msbuild.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
