---
title: Definiowanie niestandardowych poleceń menu dla projektów języka Python
description: Edytując pliki projektu i obiekty docelowe, można dodać niestandardowe polecenia do menu kontekstowego projektu Języka Python w programie Visual Studio, aby wywołać programy wykonywalne, skrypty, moduły, wbudowane fragmenty kodu i pip.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ec53a67980866ed6422fae5764bbf6a9313ef91e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957709"
---
# <a name="define-custom-commands-for-python-projects"></a>Definiowanie poleceń niestandardowych dla projektów języka Python

W trakcie pracy z projektami Języka Python możesz przełączyć się do okna poleceń, aby uruchamiać określone skrypty lub moduły, uruchamiać polecenia pip lub uruchamiać inne dowolne narzędzie. Aby ulepszyć przepływ pracy, można dodać polecenia niestandardowe do podmenu **Pythona** w menu kontekstowym projektu Języka Python. Te polecenia można uruchomić w oknie konsoli lub w oknie **danych wyjściowych** programu Visual Studio. Można również użyć wyrażeń regularnych, aby poinstruować visual studio, jak przeanalizować błędy i ostrzeżenia z danych wyjściowych polecenia.

Domyślnie to menu zawiera tylko pojedyncze polecenie **Uruchom PyLint:**

![Domyślny wygląd podmenu Pythona w menu kontekstowym projektu](media/custom-commands-default-menu.png)

Polecenia niestandardowe są wyświetlane w tym samym menu kontekstowym. Polecenia niestandardowe są dodawane bezpośrednio do pliku projektu, gdzie mają zastosowanie do tego pojedynczego projektu. Można również zdefiniować polecenia niestandardowe w pliku *.targets,* które można łatwo zaimportować do wielu plików projektu.

Niektóre szablony projektów języka Python w programie Visual Studio już dodać niestandardowe polecenia własnych przy użyciu pliku *.targets.* Na przykład szablony Bottle Web Project i Flask Web Project dodają dwa polecenia: **Uruchom serwer** i Uruchom **serwer debugowania**. Szablon Django Web Project dodaje te same polecenia plus sporo więcej:

![Pojawienie się podmenu Pythona w menu kontekstowym projektu Django](media/custom-commands-django-menu.png)

Każde polecenie niestandardowe może odnosić się do pliku Pythona, modułu Pythona, wbudowanego kodu Pythona, dowolnego pliku wykonywalnego lub polecenia pip. Można również określić, jak i gdzie jest uruchamiane polecenie.

> [!Tip]
> Za każdym razem, gdy wprowadzać zmiany w pliku projektu w edytorze tekstu, konieczne jest ponowne załadowanie projektu w programie Visual Studio, aby zastosować te zmiany. Na przykład należy ponownie załadować projekt po dodaniu niestandardowych definicji poleceń dla tych poleceń, aby pojawić się w menu kontekstowym projektu.
>
> Jak być może wiesz, Visual Studio zapewnia możliwość edycji pliku projektu bezpośrednio. Najpierw kliknij prawym przyciskiem myszy plik projektu i wybierz polecenie **Zwolnij projekt,** a następnie kliknij prawym przyciskiem myszy ponownie i wybierz polecenie ** \<Edytuj nazwę projektu>,** aby otworzyć projekt w edytorze programu Visual Studio. Następnie należy wprowadzić i zapisać zmiany, kliknij prawym przyciskiem myszy projekt jeszcze raz i wybierz polecenie **Przeładuj projekt,** co również monituje o potwierdzenie zamknięcia pliku projektu w edytorze.
>
> Podczas tworzenia polecenia niestandardowego wszystkie te kliknięcia mogą stać się uciążliwe. Aby uzyskać bardziej wydajny przepływ pracy, należy załadować projekt w programie Visual Studio, a także otworzyć plik *pyproj* w osobnym edytorze w ogóle (na przykład inne wystąpienie programu Visual Studio, Visual Studio Code, Notatnik, itp.). Po zapisaniu zmian w edytorze i przełączeniu do programu Visual Studio program Visual Studio wykrywa zmiany i pyta, czy przeładować projekt (**Nazwa projektu \<> została zmodyfikowana poza środowiskiem.**). Wybierz **opcję Załaduj** ponownie, a zmiany zostaną natychmiast zastosowane w jednym kroku.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Instruktaż: Dodawanie polecenia do pliku projektu

