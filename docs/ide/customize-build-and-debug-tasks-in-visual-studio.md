---
title: Dostosowywanie zadań debugowania kompilacji przy użyciu pliku tasks.vs.json launch.vs.json
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e912459f45086b1bf5f96a9458f006354e982ffd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76542688"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>Dostosowywanie zadań kompilacji i debugowania dla tworzenia folderów "Otwórz folder"

Visual Studio wie, jak uruchomić wiele różnych języków i baz kodu, ale nie wie, jak uruchomić wszystko. Jeśli [otwarto folder kodu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) w programie Visual Studio, a program Visual Studio wie, jak uruchomić kod, można go uruchomić od razu bez żadnej dodatkowej konfiguracji.

Jeśli baza kodu używa niestandardowych narzędzi kompilacji, których visual studio nie rozpoznaje, należy podać niektóre szczegóły konfiguracji, aby uruchomić i debugować kod w programie Visual Studio. Instruować program Visual Studio, jak utworzyć kod, definiując *zadania kompilacji.* Można utworzyć jedno lub więcej zadań kompilacji, aby określić wszystkie elementy, których język musi utworzyć i uruchomić jego kod. Można również tworzyć dowolne zadania, które mogą wykonywać niemal wszystko, co chcesz. Można na przykład utworzyć zadanie, aby wyświetlić listę zawartości folderu lub zmienić nazwę pliku.

Dostosuj bazę kodu bez projektu, używając następujących plików *.json:*

|Nazwa pliku|Przeznaczenie|
|-|-|
|*zadania.vs.json*|Określ niestandardowe polecenia kompilacji i przełączniki kompilatora oraz dowolne zadania (niezwiązane z kompilacją).<br>Dostęp do niego za pomocą elementu menu **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy **pozycję Konfiguruj zadania**.|
|*launch.vs.json*|Określ argumenty wiersza polecenia do debugowania.<br>Dostęp do niego za pomocą elementu menu **Eksplorator rozwiązań** **Debugowanie i ustawienia uruchamiania**.|

Te pliki *.json* znajdują się w ukrytym folderze o nazwie *.vs* w folderze głównym bazy kodu. Pliki *tasks.vs.json* i *launch.vs.json* są tworzone przez program Visual Studio zgodnie z potrzebami po wybraniu opcji **Konfiguruj zadania** lub **Ustawienia debugowania i uruchamiania** w pliku lub folderze w **Eksploratorze rozwiązań**. Te pliki *.json* są ukryte, ponieważ użytkownicy zazwyczaj nie chcą zaewidencjonować ich do kontroli źródła. Jednak jeśli chcesz mieć możliwość sprawdzenia ich do kontroli źródła, przeciągnij pliki do katalogu głównego bazy kodu, gdzie są widoczne.

> [!TIP]
> Aby wyświetlić ukryte pliki w programie Visual Studio, wybierz przycisk **Pokaż wszystkie pliki** na pasku narzędzi **Eksploratora rozwiązań.**

## <a name="define-tasks-with-tasksvsjson"></a>Definiowanie zadań za pomocą pliku tasks.vs.json

Skrypty kompilacji lub inne operacje zewnętrzne dotyczące plików w bieżącym obszarze roboczym można zautomatyzować, uruchamiając je jako zadania bezpośrednio w ide. Nowe zadanie można skonfigurować, klikając prawym przyciskiem myszy plik lub folder i wybierając pozycję **Konfiguruj zadania**.

![Menu Konfigurowanie zadań](../ide/media/customize-configure-tasks-menu.png)

Spowoduje to utworzenie (lub otwarcie) pliku *tasks.vs.json* w folderze *.vs.* Można zdefiniować zadanie kompilacji lub dowolne zadanie w tym pliku, a następnie wywołać je przy użyciu nazwy nadawanej z menu **Eksploratora rozwiązań, które** zostało kliknąć prawym przyciskiem myszy.

Zadania niestandardowe można dodawać do poszczególnych plików lub do wszystkich plików określonego typu. Na przykład pliki pakietów NuGet można skonfigurować tak, aby miały zadanie "Przywróć pakiety" lub wszystkie pliki źródłowe można skonfigurować tak, aby miały zadanie analizy statycznej, takie jak linter dla wszystkich plików *.js.*

