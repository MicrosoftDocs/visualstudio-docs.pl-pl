---
title: Dostosowywanie programu Isolated Shell | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786691"
---
# <a name="customizing-the-isolated-shell"></a>Dostosowywanie programu Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikacji programu Visual Studio izolowane powłoki można dostosować, zmieniając różne aspekty interfejsu użytkownika programu Visual Studio, a także przez ograniczenie możliwości wykonywania poleceń i opcji dołączony do specjalistycznych aplikacji.  
  
## <a name="using-the-applicationpkgdef-file"></a>Przy użyciu pliku Application.pkgdef  
 Zawiera rozwiązanie szablonu izolowanej powłoki *SolutionName*. Plik Application.pkgdef, który umożliwia modyfikowanie następujące funkcje:  
  
##### <a name="the-application-title"></a>Tytuł aplikacji  
 Można dostosować tytuł aplikacji, czyli nazwę, która jest wyświetlana na pasku tytułu aplikacji, zmieniając wartość wiersza "AppName" w *SolutionName*. Plik Application.pkgdef. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie prostej Isolated Shell aplikacji](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Jeśli użytkownik nie chce Tytuł aplikacji, aby wyświetlić projekt, który jest aktualnie załadowana, zmień wartość na wiersz "ShowHierarchyRootInTitle" *SolutionName*. Application.pkgdef plik z DWORD: 00000001 DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Ikona aplikacji  
 Można dostosować ikonę aplikacji, która znajduje się ikona, wyświetlane według nazwy aplikacji, na pasku tytułu aplikacji. Skopiuj inną ikonę do katalogu ikony. W **Eksploratora rozwiązań**, Dodaj ikonę do folderu plików zasobów. Następnie otwórz plik VSShellStub.rc i zastąp wartość IDI_STUBPROGRAM o nazwie ikonę nowego elementu. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie prostej Isolated Shell aplikacji](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Logo wiersza polecenia  
 Można dostosować logo wiersza polecenia jest tekst, który jest wyświetlany, gdy aplikacja jest uruchamiana z wiersza polecenia, zmieniając wartość na wiersz "CommandLineLogo" *SolutionName*. Plik Application.pkgdef. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie podstawowej aplikacji Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Nazwa podfolderu plików użytkownika  
 Możesz zmienić nazwę folderu aplikacji obsługuje dla plików użytkownika, zmieniając wartość na wiersz "UserFilesSubFolderName" *SolutionName*. Plik Application.pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Tytuł rozwiązania węzła drzewa w oknie dialogowym Nowy projekt  
 Można dostosować tytuł węzeł rozwiązania w oknie dialogowym Nowy projekt, zmieniając wartość na wiersz "NewProjDlgSlnTreeNodeTitle" *SolutionName*. Plik Application.pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Nagłówek zainstalowanych szablonów w oknie dialogowym Nowy projekt  
 Nagłówek zainstalowanych szablonów w oknie dialogowym Nowy projekt można zmienić, zmieniając wartość na wiersz "NewProjDlgInstalledTemplatesHdr" *SolutionName*. Plik Application.pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Umożliwia określenie, czy Ukryj różne pliki domyślnie  
 Można określić, czy ma być Ukryj różne pliki domyślne, zmieniając wartość na wiersz "HideMiscellaneousFilesByDefault" *SolutionName*. Plik Application.pkgdef. Aby ukryć różne pliki, należy ustawić wartość `dword:00000001`i aby wyświetlić pliki, ustaw wartość `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Umożliwia określenie, czy wyłączyć w oknie danych wyjściowych  
 Można określić, czy nie można wyłączyć w oknie danych wyjściowych w aplikacji, zmieniając wartość na wiersz "DisableOutputWindow" *SolutionName*. Plik Application.pkgdef. Aby wyłączyć w oknie danych wyjściowych, należy ustawić wartość `dword:00000001`, a następnie do wyświetlenia w oknie danych wyjściowych, ustaw wartość `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Umożliwia określenie, czy zezwolić porzuconych plików w oknie głównym  
 Można określić, czy nie zezwalaj na wyświetlanie plików porzuconych głównego okna aplikacji, zmieniając wartość na wiersz "AllowsDroppedFilesOnMainWindow" *SolutionName*. Plik Application.pkgdef. Aby umożliwić elementów usuniętych plików, należy ustawić wartość `dword:00000001`i aby nie zezwalać elementów usuniętych plików, należy ustawić wartość `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>Domyślna strona wyszukiwania  
 Można dostosować stronę przeglądarki sieci web, czyli strony, która jest wyświetlana po otwarciu okna przeglądarki sieci web, zmieniając wartość wiersza "DefaultSearchPage" w *SolutionName*. Plik Application.pkgdef.  
  
##### <a name="the-default-home-page"></a>Domyślną stronę główną  
 Na stronie głównej można dostosować, zmieniając wartość na wiersz "DefaultHomePage" *SolutionName*. Plik Application.pkgdef. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie podstawowej aplikacji Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Umożliwia określenie, czy ukryć koncepcji rozwiązania  
 Można określić, czy chce ukryć rozwiązania w aplikacji, zmieniając wartość wiersza "HideSolutionConcept" w *SolutionName*. Plik Application.pkgdef. Aby ukryć rozwiązania, należy ustawić wartość `dword:00000001`i aby wyświetlić rozwiązania, należy ustawić wartość `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Domyślny aparat debugowania  
 Możesz zmienić aparat debugowania, Twoja aplikacja używa, zmieniając wartość na wiersz "DefaultDebugEngine" *SolutionName*. Plik Application.pkgdef zgodnie z identyfikatorem GUID silnik debugowania.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Rozszerzenie pliku plik opcji użytkownika  
 Możesz zmienić nazwę folderu aplikacji obsługuje dla plików użytkownika, zmieniając wartość na wiersz "UserOptsFileExt" *SolutionName*. Plik Application.pkgdef.  
  
##### <a name="the-solution-file-extension"></a>Rozszerzenie pliku rozwiązania  
 Można zmienić rozszerzenia pliki rozwiązania, zmieniając wartość na wiersz "SolutionFileExt" *SolutionName*. Plik Application.pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>Główny folder plików użytkownika domyślnego  
 Można zmienić nazwy folderu głównego plików użytkownika dla aplikacji, zmieniając wartość na wiersz "UserFilesSubFolderName" *SolutionName*. Plik Application.pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>Identyfikator twórcy plik rozwiązania  
 Możesz zmienić identyfikator używany na potrzeby pliki rozwiązania, zmieniając wartość na wiersz "SolutionFileCreatorIdentifier" *SolutionName*. Plik Application.pkgdef.  
  
##### <a name="the-default-projects-location"></a>Domyślna lokalizacja projektów  
 Nazwa domyślnej lokalizacji projektów można zmienić, zmieniając wartość na wiersz "DefaultProjectsLocation" *SolutionName*. Plik Application.pkgdef.  
  
##### <a name="the-application-localization-package"></a>Lokalizacja pakietu aplikacji  
 Można zmienić używany dla aplikacji, zmieniając wartość na wiersz "AppLocalizationPackage" pakiet lokalizacji *SolutionName*. Plik Application.pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Umożliwia określenie, czy pokazać główny hierarchii w tytule  
 Można określić, czy ma być wyświetlana głównego hierarchii na pasku tytułu w aplikacji, zmieniając wartość na wiersz "ShowHierarchyRootInTitle" *SolutionName*. Plik Application.pkgdef. Aby wyświetlić główny hierarchii, należy ustawić wartość `dword:00000001`i aby ukryć głównego hierarchii, należy ustawić wartość `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Określanie strony początkowej  
 Aby określić strony początkowej dla swojej niestandardowej aplikacji w *SolutionName*. Plik Application.pkgdef, ustaw wartość "DisableStartPage" `dword:00000000`, a następnie w obszarze `[$RootKey$\StartPage\Default]` Ustaw identyfikator URI do lokalizacji pliku .xaml:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 W pliku Applicationcommands.vsct w *SolutionName*projektu interfejsu użytkownika, komentarz wpis "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Należy dodać plik .xaml i wszystkich plików graficznych, należy do *SolutionName* projektu. Te pliki faktycznie muszą zostać skopiowane do *SolutionName* katalogu projektu, nie zostały dodane z niektórych z innego katalogu.  
  
 Dla wszystkich plików, należy ustawić **typu elementu** właściwości **izolowane powłoki pliku** w kolejności plików do skopiowania do *$RootFolder$* katalogu. (Aby ustawić **typu elementu** właściwości, kliknij prawym przyciskiem myszy plik i wybierz **właściwości**. Ta właściwość znajduje się w folderze **właściwości konfiguracji**, **ogólne**.)  
  
 Aby uzyskać więcej informacji na temat dostosowywania stron startowych, zobacz [Dostosowywanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Za pomocą inne elementy programu isolated shell  
 Można użyć innych plików i projektów, które są zawarte w szablonie rozwiązań izolowanej powłoki w celu dalszego dostosowywania aplikacji.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Włącz/Wyłącz pakietów programu Visual Studio  
 *SolutionName*pliku pkgundef umożliwia wyłączenie niektórych rodzajów funkcjonalność programu Visual Studio poprzez wykluczenie niektórych pakietów. Na przykład następujący wiersz:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Usuwa projekt różne pliki z zestawu szablonów projektu wyświetlane w **nowy projekt** okna dialogowego. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie prostej Isolated Shell aplikacji](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Włącz/Wyłącz polecenia menu  
 *SolutionName*UI.vsct plik zawiera listę zakomentowany dostępne dla programu isolated shell poleceń menu. Aby wyłączyć podanego polecenia, usuń znaczniki komentarza odpowiedni wiersz. Na przykład, aby wyłączyć komentarz podział/okna, usuń znaczniki komentarza `<Define name="No_SplitCommand"/>` wiersza. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie prostej Isolated Shell aplikacji](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Mapy bitowej na ekranie powitalnym  
 Można dostosować mapy bitowej na ekranie powitalnym jest oknem, które jest wyświetlane, gdy aplikacja jest uruchamiana, zmieniając wartość wiersza "SplashScreenBitmap" w *SolutionName*. Plik Application.pkgdef. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie prostej Isolated Shell aplikacji](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Pomoc/informacje o oknie  
 W szablonie izolowanej powłoki jest osobnym projekcie umożliwia dostosowywanie Pomocy/o okno aplikacji. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie prostej Isolated Shell aplikacji](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
