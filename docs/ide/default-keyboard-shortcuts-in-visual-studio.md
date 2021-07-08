---
title: Domyślne skróty klawiaturowe
description: Dowiedz się więcej o domyślnych skrótach klawiaturowych Visual Studio, które umożliwiają dostęp do różnych poleceń i okien.
ms.custom: SEO-VS-2020
ms.date: 06/21/2021
ms.topic: reference
helpviewer_keywords:
- shortcut keys [Visual Studio], keyboard binding schemes
- keyboard binding schemes [Visual Studio]
- Help [Visual Studio], shortcut keys
- keyboard shortcuts [Visual Studio], keyboard binding schemes
- keyboard shortcuts
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a63dbc1ad3ec544e52974a7ced9a69d4585ab629
ms.sourcegitcommit: b5744be07b7882e30bae67ef2810db56cf68344f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2021
ms.locfileid: "113487721"
---
# <a name="default-keyboard-shortcuts-in-visual-studio"></a>Domyślne skróty klawiaturowe w Visual Studio

Możesz uzyskać dostęp do różnych [poleceń](reference/visual-studio-commands.md) i okien w programie Visual Studio, wybierając odpowiedni skrót klawiaturowy. Ta strona zawiera listę domyślnych skrótów poleceń dla **profilu Ogólne,** które być może wybrano podczas instaluj Visual Studio. Niezależnie od wybranego profilu [](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) możesz zidentyfikować skrót do polecenia, otwierając okno dialogowe  Opcje, rozwijając węzeł Środowisko, a następnie wybierając pozycję **Klawiatura.**  Możesz również dostosować skróty, przypisując różne skróty do dowolnego polecenia.

Aby uzyskać listę typowych skrótów klawiaturowych i inne informacje o produktywności, zobacz:

- [Porady dotyczące klawiatury](../ide/productivity-shortcuts.md)
- [Wskazówki dotyczące produktywności](../ide/productivity-features.md).

Aby uzyskać więcej informacji na temat [](../ide/reference/accessibility-tips-and-tricks.md) ułatwień dostępu w Visual Studio, zobacz Porady i wskazówki dotyczące ułatwień dostępu oraz [Porady: używanie wyłącznie klawiatury](../ide/reference/how-to-use-the-keyboard-exclusively.md).

## <a name="most-popular-keyboard-shortcuts"></a>Popularne skróty klawiaturowe

Wszystkie skróty w tej sekcji są stosowane globalnie, chyba że określono inaczej. Kontekst *globalny* oznacza, że skrót ma zastosowanie w dowolnym oknie narzędzi w Visual Studio.

> [!NOTE]
> Skrót możesz [znaleźć w dowolnym](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) poleceniu, otwierając okno dialogowe Opcje, rozwijając węzeł **Środowisko,** a następnie wybierając pozycję **Klawiatura.** 


#### <a name="build-popular-shortcuts"></a>Kompilacja: popularne skróty

|Polecenia|Skróty klawiaturowe |Identyfikator polecenia|
|-|-|-|
|Tworzenie rozwiązania|**Ctrl+Shift+B** | Build.BuildSolution |
|Anuluj|**Ctrl+Break** | Build.Cancel |
|Skompilować|**Ctrl+F7** | Build.Compile |
|Uruchamianie analizy kodu w rozwiązaniu|**Alt+F11**| Build.RunCodeAnalysisonSolution |

#### <a name="debug-popular-shortcuts"></a>Debugowanie: popularne skróty

|Polecenia|Skróty klawiaturowe [Konteksty specjalne]|Identyfikator polecenia|
|-|-|-|
|Break at, funkcja|**Ctrl+B**| Debug.BreakatFunction |
|Przerwij wszystko|**Ctrl+Alt+Break**| Debug.BreakAll |
|Usuwanie wszystkich punktów przerwania|**Ctrl+Shift+F9**| Debug.DeleteAllBreakpoints |
|Wyjątki|**Ctrl+Alt+E**| Debug.Exceptions |
|Szybki zegarek|**Ctrl+Alt+Q**<br /><br />lub **Shift+F9**| Debug.QuickWatch |
|Uruchom ponownie|**Ctrl+Shift+F5**| Debug.Restart |
|Uruchom w celu kursora|**Ctrl+F10**| Debug.RunToCursor |
|Ustawianie następnej instrukcji|**Ctrl+Shift+F10**| Debug.SetNextStatement |
|Rozpocznij|**F5**| Debug.Start |
|Uruchamianie bez debugowania|**Ctrl+F5**| Debug.StartWithoutDebugging |
|Krok do kroku|**F11**| Debug.StepInto |
|Wyetapuj|**Shift+ F11**| Debug.StepOut |
|Krok po kroku|**F10**| Debug.StepOver |
|Zatrzymywanie debugowania|**Shift+ F5**| Debug.StopDebugging |
|Przełącz punkt przerwania|**F9**| Debug.ToggleBreakpoint |

#### <a name="edit-popular-shortcuts"></a>Edytuj: popularne skróty

|Polecenia|Skróty klawiaturowe [Konteksty specjalne]|Identyfikator polecenia|
|-|-|-|
|Wiersz przerwania|**Wprowadź** tekst [Edytor tekstu, Projektant raportów, Windows Forms Designer]<br /><br />lub **Shift+Enter** [Edytor tekstu]| Edit.BreakLine |
|Zwijanie do definicji|**Ctrl+M,** **Ctrl+O** [Edytor tekstu]| Edit.CollapseToDefinitions |
|Wybór komentarza|**Ctrl+K,** **Ctrl+C** [Edytor tekstu]| Edit.CommentSelection |
|Wyraz ukończony|**Alt+Strzałka w prawo** [Edytor tekstu, Projektant przepływu pracy]<br /><br />lub **Ctrl+spacja** [Edytor tekstu, Projektant przepływu pracy]<br /><br />lub **Ctrl+K,** **W** [Projektant przepływu pracy]<br /><br />lub **Ctrl+K, Ctrl+W** [Projektant przepływu pracy]| Edit.CompleteWord |
|Kopiuj|**Ctrl+C**<br /><br />lub **Ctrl+Insert**| Edit.Copy |
|Wytnij|**Ctrl+X**<br /><br />lub **Shift +Delete**| Edit.Cut |
|Usuń|**Usuń** [Team Explorer]<br /><br />lub **Shift+Delete** [Diagram sekwencji, Diagram aktywności UML, Diagram warstwowy]<br /><br />lub **Ctrl+Delete** [Diagram klas]| Edit.Delete |
|Znajdowanie|**Ctrl+F**| Edit.Find |
|Znajdowanie wszystkich odwołań|**Shift+F12**| Edit.FindAllReferences |
|Znajdź w plikach|**Ctrl+Shift+F**| Edit.FindinFiles |
|Znajdź dalej|**F3**| Edit.FindNext |
|Znajdź następne wybrane|**Ctrl+F3**| Edit.FindNextSelected |
|Formatowanie dokumentu|**Ctrl+K, Ctrl+D** [Edytor tekstu]| Edit.FormatDocument |
|Formatowanie zaznaczenia|**Ctrl+K, Ctrl+F** [Edytor tekstu]| Edit.FormatSelection |
|Przejdź do|**Ctrl+G**| Edit.GoTo |
|Przejdź do deklaracji|**Ctrl+F12**| Edit.GoToDeclaration |
|Przejdź do definicji|**F12**| Edit.GoToDefinition |
|Przejdź do znalezienia kombi|**Ctrl + D**| Edit.GoToFindCombo |
|Przejdź do następnej lokalizacji|**F8**| Edit.GoToNextLocation |
|Wstaw fragment kodu|**Ctrl+K,** **Ctrl+X**| Edit.InsertSnippet |
|Karta Wstawianie|**Tab** [Projektant raportów, Windows Forms Designer, Edytor tekstu]| Edit.InsertTab |
|Obcięcie wiersza|**Ctrl+L** [Edytor tekstu]| Edit.LineCut |
|Rozszerzanie kolumny w dół|**Shift+Alt+Strzałka w dół** [Edytor tekstu]| Edit.LineDownExtendColumn |
|Wiersz otwarty powyżej|**Ctrl+Enter** [Edytor tekstu]| Edit.LineOpenAbove |
|Lista elementów członkowskich|**Ctrl+J** [Edytor tekstu, Projektant przepływu pracy]<br /><br />lub **Ctrl+K, Ctrl+L** [Projektant przepływu pracy]<br /><br />lub **Ctrl+K, L** [Projektant przepływu pracy]| Edit.ListMembers |
|Przejdź do strony |**Ctrl+,**| Edit.NavigateTo |
|Otwieranie pliku|**Ctrl+Shift+G**| Edit.OpenFile |
|Tryb zastępowania|**Wstaw** [Edytor tekstu]| Edit.OvertypeMode |
|Informacje o parametrach|**Ctrl+Shift+Spacja** [Edytor tekstu, Projektant przepływu pracy]<br /><br />lub **Ctrl+K, Ctrl+P** [Projektant przepływu pracy]<br /><br />lub **Ctrl+K, P** [Projektant przepływu pracy]| Edit.ParameterInfo |
|Wklej|**Ctrl+V**<br /><br />lub **Shift+Insert**| Edit.Paste |
|Wgląd w definicję|**Alt+F12** [Edytor tekstu]| Edit.PeekDefinition |
|Ponów|**Ctrl+Y**<br /><br />lub **Shift+Alt+Backspace**<br /><br />lub **Ctrl+Shift+Z**| Edit.Redo |
|Zamień|**Ctrl+H**| Edit.Replace |
|Zaznacz wszystko|**Ctrl+A**| Edit.SelectAll |
|Wybieranie bieżącego wyrazu|**Ctrl+W** [Edytor tekstu]| Edit.SelectCurrentWord |
|Anulowanie wyboru|**Esc** [Edytor tekstu, Projektant raportów, Ustawienia Designer, Windows Forms Designer, Edytor zasobów zarządzanych]| Edit.SelectionCancel |
|Otoczyć za pomocą|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Tabulator po lewej stronie|**Shift+Tab** [Edytor tekstu, Projektant raportów, Windows Forms]| Edit.TabLeft |
|Przełącz wszystkie podsuwu|**Ctrl+M, Ctrl+L** [Edytor tekstu]| Edit.ToggleAllOutlining |
|Przełącz zakładkę|**Ctrl+K, Ctrl+K** [Edytor tekstu]| Edit.ToggleBookmark |
|Przełącz tryb uzupełniania|**Ctrl+Alt+Spacja** [Edytor tekstu]| Edit.ToggleCompletionMode |
|Przełączanie rozszerzania w celu rozwinięcia|**Ctrl+M, Ctrl+M** [Edytor tekstu]| Edit.ToggleOutliningExpansion |
|Zaznaczenie opcji Cokmentuj|**Ctrl+K, Ctrl+U** [Edytor tekstu]| Edit.UncommentSelection |
|Cofnij|**Ctrl+Z**<br /><br />lub **Alt + Backspace**| Edit.Undo |
|Usuwanie wyrazów do końca|**Ctrl+Delete** [Edytor tekstu]| Edit.WordDeleteToEnd |
|Usuwanie programu Word do uruchomienia|**Ctrl+Backspace** [Edytor tekstu]| Edit.WordDeleteToStart |

#### <a name="file-popular-shortcuts"></a>Plik: popularne skróty

|Polecenia|Skróty klawiaturowe [Konteksty specjalne]|Identyfikator polecenia|
|-|-|-|
|Zakończ|**Alt+F4**| File.Exit |
|Nowy plik|**Ctrl+N**| File.NewFile |
|Nowy projekt|**Ctrl+Shift+N**| File.NewProject |
|Nowa witryna internetowa|**Shift+Alt+N**| File.NewWebSite |
|Otwieranie pliku|**Ctrl+O**| File.OpenFile |
|Otwieranie projektu|**Ctrl+Shift+O**| File.OpenProject |
|Otwieranie witryny internetowej|**Shift+Alt+O**| File.OpenWebSite |
|Zmień nazwę|**F2** [Team Explorer]| File.Rename |
|Zapisz wszystko|**Ctrl+Shift+S**| File.SaveAll |
|Zapisywanie wybranych elementów|**Ctrl+S**| File.SaveSelectedItems |
|Wyświetlanie w przeglądarce|**Ctrl+Shift+W**| File.ViewinBrowser |

#### <a name="project-popular-shortcuts"></a>Project: popularne skróty

|Polecenia|Skróty klawiaturowe [Konteksty specjalne]|Identyfikator polecenia|
|-|-|-|
|Dodawanie istniejącego elementu|**Shift+Alt+A**| Project.AddExistingItem |
|Dodawanie nowego elementu|**Ctrl+Shift+A**| Project.AddNewItem |

#### <a name="refactor-popular-shortcuts"></a>Refaktoryzacja: popularne skróty

|Polecenie|Skrót klawiaturowy [Konteksty specjalne]|Identyfikator polecenia|
|-|-|-|
|Wyodrębnianie metody|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |

