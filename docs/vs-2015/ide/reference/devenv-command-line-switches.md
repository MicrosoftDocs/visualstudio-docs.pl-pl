---
title: Przełączniki wiersza polecenia Devenv | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4eadb8c9553873f43ad9435ad43fae00f57affcb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050715"
---
# <a name="devenv-command-line-switches"></a>Przełączniki wiersza polecenia Devenv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Devenv pozwala ustawić różne opcje zintegrowanego środowiska programistycznego (IDE) i również tworzenia, debugowania i wdrażania projektów, w wierszu polecenia. Używaj tych przełączników, aby uruchomić środowisko IDE z skrypt lub plik .bat, na przykład skrypt nocna kompilacja, lub aby uruchomić środowisko IDE w określonej konfiguracji.  
  
> [!NOTE]
>  Dla zadania związane z kompilacji teraz zalecane jest używanie programu MSBuild zamiast devenv. Aby uzyskać więcej informacji, zobacz [odwołanie do wiersza polecenia](../../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Devenv musi działać jako administrator, aby można było używać [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) i [/installvstemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) przełączników.  
  
## <a name="devenv-switch-syntax"></a>Składnia — przełącznik Devenv  
 Domyślnie polecenia devenv przekazać przełączników do narzędzia devenv.com.  
  
 Zapewnia dostarczanie danych wyjściowych za pomocą strumieni standardowych systemowych, takich jak narzędzie devenv.com `stdout` i `stderr`i określa odpowiedni przekierowanie we/wy, gdy na przykład przechwytuje dane wyjściowe do pliku txt. Polecenia, które zaczyna się zamiast tego `devenv.exe` można użyć tego samego przełączników, ale będzie wysyłać je do programu devenv.exe z pominięciem narzędzie devenv.com.  
  
 Zasady składni `devenv` przełączników przypominają wyjątki dla innych narzędzi wiersza polecenia systemu DOS. Następujące reguły składni mają zastosowanie do wszystkich `devenv` przełączników i ich argumentów:  
  
- Polecenia zaczynają się od `devenv`.  
  
- Przełączniki nie jest rozróżniana wielkość liter.  
  
- Podczas określania rozwiązania lub projektu, pierwszy argument jest nazwa pliku rozwiązania lub pliku projektu, w tym ścieżki pliku.  
  
- Jeśli pierwszy argument jest plik, który nie jest rozwiązanie lub projekt, ten plik zostanie otwarty w odpowiedniego edytora, w nowym wystąpieniu środowiska IDE.  
  
- Jeśli podasz nazwę pliku projektu, a nie nazwę pliku rozwiązania `devenv` polecenia wyszuka folderu nadrzędnego pliku projektu plik rozwiązania, który ma taką samą nazwę. Na przykład polecenie `devenv /build myproject1.vbproj` wyszuka folder nadrzędny do pliku rozwiązania, który nosi nazwę "myproject1.sln".  
  
    > [!NOTE]
    >  Jeden i tylko jeden plik rozwiązania, który odwołuje się do tego projektu powinna znajdować się w folderu nadrzędnego. Jeśli folder nadrzędny zawiera nie pliku rozwiązania, który odwołuje się do tego projektu lub jeśli folder nadrzędny zawiera dwa lub więcej plików rozwiązania, które ją przywołują, następnie rozwiązanie tymczasowe zostanie utworzony plik, nosi nazwę dla tego projektu, a następnie odwołuje się do niej.  
  
- Gdy nazwy pliku i ścieżki plików zawiera spacje, należy ująć je w znaki podwójnego cudzysłowu (""). Na przykład "c:\project\\".  
  
- Wstaw jeden znak spacji między przełączniki i argumenty, w tym samym wierszu. Na przykład polecenie **devenv/log output.txt** IDE otwiera i wyświetla wszystkie rejestrowania informacji w ramach danej sesji output.txt.  
  
- Nie można użyć składni wieloznacznej `devenv` poleceń.  
  
## <a name="devenv-switches"></a>Przełączniki Devenv  
 Użyj następujących przełączników wiersza polecenia do wyświetlania IDE i wykonać zadania opisane.  
  
|Przełącznik wiersza polecenia|Opis|  
|-------------------------|-----------------|  
|[/ Command (devenv.exe)](../../ide/reference/command-devenv-exe.md)|Uruchamia IDE i wykonuje określone polecenie.|  
|[/ Debugexe — (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|Ładunki [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] wykonywalnego pod kontrolą debugera. Ten parametr nie jest dostępny dla [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../includes/csprcs-md.md)] plików wykonywalnych. Aby uzyskać więcej informacji, zobacz [automatycznie uruchamia proces w debugerze](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|  
|[/ LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) lub `/l`|Ustawia domyślny język dla środowiska IDE. Jeśli określony język nie jest uwzględniony w instalacji programu Visual Studio, to ustawienie jest ignorowane.|  
|[/ Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|Uruchamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i loguje wszelką aktywność do pliku dziennika.|  
|[/ Uruchomienia (devenv.exe)](../../ide/reference/run-devenv-exe.md) lub `/r`|Kompiluje i uruchamia określone rozwiązanie.|  
|[/ Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie, minimalizuje IDE w rozwiązaniu jest uruchamiany, gdy IDE jest zamykane po rozwiązaniu zakończył działanie.|  
|[/UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|Powoduje, że środowisko IDE będzie używać zmiennych środowiskowych PATH, INCLUDE i Biblioteka, aby uzyskać [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] kompilacji, a nie ustawienia określone w sekcji katalogi VC ++ **projektów** opcji na liście **opcje** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](http://msdn.microsoft.com/library/99389528-deb5-43b9-b99a-03c8773ebaf4)|  
|[/ Edit (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|Otwiera określone pliki w działającej instancji tej aplikacji. W przypadku Brak uruchomionych wystąpień rozpocznie nowa instancja o uproszczonym układzie okna.|  
|[/ ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|Uruchamia wystąpienie programu Visual Studio IDE bez ładowania określonego dodatku.|  
|[/ SafeMode (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|Uruchamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w trybie awaryjnym, ładuje tylko środowisko domyślne i usługi oraz wydane wersje pakietów innych firm.|  
|[/ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|Czyści wszystkie tagi SkipLoading dodane do VSPackages przez użytkowników, którzy chcą uniknąć obciążania problem pakietów VSPackage.|  
|[/ Konfiguracja (devenv.exe)](../../ide/reference/setup-devenv-exe.md)|Wymusza Visual Studio, aby scalić metadanych zasobu, który opisuje menu, paski narzędzi i grup poleceń, ze wszystkich pakietów VSPackage, które są dostępne.|  
  
 Użyj następujących przełączników wiersza polecenia do wykonania zadań opisanych. Te przełączniki wiersza polecenia nie są wyświetlane w środowisku IDE.  
  
|Przełącznik wiersza polecenia|Opis|  
|-------------------------|-----------------|  
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|Wyświetla Pomoc dotyczącą przełączniki devenv **okna wiersza polecenia**.<br /><br /> **Devenv /?**|  
|[/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)|Tworzy określonego rozwiązania lub projektu, zgodnie z konfiguracją określonego rozwiązania.<br /><br /> **/ Build myproj.csproj Devenv**|  
|[/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|Usuwa wszystkie pliki utworzone za pomocą polecenia kompilacji, bez wywierania wpływu na pliki źródłowe.<br /><br /> **Devenv myproj.csproj / clean**|  
|[/ Wdrażanie (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)|Kompiluje rozwiązanie, wraz z plikami niezbędne do wdrożenia, zgodnie z konfiguracją rozwiązania.<br /><br /> **Devenv myproj.csproj / deploy**|  
|[/Diff](../../ide/reference/diff.md)|Porównuje dwa pliki.  Przyjmuje cztery parametry: SourceFile, TargetFile, SourceDisplayName(optional),TargetDisplayName(optional).|  
|[/ InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|Rejestruje szablony projektu lub elementu, które znajdują się w  *\<VisualStudioInstallDir >* \Common7\IDE\ProjectTemplates lub  *\<VisualStudioInstallDir >* \Common7 \IDE\ItemTemplates, dzięki czemu są one dostępne za pośrednictwem **nowy projekt** i **Dodaj nowy element** okien dialogowych.<br /><br /> **/ Installvstemplates Devenv**|  
|[/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)|Pozwala określić plik, aby otrzymywać komunikaty o błędach podczas kompilacji.<br /><br /> **/ Build myproj.csproj Devenv/out log.txt**|  
|[/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|Projekt do kompilacji, czyszczenia lub wdrożenia. Można użyć tego przełącznika, tylko wtedy, gdy podano również/Build, / rebuild, / clean, lub / deploy — przełącznik.|  
|[/ ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|Określa konfigurację projektu do kompilacji lub wdrożenia. Można użyć tego przełącznika, tylko wtedy, gdy podano również przełącznika/Project.|  
|[/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|Czyści, a następnie kompiluje określone rozwiązanie lub projekt zgodnie z konfiguracją określonego rozwiązania.|  
|[/ ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|Przywraca ustawienia domyślne programu Visual Studio. Opcjonalnie resetuje ustawienia do określonego pliku .vssettings.|  
|[/Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|Powiadamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] do scalenia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] żadnych zmian w pamięci podręcznej pakietów w systemie i wyboru MEF.|  
|[/ Upgrade (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|Uaktualnienie do bieżącego pliku określonego rozwiązania i wszystkie jego pliki projektu lub pliku określonego projektu, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] formatów tych plików.|  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
