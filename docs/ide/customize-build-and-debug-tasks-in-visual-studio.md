---
title: Dostosuj zadania debugowania kompilacji za pomocą zadań. vs. JSON uruchamiania. vs. JSON
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a9101db18c8c61f249d9f0b818a75024270a079
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652573"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>Dostosowywanie zadań kompilacji i debugowania dla opracowywania aplikacji "Otwieranie folderu"

Program Visual Studio wie, jak uruchamiać wiele różnych języków i baz kodu, ale nie wie, jak uruchomić wszystko. Jeśli [otwarto folder kodu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) w programie Visual Studio, a program Visual Studio wie, jak uruchomić kod, możesz go uruchomić od razu bez żadnej dodatkowej konfiguracji.

Jeśli baza kodu używa niestandardowych narzędzi kompilacji, które nie są rozpoznawane przez program Visual Studio, musisz podać szczegóły konfiguracji, aby uruchomić i debugować kod w programie Visual Studio. Nakazujesz programowi Visual Studio tworzenie kodu przez definiowanie *zadań kompilacji*. Można utworzyć co najmniej jedno zadanie kompilacji, aby określić wszystkie elementy, które język musi skompilować i uruchomić swój kod. Możesz również utworzyć dowolne zadania, które mogą robić niemal wszystko. Na przykład można utworzyć zadanie, aby wyświetlić listę zawartości folderu lub zmienić nazwę pliku.

Dostosuj bazę kodu o niemniejszej projekcie przy użyciu następujących plików *JSON* :

|Nazwa pliku|Cel|
|-|-|
|*Tasks. vs. JSON*|Określ niestandardowe polecenia kompilacji i przełączniki kompilatora oraz dowolne zadania (niepowiązane z kompilacją).<br>Dostępne za pośrednictwem **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy element menu **Konfiguruj zadania**.|
|*Uruchom plik. vs. JSON*|Określ argumenty wiersza polecenia dla debugowania.<br>Dostępne za pośrednictwem **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy element menu **Ustawienia debugowania i uruchamiania**.|

Te pliki *. JSON* znajdują się w ukrytym folderze o nazwie *. vs* w folderze głównym bazy kodu. Pliki *Tasks. vs. JSON* i *Launch. vs. JSON* są tworzone przez program Visual Studio w zależności od tego, gdy użytkownik wybierze opcję **Skonfiguruj zadania** lub **Debuguj i uruchom ustawienia** dla pliku lub folderu w **Eksplorator rozwiązań**. Te pliki *. JSON* są ukryte, ponieważ zazwyczaj użytkownicy nie chcą zaewidencjonować ich do kontroli źródła. Jeśli jednak chcesz mieć możliwość zaewidencjonowania ich w kontroli źródła, przeciągnij pliki do katalogu głównego bazy kodu, gdzie są widoczne.

> [!TIP]
> Aby wyświetlić ukryte pliki w programie Visual Studio, wybierz przycisk **Pokaż wszystkie pliki** na pasku narzędzi **Eksplorator rozwiązań** .

## <a name="define-tasks-with-tasksvsjson"></a>Definiowanie zadań przy użyciu zadań. vs. JSON

Możesz zautomatyzować skrypty kompilacji lub wszystkie inne operacje zewnętrzne na plikach znajdujących się w bieżącym obszarze roboczym, uruchamiając je jako zadania bezpośrednio w środowisku IDE. Nowe zadanie można skonfigurować, klikając prawym przyciskiem myszy plik lub folder, a następnie wybierając pozycję **Konfiguruj zadania**.

![Menu Konfiguruj zadania](../ide/media/customize-configure-tasks-menu.png)

Spowoduje to utworzenie (lub otwarcie) pliku *Tasks. vs. JSON* w folderze *. vs* . Można zdefiniować zadanie kompilacji lub dowolne zadanie w tym pliku, a następnie wywołać je przy użyciu nazwy podaną w **Eksplorator rozwiązań** kliknięciu prawym przyciskiem myszy.

Zadania niestandardowe można dodawać do poszczególnych plików lub do wszystkich plików określonego typu. Na przykład pliki pakietów NuGet można skonfigurować w taki sposób, aby miało zadanie "Przywróć pakiety", lub wszystkie pliki źródłowe można skonfigurować tak, aby miało zadanie statycznej analizy, takie jak Linter dla wszystkich plików *js* .

### <a name="define-custom-build-tasks"></a>Definiowanie niestandardowych zadań kompilacji