#### <a name="tools-popular-shortcuts"></a>Narzędzia: popularne skróty

|Polecenie|Skrót klawiaturowy [Konteksty specjalne]|Identyfikator polecenia|
|-|-|-|
|Dołączanie do procesu|**Ctrl+Alt+P**| Tools.AttachtoProcess |

#### <a name="view-popular-shortcuts"></a>Widok: popularne skróty

|Polecenia|Skróty klawiaturowe [Konteksty specjalne]|Identyfikator polecenia|
|-|-|-|
|Widok klasy|**Ctrl+Shift+C**| View.ClassView |
|Edytuj etykietę|**F2**| View.EditLabel |
|Lista błędów|**Ctrl+, \\ Ctrl+E**<br /><br />lub **Ctrl+, \\ E**| View.ErrorList |
|Przechodzenie do tyłu|**Ctrl+-**| View.NavigateBackward |
|Poruszanie się do przodu|**Ctrl+Shift+-**| View.NavigateForward |
|Przeglądarka obiektów|**Ctrl+Alt+J**| View.ObjectBrowser |
|Dane wyjściowe|**Ctrl+Alt+O**| View.Output |
|Okno właściwości|**F4**| View.PropertiesWindow |
|Odśwież|**F5** [Team Explorer]| View.Refresh |
|Eksplorator serwera|**Ctrl+Alt+S**| View.ServerExplorer |
|Pokazywanie tagu inteligentnego|**Ctrl+.**<br /><br />lub **Shift+Alt+F10** [Widok projektu edytora HTML]| View.ShowSmartTag |
|Eksplorator rozwiązań|**Ctrl+Alt+L**| View.SolutionExplorer |
|TFS Team Explorer|**Ctrl+, \\ Ctrl+M**| View.TfsTeamExplorer |
|Przybornik|**Ctrl+Alt+X**| View.Toolbox |
|Wyświetlanie kodu|**Wprowadź** [Diagram klas]<br /><br />lub **F7** [Ustawienia Designer]| View.ViewCode |
|Projektant widoków|**Shift+F7** [Widok źródła edytora HTML]| View.ViewDesigner |

#### <a name="window-popular-shortcuts"></a>Okno: popularne skróty

|Polecenia|Skróty klawiaturowe [Konteksty specjalne]|Identyfikator polecenia|
|-|-|-|
|Okno aktywowania dokumentu|**Esc**| Window.ActivateDocumentWindow |
|Zamykanie okna dokumentu|**Ctrl+F4**| Window.CloseDocumentWindow |
|Okno Następnego dokumentu|**Ctrl+F6**| Window.NextDocumentWindow |
|Okno następnego dokumentu nav|**Ctrl+Tab**| Window.NextDocumentWindowNav |
|Następne okienko podziału|**F6**| Window.NextSplitPane |


## <a name="global-shortcuts"></a>Skróty globalne

Te skróty klawiaturowe *są globalne,* co oznacza, że można ich używać, gdy dowolne Visual Studio okno ma fokus.

- [Analiza](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze)
- [Edytuj](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit)
- [Project](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project)
- [Test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test)
- [Architektura](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture)
- [Menu kontekstowe edytora](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext)
- [Project kontekstowe i menu kontekstowe rozwiązania](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext)
- [Eksplorator testów](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)
- [Kompilacja](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build)
- [Plik](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file)
- [Refaktoryzacja](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor)
- [Narzędzia](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools)
- [Widok klasy menu kontekstowych](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview)
- [Pomoc](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help)
- [Eksplorator rozwiązań](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)
- [Wyświetlanie](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view)
- [Debugowanie](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug)
- [Test obciążeniowy](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest)
- [Zespół](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team)
- [Okno](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window)
- [Menu kontekstowe debugera](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger)
- [Inne menu kontekstowe](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext)
- [Menu kontekstowe team foundation](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext)
- [Azure](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windowsazure)
- [Centrum diagnostyki](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diagnostics)

### <a name="analyze"></a><a name="bkmk_analyze"></a> Analizować

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Przechodzenie do tyłu|**Shift+Alt+3**| Analyze.NavigateBackward |
|Przechodzenie do przodu|**Shift+Alt+4**| Analyze.NavigateForward |

### <a name="architecture"></a><a name="bkmk_architecture"></a> Architektura

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Nowy diagram|**Ctrl+, \\ Ctrl+N**| Architecture.NewDiagram |

### <a name="build"></a><a name="bkmk_build"></a> Budować

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Wybór kompilacji|**Ctrl+B** (Visual Studio 2019)| Build.BuildSelection |
|Tworzenie rozwiązania|**Ctrl+Shift+B**| Build.BuildSolution |
|Anuluj|**Ctrl+Break**| Build.Cancel |
|Skompilować|**Ctrl+F7**| Build.Compile |
|Uruchamianie analizy kodu w rozwiązaniu|**Alt+F11**| Build.RunCodeAnalysisonSolution |

### <a name="class-view-context-menus"></a><a name="bkmk_classview"></a> Widok klasy menu kontekstowych

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Właściwości|**Alt+Enter**| ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties |

### <a name="debug"></a><a name="bkmk_debug"></a> Debugowania

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Stosowanie zmian kodu|**Alt+F10**| Debug.ApplyCodeChanges |
|Dołączanie do procesu|**Ctrl+Alt+P**| Debug.AttachtoProcess |
|Autos|**Ctrl+Alt+V, A**| Debug.Autos |
|Przerwij wszystko|**Ctrl+Alt+Break**| Debug.BreakAll |
|Punkty przerwania|**Ctrl+Alt+B**| Debug.Breakpoints |
|Stos wywołań|**Ctrl+Alt+C**| Debug.CallStack |
|Usuwanie wszystkich punktów przerwania|**Ctrl+Shift+F9**| Debug.DeleteAllBreakpoints |
|Uruchom|**Alt+F2**| Debug.DiagnosticsHub.Launch |
|Demontażu|**Ctrl+Alt+D**| Debug.Disassembly |
|Eksplorator dom|**Ctrl+Alt+V, D**| Debug.DOMExplorer |
|Włączanie punktu przerwania|**Ctrl+F9**| Debug.EnableBreakpoint |
|Wyjątki|**Ctrl+Alt+E**| Debug.Exceptions |
|Punkt przerwania funkcji|**Ctrl+K, B** (Visual Studio 2019)<br />**Ctrl** + **B** (Visual Studio 2017)| Debug.FunctionBreakpoint |
|Przejdź do poprzedniego wywołania lub zdarzenia IntelliTrace|**Ctrl+Shift+F11**| Debug.GoToPreviousCallorIntelliTraceEvent |
|Rozpoczynanie diagnostyki|**Alt+F5**| Debug.Graphics.StartDiagnostics |
|Natychmiastowe|**Ctrl+Alt+I**| Debug.Immediate |
|Wywołania IntelliTrace|**Ctrl+Alt+Y, T**| Debug.IntelliTraceCalls |
|Zdarzenia IntelliTrace|**Ctrl+Alt+Y, F**| Debug.IntelliTraceEvents |
|Konsola języka JavaScript|**Ctrl+Alt+V, C**| Debug.JavaScriptConsole |
|Mieszkańców|**Ctrl+Alt+V, L**| Debug.Locals |
|Przetwarzanie kombi|**Ctrl+5**| Debug.LocationToolbar.ProcessCombo |
|Kombi ramek stosu|**Ctrl+7**| Debug.LocationToolbar.StackFrameCombo |
|Kombi wątków|**Ctrl+6**| Debug.LocationToolbar.ThreadCombo |
|Przełącz bieżący wątek oflagowany stan|**Ctrl+8**| Debug.LocationToolbar.ToggleCurrentThreadFlaggedState |
|Przełączanie oflagowanych wątków|**Ctrl+9**| Debug.LocationToolbar.ToggleFlaggedThreads |
|Pamięć 1|**Ctrl+Alt+M, 1**| Debug.Memory1 |
|Pamięć 2|**Ctrl+Alt+M, 2**| Debug.Memory2 |
|Pamięć 3|**Ctrl+Alt+M, 3**| Debug.Memory3 |
|Pamięć 4|**Ctrl+Alt+M, 4**| Debug.Memory4 |
|Moduły|**Ctrl+Alt+U**| Debug.Modules |
|Stosy równoległe|**Ctrl+Shift+D, S**| Debug.ParallelStacks |
|Równoległy zegarek 1|**Ctrl+Shift+D, 1**| Debug.ParallelWatch1 |
|Równoległy zegarek 2|**Ctrl+Shift+D, 2**| Debug.ParallelWatch2 |
|Równoległy zegarek 3|**Ctrl+Shift+D, 3**| Debug.ParallelWatch3 |
|Równoległy zegarek 4|**Ctrl+Shift+D, 4**| Debug.ParallelWatch4 |
|Procesy|**Ctrl+Alt+Z**| Debug.Processes |
|Szybki zegarek|**Shift+F9** lub **Ctrl+Alt+Q**| Debug.QuickWatch |
|Ponowne dołączanie do procesu|**Shift+Alt+P**| Debug.ReattachtoProcess |
|Odświeżanie aplikacji windowsapp|**Ctrl+Shift+R**| Debug.RefreshWindowsapp |
|Rejestrów|**Ctrl+Alt+G**| Debug.Registers |
|Uruchom ponownie|**Ctrl+Shift+F5**| Debug.Restart |
|Uruchom w celu kursora|**Ctrl+F10**| Debug.RunToCursor |
|Ustawianie następnej instrukcji|**Ctrl+Shift+F10**| Debug.SetNextStatement |
|Pokazywanie stosu wywołań na mapie kodu|**Ctrl+Shift+'**| Debug.ShowCallStackonCodeMap |
|Pokaż następną instrukcje|**Alt + Num** *| Debug.ShowNextStatement |
|Rozpocznij|**F5**| Debug.Start |
|Uruchamianie analizy aplikacji systemu Windows Phone|**Alt+F1**| Debug.StartWindowsPhoneApplicationAnalysis |
|Uruchamianie bez debugowania|**Ctrl+F5**| Debug.StartWithoutDebugging |
|Krok do kroku|**F11**| Debug.StepInto |
|Krok do bieżącego procesu|**Ctrl+Alt+F11**| Debug.StepIntoCurrentProcess |
|Krok po kroku do określonych|**Shift+Alt+F11**| Debug.StepIntoSpecific |
|Wyetapuj|**Shift + F11**| Debug.StepOut |
|Wyetapuj bieżący proces|**Ctrl+Shift+Alt+F11**| Debug.StepOutCurrentProcess |
|Krok po kroku|**F10** (Podczas debugowania: wykonuje krok nad akcją)| Debug.StepOver |
|Krok po kroku|**F10 (Jeśli** nie debugowanie: rozpoczyna debugowanie i zatrzymuje się w pierwszym wierszu kodu użytkownika)| Debug.StepOver |
|Przekłoń bieżący proces|**Ctrl+Alt+F10**| Debug.StepOverCurrentProcess |
|Zatrzymywanie debugowania|**Shift+F5**| Debug.StopDebugging |
|Zatrzymywanie analizy wydajności|**Shift+Alt+F2**| Debug.StopPerformanceAnalysis |
|Zadania|**Ctrl+Shift+D, K**| Debug.Tasks |
|Wątki|**Ctrl+Alt+H**| Debug.Threads |
|Przełącz punkt przerwania|**F9**| Debug.ToggleBreakpoint |
|Przełącz dekompełt|**Ctrl+F11**| Debug.ToggleDisassembly |
|Obejrzyj 1|**Ctrl+Alt+W, 1**| Debug.Watch1 |
|Obejrzyj 2|**Ctrl+Alt+W, 2**| Debug.Watch2 |
|Obejrzyj 3|**Ctrl+Alt+W, 3**| Debug.Watch3 |
|Obejrzyj 4|**Ctrl+Alt+W, 4**| Debug.Watch4 |

### <a name="debugger-context-menus"></a><a name="bkmk_debugger"></a> Menu kontekstowe debugera

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Usuń|**Alt+F9, D**| DebuggerContextMenus.BreakpointsWindow.Delete |
|Przejdź do dekompasu|**Alt+F9, A**| DebuggerContextMenus.BreakpointsWindow.GoToDisassembly |
|Przejdź do kodu źródłowego|**Alt+F9, S**| DebuggerContextMenus.BreakpointsWindow.GoToSourceCode |

### <a name="diagnostics-hub"></a><a name="bkmk_diagnostics"></a> Centrum diagnostyki

|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Zatrzymywanie zbierania|**Ctrl+Alt+F2**| DiagnosticsHub.StopCollection |