Aby zapoznać się z poleceniami niestandardowymi, w tej sekcji przechodzi prosty przykład, który uruchamia plik startowy projektu bezpośrednio za pomocą *pliku python.exe*. (Takie polecenie jest w rzeczywistości takie samo jak przy użyciu **debugowania** > **start bez debugowania**.)

1. Utwórz nowy projekt o nazwie "Python-CustomCommands" przy użyciu szablonu **aplikacji Języka Python.** (Zobacz [Szybki start: Tworzenie projektu języka Python na podstawie szablonu,](quickstart-02-python-in-visual-studio-project-from-template.md) aby uzyskać instrukcje, jeśli nie jesteś jeszcze zaznajomiony z tym procesem).

1. W *Python_CustomCommands.py*dodaj kod `print("Hello custom commands")`.

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań**, wybierz **Python**i zwróć uwagę, że jedynym poleceniem pojawia się w podmenu jest **Uruchom PyLint**. Polecenia niestandardowe są wyświetlane w tym samym podmenu.

1. Jak sugerowano we wstępie, otwórz *Python-CustomCommands.pyproj* w osobnym edytorze tekstu. Następnie dodaj następujące wiersze na końcu pliku `</Project>` tylko wewnątrz zamknięcia i zapisz plik.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Przełącz się z powrotem do programu Visual Studio i wybierz **ponownie załadować,** gdy monituje o zmianę pliku. Następnie sprawdź menu **Python** ponownie, aby zobaczyć, że **Uruchom PyLint** jest nadal jedynym `<PythonCommands>` elementem pokazano tam, ponieważ wiersze dodane tylko replikować domyślną grupę właściwości zawierającą polecenie PyLint.

1. Przełącz się do edytora z `<Target>` plikiem `<PropertyGroup>`projektu i dodaj następującą definicję po pliku . Jak wyjaśniono w dalszej `Target` części tego artykułu, ten element definiuje niestandardowe polecenie uruchamiania pliku startowego (identyfikowanego przez właściwość "StartupFile") przy użyciu *pliku python.exe* w oknie konsoli. Atrybut `ExecuteIn="consolepause"` używa konsoli, która czeka na naciśnięcie klawisza przed zamknięciem.

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

1. Dodaj wartość `Name` atrybutu Target do grupy `<PythonCommands>` właściwości dodane wcześniej, tak aby element wyglądał jak kod poniżej. Dodanie nazwy obiektu docelowego do tej listy jest tym, co dodaje ją do menu **Pythona.**

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Jeśli chcesz, aby twoje polecenie `$(PythonCommands)`było wyświetlane przed tymi zdefiniowanymi w , umieść je przed tym tokenem.

