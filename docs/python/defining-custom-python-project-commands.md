---
title: Definiowanie niestandardowych poleceń menu dla projektów języka Python
description: Edycji projektu i plików obiektów docelowych można dodać niestandardowe polecenia do menu kontekstowego projektu języka Python w programie Visual Studio, aby wywołać programów wykonywalnych, skryptów, moduły, fragmenty kodu i narzędzia pip.
ms.date: 11/12/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3d183041732b5170da4a7e8832346a93dec32451
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55943093"
---
# <a name="define-custom-commands-for-python-projects"></a>Definiowanie niestandardowych poleceń dla projektów języka Python

W trakcie pracy z Twoich projektów języka Python, może się okazać samodzielnie przełączenie do okna polecenia do uruchamiania skryptów określonych lub moduły, Uruchom polecenia pip lub uruchamiania dowolnego narzędzia. Aby poprawić wydajność pracy, możesz dodać niestandardowe polecenia, aby **Python** podmenu w menu kontekstowego projektu języka Python. Te polecenia mogą być uruchamiane w oknie konsoli lub w programie Visual Studio **dane wyjściowe** okna. Wyrażenia regularne umożliwia również poinstruować Visual Studio, jak analizować błędy i ostrzeżenia z danych wyjściowych polecenia.

Domyślnie menu zawiera tylko jednej **Uruchom PyLint** polecenia:

![Domyślne wyglądu podmenu języka Python w menu kontekstowym projektu](media/custom-commands-default-menu.png)

Polecenia niestandardowe są wyświetlane w tym samym menu kontekstowego. Polecenia niestandardowe są dodawane do pliku projektu bezpośrednio, gdzie mają one zastosowanie do tego pojedynczego projektu. Można również definiować niestandardowe polecenia w *.targets* pliku, który można łatwo zaimportować do wielu plikach projektów.

Niektóre szablony projektów języka Python w programie Visual Studio już dodać niestandardowe polecenia własne przy użyciu ich *.targets* pliku. Na przykład szablony projektu sieci Web Bottle i projektu sieci Web Flask dodać dwa polecenia **spustit server** i **początkowego serwera debugowania**. Szablon projektu sieci Web Django dodaje tych tych samych poleceń, a także kilka innych:

![Wyglądu podmenu języka Python w menu kontekstowym projektu Django](media/custom-commands-django-menu.png)

Każde polecenie niestandardowe mogą odwoływać się do pliku Python, moduł języka Python, wbudowany kod języka Python, dowolnego pliku wykonywalnego lub polecenia pip. Można również określić, jak i gdzie jest uruchamiane polecenie.

> [!Tip]
> Po każdym wprowadzeniu zmian do pliku projektu w edytorze tekstu, należy ponownie załadować projekt w programie Visual Studio, aby zastosować te zmiany. Na przykład należy ponownie załadować projekt po dodaniu polecenie niestandardowe definicje dla tych poleceń, które ma być wyświetlana w menu kontekstowym projektu.
>
> Jak wiadomo, program Visual Studio udostępnia środki do bezpośredniego edytowania pliku projektu. Najpierw kliknij prawym przyciskiem myszy plik projektu i wybierz **Zwolnij projekt**, a następnie ponownie kliknij prawym przyciskiem myszy i wybierz **Edytuj \<Nazwa projektu >** otworzyć projektu w edytorze programu Visual Studio. Następnie utworzyć i zapisać zmiany, ponownie kliknij prawym przyciskiem myszy projekt i wybierz **Załaduj ponownie projekt**, który także wyświetli monit o potwierdzenie zamknięcia pliku projektu w edytorze.
>
> Podczas tworzenia niestandardowych poleceń, jednak te klika przycisk może stać się uciążliwe. To bardziej wydajne przepływu pracy, załadowanie projektu w programie Visual Studio i również otworzyć *.pyproj* plik w edytorze oddzielne całkowicie (takich jak inne wystąpienie programu Visual Studio, Visual Studio Code, program Notatnik, itp.). Podczas zapisywania zmian w edytorze i przełącz się do programu Visual Studio, Visual Studio wykrywa zmiany i zapyta, czy ponownie załadować projektu (**projektu \<name > został zmodyfikowany poza środowiskiem.**). Wybierz **Załaduj ponownie** i zmiany są natychmiast stosowane w tylko jednym kroku.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Przewodnik: Dodawanie polecenia do pliku projektu

