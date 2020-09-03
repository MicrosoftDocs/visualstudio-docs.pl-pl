---
title: Przełączniki wiersza polecenia devenv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- builds [Team System], command-line
- applications [Visual Studio], executing
- compiling source code, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
- environment, Devenv commands
- compilers, Devenv commands
- switches
- Devenv, syntax and list of switches
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b8b0683024e2881f76bb6c54d9420d351fced08a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668728"
---
# <a name="devenv-command-line-switches"></a>Przełączniki wiersza polecenia Devenv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Devenv umożliwia ustawienie różnych opcji dla zintegrowanego środowiska programistycznego (IDE), a także kompilowanie, debugowanie i wdrażanie projektów z wiersza polecenia. Użyj tych przełączników, aby uruchomić środowisko IDE na podstawie skryptu lub pliku. bat, na przykład w porze nocnej, lub w celu uruchomienia środowiska IDE w określonej konfiguracji.

> [!NOTE]
> W przypadku zadań związanych z kompilacją zaleca się używanie programu MSBuild zamiast devenv. Aby uzyskać więcej informacji, zobacz informacje [dotyczące wiersza polecenia](../../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Aby używać przełączników [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) i [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) , należy uruchomić devenv jako administrator.

## <a name="devenv-switch-syntax"></a>Składnia przełącznika Devenv
 Domyślnie polecenia devenv przechodzą do narzędzia devenv.com.

 Narzędzie devenv.com zapewnia dostarczanie danych wyjściowych przez standardowe strumienie systemu, takie jak `stdout` i i `stderr` określa odpowiednie przekierowania we/wy podczas przechwytywania danych wyjściowych, na przykład do pliku txt. Polecenia, które zaczynają się w połączeniu z `devenv.exe` mogą używać tych samych przełączników, ale wyślą je do programu devenv.exe, pomijając narzędzie devenv.com.

 Reguły składni dla `devenv` przełączników przypominają te dla innych narzędzi wiersza polecenia systemu DOS. Następujące reguły składni mają zastosowanie do wszystkich `devenv` przełączników i ich argumentów:

- Polecenia zaczynają się od `devenv` .

- W przełącznikach nie jest rozróżniana wielkość liter.

- Podczas określania rozwiązania lub projektu pierwszy argument jest nazwą pliku rozwiązania lub pliku projektu, łącznie z ścieżką pliku.

- Jeśli pierwszy argument jest plikiem, który nie jest rozwiązaniem lub projektem, ten plik zostanie otwarty w odpowiednim edytorze w nowym wystąpieniu IDE.

- W przypadku podania nazwy pliku projektu zamiast nazwy pliku rozwiązania `devenv` polecenie przeszuka folder nadrzędny pliku projektu dla pliku rozwiązania o tej samej nazwie. Na przykład polecenie `devenv /build myproject1.vbproj` przeszuka folder nadrzędny dla pliku rozwiązania o nazwie "myproject1. sln".

    > [!NOTE]
    > Jeden i tylko jeden plik rozwiązania odwołujący się do tego projektu powinien znajdować się w folderze nadrzędnym. Jeśli folder nadrzędny nie zawiera pliku rozwiązania, który odwołuje się do tego projektu, lub jeśli folder nadrzędny zawiera dwa lub więcej plików rozwiązania, które odwołują się do niego, zostanie utworzony tymczasowy plik rozwiązania o nazwie dla tego projektu i odwołuje się do niego.

- Gdy ścieżki plików i nazwy plików zawierają spacje, należy je ująć w znaki podwójnego cudzysłowu (""). Na przykład "c:\Project \\ ".

- Wstaw jeden znak spacji między przełącznikami i argumentami w tym samym wierszu. Na przykład polecenie **devenv/log output.txt** otwiera IDE i wyprowadza wszystkie informacje dziennika dla tej sesji do output.txt.

- W poleceniach nie można używać składni dopasowania wzorców `devenv` .

## <a name="devenv-switches"></a>Przełączniki devenv
 Użyj następujących przełączników wiersza polecenia, aby wyświetlić środowisko IDE i wykonać opisane zadanie.

|Przełącznik wiersza polecenia|Opis|
|-------------------------|-----------------|
|[/Command (devenv.exe)](../../ide/reference/command-devenv-exe.md)|Uruchamia środowisko IDE i wykonuje określone polecenie.|
|[/DebugExe (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|Ładuje [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] plik wykonywalny pod kontrolą debugera. Ten przełącznik jest niedostępny dla [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] plików wykonywalnych lub. Aby uzyskać więcej informacji, zobacz [Automatyczne uruchamianie procesu w debugerze](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|
|[/LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) lub `/l`|Ustawia domyślny język IDE. Jeśli określony język nie jest uwzględniony w instalacji programu Visual Studio, to ustawienie zostanie zignorowane.|
|[/Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|Uruchamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i rejestruje wszystkie działania w pliku dziennika.|
|[/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) lub `/r`|Kompiluje i uruchamia określone rozwiązanie.|
|[/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie, minimalizuje środowisko IDE, gdy rozwiązanie jest uruchomione, i zamyka środowisko IDE po zakończeniu działania rozwiązania.|
|[/UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|Powoduje, że IDE używa zmiennych środowiskowych PATH, INCLUDE i LIB do [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] kompilowania zamiast ustawień określonych w sekcji katalogów VC + + opcji **projekty** w oknie dialogowym **Opcje** . Aby uzyskać więcej informacji, zobacz [Ustawianie zmiennych dotyczących ścieżki i środowiska dla kompilacji z wiersza polecenia](https://msdn.microsoft.com/library/99389528-deb5-43b9-b99a-03c8773ebaf4)|
|[/Edit (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|Otwiera określone pliki w uruchomionym wystąpieniu tej aplikacji. Jeśli nie ma uruchomionych wystąpień, zostanie uruchomione nowe wystąpienie z uproszczonym układem okna.|
|[/ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|Uruchamia wystąpienie środowiska IDE programu Visual Studio bez ładowania określonego dodatku.|
|[/SafeMode (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|Program uruchamia się [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w trybie awaryjnym i ładuje tylko domyślne środowisko i usługi oraz dostarczone wersje pakietów innych firm.|
|[/ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|Czyści wszystkie Tagi SkipLoading dodane do pakietów VSPackage przez użytkowników, którzy chcą uniknąć ładowania problemu pakietów VSPackage.|
|[/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md)|Wymusza, aby program Visual Studio scalał metadane zasobów, które opisują menu, paski narzędzi i grupy poleceń, ze wszystkich dostępnych pakietów VSPackage.|

 Użyj następujących przełączników wiersza polecenia, aby wykonać opisane zadanie. Te przełączniki wiersza polecenia nie wyświetlają środowiska IDE.

|Przełącznik wiersza polecenia|Opis|
|-------------------------|-----------------|
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|Wyświetla pomoc dla przełączników devenv w **oknie wiersza polecenia**.<br /><br /> **Devenv/?**|
|[/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)|Kompiluje określone rozwiązanie lub projekt zgodnie z konfiguracją określonego rozwiązania.<br /><br /> **Devenv csproj/Build**|
|[/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|Usuwa wszystkie pliki utworzone przez polecenie kompilacji bez wpływu na pliki źródłowe.<br /><br /> **Devenv csproj/Clean**|
|[/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)|Kompiluje rozwiązanie wraz z plikami wymaganymi do wdrożenia zgodnie z konfiguracją rozwiązań.<br /><br /> **Devenv csproj/Deploy**|
|[/Diff](../../ide/reference/diff.md)|Porównuje dwa pliki.  Przyjmuje cztery parametry: SourceFile, TargetFile, SourceDisplayName (opcjonalnie), TargetDisplayName (opcjonalnie).|
|[/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|Rejestruje szablony projektów lub elementów, które znajdują się w *\<VisualStudioInstallDir>* \Common7\IDE\ProjectTemplates lub *\<VisualStudioInstallDir>* \Common7\IDE\ItemTemplates, aby można było uzyskać do nich dostęp za pomocą okien dialogowych **Nowy projekt** i **Dodaj nowy element** .<br /><br /> **Devenv/InstallVSTemplates**|
|[/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)|Umożliwia określenie pliku do otrzymywania błędów podczas kompilowania.<br /><br /> **Devenv csproj/build/out log.txt**|
|[/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|Projekt do skompilowania, oczyszczenia lub wdrożenia. Tego przełącznika można używać tylko wtedy, gdy podano również przełącznik/Build,/Rebuild,/Clean lub/Deploy.|
|[/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|Określa konfigurację projektu do skompilowania lub wdrożenia. Tego przełącznika można używać tylko wtedy, gdy został również dostarczony przełącznik/Project.|
|[/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|Czyści, a następnie kompiluje określone rozwiązanie lub projekt zgodnie z konfiguracją określonego rozwiązania.|
|[/ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|Przywraca ustawienia domyślne programu Visual Studio. Opcjonalnie resetuje ustawienia do określonego pliku. vssettings.|
|[/Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|Powiadamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o scaleniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pakietów w systemie i sprawdź pamięć podręczną MEF pod kątem wszelkich zmian.|
|[/Upgrade (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|Uaktualnia określony plik rozwiązania oraz wszystkie jego pliki projektu lub określony plik projektu do bieżących [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] formatów tych plików.|

## <a name="see-also"></a>Zobacz też
 [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
