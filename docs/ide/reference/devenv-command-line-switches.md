---
title: Przełączniki wiersza polecenia devenv
description: Dowiedz się więcej o przełącznikach wiersza polecenia devenv i sposobach ich użycia do ustawiania opcji środowiska IDE, a także kompilowania, debugowania i wdrażania projektów, a wszystko to w wierszu polecenia.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 597a3f7e9a9b36d52f55a9215891c40b18f1a9e9
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305512"
---
# <a name="devenv-command-line-switches"></a>Przełączniki wiersza polecenia Devenv

Devenv umożliwia ustawianie różnych opcji dla środowiska IDE, tworzenie projektów, Debugowanie projektów i wdrażanie projektów z poziomu wiersza polecenia. Użyj tych przełączników do uruchomienia środowiska IDE ze skryptu lub pliku. bat (takiego jak nocne skrypty kompilacji) lub uruchomienia środowiska IDE w określonej konfiguracji.

> [!NOTE]
> W przypadku zadań związanych z kompilacją zaleca się używanie programu MSBuild zamiast devenv. Aby uzyskać więcej informacji, zobacz [Dokumentacja wiersza polecenia programu MSBuild](../../msbuild/msbuild-command-line-reference.md).

Aby uzyskać informacje na temat przełączników związanych z programowaniem pakietu VSPackage, zobacz również [przełączniki wiersza polecenia devenv do programowania pakietu VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Składnia przełącznika Devenv

Polecenia, które zaczynają się od `devenv` są obsługiwane przez `devenv.com` narzędzie, które dostarcza dane wyjściowe przez standardowe strumienie systemowe, takie jak `stdout` i `stderr` . Narzędzie określa odpowiednie przekierowania we/wy podczas przechwytywania danych wyjściowych, na przykład do pliku txt.

Alternatywnie polecenia, które zaczynają się od `devenv.exe` mogą korzystać z tych samych przełączników, ale `devenv.com` Narzędzie jest pomijane. Używanie `devenv.exe` bezpośrednio uniemożliwia wyświetlanie danych wyjściowych w konsoli programu.

Reguły składni dla `devenv` przełączników przypominają reguły dla innych narzędzi wiersza polecenia systemu DOS. Następujące reguły składni mają zastosowanie do wszystkich `devenv` przełączników i ich argumentów:

- Polecenia zaczynają się od `devenv` .

- W przełącznikach nie jest rozróżniana wielkość liter.

- Przełącznik można określić przy użyciu łącznika ("-") lub ukośnika ("/").

- Podczas określania rozwiązania lub projektu pierwszy argument jest nazwą pliku rozwiązania lub pliku projektu, łącznie z ścieżką pliku.

- Jeśli pierwszy argument to plik, który nie jest rozwiązaniem lub projektem, ten plik zostanie otwarty w odpowiednim edytorze w nowym wystąpieniu IDE.

- W przypadku podania nazwy pliku projektu zamiast nazwy pliku rozwiązania `devenv` polecenie przeszukuje folder nadrzędny pliku projektu dla pliku rozwiązania o tej samej nazwie. Na przykład polecenie `devenv myproject1.vbproj /build` przeszukuje folder nadrzędny dla pliku rozwiązania o nazwie `myproject1.sln` .

  > [!NOTE]
  > Jeden i tylko jeden plik rozwiązania odwołujący się do tego projektu powinien znajdować się w folderze nadrzędnym. Jeśli folder nadrzędny nie zawiera pliku rozwiązania, który odwołuje się do tego projektu, lub jeśli folder nadrzędny zawiera dwa lub więcej plików rozwiązania, które odwołują się do niego, zostanie utworzony tymczasowy plik rozwiązania.

- Gdy ścieżki plików i nazwy plików zawierają spacje, należy je ująć w znaki cudzysłowu (""). Na przykład `"c:\project a\"`.

- Wstaw jeden znak spacji między przełącznikami i argumentami w tym samym wierszu. Na przykład polecenie `devenv /log output.txt` otwiera środowisko IDE i wyprowadza wszystkie informacje dziennika dla tej sesji do output.txt.

- W poleceniach nie można używać składni dopasowania wzorców `devenv` .

## <a name="devenv-switches"></a>Przełączniki devenv

Poniższe przełączniki wiersza polecenia wyświetlają IDE i wykonują opisane zadanie.

|Przełącznik wiersza polecenia|Opis|
| - |-----------------|
|[/Command](command-devenv-exe.md)|Uruchamia środowisko IDE i wykonuje określone polecenie.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Ładuje plik wykonywalny języka C++ pod kontrolą debugera. Ten przełącznik nie jest dostępny dla plików wykonywalnych Visual Basic ani C#. Aby uzyskać więcej informacji, zobacz [Automatyczne uruchamianie procesu w debugerze](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|Porównuje dwa pliki. Przyjmuje cztery parametry: *SourceFile*, *TargetFile*, *SourceDisplayName* (opcjonalne) i *TargetDisplayName* (opcjonalnie).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Otwiera określone rozwiązanie bez ładowania żadnych projektów.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|Otwiera określone pliki w uruchomionym wystąpieniu tej aplikacji. Jeśli nie ma uruchomionych wystąpień, uruchamia nowe wystąpienie z uproszczonym układem okna.<br /><br /> `devenv /edit File1 File2`|
|[/LCID lub/L](lcid-devenv-exe.md)|Ustawia domyślny język IDE. Jeśli określony język nie jest uwzględniony w instalacji programu Visual Studio, to ustawienie jest ignorowane.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Uruchamia program Visual Studio i rejestruje wszystkie działania w pliku dziennika.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|Otwiera środowisko IDE bez wyświetlania ekranu powitalnego.<br /><br /> `devenv /nosplash File1 File2`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Przywraca ustawienia domyślne programu Visual Studio. Opcjonalnie resetuje ustawienia do określonego `.vssettings` pliku.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Run lub/R](run-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie, minimalizuje środowisko IDE, gdy rozwiązanie jest uruchomione, i zamyka środowisko IDE po zakończeniu działania rozwiązania.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Uruchamia program Visual Studio w trybie awaryjnym. Ten przełącznik ładuje tylko domyślne środowisko, domyślne usługi i wydane wersje pakietów innych firm.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|
|[/UseEnv](useenv-devenv-exe.md)|Powoduje, że IDE korzysta ze zmiennych środowiskowych PATH, INCLUDE, LIBPATH i LIB dla kompilacji w języku C++. Ten przełącznik jest instalowany z **programowaniem aplikacji klasycznych w języku C++** . Aby uzyskać więcej informacji, zobacz [Ustawianie zmiennych dotyczących ścieżki i środowiska dla kompilacji Command-Line](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

Poniższe przełączniki wiersza polecenia nie wyświetlają środowiska IDE.

|Przełącznik wiersza polecenia|Opis|
| - |-----------------|
|[/?](q-devenv-exe.md)|Wyświetla pomoc dotyczącą `devenv` przełączników w **oknie wiersza polecenia**.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|
|[/Build](build-devenv-exe.md)|Kompiluje określone rozwiązanie lub projekt zgodnie z konfiguracją określonego rozwiązania.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Usuwa wszystkie pliki utworzone przez polecenie kompilacji bez wpływu na pliki źródłowe.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|Kompiluje rozwiązanie wraz z plikami wymaganymi do wdrożenia zgodnie z konfiguracją rozwiązania.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Umożliwia określenie pliku do otrzymywania błędów podczas kompilowania.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|Projekt do skompilowania, oczyszczenia lub wdrożenia. Tego przełącznika można używać tylko wtedy, gdy podano również `/Build` przełącznik, `/Rebuild` , `/Clean` , lub `/Deploy` .<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Określa konfigurację projektu do skompilowania lub wdrożenia. Tego przełącznika można używać tylko wtedy, gdy został również dostarczony `/Project` przełącznik.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|Czyści, a następnie kompiluje określone rozwiązanie lub projekt zgodnie z konfiguracją określonego rozwiązania.<br /><br /> `devenv mysln.sln /rebuild`|
|[/Upgrade](upgrade-devenv-exe.md)|Uaktualnia określony plik rozwiązania oraz wszystkie jego pliki projektu lub określony plik projektu do bieżących formatów programu Visual Studio dla tych plików.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](general-environment-options-dialog-box.md)
- [Devenv przełączniki wiersza polecenia pakietu VSPackage Development](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