Zapoznać się z niestandardowych poleceń, w tej sekcji przedstawiono prosty przykład jest uruchamiany plik startowy projektu bezpośrednio przy użyciu *python.exe*. (Takie polecenie skutecznie jest taka sama jak za pomocą **debugowania** > **Uruchom bez debugowania**.)

1. Utwórz nowy projekt o nazwie "Python-CustomCommands" przy użyciu **aplikację w języku Python** szablonu. (Zobacz [Szybki Start: Tworzenie projektu w języku Python na podstawie szablonu](quickstart-02-python-in-visual-studio-project-from-template.md) Aby uzyskać instrukcje, jeśli nie znasz już z procesem.)

1. W *Python_CustomCommands.py*, Dodaj kod `print("Hello custom commands")`.

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, wybierz opcję **Python**i zwróć uwagę, że jest tylko polecenie, które pojawia się podmenu **Uruchom PyLint**. Niestandardowych poleceń pojawiają się w tej samej podmenu.

1. Zgodnie z sugestią we wstępie, otwórz *Python CustomCommands.pyproj* w edytorze tekstów oddzielne. Następnie dodaj następujące wiersze na końcu pliku znajdujący się wewnątrz zamykającym `</Project>` i Zapisz plik.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Przejdź z powrotem do programu Visual Studio i wybierz **Załaduj ponownie** po wyświetleniu monitu o zmianie pliku. Następnie sprawdź **Python** menu ponownie, aby zobaczyć, że **Uruchom PyLint** nadal jest jedynym elementem w nim wyświetlone ponieważ wiersze dodawanych tylko replikacja domyślnie `<PythonCommands>` grupy właściwości zawierającej PyLint polecenie.

1. Przejdź do edytora z pliku projektu i dodaj następującą `<Target>` definicji po `<PropertyGroup>`. Zgodnie z opisem w dalszej części tego artykułu, to `Target` element definiuje niestandardowe polecenia uruchomienia pliku (określone przez właściwość "StartupFile") przy użyciu *python.exe* w oknie konsoli. Ten atrybut `ExecuteIn="consolepause"` używa konsoli, która oczekuje na naciśnij dowolny klawisz, przed zamknięciem.

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. Dodaj wartość elementu docelowego `Name` atrybutu `<PythonCommands>` grupy właściwości dodane wcześniej, więc, że element wygląda jak poniższy kod. Dodawanie nazwę docelowej do tej listy to, co dodaje go do **Python** menu.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Jeśli chcesz, aby Twoje polecenie, aby pojawić się przed tymi określonymi w `$(PythonCommands)`, umieść je przed tego tokenu.