### <a name="define-custom-build-tasks"></a>Definiowanie niestandardowych zadań kompilacji

Jeśli baza kodu używa niestandardowych narzędzi kompilacji, których program Visual Studio nie rozpoznaje, nie można uruchomić i debugować kodu w programie Visual Studio, dopóki nie wykonasz niektórych kroków konfiguracji. Visual Studio udostępnia *zadania kompilacji,* w których można powiedzieć visual studio, jak tworzyć, odbudowywać i czyścić kod. Plik zadań *kompilacji tasks.vs.json* łączy wewnętrzną pętlę rozwoju programu Visual Studio z niestandardowymi narzędziami kompilacji używanymi przez bazę kodu.

Należy wziąć pod uwagę codebase, który składa się z jednego pliku C# o nazwie *hello.cs*. *Plik makefile* dla takiej bazy kodu może wyglądać następująco:

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

Dla takiego *pliku makefile,* który zawiera kompilacji, czyszczenia i przebudowy obiektów docelowych, można zdefiniować następujące *tasks.vs.json* pliku. Zawiera trzy zadania kompilacji do tworzenia, przebudowy i czyszczenia bazy kodu, przy użyciu NMAKE jako narzędzie kompilacji.

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

Po zdefiniowaniu zadań kompilacji w *pliku tasks.vs.json*do odpowiednich plików w **Eksploratorze rozwiązań**zostaną dodane dodatkowe elementy menu menu (menu kontekstowe) po zdefiniowaniu zadań kompilacji w witrynie Tasks.vs.json . W tym przykładzie opcje "build", "rebuild" i "clean" są dodawane do menu kontekstowego dowolnych plików *makefile.*

