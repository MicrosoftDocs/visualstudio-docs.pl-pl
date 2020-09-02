---
title: Dostosowywanie powłoki izolowanej | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 724d4d0c4b392a362e702f33ea996df3a6fc0ad6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555972"
---
# <a name="customizing-the-isolated-shell"></a>Dostosowywanie programu Shell (izolowanego)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikację powłoki izolowanej programu Visual Studio można dostosować, zmieniając różne aspekty interfejsu użytkownika programu Visual Studio oraz ograniczając polecenia i funkcje zawarte w aplikacji wyspecjalizowanej.  
  
## <a name="using-the-applicationpkgdef-file"></a>Korzystanie z pliku Application. pkgdef  
 Rozwiązanie odizolowanego szablonu powłoki obejmuje *rozwiązanie*. Plik Application. pkgdef, który umożliwia modyfikowanie następujących funkcji:  
  
##### <a name="the-application-title"></a>Tytuł aplikacji  
 Można dostosować tytuł aplikacji, która jest wyświetlana na pasku tytułu aplikacji, zmieniając wartość w wierszu "nazwa_aplikacji" w polu *SolutionName*. Plik Application. pkgdef. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Jeśli nie chcesz, aby tytuł aplikacji wyświetlał aktualnie załadowany projekt, Zmień wartość w wierszu "ShowHierarchyRootInTitle" w polu *SolutionName*. Plik Application. pkgdef z typu DWORD: 00000001 do wartości DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Ikona aplikacji  
 Można dostosować ikonę aplikacji, która jest wyświetlana na ikonie aplikacji na pasku tytułu aplikacji. Skopiuj inną ikonę do katalogu ikony. W **Eksplorator rozwiązań**Dodaj ikonę do folderu pliki zasobów. Następnie otwórz plik VSShellStub. RC i Zastąp wartość IDI_STUBPROGRAM nazwą nowej ikony. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Logo wiersza polecenia  
 Można dostosować logo wiersza polecenia, czyli tekst, który pojawia się, gdy aplikacja jest uruchamiana z wiersza polecenia, zmieniając wartość wiersza "CommandLineLogo" w *rozwiązaniu*. Plik Application. pkgdef. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Nazwa podfolderu plików użytkownika  
 Można zmienić nazwę folderu zachowywanego przez aplikację dla plików użytkowników, zmieniając wartość wiersza "UserFilesSubFolderName" w polu *SolutionName*. Plik Application. pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Tytuł węzła drzewa rozwiązań w oknie dialogowym Nowy projekt  
 Tytuł węzła rozwiązania można dostosować w oknie dialogowym Nowy projekt, zmieniając wartość wiersza "NewProjDlgSlnTreeNodeTitle" w polu *SolutionName*. Plik Application. pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Nagłówek zainstalowanych szablonów w oknie dialogowym Nowy projekt  
 Można zmienić nagłówek zainstalowanych szablonów w oknie dialogowym Nowy projekt, zmieniając wartość wiersza "NewProjDlgInstalledTemplatesHdr" w polu *SolutionName*. Plik Application. pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Czy domyślnie ukryć różne pliki  
 Można określić, czy domyślnie ukryć różne pliki, zmieniając wartość w wierszu "HideMiscellaneousFilesByDefault" w polu *SolutionName*. Plik Application. pkgdef. Aby ukryć różne pliki, ustaw wartość `dword:00000001` i aby wyświetlić pliki, ustaw wartość `dword:00000000` .  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Określa, czy wyłączać okno danych wyjściowych  
 Możesz określić, czy okno danych wyjściowych w aplikacji ma zostać wyłączone przez zmianę wartości wiersza "DisableOutputWindow" w polu *SolutionName*. Plik Application. pkgdef. Aby wyłączyć okno dane wyjściowe, ustaw wartość `dword:00000001` i aby wyświetlić okno dane wyjściowe, ustaw wartość `dword:00000000` .  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Określa, czy zezwalać na porzucanie plików w oknie głównym  
 Możesz określić, czy zezwolić na porzucanie plików w oknie głównym aplikacji, zmieniając wartość wiersza "AllowsDroppedFilesOnMainWindow" w pliku *SolutionName*. Plik Application. pkgdef. Aby zezwolić na upuszczanie plików, ustaw wartość `dword:00000001` i aby nie zezwalać na gubienie plików, ustaw wartość `dword:00000000` .  
  
##### <a name="the-default-search-page"></a>Domyślna strona wyszukiwania  
 Możesz dostosować stronę przeglądarki sieci Web, która jest stroną wyświetlaną po otwarciu okna przeglądarki sieci Web, zmieniając wartość wiersza "DefaultSearchPage" w polu *SolutionName*. Plik Application. pkgdef.  
  
##### <a name="the-default-home-page"></a>Domyślna strona główna  
 Stronę główną można dostosować, zmieniając wartość wiersza "DefaultHomePage" w polu *SolutionName*. Plik Application. pkgdef. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Czy należy ukryć koncepcję rozwiązania  
 Można określić, czy w aplikacji ma być ukrywane rozwiązanie, zmieniając wartość w wierszu "HideSolutionConcept" w polu *SolutionName*. Plik Application. pkgdef. Aby ukryć rozwiązanie, ustaw wartość `dword:00000001` i aby wyświetlić rozwiązanie, ustaw wartość `dword:00000000` .  
  
