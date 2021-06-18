---
title: Korzystanie z programu MSBuild
description: Poznaj różne części pliku projektu MSBuild, w tym elementy, metadane elementów, właściwości, elementy docelowe i zadania.
ms.date: 10/19/2020
ms.topic: conceptual
ms.custom: contperf-fy21q2
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e3a301c1bd4758ea08f49036fcf8756c8d7e7c26
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306452"
---
# <a name="walkthrough-use-msbuild"></a>Przewodnik: korzystanie z programu MSBuild

MSBuild to platforma kompilacji dla firmy Microsoft i Visual Studio. Ten przewodnik stanowi wprowadzenie do bloków konstrukcyjnych programu MSBuild i pokazuje, jak pisać, manipulować i debugować projekty MSBuild. Dowiesz się więcej na temat:

- Tworzenie pliku projektu i manipulowanie nim.

- Jak używać właściwości kompilacji

- Jak używać elementów kompilacji.

Program MSBuild można uruchomić Visual Studio lub w **oknie polecenia**. W tym przewodniku utworzysz plik projektu MSBuild przy użyciu Visual Studio. Plik projektu można edytować w Visual Studio,  a następnie użyć okna polecenia do skompilowania projektu i zbadania wyników.

## <a name="install-msbuild"></a>Instalowanie programu MSBuild

::: moniker range="vs-2017"