![menu kontekstowe makefile z kompilacją, przebudową i czyszczeniem](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Polecenia są wyświetlane w menu kontekstowym w menu `contextType` **Konfiguruj zadania** ze względu na ich ustawienia. "build", "rebuild" i "clean" są poleceniami kompilacji, więc pojawiają się w sekcji kompilacji w środku menu kontekstowego.

Po wybraniu jednej z tych opcji zadanie zostanie wykonane. Dane wyjściowe są wyświetlane w oknie **Dane wyjściowe,** a błędy kompilacji są wyświetlane na **liście błędów**.

### <a name="define-arbitrary-tasks"></a>Definiowanie dowolnych zadań

Można zdefiniować dowolne zadania w pliku *tasks.vs.json,* aby wykonać prawie wszystko, co chcesz. Na przykład można zdefiniować zadanie, aby wyświetlić nazwę aktualnie wybranego pliku w oknie **Dane wyjściowe** lub wyświetlić listę plików w określonym katalogu.

W poniższym przykładzie przedstawiono plik *tasks.vs.json* definiujący pojedyncze zadanie. Po wywołaniu zadanie wyświetla nazwę pliku aktualnie wybranego pliku *.js.*

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

- `taskName`określa nazwę wyświetlaną w menu po kliknięciu prawym przyciskiem myszy.
- `appliesTo`określa, na których plikach można wykonać polecenie.
- Właściwość `command` określa polecenie do wywołania. W tym przykładzie zmienna środowiskowa `COMSPEC` służy do identyfikowania interpretera wiersza polecenia, zazwyczaj *cmd.exe*.
- Właściwość `args` określa argumenty, które mają być przekazywane do przywołane polecenia.
- Makro `${file}` pobiera wybrany plik w **Eksploratorze rozwiązań**.

Po *zapisaniu pliku tasks.vs.json*można kliknąć prawym przyciskiem myszy dowolny plik *.js* w folderze i wybrać **opcję Nazwa pliku Echo**. Nazwa pliku jest wyświetlana w oknie **Dane wyjściowe.**

> [!NOTE]
> Jeśli baza kodu nie zawiera pliku *tasks.vs.json,* można go utworzyć, wybierając polecenie **Konfiguruj zadania** z menu kontekstowego pliku w **Eksploratorze rozwiązań**lub menu kontekstowym pliku.

W następnym przykładzie zdefiniowano zadanie, które wyświetla listę plików i podfolderów katalogu *pojemników.*

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

- `${outDir}`jest makrą niestandardową, `tasks` która jest najpierw zdefiniowana przed blokiem. Następnie jest wywoływana `args` w nieruchomości.

To zadanie dotyczy wszystkich plików. Po otwarciu menu kontekstowego dowolnego pliku w **Eksploratorze rozwiązań**nazwa zadania **pojawi** się u dołu menu. Po wybraniu **opcji Lista danych wyjściowych**zawartość katalogu *pojemnika* jest wyświetlana w oknie **Dane wyjściowe** w programie Visual Studio.

![Dowolne zadanie w menu kontekstowym](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Zakres ustawień

Wiele plików *tasks.vs.json* może istnieć w katalogu głównym i podkatalogach bazy kodu. Ten projekt umożliwia elastyczność mieć różne zachowanie w różnych podkatalogach bazy kodu. Visual Studio agreguje lub zastępuje ustawienia w całej bazie kodu, ustalając priorytety plików w następującej kolejności:

- Pliki ustawień w katalogu *.vs* folderu głównego.
- Katalog, w którym obliczane jest ustawienie.
- Katalog nadrzędny bieżącego katalogu, aż do katalogu głównego.
- Pliki ustawień w katalogu głównym.

Te reguły agregacji mają zastosowanie do *pliku tasks.vs.json*. Aby uzyskać informacje na temat sposobu agregowania ustawień w innym pliku, zobacz odpowiednią sekcję dla tego pliku w tym artykule.

### <a name="properties-for-tasksvsjson"></a>Właściwości dla tasks.vs.json

W tej sekcji opisano niektóre właściwości, które można określić w *pliku tasks.vs.json*.

#### <a name="appliesto"></a>Appliesto

Zadania dla dowolnego pliku lub folderu można tworzyć, określając jego nazwę w `appliesTo` polu, na przykład `"appliesTo": "hello.js"`. Jako wartości można używać następujących masek plików:

|||
|-|-|
|`"*"`| zadanie jest dostępne dla wszystkich plików i folderów w obszarze roboczym|
|`"*/"`| zadanie jest dostępne dla wszystkich folderów w obszarze roboczym|
|`"*.js"`| zadanie jest dostępne dla wszystkich plików z rozszerzeniem *.js* w obszarze roboczym|
|`"/*.js"`| zadanie jest dostępne dla wszystkich plików z rozszerzeniem *.js* w katalogu głównym obszaru roboczego|
|`"src/*/"`| zadanie jest dostępne dla wszystkich podfolderów folderu *src*|
|`"makefile"`| zadanie jest dostępne dla wszystkich plików *makefile* w obszarze roboczym|
|`"/makefile"`| zadanie jest dostępne tylko dla *pliku makefile* w katalogu głównym obszaru roboczego|

#### <a name="macros-for-tasksvsjson"></a>Makra dla tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Określa dowolną zmienną środowiskową (na przykład ${env. PATH}, ${env.COMSPEC} i tak dalej), który jest ustawiony dla wiersza polecenia dewelopera. Aby uzyskać więcej informacji, zobacz [Wiersz polecenia dewelopera dla programu Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Pełna ścieżka do folderu obszaru roboczego (na przykład *C:\sources\hello*)|
|`${file}`| Pełna ścieżka pliku lub folderu wybranego do uruchomienia tego zadania (na przykład *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Ścieżka względna do pliku lub folderu (na przykład *src\hello.js)*|
|`${fileBasename}`| Nazwa pliku bez ścieżki lub rozszerzenia (na przykład *hello*)|
|`${fileDirname}`| Pełna ścieżka do pliku, z wyłączeniem nazwy pliku (na przykład *C:\sources\hello\src*)|
|`${fileExtname}`| Rozszerzenie wybranego pliku (na przykład *.js*)|

## <a name="configure-debugging-with-launchvsjson"></a>Konfigurowanie debugowania za pomocą pliku launch.vs.json

Aby skonfigurować projekty CMake do debugowania, zobacz [Konfigurowanie sesji debugowania CMake](/cpp/build/configure-cmake-debugging-sessions).

1. Aby skonfigurować bazę kodu do debugowania, w **Eksploratorze rozwiązań** wybierz element menu menu **Debugowanie i Uruchamianie ustawień** z menu kontekstowego lub kontekstowego pliku wykonywalnego.

   ![Menu kontekstowe Ustawienia debugowania i uruchamiania](media/customize-debug-launch-menu.png)

1. W oknie **dialogowym Wybieranie debugera** wybierz opcję, a następnie wybierz przycisk **Wybierz.**

   ![Wybieranie okna dialogowego Debuger](media/customize-select-a-debugger.png)

   Jeśli plik *launch.vs.json* jeszcze nie istnieje, zostanie utworzony.

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

1. Następnie kliknij prawym przyciskiem myszy plik wykonywalny w **Eksploratorze rozwiązań**i wybierz pozycję **Ustaw jako element startowy**.

   Plik wykonywalny jest oznaczony jako element startowy bazy kodu, a tytuł przycisku **Start** debugowania zmienia się w celu odzwierciedlenia nazwy pliku wykonywalnego.

   ![Dostosowany przycisk Start](media/customize-start-button.png)

   Po wybraniu **F5**debuger uruchamia się i zatrzymuje w dowolnym punkcie przerwania, który może być już ustawiony. Wszystkie znane okna debugera są dostępne i funkcjonalne.

   > [!IMPORTANT]
   > Aby uzyskać dodatkowe informacje na temat niestandardowych zadań kompilacji i debugowania w projektach folderów otwartych w języku C++, zobacz [Obsługa otwierania folderów dla systemów kompilacji języka C++ w programie Visual Studio](/cpp/build/open-folder-projects-cpp).

### <a name="specify-arguments-for-debugging"></a>Określanie argumentów do debugowania

Można określić argumenty wiersza polecenia do przekazania do debugowania w pliku *launch.vs.json.* Dodaj argumenty w `args` tablicy, jak pokazano w poniższym przykładzie:

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

Po zapisaniu tego pliku nazwa nowej konfiguracji pojawia się na liście rozwijanej docelowej debugowania i można ją wybrać, aby uruchomić debuger. Można utworzyć dowolną liczbę konfiguracji debugowania.

![Lista rozwijana konfiguracji debugowania](media/customize-debug-configurations.png)

> [!NOTE]
> `configurations` Właściwość tablicy w *pliku launch.vs.json* jest odczytywana z dwóch lokalizacji&mdash;plików katalogu głównego bazy kodu i katalogu *.vs.* W przypadku konfliktu priorytetem jest wartość w *pliku .vs\launch.vs.json*.

## <a name="additional-settings-files"></a>Dodatkowe pliki ustawień

Oprócz trzech plików *.json* opisanych w tym temacie program Visual Studio odczytuje również ustawienia z niektórych dodatkowych plików, jeśli istnieją one w bazie kodu.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Program Visual Studio odczytuje ograniczone ustawienia z pliku o nazwie *settings.json*, jeśli znajduje się w katalogu o nazwie *.vscode*. Ta funkcja jest dostępna dla baz kodu, które zostały wcześniej opracowane w programie Visual Studio Code. Obecnie jedynym ustawieniem odczytanym z *pliku .vscode\settings.json* jest `files.exclude`, które filtruje pliki wizualnie w Eksploratorze rozwiązań i z niektórych narzędzi wyszukiwania.

W bazie kodu może być dowolna liczba plików *vscode\settings.json.* Ustawienia odczytywane z tego pliku są stosowane do nadrzędnego katalogu *.vscode* i wszystkich jego podkatalogów.

### <a name="gitignore"></a>.gitignore

*Pliki .gitignore* służą do informowania Gita, które pliki zignorować; oznacza to, które pliki i katalogi nie chcesz zaewidencjonować. *Pliki .gitignore* są zwykle zawarte jako część bazy kodu, dzięki czemu ustawienia mogą być współużytkowane wszystkim deweloperom bazy kodu. Program Visual Studio odczytuje wzorce w plikach *gitignore,* aby wizualnie filtrować elementy i niektóre narzędzia wyszukiwania.

Ustawienia odczytywane z pliku *gitignore* są stosowane do katalogu nadrzędnego i wszystkich podkatalogów.

## <a name="see-also"></a>Zobacz też

- [Tworzenie kodu bez projektów ani rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Otwieranie folderu projektów na potrzeby języka C++](/cpp/build/open-folder-projects-cpp)
- [CZłoprojekty dla języka C++](/cpp/build/cmake-projects-in-visual-studio)
- [Odwołanie NMAKE](/cpp/build/reference/nmake-reference)
- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
