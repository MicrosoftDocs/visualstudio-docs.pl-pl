---
title: Dostosowywanie zadań kompilacji debugowania, za pomocą pliku launch.vs.json tasks.vs.json
ms.date: 02/21/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
- vsworkspacesettings.json file [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2662c09c4d131f52b0426a910d9dd4b60e6b3459
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2019
ms.locfileid: "54270128"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>Dostosowywanie kompilacji i debugowania zadań rozwoju "Otwórz Folder"

Program Visual Studio wie, jak uruchamiać wiele różnych językach i bazach kodu, ale nie wie, jak uruchomić wszystko. Jeśli użytkownik [otworzyć folder kodu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) w programie Visual Studio i Visual Studio wie, jak uruchomić kod, uruchom go następnie od razu bez przeprowadzania dodatkowej konfiguracji.

Jeśli kodu używa niestandardowych narzędzi kompilacji, które nie rozpoznaje programu Visual Studio, musisz podać kilka szczegółów konfiguracji, do uruchamiania i debugowania kodu w programie Visual Studio. Poinstruować Visual Studio, jak tworzyć kod, definiując *zadania kompilacji*. Można utworzyć jeden lub więcej zadań, aby określić wszystkie elementy wymagane przez język do kompilowanie i uruchamianie jej kodu kompilacji. Można również utworzyć dowolne zadania, które prawie wszystko, co chcesz zrobić. Na przykład można utworzyć zadania, aby wyświetlić listę zawartości folderu lub aby zmienić nazwę pliku.

Dostosowywanie bez projektu bazę kodu przy użyciu następujących *.json* plików:

|Nazwa pliku|Cel|
|-|-|
|*tasks.vs.json*|Określenie niestandardowych poleceń kompilacji i przełączniki kompilatora i dowolnego (bez kompilacji powiązane) zadania.<br>Udostępnianych za pośrednictwem **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy element menu **skonfigurować zadania**.|
|*launch.vs.json*|Określ argumenty wiersza polecenia do debugowania.<br>Udostępnianych za pośrednictwem **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy element menu **ustawienia debugowania i uruchamiania**.|
|*VSWorkspaceSettings.json*|Ogólne ustawienia, które mogą mieć wpływ na zadania i uruchamiania. Na przykład zdefiniowanie `envVars` w *VSWorkspaceSettings.json* dodaje zmienne środowiska określonego zewnętrznie uruchamianie poleceń.<br>Ten plik można tworzyć ręcznie.|

Te *.json* pliki znajdują się w ukrytym folderze o nazwie *.vs* w folderze głównym kodu. *Tasks.vs.json* i *launch.vs.json* pliki są tworzone przez program Visual Studio na zgodnie z potrzebami, po wybraniu **skonfigurować zadania** lub **debugowania Ustawienia i uruchamiania** do pliku lub folderu w **Eksploratora rozwiązań**. Te *.json* pliki są ukryte, ponieważ użytkownicy zwykle nie chcesz zaewidencjonować je w kontroli źródła. Jednak jeśli chcesz mieć możliwość sprawdzania ich do kontroli źródła, przeciągnij pliki w folderze głównym w bazie kodu, gdzie są one widoczne.

> [!TIP]
> Aby wyświetlić ukryte pliki w programie Visual Studio, wybierz **Pokaż wszystkie pliki** znajdujący się na **Eksploratora rozwiązań** paska narzędzi.

## <a name="define-tasks-with-tasksvsjson"></a>Definiowanie zadań za pomocą pliku tasks.vs.json

Można zautomatyzować skrypty kompilacji lub innych zewnętrznych operacji na plikach, znajdującym się w bieżącym obszarze roboczym, uruchamiając je jako zadania bezpośrednio w środowisku IDE. Można skonfigurować nowe zadanie, kliknij prawym przyciskiem myszy pliku lub folderu i wybierając **skonfigurować zadania**.

![Konfigurowanie menu zadania](../ide/media/customize-configure-tasks-menu.png)

Tworzy (lub zostanie otwarty) *tasks.vs.json* w pliku *.vs* folderu. Można zdefiniować zadania kompilacji lub dowolnego zadania w tym pliku, a następnie wywołaj go przy użyciu nazwy, należy nadać mu z **Eksploratora rozwiązań** prawym przyciskiem myszy.

Niestandardowe zadania można dodawać do pojedynczych plików lub do wszystkich plików określonego typu. Na przykład pliki pakietu NuGet można skonfigurować, aby zadanie "Przywróć Packages" lub wszystkie pliki źródłowe można skonfigurować tak, aby zadanie analizy statycznej, takich jak linter dla wszystkich *js* plików.

### <a name="define-custom-build-tasks"></a>Definiowanie zadań kompilacji niestandardowej

Jeśli baza kodu używa niestandardowych narzędzi kompilacji, które nie rozpoznaje programu Visual Studio, nie można uruchomić i debugowania kodu w programie Visual Studio, dopóki nie można wykonać kilka kroków konfiguracji. Program Visual Studio udostępnia *zadania kompilacji* w przypadku, gdy program Visual Studio można stwierdzić sposób tworzenia, ponownej kompilacji i czyszczenia kodu. *Tasks.vs.json* kompilacji pozamałżeńskie pliku zadania pętli wewnętrzny rozwoju Visual Studio niestandardowe narzędzia build tools używane przez bazy kodu.

Należy wziąć pod uwagę bazy kodu, który składa się z pojedynczego C# pliku o nazwie *hello.cs*. *Pliku reguł programu make* dla takiego kodu może wyglądać następująco:

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

Aby uzyskać takie *pliku reguł programu make* , zawierający kompilacji czyste, a odbudować elementów docelowych, można zdefiniować następujące *tasks.vs.json* pliku. Zawiera on trzy zadania kompilacji na potrzeby kompilowania, ponownie skompilować i czyszczenia kodu za pomocą NMAKE jako narzędzia kompilacji.

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

Po zdefiniowaniu zadań kompilacji w *tasks.vs.json*, dodatkowe kliknij prawym przyciskiem myszy menu (menu kontekstowe) elementy są dodawane do odpowiednich plików w **Eksploratora rozwiązań**. Na przykład "kompilacja", "rebuild" i "czysta" opcje są dodawane do menu kontekstowego dowolnego *pliku reguł programu make* plików.

![menu kontekstowe pliku reguł programu make, kompilacji, ponownej kompilacji i czyszczenia](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Polecenia są wyświetlane w menu kontekstowym w obszarze **skonfigurować zadania** polecenia ze względu na ich `contextType` ustawienia. "kompilacja", "rebuild" i "czysta" są poleceń kompilacji, aby były widoczne w sekcji kompilacji w trakcie menu kontekstowego.

Zadanie podrzędne jest wykonywane po wybraniu jednej z poniższych opcji. Dane wyjściowe pojawia się w **dane wyjściowe** okna i błędy kompilacji są wyświetlane w **lista błędów**.

### <a name="define-arbitrary-tasks"></a>Definiowanie dowolnych zadań

Można zdefiniować dowolnego zadania w *tasks.vs.json* pliku, aby wszystko, co chcesz zrobić. Na przykład można zdefiniować zadania, aby wyświetlić nazwę aktualnie wybranego pliku w **dane wyjściowe** okna, lub aby wyświetlić listę plików w określonym katalogu.

W poniższym przykładzie przedstawiono *tasks.vs.json* pliku, który definiuje jedno zadanie. Po wywołaniu, zadanie Wyświetla nazwę pliku z aktualnie wybranej *js* pliku.

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

- `taskName` Określa nazwę, która jest wyświetlana w menu kontekstowym.
- `appliesTo` Określa pliki, które można wykonać polecenia na.
- `command` Właściwość określa polecenie do wywołania. W tym przykładzie `COMSPEC` zmienna środowiskowa jest używany do identyfikowania interpretera wiersza polecenia, zwykle *cmd.exe*.
- `args` Właściwość określa argumenty do przekazania do wywoływanej polecenia.
- `${file}` — Makro pobiera wybranego pliku w **Eksploratora rozwiązań**.

Po zapisaniu *tasks.vs.json*, kliknąć prawym przyciskiem myszy na dowolnym *js* plików w folderze, a następnie wybierz **Echo, nazwa_pliku**. Nazwa pliku jest wyświetlana w **dane wyjściowe** okna.

> [!NOTE]
> Jeśli nie zawiera kodu *tasks.vs.json* pliku, możesz ją utworzyć, wybierając **skonfigurować zadania** menu kontekście lub kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań**.

W następnym przykładzie zdefiniowano klasę task, która zawiera listę plików i podfolderów *bin* katalogu.

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

- `${outDir}` zdefiniowano niestandardowego, który jest pierwszy przed `tasks` bloku. Następnie jest wywoływana w `args` właściwości.

To zadanie jest stosowana do wszystkich plików. Po otwarciu menu kontekstowe dla każdego pliku w **Eksploratora rozwiązań**, nazwa zadania **danych wyjściowych listy** pojawia się u dołu menu. Po wybraniu **listy danych wyjściowych**, zawartość *bin* katalogu są wymienione w **dane wyjściowe** okna w programie Visual Studio.

![Dowolne zadanie w menu kontekstowym](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Zakres ustawień

Wiele *tasks.vs.json* pliki mogą znajdować się w głównych i podkatalogi bazę kodu. Ten projekt umożliwia elastyczność mają różne zachowanie w podkatalogach różne bazy kodu. Visual Studio agreguje lub zastępuje ustawienia w całej bazie kodu, priorytetyzowanie plików w następującej kolejności:

- Ustawienia plików w folderze głównym *.vs* katalogu.
- Katalog, w której jest obliczany ustawienie.
- Katalog nadrzędny bieżący katalog do katalogu głównego.
- Ustawienia plików w katalogu głównym.

Mają zastosowanie następujące reguły agregacji *tasks.vs.json* i *VSWorkspaceSettings.json* plików. Instrukcje dotyczące sposobu ustawienia w innym pliku są agregowane zobacz sekcję odpowiednie dla tego pliku, w tym artykule.

### <a name="properties-for-tasksvsjson"></a>Właściwości pliku tasks.vs.json

W tej sekcji opisano niektóre właściwości, można określić w *tasks.vs.json*.

#### <a name="appliesto"></a>AppliesTo

Można utworzyć zadania dla dowolnego pliku lub folderu, określając jej nazwę w `appliesTo` pole, na przykład `"appliesTo": "hello.js"`. Następujące maski plików mogą być używane jako wartości:

|||
|-|-|
|`"*"`| zadanie jest dostępne dla wszystkich plików i folderów w obszarze roboczym|
|`"*/"`| zadanie jest dostępne dla wszystkich folderów w obszarze roboczym|
|`"*.js"`| zadanie jest dostępny dla wszystkich plików z rozszerzeniem *js* w obszarze roboczym|
|`"/*.js"`| zadanie jest dostępny dla wszystkich plików z rozszerzeniem *js* w katalogu głównym obszaru roboczego|
|`"src/*/"`| zadanie jest dostępne dla wszystkich podfolderów *src* folderu|
|`"makefile"`| zadanie jest dostępny dla wszystkich *pliku reguł programu make* plików w obszarze roboczym|
|`"/makefile"`| zadanie jest dostępna tylko dla *pliku reguł programu make* w katalogu głównym obszaru roboczego|

#### <a name="macros-for-tasksvsjson"></a>Makra dla tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Określa wszystkie zmienne środowiskowe (np. ${env. PATH}, ${env.COMSPEC} i tak dalej) który jest skonfigurowany dla wiersza polecenia dla deweloperów. Aby uzyskać więcej informacji, zobacz [wiersz polecenia programisty dla programu Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Pełna ścieżka do folderu obszaru roboczego (na przykład *C:\sources\hello*)|
|`${file}`| Pełna ścieżka pliku lub folderu wybrana do uruchomienia tego zadania względem (na przykład *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Względna ścieżka do pliku lub folderu (na przykład *src\hello.js*)|
|`${fileBasename}`| Nazwa pliku bez ścieżki i rozszerzenia (na przykład *hello*)|
|`${fileDirname}`| Pełna ścieżka do pliku, z wyjątkiem nazwy pliku (na przykład *C:\sources\hello\src*)|
|`${fileExtname}`| Rozszerzenie wybranego pliku (na przykład *js*)|

## <a name="configure-debugging-with-launchvsjson"></a>Konfigurowanie debugowania za pomocą pliku launch.vs.json

1. Aby skonfigurować usługi w bazie kodu do debugowania, **Eksploratora rozwiązań** wybierz **ustawienia debugowania i uruchamiania** element menu w menu kliknij prawym przyciskiem myszy lub kontekstu pliku wykonywalnego.

   ![Ustawienia debugowania i uruchamiania menu kontekstowe](media/customize-debug-launch-menu.png)

1. W **wybierz debuger** okno dialogowe, wybierz jedną z opcji, a następnie wybierz **wybierz** przycisku.

   ![Wybierz okno dialogowe debugera](media/customize-select-a-debugger.png)

   Jeśli *launch.vs.json* plik już nie istnieje, jest on tworzony.

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

1. Następnie kliknij prawym przyciskiem myszy plik wykonywalny w **Eksploratora rozwiązań**i wybierz polecenie **Ustaw jako element startowy**.

   Plik wykonywalny jest wyznaczony jako element startowy dla kodu i debugowania **Start** zmieniony tytuł przycisku, aby odzwierciedlić nazwę plik wykonywalny.

   ![Dostosowany przycisk Start](media/customize-start-button.png)

   Po wybraniu **F5**, debuger uruchamia i zatrzymuje w dowolnym punkcie przerwania może zostały skonfigurowane. Wszystkie znajomego debugera systemu windows są dostępne i funkcjonalne.

### <a name="specify-arguments-for-debugging"></a>Określ argumenty do debugowania

Można określić argumenty wiersza polecenia do przekazywania do debugowania w *launch.vs.json* pliku. Dodaj argumenty `args` tablicy, jak pokazano w poniższym przykładzie:

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

Po zapisaniu tego pliku nazwa nowej konfiguracji, który pojawia się na liście rozwijanej debugowania. Ponadto możesz wybrać go, aby uruchomić debuger. Można utworzyć wiele konfiguracji debugowania, jak chcesz.

![Listy rozwijanej konfiguracji debugowania](media/customize-debug-configurations.png)

> [!NOTE]
> `configurations` Tablicy właściwości *launch.vs.json* są odczytywane z dwóch lokalizacji pliku&mdash;katalog główny bazie kodu i *.vs* katalogu. Jeśli występuje konflikt, pierwszeństwo mają wartość w *.vs\launch.vs.json*.

## <a name="define-workspace-settings-in-vsworkspacesettingsjson"></a>Zdefiniuj ustawienia obszaru roboczego w VSWorkspaceSettings.json

Można określić ogólne ustawienia, które mogą mieć wpływ na zadania i uruchamiane w programie *VSWorkspaceSettings.json* pliku. Na przykład, jeśli zdefiniujesz `envVars` w *VSWorkspaceSettings.json*, program Visual Studio dodaje zmienne środowiskowe określony do poleceń, które są uruchamiane na zewnątrz. Aby użyć tego pliku, musisz utworzyć go ręcznie.

## <a name="additional-settings-files"></a>Pliki dodatkowe ustawienia

Oprócz tych trzech *.json* pliki opisane w tym temacie, Visual Studio również odczytuje ustawienia z niektórych dodatkowych plików, jeśli nie istnieją w bazie kodu.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Program Visual Studio odczytuje ograniczone ustawienia z pliku o nazwie *settings.json*, jeśli znajduje się w katalogu o nazwie *.vscode*. Ta funkcjonalność jest dostarczana dla ścieżek bazowych kodu, które wcześniej zostały opracowane w programie Visual Studio Code. Obecnie jedynym ustawieniem, to znaczy odczytywać *.vscode\settings.json* jest `files.exclude`, która filtruje pliki wizualnie w Eksploratorze rozwiązań i niektóre narzędzia do wyszukiwania.

Może mieć dowolną liczbę *.vscode\settings.json* pliki w bazie kodu. Odczyt z pliku ustawień dotyczą katalog nadrzędny tworzonego *.vscode* i wszystkich podkatalogach.

### <a name="gitignore"></a>.gitignore

*.gitignore* pliki są używane do poinformować usługę Git, które plików do ignorowania; oznacza to, które pliki i katalogi nie chcesz zaewidencjonować. *.gitignore* pliki są zazwyczaj dołączone jako część bazy kodu, aby ustawienia mogą być udostępniane innym programistom bazy kodu. Program Visual Studio odczytuje wzorce w *.gitignore* pliki, aby filtrować elementy wizualne i niektóre wyszukiwania narzędzi.

Odczytywanie ustawień *.gitignore* pliku są stosowane do katalogu nadrzędnego i wszystkich podkatalogach.

## <a name="see-also"></a>Zobacz także

- [Tworzenie kodu bez projektów ani rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Otwórz Folder projektów w języku C++](/cpp/ide/non-msbuild-projects)
- [Projekty CMake w języku C++](/cpp/ide/cmake-tools-for-visual-cpp)
- [NMAKE — dokumentacja](/cpp/build/nmake-reference)
- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)