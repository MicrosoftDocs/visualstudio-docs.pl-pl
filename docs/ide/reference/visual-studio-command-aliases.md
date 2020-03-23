---
title: Aliasy poleceń
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
ms.openlocfilehash: b420644672309371ab61f1499e22d4745c69c569
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596414"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio — Aliasy poleceń

Aliasy poleceń umożliwiają wpisywać mniejszą liczbę znaków, gdy chcesz wykonać polecenie. Aliasy należy wprowadzić w polu **Znajdź/Pouczaj** lub **po wierszu Polecenia.** Na przykład zamiast wprowadzać `>File.OpenFile` do wyświetlania okna dialogowego **Otwórz plik,** można `>of`użyć wstępnie zdefiniowanego aliasu .

Wpisz `alias` w oknie **Polecenia,** aby wyświetlić listę bieżących aliasów i ich definicji. Wpisz, `>cls` aby wyczyścić zawartość okna **Polecenia.** Jeśli chcesz wyświetlić alias określonego polecenia, `alias <command name>`wpisz .

Można łatwo utworzyć własny alias dla jednego z poleceń programu Visual Studio (z argumentami lub bez). Na przykład składnia aliasingu `File.NewFile MyFile.txt` `alias MyAlias File.NewFile MyFile.txt`to . Możesz usunąć jeden ze swoich aliasów za pomocą`alias <alias name> /delete`

Poniższa tabela zawiera listę wstępnie zdefiniowanych aliasów poleceń programu Visual Studio. Niektóre nazwy poleceń mają więcej niż jeden wstępnie zdefiniowany alias. Kliknij łącza do poniższych nazw poleceń, aby wyświetlić szczegółowe tematy wyjaśniające poprawną składnię, argumenty i przełączniki dla tych poleceń.

