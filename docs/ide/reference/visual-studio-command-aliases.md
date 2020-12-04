---
title: Aliasy poleceń
description: Dowiedz się, jak używać aliasów poleceń do wpisywania mniejszej liczby znaków, gdy chcesz wykonać polecenie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- aliases, Visual Studio commands
- Visual Studio, commands
- predefined command aliases
- commands, aliases
- Visual Studio commands
- pre-defined command aliases
- command aliases
ms.assetid: de8bb378-8c1c-4087-a9a5-537fa8314c19
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9dda564939652a09b64fec65747ca14d1315b3f1
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561074"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio — Aliasy poleceń

Aliasy poleceń umożliwiają wpisanie mniejszej liczby znaków, gdy chcesz wykonać polecenie. Wpisz aliasy w polu **Znajdź/polecenie** lub w oknie **wiersza polecenia** . Na przykład zamiast wprowadzania `>File.OpenFile` do wyświetlania okna dialogowego **Otwórz plik** można użyć wstępnie zdefiniowanego aliasu `>of` .

Wpisz `alias` w oknie **polecenia** , aby wyświetlić listę bieżących aliasów i ich definicje. Wpisz, `>cls` Aby wyczyścić zawartość okna **poleceń** . Jeśli chcesz zobaczyć alias dla określonego polecenia, wpisz `alias <command name>` .

Można łatwo utworzyć własny alias dla jednego z poleceń programu Visual Studio (z argumentami lub bez nich). Na przykład składnia aliasu `File.NewFile MyFile.txt` to `alias MyAlias File.NewFile MyFile.txt` . Jeden z aliasów można usunąć za pomocą `alias <alias name> /delete`

Poniższa tabela zawiera listę wstępnie zdefiniowanych aliasów poleceń programu Visual Studio. Niektóre nazwy poleceń mają więcej niż jeden wstępnie zdefiniowany alias. Kliknij linki do poniższych nazw poleceń, aby wyświetlić szczegółowe tematy objaśniające poprawną składnię, argumenty i przełączniki dla tych poleceń.