##### <a name="the-default-debug-engine"></a>Domyślny aparat debugowania  
 Można zmienić aparat debugowania używany przez aplikację, zmieniając wartość wiersza "DefaultDebugEngine" w elemencie *SolutionName*. Plik Application. pkgdef na identyfikator GUID aparatu debugowania.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Rozszerzenie pliku opcji użytkownika  
 Można zmienić nazwę folderu zachowywanego przez aplikację dla plików użytkowników, zmieniając wartość wiersza "UserOptsFileExt" w polu *SolutionName*. Plik Application. pkgdef.  
  
##### <a name="the-solution-file-extension"></a>Rozszerzenie pliku rozwiązania  
 Rozszerzenie używane dla plików rozwiązania można zmienić, zmieniając wartość wiersza "SolutionFileExt" w polu *SolutionName*. Plik Application. pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>Katalog główny domyślnego folderu plików użytkownika  
 Można zmienić nazwę folderu głównego plików użytkownika dla aplikacji, zmieniając wartość wiersza "UserFilesSubFolderName" w polu *SolutionName*. Plik Application. pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>Identyfikator twórcy pliku rozwiązania  
 Identyfikator używany dla plików rozwiązania można zmienić, zmieniając wartość wiersza "SolutionFileCreatorIdentifier" w polu *SolutionName*. Plik Application. pkgdef.  
  
##### <a name="the-default-projects-location"></a>Domyślna lokalizacja projektów  
 Nazwę domyślnej lokalizacji projektów można zmienić, zmieniając wartość wiersza "DefaultProjectsLocation" w polu *SolutionName*. Plik Application. pkgdef.  
  
##### <a name="the-application-localization-package"></a>Pakiet lokalizacji aplikacji  
 Można zmienić pakiet lokalizacji używany przez aplikację, zmieniając wartość wiersza "AppLocalizationPackage" w polu *SolutionName*. Plik Application. pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Określa, czy element główny hierarchii ma być pokazywany w tytule  
 Możesz określić, czy element główny hierarchii ma być pokazywany na pasku tytułu aplikacji, zmieniając wartość w wierszu "ShowHierarchyRootInTitle" w polu *SolutionName*. Plik Application. pkgdef. Aby wyświetlić katalog główny hierarchii, ustaw wartość `dword:00000001` i Ukryj katalog główny hierarchii, ustaw wartość `dword:00000000` .  
  
##### <a name="specifying-a-start-page"></a>Określanie strony początkowej  
 Aby określić stronę początkową dla aplikacji niestandardowej, w polu *rozwiązanie*. Plik Application. pkgdef, ustaw wartość "DisableStartPage" na `dword:00000000` , a w obszarze `[$RootKey$\StartPage\Default]` Ustaw identyfikator URI na lokalizację pliku. XAML:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 W pliku ApplicationCommands. vsct w projekcie interfejsu użytkownika *rozwiązania*, Dodaj komentarz do wpisu "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Należy dodać plik XAML i wszystkie potrzebne pliki graficzne do projektu *SolutionName* . Te pliki muszą zostać rzeczywiście skopiowane do katalogu projektu *rozwiązania SolutionName* , które nie zostały dodane z innego katalogu.  
  
 Na wszystkich plikach ustaw właściwość **Typ elementu** na **izolowany plik powłoki** , aby pliki zostały skopiowane do katalogu *$RootFolder $* . (Aby ustawić właściwość **Typ elementu** , kliknij prawym przyciskiem myszy plik i wybierz polecenie **Właściwości**. Ta właściwość jest dostępna w obszarze **Właściwości konfiguracji**, **Ogólne**.)  
  
 Aby uzyskać więcej informacji na temat dostosowywania stron początkowych, zobacz [Dostosowywanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Używanie innych elementów powłoki izolowanej  
 Możesz użyć innych plików i projektów, które są zawarte w szablonie rozwiązaniu powłoki izolowanej, aby dodatkowo dostosować aplikację.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Włącz/Wyłącz pakiety programu Visual Studio  
 Plik *Solution*. pkgundef umożliwia wyłączenie niektórych rodzajów funkcji programu Visual Studio przez wykluczenie niektórych pakietów. Na przykład następujący wiersz:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 usuwa projekt różne pliki z zestawu szablonów projektu wyświetlanego w oknie dialogowym **Nowy projekt** . Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Włączanie/wyłączanie poleceń menu  
 Plik *SolutionName*UI. vsct zawiera listę wszystkich poleceń menu dostępnych dla izolowanej powłoki. Aby wyłączyć dane polecenie, Usuń oznaczenie komentarza do odpowiedniego wiersza. Na przykład, aby wyłączyć komentarz okna/podziału, Usuń komentarz z `<Define name="No_SplitCommand"/>` wiersza. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Mapa bitowa używana na ekranie powitalnym  
 Można dostosować mapę bitową używaną na ekranie powitalnym, która jest oknem wyświetlanym podczas uruchamiania aplikacji, zmieniając wartość wiersza "SplashScreenBitmap" w elemencie *SolutionName*. Plik Application. pkgdef. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Okno Pomoc/informacje  
 W szablonie powłoki izolowanej istnieje oddzielny projekt, którego możesz użyć do dostosowania pola pomoc/informacje dla aplikacji. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
