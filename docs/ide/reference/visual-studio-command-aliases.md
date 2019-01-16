---
title: Aliasy poleceń
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae0064052fa2f042eec218f3653f4b43fa24ba0a
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "53878890"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio — Aliasy poleceń

Aliasy poleceń pozwalają typu mniej znaków, gdy chcesz wykonać polecenie. Wprowadź aliasów do **Find/Command** pole lub **polecenia** okna. Na przykład, zamiast wprowadzać `>File.OpenFile` do wyświetlenia **Otwórz plik** okno dialogowe, można użyć wstępnie zdefiniowanych aliasów `>of`.

Typ `alias` w **polecenia** okno, aby wyświetlić listę bieżących aliasów i ich definicje. Typ `>cls` aby wyczyścić zawartość **polecenia** okna. Jeśli chcesz zobaczyć aliasu dla określonego polecenia, wpisz `alias <command name>`.

Można łatwo utworzyć aliasu dla jednego z poleceń programu Visual Studio (z lub bez argumentów). Na przykład składnia aliasów `File.NewFile MyFile.txt` jest `alias MyAlias File.NewFile MyFile.txt`. Można usunąć jeden z aliasy `alias <alias name> /delete`

Poniższa tabela zawiera listę wstępnie zdefiniowane aliasy poleceń programu Visual Studio. Niektóre nazwy polecenia mają więcej niż jeden alias wstępnie zdefiniowane. Kliknij linki poniżej, aby wyświetlić szczegółowe tematy, które wyjaśniają poprawnej składni, argumentów i przełączników dla tych poleceń, nazwy polecenia.

