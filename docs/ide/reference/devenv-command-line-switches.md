---
title: Przełączniki wiersza polecenia Devenv
ms.date: 02/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29a86959ccd4b0224e22e480588d36a0d637336e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911981"
---
# <a name="devenv-command-line-switches"></a>Przełączniki wiersza polecenia Devenv

Devenv pozwala ustawić różne opcje zintegrowanego środowiska programistycznego (IDE), a także tworzenia, debugowania i wdrażania projektów, w wierszu polecenia. Używaj tych przełączników, aby uruchomić środowisko IDE z skrypt lub plik .bat, na przykład skryptu nocna kompilacja, lub aby uruchomić środowisko IDE w określonej konfiguracji.

> [!NOTE]
> Zadania związane z kompilacji zaleca się używać programu MSBuild zamiast devenv. Aby uzyskać więcej informacji, zobacz [wiersza polecenia MSBuild](../../msbuild/msbuild-command-line-reference.md).

## <a name="devenv-switch-syntax"></a>Składnia przełącznik Devenv

Polecenia, które zaczynają się od `devenv` są obsługiwane przez `devenv.com` narzędzia, które dostarcza dane wyjściowe za pośrednictwem standardowych systemowych strumieni, takich jak `stdout` i `stderr`. Tego narzędzia można określić odpowiednią przekierowanie We/Wy podczas przechwytuje dane wyjściowe, na przykład plik z rozszerzeniem txt.

Z drugiej strony, polecenia, które zaczynają się od `devenv.exe` można użyć tego samego przełączników, ale `devenv.com` narzędzie jest pomijany. Za pomocą `devenv.exe` bezpośrednio zapobiega dane wyjściowe w konsoli.

Zasady składni `devenv` przełączników przypominają wyjątki dla innych narzędzi wiersza polecenia systemu DOS. Następujące reguły składni mają zastosowanie do wszystkich `devenv` przełączników i ich argumentów:

- Polecenia zaczynają się od `devenv`.

- Przełączniki nie jest rozróżniana wielkość liter.

- Podczas określania rozwiązania lub projektu, pierwszy argument jest nazwa pliku rozwiązania lub pliku projektu, w tym ścieżki pliku.

- Jeśli pierwszy argument jest plik, który nie jest rozwiązanie lub projekt, ten plik zostanie otwarty w odpowiedniego edytora, w nowym wystąpieniu środowiska IDE.

- Jeśli podasz nazwę pliku projektu, a nie nazwę pliku rozwiązania `devenv` polecenie wyszukuje folderu nadrzędnego pliku projektu plik rozwiązania, który ma taką samą nazwę. Na przykład polecenie `devenv myproject1.vbproj /build` wyszukuje folder nadrzędny do pliku rozwiązania, który nosi nazwę "myproject1.sln".

    > [!NOTE]
    > Jeden i tylko jeden plik rozwiązania, który odwołuje się do tego projektu powinna znajdować się w folderu nadrzędnego. Jeśli folder nadrzędny zawiera plik rozwiązania nie odwołujący się tego projektu, lub jeśli folder nadrzędny zawiera dwa lub więcej plików rozwiązania, które ją przywołują, następnie rozwiązanie tymczasowe tworzony jest plik.

- Gdy nazwy pliku i ścieżki plików zawiera spacje, należy ująć je w znaki cudzysłowu (""). Na przykład "c:\project\\".

- Wstaw jeden znak spacji między przełączniki i argumenty, w tym samym wierszu. Na przykład polecenie **devenv/log output.txt** IDE otwiera i wyświetla wszystkie rejestrowania informacji w ramach danej sesji output.txt.

- Nie można użyć składni wieloznacznej `devenv` poleceń.

## <a name="devenv-switches"></a>Przełączniki Devenv

Następujące przełączniki wiersza polecenia Wyświetl IDE i wykonać zadania opisane.