### <a name="edit"></a><a name="bkmk_edit"></a> Edytuj

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Kopiuj|**Ctrl+C**<br /><br /> lub<br /><br /> **Ctrl+Ins**| Edit.Copy |
|Wytnij|**Ctrl+X**<br /><br /> lub<br /><br /> **Shift+Delete**| Edit.Cut |
|Cykliczny pierścień schowka|**Ctrl+Shift+V**<br /><br /> lub<br /><br /> **Ctrl+Shift+Ins**| Edit.CycleClipboardRing |
|Usuń|**Usuwanie**| Edit.Delete |
|Duplikuj|**Ctrl + D**| Edit.Duplicate |
|Znajdowanie|**Ctrl+F**| Edit.Find |
|Znajdowanie wszystkich odwołań|**Shift+F12**| Edit.FindAllReferences |
|Znajdź w plikach|**Ctrl+Shift+F**| Edit.FindinFiles |
|Znajdź dalej|**F3**| Edit.FindNext |
|Znajdź następny wybrany|**Ctrl+F3**| Edit.FindNextSelected |
|Znajdź poprzednią|**Shift + F3**| Edit.FindPrevious |
|Znajdź poprzednią wybraną|**Ctrl+Shift+F3**| Edit.FindPreviousSelected |
|Generowanie metody|**Ctrl+K, Ctrl+M**| Edit.GenerateMethod |
|Przejdź do|**Ctrl+G**| Edit.GoTo |
|Przejdź do wszystkich|**Ctrl+,** lub **Ctrl+T**| Edit.GoToAll |
|Przejdź do deklaracji|**Ctrl+F12**| Edit.GoToDeclaration |
|Przejdź do definicji|**F12**| Edit.GoToDefinition |
|Przejdź do członka|**Ctrl+1, Ctrl+M** lub **Ctrl+1, M** lub **Alt+ \\**| Edit.GoToMember |
|Przejdź do następnej lokalizacji|**F8** (Następny błąd w oknie Lista błędów lub Dane wyjściowe)| Edit.GoToNextLocation |
|Przejdź do lokalizacji wstępnej|**Shift+F8** (poprzedni błąd w oknie Lista błędów lub Dane wyjściowe)| Edit.GoToPrevLocation |
|Wstaw fragment kodu|**Ctrl+K, Ctrl+X**| Edit.InsertSnippet |
|Przenoszenie kontrolki w dół|**Ctrl+strzałka w dół**| Edit.MoveControlDown |
|Przenoszenie kontrolki w dół siatki|**Strzałka w dół**| Edit.MoveControlDownGrid |
|Przenoszenie kontrolki w lewo|**Ctrl+Strzałka w lewo**| Edit.MoveControlLeft |
|Przenoszenie kontrolki do lewej siatki|**Strzałka w lewo**| Edit.MoveControlLeftGrid |
|Przenoszenie kontrolki w prawo|**Ctrl+Strzałka w prawo**| Edit.MoveControlRight |
|Przenoszenie kontrolki w prawo siatki|**Strzałka w prawo**| Edit.MoveControlRightGrid |
|Przenieś kontrolę w górę|**Ctrl+Strzałka w górę**| Edit.MoveControlUp |
|Przenoszenie kontrolki w górę siatki|**Strzałka w górę**| Edit.MoveControlUpGrid |
|Następna zakładka|**Ctrl+K, Ctrl+N**| Edit.NextBookmark |
|Następna zakładka w folderze|**Ctrl+Shift+K, Ctrl+Shift+N**| Edit.NextBookmarkInFolder |
|Otwieranie pliku|**Ctrl+Shift+G** (otwiera nazwę pliku pod kursorem)| Edit.OpenFile |
|Wklej|**Ctrl+V**<br /><br /> lub<br /><br /> **Shift+Ins**| Edit.Paste |
|Poprzednia zakładka|**Ctrl+K, Ctrl+P**| Edit.PreviousBookmark |
|Poprzednia zakładka w folderze|**Ctrl+Shift+K, Ctrl+Shift+P**| Edit.PreviousBookmarkInFolder |
|Symbol szybkiego znalezienia|**Shift+Alt+F12**| Edit.QuickFindSymbol |
|Ponów|**Ctrl+Y**<br /><br /> lub<br /><br /> **Ctrl+Shift+Z**<br /><br /> lub<br /><br /> **Shift+Alt+Backspace**| Edit.Redo |
|Odświeżanie odwołań zdalnych|**Ctrl+Shift+J**| Edit.RefreshRemoteReferences |
|Zamień|**Ctrl+H**| Edit.Replace |
|Zastąp w plikach|**Ctrl+Shift+H**| Edit.ReplaceinFiles |
|Zaznacz wszystko|**Ctrl+A**| Edit.SelectAll |
|Wybieranie następnej kontrolki|**Tab**| Edit.SelectNextControl |
|Wybieranie poprzedniej kontrolki|**Shift+Tab**| Edit.SelectPreviousControl |
|Pokazywanie siatki kafelków|**Enter**| Edit.ShowTileGrid |
|Kontrola rozmiaru w dół|**Ctrl+Shift+Strzałka w dół**| Edit.SizeControlDown |
|Kontrolka rozmiaru w dół siatki|**Shift+Strzałka w dół**| Edit.SizeControlDownGrid |
|Kontrolka rozmiaru w lewo|**Ctrl+Shift+Strzałka w lewo**| Edit.SizeControlLeft |
|Kontrolka rozmiaru w lewej siatce|**Shift+Strzałka w lewo**| Edit.SizeControlLeftGrid |
|Prawa kontrolka rozmiaru|**Ctrl+Shift+Strzałka w prawo**| Edit.SizeControlRight |
|Prawa siatka kontroli rozmiaru|**Shift+Strzałka w prawo**| Edit.SizeControlRightGrid |
|Kontrola rozmiaru|**Ctrl+Shift+Strzałka w górę**| Edit.SizeControlUp |
|Kontrola rozmiaru w górę siatki|**Shift+Strzałka w górę**| Edit.SizeControlUpGrid |
|Zatrzymywanie wyszukiwania|**Alt+F3, S**| Edit.StopSearch |
|Otoczyć za pomocą|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Cofnij|**Ctrl+Z**<br /><br /> lub<br /><br /> **Alt+Backspace**| Edit.Undo |

### <a name="editor-context-menus"></a><a name="bkmk_editorContext"></a> Menu kontekstowe edytora

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Warunki punktu przerwania|**Alt+F9, C**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointConditions |
|Etykiety edycji punktu przerwania|**Alt+F9, L**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels |
|Pokaż element|**Ctrl+'**| EditorContextMenus.CodeWindow.CodeMap.ShowItem |
|Wykonaj polecenie|**Ctrl+Alt+F5**| EditorContextMenus.CodeWindow.Execute |
|Przejdź do widoku|**Ctrl+M, Ctrl+G**| EditorContextMenus.CodeWindow.GoToView |
|Przełącz plik kodu nagłówka|**Ctrl+K, Ctrl+O** (litera 'O')| EditorContextMenus.CodeWindow.ToggleHeaderCodeFile |
|Wyświetlanie hierarchii wywołań|**Ctrl+K, Ctrl+T**<br /><br /> lub<br /><br /> **Ctrl+K, T**| EditorContextMenus.CodeWindow.ViewCallHierarchy |

### <a name="file"></a><a name="bkmk_file"></a> Plik

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Zakończ|**Alt+F4**| File.Exit |
|Nowy plik|**Ctrl+N**| File.NewFile |
|Nowy projekt|**Ctrl+Shift+N**| File.NewProject |
|Nowa witryna internetowa|**Shift+Alt+N**| File.NewWebSite |
|Otwieranie pliku|**Ctrl+O** (litera 'O')| File.OpenFile |
|Otwieranie projektu|**Ctrl+Shift+O** (litera 'O')| File.OpenProject |
|Otwieranie witryny internetowej|**Shift+Alt+O** (litera 'O')| File.OpenWebSite |
|Drukuj|**Ctrl+P**| File.Print |
|Zapisz wszystko|**Ctrl+Shift+S**| File.SaveAll |
|Zapisywanie wybranych elementów|**Ctrl+S**| File.SaveSelectedItems |
|Wyświetlanie w przeglądarce|**Ctrl+Shift+W**| File.ViewinBrowser |

### <a name="help"></a><a name="bkmk_help"></a> Pomoc

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Dodawanie i usuwanie zawartości pomocy|**Ctrl+Alt+F1**| Help.AddandRemoveHelpContent |
|Pomoc F1|**F1**| Help.F1Help |
|Wyświetlanie pomocy|**Ctrl+F1**| Help.ViewHelp |
|Pomoc okna|**Shift+F1**| Help.WindowHelp |

### <a name="load-test"></a><a name="bkmk_loadtest"></a> Test obciążeniowy

|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Przejście do okienka licznika|**Ctrl+R, Q**| LoadTest.JumpToCounterPane |

### <a name="other-context-menus"></a><a name="bkmk_otherContext"></a> Inne menu kontekstowe

|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Dodawanie nowego diagramu|**Insert**| OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram |

### <a name="project"></a><a name="bkmk_project"></a> Projekt

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Dodawanie istniejącego elementu|**Shift+Alt+A**| Project.AddExistingItem |
|Dodawanie nowego elementu|**Ctrl+Shift+A**| Project.AddNewItem |
|Kreator klas|**Ctrl+Shift+X**| Project.ClassWizard |
|Zastąpienie|**Ctrl+Alt+Ins**| Project.Override |
|Podgląd zmian|**Alt+;** następnie **Alt + C**| Project.Previewchanges |
|Publikowanie wybranych plików|**Alt+;** następnie **Alt + P**| Project.Publishselectedfiles |
|Zastępowanie wybranych plików z serwera|**Alt+;** , **a następnie Alt+R**| Project.Replaceselectedfilesfromserver |

### <a name="project-and-solution-context-menus"></a><a name="bkmk_projectContext"></a>Project i menu kontekstowe rozwiązania

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Przechodzenie w dół|**Alt+Strzałka w dół**| ProjectandSolutionContextMenus.Item.MoveDown |
|Przenieś w górę|**Alt+Strzałka w górę**| ProjectandSolutionContextMenus.Item.MoveUp |

### <a name="refactor"></a><a name="bkmk_refactor"></a> Refactor

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Hermetyzowanie pola|**Ctrl+R, Ctrl+E**| Refactor.EncapsulateField |
|Wyodrębnianie interfejsu|**Ctrl+R, Ctrl+I**| Refactor.ExtractInterface |
|Wyodrębnianie metody|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |
|Usuwanie parametrów|**Ctrl+R, Ctrl+V**| Refactor.RemoveParameters |
|Zmień nazwę|**Ctrl+R, Ctrl+R**| Refactor.Rename |
|Zmiana kolejności parametrów|**Ctrl+R, Ctrl+O** (litera 'O')| Refactor.ReorderParameters |