Jeśli baza kodu używa niestandardowych narzędzi kompilacji, które nie są rozpoznawane przez program Visual Studio, nie można uruchomić i debugować kodu w programie Visual Studio, dopóki nie zostaną wykonane pewne czynności konfiguracyjne. Program Visual Studio zawiera *zadania kompilacji* , w których można poinformować program Visual Studio, jak skompilować, skompilować i wyczyścić swój kod. Plik zadania Build Tasks *. vs. JSON* Couples wewnętrzną pętlę programistyczną programu Visual Studio do niestandardowych narzędzi kompilacji używanych przez bazę kodu.

Rozważmy bazę kodu, która składa C# się z pojedynczego pliku o nazwie *Hello.cs*. Plik *reguł programu make* dla takiej bazy kodu może wyglądać następująco:

<!-- markdownlint-disable MD010 -->
```makefile
build: directory hello.exe

hello.exe: hello.cs
    csc -debug hello.cs /out:bin\hello.exe

clean:
    del bin\hello.exe bin\hello.pdb

rebuild: clean build

directory: bin

bin:
    md bin
```
<!-- markdownlint-enable MD010 -->

W przypadku takiego pliku *reguł programu make* , który zawiera elementy docelowe kompilacji, czyszczenia i odbudowywania, można zdefiniować następujące pliki *zadań. vs. JSON* . Zawiera trzy zadania kompilacji do kompilowania, ponownego kompilowania i czyszczenia bazy kodu przy użyciu NMAKE jako narzędzia do kompilowania.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "makefile-build",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "build",
      "command": "nmake",
      "args": [ "build" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-clean",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "clean",
      "command": "nmake",
      "args": [ "clean" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-rebuild",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "rebuild",
      "command": "nmake",
      "args": [ "rebuild" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    }
  ]
}
```

Po zdefiniowaniu zadań kompilacji w pliku *Tasks. vs. JSON*do odpowiednich plików w **Eksplorator rozwiązań**są dodawane dodatkowe menu z prawym przyciskiem myszy (menu kontekstowe). W tym przykładzie opcje "build", "build" i "Clean" są dodawane do menu kontekstowego dowolnych plików *reguł programu make* .

![menu kontekstowe pliku reguł programu make z kompilacjami, odbudowywaniem i czyszczeniem](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Polecenia pojawiają się w menu kontekstowym w ramach polecenia **Konfiguruj zadania** z powodu ich `contextType` ustawień. "Kompilacja", "Kompiluj" i "Clean" są poleceniami kompilacji, więc są one wyświetlane w sekcji Kompilacja w środku menu kontekstowego.

Po wybraniu jednej z tych opcji zadanie jest wykonywane. Dane wyjściowe pojawiają się w oknie **danych wyjściowych** , a błędy kompilacji pojawiają się w **Lista błędów**.

### <a name="define-arbitrary-tasks"></a>Definiowanie dowolnych zadań

Możesz zdefiniować dowolne zadania w pliku *Tasks. vs. JSON* , aby zrobić to w dowolny sposób. Na przykład można zdefiniować zadanie, aby wyświetlić nazwę aktualnie wybranego pliku w oknie **danych wyjściowych** lub listę plików w określonym katalogu.

W poniższym przykładzie przedstawiono plik *Tasks. vs. JSON* , który definiuje pojedyncze zadanie. Po wywołaniu, zadanie wyświetla nazwę pliku aktualnie wybranego pliku *js* .

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.js",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "echo ${file}" ]
    }
  ]
}
```

- `taskName` określa nazwę, która pojawia się w menu rozwijanym prawym przyciskiem myszy.
- `appliesTo` określa, które pliki można wykonać polecenie.
- Właściwość `command` Określa polecenie do wywołania. W tym przykładzie zmienna środowiskowa `COMSPEC` służy do identyfikowania interpretera wiersza polecenia, zazwyczaj *cmd. exe*.
- Właściwość `args` określa argumenty, które mają zostać przekazane do wywoływanego polecenia.
- Makro `${file}` pobiera wybrany plik z **Eksplorator rozwiązań**.

Po zapisaniu *zadań. vs. JSON*można kliknąć prawym przyciskiem myszy dowolny plik *js* w folderze, a następnie wybrać polecenie **echo filename**. Nazwa pliku zostanie wyświetlona w oknie **danych wyjściowych** .

> [!NOTE]
> Jeśli baza kodu nie zawiera pliku *Tasks. vs. JSON* , można go utworzyć, wybierając pozycję **Konfiguruj zadania** w menu kontekstowym lub prawym przyciskiem myszy pliku w **Eksplorator rozwiązań**.

