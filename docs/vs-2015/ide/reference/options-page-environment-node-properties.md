---
title: Strona opcji, właściwości węzła środowiska | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c7b6370793068ff07f30066ddd51b72dcc924b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668701"
---
# <a name="options-page-environment-node-properties"></a>Strona opcji, środowisko — Właściwości węzła
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tym dokumencie opisano strony (lub kolekcje właściwości), które są skojarzone z kategorią **środowiskową** `DTE.Properties("Environment", <Property Page>)`, w oknie dialogowym **Opcje** . Tytuł każdej podsekcji to wywołanie, które jest używane w celu uzyskania dostępu do kolekcji właściwości, a tabela w każdej podsekcji wyświetla właściwości w kolekcji.

## <a name="general"></a>Ogólne
 `DTE.Properties("Environment", "General")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|ShowStatusBar|Get/Set (wartość logiczna)|Określa, czy pasek stanu jest widoczny.|
|WindowMenuContainsNItems|Pobierz/ustaw (krótki)|Określa, w jaki sposób okna dokumentów są zawarte w dolnej części menu systemu Windows.|
|MRUListContainsNItems|Pobierz/ustaw (krótki)|Określa, ile plików jest wyświetlanych w podmenu "ostatnio używane".|
|Animacje|Get/Set (wartość logiczna)|Określa, czy zintegrowane środowisko programistyczne (IDE) używa animacji na pasku stanu.|
|AnimationSpeed|Pobierz/ustaw (krótki)||
|AutoAdjustExperience|Get/Set (wartość logiczna)|Program automatycznie dostosowuje działanie wizualizacji w zależności od wydajności klienta.|
|RichClientExperienceOptions|Get/Set (Wyliczenie)|Umożliwia rozbudowane środowisko klienta z wartościami w <xref:EnvDTE100.vsRichClientExperienceOptions>.|
|CloseButtonActiveTabOnly|Get/Set (wartość logiczna)|Określa, czy przycisk **Zamknij** jest pokazywany tylko na aktywnej karcie.|
|AutohidePinActiveTabOnly|Get/Set (wartość logiczna)|Określa, czy przycisk **Autoukrywanie** ma wpływ tylko na aktywną kartę.|

## <a name="add-inmacros-security"></a>Zabezpieczenia dodatków/makr
 `DTE.Properties("Environment", "AddinMacrosSecurity")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|MacrosEnabled|Get/Set (wartość logiczna)|Zezwala na uruchamianie makr.|
|AddinsEnabled|Get/Set (wartość logiczna)|Zezwala na ładowanie dodatków.|
|LoadAddinsFromTheWeb|Get/Set (wartość logiczna)|Zezwala dodatekom na ładowanie z adresu URL w sieci Web.|

## <a name="documents"></a>Dokumenty
 `DTE.Properties("Environment", "Documents")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|ReuseSavedActiveDocWindow|Get/Set (wartość logiczna)|Określa, czy otwieranie nowego pliku ponownie używa bieżącego okna dokumentu, jeśli bieżący dokument zostanie zapisany. `false` oznacza, że zawsze otwiera nowe okno dokumentu dla każdego otwartego dokumentu.|
|DetectFileChangesOutsideIDE|Get/Set (wartość logiczna)|Określa, czy środowisko automatycznie ponownie ładuje pliki otwierane w środowisku IDE, gdy system operacyjny powiadamia IDE o tym, że pliki zostały zmodyfikowane na dysku.|
|AutoloadExternalChanges|Get/Set (wartość logiczna)|Określa, czy wykryte modyfikacje zewnętrzne otwierają dokumenty automatycznie ładują zmodyfikowany plik, jeśli otwarty dokument nie jest modyfikowany. Jeśli otwarty dokument jest modyfikowany, a ta właściwość jest `true`, IDE będzie monitowany o to, czy ta właściwość została `false`.|
|InitializeOpenFileFromCurrentDocument|Get/Set (wartość logiczna)|Określa, czy <xref:EnvDTE.DTEClass.OpenFile%2A> polecenie podzieli nazwę katalogu i pliku z ostatniego aktywnego dokumentu lub z ostatniego miejsca, w którym otwarto plik.|
|MiscFilesProjectSavesLastNItems|Pobierz/ustaw (krótki)|Określa, ile plików jest rekordów projektu różne pliki. W związku z tym można zobaczyć, co ostatnio było otwarte jako różne pliki na dysku przy następnym użyciu środowiska IDE.|
|ShowMiscFilesProject|Get/Set (wartość logiczna)|Określa, czy jest wyświetlany projekt różne pliki.|
|CheckForConsisentLineEndings|Get/Set (wartość logiczna)|Sprawdza spójność końców wierszy podczas ładowania pliku.|
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (wartość logiczna)|Zapisuje dokumenty jako Unicode, gdy nie można zapisać danych na stronie kodowej.|
|DontShowGlobalUndoChangeLossDialog|Get/Set (wartość logiczna)|Wyświetla ostrzeżenie, gdy globalne cofnięcie zmodyfikuje inne edytowane pliki.|
|AllowEditingReadOnlyFiles|Get/Set (wartość logiczna)|Umożliwia edytowanie plików tylko do odczytu, ale w przypadku próby ich zapisania należy podać ostrzeżenie.|
|DocumentDockPreference|Get/Set (Wyliczenie)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>., Umieść na karcie, w której ma zostać wstawiony otwarty dokument.|

## <a name="extension-manager"></a>Menedżer rozszerzeń
 `DTE.Properties("Environment", "ExtensionManager")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|EnableAdminExtensions|Get/Set (wartość logiczna)|Ładuje rozszerzenia dla poszczególnych użytkowników, gdy program Visual Studio jest uruchamiany w ramach poświadczeń administratora. Po zmianie tej wartości program Visual Studio musi zostać ponownie uruchomiony.|
