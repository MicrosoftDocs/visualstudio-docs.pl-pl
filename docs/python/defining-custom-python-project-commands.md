---
title: Definiowanie niestandardowych poleceń menu dla projektów języka Python
description: Edytując pliki projektu i elementów docelowych, można dodawać niestandardowe polecenia do menu kontekstowego projektu języka Python w programie Visual Studio, aby wywoływać programy wykonywalne, skrypty, moduły, fragmenty kodu wbudowane i PIP.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6e9e7fe418528bb888672b1b73d421d811b9e69e
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386988"
---
# <a name="define-custom-commands-for-python-projects"></a>Definiowanie poleceń niestandardowych dla projektów języka Python

W procesie pracy z projektami w języku Python możesz się dowiedzieć, jak przełączać się do okna polecenia w celu uruchomienia określonych skryptów lub modułów, uruchamiania poleceń PIP lub uruchamiania innego dowolnego narzędzia. Aby usprawnić przepływ pracy, możesz dodać niestandardowe polecenia do podmenu **Python** w menu kontekstowym projektu języka Python. Te polecenia można uruchomić w oknie konsoli lub w oknie **danych wyjściowych** programu Visual Studio. Można również użyć wyrażeń regularnych, aby nakazać programowi Visual Studio analizowanie błędów i ostrzeżeń z danych wyjściowych polecenia.

Domyślnie to menu zawiera tylko pojedyncze **uruchomienie polecenia PyLint** :

![Domyślny wygląd podmenu języka Python w menu kontekstowym projektu](media/custom-commands-default-menu.png)

Polecenia niestandardowe są wyświetlane w tym samym menu kontekstowym. Polecenia niestandardowe są dodawane do pliku projektu bezpośrednio, gdy mają zastosowanie do tego pojedynczego projektu. Możesz również zdefiniować niestandardowe polecenia w pliku *targets* , który można łatwo zaimportować do wielu plików projektu.

Niektóre szablony projektów języka Python w programie Visual Studio już dodają niestandardowe polecenia przy użyciu pliku *. targets* . Na przykład projekt sieci Web w butelkach i kolby szablon projektu sieci Web Dodaj dwa polecenia, **Uruchom serwer** i **Uruchom debugowanie serwera**. Szablon projektu sieci Web Django dodaje te same polecenia i jeszcze więcej:

![Wygląd podmenu języka Python w menu kontekstowym projektu Django](media/custom-commands-django-menu.png)

Każde polecenie niestandardowe może odwoływać się do pliku języka Python, modułu języka Python, wbudowanego kodu języka Python, dowolnego pliku wykonywalnego lub polecenia PIP. Możesz również określić sposób i miejsce uruchomienia polecenia.

> [!Tip]
> Za każdym razem, gdy wprowadzisz zmiany w pliku projektu w edytorze tekstu, konieczne jest ponowne załadowanie projektu w programie Visual Studio, aby zastosować te zmiany. Na przykład należy załadować projekt po dodaniu niestandardowych definicji poleceń dla tych poleceń, które mają być wyświetlane w menu kontekstowym projektu.
>
> W miarę możliwości program Visual Studio udostępnia środki umożliwiające bezpośrednie edytowanie pliku projektu. Najpierw kliknij prawym przyciskiem myszy plik projektu i wybierz polecenie **Zwolnij projekt**, a następnie kliknij ponownie prawym przyciskiem myszy i wybierz polecenie ** \<project-name> Edytuj** , aby otworzyć projekt w edytorze programu Visual Studio. Następnie wprowadź i Zapisz zmiany, kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Załaduj ponownie projekt**, które również poprosi o potwierdzenie zamknięcia pliku projektu w edytorze.
>
> Jednak podczas tworzenia polecenia niestandardowego wszystkie te kliknięcia mogą stać się żmudnym. Aby zapewnić wydajniejszy przepływ pracy, Załaduj projekt w programie Visual Studio, a następnie otwórz plik *. pyproj* w osobnym edytorze całkowicie (na przykład inne wystąpienie programu Visual Studio, Visual Studio Code, notatnik itp.). Po zapisaniu zmian w edytorze i przełączeniu się do programu Visual Studio program Visual Studio wykrywa zmiany i pyta, czy projekt został** \<name> zmodyfikowany poza środowiskiem.** Wybierz pozycję **Załaduj ponownie** , a zmiany zostaną zastosowane natychmiast po jednym kroku.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Przewodnik: Dodawanie polecenia do pliku projektu