|Przełącznik wiersza polecenia|Opis|
| - |-----------------|
|[/Command](../../ide/reference/command-devenv-exe.md)|Uruchamia IDE i wykonuje określone polecenie.|
|[/DebugExe](../../ide/reference/debugexe-devenv-exe.md)|Ładuje plik wykonywalny C++ pod kontrolą debugera. Ten parametr nie jest dostępny dla języka Visual Basic lub C# plików wykonywalnych. Aby uzyskać więcej informacji, zobacz [automatycznie uruchamia proces w debugerze](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|
|[/ LCID lub/l](../../ide/reference/lcid-devenv-exe.md)|Ustawia domyślny język dla środowiska IDE. Jeśli określony język nie jest uwzględniony w instalacji programu Visual Studio, to ustawienie jest ignorowane.|
|[/Log](../../ide/reference/log-devenv-exe.md)|Uruchamia programu Visual Studio i loguje wszelką aktywność do pliku dziennika.|
|[/ Run lub/r](../../ide/reference/run-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie.|
|[/Runexit](../../ide/reference/runexit-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie, minimalizuje IDE w rozwiązaniu jest uruchamiany, gdy IDE jest zamykane po rozwiązaniu zakończył działanie.|
|[/UseEnv](../../ide/reference/useenv-devenv-exe.md)|Powoduje, że środowisko IDE będzie używać zmiennych środowiskowych PATH, INCLUDE i Biblioteka kompilacji C++, a nie ustawienia określone w sekcji katalogi VC ++ **projektów** opcji na liście **opcje** okno dialogowe. Ten przełącznik został zainstalowany przy użyciu **programowanie aplikacji klasycznych w języku C++** obciążenia. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|
|[/Edit](../../ide/reference/edit-devenv-exe.md)|Otwiera określone pliki w działającej instancji tej aplikacji. W przypadku Brak uruchomionych wystąpień uruchamia nowe wystąpienie o uproszczonym układzie okna.|
|[/SafeMode](../../ide/reference/safemode-devenv-exe.md)|Uruchamia programu Visual Studio w trybie awaryjnym, ładuje tylko środowisko domyślne i usługi i wydane wersje pakietów innych firm.|
|[/ResetSkipPkgs](../../ide/reference/resetskippkgs-devenv-exe.md)|Czyści wszystkie tagi SkipLoading dodane do VSPackages przez użytkowników, którzy chcą uniknąć obciążania problem pakietów VSPackage.|
|[/Setup](../../ide/reference/setup-devenv-exe.md)|Wymusza Visual Studio, aby scalić metadanych zasobu, który opisuje menu, paski narzędzi i grup poleceń, ze wszystkich pakietów VSPackage, które są dostępne. Należy uruchomić to polecenie jako administrator.|

Następujące przełączniki wiersza polecenia nie są wyświetlane w środowisku IDE.

|Przełącznik wiersza polecenia|Opis|
| - |-----------------|
|[/?](../../ide/reference/q-devenv-exe.md)|Wyświetla Pomoc dotyczącą przełączniki devenv **okna wiersza polecenia**.<br /><br /> `devenv /?`|
|[/Build](../../ide/reference/build-devenv-exe.md)|Tworzy określonego rozwiązania lub projektu, zgodnie z konfiguracją określonego rozwiązania.<br /><br /> `devenv myproj.csproj /build`|
|[/Clean](../../ide/reference/clean-devenv-exe.md)|Usuwa wszystkie pliki utworzone za pomocą polecenia kompilacji, bez wywierania wpływu na pliki źródłowe.<br /><br /> `devenv myproj.csproj /clean`|
|[/Deploy](../../ide/reference/deploy-devenv-exe.md)|Kompiluje rozwiązanie, wraz z plikami niezbędne do wdrożenia, zgodnie z konfiguracją rozwiązania.<br /><br /> `devenv myproj.csproj /deploy`|
|[/Diff](../../ide/reference/diff.md)|Porównuje dwa pliki. Przyjmuje cztery parametry: (Opcjonalnie) SourceDisplayName SourceFile, TargetFile, TargetDisplayName (opcjonalnie).|
|[/Out](../../ide/reference/out-devenv-exe.md)|Pozwala określić plik, aby otrzymywać komunikaty o błędach podczas kompilacji.<br /><br /> `devenv myproj.csproj /build /out log.txt`|
|[/Project](../../ide/reference/project-devenv-exe.md)|Projekt do kompilacji, czyszczenia lub wdrożenia. Można użyć tego przełącznika, tylko wtedy, gdy podano również/Build, / rebuild, / clean, lub / deploy — przełącznik.|
|[/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)|Określa konfigurację projektu do kompilacji lub wdrożenia. Można użyć tego przełącznika, tylko wtedy, gdy podano również przełącznika/Project.|
|[/Rebuild](../../ide/reference/rebuild-devenv-exe.md)|Czyści, a następnie kompiluje określone rozwiązanie lub projekt zgodnie z konfiguracją określonego rozwiązania.|
|[/ResetSettings](../../ide/reference/resetsettings-devenv-exe.md)|Przywraca ustawienia domyślne programu Visual Studio. Opcjonalnie resetuje ustawienia do określonego pliku .vssettings.|
|[/Upgrade](../../ide/reference/upgrade-devenv-exe.md)|Uaktualnia pliku określonego rozwiązania i wszystkie jego pliki projektu lub plik określony projekt do bieżącego formatu Visual Studio dla tych plików.|

## <a name="see-also"></a>Zobacz także

* [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