Jeśli masz już Visual Studio, masz już zainstalowany program MSBuild. Aby zainstalować program MSBuild 15 w systemie, który nie ma programu Visual Studio, przejdź do strony Visual Studio [starszych](https://visualstudio.microsoft.com/vs/older-downloads/)plików do pobrania, rozwiń pozycję **Visual Studio 2017** i wybierz przycisk **Pobierz.** Jeśli masz subskrypcję Visual Studio, zaloguj się i znajdź link, aby pobrać najnowszą wersję narzędzi **Build Tools for Visual Studio 2017.** Jeśli nie masz subskrypcji Visual Studio, nadal możesz zainstalować najnowszą wersję narzędzi kompilacji. Na tej stronie użyj selektora wersji, aby przełączyć się na wersję 2019 strony i postępować zgodnie z instrukcjami instalacji.
::: moniker-end

::: moniker range=">=vs-2019"
Jeśli masz już Visual Studio, masz już zainstalowany program MSBuild. W Visual Studio 2019 r. i nowszych jest on instalowany w folderze Visual Studio instalacji. W przypadku typowej instalacji domyślnej na Windows 10 MSBuild.exe znajduje się w folderze instalacyjnym w *folderze MSBuild\Current\Bin.*

Aby zainstalować program MSBuild w systemie, który nie ma programu Visual Studio, przejdź do strony Visual Studio [downloads (Pliki](https://visualstudio.microsoft.com/downloads/) do pobrania) i przewiń w dół do sekcji **Wszystkie** pliki do pobrania, a następnie rozwiń pozycję Tools for Visual Studio Visual Studio 2019 (Narzędzia dla programu **Visual Studio 2019).** Zainstaluj **narzędzia Build Tools for Visual Studio 2019,** które obejmują program MSBuild, lub zainstaluj [zestaw .NET Core SDK](/dotnet/core/sdk#acquiring-the-net-core-sdk).

W instalatorze upewnij się, że wybrano narzędzia MSBuild dla obciążeń, których używasz, a następnie wybierz pozycję **Zainstaluj.**

![Instalowanie programu MSBuild](media/walkthrough-using-msbuild/installation-msbuild-tools.png)

::: moniker-end

## <a name="create-an-msbuild-project"></a>Tworzenie projektu MSBuild

 System Visual Studio jest oparty na programie MSBuild. Ułatwia to tworzenie nowego pliku projektu przy użyciu Visual Studio. W tej sekcji utworzysz plik projektu Visual C#. Zamiast tego możesz utworzyć Visual Basic projektu. W kontekście tego przewodnika różnica między dwoma plikami projektu jest niewielka.

**Aby utworzyć plik projektu**

1. Otwórz Visual Studio i utwórz projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno uruchamiania. Naciśnij **klawisze Ctrl +Q,** aby otworzyć pole wyszukiwania, wpisz **winforms,** a następnie wybierz pozycję **Utwórz nową aplikację Windows Forms aplikacji (.NET Framework).** W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.

    W polu **Nazwa** wpisz `BuildApp`. Wprowadź **lokalizację** rozwiązania, na przykład *D: \\*. Zaakceptuj wartości domyślne dla **rozwiązania,** **nazwy rozwiązania** **(BuildApp)** i **struktury**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).** W lewym okienku okna dialogowego **Nowy** projekt rozwiń pozycję **Visual C#** Windows Desktop, a następnie wybierz  >  pozycję Windows Forms App **(.NET Framework).** Następnie wybierz przycisk **OK.**

    W polu **Nazwa** wpisz `BuildApp`. Wprowadź **lokalizację** rozwiązania, na przykład *D: \\*. Zaakceptuj wartości domyślne dla opcji **Utwórz katalog dla** rozwiązania (wybrane), Dodaj do **kontroli** źródła (nie zaznaczono) i **Nazwa rozwiązania** **(BuildApp).**
    ::: moniker-end

1. Kliknij **przycisk OK** lub **Utwórz,** aby utworzyć plik projektu.

## <a name="examine-the-project-file"></a>Badanie pliku projektu

 W poprzedniej sekcji utworzyliśmy plik Visual Studio Visual C#. Plik projektu jest reprezentowany w **Eksplorator rozwiązań** projektu o nazwie BuildApp. Możesz użyć edytora Visual Studio kodu, aby zbadać plik projektu.

**Aby zbadać plik projektu**

1. W **Eksplorator rozwiązań** kliknij węzeł projektu **BuildApp.**

1. W przeglądarce **Właściwości** zwróć uwagę, że właściwość **Project File** to *BuildApp.csproj.* Wszystkie pliki projektu mają nazwy z sufiksem *proj*. Jeśli utworzono projekt Visual Basic, nazwą pliku projektu będzie *BuildApp.vbproj.*

1. Ponownie kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij **polecenie Edytuj kompilacjęApp.csproj.** 

     Plik projektu zostanie wyświetlony w edytorze kodu.

>[!NOTE]
> W przypadku niektórych typów projektów, takich jak C++, należy zwolnić projekt (kliknąć prawym przyciskiem myszy plik projektu i wybrać polecenie **Zwolnij** projekt ), aby można było otworzyć i edytować plik projektu.

## <a name="targets-and-tasks"></a>Obiekty docelowe i zadania

Pliki projektu to pliki w formacie XML z węzłem głównym [Project](../msbuild/project-element-msbuild.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Nowsze projekty platformy .NET Core (w stylu zestawu SDK) mają `Sdk` atrybut .

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Jeśli projekt nie jest projektem w stylu zestawu SDK, należy określić przestrzeń nazw xmlns w elemencie Project. Jeśli `ToolsVersion` jest obecny w nowym projekcie, musi to być "15.0".

Tworzenie aplikacji odbywa się przy użyciu elementów [docelowych](../msbuild/target-element-msbuild.md) [i](../msbuild/task-element-msbuild.md) zadań.

- Zadanie to najmniejsza jednostka pracy, czyli "atom" kompilacji. Zadania są niezależnymi składnikami wykonywalnymi, które mogą mieć dane wejściowe i wyjściowe. Obecnie w pliku projektu nie ma żadnych zadań, do których się odwoływuje ani które zostały zdefiniowane. Zadania można dodać do pliku projektu w poniższych sekcjach. Aby uzyskać więcej informacji, zobacz [temat Zadania.](../msbuild/msbuild-tasks.md)

- Element docelowy to nazwana sekwencja zadań. Aby uzyskać więcej informacji, zobacz [temat Targets (Cele).](../msbuild/msbuild-targets.md)
- [Może to być nazwana sekwencja zadań, ale w krytycznym znaczeniu reprezentuje coś do sytowania lub wykonania, więc powinna być zdefiniowana w sposób ukierunkowany na cel]

Domyślny element docelowy nie jest zdefiniowany w pliku projektu. Zamiast tego jest on określony w importowanych projektach. Import [element](../msbuild/import-element-msbuild.md) określa importowane projekty. Na przykład w projekcie języka C# domyślny element docelowy jest importowany z pliku *Microsoft.CSharp.targets.*

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

Zaimportowane pliki są skutecznie wstawiane do pliku projektu wszędzie tam, gdzie się do nich odwołujesz.

W projektach w stylu zestawu SDK ten element importu nie jest wyświetlony, ponieważ atrybut SDK powoduje niejawne zaimportowanie tego pliku.

Program MSBuild śledzi cele kompilacji i gwarantuje, że każdy obiekt docelowy zostanie skompilowany nie więcej niż raz.

## <a name="add-a-target-and-a-task"></a>Dodawanie obiektu docelowego i zadania

 Dodaj element docelowy do pliku projektu. Dodaj zadanie do obiektu docelowego, które wypisuje komunikat.

**Aby dodać element docelowy i zadanie**

1. Dodaj następujące wiersze do pliku projektu tuż po instrukcji Import:

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

    Powoduje to utworzenie obiektu docelowego o nazwie HelloWorld. Zwróć uwagę, że masz obsługę funkcji IntelliSense podczas edytowania pliku projektu.

2. Dodaj wiersze do obiektu docelowego HelloWorld, aby wynikowa sekcja wyglądała następująco:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3. Zapisz plik projektu.

Zadanie Komunikat jest jednym z wielu zadań dostarczanych z programem MSBuild. Aby uzyskać pełną listę dostępnych zadań i informacji o użyciu, zobacz [Task reference](../msbuild/msbuild-task-reference.md).

Zadanie Komunikat przyjmuje wartość ciągu atrybutu Text jako dane wejściowe i wyświetla ją na urządzeniu wyjściowym (lub zapisuje ją w co najmniej jednym dziennikiem, jeśli ma to zastosowanie). Obiekt docelowy HelloWorld wykonuje zadanie Message dwa razy: najpierw wyświetla "Hello", a następnie wyświetla "World".

## <a name="build-the-target"></a>Kompilowanie obiektu docelowego

Próba skompilowania tego projektu na Visual Studio nie spowoduje skompilowania zdefiniowanego obiektu docelowego. Wynika to z Visual Studio domyślnego obiektu docelowego, który nadal znajduje się w zaimportowaniu *pliku targets.*

Uruchom program MSBuild z **wiersz polecenia dla deweloperów** for Visual Studio, aby utworzyć zdefiniowany powyżej obiekt docelowy HelloWorld. Użyj przełącznika wiersza polecenia -target lub -t, aby wybrać element docelowy.

> [!NOTE]
> W poniższych sekcjach **wiersz polecenia dla deweloperów** to **okno** poleceń.

**Aby skompilować element docelowy:**

1. Otwórz **okno polecenia**.

   (Windows 10) W polu wyszukiwania na pasku zadań rozpocznij wpisywanie nazwy narzędzia, takiej jak `dev` lub `developer command prompt` . Zostanie wyświetlona lista zainstalowanych aplikacji, które pasują do wzorca wyszukiwania.

   Jeśli musisz znaleźć go ręcznie, plik  zostanieLaunchDevCmd.batw folderze instalacyjnym<*visualstudio \> \<version> \Common7\Tools.*

2. W oknie polecenia przejdź do folderu zawierającego plik projektu, w tym przypadku *D:\BuildApp\BuildApp.*

3. Uruchom program msbuild za pomocą przełącznika poleceń `-t:HelloWorld` . W ten sposób zostanie wybrane i skompilowane miejsce docelowe HelloWorld:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Sprawdź dane wyjściowe w **okno Polecenie**. Powinny zostać wyświetlony dwa wiersze "Hello" i "World":

    ```output
    Hello
    World
    ```

> [!NOTE]
> Jeśli zamiast tego `The target "HelloWorld" does not exist in the project` zobaczysz, prawdopodobnie nie pamiętasz zapisać pliku projektu w edytorze kodu. Zapisz plik i spróbuj ponownie.

 Naprzemiennie między edytorem kodu i oknem polecenia możesz zmienić plik projektu i szybko wyświetlić wyniki.

## <a name="build-properties"></a>Właściwości kompilacji

 Właściwości kompilacji to pary nazwa-wartość, które są przewodnikami kompilacji. W górnej części pliku projektu zdefiniowano już kilka właściwości kompilacji:

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

 Wszystkie właściwości są elementami podrzędnymi elementów PropertyGroup. Nazwa właściwości jest nazwą elementu podrzędnego, a wartość właściwości jest elementem tekstowym elementu podrzędnego. Na przykład

```xml
<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
```

 Definiuje właściwość o nazwie TargetFrameworkVersion, nadając jej wartość ciągu "v4.5".

 Właściwości kompilacji mogą być ponownie definiowane w dowolnym momencie. Jeśli użytkownik

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 Pojawia się później w pliku projektu lub w pliku zaimportowany później w pliku projektu, a następnie TargetFrameworkVersion przyjmuje nową wartość "v3.5".

## <a name="examine-a-property-value"></a>Badanie wartości właściwości

 Aby uzyskać wartość właściwości, użyj następującej składni, gdzie `PropertyName` to nazwa właściwości:

```xml
$(PropertyName)
```

Użyj tej składni, aby sprawdzić niektóre właściwości w pliku projektu.

**Aby sprawdzić wartość właściwości**

1. W edytorze kodu zastąp element docelowy HelloWorld tym kodem:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

1. Zapisz plik projektu.

1. W **oknie polecenia** wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Sprawdź dane wyjściowe. Powinny zostać wyświetlony te dwa wiersze (twoja .NET Framework wersja może się różnić):

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

Wiele właściwości, takich jak , `Configuration` jest definiowanych warunkowo, czyli `Condition` atrybut pojawia się w elemencie właściwości. Właściwości warunkowe są definiowane lub ponownie definiowane tylko wtedy, gdy warunek ma wartość "true". Należy pamiętać, że niezdefiniowane właściwości mają nadaną domyślną wartość pustego ciągu. Na przykład

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

oznacza "Jeśli właściwość Configuration nie została jeszcze zdefiniowana, zdefiniuj ją i nadaj jej wartość "Debuguj".

Prawie wszystkie elementy programu MSBuild mogą mieć atrybut Warunek. Aby uzyskać więcej informacji na temat używania atrybutu Warunek, zobacz [Warunki](../msbuild/msbuild-conditions.md).

### <a name="reserved-properties"></a>Właściwości zarezerwowane

Program MSBuild rezerwuje niektóre nazwy właściwości do przechowywania informacji o pliku projektu i plikach binarnych programu MSBuild. MsBuildToolsPath jest przykładem właściwości zarezerwowanej. Właściwości zarezerwowane są przywołyowane za pomocą notacji $, podobnie jak każda inna właściwość. Aby uzyskać więcej informacji, zobacz [How to: Reference the name or location of](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) the project file (Jak odwoływać się do nazwy lub lokalizacji pliku projektu) oraz [MsBuild reserved and well-known properties](../msbuild/msbuild-reserved-and-well-known-properties.md)(2. Zastrzeżone i dobrze znane właściwości programu MSBuild).

### <a name="environment-variables"></a>Zmienne środowiskowe

W plikach projektu można odwoływać się do zmiennych środowiskowych tak samo jak do właściwości kompilacji. Aby na przykład użyć zmiennej środowiskowej PATH w pliku projektu, użyj zmiennej $(Path). Jeśli projekt zawiera definicję właściwości o takiej samej nazwie jak zmienna środowiskowa, właściwość w projekcie zastępuje wartość zmiennej środowiskowej. Aby uzyskać więcej informacji, [zobacz Jak używać zmiennych środowiskowych w kompilacji](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Ustawianie właściwości z wiersza polecenia

Właściwości można zdefiniować w wierszu polecenia za pomocą przełącznika wiersza polecenia -property lub -p. Wartości właściwości odebrane z wiersza polecenia zastępują wartości właściwości ustawione w pliku projektu i zmiennych środowiskowych.

**Aby ustawić wartość właściwości z wiersza polecenia:**

1. W **oknie polecenia** wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

1. Sprawdź dane wyjściowe. Powinien zostać wyświetlony ten wiersz:

    ```output
    Configuration is Release.
    ```

Program MSBuild tworzy właściwość Configuration i nadaje jej wartość "Release".

## <a name="special-characters"></a>Znaki specjalne

Niektóre znaki mają specjalne znaczenie w plikach projektu MSBuild. Przykłady tych znaków to średniki (;) i gwiazdki (*). Aby używać tych znaków specjalnych jako literałów w pliku projektu, należy je określić przy użyciu składni % , gdzie reprezentuje wartość szesnastkową \<xx> \<xx> ASCII znaku.

Zmień zadanie Komunikat, aby pokazać wartość właściwości Configuration ze znakami specjalnymi, aby była bardziej czytelna.

**Aby użyć znaków specjalnych w zadaniu Komunikat:**

1. W edytorze kodu zastąp oba zadania komunikatów tym wierszem:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

1. Zapisz plik projektu.

1. W **oknie polecenia** wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Sprawdź dane wyjściowe. Powinien zostać wyświetlony ten wiersz:

    ```output
    $(Configuration) is "Debug"
    ```

Aby uzyskać więcej informacji, zobacz [MsBuild special characters (Znaki specjalne msBuild).](../msbuild/msbuild-special-characters.md)

## <a name="build-items"></a>Elementy kompilacji

Element to element informacji, zazwyczaj nazwa pliku, który jest używany jako dane wejściowe systemu kompilacji. Na przykład kolekcja elementów reprezentujących pliki źródłowe może zostać przekazana do zadania o nazwie Compile, aby skompilować je do zestawu.

Wszystkie elementy są elementami podrzędnymi elementów ItemGroup. Nazwa elementu jest nazwą elementu podrzędnego, a wartość elementu jest wartością atrybutu Include elementu podrzędnego. Wartości elementów o tej samej nazwie są zbierane w typach elementów o tej nazwie.  Na przykład

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Definiuje grupę elementów zawierającą dwa elementy. Typ elementu Compile ma dwie wartości: *Program.cs* i *Properties\AssemblyInfo.cs.*

Poniższy kod tworzy ten sam typ elementu, deklarując oba pliki w jednym atrybutie Include, rozdzielając je średnikami.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).

> [!NOTE]
> Ścieżki plików są względne względem folderu zawierającego plik projektu MSBuild, nawet jeśli plik projektu jest zaimportowanym plikiem projektu. Istnieje kilka wyjątków od tej reguły, na przykład w przypadku korzystania z elementów [Import](import-element-msbuild.md) i [UsingTask.](usingtask-element-msbuild.md)

## <a name="examine-item-type-values"></a>Badanie wartości typu elementu

 Aby uzyskać wartości typu elementu, użyj następującej składni, gdzie ItemType jest nazwą typu elementu:

```xml
@(ItemType)
```

Użyj tej składni, aby sprawdzić typ elementu Kompilacja w pliku projektu.

**Aby sprawdzić wartości typu elementu:**

1. W edytorze kodu zastąp zadanie docelowe HelloWorld tym kodem:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

1. Zapisz plik projektu.

1. W **oknie polecenia** wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Sprawdź dane wyjściowe. Powinna zostać wyświetlony ten długi wiersz:

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

Wartości typu elementu są domyślnie oddzielone średnikami.

Aby zmienić separator typu elementu, użyj następującej składni, gdzie ItemType jest typem elementu, a Separator to ciąg z co najmniej jednym znakiem rozdzielającym:

```xml
@(ItemType, Separator)
```

Zmień zadanie Komunikat, aby używać powrotów karetki i źródeł wiersza (%0A%0D), aby wyświetlać kompilowanie elementów po jednym w wierszu.

**Aby wyświetlić wartości typu elementu po jednym w wierszu**

1. W edytorze kodu zastąp zadanie Message tym wierszem:

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2. Zapisz plik projektu.

3. W **oknie polecenia** wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Sprawdź dane wyjściowe. Powinny zostać wyświetlony następujące wiersze:

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Uwzględnianie, wykluczanie i symbole wieloznaczne

 Możesz użyć symboli wieloznacznych "*", " "i "?" z atrybutem Include, aby dodać elementy \* \* do typu elementu. Na przykład

```xml
<Photos Include="images\*.jpeg" />
```

 dodaje wszystkie pliki z rozszerzeniem *pliku jpeg* w *folderze images* do elementu photos, natomiast

```xml
<Photos Include="images\**\*.jpeg" />
```

 Dodaje wszystkie pliki z rozszerzeniem *pliku jpeg* w folderze *images* i wszystkich jego podfolderach do typu elementu Zdjęcia. Aby uzyskać więcej przykładów, [zobacz Jak wybrać pliki do skompilowania.](../msbuild/how-to-select-the-files-to-build.md)

 Zauważ, że w przypadku zadeklarowania elementów są one dodawane do typu elementu. Na przykład

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 Tworzy typ elementu o nazwie Photo zawierający wszystkie pliki w folderze *images* z rozszerzeniem pliku *jpeg* *lub.gif*. Jest to równoważne następującej linii:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Możesz wykluczyć element z typu elementu za pomocą atrybutu Exclude. Na przykład

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 dodaje wszystkie pliki z rozszerzeniem *pliku cs do* typu elementu Compile, z wyjątkiem plików, których nazwy zawierają ciąg *Projektant*. Aby uzyskać więcej przykładów, [zobacz Jak wykluczyć pliki z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).

Atrybut Exclude ma wpływ tylko na elementy dodane przez atrybut Include w elemencie item, który je zawiera. Na przykład

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

Nie wyklucza pliku *Form1.cs*, który został dodany w poprzednim elemencie elementu.

**Dołączanie i wykluczanie elementów**

1. W edytorze kodu zastąp zadanie Message tym wierszem:

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2. Dodaj tę grupę elementów tuż po elemencie Import:

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3. Zapisz plik projektu.

4. W **oknie polecenia** wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5. Sprawdź dane wyjściowe. Powinien zostać wyświetlony ten wiersz:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Metadane elementu

 Elementy mogą zawierać metadane oprócz informacji zebranych z atrybutów Uwzględnij i Wyklucz. Te metadane mogą być używane przez zadania, które wymagają więcej informacji o elementach niż tylko wartość elementu.

 Metadane elementu są deklarowane w pliku projektu przez utworzenie elementu o nazwie metadanych jako elementu podrzędnego elementu. Element może mieć zero lub więcej wartości metadanych. Na przykład następujący element CSFile ma metadane Culture z wartością "Fr":

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Aby uzyskać wartość metadanych typu elementu, użyj następującej składni, gdzie ItemType jest nazwą typu elementu, a MetaDataName jest nazwą metadanych:

```xml
%(ItemType.MetaDataName)
```

**Aby zbadać metadane elementu:**

1. W edytorze kodu zastąp zadanie Message tym wierszem:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2. Zapisz plik projektu.

3. W **oknie polecenia** wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Sprawdź dane wyjściowe. Powinny zostać wyświetlony następujące wiersze:

    ```output
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

Zwróć uwagę, że fraza "Compile.DependentUpon" pojawia się kilka razy. Użycie metadanych z tą składnią w ramach elementu docelowego powoduje "przetwarzanie wsadowe". Przetwarzanie wsadowe oznacza, że zadania w ramach elementu docelowego są wykonywane raz dla każdej unikatowej wartości metadanych. Jest to odpowiednik wspólnej konstrukcji programowania "for loop" w skrypcie MSBuild. Aby uzyskać więcej informacji, zobacz [Batching (Przetwarzanie wsadowe).](../msbuild/msbuild-batching.md)

### <a name="well-known-metadata"></a>Dobrze znane metadane

 Za każdym razem, gdy element jest dodawany do listy elementów, jest on przypisywany do niektórych dobrze znanych metadanych. Na przykład funkcja %(Filename) zwraca nazwę pliku dowolnego elementu. Aby uzyskać pełną listę dobrze znanych metadanych, zobacz Metadane dobrze [znanego elementu](../msbuild/msbuild-well-known-item-metadata.md).

**Aby sprawdzić dobrze znane metadane:**

1. W edytorze kodu zastąp zadanie Message tym wierszem:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2. Zapisz plik projektu.

3. W **oknie polecenia** wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Sprawdź dane wyjściowe. Powinny zostać wyświetlony następujące wiersze:

    ```output
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

Porównując dwa powyższe przykłady, można zobaczyć, że chociaż nie każdy element w typie elementu Kompilacja ma metadane DependentUpon, wszystkie elementy mają dobrze znane metadane Nazwa pliku.

### <a name="metadata-transformations"></a>Przekształcenia metadanych

 Listy elementów można przekształcić w nowe listy elementów. Aby przekształcić listę elementów, użyj następującej składni, gdzie to nazwa typu elementu i jest \<ItemType> \<MetadataName> nazwą metadanych:

```xml
@(ItemType -> '%(MetadataName)')
```

Na przykład listę elementów plików źródłowych można przekształcić w kolekcję plików obiektów przy użyciu wyrażenia, takiego jak `@(SourceFiles -> '%(Filename).obj')` . Aby uzyskać więcej informacji, zobacz [Przekształcenia](../msbuild/msbuild-transforms.md).

**Aby przekształcić elementy przy użyciu metadanych:**

1. W edytorze kodu zastąp zadanie Message tym wierszem:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2. Zapisz plik projektu.

3. W **oknie polecenia** wprowadź i wykonaj ten wiersz:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Sprawdź dane wyjściowe. Powinien zostać wyświetlony ten wiersz:

    ```output
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Zwróć uwagę, że metadane wyrażone w tej składni nie powodują przetwarzania wsadowego.

## <a name="next-steps"></a>Następne kroki

 Aby dowiedzieć się, jak utworzyć prosty plik projektu po jednym kroku, wypróbuj przewodnik: tworzenie pliku projektu [MSBuild od podstaw.](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie programu MSBuild](../msbuild/msbuild.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
