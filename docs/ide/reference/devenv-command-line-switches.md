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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3ed82bd8ba3845541d7dce628f99fb78b62ab9f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595712"
---
# <a name="devenv-command-line-switches"></a>Przełączniki wiersza polecenia Devenv

Devenv umożliwia ustawianie różnych opcji dla środowiska IDE, tworzenie projektów, Debugowanie projektów i wdrażanie projektów z poziomu wiersza polecenia. Użyj tych przełączników do uruchomienia środowiska IDE ze skryptu lub pliku. bat (takiego jak nocne skrypty kompilacji) lub uruchomienia środowiska IDE w określonej konfiguracji.

> [!NOTE]
> W przypadku zadań związanych z kompilacją zaleca się używanie programu MSBuild zamiast devenv. Aby uzyskać więcej informacji, zobacz [wiersza polecenia MSBuild](../../msbuild/msbuild-command-line-reference.md).

Aby uzyskać informacje na temat przełączników związanych z programowaniem pakietu VSPackage, zobacz również [przełączniki wiersza polecenia devenv do programowania pakietu VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Składnia przełącznik Devenv

Polecenia, które zaczynają się od `devenv` są obsługiwane przez `devenv.com` narzędzia, które dostarcza dane wyjściowe za pośrednictwem standardowych systemowych strumieni, takich jak `stdout` i `stderr`. Tego narzędzia można określić odpowiednią przekierowanie We/Wy podczas przechwytuje dane wyjściowe, na przykład plik z rozszerzeniem txt.

Alternatywnie polecenia, które zaczynają się od `devenv.exe` mogą używać tych samych przełączników, ale narzędzie `devenv.com` jest pomijane. Za pomocą `devenv.exe` bezpośrednio zapobiega dane wyjściowe w konsoli.

Reguły składni dla przełączników `devenv` przypominają reguły dla innych narzędzi wiersza polecenia systemu DOS. Następujące reguły składni mają zastosowanie do wszystkich `devenv` przełączników i ich argumentów:

- Polecenia zaczynają się od `devenv`.

- W przełącznikach nie jest rozróżniana wielkość liter.

- Przełącznik można określić przy użyciu łącznika ("-") lub ukośnika ("/").

- Podczas określania rozwiązania lub projektu, pierwszy argument jest nazwa pliku rozwiązania lub pliku projektu, w tym ścieżki pliku.

- Jeśli pierwszy argument to plik, który nie jest rozwiązaniem lub projektem, ten plik zostanie otwarty w odpowiednim edytorze w nowym wystąpieniu IDE.

- Jeśli podasz nazwę pliku projektu, a nie nazwę pliku rozwiązania `devenv` polecenie wyszukuje folderu nadrzędnego pliku projektu plik rozwiązania, który ma taką samą nazwę. Na przykład polecenie `devenv myproject1.vbproj /build` przeszukuje folder nadrzędny dla pliku rozwiązania o nazwie `myproject1.sln`.

  > [!NOTE]
  > Jeden i tylko jeden plik rozwiązania, który odwołuje się do tego projektu powinna znajdować się w folderu nadrzędnego. Jeśli folder nadrzędny zawiera plik rozwiązania nie odwołujący się tego projektu, lub jeśli folder nadrzędny zawiera dwa lub więcej plików rozwiązania, które ją przywołują, następnie rozwiązanie tymczasowe tworzony jest plik.

- Gdy nazwy pliku i ścieżki plików zawiera spacje, należy ująć je w znaki cudzysłowu (""). Na przykład `"c:\project a\"`.

- Wstaw jeden znak spacji między przełączniki i argumenty, w tym samym wierszu. Na przykład polecenie `devenv /log output.txt` otwiera środowisko IDE i wyprowadza wszystkie informacje dziennika dla tej sesji do danych wyjściowych. txt.

- Nie można użyć składni dopasowania wzorca w poleceniach `devenv`.

## <a name="devenv-switches"></a>Przełączniki Devenv

Poniższe przełączniki wiersza polecenia wyświetlają IDE i wykonują opisane zadanie.

|Przełącznik w wierszu polecenia|Opis|
| - |-----------------|
|[/Command](command-devenv-exe.md)|Uruchamia IDE i wykonuje określone polecenie.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Ładuje plik wykonywalny C++ pod kontrolą debugera. Ten przełącznik nie jest dostępny dla Visual Basic C# ani plików wykonywalnych. Aby uzyskać więcej informacji, zobacz [automatycznie uruchamia proces w debugerze](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|Porównuje dwa pliki. Przyjmuje cztery parametry: *SourceFile*, *TargetFile*, *SourceDisplayName* (opcjonalne) i *TargetDisplayName* (opcjonalnie).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Otwiera określone rozwiązanie bez ładowania żadnych projektów.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|Otwiera określone pliki w działającej instancji tej aplikacji. W przypadku Brak uruchomionych wystąpień uruchamia nowe wystąpienie o uproszczonym układzie okna.<br /><br /> `devenv /edit File1 File2`|
|[/LCID lub/L](lcid-devenv-exe.md)|Ustawia domyślny język dla środowiska IDE. Jeśli określony język nie jest uwzględniony w instalacji programu Visual Studio, to ustawienie jest ignorowane.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Uruchamia programu Visual Studio i loguje wszelką aktywność do pliku dziennika.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|Otwiera środowisko IDE bez wyświetlania ekranu powitalnego.<br /><br /> `devenv /nosplash File1 File2`|
|[/Run lub/R](run-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie, minimalizuje IDE w rozwiązaniu jest uruchamiany, gdy IDE jest zamykane po rozwiązaniu zakończył działanie.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Uruchamia program Visual Studio w trybie awaryjnym. Ten przełącznik ładuje tylko domyślne środowisko, domyślne usługi i wydane wersje pakietów innych firm.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|
|[/UseEnv](useenv-devenv-exe.md)|Powoduje, że IDE używa zmiennych środowiskowych PATH, INCLUDE, LIBPATH i LIB do C++ kompilowania. Ten przełącznik został zainstalowany przy użyciu **programowanie aplikacji klasycznych w języku C++** obciążenia. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

Poniższe przełączniki wiersza polecenia nie wyświetlają środowiska IDE.

|Przełącznik w wierszu polecenia|Opis|
| - |-----------------|
|[/?](q-devenv-exe.md)|Wyświetla pomoc dla przełączników `devenv` w **oknie wiersza polecenia**.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów.|
|[/Build](build-devenv-exe.md)|Tworzy określonego rozwiązania lub projektu, zgodnie z konfiguracją określonego rozwiązania.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Usuwa wszystkie pliki utworzone za pomocą polecenia kompilacji, bez wywierania wpływu na pliki źródłowe.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|Kompiluje rozwiązanie wraz z plikami wymaganymi do wdrożenia zgodnie z konfiguracją rozwiązania.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Pozwala określić plik, aby otrzymywać komunikaty o błędach podczas kompilacji.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|Projekt do kompilacji, czyszczenia lub wdrożenia. Tego przełącznika można używać tylko wtedy, gdy został również dostarczony przełącznik `/Build`, `/Rebuild`, `/Clean`lub `/Deploy`.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Określa konfigurację projektu do kompilacji lub wdrożenia. Tego przełącznika można używać tylko wtedy, gdy został również dostarczony przełącznik `/Project`.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|Czyści, a następnie kompiluje określone rozwiązanie lub projekt zgodnie z konfiguracją określonego rozwiązania.<br /><br /> `devenv mysln.sln /rebuild`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Przywraca ustawienia domyślne programu Visual Studio. Opcjonalnie resetuje ustawienia do określonego pliku `.vssettings`.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Upgrade](upgrade-devenv-exe.md)|Uaktualnia pliku określonego rozwiązania i wszystkie jego pliki projektu lub plik określony projekt do bieżącego formatu Visual Studio dla tych plików.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](general-environment-options-dialog-box.md)
- [Devenv przełączniki wiersza polecenia pakietu VSPackage Development](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
