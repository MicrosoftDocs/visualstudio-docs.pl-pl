---
title: Przełączniki linii poleceń Devenv
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
ms.openlocfilehash: b3ed82bd8ba3845541d7dce628f99fb78b62ab9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595712"
---
# <a name="devenv-command-line-switches"></a>Przełączniki wiersza polecenia Devenv

Devenv umożliwia ustawienie różnych opcji dla IDE, tworzenie projektów, debugowanie projektów i wdrażanie projektów z wiersza polecenia. Użyj tych przełączników, aby uruchomić IDE ze skryptu lub pliku .bat (na przykład skrypt kompilacji nocnej) lub uruchomić IDE w określonej konfiguracji.

> [!NOTE]
> W przypadku zadań związanych z kompilacją zaleca się użycie programu MSBuild zamiast devenv. Aby uzyskać więcej informacji, zobacz [odwołanie do wiersza polecenia MSBuild](../../msbuild/msbuild-command-line-reference.md).

Aby uzyskać informacje na temat przełączników związanych z programem VSPackage, zobacz także [Przełączniki wiersza polecenia Devenv dla rozwoju VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Składnia przełącznika Devenv

Polecenia, które `devenv` zaczynają się są `devenv.com` obsługiwane przez narzędzie, które dostarcza dane `stdout` wyjściowe za pośrednictwem standardowych strumieni systemowych, takich jak i `stderr`. Narzędzie określa odpowiednie przekierowanie we/wy podczas przechwytywania danych wyjściowych, na przykład do pliku txt.

Alternatywnie polecenia, które `devenv.exe` zaczynają się można użyć tych `devenv.com` samych przełączników, ale narzędzie jest pomijane. Użycie `devenv.exe` bezpośrednio zapobiega pojawianiu się danych wyjściowych na konsoli.

Reguły składni `devenv` dla przełączników przypominają reguły dla innych narzędzi wiersza polecenia DOS. Do wszystkich `devenv` przełączników i ich argumentów mają zastosowanie następujące reguły składni:

- Polecenia zaczynają `devenv`się od .

- W przełącznikach nie jest rozróżniana wielkość liter.

- Przełącznik można określić za pomocą łącznika ("-") lub ukośnika do przodu ("/").

- Podczas określania rozwiązania lub projektu, pierwszy argument jest nazwa pliku rozwiązania lub pliku projektu, w tym ścieżki pliku.

- Jeśli pierwszy argument jest plik, który nie jest rozwiązaniem lub projektem, ten plik otwiera się w odpowiednim edytorze, w nowym wystąpieniu IDE.

- Po podaniu nazwy pliku projektu zamiast nazwy pliku `devenv` rozwiązania polecenie przeszukuje folder nadrzędny pliku projektu w poszukiwaniu pliku rozwiązania o tej samej nazwie. Na przykład polecenie `devenv myproject1.vbproj /build` przeszukuje folder nadrzędny w `myproject1.sln`poszukiwaniu pliku rozwiązania o nazwie .

  > [!NOTE]
  > Jeden i tylko jeden plik rozwiązania, który odwołuje się do tego projektu powinny znajdować się w folderze nadrzędnym. Jeśli folder nadrzędny nie zawiera pliku rozwiązania, który odwołuje się do tego projektu lub jeśli folder nadrzędny zawiera dwa lub więcej plików rozwiązania, które się do niego odwołują, tworzony jest tymczasowy plik rozwiązania.

- Gdy ścieżki plików i nazwy plików zawierają spacje, należy je ująć w cudzysłów (""). Na przykład `"c:\project a\"`.

- Wstaw jeden znak spacji między przełącznikami a argumentami w tym samym wierszu. Na przykład polecenie `devenv /log output.txt` otwiera IDE i wyprowadza wszystkie informacje dziennika dla tej sesji do pliku output.txt.

- Nie można użyć składni dopasowania wzorca w `devenv` poleceniach.

## <a name="devenv-switches"></a>Przełączniki Devenv

Następujące przełączniki wiersza polecenia wyświetlają IDE i wykonują opisane zadanie.

|Przełącznik wiersza polecenia|Opis|
| - |-----------------|
|[/Polecenie](command-devenv-exe.md)|Uruchamia IDE i wykonuje określone polecenie.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Ładuje wykonywalny C++ pod kontrolą debugera. Ten przełącznik nie jest dostępny dla plików wykonywalnych języka Visual Basic lub C#. Aby uzyskać więcej informacji, zobacz [Automatyczne uruchamianie procesu w debugerze](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/Dyfer wyd.](diff.md)|Porównuje dwa pliki. Przyjmuje cztery parametry: *SourceFile*, *TargetFile*, *SourceDisplayName* (opcjonalnie) i *TargetDisplayName* (opcjonalnie).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Otwiera określone rozwiązanie bez ładowania żadnych projektów.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edytuj](edit-devenv-exe.md)|Otwiera określone pliki w uruchomionym wystąpieniu tej aplikacji. Jeśli nie ma uruchomionych wystąpień, rozpoczyna nowe wystąpienie z uproszczonym układem okna.<br /><br /> `devenv /edit File1 File2`|
|[/LCID lub /L](lcid-devenv-exe.md)|Ustawia domyślny język ide. Jeśli określony język nie jest uwzględniony w instalacji programu Visual Studio, to ustawienie jest ignorowane.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Uruchamia program Visual Studio i rejestruje całą aktywność do pliku dziennika.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash (Nieskładka)](nosplash-devenv-exe.md)|Otwiera IDE bez wyświetlania ekranu powitalnego.<br /><br /> `devenv /nosplash File1 File2`|
|[/Run lub /R](run-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie, minimalizuje IDE po uruchomieniu rozwiązania i zamyka IDE po zakończeniu pracy rozwiązania.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Uruchamia program Visual Studio w trybie awaryjnym. Ten przełącznik ładuje tylko środowisko domyślne, usługi domyślne i wysłane wersje pakietów innych firm.<br /><br /> Ten przełącznik nie ma żadnych argumentów.|
|[/UseEnv](useenv-devenv-exe.md)|Powoduje, że IDE do używania PATH, INCLUDE, LIBPATH i LIB zmiennych środowiska dla kompilacji C++. Ten przełącznik jest zainstalowany z programem Desktop development z obciążeniem **języka C++.** Aby uzyskać więcej informacji, zobacz [Ustawianie zmiennych ścieżki i środowiska dla kompilacji wiersza polecenia](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

Następujące przełączniki wiersza polecenia nie są wyświetlane IDE.

|Przełącznik wiersza polecenia|Opis|
| - |-----------------|
|[/?](q-devenv-exe.md)|Wyświetla pomoc `devenv` dotyczącą przełączników w **oknie wiersza polecenia**.<br /><br /> Ten przełącznik nie ma żadnych argumentów.|
|[/Build](build-devenv-exe.md)|Tworzy określone rozwiązanie lub projekt zgodnie z konfiguracją określonego rozwiązania.<br /><br /> `devenv mysln.sln /build`|
|[/Czyste](clean-devenv-exe.md)|Usuwa wszystkie pliki utworzone przez polecenie kompilacji, bez wpływu na pliki źródłowe.<br /><br /> `devenv mysln.sln /clean`|
|[/Wdrażanie](deploy-devenv-exe.md)|Tworzy rozwiązanie wraz z plikami niezbędnymi do wdrożenia, zgodnie z konfiguracją rozwiązania.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Umożliwia określenie pliku, który ma być odbierany przez błędy podczas tworzenia.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Projekt](project-devenv-exe.md)|Projekt do tworzenia, czyszczenia lub wdrażania. Tego przełącznika można używać tylko wtedy, `/Build` `/Rebuild`gdy `/Clean`podano `/Deploy` również przełącznik , , lub switch.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Określa konfigurację projektu do utworzenia lub wdrożenia. Tego przełącznika można używać tylko wtedy, `/Project` gdy przełącznik został dostarczony.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Odbuduj](rebuild-devenv-exe.md)|Czyści, a następnie tworzy określone rozwiązanie lub projekt zgodnie z konfiguracją określonego rozwiązania.<br /><br /> `devenv mysln.sln /rebuild`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Przywraca domyślne ustawienia programu Visual Studio. Opcjonalnie resetuje ustawienia do `.vssettings` określonego pliku.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Upgrade](upgrade-devenv-exe.md)|Uaktualnia plik określonego rozwiązania i wszystkie jego pliki projektu lub określony plik projektu do bieżących formatów programu Visual Studio dla tych plików.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](general-environment-options-dialog-box.md)
- [Przełączniki wiersza polecenia Devenv dla rozwoju VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