1. Zapisz plik projektu, przełącz się do programu Visual Studio i ponownie załaduj projekt po wyświetleniu monitu. Następnie kliknij prawym przyciskiem myszy projekt **Python-CustomCommands** i **wybierz**python . W menu powinna zostać wyświetlna pozycja **Uruchom plik startowy.** Jeśli nie widzisz elementu menu, sprawdź, czy nazwa `<PythonCommands>` została dodana do elementu. Zobacz też [Rozwiązywanie problemów](#troubleshooting) w dalszej części tego artykułu.

    ![Polecenie niestandardowe wyświetlane w podmenu kontekstu języka Python](media/custom-commands-walkthrough-menu-item.png)

1. Zaznacz polecenie **Uruchom plik startowy,** a w oknie polecenia powinno pojawić się okno polecenia z tekstem **Hello custom commands,** po którym **następuje naciśnięcie dowolnego klawisza, aby kontynuować**.  Naciśnij klawisz, aby zamknąć okno.

    ![Niestandardowe dane wyjściowe polecenia w oknie konsoli](media/custom-commands-walkthrough-console.png)

1. Wróć do edytora z plikiem projektu `ExecuteIn` i zmień `output`wartość atrybutu na . Zapisz plik, przełącz się do programu Visual Studio, ponownie załaduj projekt i ponownie wywołaj polecenie. Tym razem zobaczysz dane wyjściowe programu są wyświetlane w oknie **Dane wyjściowe** programu Visual Studio:

    ![Niestandardowe wyjście polecenia w oknie wyjściowym](media/custom-commands-walkthrough-output-window.png)

1. Aby dodać więcej poleceń, `<Target>` zdefiniuj odpowiedni element dla `<PythonCommands>` każdego polecenia, dodaj nazwę obiektu docelowego do grupy właściwości i ponownie załaduj projekt w programie Visual Studio.

>[!Tip]
> Jeśli wywołasz polecenie, które używa właściwości projektu, takich jak `($StartupFile)`, a polecenie kończy się niepowodzeniem, ponieważ token jest niezdefiniowany, Visual Studio wyłącza polecenie, dopóki nie zostanie ponownie załadowany projekt. Wprowadzanie zmian w projekcie, które zdefiniowałyby właściwość, jednak nie odświeża stanu tych poleceń, więc nadal trzeba ponownie załadować projekt w takich przypadkach.

## <a name="command-target-structure"></a>Struktura docelowa polecenia

Ogólna forma `<Target>` elementu jest pokazana w następującym pseudodeksie:

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

Aby odwołać się do właściwości projektu lub zmiennych środowiskowych `$()` w wartościach `$(StartupFile)` `$(MSBuildProjectDirectory)`atrybutów, należy użyć nazwy w tokenie, takim jak i . Aby uzyskać więcej informacji, zobacz [WŁAŚCIWOŚCI MSBuild](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Atrybuty docelowe

| Atrybut | Wymagany | Opis |
| --- | --- | --- |
| Nazwa | Tak | Identyfikator polecenia w projekcie programu Visual Studio. Ta nazwa musi zostać `<PythonCommands>` dodana do grupy właściwości, aby polecenie pojawiło się w podmenu Pythona. |
| Label | Tak | Nazwa wyświetlana interfejsu użytkownika, która pojawia się w podmenu Python. |
| Zwraca | Tak | Musi `@(Commands)`zawierać , który identyfikuje obiekt docelowy jako polecenie. |

### <a name="createpythoncommanditem-attributes"></a>Atrybuty CreatePythonCommandItem

Wszystkie wartości atrybutów są niewrażliwe na wielkości liter.

| Atrybut | Wymagany | Opis |
| --- | --- | --- |
| Targettype | Tak | Określa, co zawiera atrybut Target i jak jest używany wraz z atrybutem Argumenty:<ul><li>**plik wykonywalny**: Uruchom plik wykonywalny o nazwie w polu Docelowym, dołączając wartość w argumentach, tak jakby został wprowadzony bezpośrednio w wierszu polecenia. Wartość musi zawierać tylko nazwę programu bez argumentów.</li><li>**skrypt**: Uruchom *plik python.exe* z nazwami plików w docelowych, a następnie z wartością w argumenty.</li><li>**moduł**: `python -m` Uruchom, po którym następuje nazwa modułu w punkcie docelowym, a następnie wartość w argumentach.</li><li>**code**: Uruchom wbudowany kod zawarty w docelowych. Argumentów wartość jest ignorowana.</li><li>**pip:** `pip` Uruchom polecenie w docelowych, a następnie argumenty; jest ExecuteIn jest ustawiona na "output", `install` jednak pip zakłada polecenie i używa target jako nazwa pakietu.</li></ul> |
| Środowisko docelowe | Tak | Nazwa pliku, nazwa modułu, kod lub polecenie pip do użycia, w zależności od targettype. |
| Argumenty | Optional (Opcjonalność) | Określa ciąg argumentów (jeśli istnieje) do nadanych obiektowi docelowemu. Należy zauważyć, że `script`gdy targettype jest , argumenty są podane do programu Python, a nie *python.exe*. Ignorowane dla `code` targettype. |
| Wykonaj w | Tak | Określa środowisko, w którym ma być uruchamiane polecenie:<ul><li>**console**: (Domyślnie) Uruchamia obiekt docelowy i argumenty tak, jakby zostały wprowadzone bezpośrednio w wierszu polecenia. Okno polecenia pojawia się, gdy obiekt docelowy jest uruchomiony, a następnie jest zamykany automatycznie.</li><li>**consolepause**: Tak samo jak konsola, ale czeka na naciśnięcie klawisza przed zamknięciem okna.</li><li>**dane wyjściowe:** uruchamia obiekt docelowy i wyświetla jego wyniki w oknie **Dane wyjściowe** w programie Visual Studio. Jeśli TargetType jest "pip", Visual Studio używa target jako nazwa pakietu i dołącza argumenty.</li><li>**repl:** Uruchamia obiekt docelowy w oknie [Interaktywnym Języka Python;](python-interactive-repl-in-visual-studio.md) opcjonalna nazwa wyświetlana jest używana dla tytułu okna.</li><li>**none**: zachowuje się tak samo jak konsola.</li></ul>|
| WorkingDirectory | Optional (Opcjonalność) | Folder, w którym ma być uruchamiane polecenie. |
| Rejestr błędów<br>OstrzeżenieRegEx | Optional (Opcjonalność) | Używany tylko wtedy, `output`gdy ExecuteIn jest . Obie wartości określają wyrażenie regularne, za pomocą którego program Visual Studio analizuje dane wyjściowe polecenia, aby wyświetlić błędy i ostrzeżenia w oknie **lista błędów.** Jeśli nie zostanie określony, polecenie nie ma wpływu na okno **Lista błędów.** Aby uzyskać więcej informacji na temat oczekiwań programu Visual Studio, zobacz [Nazwane grupy przechwytywania](#named-capture-groups-for-regular-expressions). |
| Wymaganepakiecje | Optional (Opcjonalność) | Lista wymagań pakietu dla polecenia przy użyciu tego samego formatu co [*requirements.txt*](https://pip.readthedocs.io/en/1.1/requirements.html) (pip.readthedocs.io). Na przykład polecenie **Uruchom PyLint** określa `pylint>=1.0.0`. Przed uruchomieniem polecenia visual studio sprawdza, czy wszystkie pakiety na liście są zainstalowane. Visual Studio używa pip zainstalować brakujące pakiety. |
| Środowisko | Optional (Opcjonalność) | Ciąg zmiennych środowiskowych do zdefiniowania przed uruchomieniem polecenia. Każda zmienna używa \<formularza NAZWA>\<= WARTOŚĆ> z wieloma zmiennymi oddzielonymi średnikami. Zmienna z wieloma wartościami musi być zawarta w cudzysłowie pojedynczym lub podwójnym, jak w 'NAME=VALUE1; WARTOŚĆ 2". |

#### <a name="named-capture-groups-for-regular-expressions"></a>Nazwane grupy przechwytywania dla wyrażeń regularnych

Podczas analizowania błędów i ostrzeżeń z danych wyjściowych polecenia program Visual `ErrorRegex` `WarningRegex` Studio oczekuje, że wyrażenia regularne w wartości i wartości używają następujących nazwanych grup:

- `(?<message>...)`: Tekst błędu
- `(?<code>...)`: Kod błędu
- `(?<filename>...)`: Nazwa pliku, dla którego zgłoszono błąd
- `(?<line>...)`: Numer wiersza lokalizacji w pliku, dla którego zgłoszono błąd.
- `(?<column>...)`: Numer kolumny lokalizacji w pliku, dla którego zgłoszono błąd.

Na przykład PyLint generuje ostrzeżenia w następującym formularzu:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Aby umożliwić programowi Visual Studio wyodrębnianie właściwych informacji z takich `WarningRegex` ostrzeżeń i wyświetlanie ich w oknie **Lista błędów,** wartość polecenia Uruchom **Pylint** jest następująca:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Należy `msg_id` zauważyć, że w `code`wartości powinny być rzeczywiście , zobacz [Problem 3680](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="create-a-targets-file-with-custom-commands"></a>Tworzenie pliku .targets za pomocą poleceń niestandardowych

Definiowanie poleceń niestandardowych w pliku projektu udostępnia je tylko temu plikowi projektu. Aby użyć poleceń w wielu plikach `<PythonCommands>` projektu, zamiast `<Target>` tego należy zdefiniować grupę właściwości i wszystkie elementy w pliku *.targets.* Następnie należy zaimportować ten plik do poszczególnych plików projektu.

Plik *.targets* jest sformatowany w następujący sposób:

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

Aby załadować plik *.targets* do `<Import Project="(path)">` projektu, umieść `<Project>` element w dowolnym miejscu w elemencie. Na przykład jeśli masz plik o nazwie *CustomCommands.targets* w podfolderze *obiektów docelowych* w projekcie, użyj następującego kodu:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Za każdym razem, gdy zmieniasz plik *.targets,* należy ponownie załadować *rozwiązanie,* które zawiera projekt, a nie tylko sam projekt.

## <a name="example-commands"></a>Przykładowe polecenia

### <a name="run-pylint-module-target"></a>Uruchom PyLint (docelowy moduł)

W pliku *Microsoft.PythonTools.targets* pojawia się następujący kod:

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

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Uruchom instalację pip z określonym pakietem (cel pip)

Następujące polecenie `pip install my-package` jest uruchamiane w oknie **Dane wyjściowe.** Takie polecenie można użyć podczas tworzenia pakietu i testowania jego instalacji. Należy zauważyć, że target zawiera `install` nazwę pakietu, a `ExecuteIn="output"`nie polecenie, które jest przyjmowane podczas korzystania z .

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

### <a name="show-outdated-pip-packages-pip-target"></a>Pokaż przestarzałe pakiety pip (cel pip)

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

### <a name="run-an-executable-with-consolepause"></a>Uruchamianie pliku wykonywalnego za pomocą consolepause

Następujące polecenie po `where` prostu uruchamia się, aby wyświetlić pliki Języka Python, począwszy od folderu projektu:

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

### <a name="run-server-and-run-debug-server-commands"></a>Uruchamianie serwera i uruchamianie poleceń serwera debugowania

Aby dowiedzieć się, jak zdefiniowane są polecenia **serwera uruchamiania** i **uruchamiania dla** projektów sieci web, sprawdź [witrynę Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

### <a name="install-package-for-development"></a>Zainstaluj pakiet do tworzenia programów

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

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), używane za zgodą.*

### <a name="generate-windows-installer"></a>Generowanie instalatora windows

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

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), używane za zgodą.*

### <a name="generate-wheel-package"></a>Generowanie pakietu kół

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

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), używane za zgodą.*

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="message-the-project-file-could-not-be-loaded"></a>Komunikat: "Nie można załadować pliku projektu"

Wskazuje, że w pliku projektu są błędy składniowe. Komunikat zawiera określony błąd z numerem wiersza i położeniem znaku.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Okno konsoli zamyka się natychmiast po uruchomieniu polecenia

Użyj `ExecuteIn="consolepause"` zamiast `ExecuteIn="console"`.

### <a name="command-does-not-appear-on-the-menu"></a>Polecenie nie pojawia się w menu

Sprawdź, czy polecenie znajduje `<PythonCommands>` się w grupie właściwości i czy nazwa na liście `<Target>` poleceń jest zgodna z nazwą określoną w elemencie.

Na przykład w następujących elementach nazwa "Przykład" w grupie właściwości nie pasuje do nazwy "ExampleCommand" w obiekcie docelowym. Visual Studio nie znajduje polecenia o nazwie "Przykład", więc nie pojawia się żadne polecenie. Użyj "ExampleCommand" na liście poleceń lub zmień nazwę obiektu docelowego tylko na "Przykład".

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Komunikat: "Wystąpił błąd \<podczas uruchamiania nazwy polecenia>. Nie można uzyskać \<> nazwy docelowej polecenia z projektu."

Wskazuje, że zawartość `<Target>` lub `<CreatePythonCommandItem>` elementy są niepoprawne. Możliwe powody to:

- Wymagany `Target` atrybut jest pusty.
- Wymagany `TargetType` atrybut jest pusty lub zawiera nierozpoznaną wartość.
- Wymagany `ExecuteIn` atrybut jest pusty lub zawiera nierozpoznaną wartość.
- `ErrorRegex`lub `WarningRegex` jest określony `ExecuteIn="output"`bez ustawienia .
- Nierozpoznane atrybuty istnieją w elemencie. Na przykład, być `Argumnets` może użyto (błędnie) zamiast `Arguments`.

Wartości atrybutów mogą być puste, jeśli odwołujesz się do właściwości, która nie jest zdefiniowana. Na przykład jeśli używasz `$(StartupFile)` tokenu, ale żaden plik startowy nie został zdefiniowany w projekcie, token zostanie rozpoznany na pusty ciąg. W takich przypadkach można zdefiniować wartość domyślną. Na przykład polecenia **Uruchom serwer** i Uruchom **serwer debugowania** zdefiniowane w szablonach projektu Butelka, Kolby i Django domyślnie *manage.py,* jeśli nie określono inaczej pliku startowego serwera we właściwościach projektu.

### <a name="visual-studio-hangs-and-crashes-when-running-the-command"></a>Visual Studio zawiesza się i ulega awarii podczas uruchamiania polecenia

Prawdopodobnie próbujesz uruchomić polecenie konsoli za `ExecuteIn="output"`pomocą programu Visual Studio, w którym to przypadku program Visual Studio może ulec awarii podczas próby przeanalizowania danych wyjściowych. Zamiast tego użyj polecenia cmdlet `ExecuteIn="console"`. (Patrz [numer 3682).](https://github.com/Microsoft/PTVS/issues/3681)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Polecenie wykonywalne "nie jest rozpoznawane jako polecenie wewnętrzne lub zewnętrzne, program operacyjny lub plik wsadowy"

W `TargetType="executable"`przypadku korzystania `Target` z wartości musi być *tylko* nazwa programu bez żadnych argumentów, takich jak *python* lub *python.exe* tylko. Przenieś wszelkie argumenty `Arguments` do atrybutu.