|EnableOnline|Get/Set (wartość logiczna)|Umożliwia dostęp do rozszerzeń w galerii programu Visual Studio.|
|AutomaticallyCheckForUpdates|Get/Set (wartość logiczna)|Automatycznie sprawdza dostępność aktualizacji zainstalowanych rozszerzeń.|

## <a name="find-and-replace"></a>Znajdź i zamień
 `DTE.Properties("Environment", "FindAndReplace")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|ShowWarningMessages|Get/Set (wartość logiczna)|Wyświetla komunikaty ostrzegawcze.|
|InitializeFromEditor|Get/Set (wartość logiczna)|Automatycznie wypełnia pole **Znajdź** z tekstem z edytora.|
|ShowMessageBoxes|Get/Set (wartość logiczna)|Wyświetla komunikaty informacyjne.|
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (wartość logiczna)|Ukrywa okno **Znajdź i Zamień po znalezieniu** dopasowania przy użyciu funkcji **szybkiego wyszukiwania** lub **szybkiego zamieniania**.|

## <a name="import-and-export-settings"></a>Import i eksport ustawień
 `DTE.Properties("Environment", "Import and Export Settings")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|TrackTeamSettings|Get/Set (wartość logiczna)|Używa ustawień w pliku określonym przez TeamSettingsFile.|
|TeamSettingsFile|Get/set (ciąg)|Nazwa pliku, który ma ustawienia zespołu.|
|AutoSaveFile|Get/set (ciąg)|Nazwa pliku, w którym są zapisywane automatycznie ustawienia użytkownika.|

## <a name="international-settings"></a>Ustawienia międzynarodowe
 `DTE.Properties("Environment", "International")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|Język|Get/set (ciąg)|Wartość identyfikatora LCID bieżącego języka dla programu Visual Studio.|

## <a name="keyboard"></a>Klawiatura
 `DTE.Properties("Environment", "Keyboard")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|Schemat|Get/set (ciąg)|Zwraca ciąg zawierający wbudowany schemat, ciąg zawierający pełną ścieżkę do pliku. VSK, który jest ładowany lub "(wartość domyślna)", jeśli nie załadowano pliku VSK.|

