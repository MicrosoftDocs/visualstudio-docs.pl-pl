---
title: Strona opcji, środowisko — właściwości węzła | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ae1dc5c7eb8b1f10771afacfe1398e17b2bf8ed8
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54753519"
---
# <a name="options-page-environment-node-properties"></a>Strona opcji, środowisko — Właściwości węzła
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
W tym dokumencie opisano strony (lub kolekcje właściwości), są skojarzone z **środowiska** kategorii `DTE.Properties("Environment", <Property Page>)`, z **opcje** okno dialogowe. Tytuł każdej podsekcji to wywołanie, który umożliwia dostęp do kolekcji właściwości, a tabela w każdej podsekcji zawiera listę właściwości w kolekcji.  
  
## <a name="general"></a>Ogólne  
 `DTE.Properties("Environment", "General")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|ShowStatusBar|Get/Set (wartość logiczna)|Określa, czy pasek stanu jest widoczny.|  
|WindowMenuContainsNItems|Get/Set (krótki)|Określa, jak okna dokumentu znajdują się w dolnej części Windows menu.|  
|MRUListContainsNItems|Get/Set (krótki)|Określa, ile plików jest wyświetlane w podmenu "Ostatnio używane".|  
|Animacje|Get/Set (wartość logiczna)|Określa, czy zintegrowanego środowiska programistycznego (IDE) używa animacji w pasku stanu.|  
|AnimationSpeed|Get/Set (krótki)||  
|AutoAdjustExperience|Get/Set (wartość logiczna)|Automatycznie dostosowuje środowisko wizualne w zależności od wydajności klienta.|  
|RichClientExperienceOptions|Get/Set (Wyliczenie)|Zapewnia bogate doświadczenia wizualne z wartościami w <xref:EnvDTE100.vsRichClientExperienceOptions>.|  
|CloseButtonActiveTabOnly|Get/Set (wartość logiczna)|Określa, czy **Zamknij** przycisk jest wyświetlany tylko na karcie aktywne.|  
|AutohidePinActiveTabOnly|Get/Set (wartość logiczna)|Określa, czy **Autoukrywanie** przycisk dotyczy tylko aktywną kartę.|  
  
## <a name="add-inmacros-security"></a>Dodawanie dodatków/makr zabezpieczeń  
 `DTE.Properties("Environment", "AddinMacrosSecurity")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|MacrosEnabled|Get/Set (wartość logiczna)|Zezwala na uruchamianie makr.|  
|AddinsEnabled|Get/Set (wartość logiczna)|Umożliwia dodatków do załadowania.|  
|LoadAddinsFromTheWeb|Get/Set (wartość logiczna)|Umożliwia dodatków ładowanie z adresu URL w sieci Web.|  
  
## <a name="documents"></a>Dokumenty  
 `DTE.Properties("Environment", "Documents")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|ReuseSavedActiveDocWindow|Get/Set (wartość logiczna)|Określa, czy otwieranie nowego pliku używa bieżącego okna dokumentu, jeśli bieżący dokument zostanie zapisany. `false` oznacza, że zawsze otwieraj dla każdego dokumentu, otworzyć nowe okno dokumentu.|  
|DetectFileChangesOutsideIDE|Get/Set (wartość logiczna)|Określa, czy środowisko automatycznie ładuje ponownie plików otwieranych w IDE, gdy system operacyjny powiadamia IDE, że pliki zostały zmodyfikowane na dysku.|  
|AutoloadExternalChanges|Get/Set (wartość logiczna)|Określa, czy wykrył, że zewnętrzne zmiany w otwartych dokumentach automatycznie załadować ponownie zmodyfikowanego pliku, jeśli Otwórz dokument nie został zmodyfikowany. Jeśli zostanie zmodyfikowany w otwartym dokumencie, a ta właściwość jest `true`, a następnie monituje IDE, jak gdyby ta właściwość `false`.|  
|InitializeOpenFileFromCurrentDocument|Get/Set (wartość logiczna)|Określa, czy <xref:EnvDTE.DTEClass.OpenFile%2A> polecenie inicjowania inicjuje nazwy katalogów i plików z ostatnich aktywnego dokumentu lub z ostatnio otwarto pliku.|  
|MiscFilesProjectSavesLastNItems|Get/Set (krótki)|Określa, ile plików rekordów projektu różne pliki. W rezultacie możesz zobaczyć, co ostatnio otwartym jako inny plik na dysku obok użycia środowiska IDE.|  
|ShowMiscFilesProject|Get/Set (wartość logiczna)|Określa, czy jest wyświetlany projekt różne pliki.|  
|CheckForConsisentLineEndings|Get/Set (wartość logiczna)|Sprawdza spójność końców wierszy przy ładowaniu plików.|  
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (wartość logiczna)|Zapisuje dokumenty w formacie Unicode, gdy nie można zapisać danych w stronie kodowej.|  
|DontShowGlobalUndoChangeLossDialog|Get/Set (wartość logiczna)|Zostanie wyświetlone ostrzeżenie, gdy globalne cofanie modyfikuje innych edytowanych plików.|  
|AllowEditingReadOnlyFiles|Get/Set (wartość logiczna)|Zezwala na edytowanie plików tylko do odczytu, ale zapewniają ostrzeżenie po próba je zapisać.|  
|DocumentDockPreference|Get/Set (Wyliczenie)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. Pozycja w karcie dobrze, do której należy wstawić otwartego dokumentu.|  
  
## <a name="extension-manager"></a>Menedżer rozszerzeń  
 `DTE.Properties("Environment", "ExtensionManager")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|EnableAdminExtensions|Get/Set (wartość logiczna)|Ładuje rozszerzenia dla poszczególnych użytkowników, po uruchomieniu programu Visual Studio w obszarze poświadczeń administratora. Po zmianie tej wartości, należy ponownie uruchomić program Visual Studio.|  