W następnym przykładzie zdefiniowano zadanie, które wyświetla listę plików i podfolderów katalogu *bin* .

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "List Outputs",
      "appliesTo": "*",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "dir ${outDir}" ]
    }
  ]
}
```

- `${outDir}` jest makrem niestandardowym, które jest najpierw zdefiniowane przed blokiem `tasks`. Jest on następnie wywoływany we właściwości `args`.

To zadanie dotyczy wszystkich plików. Po otwarciu menu kontekstowego dla każdego pliku w **Eksplorator rozwiązań**, dane **wyjściowe listy** nazwa zadania są wyświetlane u dołu menu. Po wybraniu opcji dane **wyjściowe listy**zawartość katalogu *bin* zostanie wyświetlona w oknie **danych wyjściowych** w programie Visual Studio.

![Dowolne zadanie w menu kontekstowym](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Zakres ustawień

Wiele plików *Tasks. vs. JSON* może istnieć w katalogu głównym i podkatalogach bazy kodu. Ten projekt pozwala elastycznie mieć inne zachowanie w różnych podkatalogach bazy kodu. Program Visual Studio agreguje lub zastępuje ustawienia w całej bazie kodu, priorytetyzacji plików w następującej kolejności:

- Pliki ustawień w katalogu programu *vs* folderu głównego.
- Katalog, w którym jest obliczane ustawienie.
- Katalog nadrzędny bieżącego katalogu, cały sposób do katalogu głównego.
- Pliki ustawień w katalogu głównym.

Te reguły agregacji mają zastosowanie do *zadań. vs. JSON*. Aby uzyskać informacje na temat sposobu agregowania ustawień w innym pliku, zapoznaj się z odpowiednią sekcją tego pliku w tym artykule.

### <a name="properties-for-tasksvsjson"></a>Właściwości Tasks. vs. JSON

W tej sekcji opisano niektóre właściwości, które można określić w pliku *Tasks. vs. JSON*.

#### <a name="appliesto"></a>Zignorowan

Można utworzyć zadania dla dowolnego pliku lub folderu, określając jego nazwę w polu `appliesTo`, na przykład `"appliesTo": "hello.js"`. Następujące maski plików mogą być używane jako wartości:

|||
|-|-|
|`"*"`| zadanie jest dostępne dla wszystkich plików i folderów w obszarze roboczym|
|`"*/"`| zadanie jest dostępne dla wszystkich folderów w obszarze roboczym|
|`"*.js"`| zadanie jest dostępne dla wszystkich plików z rozszerzeniem *js* w obszarze roboczym|
|`"/*.js"`| zadanie jest dostępne dla wszystkich plików z rozszerzeniem *js* w folderze głównym obszaru roboczego|
|`"src/*/"`| zadanie jest dostępne dla wszystkich podfolderów folderu *src*|
|`"makefile"`| zadanie jest dostępne dla wszystkich plików pliku *reguł programu make* w obszarze roboczym|
|`"/makefile"`| zadanie jest dostępne tylko dla pliku *reguł programu make* w folderze głównym obszaru roboczego|

#### <a name="macros-for-tasksvsjson"></a>Makra zadań. vs. JSON

|||
|-|-|
|`${env.<VARIABLE>}`| Określa zmienną środowiskową (na przykład $ {ENV. PATH}, $ {ENV. wywołana} itd.), która jest ustawiona dla wiersza polecenia dewelopera. Aby uzyskać więcej informacji, zobacz [wiersz polecenia programisty dla programu Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Pełna ścieżka do folderu obszaru roboczego (na przykład *C:\sources\hello*)|
|`${file}`| Pełna ścieżka pliku lub folderu wybranego do uruchomienia tego zadania (na przykład *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Ścieżka względna do pliku lub folderu (na przykład *src\hello.js*)|
|`${fileBasename}`| Nazwa pliku bez ścieżki lub rozszerzenia (na przykład *Witaj*)|
|`${fileDirname}`| Pełna ścieżka do pliku, z wyłączeniem nazwy pliku (na przykład *C:\sources\hello\src*)|
|`${fileExtname}`| Rozszerzenie wybranego pliku (na przykład *. js*)|

## <a name="configure-debugging-with-launchvsjson"></a>Konfigurowanie debugowania przy użyciu pliku Launch. vs. JSON

1. Aby skonfigurować bazę kodu do debugowania, w **Eksplorator rozwiązań** wybierz element menu **Ustawienia debugowania i uruchamiania** w menu kontekstowym lub prawym przyciskiem myszy pliku wykonywalnego.

   ![Menu kontekstowe ustawień debugowania i uruchamiania](media/customize-debug-launch-menu.png)

1. W oknie dialogowym **Wybierz debuger** wybierz opcję, a następnie wybierz przycisk **Wybierz** .

   ![Okno dialogowe Wybieranie debugera](media/customize-select-a-debugger.png)

   Jeśli plik *Launch. vs. JSON* jeszcze nie istnieje, zostanie utworzony.

   ```json
   {
     "version": "0.2.1",
     "defaults": {},
     "configurations": [
       {
         "type": "default",
         "project": "bin\\hello.exe",
         "name": "hello.exe"
       }
     ]
   }
   ```

1. Następnie kliknij prawym przyciskiem myszy plik wykonywalny w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Ustaw jako element startowy**.

   Plik wykonywalny jest wyznaczono jako element startowy bazy kodu, a tytuł przycisku **uruchamiania** debugowania zmienia się w celu odzwierciedlenia nazwy pliku wykonywalnego.

   ![Dostosowany przycisk startowy](media/customize-start-button.png)

   Po wybraniu klawisza **F5**debuger zostanie uruchomiony i zatrzymany w dowolnym punkcie przerwania, który został już ustawiony. Wszystkie znane okna debugera są dostępne i funkcjonalne.

   > [!IMPORTANT]
   > Aby uzyskać dodatkowe informacje na temat niestandardowych zadań kompilacji i C++ debugowania w projektach otwartych folderów, zobacz [Otwieranie folderu C++ obsługa dla systemów kompilacji w programie Visual Studio](/cpp/build/open-folder-projects-cpp).

### <a name="specify-arguments-for-debugging"></a>Określ argumenty dla debugowania

Można określić argumenty wiersza polecenia, które zostaną przekazane do debugowania w pliku *Launch. vs. JSON* . Dodaj argumenty w tablicy `args`, jak pokazano w następującym przykładzie:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe"
    },
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe a1",
      "args": [ "a1" ]
    }
  ]
}
```