1. Zapisz plik projektu, przełącz się do programu Visual Studio i ponownie Załaduj projekt po wyświetleniu monitu. Kliknij prawym przyciskiem myszy **Python CustomCommands** projektu, a następnie wybierz **Python**. Powinien zostać wyświetlony **Uruchom plik startowy** elementu menu. Jeśli nie widzisz pozycji menu, sprawdź, dodano nazwę aby `<PythonCommands>` elementu. Zobacz też [Rozwiązywanie problemów](#troubleshooting) w dalszej części tego artykułu.

    ![Polecenie niestandardowe, które pojawiają się w podmenu kontekst języka Python](media/custom-commands-walkthrough-menu-item.png)

1. Wybierz **Uruchom plik startowy** polecenia i powinien zostać wyświetlony okno polecenia, są wyświetlane z tekstem **Hello niestandardowych poleceń** następuje **naciśnij dowolny klawisz, aby kontynuować**.  Naciśnij dowolny klawisz, aby zamknąć okno.

    ![Dane wyjściowe polecenia niestandardowe w oknie konsoli](media/custom-commands-walkthrough-console.png)

1. Powrócić do edytora przy użyciu pliku projektu i zmień wartość właściwości `ExecuteIn` atrybutu `output`. Zapisz plik, przełącz się do programu Visual Studio, Załaduj ponownie projekt i wywołać polecenie ponownie. Teraz widać, że program danych wyjściowych są wyświetlane w programie Visual Studio **dane wyjściowe** okna:

    ![Dane wyjściowe polecenia niestandardowe w oknie danych wyjściowych](media/custom-commands-walkthrough-output-window.png)

1. Aby dodać więcej poleceń, należy zdefiniować odpowiednią `<Target>` elementu dla każdego polecenia, Dodaj nazwę obiektu docelowego do `<PythonCommands>` grupy właściwości i ponownie Załaduj projekt w programie Visual Studio.

>[!Tip]
> Jeśli wywołujesz polecenia, że używa właściwości projektu, taki jak `($StartupFile)`, a polecenie kończy się niepowodzeniem, ponieważ token jest niezdefiniowana, po ponownym załadowaniu projektu program Visual Studio wyłącza polecenie. Wprowadzanie zmian do projektu, który zdefiniuje właściwość, jednak nie powoduje odświeżenia stan tych poleceń, więc nadal należy ponownie załadować projekt w takich przypadkach.

## <a name="command-target-structure"></a>Struktura docelowa polecenia

Ogólna postać `<Target>` element jest wyświetlany w poniższym pseudo kodzie:

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

Aby odwołać się do właściwości projektu lub zmiennych środowiskowych w wartości atrybutów, użyj nazwy w ramach `$()` tokenów, takich jak `$(StartupFile)` i `$(MSBuildProjectDirectory)`. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Atrybuty docelowe

| Atrybut | Wymagane | Opis |
| --- | --- | --- |
| Name | Tak | Identyfikator polecenia w ramach projektu programu Visual Studio. Ta nazwa musi zostać dodany do `<PythonCommands>` grupy właściwości dla polecenia ma być wyświetlana w podmenu języka Python. |
| Etykieta | Tak | Nazwa wyświetlana interfejsu użytkownika jest wyświetlana w podmenu języka Python. |
| Zwraca | Tak | Musi zawierać `@(Commands)`, który identyfikuje element docelowy jako polecenie. |

### <a name="createpythoncommanditem-attributes"></a>Atrybuty CreatePythonCommandItem

Wszystkie wartości atrybutów jest rozróżniana wielkość liter.

| Atrybut | Wymagane | Opis |
| --- | --- | --- |
| TargetType | Tak | Określa atrybut docelowy zawiera i sposobie ich użycia wraz z atrybutem argumenty:<ul><li>**Plik wykonywalny**: Uruchom plik wykonywalny o nazwie w lokalizacji docelowej, dodając wartość w argumentach, tak, jakby wprowadzone bezpośrednio w wierszu polecenia. Wartość musi zawierać tylko nazwę programu bez argumentów.</li><li>**skrypt**: Uruchom *python.exe* przy użyciu nazwy pliku w lokalizacji docelowej, a następnie z wartością w argumentach.</li><li>**Moduł**: Uruchom `python -m` następuje nazwa modułu w lokalizacji docelowej, a następnie z wartością w argumentach.</li><li>**Kod**: Uruchamianie kodu wbudowanego znajdujących się w lokalizacji docelowej. Wartość argumentów jest ignorowana.</li><li>**Narzędzie PIP**: Uruchom `pip` za pomocą polecenia w lokalizacji docelowej, a następnie argumentów; jest ExecuteIn jest ustawiona na "wyjściowe", jednak zakłada pip `install` polecenia i używa docelowy jako nazwę pakietu.</li></ul> |
| Cel | Tak | Nazwa pliku, nazwa modułu, kodu lub polecenia pip do użycia, w zależności od TargetType. |
| Argumenty | Optional | Określa ciąg argumentów (jeśli istnieje), oferowanie element docelowy. Należy pamiętać, że po TargetType `script`, podano argumentów do programu Python nie *python.exe*. Ignorowane dla `code` TargetType. |
| ExecuteIn | Tak | Określa środowisko, w którym należy uruchomić polecenie:<ul><li>**Konsola**: (Ustawienie domyślne) Uruchamia element docelowy i argumenty, tak, jakby one są umieszczone bezpośrednio w wierszu polecenia. Zostanie wyświetlone okno polecenia, a docelowym jest uruchomiona, a następnie automatycznie zamknięte.</li><li>**consolepause**: Taka sama jak konsoli, ale czeka na naciśnięcie klawisza przed zamknięciem okna.</li><li>**Dane wyjściowe**: Uruchamia docelowego i wyświetla wyniki w **dane wyjściowe** okna w programie Visual Studio. Jeśli TargetType "pip", Visual Studio używa docelowy jako nazwę pakietu i dołącza argumentów.</li><li>**repl**: Uruchamia docelowego w [Python Interactive](python-interactive-repl-in-visual-studio.md) okno; opcjonalnie wyświetlana nazwa jest używana dla tytułu okna.</li><li>**Brak**: działa tak samo jak konsoli.</li></ul>|
| WorkingDirectory | Optional | Folder, w którym należy uruchomić polecenie. |
| ErrorRegex<br>WarningRegEx | Optional | Używana tylko wtedy, gdy ExecuteIn jest `output`. Obie wartości określić wyrażenie regularne, za pomocą których program Visual Studio analizuje dane wyjściowe, aby wyświetlić błędy i ostrzeżenia w polecenia jego **lista błędów** okna. Jeśli nie zostanie określony, polecenie nie ma wpływu na **lista błędów** okna. Aby uzyskać więcej informacji, w jaki program Visual Studio oczekuje, zobacz [nazwanych grup przechwytywania](#named-capture-groups-for-regular-expressions). |
| RequiredPackages | Optional | Listę wymagań dotyczących pakietu dla polecenia, używając tego samego formatu co [ *requirements.txt* ](https://pip.readthedocs.io/en/1.1/requirements.html) (pip.readthedocs.io). **Uruchom PyLint** polecenia, na przykład Określa `pylint>=1.0.0`. Przed uruchomieniem polecenia, programu Visual Studio sprawdza, czy są zainstalowane wszystkie pakiety na liście. Visual Studio używa pip, aby zainstalować wszystkie brakujące pakiety. |
| Środowisko | Optional | Ciąg zmiennych środowiskowych w celu definiowania przed uruchomieniem polecenia. Każda zmienna używa formularza \<NAME > =\<wartość > wiele zmiennych, oddzielając je średnikami. Zmienna z wieloma wartościami muszą być zawarte w pojedynczym lub podwójnym cudzysłowie, jak w "Nazwa = wartość1; WARTOŚĆ2 ". |

#### <a name="named-capture-groups-for-regular-expressions"></a>Funkcji przechwytywania o nazwie grupy dla wyrażeń regularnych

Podczas analizowania błędów i ostrzeżeń z danych wyjściowych polecenia, programu Visual Studio oczekuje wyrażeń regularnych w `ErrorRegex` i `WarningRegex` wartości należy użyć następującego nazwanych grup:

- `(?<message>...)`: Tekst błędu
- `(?<code>...)`: Kod błędu
- `(?<filename>...)`: Nazwa pliku, dla której zgłaszany jest błąd
- `(?<line>...)`: Numer wiersza lokalizacji w pliku, dla której zgłaszany jest błąd.
- `(?<column>...)`: Numer kolumny lokalizacji w pliku, dla której zgłaszany jest błąd.

Na przykład PyLint generuje ostrzeżenia o następującej postaci:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Aby programowi Visual Studio wyodrębnić właściwe informacje z takich ostrzeżeń i wyświetlić je w **lista błędów** oknie `WarningRegex` wartość **Uruchom Pylint** polecenia jest następująca:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Należy pamiętać, że `msg_id` wartość powinna być faktycznie `code`, zobacz [3680 problem](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="create-a-targets-file-with-custom-commands"></a>Utwórz plik .targets za pomocą polecenia niestandardowe

Definiowanie niestandardowych poleceń w pliku projektu udostępnia je do tego pliku projektu. Aby użyć poleceń w wielu plikach projektów, możesz zamiast tego Zdefiniuj `<PythonCommands>` właściwości grupy i wszystkie Twoje `<Target>` elementów w *.targets* pliku. Następnie można zaimportować ten plik do indywidualnych plików projektu.

*.Targets* plik jest sformatowany w następujący sposób:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

Ładowanie *.targets* plik do projektu, umieść `<Import Project="(path)">` element w obrębie `<Project>` elementu. Na przykład, jeśli istnieje plik o nazwie *CustomCommands.targets* w *cele* podfolderu w projekcie, użyj następującego kodu:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Zawsze, gdy zmienisz *.targets* pliku, należy ponownie załadować *rozwiązania* zawierający projekt, nie tylko projekt.

## <a name="example-commands"></a>Przykładowe polecenia

### <a name="run-pylint-module-target"></a>Spustit PyLint (obiekt docelowy modułu)

Poniższy kod, który pojawia się w *Microsoft.PythonTools.targets* pliku:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Uruchom instalację narzędzia pip z określonego pakietu (obiekt docelowy adresu pip)

Następujące polecenie uruchamia `pip install my-package` w **dane wyjściowe** okna. Można użyć polecenia programu podczas tworzenia pakietu i testowania jej instalacji. Należy pamiętać, że docelowy zawiera nazwę pakietu, a nie od `install` polecenia przyjęto, że podczas korzystania `ExecuteIn="output"`.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>Pokaż przestarzałe pakiety pip (obiekt docelowy adresu pip)

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>Uruchom plik wykonywalny z consolepause

Następujące polecenie, po prostu działa `where` pokazanie Python pliki w folderze projektu:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>Uruchom serwer i debugowanie wykonywania polecenia serwera

Aby poznać sposób, w jaki **początkowego serwera** i **początkowego serwera debugowania** poleceń dla projektów sieci web są zdefiniowane, sprawdź [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

### <a name="install-package-for-development"></a>Zainstaluj pakiet do tworzenia aplikacji

```xml
<PropertyGroup>
  <PythonCommands>PipInstallDevCommand;$(PythonCommands);</PythonCommands>
</PropertyGroup>

<Target Name="PipInstallDevCommand" Label="Install package for development" Returns="@(Commands)">
    <CreatePythonCommandItem Target="pip" TargetType="module" Arguments="install --editable $(ProjectDir)"
        WorkingDirectory="$(WorkingDirectory)" ExecuteIn="Repl:Install package for development">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), używane z uprawnieniami.*

### <a name="generate-windows-installer"></a>Generowanie Instalatora Windows

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWinInstCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWinInstCommand" Label="Generate Windows Installer" Returns="@(Commands)">
    <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
        Arguments="bdist_wininst --user-access-control=force --title &quot;$(InstallerTitle)&quot; --dist-dir=&quot;$(DistributionOutputDir)&quot;"
        WorkingDirectory="$(WorkingDirectory)" RequiredPackages="setuptools"
        ExecuteIn="Repl:Generate Windows Installer">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), używane z uprawnieniami.*

### <a name="generate-wheel-package"></a>Generuj pakiet wheel

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWheelCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWheelCommand" Label="Generate Wheel Package" Returns="@(Commands)">

  <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
      Arguments="bdist_wheel --dist-dir=&quot;$(DistributionOutputDir)&quot;"
      WorkingDirectory="$(WorkingDirectory)" RequiredPackages="wheel;setuptools"
      ExecuteIn="Repl:Generate Wheel Package">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), używane z uprawnieniami.*

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="message-the-project-file-could-not-be-loaded"></a>Komunikat: "Nie można załadować pliku projektu"

Oznacza, że błędy składni w pliku projektu. Komunikat zawiera konkretny błąd o numerze wiersza i położenie znaku.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Zamyka okno konsoli, natychmiast, po uruchomieniu polecenia

Użyj `ExecuteIn="consolepause"` zamiast `ExecuteIn="console"`.

### <a name="command-does-not-appear-on-the-menu"></a>Nie ma polecenia menu

Upewnij się, że polecenie znajduje się w `<PythonCommands>` grupy właściwości i czy nazwa na liście polecenia odpowiada nazwie określonej w `<Target>` elementu.

Na przykład w następujących elementów, z nazwą "Przykład" w grupie właściwości nie jest zgodna z nazwą "ExampleCommand" w elemencie docelowym. Program Visual Studio nie odnajdzie polecenie o nazwie "Przykładowy", więc pojawia się żadne polecenie. Użyj "ExampleCommand" na liście polecenia albo tylko zmienić nazwę elementu docelowego "Przykład".

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Komunikat: "Wystąpił błąd podczas uruchamiania \<nazwa polecenia >. Nie można pobrać polecenia \<target-name > z projektu. "

Oznacza to, że zawartość `<Target>` lub `<CreatePythonCommandItem>` elementy są nieprawidłowe. Możliwe przyczyny:

- Wymagane `Target` atrybut jest pusty.
- Wymagane `TargetType` atrybutu jest pusta lub zawiera obsahuje nerozpoznanou hodnotu.
- Wymagane `ExecuteIn` atrybutu jest pusta lub zawiera obsahuje nerozpoznanou hodnotu.
- `ErrorRegex` lub `WarningRegex` został określony bez ustawienia `ExecuteIn="output"`.
- Nierozpoznany istnieją atrybuty w elemencie. Na przykład, być może użyto `Argumnets` (czytelną) zamiast `Arguments`.

Wartości atrybutów może być pusta, jeśli odwołujesz się do właściwości, która nie jest zdefiniowana. Na przykład, jeśli przy użyciu tokenu `$(StartupFile)` , ale nie plik startowy został zdefiniowany w projekcie, a następnie token jest rozpoznawany jako ciąg pusty. W takich przypadkach można określić wartość domyślną. Na przykład **uruchom serwer** i **serwera debugowania Uruchom** polecenia zdefiniowane w Bottle, Flask, i domyślnie szablony projektów Django *manage.py* Jeśli jeszcze tego nie inny sposób określony plik startowy serwera we właściwościach projektu.

### <a name="visual-studio-hangs-and-crashes-when-running-the-command"></a>Program Visual Studio zawiesza się i ulega awarii podczas uruchamiania polecenia

Prawdopodobnie próbuje uruchomić polecenie konsoli z `ExecuteIn="output"`, w którym to przypadku programu Visual Studio może ulec awarii próby przeprowadzenia analizy danych wyjściowych. Zamiast nich należy używać słów kluczowych `ExecuteIn="console"`. (Zobacz [wystawiać 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Polecenia pliku wykonywalnego "nie został rozpoznany jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy"

Korzystając z `TargetType="executable"`, wartość w `Target` musi być *tylko* nazwy bez argumentów, takich jak program *python* lub *python.exe* tylko. Przenieś wszystkie argumenty `Arguments` atrybutu.