|EnableOnline|Get/Set (wartość logiczna)|Umożliwia dostęp do rozszerzenia w galerii Visual Studio.|  
|AutomaticallyCheckForUpdates|Get/Set (wartość logiczna)|Automatycznie sprawdza, czy aktualizacje do zainstalowanych rozszerzeń.|  
  
## <a name="find-and-replace"></a>Znajdź i zamień  
 `DTE.Properties("Environment", "FindAndReplace")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|ShowWarningMessages|Get/Set (wartość logiczna)|Wyświetla komunikaty ostrzegawcze.|  
|InitializeFromEditor|Get/Set (wartość logiczna)|Automatycznie wypełni **Znajdź** pole z tekstem z edytora.|  
|ShowMessageBoxes|Get/Set (wartość logiczna)|Wyświetla komunikaty informacyjne.|  
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (wartość logiczna)|Ukrywa **Znajdź i Zamień** okna po dopasowanie znajduje się za pomocą **szybkie znajdowanie** lub **szybkiego zamieniania**.|  
  
## <a name="import-and-export-settings"></a>Import i eksport ustawień  
 `DTE.Properties("Environment", "Import and Export Settings")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|TrackTeamSettings|Get/Set (wartość logiczna)|Używa ustawień w pliku określonym przez TeamSettingsFile.|  
|TeamSettingsFile|Get/Set (ciąg)|Nazwa pliku, który zawiera ustawienia zespołu.|  
|AutoSaveFile|Get/Set (ciąg)|Nazwa pliku, gdy ustawienia użytkownika są zapisywane automatycznie.|  
  
## <a name="international-settings"></a>Ustawienia międzynarodowe  
 `DTE.Properties("Environment", "International")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|Język|Get/Set (ciąg)|Wartość identyfikatora LCID dla bieżącego języka dla programu Visual Studio.|  
  
## <a name="keyboard"></a>Klawiatury  
 `DTE.Properties("Environment", "Keyboard")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|Schemat|Get/Set (ciąg)|Zwraca ciąg, który zawiera schemat wbudowany, ciąg zawierający pełną ścieżkę pliku .vsk, który jest ładowany, "(domyślna)", jeśli żaden plik .vsk jest ładowany.|  
  