Aby zaznajomić się z poleceniami niestandardowymi, w tej sekcji przedstawiono prosty przykład, który uruchamia plik startowy projektu bezpośrednio przy użyciu *python.exe*. (Takie polecenie jest efektywnie takie samo jak w przypadku **debugowania**  >  **Uruchom bez debugowania**).

1. Utwórz nowy projekt o nazwie "Python-CustomCommands" przy użyciu szablonu **aplikacji języka Python** . (Zobacz [Szybki Start: Tworzenie projektu w języku Python na podstawie szablonu,](quickstart-02-python-in-visual-studio-project-from-template.md) Aby uzyskać instrukcje, jeśli jeszcze nie znasz tego procesu).

1. W *Python_CustomCommands. PR*Dodaj kod `print("Hello custom commands")` .

1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań**, wybierz opcję **Python**i zwróć uwagę, że jedyne polecenie, które pojawia się w podmenu, jest **uruchamiane PyLint**. Twoje polecenia niestandardowe są wyświetlane w tym samym podmenu.

1. Zgodnie z sugestią we wprowadzeniu Otwórz środowisko *Python-CustomCommands. pyproj* w osobnym edytorze tekstów. Następnie Dodaj następujące wiersze na końcu pliku tuż wewnątrz zamykania `</Project>` i Zapisz plik.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Wróć do programu Visual Studio i wybierz pozycję **Załaduj ponownie** , gdy zostanie wyświetlony komunikat z prośbą o zmianę pliku. Następnie sprawdź ponownie menu **Python** , aby zobaczyć, że polecenie **Run PyLint** jest nadal jedynym widocznym elementem, ponieważ dodane przez siebie wiersze zawierają tylko replikę domyślnej `<PythonCommands>` grupy właściwości zawierającej polecenia PyLint.

1. Przejdź do edytora przy użyciu pliku projektu i Dodaj następującą `<Target>` definicję po `<PropertyGroup>` . Jak wyjaśniono w dalszej części tego artykułu, ten `Target` element definiuje niestandardowe polecenie do uruchamiania pliku startowego (identyfikowanego przez właściwość "StartupFile") przy użyciu *python.exe* w oknie konsoli. Ten atrybut `ExecuteIn="consolepause"` używa konsoli, która czeka na naciśnięcie klawisza przed zamknięciem.

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

1. Dodaj wartość `Name` atrybutu Target do `<PythonCommands>` grupy właściwości, która została dodana wcześniej, tak aby element wyglądał jak poniższy kod. Dodanie nazwy docelowej do tej listy powoduje dodanie jej do menu **Python** .

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Jeśli chcesz, aby polecenie pojawiało się przed tymi zdefiniowanymi w `$(PythonCommands)` , umieść je przed tym tokenem.