|Nazwa polecenia|Alias|Pełna nazwa|
|------------------|-----------|-------------------|
|[Print — polecenie](../../ide/reference/print-command.md)|?|Debuguj. Print|
|[Szybkie czujka — polecenie](../../ide/reference/quick-watch-command.md)|??|Debuguj. QuickWatch|
|Dodaj nowy projekt|Addproj|Plik. AddNewProject|
|[Alias — polecenie](../../ide/reference/alias-command.md)|Alias|Tools. alias|
|okno zmiennych automatycznych|Automatyczne|Debug.Autos|
|Okno punktów przerwania|czarnej listy|Debug.Breakpoints|
|Przełącz punkt przerwania|BP|Debuguj. Togglebreakpoint —|
|Stos wywołań, okno|Stosu wywołań|Debug.CallStack|
|Wyczyść zakładki|ClearBook|Edit.ClearBookmarks|
|Zamknij|Zamknij|Plik. Zamknij|
|Zamknij wszystkie dokumenty|CloseAll|Window. CloseAllDocuments|
|Wyczyść wszystko|ze|Edytuj. ClearAll|
|Tryb polecenia|cmd|View.CommandWindow|
|Wyświetl kod|kod|View.ViewCode|
|[List Memory — polecenie](../../ide/reference/list-memory-command.md)|d|Debuguj. ListMemory —|
|[Wyświetl pamięć polecenia](../../ide/reference/list-memory-command.md) jako ANSI|da|Debug. ListMemory —/ANSI|
|[Lista One-Byte format polecenia pamięci](../../ide/reference/list-memory-command.md)|bazy danych|Debug. ListMemory —/format: OneByte|
|[Wyświetl listę poleceń](../../ide/reference/list-memory-command.md) jako ANSI w formacie Four-Byte|DC|Debug. ListMemory —/format: FourBytes/ANSI|
|[Lista Four-Byte format polecenia pamięci](../../ide/reference/list-memory-command.md)|dd|Debug. ListMemory —/format: FourBytes|
|Usuń do BOL|DelBOL|Edytuj. DeleteToBOL|
|Usuń do EOL|DelEOL|Edytuj. DeleteToEOL|
|Usuń odstępy w poziomie|DelHSp|Edytuj. DeleteHorizontalWhitespace|
|Projektant widoków|projektant|View.ViewDesigner|
|[List Memory — polecenie](../../ide/reference/list-memory-command.md) Format zmiennoprzecinkowy|DF|Debug. ListMemory —/format: float|
|Dezasemblacja, okno|DISASM|Debug.Disassembly|
|[Lista Eight-Byte format polecenia pamięci](../../ide/reference/list-memory-command.md)|elemencie DQ|Debug. ListMemory —/format: EightBytes|
|[Wyświetl pamięć polecenia](../../ide/reference/list-memory-command.md) jako Unicode|du|Debug. ListMemory —/Unicode|
|[Polecenie szacowania instrukcji](../../ide/reference/evaluate-statement-command.md)|powiadomienie|Debuguj. EvaluateStatement|
|Zakończ|Zakończ|File.Exit|
|Formatowanie zaznaczenia|format|Edit.FormatSelection|
|Pełny ekran|Pełnoekranowy|View.FullScreen|
|[Uruchom polecenie](../../ide/reference/start-command.md)|g|Debug.Start|
|[Przejdź do — polecenie](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|Przejdź do nawiasu klamrowego|GotoBrace|Edit.GotoBrace|
|F1Help|Pomoc|Help.F1Help|
|Tryb natychmiastowy|immed|Tools. immediatemode|
|Wstaw plik jako tekst|InsertFile|Edytuj. InsertFileAsText|
|[Listing stosu wywołań — polecenie](../../ide/reference/list-call-stack-command.md)|bazy|Debuguj. ListCallStack|
|Zmień na małe litery|Lcase|Edit.MakeLowercase|
|Wytnij wiersz|LineCut|Edit.LineCut|
|Usuń wiersz|LineDel|Edit.LineDelete|
|Lista składników|Wyświetlanie członków|Edit.ListMembers|
|okno zmiennych lokalnych|Zmienne lokalne|Debug.Locals|
|[Polecenie dziennika danych wyjściowych okna polecenia](../../ide/reference/log-command-window-output-command.md)|Dziennik|Tools. LogCommandWindowOutput|
|Tryb oznaczania okna polecenia|znacznik|Tools. CommandWindowMarkMode|
|okno pamięci|Memory1 pamięci|Debug.Memory1|
|Okno pamięci 2|Memory2|Debug.Memory2|
|Okno pamięci 3|Memory3|Debug.Memory3|
|Okno pamięci 4|Memory4|Debug.Memory4|
|[Set podstawy — polecenie](../../ide/reference/set-radix-command.md)|n|Debuguj. SetRadix|
|[ShowWebBrowser — — polecenie](../../ide/reference/showwebbrowser-command.md)|Nawigacja nawigacji|Widok. ShowWebBrowser —|
|Następna zakładka|NextBook|Edit.NextBookmark|
|[Nowy plik — polecenie](../../ide/reference/new-file-command.md)|oznaczona|File.NewFile|
|Nowy projekt|np. NewProj|File.NewProject|
|[Otwórz plik — polecenie](../../ide/reference/open-file-command.md)|z otwartego|File.OpenFile|
|[Otwórz projekt — polecenie](../../ide/reference/open-project-command.md)|op|File.OpenProject|
|Zwiń do definicji/Zatrzymaj tworzenie konspektu|OutlineDefs StopOutlining|Edytuj. CollapseToDefinitions|
|Przekrocz nad|p|Debug.StepOver|
|Informacje o parametrach|ParamInfo|Edit.ParameterInfo|
|Wyjdź|pr|Debug.StepOut|
|Poprzednia zakładka|PrevBook|Edit.PreviousBookmark|
|Drukowanie pliku|drukowanie|File.Print|
|Okno Właściwości|props|View.PropertiesWindow|
|Stop|q|Debug.StopDebugging|
|Ponów|ponawia|Edit.Redo|
|Okno rejestrów|rejestry|Debug.Registers|
|Uruchom do kursora|RTC|Debug.RunToCursor|
|Zapisz zaznaczone elementy|zapisywanie|File.SaveSelectedItems|
|Zapisz wszystko|SaveAll|File.SaveAll|
|Zapisz jako|Przełącznik|Plik. SaveSelectedItemsAs|
|[Shell — polecenie](../../ide/reference/shell-command.md)|powłoka|Tools. Shell|
|Zatrzymaj Znajdowanie w plikach|StopFind|Edit. FindInFiles/Stop|
|Zakotwiczenie wymiany|SwapAnchor|Edit.SwapAnchor|
|Wkrocz do|t|Debug.StepInto|
|Na tabulatory zaznaczenie|tabify — formatowanie|Edytuj. TabifySelection|
|Okno listy zadań|TaskList|View.TaskList|
|Okno wątków|Wątki|Debug.Threads|
|Kafelek w poziomie|TileH|Window. TileHorizontally|
|Sąsiadująco w pionie|TileV|Window. TileVertically|
|Przełącz zakładkę|ToggleBook|Edit.ToggleBookmark|
|Okno przybornika|przybornik|View.Toolbox|
|[List demontażu — polecenie](../../ide/reference/list-disassembly-command.md)|u|Debuguj. ListDisassembly|
|Zmień wielkie litery|Ucase|Edit.MakeUppercase|
|Cofnij|Anulowanie|Edit.Undo|
|Tabulatory na zaznaczenie|Tabulatory na|Edytuj. UntabifySelection|
|okno czujki|Zegarek|Debuguj. WatchN|
|Przełącz Zawijanie wierszy|WordWrap|Edit.ToggleWordWrap|
|Wyświetlanie listy procesów|&#124;|Debuguj. ListProcesses|
|[Lista wątków — polecenie](../../ide/reference/list-threads-command.md)|~ ~ * k ~ \* KB|Debug. Listthreads — Debug. ListTheads/AllThreads|

## <a name="see-also"></a>Zobacz także

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