## <a name="projects-and-solution"></a>Projekty i rozwiązania  
 `DTE.Properties("Environment", "ProjectsAndSolution")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|OnRunOrPreview|Get/Set (ciąg)|Określa, czy IDE zapisuje całą zawartość przed przystąpieniem do przeglądania lub systemem skompilowanym projektem.|  
|ProjectsLocation|Get/Set (ciąg)|Określa domyślnego katalogu, w którym **Dodaj projekt** okno dialogowe zapisuje nowe projekty.|  
|ShowOutputWindowBeforeBuild|Get/Set (wartość logiczna)|Określa, czy uruchomienie kompilacji Wyświetla **dane wyjściowe** okna.|  
|ShowTaskListAfterBuild|Get/Set (wartość logiczna)|Określa, czy operacja powiodła się kompilacja Wyświetla **listy zadań** po zakończeniu kompilacji.|  
|TrackFileSelectionInExplorer|Get/Set (wartość logiczna)|Określa, czy bieżący element jest śledzona w **Eksploratora rozwiązań**.|  
|AlwaysShowSolutionNode|Get/Set (wartość logiczna)|Określa, czy węzeł rozwiązania jest wyświetlany.|  
|OnlySaveStartupProjectsAndDependencies|Get/Set (wartość logiczna)|Określa, czy operacji zapisywania są ograniczone do uruchomienia projektów i ich pliki zależne.|  
|ShowAdvancedBuildConfigurations|Get/Set (wartość logiczna)|Określa, czy zaawansowane konfiguracje kompilacji są wyświetlane.|  
|ConcurrentBuilds|Get/Set (ciąg)|Określa maksymalną liczbę równolegle kompilowanych projektów, które mogą wystąpić.|  
|SaveNewProjects|Get/Set (wartość logiczna)|Określa, czy nowe projekty są zapisywane automatycznie utworzone.|  
|PromptForRenameSymbol|Get/Set (wartość logiczna)|Określa, czy Monituj o symboliczną zmianę nazwy podczas pliki zostały zmienione.|  
|OnRunWhenErrors|Get/Set (Wyliczenie)|Określa zachowanie przy uruchomieniu, gdy Kompilacja została ukończona z błędami.|  
|OnRunWhenOutOfDate|Get/Set (Wyliczenie)|Określa zachowanie przy uruchomieniu, gdy projekt jest nieaktualny.|  
|ProjectTemplatesLocation|Get/Set (ciąg)|Katalog, który zawiera szablony projektów użytkownika.|  
|ProjectItemTemplatesLocation|Get/Set (ciąg)|Katalog zawierający szablonów elementu użytkownika.|  
|DefaultBehaviorForStartupProjects|Get/Set (ciąg)||  
|MSBuildOutputVerbosity|Get/Set (ciąg)|Określa poziom szczegółowości danych wyjściowych kompilacji.|  
  
## <a name="startup"></a>Uruchamianie  
 `DTE.Properties("Environment", "Startup")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|OnStartUp|Get/Set (Wyliczenie)|Działanie podejmowane w momencie uruchamiania z <xref:EnvDTE.vsStartUp>, przy użyciu wartości od 0 do 5:<br /><br /> -   0: Otwórz stronę główną<br />-   1: Załaduj ostatnie załadowanego rozwiązania<br />-   2: Pokaż **Otwórz projekt** okno dialogowe<br />-   3: Pokaż **nowy projekt** okno dialogowe<br />-   4: Pokaż puste środowisko<br />-   5: Pokaż stronę początkową|  
|StartPageRSSUrl|Get/Set (ciąg)|Adres URL dla źródła danych RSS, jest używany podczas uruchamiania.|  
|StartPageRefreshDownloadedContent|Get/Set (wartość logiczna)|Odświeża strona startowa po każdym przejściu z interwałem określonym w StartPageRefreshInterval.|  
|StartPageRefreshInterval|Get/Set (krótki)|Interwał w minutach, aby odświeżyć stronę początkową.|  
  
## <a name="tasklist"></a>TaskList  
 `DTE.Properties("Environment", "TaskList")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|ConfirmTaskDeletion|Get/Set (wartość logiczna)|Określa, czy okno dialogowe z potwierdzeniem Wyświetla podczas usuwania zadania z **listy zadań**.|  
|WarnOnAddingHiddenItem|Get/Set (wartość logiczna)|Określa, czy zostanie wyświetlone ostrzeżenie podczas dodawania użytkownika zadania, które nie będą wyświetlane.|  
|DontShowFilePaths|Get/Set (wartość logiczna)|Określa, czy ma być wyświetlana ełne ścieżki plików na liście zadań.|  
|CommentTokens|SafeArray|Zwraca SafeArray komentarza wartości tokenu. Każdy ma pola, `Name` (ciąg) i `Priority` (<xref:EnvDTE.vsTaskPriority>, wysoki, średni lub niski).|  
  
## <a name="web-browser"></a>Przeglądarki sieci Web  
 `DTE.Properties("Environment", "WebBrowser")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|Strona główna|Get/Set (ciąg)|Reprezentuje adres URL strony głównej.|  
|SearchPage|Get/Set (ciąg)|Reprezentuje adres URL strony wyszukiwania.|  
|ViewSourceIn|Get/Set (Wyliczenie)|<xref:EnvDTE.vsBrowserViewSource> (Źródło, projekt, zewnętrzny).|  
|ViewSourceExternalProgram|Get/Set (ciąg)|Ścieżka Podgląd źródła zewnętrznego.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie ustawień opcji](http://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Określanie nazw elementów właściwości na stronach opcji](http://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Strona opcji, czcionki i kolory — właściwości węzła](../../ide/reference/options-page-fonts-and-colors-node-properties.md)   
 [Strona opcji, Edytor tekstu — właściwości węzła](../../ide/reference/options-page-text-editor-node-properties.md)   
 [Środowisko, Opcje — okno dialogowe](../../ide/reference/environment-options-dialog-box.md)