|Nazwa polecenia|Alias|Pełna nazwa|
|------------------|-----------|-------------------|
|[Print — Polecenie](../../ide/reference/print-command.md)|?|Debug.Drukuj|
|[Szybka czujka — Polecenie](../../ide/reference/quick-watch-command.md)|??|Debug.Quickwatch|
|Dodaj nowy projekt|DodajProj|Plik.AddNewProject|
|[Alias — Polecenie](../../ide/reference/alias-command.md)|Alias|Narzędzia.Alias|
|okno zmiennych automatycznych|Autos|Debug.Autos|
|Okno punktów przerwania|Bl|Debug.Breakpoints|
|Przełączanie punktu przerwania|Bp|Debug.ToggleBreakPoint|
|Stos wywołań, okno|Callstack|Debug.CallStack|
|Wyczyść zakładki|Książka ClearBook|Edit.ClearBookmarks|
|Zamykanie|Zamykanie|Plik.Zamknij|
|Zamknij wszystkie dokumenty|ZamknijWszystki|Window.CloseAllDocuments|
|Wyczyść wszystko|Cls|Edit.ClearWszystko|
|Tryb polecenia|cmd|View.CommandWindow|
|Wyświetl kod|kod|View.ViewCode|
|[Lista pamięci — Polecenie](../../ide/reference/list-memory-command.md)|d|Debug.ListMemory|
|[Polecenie lista pamięci](../../ide/reference/list-memory-command.md) jako ANSI|da|Debug.ListMemory /Ansi|
|[Polecenie Pamięć listy](../../ide/reference/list-memory-command.md) Format jedno bajtowy|bazy danych|Debug.ListMemory /Format:OneByte|
|[Polecenie Lista pamięci](../../ide/reference/list-memory-command.md) jako ANSI w formacie cztero bajtowym|Dc|Debug.ListMemory /Format:FourBytes /Ansi|
|[Polecenie Pamięć listy](../../ide/reference/list-memory-command.md) Format cztero bajtowy|dd|Debug.ListMemory /Format:FourBytes|
|Usuń do BOL|DelBOL ( DelBOL )|Edit.DeleteToBOL|
|Usuń do EOL|Okręg wyborczy DelEOL|Edit.DeleteToEOL|
|Usuń poziome odstępy|DelHSp ( DelHSp )|Edit.DeleteHorizontalWhitespace|
|Projektant widoków|projektant|View.ViewDesigner|
|[Polecenie Pamięć listy](../../ide/reference/list-memory-command.md) Format float|Df|Debug.ListMemory/Format:Float|
|Dezasemblacja, okno|Disasm|Debug.Disassembly|
|[Polecenie Pamięć listy](../../ide/reference/list-memory-command.md) Format ośmiokątowy|Dq|Debug.ListMemory /Format:EightBytes|
|[Polecenie Lista pamięci](../../ide/reference/list-memory-command.md) jako Unicode|Du|Debug.ListMemory /Unicode|
|[Polecenie Oceń instrukcję](../../ide/reference/evaluate-statement-command.md)|Eval|Debug.EvaluateStatement (Debug.EvaluateStatement)|
|Zakończ|Zakończ|File.Exit|
|Formatowanie zaznaczenia|format|Edit.FormatSelection|
|Pełny ekran|Pełny ekran|View.FullScreen|
|[Uruchomienie — Polecenie](../../ide/reference/start-command.md)|g|Debug.Start|
|[Przejdź do — Polecenie](../../ide/reference/go-to-command.md)|GotoLn (GotoLn)|Edit.GoTo|
|Przejdź do Klamra|GotoBrace (GotoBrace)|Edit.GotoBrace|
|F1Help (pomoc w 1.|Pomoc|Help.F1Help|
|Tryb natychmiastowy|immed|Narzędzia.ImmediateMode|
|Wstawianie pliku jako tekstu|Plik Wstawiania|Tekst edit.insertFileAsText|
|[Lista stosu wywołań — Polecenie](../../ide/reference/list-call-stack-command.md)|Kb|Debug.ListCallStack (Debug.ListCallStack)|
|Zrób dolną obudowę|Lcase|Edit.MakeLowercase|
|Linia cięcia|LiniaCut|Edit.LineCut|
|Usuń wiersz|Linia|Edit.LineDelete|
|Lista składników|Członkowie listy|Edit.ListMembers|
|okno zmiennych lokalnych|Mieszkańców|Debug.Locals|
|[Zapisuj dane wyjściowe okna Polecenie — Polecenie](../../ide/reference/log-command-window-output-command.md)|Log|Narzędzia.LogCommandWindowOutput|
|Tryb oznaczenia okna polecenia|Mark|Narzędzia.CommandWindowMarkMode|
|okno pamięci|Pamięć pamięci1|Debug.Memory1|
|Okno pamięci 2|Pamięć2|Debug.Memory2|
|Okno pamięci 3|Pamięć3|Debug.Memory3|
|Okno pamięci 4|Pamięć4|Debug.Memory4|
|[Ustaw Radix — Polecenie](../../ide/reference/set-radix-command.md)|n|Debug.SetRadix|
|[ShowWebBrowser — Polecenie](../../ide/reference/showwebbrowser-command.md)|nawigacja nawiga|View.ShowWebWiększacz|
|Następna zakładka|Następna książka|Edit.NextBookmark|
|[Nowy plik — Polecenie](../../ide/reference/new-file-command.md)|Nf|File.NewFile|
|Nowy projekt|np NewProj|File.NewProject|
|[Otwórz plik — Polecenie](../../ide/reference/open-file-command.md)|z Open|File.OpenFile|
|[Otwórz projekt — Polecenie](../../ide/reference/open-project-command.md)|Op|File.OpenProject|
|Zwiń do definicji/Zatrzymaj konspekt|ZarysDefs StopOutlining|Edit.CollapseToDefinitions|
|Krok nad|p|Debug.StepOver|
|Informacje o parametrach|ParamInfo ( ParamInfo )|Edit.ParameterInfo|
|Wyjdź|Pr|Debug.StepOut|
|Poprzednia zakładka|Książka wstępna|Edit.PreviousBookmark|
|Drukowanie pliku|drukowanie|File.Print|
|Okno Właściwości|Rekwizyty|View.PropertiesWindow|
|Stop|q|Debug.StopDebugging|
|Ponów|Ponów|Edit.Redo|
|Okno rejestrów|rejestry|Debug.Registers|
|Uruchom do kursora|Rtc|Debug.RunToCursor|
|Zapisywanie zaznaczonych elementów|zapisywanie|File.SaveSelectedItems|
|Zapisz wszystko|SaveAll (Oszczędzajwszy)|File.SaveAll|
|Zapisz jako|Saveas|Plik.SaveSelectedItemsAs|
|[Shell — Polecenie](../../ide/reference/shell-command.md)|powłoka|Narzędzia.Powłoka|
|Zatrzymaj znajdowanie w plikach|Zatrzymaj|Edit.FindInFiles /stop|
|Zamień kotwicę|SwapAnchor|Edit.SwapAnchor|
|Wejdź do|t|Debug.StepInto|
|Wybór tabify|tabify — formatowanie|Wybór pliku Edit.TabifySelection|
|Okno Lista zadań|Tasklist|View.TaskList|
|Okno wątków|Wątki|Debug.Threads|
|Kafelek w poziomie|PłytkaH|Okno.TileHorizontally|
|Płytka pionowo|PłytkaV|Window.TileWersycyjnie|
|Przełączanie zakładki|PrzełączanieBook|Edit.ToggleBookmark|
|Okno przybornika|przybornik|View.Toolbox|
|[Lista dezasemblacji — Polecenie](../../ide/reference/list-disassembly-command.md)|u|Debug.ListZdjęcie|
|Wielkie litery|Ucase ( ucase )|Edit.MakeUppercase|
|Cofanie|Cofnij|Edit.Undo|
|Ujednolicenie zaznaczenia|Untabify|Edit.UntabifySelection|
|okno czujki|Obejrzyj|Debug.WatchN|
|Przełączanie zawijanie wyrazów|WordWrap|Edit.ToggleWordWrap|
|Lista procesów|&#124;|Debug.ListProcesses|
|[Lista wątków — Polecenie](../../ide/reference/list-threads-command.md)|~ ~*k\*~ kb|Debug.ListThreads Debug.ListTheads /AllThreads|

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