Po zapisaniu tego pliku Nazwa nowej konfiguracji zostanie wyświetlona na liście rozwijanej cel debugowania i można ją wybrać, aby uruchomić debuger. Można utworzyć dowolną liczbę konfiguracji debugowania.

![Lista rozwijana konfiguracji debugowania](media/customize-debug-configurations.png)

> [!NOTE]
> Właściwość Array `configurations` w pliku *Launch. vs. JSON* jest odczytywana z dwóch lokalizacji plików &mdash;the katalogu głównego dla bazy kodu i katalogu *. vs* . W razie wystąpienia konfliktu priorytet jest przyznany wartości w *. vs\launch.vs.JSON*.

## <a name="additional-settings-files"></a>Dodatkowe pliki ustawień

Oprócz trzech plików *. JSON* opisanych w tym temacie program Visual Studio odczytuje również ustawienia z pewnych dodatkowych plików, jeśli istnieją w bazie kodu.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Program Visual Studio odczytuje ograniczone ustawienia z pliku o nazwie *Settings. JSON*, jeśli znajduje się on w katalogu o nazwie *. programu vscode*. Ta funkcja jest dostępna dla baz kodu, które zostały wcześniej opracowane w Visual Studio Code. Obecnie jedynym ustawieniem, które jest odczytywane z *. vscode\settings.JSON* , jest `files.exclude`, które filtruje pliki wizualnie w Eksplorator rozwiązań i z niektórych narzędzi do wyszukiwania.

W bazie kodu może być dowolna liczba plików *. vscode\settings.JSON* . Ustawienia odczytane z tego pliku są stosowane do katalogu nadrzędnego elementu *. programu vscode* i wszystkich jego podkatalogów.

### <a name="gitignore"></a>. gitignore

pliki *. gitignore* są używane do poinformowania narzędzia Git o ignorowaniu plików; oznacza to, które pliki i katalogi nie mają być zaewidencjonowania. pliki *. gitignore* są zwykle dołączone jako część bazy kodu, dzięki czemu można udostępniać te ustawienia wszystkim deweloperom bazy kodu. Program Visual Studio odczytuje wzorce w plikach *. gitignore* , aby przefiltrować elementy wizualnie i z niektórych narzędzi do wyszukiwania.

Ustawienia odczytane z pliku *. gitignore* są stosowane do jego katalogu nadrzędnego i wszystkich podkatalogów.

## <a name="see-also"></a>Zobacz także

- [Opracowywanie kodu bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Otwieranie folderu projektów na potrzeby języka C++](/cpp/build/open-folder-projects-cpp)
- [CMake projekty dlaC++](/cpp/build/cmake-projects-in-visual-studio)
- [Odwołanie NMAKE](/cpp/build/reference/nmake-reference)
- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
