---
title: Przełączniki wiersza polecenia Devenv
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db9aaeb48095b058abb0deefa342598eefeed1b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970230"
---
# <a name="devenv-command-line-switches"></a>Przełączniki wiersza polecenia Devenv

Devenv pozwala ustawić różne opcje środowiska IDE, kompilować projekty, debugowania projektów i wdrażać projekty z poziomu wiersza polecenia. Używaj tych przełączników, aby uruchomić środowisko IDE z skrypt lub plik .bat, (na przykład skrypt nocna Kompilacja) lub do uruchomienia środowiska IDE w określonej konfiguracji.

> [!NOTE]
> Zadania związane z kompilacji zaleca się używać programu MSBuild zamiast devenv. Aby uzyskać więcej informacji, zobacz [wiersza polecenia MSBuild](../../msbuild/msbuild-command-line-reference.md).

Aby uzyskać informacje dotyczące przełączników that are related to programowania pakietu VSPackage, zobacz też [przełączniki wiersza polecenia Devenv dla programowania pakietu VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Składnia przełącznik Devenv

Polecenia, które zaczynają się od `devenv` są obsługiwane przez `devenv.com` narzędzia, które dostarcza dane wyjściowe za pośrednictwem standardowych systemowych strumieni, takich jak `stdout` i `stderr`. Tego narzędzia można określić odpowiednią przekierowanie We/Wy podczas przechwytuje dane wyjściowe, na przykład plik z rozszerzeniem txt.

Alternatywnie poleceń, które zaczynają się od `devenv.exe` można użyć tego samego przełączników, ale `devenv.com` narzędzie jest pomijany. Za pomocą `devenv.exe` bezpośrednio zapobiega dane wyjściowe w konsoli.

Zasady składni `devenv` przełączników przypominają reguły dla innych narzędzi wiersza polecenia systemu DOS. Następujące reguły składni mają zastosowanie do wszystkich `devenv` przełączników i ich argumentów:

- Polecenia zaczynają się od `devenv`.

- Przełączniki nie jest rozróżniana wielkość liter.

- Należy określić przełącznik, za pomocą łącznika ("-") lub ukośnika ("/").

- Podczas określania rozwiązania lub projektu, pierwszy argument jest nazwa pliku rozwiązania lub pliku projektu, w tym ścieżki pliku.

- Jeśli pierwszy argument jest plik, który nie jest rozwiązanie lub projekt, ten plik zostanie otwarty w odpowiedniego edytora, w nowym wystąpieniu środowiska IDE.

- Jeśli podasz nazwę pliku projektu, a nie nazwę pliku rozwiązania `devenv` polecenie wyszukuje folderu nadrzędnego pliku projektu plik rozwiązania, który ma taką samą nazwę. Na przykład polecenie `devenv myproject1.vbproj /build` wyszukuje folder nadrzędny do pliku rozwiązania, który nosi nazwę `myproject1.sln`.

  > [!NOTE]
  > Jeden i tylko jeden plik rozwiązania, który odwołuje się do tego projektu powinna znajdować się w folderu nadrzędnego. Jeśli folder nadrzędny zawiera plik rozwiązania nie odwołujący się tego projektu, lub jeśli folder nadrzędny zawiera dwa lub więcej plików rozwiązania, które ją przywołują, następnie rozwiązanie tymczasowe tworzony jest plik.

- Gdy nazwy pliku i ścieżki plików zawiera spacje, należy ująć je w znaki cudzysłowu (""). Na przykład `"c:\project a\"`.

- Wstaw jeden znak spacji między przełączniki i argumenty, w tym samym wierszu. Na przykład polecenie `devenv /log output.txt` IDE otwiera i wyświetla wszystkie rejestrowania informacji w ramach danej sesji output.txt.

- Nie można użyć składni wieloznacznej `devenv` poleceń.

## <a name="devenv-switches"></a>Przełączniki Devenv

Następujące przełączniki wiersza polecenia wyświetlenia IDE i wykonaj opisane zadania.

|Przełącznik wiersza polecenia|Opis|
| - |-----------------|
|[/Command](command-devenv-exe.md)|Uruchamia IDE i wykonuje określone polecenie.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Ładuje plik wykonywalny C++ pod kontrolą debugera. Ten przełącznik nie jest dostępna dla języka Visual Basic lub C# plików wykonywalnych. Aby uzyskać więcej informacji, zobacz [automatycznie uruchamia proces w debugerze](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|Porównuje dwa pliki. Przyjmuje cztery parametry: *SourceFile*, *TargetFile*, *SourceDisplayName* (opcjonalnie) i *TargetDisplayName* (opcjonalnie).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Otwiera określone rozwiązanie bez ładowania jakiegokolwiek projektu.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|Otwiera określone pliki w działającej instancji tej aplikacji. W przypadku Brak uruchomionych wystąpień uruchamia nowe wystąpienie o uproszczonym układzie okna.<br /><br /> `devenv /edit File1 File2`|
|[/ LCID lub/l](lcid-devenv-exe.md)|Ustawia domyślny język dla środowiska IDE. Jeśli określony język nie jest uwzględniony w instalacji programu Visual Studio, to ustawienie jest ignorowane.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Uruchamia programu Visual Studio i loguje wszelką aktywność do pliku dziennika.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|Otwiera IDE bez wyświetlania na ekranie powitalnym.<br /><br /> `devenv /nosplash File1 File2`|
|[/ Run lub/r](run-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie.<br /><br /> `devenv /run mysln.sln`|
|[/ RunExit](runexit-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie, minimalizuje IDE w rozwiązaniu jest uruchamiany, gdy IDE jest zamykane po rozwiązaniu zakończył działanie.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Uruchamia programu Visual Studio w trybie awaryjnym. Ten przełącznik ładuje domyślnym środowisku usługi domyślne i wydane wersje pakietów innych firm.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|
|[/UseEnv](useenv-devenv-exe.md)|Powoduje, że środowisko IDE będzie używać zmiennych środowiskowych PATH, INCLUDE, LIBPATH i LIB dla kompilacji języka C++. Ten przełącznik został zainstalowany przy użyciu **programowanie aplikacji klasycznych w języku C++** obciążenia. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

IDE nie są wyświetlane następujące przełączniki wiersza polecenia.

|Przełącznik wiersza polecenia|Opis|
| - |-----------------|
|[/?](q-devenv-exe.md)|Wyświetla Pomoc dotyczącą `devenv` przełącznikami w **okna wiersza polecenia**.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|
|[/Build](build-devenv-exe.md)|Tworzy określonego rozwiązania lub projektu, zgodnie z konfiguracją określonego rozwiązania.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Usuwa wszystkie pliki utworzone za pomocą polecenia kompilacji, bez wywierania wpływu na pliki źródłowe.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|Kompiluje rozwiązanie, wraz z plikami niezbędne do wdrożenia, zgodnie z konfiguracją rozwiązania.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Pozwala określić plik, aby otrzymywać komunikaty o błędach podczas kompilacji.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|Projekt do kompilacji, czyszczenia lub wdrożenia. Można użyć tego przełącznika, tylko wtedy, gdy zostały również podane `/Build`, `/Rebuild`, `/Clean`, lub `/Deploy` przełącznika.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Określa konfigurację projektu do kompilacji lub wdrożenia. Można użyć tego przełącznika, tylko wtedy, gdy zostały również podane `/Project` przełącznika.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|Czyści, a następnie kompiluje określone rozwiązanie lub projekt zgodnie z konfiguracją określonego rozwiązania.<br /><br /> `devenv mysln.sln /rebuild`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Przywraca ustawienia domyślne programu Visual Studio. Opcjonalnie resetuje ustawienia do określonego `.vssettings` pliku.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Upgrade](upgrade-devenv-exe.md)|Uaktualnia pliku określonego rozwiązania i wszystkie jego pliki projektu lub plik określony projekt do bieżącego formatu Visual Studio dla tych plików.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](general-environment-options-dialog-box.md)
- [Przełączniki wiersza polecenia Devenv dla programowania pakietu VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