## <a name="projects-and-solution"></a>Projekty i rozwiązanie
 `DTE.Properties("Environment", "ProjectsAndSolution")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|OnRunOrPreview|Get/set (ciąg)|Określa, czy IDE zapisuje wszystko przed podglądem lub uruchomieniem skompilowanego projektu.|
|ProjectsLocation|Get/set (ciąg)|Określa domyślny katalog, w którym okno dialogowe **Dodaj projekt** zapisuje nowe projekty.|
|ShowOutputWindowBeforeBuild|Get/Set (wartość logiczna)|Określa, czy uruchomienie kompilacji powoduje wyświetlenie okna **danych wyjściowych** .|
|ShowTaskListAfterBuild|Get/Set (wartość logiczna)|Określa, czy niepowodzenie operacji kompilacji wyświetla **Lista zadań** po zakończeniu kompilacji.|
|TrackFileSelectionInExplorer|Get/Set (wartość logiczna)|Określa, czy bieżący element jest śledzony w **Eksplorator rozwiązań**.|
|AlwaysShowSolutionNode|Get/Set (wartość logiczna)|Określa, czy jest wyświetlany węzeł rozwiązania.|
|OnlySaveStartupProjectsAndDependencies|Get/Set (wartość logiczna)|Określa, czy operacje zapisu są ograniczone do projektów startowych i ich plików zależnych.|
|ShowAdvancedBuildConfigurations|Get/Set (wartość logiczna)|Określa, czy są wyświetlane zaawansowane konfiguracje kompilacji.|
|ConcurrentBuilds|Get/set (ciąg)|Określa maksymalną liczbę równoległych kompilacji projektów, które mogą wystąpić.|
|SaveNewProjects|Get/Set (wartość logiczna)|Określa, czy nowe projekty są automatycznie zapisywane po utworzeniu.|
|PromptForRenameSymbol|Get/Set (wartość logiczna)|Określa, czy ma być wyświetlany monit o zmianę nazwy symbolicznej w przypadku zmiany nazwy plików.|
|OnRunWhenErrors|Get/Set (Wyliczenie)|Określa zachowanie podczas uruchamiania, gdy kompilacja została ukończona z błędami.|
|OnRunWhenOutOfDate|Get/Set (Wyliczenie)|Określa zachowanie podczas uruchamiania, gdy projekt jest nieaktualny.|
|ProjectTemplatesLocation|Get/set (ciąg)|Katalog zawierający szablony projektu użytkownika.|
|ProjectItemTemplatesLocation|Get/set (ciąg)|Katalog zawierający szablony elementów użytkownika.|
|DefaultBehaviorForStartupProjects|Get/set (ciąg)||
|MSBuildOutputVerbosity|Get/set (ciąg)|Określa poziom szczegółowości danych wyjściowych kompilacji.|

## <a name="startup"></a>Folderze
 `DTE.Properties("Environment", "Startup")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|OnStart|Get/Set (Wyliczenie)|Akcja do podjęcia przy uruchamianiu, z <xref:EnvDTE.vsStartUp>, z wartościami 0 – 5:<br /><br /> -0: Otwórz stronę główną<br />-1: Załaduj ostatnio załadowane rozwiązanie<br />-2: Pokaż okno dialogowe **Otwieranie projektu**<br />-3: Pokaż **Nowy projekt** okno dialogowe<br />-4: Pokaż puste środowisko<br />-5: Pokaż stronę początkową|
|StartPageRSSUrl|Get/set (ciąg)|Adres URL źródła danych RSS, które jest używane podczas uruchamiania.|
|StartPageRefreshDownloadedContent|Get/Set (wartość logiczna)|Odświeża stronę początkową po każdym przejściu interwału określonego w StartPageRefreshInterval.|
|StartPageRefreshInterval|Pobierz/ustaw (krótki)|Interwał odświeżania strony początkowej (w minutach).|

## <a name="tasklist"></a>TaskList
 `DTE.Properties("Environment", "TaskList")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|ConfirmTaskDeletion|Get/Set (wartość logiczna)|Określa, czy pole potwierdzenia ma być wyświetlane podczas usuwania zadań z **Lista zadań**.|
|WarnOnAddingHiddenItem|Get/Set (wartość logiczna)|Określa, czy ma być wyświetlane ostrzeżenie podczas dodawania zadania użytkownika, które nie będzie wyświetlane.|
|DontShowFilePaths|Get/Set (wartość logiczna)|Określa, czy mają być pokazywane pełne ścieżki plików w Lista zadań.|
|CommentTokens|SafeArray|Zwraca element SafeArray wartości tokenów komentarzy. Każdy z nich zawiera pola, `Name` (ciąg) i `Priority` (<xref:EnvDTE.vsTaskPriority>, wysoki, średni lub niski).|

## <a name="web-browser"></a>Przeglądarka sieci Web
 `DTE.Properties("Environment", "WebBrowser")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|Głównej|Get/set (ciąg)|Reprezentuje adres URL strony głównej.|
|SearchPage|Get/set (ciąg)|Przedstawia adres URL strony wyszukiwania.|
|ViewSourceIn|Get/Set (Wyliczenie)|<xref:EnvDTE.vsBrowserViewSource> (Źródło, projekt, zewnętrzny).|
|ViewSourceExternalProgram|Get/set (ciąg)|Ścieżka zewnętrznej przeglądarki źródła.|

## <a name="see-also"></a>Zobacz też
 [Kontrolowanie ustawień opcji](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [określających nazwy elementów właściwości na](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) stronie Opcje strony opcji [, czcionki i kolory](../../ide/reference/options-page-fonts-and-colors-node-properties.md) [Strona Opcje właściwości węzła Edytor tekstu,](../../ide/reference/options-page-text-editor-node-properties.md) okno [dialogowe Opcje środowiska](../../ide/reference/environment-options-dialog-box.md)