|Nazwa polecenia|Alias|Pełna nazwa|
|------------------|-----------|-------------------|
|[Drukuj, polecenie](../../ide/reference/print-command.md)|?|Debug.Print|
|[Szybka czujka, polecenie](../../ide/reference/quick-watch-command.md)|??|Debug.quickwatch —|
|Dodaj nowy projekt|AddProj|File.AddNewProject|
|[Alias, polecenie](../../ide/reference/alias-command.md)|Alias|Tools.alias —|
|okno zmiennych automatycznych|Automatyczne|Debug.Autos|
|Okno punktów przerwania|reklamy BL|Debug.Breakpoints|
|Przełącz punkt przerwania|najlepszych praktyk w zakresie|Debug.togglebreakpoint —|
|Stos wywołań, okno|Stos wywołań|Debug.CallStack|
|Wyczyść zakładki|ClearBook|Edit.ClearBookmarks|
|Zamknięcie|Zamknięcie|File.Close|
|Zamknij wszystkie dokumenty|Closeall —|Window.CloseAllDocuments|
|Wyczyść wszystko|ze specyfikacją CLS|Edit.ClearAll|
|Tryb poleceń|cmd|View.CommandWindow|
|Wyświetl kod|kod|View.ViewCode|
|[Lista pamięci, polecenie](../../ide/reference/list-memory-command.md)|d|Debug.listmemory —|
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) jako ANSI|da|Debug.listmemory — /Ansi|
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) jednobajtowych formatu|bazy danych|Debug.listmemory — /Format:OneByte|
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) jako ANSI za pomocą 4-bajtowych formatowania|Kontroler domeny|Debug.listmemory — /Format:FourBytes /Ansi|
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) format czwartego bajtu|dd|Debug.listmemory — /Format:FourBytes|
|Usuń do BOL|DelBOL|Edit.DeleteToBOL|
|Usuń do EOL|DelEOL|Edit.DeleteToEOL|
|Usuń poziome odstępy|DelHSp|Edit.DeleteHorizontalWhitespace|
|Pokaż projektanta|projektant|View.ViewDesigner|
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) formacie zmiennoprzecinkowych|DF|Debug.ListMemory/Format:Float|
|Dezasemblacja, okno|disasm|Debug.Disassembly|
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) format 8-bajtową|dq|Debug.listmemory — /Format:EightBytes|
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) jako Unicode|jednostka bazy danych|Debug.listmemory — /Unicode|
|[Oceń instrukcję, polecenie](../../ide/reference/evaluate-statement-command.md)|Eval|Debug.evaluatestatement —|
|Zakończ|Zakończ|File.Exit|
|Formatuj zaznaczenie|format|Edit.FormatSelection|
|Pełny ekran|Pełny ekran|View.FullScreen|
|[Uruchomienie, polecenie](../../ide/reference/start-command.md)|g|Debug.Start|
|[Przejdź do, polecenie](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|Przejdź do nawiasu klamrowego|GotoBrace|Edit.GotoBrace|
|F1Help|Pomoc|Help.F1Help|
|Tryb natychmiastowy|natychmiast|Tools.ImmediateMode|
|Wstaw plik jako tekst|InsertFile|Edit.InsertFileAsText|
|[Lista stosu wywołań, polecenie](../../ide/reference/list-call-stack-command.md)|KB|Debug.listcallstack —|
|Zmień na małe litery|LCase|Edit.MakeLowercase|
|Wytnij wiersz|LineCut|Edit.LineCut|
|Usuń wiersz|LineDel|Edit.LineDelete|
|Lista składników|Wyświetlanie członków|Edit.ListMembers|
|okno zmiennych lokalnych|Zmienne lokalne|Debug.Locals|
|[Zapisuj dane wyjściowe okna Polecenie, polecenie](../../ide/reference/log-command-window-output-command.md)|Log|Tools.LogCommandWindowOutput|
|Tryb oznaczania w oknie polecenia|znacznik|Tools.CommandWindowMarkMode|
|okno pamięci|Memory1 pamięci|Debug.Memory1|
|Okno pamięci 2|Memory2|Debug.Memory2|
|Okno pamięci 3|Pamięci3|Debug.Memory3|
|Okno pamięci 4|Memory4|Debug.Memory4|
|[Ustaw Radix, polecenie](../../ide/reference/set-radix-command.md)|n|Debug.setradix —|
|[ShowWebBrowser, polecenie](../../ide/reference/showwebbrowser-command.md)|Przejdź w okienku nawigacji|View.showwebbrowser —|
|Następna zakładka|NextBook|Edit.NextBookmark|
|[Nowy plik, polecenie](../../ide/reference/new-file-command.md)|NF|File.NewFile|
|Nowy projekt|potoki NewProj|File.NewProject|
|[Otwórz plik, polecenie](../../ide/reference/open-file-command.md)|jest on otwarty|File.OpenFile|
|[Otwórz projekt, polecenie](../../ide/reference/open-project-command.md)|OP|File.OpenProject|
|Zwiń do definicji/Zatrzymaj tworzenie konspektu|OutlineDefs StopOutlining|Edit.CollapseToDefinitions|
|Przekrocz nad|p|Debug.StepOver|
|Informacje o parametrach|ParamInfo|Edit.ParameterInfo|
|Wyjdź|żądania ściągnięcia|Debug.StepOut|
|Poprzednia zakładka|PrevBook|Edit.PreviousBookmark|
|Drukuj plik|Drukuj|File.Print|
|Okno Właściwości|właściwości|View.PropertiesWindow|
|Zatrzymywanie|q|Debug.StopDebugging|
|Wykonaj ponownie|Wykonaj ponownie|Edit.Redo|
|Okno rejestrów|rejestry|Debug.Registers|
|Uruchom do kursora|RTC|Debug.RunToCursor|
|Zapisz wybrane elementy|Zapisz|File.SaveSelectedItems|
|Zapisz wszystko|SaveAll|File.SaveAll|
|Zapisz jako|Zapisz jako|File.SaveSelectedItemsAs|
|[Powłoka, polecenie](../../ide/reference/shell-command.md)|powłoka|Tools.Shell —|
|Zatrzymaj Znajdź w plikach|StopFind|Edit.findinfiles — / Stop|
|Zamień zakotwiczenie|SwapAnchor|Edit.SwapAnchor|
|Wkrocz|t|Debug.StepInto|
|Zmień spacje na tabulatory zaznaczenia|tabify — formatowanie|Edit.TabifySelection|
|Tasklist okna|TaskList|View.TaskList|
|Okno wątków|Wątki|Debug.Threads|
|Sąsiadująco w poziomie|TileH|Window.TileHorizontally|
|Sąsiadująco w pionie|TileV|Window.TileVertically|
|Przełącz zakładkę|ToggleBook|Edit.ToggleBookmark|
|Okno przybornika|przybornik|View.Toolbox|
|[Lista dezasemblacji, polecenie](../../ide/reference/list-disassembly-command.md)|u|Debug.listdisassembly —|
|Zmień litery na wielkie|UCase|Edit.MakeUppercase|
|Cofnij|Cofnij|Edit.Undo|
|Zmień tabulatory na spacje zaznaczenia|Zmień tabulatory na spacje|Edit.UntabifySelection|
|okno czujki|Wyrażenie kontrolne|Debug.WatchN|
|Przełącz zawijanie wierszy|WordWrap|Edit.ToggleWordWrap|
|Wyświetl procesy|&#124;|Debug.ListProcesses|
|[Lista wątków, polecenie](../../ide/reference/list-threads-command.md)|~ ~ * k ~\*kb|Debug.listthreads — Debug.ListTheads /AllThreads|

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)