### <a name="solution-explorer"></a><a name="bkmk_solutionexplorerGLOBAL"></a> Eksplorator rozwiązań

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Otwieranie filtru plików|**Ctrl+[**, **O** (litera 'O')<br /><br /> lub<br /><br /> **Ctrl+[**, **Ctrl+O** (litera 'O')| SolutionExplorer.OpenFilesFilter |
|Filtr Oczekujące zmiany|**Ctrl+[**, **P**<br /><br /> lub<br /><br /> **Ctrl+[**, **Ctrl+P**| SolutionExplorer.PendingChangesFilter |
|Synchronizowanie z aktywnym dokumentem|**Ctrl+[**, **S**<br /><br /> lub<br /><br /> **Ctrl+[**, **Ctrl+S**| SolutionExplorer.SyncWithActiveDocument |

### <a name="team"></a><a name="bkmk_team"></a> Zespołu

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Przejdź do gałęzi git|**Ctrl+0** (zero), **Ctrl+N**<br /><br /> lub<br /><br /> **Ctrl+0, N**| Team.Git.GoToGitBranches |
|Przejdź do zmian w usłudze Git|**Ctrl+0** (zero), **Ctrl+G**<br /><br /> lub<br /><br /> **Ctrl+0, G**| Team.Git.GoToGitChanges |
|Przejdź do zatwierdzeń usługi Git|**Ctrl+0** (zero), **Ctrl+O** (litera 'O')<br /><br /> lub<br /><br /> **Ctrl+0, O**| Team.Git.GoToGitCommits |
|Wyszukiwanie w programie Team Explorer|**Ctrl+'**| Team.TeamExplorerSearch |

### <a name="team-foundation-context-menus"></a><a name="bkmk_TFcontext"></a> Menu kontekstowe team Foundation

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Przejdź do kompilacji|**Ctrl+0** (zero), **Ctrl+B**<br /><br /> lub<br /><br /> **Ctrl+0, B**| TeamFoundationContextMenus.Commands.GoToBuilds |
|Przejdź do połączenia|**Ctrl+0** (zero), **Ctrl+C**<br /><br /> lub<br /><br /> **Ctrl+0, C**| TeamFoundationContextMenus.Commands.GoToConnect |
|Przejdź do dokumentów|**Ctrl+0** (zero), **Ctrl+D**<br /><br /> lub<br /><br /> **Ctrl+0, D**| TeamFoundationContextMenus.Commands.GoToDocuments |
|Przejdź do strony głównej|**Ctrl+0** (zero), **Ctrl+H**<br /><br /> lub<br /><br /> **Ctrl+0, H**| TeamFoundationContextMenus.Commands.GoToHome |
|Przejdź do mojej pracy|**Ctrl+0** (zero), **Ctrl+M**<br /><br /> lub<br /><br /> **Ctrl+0, M**| TeamFoundationContextMenus.Commands.GoToMyWork |
|Przejdź do oczekujących zmian|**Ctrl+0** (zero), **Ctrl+P**<br /><br /> lub<br /><br /> **Ctrl+0, P**| TeamFoundationContextMenus.Commands.GoToPendingChanges |
|Przejdź do raportów|**Ctrl+0** (zero), **Ctrl+R**<br /><br /> lub<br /><br /> **Ctrl+0, R**| TeamFoundationContextMenus.Commands.GoToReports |
|Przejdź do ustawień|**Ctrl+0** (zero), **Ctrl+S**<br /><br /> lub<br /><br /> **Ctrl+0, S**| TeamFoundationContextMenus.Commands.GoToSettings |
|Przejdź do dostępu do Internetu|**Ctrl+0** (zero), **Ctrl+A**<br /><br /> lub<br /><br /> **Ctrl+0, A**| TeamFoundationContextMenus.Commands.GoToWebAccess |
|Przejdź do elementów roboczych|**Ctrl+0** (zero), **Ctrl+W**<br /><br /> lub<br /><br /> **Ctrl+0, W**| TeamFoundationContextMenus.Commands.GoToWorkItems |

### <a name="test"></a><a name="bkmk_test"></a> Test

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Korzystanie z konstruktora kodowany testów interfejsu użytkownika|**Ctrl+, \\ Ctrl+C**| Test.UseCodedUITestBuilder |
|Używanie istniejącego rejestrowania akcji|**Ctrl+, \\ Ctrl+A**| Test.UseExistingActionRecording |

### <a name="test-explorer"></a><a name="bkmk_testexplorerGLOBAL"></a> Eksplorator testów

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Debugowanie wszystkich testów|**Ctrl+R, Ctrl+A**| TestExplorer.DebugAllTests |
|Debugowanie wszystkich testów w kontekście|**Ctrl+R, Ctrl+T**| TestExplorer.DebugAllTestsInContext |
|Debugowanie ostatniego uruchomienia|**Ctrl+R, D**| TestExplorer.DebugLastRun |
|Powtórz ostatnie uruchomienie|**Ctrl+R, L**| TestExplorer.RepeatLastRun |
|Uruchamianie wszystkich testów|**Ctrl+R, A**| TestExplorer.RunAllTests |
|Uruchamianie wszystkich testów w kontekście|**Ctrl+R, T**| TestExplorer.RunAllTestsInContext |
|Pokazywanie eksploratora testów|**Ctrl+E, T**| TestExplorer.ShowTestExplorer |
|Otwieranie karty|**Ctrl+E, L**| LiveUnitTesting.OpenTab |
|Wyniki pokrycia kodu|**Ctrl+E, C**| Test.CodeCoverageResults |

### <a name="tools"></a><a name="bkmk_tools"></a> Narzędzia

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Dołączanie do procesu|**Ctrl+Alt+P**| Tools.AttachtoProcess |
|Menedżer fragmentów kodu|**Ctrl+K, Ctrl+B**| Tools.CodeSnippetsManager |
|Wymuszanie gc|**Ctrl+Shift+Alt+F12, Ctrl+Shift+Alt+F12**| Tools.ForceGC |

### <a name="view"></a><a name="bkmk_view"></a> Widok

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Wszystkie okna|**Shift+Alt+M**| View.AllWindows |
|Eksplorator architektury|**Ctrl+, \\ Ctrl+R**| View.ArchitectureExplorer |
|do tyłu|**Alt+Strzałka w lewo** (funkcje inne niż View.NavigateBackward w edytorze tekstów)| View.Backward |
|Okno zakładki|**Ctrl+K, Ctrl+W**| View.BookmarkWindow |
|Przeglądaj dalej|**Ctrl+Shift+1**| View.BrowseNext |
|Przeglądaj poprzednie|**Ctrl+Shift+2**| View.BrowsePrevious |
|Hierarchia wywołań|**Ctrl+Alt+K**| View.CallHierarchy |
|Widok klasy|**Ctrl+Shift+C**| View.ClassView |
|Widok klasy przejdź do kombi wyszukiwania|**Ctrl+K, Ctrl+V**| View.ClassViewGoToSearchCombo |
|Okno definicji kodu|**Ctrl+, \\ D**<br /><br /> lub<br /><br /> **Ctrl+, \\ Ctrl+D**| View.CodeDefinitionWindow |
|Okno polecenia|**Ctrl+Alt+A**| View.CommandWindow |
|Źródła danych|**Shift+Alt+D**| View.DataSources |
|Konspekt dokumentu|**Ctrl+Alt+T**| View.DocumentOutline |
|Edytowanie etykiety|**F2**| View.EditLabel |
|Lista błędów|**Ctrl+, \\ E**<br /><br /> lub<br /><br /> **Ctrl+, \\ Ctrl+E**| View.ErrorList |
|interakcyjne F#|**Ctrl+Alt+F**| View.F#Interactive |
|Znajdowanie wyników symboli|**Ctrl+Alt+F12**| View.FindSymbolResults |
|do przodu|**Alt+Strzałka w prawo**  (funkcje różnią się od funkcji View.NavigateForward w edytorze tekstów)| View.Forward |
|Przekazywanie kontekstu przeglądania|**Ctrl+Shift+7**| View.ForwardBrowseContext |
|Pełny ekran|**Shift+Alt+Enter**| View.FullScreen |
|Przechodzenie do tyłu|**Ctrl+-**| View.NavigateBackward |
|Przechodzenie do przodu|**Ctrl+Shift+-**| View.NavigateForward |
|Następny błąd|**Ctrl+Shift+F12**| View.NextError |
|Powiadomienia|**Ctrl+W, N**<br /><br /> lub<br /><br /> **Ctrl+W, Ctrl+N**| View.Notifications |
|Przeglądarka obiektów|**Ctrl+Alt+J**| View.ObjectBrowser |
|Przeglądarka obiektów przejdź do wyszukiwania kombi|**Ctrl+K, Ctrl+R**| View.ObjectBrowserGoToSearchCombo |
|Dane wyjściowe|**Ctrl+Alt+O** (litera 'O')| View.Output |
|Kontekst przeglądania podręcznego|**Ctrl+Shift+8** (tylko C++)| View.PopBrowseContext |
|Okno właściwości|**F4**| View.PropertiesWindow |
|strony właściwości|**Shift+F4**| View.PropertyPages |
|Widok zasobów|**Ctrl+Shift+E**| View.ResourceView |
|Eksplorator serwera|**Ctrl+Alt+S**| View.ServerExplorer |
|Pokazywanie tagu inteligentnego|**Shift+Alt+F10**<br /><br /> lub<br /><br /> **Ctrl+.**| View.ShowSmartTag |
|Eksplorator rozwiązań|**Ctrl+Alt+L**| View.SolutionExplorer |
|SQL obiektu serwera|**Ctrl+, \\ Ctrl+S**| View.SQLServerObjectExplorer |
|Lista zadań|**Ctrl+, \\ T**<br /><br /> lub<br /><br /> **Ctrl+, \\ Ctrl+T**| View.TaskList |
|Tfs Team Explorer|**Ctrl+, \\ Ctrl+M**| View.TfsTeamExplorer |
|Przybornik|**Ctrl+Alt+X**| View.Toolbox |
|Eksplorator modeli UML|**Ctrl+, \\ Ctrl+U**| View.UMLModelExplorer |
|Wyświetlanie kodu|**F7**| View.ViewCode |
|Projektant widoków|**Shift+F7**| View.ViewDesigner |
|Przeglądarka sieci Web|**Ctrl+Alt+R**| View.WebBrowser |
|Powiększanie|**Ctrl+Shift+.**| View.ZoomIn |
|Pomniejszanie|**Ctrl+Shift+,**| View.ZoomOut |
|Pokaż Eksplorator testów|**Ctrl+E, T**| TestExplorer.ShowTestExplorer |

### <a name="window"></a><a name="bkmk_window"></a> Okno

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Okno aktywowania dokumentu|**Esc**| Window.ActivateDocumentWindow |
|Dodawanie karty do zaznaczenia|**Ctrl+Shift+Alt+Spacja**| Window.AddTabtoSelection |
|Zamykanie okna dokumentu|**Ctrl+F4**| Window.CloseDocumentWindow |
|Zamykanie okna narzędzia|**Shift + Esc**| Window.CloseToolWindow |
|Zachowaj otwartą kartę|**Ctrl+Alt+Home**| Window.KeepTabOpen |
|Przechodzenie do paska nawigacyjnego|**Ctrl+F2**| Window.MovetoNavigationBar |
|Okno Następnego dokumentu|**Ctrl+F6**| Window.NextDocumentWindow |
|Okno następnego dokumentu nav|**Ctrl+Tab**| Window.NextDocumentWindowNav |
|Następne okienko|**Alt+F6**| Window.NextPane |
|Następne okienko podziału|**F6**| Window.NextSplitPane |
|Karta Dalej|**Ctrl+Alt+PgDn**<br /><br /> lub<br /><br /> **Ctrl+PgDn**| Window.NextTab |
|Następna karta i dodawanie do zaznaczenia|**Ctrl+Shift+Alt+PgDn**| Window.NextTabandAddtoSelection |
|Następny nav okna narzędzi|**Alt+F7**| Window.NextToolWindowNav |
|Okno poprzedniego dokumentu|**Ctrl+Shift+F6**| Window.PreviousDocumentWindow |
|Okno poprzedniego dokumentu nav|**Ctrl+Shift+Tab**| Window.PreviousDocumentWindowNav |
|Poprzednie okienko|**Shift+Alt+F6**| Window.PreviousPane |
|Poprzednie okienko podziału|**Shift+F6**| Window.PreviousSplitPane |
|Poprzednia karta|**Ctrl+Alt+PgUp**<br /><br /> lub<br /><br /> **Ctrl+PgUp**| Window.PreviousTab |
|Poprzednia karta i dodawanie do zaznaczenia|**Ctrl+Shift+Alt+PgUp**| Window.PreviousTabandAddtoSelection |
|Poprzednie okno narzędzia nav|**Shift+Alt+F7**| Window.PreviousToolWindowNav |
|Szybkie uruchamianie|**Ctrl+Q**| Window.QuickLaunch |
|Szybkie uruchamianie w poprzedniej kategorii|**Ctrl+Shift+Q**| Window.QuickLaunchPreviousCategory |
|Menu Pokaż dokowanie|**Alt+-**| Window.ShowDockMenu |
|Show Ex MDI file list (Pokaż listę plików Ex MDI)|**Ctrl+Alt+Strzałka w dół**| Window.ShowEzMDIFileList |
|Wyszukiwanie w Eksploratorze rozwiązań|**Ctrl+;**| Window.SolutionExplorerSearch |
|Wyszukiwanie w oknie|**Alt+'**| Window.WindowSearch |

### <a name="azure"></a><a name="bkmk_windowsazure"></a> Azure

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Ponów próbę wykonania operacji skryptu usługi mobilnej|**Ctrl+Num, \* Ctrl+R**| WindowsAzure.RetryMobileServiceScriptOperation |
|Wyświetlanie szczegółów błędu skryptu usługi mobilnej|**Ctrl+Num, \* Ctrl+D**| WindowsAzure.ShowMobileServiceScriptErrorDetails |

## <a name="context-specific-shortcuts"></a>Skróty kontekstowe


### <a name="adonet-entity-data-model-designer"></a>Projektant modelu danych jednostki ADO.NET

Skróty specyficzne dla tego kontekstu to:

|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|W dół|**Alt+Strzałka w dół**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down |
|W dół 5|**Alt+PgDn**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5 |
|Do dołu|**Alt+End**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom |
|Do góry|**Alt+Home**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop |
|W górę|**Alt+Strzałka w górę**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up |
|W górę 5|**Alt+PgUp**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5 |
|Zmień nazwę|**Ctrl+R, R**| OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename |
|Usuń z diagramu|**Shift+Del**| OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram |
|Przeglądarka modelu danych jednostki|**Ctrl+1**| View.EntityDataModelBrowser |
|Szczegóły mapowania modelu danych jednostki|**Ctrl+2**| View.EntityDataModelMappingDetails |

### <a name="class-diagram"></a>Diagram klas

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Zwiń|**Liczba —**| ClassDiagram.Collapse |
|Rozwiń|**Num +**| ClassDiagram.Expand |
|Usuń|**Ctrl+Del**| Edit.Delete |
|Rozwiń listę zwiń typ podstawowy|**Shift+Alt+B**| Edit.ExpandCollapseBaseTypeList |
|Przejdź do wersji lollipop|**Shift+Alt+L**| Edit.NavigateToLollipop |
|Usuń z diagramu|**Usuwanie**| Edit.RemovefromDiagram |
|Wyświetlanie kodu|**Enter**| View.ViewCode |

### <a name="coded-ui-test-editor"></a>Edytor kodowanego testu interfejsu użytkownika

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Kopiowanie odwołania do schowka|**Ctrl+C**| OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard |
|Opóźnienie wstawiania przed|**Ctrl+Alt+D**| OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore |
|Zlokalizuj wszystko|**Shift+Alt+L**| OtherContextMenus.UITestEditorContextMenu.LocateAll |
|Lokalizowanie kontrolki interfejsu użytkownika|**Ctrl+Shift+L**| OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl |
|Przenoszenie kodu|**Ctrl+Alt+C**| OtherContextMenus.UITestEditorContextMenu.Movecode |
|Podział na nową metodę|**Ctrl+Shift+T**| OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod |

### <a name="dataset-editor"></a>Edytor obiektów DataSet

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Wstawianie kolumny|**Insert**| OtherContextMenus.ColumnContext.InsertColumn |
|Kolumna|**Ctrl+L**| OtherContextMenus.DbTableContext.Add.Column |

### <a name="difference-viewer"></a>Podgląd różnic

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Ignoruj odstępy przycięcia|**Ctrl+, \\ Ctrl+Spacja**| Diff.IgnoreTrimWhitespace |
|Widok wbudowane|**Ctrl+, \\ Ctrl+1**| Diff.InlineView |
|Widok tylko do lewej|**Ctrl+, \\ Ctrl+3**| Diff.LeftOnlyView |
|Następna różnica|**F8**| Diff.NextDifference |
|Poprzednia różnica|**Shift+F8**| Diff.PreviousDifference |
|Widok tylko w prawo|**Ctrl+, \\ Ctrl+4**| Diff.RightOnlyView |
|Widok obok siebie|**Ctrl+, \\ Ctrl+2**| Diff.SideBySideView |
|Przełączanie między lewą i prawą|**Ctrl+, \\ Ctrl+Tab**| Diff.SwitchBetweenLeftAndRight |
|Przełącznik synchronizowania widoku|**Ctrl+, \\ Ctrl+Strzałka w dół**| Diff.SynchronizeViewToggle |
|Dodawanie komentarza|**Ctrl+Shift+K**| EditorContextMenus.CodeWindow.AddComment |
|Edytowanie pliku lokalnego|**Ctrl+Shift+P**| EditorContextMenus.CodeWindow.EditLocalFile |

### <a name="dom-explorer"></a>Eksplorator DOM

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Odśwież|**F5**| DOMExplorer.Refresh |
|Select, element|**Ctrl+B**| DOMExplorer.SelectElement |
|Wyświetlanie układu|**Ctrl+Shift+I**| DOMExplorer.ShowLayout |

### <a name="f-interactive"></a>interakcyjne F#

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Anulowanie interaktywnej oceny|**Ctrl+Break**| OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation |

### <a name="graph-document-editor"></a>Edytor dokumentów wykresu

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Dodawanie węzła|**Insert**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode |
|Obie zależności|**B**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies |
|Zależności przychodzące|**I**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies |
|Zależności wychodzące|**O**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies |
|Nowy komentarz|**Ctrl+Shift+K**<br /><br /> lub<br /><br /> **Ctrl+E, C**| ArchitectureContextMenus.DirectedGraphContextMenu.NewComment |
|Usuń|**Usuwanie**| ArchitectureContextMenus.DirectedGraphContextMenu.Remove |
|Zmień nazwę|**F2**| ArchitectureContextMenus.DirectedGraphContextMenu.Rename |

### <a name="graphics-diagnostics"></a>Diagnostyka grafiki

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Ramka przechwytywania|Brak| Debug.Graphics.CaptureFrame |
|Przenoszenie zaznaczenia pikseli w dół|**Shift+Alt+Strzałka w dół**| Graphics.MovePixelSelectionDown |
|Przenoszenie zaznaczenia pikseli w lewo|**Shift+Alt+Strzałka w lewo**| Graphics.MovePixelSelectionLeft |
|Przenoszenie zaznaczenia pikseli w prawo|**Shift+Alt+Strzałka w prawo**| Graphics.MovePixelSelectionRight |
|Przenoszenie zaznaczenia pikseli w górę|**Shift+Alt+Strzałka w górę**| Graphics.MovePixelSelectionUp |
|Powiększanie do rzeczywistego rozmiaru|**Shift+Alt+0** (zero)| Graphics.ZoomToActualSize |
|Powiększanie w celu dopasowania do okna|**Shift+Alt+9**| Graphics.ZoomToFitInWindow |
|Powiększanie|**Shift+Alt+=**| Graphics.ZoomIn |
|Pomniejszanie|**Shift+Alt+-**| Graphics.ZoomOut |

### <a name="html-editor"></a>Edytor HTML

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Przejdź do kontrolera|**Ctrl+M, Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |

### <a name="html-editor-design-view"></a>Widok projektu edytora HTML

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Przenoszenie kontrolki w dół|**Ctrl+strzałka w dół**| Edit.MoveControlDown |
|Przenieś kontrolę w górę|**Ctrl+Strzałka w górę**| Edit.MoveControlUp |
|Pogrubiona|**Ctrl+B**| Format.Bold |
|Konwertowanie na hiperlink|**Ctrl+L**| Format.ConverttoHyperlink |
|Wstaw zakładkę|**Ctrl+Shift+L**| Format.InsertBookmark |
|Kursywa|**CTRL + I**| Format.Italic |
|Podkreślenie|**Ctrl+U**| Format.Underline |
|Dodawanie strony zawartości|**Ctrl+M, Ctrl+C**| Project.AddContentPage |
|Kolumna po lewej stronie|**Ctrl+Alt+Strzałka w lewo**| Table.ColumntotheLeft |
|Kolumna z prawej strony|**Ctrl+Alt+Strzałka w prawo**| Table.ColumntotheRight |
|Wiersz powyżej|**Ctrl+Alt+Strzałka w górę**| Table.RowAbove |
|Wiersz poniżej|**Ctrl+Alt+Strzałka w dół**| Table.RowBelow |
|Kontrolki nievisualne sieci|**Ctrl+Shift+N**| View.ASP.NETNonvisualControls |
|Edytowanie wzorca|**Ctrl+M, Ctrl+M**| View.EditMaster |
|Następny widok|**Ctrl+PgDn**| View.NextView |
|Pokazywanie tagu inteligentnego|**Shift+Alt+F10**| View.ShowSmartTag |
|Wyświetlanie znaczników|**Shift+F7**| View.ViewMarkup |
|Poprzednia karta|**Ctrl+PgUp**| Window.PreviousTab |

### <a name="html-editor-source-view"></a>Widok źródła edytora HTML

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Przejdź do kontrolera|**Ctrl+M, Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |
|Następny widok|**Ctrl+PgDn**| View.NextView |
|Synchronizowanie widoków|**Ctrl+Shift+Y**| View.SynchronizeViews |
|Projektant widoków|**Shift+F7**| View.ViewDesigner |
|Poprzednia karta|**Ctrl+PgUp**| Window.PreviousTab |

### <a name="layer-diagram"></a>Diagram warstwowy

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Usuń|**Shift+Delete**| Edit.Delete |

### <a name="managed-resources-editor"></a>Edytor zasobów zarządzanych

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Edytuj komórkę|**F2**| Edit.EditCell |
|Usuń|**Usuwanie**| Edit.Remove |
|Usuń wiersz|**Ctrl+Delete**| Edit.RemoveRow |
|Anulowanie wyboru|**Escape**| Edit.SelectionCancel |
|Dźwięk|**Ctrl+4**| Resources.Audio |
|Pliki|**Ctrl+5**| Resources.Files |
|Ikony|**Ctrl+3**| Resources.Icons |
|Obrazy|**Ctrl+2**| Resources.Images |
|Inne|**Ctrl+6**| Resources.Other |
|Ciągi|**Ctrl+1**| Resources.Strings |

### <a name="merge-editor-window"></a>Okno Edytor scalania

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Ustawianie fokusu w lewym oknie|**Alt+1**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow |
|Ustawianie fokusu w oknie wyników|**Alt+2**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow |
|Ustawianie fokusu w prawym oknie|**Alt+3**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow |

### <a name="microsoft-sql-server-data-tools-schema-compare"></a>Narzędzia danych Microsoft SQL Server, Porównywanie schematów

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Porównanie schematów SSDT|**Shift+Alt+C**| SQL.SSDTSchemaCompareCompare |
|Porównywanie schematów SSDT — generowanie skryptu|**Shift+Alt+G**| SQL.SSDTSchemaCompareGenerateScript |
|Porównywanie następnej zmiany schematu SSDT|**Shift+Alt+.**| SQL.SSDTSchemaCompareNextChange |
|Porównanie schematów SSDT z poprzednią zmianą|**Shift+Alt+,**| SQL.SSDTSchemaComparePreviousChange |
|Zatrzymywanie porównywania schematów SSDT|**Alt+Break**| SQL.SSDTSchemaCompareStop |
|Porównanie aktualizacji zapisu w schemacie SSDT|**Shift+Alt+U**| SQL.SSDTSchemaCompareWriteUpdates |

### <a name="microsoft-sql-server-data-tools-table-designer"></a>Narzędzia danych Microsoft SQL Server, Projektant tabel

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|CommitAllEdits|**Shift+Alt+U**|
|Rozwijanie symboli wieloznacznych|**Ctrl+R, E**<br /><br /> lub<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|W pełni kwalifikowane nazwy|**Ctrl+R, Q**<br /><br /> lub<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Przejście do schematu|**Ctrl+R, M**<br /><br /> lub<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|Zmień nazwę|**F2**<br /><br /> lub<br /><br /> **Ctrl+R, R**<br /><br /> lub<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|ViewFileInScriptPanel|**Shift+Alt+PgDn**| |

### <a name="microsoft-sql-server-data-tools-t-sql-editor"></a>Narzędzia danych Microsoft SQL Server, Edytor T-SQL

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|CommitAllEdits|**Shift+Alt+U**|
|Wykonywanie za pomocą debugera|**Alt+F5**| SQL.ExecuteWithDebugger |
|Rozwijanie symboli wieloznacznych|**Ctrl+R, E**<br /><br /> lub<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|W pełni kwalifikowane nazwy|**Ctrl+R, Q**<br /><br /> lub<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Przejście do schematu|**Ctrl+R, M**<br /><br /> lub<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|Zmień nazwę|**F2**<br /><br /> lub<br /><br /> **Ctrl+R, R**<br /><br /> lub<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|T <1> <3> SQL editor cancel query|**Alt+Break**| SQL.TSqlEditorCancelQuery |
|T SQL wykonywania zapytania w edytorze|**Ctrl+Shift+E**| SQL.TSqlEditorExecuteQuery |
|T <1> <3> editor results as file (T SQL wyniki edytora jako plik)|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|T SQL <1> <2> wyniki edytora jako siatka|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|T SQL w edytorze jako tekst|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|T <3> <8> editor show estimated plan (SQL Szacowany plan jest pokazywany w edytorze T)|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|T SQL <2> <2> editor toggle execution plan (Przełączanie planu wykonywania w edytorze T)|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|SQL T <1> <8> w okienku wyników przełączania|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|T SQL klonowania edytora|**Ctrl+Alt+N**|SQL. TSqlEditorCloneQuery |
|T SQL bazy danych edytora|**Shift+Alt+PgDn**|SQL. TSqlEditorDatabaseCombo |

### <a name="microsoft-sql-server-data-tools-t-sql-pdw-editor"></a>Narzędzia danych Microsoft SQL Server, Edytor T-SQL PDW

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|T <1> <3> SQL editor cancel query|**Alt+Break**| SQL.TSqlEditorCancelQuery |
|T SQL wykonywania zapytania w edytorze|**Ctrl+Shift+E**| SQL.TSqlEditorExecuteQuery |
|T <1> <3> editor results as file (T SQL wyniki edytora jako plik)|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|T SQL <1> <2> wyniki edytora jako siatka|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|T SQL w edytorze jako tekst|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|T <3> <8> editor show estimated plan (SQL Szacowany plan jest pokazywany w edytorze T)|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|T SQL <2> <2> editor toggle execution plan (Przełączanie planu wykonywania w edytorze T)|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|SQL T <1> <8> w okienku wyników przełączania|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|T SQL klonowania edytora|**Ctrl+Alt+N**|SQL. TSqlEditorCloneQuery |
|T SQL klonowania edytora|**Shift+Alt+PgDn**|SQL. TSqlEditorCloneQuery |

### <a name="page-inspector"></a>Inspektor strony

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Minimalizuj|**F12**| PageInspector.Minimize |

### <a name="query-designer"></a>Projektant zapytań

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Anulowanie pobierania danych|**Ctrl+T**| QueryDesigner.CancelRetrievingData |
|Kryteria|**Ctrl+2**| QueryDesigner.Criteria |
|Diagram|**Ctrl+1**| QueryDesigner.Diagram |
|Wykonaj SQL|**Ctrl+R**| QueryDesigner.ExecuteSQL |
|Goto row (Goto row)|**Ctrl+G**| QueryDesigner.GotoRow |
|Tryb sprzężenia|**Ctrl+Shift+J**| QueryDesigner.JoinMode |
|Wyniki|**Ctrl+4**| QueryDesigner.Results |
|Sql|**Ctrl+3**| QueryDesigner.SQL |

### <a name="query-results"></a>Wyniki zapytania

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Wyniki zapytania nowego wiersza|**Alt+End**| SQL.QueryResultsNewRow |
|Odświeżanie wyników zapytania|**Shift+Alt+R**| SQL.QueryResultsRefresh |
|Zatrzymywanie wyników zapytania|**Alt+Break**| SQL.QueryResultsStop |

### <a name="report-designer"></a>Projektant raportów

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Wiersz przerwania|**Enter**| Edit.BreakLine |
|Char left|**Strzałka w lewo**| Edit.CharLeft |
|Char left extend|**Shift+Strzałka w lewo**| Edit.CharLeftExtend |
|Char po prawej stronie|**Strzałka w prawo**| Edit.CharRight |
|Rozszerzenie w prawo dla znaków|**Shift+Strzałka w prawo**| Edit.CharRightExtend |
|Karta Wstawianie|**Tab**| Edit.InsertTab |
|Wiersz w dół|**Strzałka w dół**| Edit.LineDown |
|Rozszerzanie linii w dół|**Shift+Strzałka w dół**| Edit.LineDownExtend |
|Wiersz w górę|**Strzałka w górę**| Edit.LineUp |
|Rozszerzanie linii|**Shift+Strzałka w górę**| Edit.LineUpExtend |
|Przenoszenie kontrolki w dół|**Ctrl+strzałka w dół**| Edit.MoveControlDown |
|Przenoszenie kontrolki w lewo|**Ctrl+Strzałka w lewo**| Edit.MoveControlLeft |
|Przenoszenie kontrolki w prawo|**Ctrl+Strzałka w prawo**| Edit.MoveControlRight |
|Przenoszenie kontroli w górę|**Ctrl+Strzałka w górę**| Edit.MoveControlUp |
|Anulowanie wyboru|**Esc**| Edit.SelectionCancel |
|Kontrola rozmiaru w dół|**Ctrl+Shift+Strzałka w dół**| Edit.SizeControlDown |
|Kontrolka rozmiaru w lewo|**Ctrl+Shift+Strzałka w lewo**| Edit.SizeControlLeft |
|Prawa kontrolka rozmiaru|**Ctrl+Shift+Strzałka w prawo**| Edit.SizeControlRight |
|Kontrola rozmiaru w górę|**Ctrl+Shift+Strzałka w górę**| Edit.SizeControlUp |
|Tabulator po lewej stronie|**Shift+Tab**| Edit.TabLeft |
| Dane raportu|**Ctrl+Alt+D**| View.ReportData |

### <a name="sequence-diagram"></a>Diagramów sekwencji

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Przechodzenie do kodu|**F12**| ArchitectureDesigner.Sequence.NavigateToCode |
|Usuń|**Shift+Del**| Edit.Delete |

### <a name="settings-designer"></a>Projektant ustawień

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Edytowanie komórki|**F2**| Edit.EditCell |
|Usuwanie wiersza|**Ctrl+Delete**| Edit.RemoveRow |
|Anulowanie wyboru|**Esc**| Edit.SelectionCancel |
|Wyświetlanie kodu|**F7**| View.ViewCode |

### <a name="solution-explorer"></a>Eksplorator rozwiązań

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Wyświetlanie w inspektorze strony|**Ctrl+K, Ctrl+G**| ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector |

### <a name="team-explorer"></a>Team Explorer

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Usuń|**Usuwanie**| Edit.Delete |
|Zmień nazwę|**F2**| File.Rename |
|Przejdź do nawigacji w programie Team Explorer|**Alt+Home**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation |
|Przejdź do zawartości następnej sekcji programu Team Explorer|**Alt+Strzałka w dół**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent |
|Przejdź do zawartości strony programu Team Explorer|**Alt+0** (zero)| TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent |
|Przejdź do zawartości poprzedniej sekcji w programie Team Explorer|**Alt+Strzałka w górę**| TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent |
|Przejdź do zawartości sekcji 1 programu Team Explorer|**Alt+1**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content |
|Przejdź do zawartości sekcji 2 programu Team Explorer|**Alt+2**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content |
|Przejdź do zawartości sekcji 3 programu Team Explorer|**Alt+3**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content |
|Przejdź do sekcji 4 programu Team Explorer|**Alt+4**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content |
|Przejdź do sekcji 5 programu Team Explorer|**Alt+5**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content |
|Przejdź do sekcji 6 programu Team Explorer|**Alt+6**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content |
|Przejdź do zawartości sekcji 7 programu Team Explorer|**Alt+7**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content |
|Przejdź do sekcji Team Explorer 8 zawartości|**Alt+8**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content |
|Przejdź do sekcji Team Explorer 9 zawartości|**Alt+9**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content |
|Przechodzenie do tyłu w programie Team Explorer|**Alt+Strzałka w lewo**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward |
|Przechodzenie do przodu w programie Team Explorer|**Alt+Strzałka w prawo**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward |
|Kontekst TFS moja strona służbowa tworzy kopię wi|**Shift+Alt+C**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI |
|Kontekst TFS moja strona służbowa : nowe połączone wi|**Shift+Alt+L**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI |
|Odśwież|**F5**| View.Refresh |

### <a name="test-explorer"></a>Eksplorator testów

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Otwieranie testu|**F12**| TestExplorer.OpenTest |

### <a name="text-editor"></a>Edytor tekstu

Skróty specyficzne dla tego kontekstu to:


| Polecenia | Skróty klawiaturowe |Identyfikator polecenia|
|-|-|-|
|Wiersz przerwania| **Enter**<br /><br /> lub<br /><br /> **Shift+Enter** | Edit.BreakLine |
|Char left| **Strzałka w lewo** | Edit.CharLeft |
|Char left extend| **Shift+Strzałka w lewo** | Edit.CharLeftExtend |
|Kolumna rozszerz w lewo dla znaków| **Shift+Alt+Strzałka w lewo** | Edit.CharLeftExtendColumn |
|Char po prawej stronie| **Strzałka w prawo** | Edit.CharRight |
|Rozszerzenie w prawo dla znaków| **Shift+Strzałka w prawo** | Edit.CharRightExtend |
|Prawa kolumna rozszerzenia char| **Shift+Alt+Strzałka w prawo** | Edit.CharRightExtendColumn |
|Wyczyść zakładki| **Ctrl+K, Ctrl+L** | Edit.ClearBookmarks |
|Zwiń wszystkie zwijanie| **Ctrl+M, Ctrl+A** | Edit.CollapseAllOutlining |
|Zwiń bieżący region| **Ctrl+M, Ctrl+S** | Edit.CollapseCurrentRegion |
|Zwiń tag| **Ctrl+M, Ctrl+T** | Edit.CollapseTag |
|Zwijanie do definicji| **Ctrl+M, Ctrl+O** (litera 'O') | Edit.CollapseToDefinitions |
|Wybór kontraktu| **Shift+Alt+-** | Edit.ContractSelection |
|Wybór komentarza| **Ctrl+K, Ctrl+C** | Edit.CommentSelection |
|Wyraz ukończony| **Ctrl+Space**<br /><br /> lub<br /><br /> **Alt+Strzałka w prawo** | Edit.CompleteWord |
|Porada kopiowania parametru| **Ctrl+Shift+Alt+C** | Edit.CopyParameterTip |
|Zmniejszanie poziomu filtru| **Alt+,** | Edit.DecreaseFilterLevel |
|Usuwanie wstecz| **Backspace**<br /><br /> lub<br /><br /> **Shift+Bkspce** | Edit.DeleteBackwards |
|Usuwanie poziomego odstępu| **Ctrl+K, Ctrl+\\** | Edit.DeleteHorizontalWhiteSpace |
|Koniec dokumentu| **Ctrl+End** | Edit.DocumentEnd |
|Rozszerzenie końca dokumentu| **Ctrl+Shift+End** | Edit.DocumentEndExtend |
|Rozpoczynanie dokumentu| **Ctrl+Home** | Edit.DocumentStart |
|Rozpoczynanie rozszerzania dokumentu| **Ctrl+Shift+Home** | Edit.DocumentStartExtend |
|Rozwiń wszystkie wyłoki| **Ctrl+M, Ctrl+X** | Edit.ExpandAllOutlining |
|Rozwijanie bieżącego regionu| **Ctrl+M, Ctrl+E** | Edit.ExpandCurrentRegion |
|Rozwiń wybór| **Shift+Alt+=** | Edit.ExpandSelection |
|Rozwiń zaznaczenie do zawierającego blok| **Shift+Alt+]** | Edit.ExpandSelectiontoContainingBlock |
|Formatowanie dokumentu| **Ctrl+K, Ctrl+D** | Edit.FormatDocument |
|Formatowanie zaznaczenia| **Ctrl+K, Ctrl+F** | Edit.FormatSelection |
|Goto all| **Ctrl+T**<br /><br /> lub<br /><br /> **Ctrl+,** | Edit.GotoAll |
|Nawias klamrowy Goto| **Ctrl+]** | Edit.GotoBrace |
|Rozszerzenie nawiasu klamrowego Goto| **Ctrl+Shift+]** | Edit.GotoBraceExtend |
|Goto recent| **Ctrl+T,R** | Edit.GotoRecent |
|Goto next issue in file (Goto next issue in file )Goto next issue in file| **Alt+PgDn** | Edit.GotoNextIssueinFile |
|Goto previous issue in file (Goto previous issue in file )Goto previous issue in file| **Alt+PgUp** | Edit.GotoPreviousIssueinFile |
|Ukryj zaznaczenie| **Ctrl+M, Ctrl+H** | Edit.HideSelection |
|Zwiększanie poziomu filtru| **Alt +.** | Edit.IncreaseFilterLevel |
|Wyszukiwanie przyrostowe| **CTRL + I** | Edit.IncrementalSearch |
|Wstawianie carets w ogóle zgodne| **Shift+Alt+;** | Edit.InsertCaretsatAllMatching |
|Wstaw następny pasujący wieniec| **Shift+Alt+.** | Edit.InsertNextMatchingCaret |
|Karta Wstawianie| **Tab** | Edit.InsertTab |
|Wycinanie liniowe| **Ctrl+L** | Edit.LineCut |
|Usuwanie wiersza| **Ctrl+Shift+L** | Edit.LineDelete |
|Wiersz w dół| **Strzałka w dół** | Edit.LineDown |
|Rozszerzanie wiersza w dół| **Shift+Strzałka w dół** | Edit.LineDownExtend |
|Rozszerzanie kolumny wiersza w dół| **Shift+Alt+Strzałka w dół** | Edit.LineDownExtendColumn |
|Koniec wiersza| **End** | Edit.LineEnd |
|Rozszerzenie końca wiersza| **Shift+End** | Edit.LineEndExtend |
|Rozszerzanie kolumny na końcu wiersza| **Shift+Alt+End** | Edit.LineEndExtendColumn |
|Wiersz otwarty powyżej| **Ctrl+Enter** | Edit.LineOpenAbove |
|Wiersz otwarty poniżej| **Ctrl+Shift+Enter** | Edit.LineOpenBelow |
|Początek wiersza| **Ekran główny** | Edit.LineStart |
|Początek wiersza , rozszerzanie| **Shift+Home** | Edit.LineStartExtend |
|Początek wiersza , rozszerzanie kolumny| **Shift+Alt+Home** | Edit.LineStartExtendColumn |
|Transponowanie wiersza| **Shift+Alt+T** | Edit.LineTranspose |
|Wiersz w górę| **Strzałka w górę** | Edit.LineUp |
|Rozszerzanie linii| **Shift+Strzałka w górę** | Edit.LineUpExtend |
|Rozszerzanie kolumny w wierszu| **Shift+Alt+Strzałka w górę** | Edit.LineUpExtendColumn |
|Lista elementów członkowskich| **Ctrl+J** | Edit.ListMembers |
|Małe litery| **Ctrl+U** | Edit.MakeLowercase |
|Wielkie litery| **Ctrl+Shift+U** | Edit.MakeUppercase |
|Przenieś wybrane wiersze w dół| **Alt+Strzałka w dół** | Edit.MoveSelectedLinesDown |
|Przenieś wybrane wiersze w górę| **Alt+Strzałka w górę** | Edit.MoveSelectedLinesUp |
|Dalej wyróżnione odwołanie| **Ctrl+Shift+Strzałka w dół** | Edit.NextHighlightedReference |
|Tryb zastępowania| **Insert** | Edit.OvertypeMode |
|Page down (Strona w dół)| **PgDn** | Edit.PageDown |
|Rozszerzanie strony w dół| **Shift+PgDn** | Edit.PageDownExtend |
|Stronicuj w górę| **PgUp** | Edit.PageUp |
|Rozszerzanie strony w górę| **Shift+PgUp** | Edit.PageUpExtend |
|Informacje o parametrach| **Ctrl+Shift+Spacebar** | Edit.ParameterInfo |
|Porada wklejania parametru| **Ctrl+Shift+Alt+P** | Edit.PasteParameterTip |
|Podejrzanie do tyłu| **Ctrl+Alt+-** | Edit.PeekBackward |
|Wgląd w definicję| **Alt+F12** | Edit.PeekDefinition |
|Podejrzanie do przodu| **Ctrl+Alt+=** | Edit.PeekForward |
|Poprzednie wyróżnione odwołanie| **Ctrl+Shift+Strzałka w górę** | Edit.PreviousHighlightedReference |
|Szybkie informacje| **Ctrl+K, Ctrl+I** | Edit.QuickInfo |
|Odwrotne wyszukiwanie przyrostowe| **Ctrl+Shift+I** | Edit.ReverseIncrementalSearch |
|Przewiń wiersz w dół| **Ctrl+strzałka w dół** | Edit.ScrollLineDown |
|Przewiń wiersz w górę| **Ctrl+Strzałka w górę** | Edit.ScrollLineUp |
|Wybieranie bieżącego wyrazu| **Ctrl+W** | Edit.SelectCurrentWord |
|Anulowanie wyboru| **Escape** | Edit.SelectionCancel |
|Wybierz pozycję , aby ostatnio wrócić| **Ctrl+=** | Edit.SelectToLastGoBack |
|Menu Pokaż kod obiektywu| **Ctrl+K, Ctrl+\`** | Edit.ShowCodeLensMenu |
|Pokaż menu nawigowania| **Alt+\`** | Edit.ShowNavigateMenu |
|Zatrzymywanie ukrywania bieżącego| **Ctrl+M, Ctrl+U** | Edit.StopHidingCurrent |
|Zatrzymywanie linuowania| **Ctrl+M, Ctrl+P** | Edit.StopOutlining |
|Zamień kotwicę| **Ctrl+K, Ctrl+A** | Edit.SwapAnchor |
|Tabulator po lewej stronie| **Shift+Tab** | Edit.TabLeft |
|Przełącz wszystkie wyłoki| **Ctrl+M, Ctrl+L** | Edit.ToggleAllOutlining |
|Przełącz zakładkę| **Ctrl+K, Ctrl+K** | Edit.ToggleBookmark |
|Przełączanie trybu uzupełniania| **Ctrl+Alt+Spacja** | Edit.ToggleCompletionMode |
|Przełączanie rozszerzania wyekslinowania| **Ctrl+M, Ctrl+M** | Edit.ToggleOutliningExpansion |
|Skrót do przełączania listy zadań| **Ctrl+K, Ctrl+H** | Edit.ToggleTaskListShortcut |
|Przełączanie zawijania wyrazów| **Ctrl+E, Ctrl+W** | Edit.ToggleWordWrap |
|Zaznaczenie opcji Cokmentuj| **Ctrl+K, Ctrl+U** | Edit.UncommentSelection |
|Wyświetl do dołu| **Ctrl+PgDn** | Edit.ViewBottom |
|Wyświetl dolne rozszerzenie| **Ctrl+Shift+PgDn** | Edit.ViewBottomExtend |
|Wyświetl u góry| **Ctrl+PgUp** | Edit.ViewTop |
|Wyświetl górne rozszerzenie| **Ctrl+Shift+PgUp** | Edit.ViewTopExtend |
|Wyświetlanie białych spacji| **Ctrl+R, Ctrl+W** | Edit.ViewWhiteSpace |
|Usuwanie programu Word do końca| **Ctrl+Delete** | Edit.WordDeleteToEnd |
|Usuwanie programu Word do uruchomienia| **Ctrl+Backspace** | Edit.WordDeleteToStart |
|Następne słowo| **Ctrl+Strzałka w prawo** | Edit.WordNext |
|Następne rozszerzenie programu Word| **Ctrl+Shift+Strzałka w prawo** | Edit.WordNextExtend |
|Następne rozszerzanie kolumny programu Word| **Ctrl+Shift+Alt+Strzałka w prawo** | Edit.WordNextExtendColumn |
|Wyraz poprzedni| **Ctrl+Strzałka w lewo** | Edit.WordPrevious |
|Poprzednie rozszerzenie programu Word| **Ctrl+Shift+Strzałka w lewo** | Edit.WordPreviousExtend |
|Poprzednia kolumna rozszerzenia programu Word| **Ctrl+Shift+Alt+Strzałka w lewo** | Edit.WordPreviousExtendColumn |
|Transponowanie wyrazów| **Ctrl+Shift+T** | Edit.WordTranspose |
|Wykonywanie w trybie interaktywnym| **Alt+Enter** | EditorContextMenus.CodeWindow.ExecuteInInteractive |
|Wykonywanie wiersza w trybie interaktywnym| **Alt+'** | EditorContextMenus.CodeWindow.ExecuteLineInInteractive |
|Wyświetlanie w inspektorze strony| **Ctrl+K, Ctrl+G** | OtherContextMenus.HTMLContext.ViewinPageInspector |
|Tfs annotate move next region (Adnotacje TFS : przenoszenie następnego regionu)| **Alt+PgDn** | TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion |
|Tfs annotate move previous region (Przenoszenie poprzedniego regionu przy użyciu adnotacji tfs)| **Alt+PgUp** | TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion |

### <a name="uml-activity-diagram"></a>Diagram aktywności UML

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Usuń|**Shift+Del**| Edit.Delete |

### <a name="uml-class-diagram"></a>Diagram klas UML

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Usuń z modelu|**Shift+Del**| Edit.DeleteFromModel |

### <a name="uml-component-diagram"></a>Diagram składników UML

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Usuń z modelu|**Shift+Del**| Edit.DeleteFromModel |

### <a name="uml-use-case-diagram"></a>Diagram przypadków użycia UML

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Usuń z modelu|**Shift+Del**| Edit.DeleteFromModel |

### <a name="vc-accelerator-editor"></a>Edytor klawiszy skrótów VC

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Nowy akcelerator|**Insert**| Edit.NewAccelerator |
|Wpisanie następnego klucza|**Ctrl+W**| Edit.NextKeyTyped |

### <a name="vc-dialog-editor"></a>Edytor okien dialogowych VC

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Przenoszenie kontrolki w dół|**Strzałka w dół**| Edit.MoveControlDown |
|Przenoszenie kontrolki w lewo|**Strzałka w lewo**| Edit.MoveControlLeft |
|Przenoszenie kontrolki w prawo|**Strzałka w prawo**| Edit.MoveControlRight |
|Przenieś kontrolę w górę|**Strzałka w górę**| Edit.MoveControlUp |
|Przewiń kolumnę w lewo|**Ctrl+Strzałka w lewo**| Edit.ScrollColumnLeft |
|Przewiń kolumnę w prawo|**Ctrl+Strzałka w prawo**| Edit.ScrollColumnRight |
|Przewiń wiersz w dół|**Ctrl+strzałka w dół**| Edit.ScrollLineDown |
|Przewiń wiersz w górę|**Ctrl+Strzałka w górę**| Edit.ScrollLineUp |
|Kontrola rozmiaru w dół|**Shift+Strzałka w dół**| Edit.SizeControlDown |
|Kontrolka rozmiaru w lewo|**Shift+Strzałka w lewo**| Edit.SizeControlLeft |
|Prawa kontrolka rozmiaru|**Shift+Strzałka w prawo**| Edit.SizeControlRight |
|Kontrola rozmiaru|**Shift+Strzałka w górę**| Edit.SizeControlUp |
|Wyrównywanie dolnej części|**Ctrl+Shift+Strzałka w dół**| Format.AlignBottoms |
|Wyrównaj centra|**Shift+F9**| Format.AlignCenters |
|Wyrównaj do lewej|**Ctrl+Shift+Strzałka w lewo**| Format.AlignLefts |
|Wyrównywanie środkowych|**F9**| Format.AlignMiddles |
|Wyrównywanie praw|**Ctrl+Shift+Strzałka w prawo**| Format.AlignRights |
|Wyrównaj wierzchoł|**Ctrl+Shift+Strzałka w górę**| Format.AlignTops |
|Dolna część przycisku|**Ctrl+B**| Format.ButtonBottom |
|Przycisk po prawej stronie|**Ctrl+R**| Format.ButtonRight |
|Wyśrodkowanie w poziomie|**Ctrl+Shift+F9**| Format.CenterHorizontal |
|Wyśrodkowanie pionowe|**Ctrl+F9**| Format.CenterVertical |
|Sprawdzanie mnemonik|**Ctrl+M**| Format.CheckMnemonics |
|Rozmiar zawartości|**Shift+F7**| Format.SizetoContent |
|Spacja między|**Alt+Strzałka w prawo**<br /><br /> lub<br /><br /> **Alt+Strzałka w lewo**| Format.SpaceAcross |
|Spacja w dół|**Alt+Strzałka w górę**<br /><br /> lub<br /><br /> **Alt+Strzałka w dół**| Format.SpaceDown |
|Kolejność tabulacji|**Ctrl + D**| Format.TabOrder |
|Okno dialogowe testowania|**Ctrl+T**| Format.TestDialog |
|Przełącz prowadnice|**Ctrl+G**| Format.ToggleGuides |

### <a name="vc-image-editor"></a>Edytor obrazów VC

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Narzędzie Airbrush|**Ctrl+A**| Image.AirbrushTool |
|Narzędzie pędzla|**Ctrl+B**| Image.BrushTool |
|Kopiowanie i zaznaczanie konturu|**Ctrl+Shift+U**| Image.CopyandOutlineSelection |
|Rysowanie nieprzezroczyste|**Ctrl+J**| Image.DrawOpaque |
|Narzędzie wielokropka|**Alt+P**| Image.EllipseTool |
|Narzędzie do wymazywania|**Ctrl+Shift+I**| Image.EraseTool |
|Narzędzie wypełnione wielokropka|**Ctrl+Shift+Alt+P**| Image.FilledEllipseTool |
|Narzędzie wypełnionego prostokąta|**Ctrl+Shift+Alt+R**| Image.FilledRectangleTool |
|Narzędzie wypełnionego prostokąta|**Ctrl+Shift+Alt+W**| Image.FilledRoundedRectangleTool |
|Narzędzie wypełniania|**Ctrl+F**| Image.FillTool |
|Przerzucanie w poziomie|**Ctrl+H**| Image.FlipHorizontal |
|Przerzucanie w pionie|**Shift+Alt+H**| Image.FlipVertical |
|Większy pędzl|**Ctrl+=**| Image.LargerBrush |
|Narzędzie liniowe|**Ctrl+L**| Image.LineTool |
|Narzędzie powiększania|**Ctrl+M**| Image.MagnificationTool |
|Powiększyć|**Ctrl+Shift+M**| Image.Magnify |
|Nowy typ obrazu|**Insert**| Image.NewImageType |
|Następny kolor|**Ctrl+]**<br /><br /> lub<br /><br /> **Ctrl+Strzałka w prawo**| Image.NextColor |
|Następny prawy kolor|**Ctrl+Shift+]**<br /><br /> lub<br /><br /> **Ctrl+Shift+Strzałka w prawo**| Image.NextRightColor |
|Narzędzie wielokropka z konturem|**Shift+Alt+P**| Image.OutlinedEllipseTool |
|Narzędzie prostokąta z konturem|**Shift+Alt+R**| Image.OutlinedRectangleTool |
|Narzędzie z zaokrąglonym prostokątem z konturem|**Shift+Alt+W**| Image.OutlinedRoundedRectangleTool |
|Narzędzie ołówka|**CTRL + I**| Image.PencilTool |
|Poprzedni kolor|**Ctrl+[**<br /><br /> lub<br /><br /> **Ctrl+Strzałka w lewo**| Image.PreviousColor |
|Poprzedni prawy kolor|**Ctrl+Shift+[**<br /><br /> lub<br /><br /> **Ctrl+Shift+Strzałka w lewo**| Image.PreviousRightColor |
|Narzędzie wyboru prostokąta|**Shift+Alt+S**| Image.RectangleSelectionTool |
|Narzędzie prostokąta|**Alt+R**| Image.RectangleTool |
|Obrót o 90 stopni stopnia|**Ctrl+Shift+H**| Image.Rotate90Degrees |
|Narzędzie zaokrąglonego prostokąta|**Alt+W**| Image.RoundedRectangleTool |
|Pokazywanie siatki|**Ctrl+Alt+S**| Image.ShowGrid |
|Pokazywanie siatki kafelków|**Ctrl+Shift+Alt+S**| Image.ShowTileGrid |
|Mały pędzl|**Ctrl+.**| Image.SmallBrush |
|Mniejszy pędzl|**Ctrl+-**| Image.SmallerBrush |
|Narzędzie tekstowe|**Ctrl+T**| Image.TextTool |
|Używanie zaznaczenia jako pędzla|**Ctrl+U**| Image.UseSelectionasBrush |
|Powiększanie|**Ctrl+Shift+.**<br /><br /> lub<br /><br /> **Ctrl+Strzałka w górę**| Image.ZoomIn |
|Pomniejszanie|**Ctrl+Shift+,**<br /><br /> lub<br /><br /> **Ctrl+strzałka w dół**| Image.ZoomOut |

### <a name="vc-string-editor"></a>Edytor ciągów VC

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Nowy ciąg|**Insert**| Edit.NewString |

### <a name="view-designer"></a>Projektant widoków

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Anulowanie pobierania danych|**Ctrl+T**| QueryDesigner.CancelRetrievingData |
|Kryteria|**Ctrl+2**| QueryDesigner.Criteria |
|Diagram|**Ctrl+1**| QueryDesigner.Diagram |
|Wykonaj SQL|**Ctrl+R**| QueryDesigner.ExecuteSQL |
|Goto row (Goto row)|**Ctrl+G**| QueryDesigner.GotoRow |
|Tryb sprzężenia|**Ctrl+Shift+J**| QueryDesigner.JoinMode |
|Wyniki|**Ctrl+4**| QueryDesigner.Results |
|Sql|**Ctrl+3**| QueryDesigner.SQL |

### <a name="visual-studio"></a>Visual Studio

Skróty specyficzne dla tego kontekstu to:


|Polecenie|Skrót klawiaturowy|Identyfikator polecenia|
|-|-|-|
|Okienko Ukrywanie metod|**Ctrl+1**| OtherContextMenus.ORDesignerContext.HideMethodsPane |

### <a name="windows-forms-designer"></a>Projektant Windows Forms

Skróty specyficzne dla tego kontekstu są:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Linia przerwania|**Enter**| Edit.BreakLine |
|Char po lewej stronie|**Strzałka w lewo**| Edit.CharLeft |
|Lewe rozszerzenie char|**Shift+Strzałka w lewo**| Edit.CharLeftExtend |
|Char po prawej stronie|**Strzałka w prawo**| Edit.CharRight |
|Rozszerzanie znaków w prawo|**Shift+Strzałka w prawo**| Edit.CharRightExtend |
|Koniec dokumentu|**End**| Edit.DocumentEnd |
|Rozszerzenie końca dokumentu|**Shift+End**| Edit.DocumentEndExtend |
|Rozpoczynanie dokumentu|**Ekran główny**| Edit.DocumentStart |
|Rozpoczynanie rozszerzania dokumentu|**Shift+Home**| Edit.DocumentStartExtend |
|Karta Wstawianie|**Tab**| Edit.InsertTab |
|Wiersz w dół|**Strzałka w dół**| Edit.LineDown |
|Rozszerzanie wiersza w dół|**Shift+Strzałka w górę**| Edit.LineDownExtend |
|Wiersz w górę|**Strzałka w górę**| Edit.LineUp |
|Rozszerzanie wiersza|**Shift+Strzałka w dół**| Edit.LineUpExtend |
|Przenoszenie kontrolki w dół|**Ctrl+strzałka w dół**| Edit.MoveControlDown |
|Przenoszenie kontrolki w lewo|**Ctrl+Strzałka w lewo**| Edit.MoveControlLeft |
|Przenoszenie kontrolki w prawo|**Ctrl+Strzałka w prawo**| Edit.MoveControlRight |
|Przenoszenie kontroli w górę|**Ctrl+Strzałka w górę**| Edit.MoveControlUp |
|Anulowanie wyboru|**Escape**| Edit.SelectionCancel |
|Kontrola rozmiaru w dół|**Ctrl+Shift+Strzałka w dół**| Edit.SizeControlDown |
|Kontrolka rozmiaru w lewo|**Ctrl+Shift+Strzałka w lewo**| Edit.SizeControlLeft |
|Prawo kontroli rozmiaru|**Ctrl+Shift+Strzałka w prawo**| Edit.SizeControlRight |
|Kontrola rozmiaru w górę|**Ctrl+Shift+Strzałka w górę**| Edit.SizeControlUp |
|Tabulator po lewej stronie|**Shift+Tab**| Edit.TabLeft |

### <a name="work-item-editor"></a>Edytor elementu roboczego

Skróty specyficzne dla tego kontekstu są:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Tworzenie kopii elementu roboczego|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|Odświeżanie elementu roboczego|**F5**| Edit.RefreshWorkItem |
|Nowy połączony element pracy|**Shift+Alt+L**| Team.NewLinkedWorkItem |

### <a name="work-item-query-view"></a>Widok zapytania o elementy robocze

Skróty specyficzne dla tego kontekstu są:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Tworzenie kopii elementu roboczego|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|Wcięcie|**Shift+Alt+Strzałka w prawo**| Edit.Indent |
|Wywęzłobienie|**Shift+Alt+Strzałka w lewo**| Edit.Outdent |
|Nowy połączony element pracy|**Shift+Alt+L**| Team.NewLinkedWorkItem |
|Odśwież|**F5**| Team.Refresh |
|przełączanie|**Shift+Alt+V**| Window.Toggle |

### <a name="work-item-results-view"></a>Widok wyników dotyczących elementu pracy

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Tworzenie kopii elementu roboczego|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|Wcięcie|**Shift+Alt+Strzałka w prawo**| Edit.Indent |
|Wywęzłobienie|**Shift+Alt+Strzałka w lewo**| Edit.Outdent |
|Goto next work item (Goto next work item)Goto next work item|**Shift+Alt+N**| Team.GotoNextWorkItem |
|Goto previous work item (Goto previous work item)|**Shift+Alt+P**| Team.GotoPreviousWorkItem |
|Nowy połączony element pracy|**Shift+Alt+L**| Team.NewLinkedWorkItem |
|Odśwież|**F5**| Team.Refresh |
|przełączanie|**Shift+Alt+V**| Window.Toggle |

### <a name="workflow-designer"></a>Projektant przepływów pracy

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Wyraz ukończony|**Ctrl+K, W**<br /><br /> lub<br /><br /> **Ctrl+K, Ctrl+W**<br /><br /> lub<br /><br /> **Ctrl+Spacja**<br /><br /> lub<br /><br /> **Alt+Strzałka w prawo**| Edit.CompleteWord |
|Zmniejszanie poziomu filtru|**Alt+,**| Edit.DecreaseFilterLevel |
|Zwiększanie poziomu filtru|**Alt +.**| Edit.IncreaseFilterLevel |
|Lista elementów członkowskich|**Ctrl+K, L**<br /><br /> lub<br /><br /> **Ctrl+K, Ctrl+L**<br /><br /> lub<br /><br /> **Ctrl+J**| Edit.ListMembers |
|Informacje o parametrach|**Ctrl+K, P**<br /><br /> lub<br /><br /> **Ctrl+K, Ctrl+P**<br /><br /> lub<br /><br /> **Ctrl+Shift+Spacebar**| Edit.ParameterInfo |
|Szybkie informacje|**Ctrl+K, I**<br /><br /> lub<br /><br /> **Ctrl+K, Ctrl+I**| Edit.QuickInfo |
|Zwiń|**Ctrl+E, Ctrl+C**<br /><br /> lub<br /><br /> **Ctrl+E, C**| WorkflowDesigner.Collapse |
|Zwiń wszystko|lub| WorkflowDesigner.CollapseAll |
|Połączenie węzłów|**Ctrl+E, Ctrl+F**<br /><br /> lub<br /><br /> **Ctrl+E, F**| WorkflowDesigner.ConnectNodes |
|Tworzenie zmiennej|**Ctrl+E, Ctrl+N**<br /><br /> lub<br /><br /> **Ctrl+E, N**| WorkflowDesigner.CreateVariable |
|Rozwiń wszystko|**Ctrl+E, Ctrl+X**<br /><br /> lub<br /><br /> **Ctrl+E, X**| WorkflowDesigner.ExpandAll |
|Rozwiń w miejscu|**Ctrl+E, Ctrl+E**<br /><br /> lub<br /><br /> **Ctrl+E, E**| WorkflowDesigner.ExpandInPlace |
|Przejdź do elementu nadrzędnego|**Ctrl+E, Ctrl+P**<br /><br /> lub<br /><br /> **Ctrl+E, P**| WorkflowDesigner.GoToParent |
|Przenieś fokus|**Ctrl+E, Ctrl+M**<br /><br /> lub<br /><br /> **Ctrl+E, M**| WorkflowDesigner.MoveFocus |
|Nawigowanie po projektancie|**Ctrl+Alt+F6**| WorkflowDesigner.NavigateThroughDesigner |
|Przywracanie|**Ctrl+E, Ctrl+R**<br /><br /> lub<br /><br /> **Ctrl+E, R**| WorkflowDesigner.Restore |
|Pokaż projektanta ukrywania argumentów|**Ctrl+E, Ctrl+A**<br /><br /> lub<br /><br /> **Ctrl+E, A**| WorkflowDesigner.ShowHideArgumentDesigner |
|Show hide imports designer (Pokaż projektant ukrywania importów)|**Ctrl+E, Ctrl+I**<br /><br /> lub<br /><br /> **Ctrl+E, I**| WorkflowDesigner.ShowHideImportsDesigner |
|Pokaż mapę ukrywania przeglądu|**Ctrl+E, Ctrl+O** (litera 'O')<br /><br /> lub<br /><br /> **Ctrl+E, O**| WorkflowDesigner.ShowHideOverviewMap |
|Pokaż ukrywanie projektanta zmiennych|**Ctrl+E, Ctrl+V**<br /><br /> lub<br /><br /> **Ctrl+E, V**| WorkflowDesigner.ShowHideVariableDesigner |
|Przełączanie zaznaczenia|**Ctrl+E, Ctrl+S**<br /><br /> lub<br /><br /> **Ctrl+E, S**| WorkflowDesigner.ToggleSelection |
|Powiększanie|**Ctrl+Num +**| WorkflowDesigner.ZoomIn |
|Pomniejszanie|**Ctrl+Num —**| WorkflowDesigner.ZoomOut |

### <a name="xaml-ui-designer"></a>Projektant języka XAML

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Dopasuj wszystko|**Ctrl+0** (zero)| Design.FitAll |
|Pokaż dojścia|**F9**| Design.ShowHandles |
|Powiększanie|**Ctrl+Alt+=**| Design.ZoomIn |
|Pomniejszanie|**Ctrl+Alt+-**| Design.ZoomOut |
|Opcje projektanta|**Ctrl+Shift+;**|
|Edytowanie tekstu|**F2**| Format.EditText |
|Wszystko|**Ctrl+Shift+R**| Format.ResetLayout.All |
|Uruchamianie kodu projektu|**Ctrl+F9**|
|Ukryj (tylko blend)|**Ctrl+H**| Timeline.Hide (tylko blend) |
|Blokada (tylko blend)|**Ctrl+L**| Timeline.Lock (tylko blend) |
|Pokaż (tylko blend)|**Ctrl+Shift+H**| Timeline.Show (tylko blend) |
|Odblokowywanie (tylko blend)|**Ctrl+Shift+L**| Timeline.Unlock (tylko blend) |
|Lewy ruch brzegowy w lewo|**Ctrl+Shift+,**| View.EdgeLeftMoveLeft |
|Przesuwanie krawędzi w lewo w prawo|**Ctrl+Shift+.**| View.EdgeLeftMoveRight |
|Przesuwanie krawędzi w lewo w prawo|**Ctrl+Shift+Alt+,**| View.EdgeRightMoveLeft |
|Prawe przesuwanie krawędzi w prawo|**Ctrl+Shift+Alt+.**| View.EdgeRightMoveRight |
|Menu Pokaż znacznik właściwości|**Ctrl+Spacja**| View.ShowPropertyMarkerMenu |

### <a name="xml-text-editor"></a>Edytor (tekstu) XML

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Uruchamianie debugowania XSLT|**Alt+F5**| XML.StartXSLTDebugging |
|Uruchamianie kodu XSLT bez debugowania|**Ctrl+Alt+F5**| XML.StartXSLTWithoutDebugging |

### <a name="xml-schema-designer"></a>Projektant schematu XML

Skróty specyficzne dla tego kontekstu to:


|Polecenia|Skróty klawiaturowe|Identyfikator polecenia|
|-|-|-|
|Od dołu do góry|**Alt+Strzałka w górę**| GraphView.BottomtoTop |
|Od lewej do prawej|**Alt+Strzałka w prawo**| GraphView.LefttoRight |
|Od prawej do lewej|**Alt+Strzałka w lewo**| GraphView.RighttoLeft |
|Od góry do dołu|**Alt+Strzałka w dół**| GraphView.ToptoBottom |
|Usuwanie z obszaru roboczego|**Usuwanie**| OtherContextMenus.GraphView.RemovefromWorkspace |
|Wyświetlanie widoku modelu zawartości|**Ctrl+2**| XsdDesigner.ShowContentModelView |
|Wyświetlanie widoku wykresu|**Ctrl+3**| XsdDesigner.ShowGraphView |
|Wyświetlanie widoku startowego|**Ctrl+1**| XsdDesigner.ShowStartView |

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](reference/visual-studio-commands.md)