1. Zapisz plik projektu, przełącz się do programu Visual Studio i Załaduj ponownie projekt po wyświetleniu monitu. Następnie kliknij prawym przyciskiem myszy projekt **Python-CustomCommands** i wybierz polecenie **Python**. W menu powinien zostać wyświetlony element **Uruchom plik startowy** . Jeśli nie widzisz elementu menu, sprawdź, czy nazwa została dodana do `<PythonCommands>` elementu. Zobacz również [Rozwiązywanie problemów](#troubleshooting) w dalszej części tego artykułu.

    ![Niestandardowe polecenie pojawiające się w podmenu kontekstu języka Python](media/custom-commands-walkthrough-menu-item.png)

1. Wybierz polecenie **Uruchom plik startowy** , aby wyświetlić okno poleceń z poleceniami **niestandardowymi Hello** , a następnie **naciśnij dowolny klawisz, aby kontynuować**.  Naciśnij klawisz, aby zamknąć okno.

    ![Niestandardowe dane wyjściowe polecenia w oknie konsoli](media/custom-commands-walkthrough-console.png)

1. Wróć do edytora z plikiem projektu i zmień wartość `ExecuteIn` atrybutu na `output` . Zapisz plik, przełącz się do programu Visual Studio, Załaduj ponownie projekt i Wywołaj polecenie ponownie. Tym razem zobaczysz, że dane wyjściowe programu są wyświetlane w oknie **danych wyjściowych** w programie Visual Studio:

    ![Dane wyjściowe polecenia niestandardowego w oknie danych wyjściowych](media/custom-commands-walkthrough-output-window.png)

1. Aby dodać więcej poleceń, zdefiniuj odpowiedni `<Target>` element dla każdego polecenia, Dodaj nazwę obiektu docelowego do `<PythonCommands>` grupy właściwości i Załaduj ponownie projekt w programie Visual Studio.

>[!Tip]
> Jeśli wywołasz polecenie, które używa właściwości projektu, takich jak `($StartupFile)` , i polecenie nie powiedzie się, ponieważ token jest niezdefiniowany, program Visual Studio wyłączy polecenie do momentu ponownego załadowania projektu. Jednak wprowadzanie zmian w projekcie, który spowodowałoby zdefiniowanie właściwości, nie powoduje odświeżenia stanu tych poleceń, dlatego nadal trzeba ponownie załadować projekt w takich przypadkach.

## <a name="command-target-structure"></a>Struktura docelowa polecenia

Ogólny formularz `<Target>` elementu jest wyświetlany w następującym pseudo kodu:

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

Aby odwołać się do właściwości projektu lub zmiennych środowiskowych w wartościach atrybutów, użyj nazwy w `$()` tokenie, takiej jak `$(StartupFile)` i `$(MSBuildProjectDirectory)` . Aby uzyskać więcej informacji, zobacz [Właściwości programu MSBuild](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Atrybuty docelowe

| Atrybut | Wymagane | Opis |
| --- | --- | --- |
| Nazwa | Tak | Identyfikator polecenia w projekcie programu Visual Studio. Ta nazwa musi być dodana do `<PythonCommands>` grupy właściwości, aby polecenie pojawiało się w podmenu Python. |
| Etykieta | Tak | Nazwa wyświetlana interfejsu użytkownika, która pojawia się w podmenu języka Python. |
| Zwraca | Tak | Musi zawierać `@(Commands)` , który identyfikuje obiekt docelowy jako polecenie. |

### <a name="createpythoncommanditem-attributes"></a>CreatePythonCommandItem — atrybuty

Wszystkie wartości atrybutów nie uwzględnia wielkości liter.

| Atrybut | Wymagane | Opis |
| --- | --- | --- |
| Typ | Tak | Określa, co zawiera atrybut target i jak jest używany wraz z atrybutem arguments:<ul><li>**plik wykonywalny**: Uruchom plik wykonywalny o nazwie in Target, dołączając wartość w argumentach, tak jak w przypadku wprowadzenia bezpośrednio w wierszu polecenia. Wartość musi zawierać tylko nazwę programu bez argumentów.</li><li>**skrypt**: Uruchom *python.exe* z nazwą pliku w miejscu docelowym, a następnie z wartością w argumentach.</li><li>**moduł**: przebieg `python -m` , po którym następuje nazwa modułu w miejscu docelowym, a następnie wartość w argumentach.</li><li>**kod**: Uruchom wbudowany kod zawarty w elemencie docelowym. Wartość argumentów jest ignorowana.</li><li>**PIP**: przebieg `pip` przy użyciu polecenia w elemencie Target, a następnie argumentów; to Execute jest ustawione na "output", jednak PIP przyjmuje `install` polecenie i używa elementu Target jako nazwy pakietu.</li></ul> |
| Cel | Tak | Nazwa pliku, nazwę modułu, kod lub polecenie PIP, które ma być używane, w zależności od TargetType. |
| Argumenty | Opcjonalne | Określa ciąg argumentów (jeśli istnieją) do przekazania do obiektu docelowego. Należy pamiętać, że gdy TargetType ma wartość `script` , argumenty są przydawane do programu w języku Python, a nie *python.exe*. Zignorowano dla `code` TargetType. |
| Wykonaj | Tak | Określa środowisko, w którym należy uruchomić polecenie:<ul><li>**konsola**: (domyślnie) uruchamia obiekt docelowy i argumenty, tak jak w przypadku wprowadzania ich bezpośrednio w wierszu polecenia. Okno polecenia pojawia się, gdy obiekt docelowy jest uruchomiony, a następnie jest zamykane automatycznie.</li><li>**consolepause**: taki sam jak konsola, ale czeka na naciśnięcie przed zamknięciem okna.</li><li>**Output**: uruchamia obiekt docelowy i wyświetla jego wyniki w oknie **danych wyjściowych** w programie Visual Studio. Jeśli TargetType jest "PIP", program Visual Studio używa elementu docelowego jako nazwy pakietu i dołącza argumenty.</li><li>**REPL**: uruchamia cel w oknie [interaktywnym języka Python](python-interactive-repl-in-visual-studio.md) ; opcjonalna nazwa wyświetlana jest używana dla tytułu okna.</li><li>**Brak**: działa tak samo jak konsola.</li></ul>|
| WorkingDirectory | Opcjonalne | Folder, w którym ma zostać uruchomione polecenie. |
| ErrorRegex<br>WarningRegEx | Opcjonalne | Używane tylko wtedy, gdy jest wykonywane `output` . Obie wartości określają wyrażenie regularne, za pomocą którego program Visual Studio analizuje dane wyjściowe polecenia w celu wyświetlenia błędów i ostrzeżeń w jego oknie **Lista błędów** . Jeśli nie zostanie określony, polecenie nie ma wpływu na okno **Lista błędów** . Aby uzyskać więcej informacji na temat oczekiwań programu Visual Studio, zobacz [nazwane grupy przechwytywania](#named-capture-groups-for-regular-expressions). |
| RequiredPackages | Opcjonalne | Lista wymagań pakietu dla polecenia przy użyciu tego samego formatu co [*requirements.txt*](https://pip.pypa.io/en/stable/user_guide/#requirements-files) (PIP.readthedocs.IO). Polecenie **Uruchom PyLint** , na przykład `pylint>=1.0.0` . Przed uruchomieniem polecenia program Visual Studio sprawdza, czy wszystkie pakiety na liście są zainstalowane. Program Visual Studio używa narzędzia PIP, aby zainstalować brakujące pakiety. |
| Środowisko | Opcjonalne | Ciąg zmiennych środowiskowych do zdefiniowania przed uruchomieniem polecenia. Każda zmienna używa formularza \<NAME> = \<VALUE> z wieloma zmiennymi oddzielonymi średnikami. Zmienna z wieloma wartościami musi być zawarta w pojedynczym lub podwójnym cudzysłowie, jak w polu "NAME = WARTOŚĆ1; WARTOŚĆ2 ". |

#### <a name="named-capture-groups-for-regular-expressions"></a>Nazwane grupy przechwytywania dla wyrażeń regularnych

Podczas analizowania błędów i ostrzeżeń z danych wyjściowych polecenia program Visual Studio oczekuje, że wyrażenia regularne w `ErrorRegex` i `WarningRegex` wartości używają następujących nazwanych grup:

- `(?<message>...)`: Tekst błędu
- `(?<code>...)`: Kod błędu
- `(?<filename>...)`: Nazwa pliku, dla którego jest raportowany błąd
- `(?<line>...)`: Numer wiersza lokalizacji w pliku, dla którego zgłoszony został błąd.
- `(?<column>...)`: Numer kolumny lokalizacji w pliku, dla którego zgłoszony został błąd.

Na przykład PyLint generuje ostrzeżenia o następującej postaci:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Aby umożliwić programowi Visual Studio wyodrębnienie odpowiednich informacji z takich ostrzeżeń i wyświetlenie ich w oknie **Lista błędów** , `WarningRegex` wartość polecenia **Run pylint** jest następująca:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Należy zauważyć, że `msg_id` w wartości powinny być rzeczywiście `code` , patrz [problem 3680](https://github.com/Microsoft/PTVS/issues/3680)).

## <a name="create-a-targets-file-with-custom-commands"></a>Utwórz plik. targets z poleceniami niestandardowymi

Definiowanie poleceń niestandardowych w pliku projektu sprawia, że są one dostępne tylko dla tego pliku projektu. Aby użyć poleceń w wielu plikach projektu, zamiast tego należy zdefiniować `<PythonCommands>` grupę właściwości i wszystkie `<Target>` elementy w pliku *. targets* . Następnie można zaimportować ten plik do poszczególnych plików projektu.

Plik *targets* jest sformatowany w następujący sposób:

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

Aby załadować plik *targets* do projektu, umieść `<Import Project="(path)">` element w dowolnym miejscu `<Project>` elementu. Na przykład jeśli masz plik o nazwie *CustomCommands. targets* w podfolderze *targets* w projekcie, użyj następującego kodu:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Za każdym razem, gdy zmieniasz plik *targets* , należy ponownie załadować *rozwiązanie* , które zawiera projekt, a nie tylko projekt.

## <a name="example-commands"></a>Przykładowe polecenia

### <a name="run-pylint-module-target"></a>Uruchom PyLint (obiekt docelowy modułu)

Poniższy kod pojawia się w pliku *Microsoft. PythonTools. targets* :

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

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Uruchom instalację PIP z określonym pakietem (obiekt docelowy PIP)

`pip install my-package`W oknie **dane wyjściowe** zostanie uruchomione następujące polecenie. Możesz użyć takiego polecenia podczas tworzenia pakietu i testowania jego instalacji. Należy pamiętać, że element docelowy zawiera nazwę pakietu, a nie `install` polecenie, które jest zakładane podczas korzystania z programu `ExecuteIn="output"` .

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

### <a name="show-outdated-pip-packages-pip-target"></a>Pokaż nieaktualne pakiety PIP (obiekt docelowy PIP)

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

Następujące polecenie uruchamia się po prostu, `where` Aby wyświetlić pliki języka Python, zaczynając od folderu projektu:

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

### <a name="run-server-and-run-debug-server-commands"></a>Uruchom serwer i uruchom polecenia serwera debugowania

Aby poznać sposób definiowania poleceń **serwer początkowy** i **Uruchom serwer debugowania** dla projektów sieci Web, przejrzyj [Microsoft. PythonTools. Web. targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

### <a name="install-package-for-development"></a>Zainstaluj pakiet na potrzeby programowania

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

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), używany z uprawnieniem.*

### <a name="generate-windows-installer"></a>Generuj Instalator Windows

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

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), używany z uprawnieniem.*

### <a name="generate-wheel-package"></a>Generuj pakiet kółka

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

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), używany z uprawnieniem.*

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="message-the-project-file-could-not-be-loaded"></a>Komunikat: "nie można załadować pliku projektu"

Wskazuje, że w pliku projektu występują błędy składniowe. Komunikat zawiera konkretny błąd z numerem wiersza i pozycją znaku.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Okno konsoli jest zamykane natychmiast po uruchomieniu polecenia

Użyj `ExecuteIn="consolepause"` zamiast `ExecuteIn="console"` .

### <a name="command-does-not-appear-on-the-menu"></a>Polecenie nie pojawia się w menu

Sprawdź, czy polecenie jest zawarte w `<PythonCommands>` grupie właściwości i czy nazwa na liście poleceń jest zgodna z nazwą określoną w `<Target>` elemencie.

Na przykład w następujących elementach nazwa "przykład" w grupie właściwości nie jest zgodna z nazwą "ExampleCommand" w elemencie docelowym. Program Visual Studio nie odnajdzie polecenia o nazwie "example", dlatego nie pojawia się polecenie. Użyj opcji "ExampleCommand" na liście poleceń lub Zmień nazwę elementu docelowego na "przykład".

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Komunikat: "Wystąpił błąd podczas uruchamiania \<command name> . Nie można pobrać polecenia \<target-name> z projektu. "

Wskazuje, że zawartość `<Target>` lub `<CreatePythonCommandItem>` elementów jest niepoprawna. Możliwe przyczyny to:

- Wymagany `Target` atrybut jest pusty.
- Wymagany `TargetType` atrybut jest pusty lub zawiera nierozpoznaną wartość.
- Wymagany `ExecuteIn` atrybut jest pusty lub zawiera nierozpoznaną wartość.
- `ErrorRegex`lub `WarningRegex` jest określony bez ustawienia `ExecuteIn="output"` .
- W elemencie istnieją nierozpoznane atrybuty. Można na przykład użyć `Argumnets` (błędne słowo) zamiast `Arguments` .

Wartości atrybutów mogą być puste, jeśli odwołujesz się do właściwości, która nie została zdefiniowana. Na przykład, jeśli używasz tokenu `$(StartupFile)` , ale nie zdefiniowano pliku startowego w projekcie, token jest rozpoznawany jako pusty ciąg. W takich przypadkach może być konieczne zdefiniowanie wartości domyślnej. Na przykład polecenia **Uruchom serwer** i **Uruchom serwer debugowania** zdefiniowane w szablonach projektu butelka, kolby i Django domyślnie są *manage.py* , jeśli nie określono w inny sposób pliku startowego serwera we właściwościach projektu.

### <a name="visual-studio-stops-responding-and-crashes-when-running-the-command"></a>Program Visual Studio przestaje odpowiadać i ulega awarii podczas uruchamiania polecenia

Prawdopodobnie próbujesz uruchomić polecenie konsoli za pomocą programu `ExecuteIn="output"` , w którym to przypadku program Visual Studio może ulec awarii podczas próby przeanalizowania danych wyjściowych. Zamiast tego użyj polecenia cmdlet `ExecuteIn="console"`. (Zobacz [problem 3682](https://github.com/Microsoft/PTVS/issues/3681)).

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Polecenie wykonywalne "nie jest rozpoznawane jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy"

W przypadku używania `TargetType="executable"` , wartość w `Target` musi mieć *tylko* nazwę programu bez żadnych argumentów, takich jak *Python* lub *python.exe* . Przenieś wszystkie argumenty do `Arguments` atrybutu.
