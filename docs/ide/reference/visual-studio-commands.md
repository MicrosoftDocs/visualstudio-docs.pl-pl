---
title: Polecenia
description: Dowiedz się więcej na temat różnych poleceń, do których masz dostęp w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7928c03e52e4a72fb354bd7202e041ec2264fcd6
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560957"
---
# <a name="visual-studio-commands"></a>Visual Studio — Polecenia

Polecenia programu Visual Studio można wprowadzać w oknie **poleceń** , oknie **bezpośrednim** lub w polu **Znajdź/polecenie** . W każdym przypadku znak większości ( `>` ) wskazuje, że polecenie, a nie operację wyszukiwania lub debugowania, następuje poniżej.

Pełną listę poleceń i ich składnię można znaleźć na stronie **Klawiatura** w obszarze **Narzędzia**  >  **Opcje**  >  **środowiska**.

W zlokalizowanych wersjach środowiska IDE nazwy poleceń można wprowadzać w języku macierzystym IDE lub w języku angielskim. Na przykład można wpisać albo `File.NewFile` `Fichier.NouveauFichier` w IDE, aby wykonać to samo polecenie.

Wiele poleceń ma aliasy. Aby uzyskać listę aliasów poleceń, zobacz [Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md). Aby zapoznać się z skrótami klawiaturowymi poleceń, zobacz [domyślne skróty klawiaturowe w programie Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md).

## <a name="escape-character"></a>Znak ucieczki

Znak ucieczki dla poleceń programu Visual Studio jest karetką (^). Znak ucieczki oznacza, że znak bezpośrednio po nim jest interpretowany dosłownie, a nie jako znak kontrolny. Można go użyć do osadzenia prostych cudzysłowów ("), spacji, ukośników wiodących, karetki lub innych znaków literału w wartości parametru lub przełącznika, z wyjątkiem nazw przełączników. Na przykład:

```
>Edit.Find ^^t /regex
```

Daszek działa tak samo, niezależnie od tego, czy znajduje się wewnątrz, czy poza cudzysłowem. Jeśli karetka jest ostatnim znakiem w wierszu, zostanie zignorowana.

## <a name="commands-with-arguments"></a>Polecenia z argumentami

Następujące polecenia przyjmują argumenty lub przełączniki:

| Nazwa polecenia | Opis |
| - | - |
| [Dodaj istniejący element](../../ide/reference/add-existing-item-command.md) | Dodaje istniejący plik do bieżącego rozwiązania i otwiera go. |
| [Dodaj istniejący projekt](../../ide/reference/add-existing-project-command.md) | Dodaje istniejący projekt do bieżącego rozwiązania. |
| [Dodaj nowy element](../../ide/reference/add-new-item-command.md) | Dodaje nowy element rozwiązania, taki jak. htm, CSS, txt lub FRAMESET do bieżącego rozwiązania i otwiera go. |
| [Użyj](../../ide/reference/alias-command.md) | Tworzy nowy alias dla kompletnego polecenia, kompletne polecenie i argumenty, a nawet inny alias. |
| [Oceń instrukcję](../../ide/reference/evaluate-statement-command.md) | Oblicza i wyświetla daną instrukcję. |
| [Wyświetlić](../../ide/reference/find-command.md) | Przeszukuje pliki za pomocą podzestawu opcji dostępnych w kontrolce **Znajdowanie i zamienianie** . |
| [Znajdź w plikach](../../ide/reference/find-in-files-command.md) | Przeszukuje pliki za pomocą podzestawu opcji dostępnych na stronie [Znajdź w plikach](../../ide/find-in-files.md). |
| [Przejdź do](../../ide/reference/go-to-command.md) | Przenosi kursor do określonego wiersza. |
| [Wyświetl stos wywołań](../../ide/reference/list-call-stack-command.md) | Wyświetla bieżący stos wywołań. |
| [Demontaż listy](../../ide/reference/list-disassembly-command.md) | Rozpoczyna proces debugowania i pozwala określić, jak błędy są obsługiwane. |
| [Wyświetl pamięć](../../ide/reference/list-memory-command.md) | Wyświetla zawartość określonego zakresu pamięci. |
| [Lista modułów](../../ide/reference/list-modules-command.md) | Wyświetla listę modułów dla bieżącego procesu. |
| [Lista rejestrów](../../ide/reference/list-registers-command.md) | Wyświetla listę rejestrów. |
| [Źródło listy](../../ide/reference/list-source-command.md) | Wyświetla określone wiersze kodu źródłowego. |
| [Wyświetl wątki](../../ide/reference/list-threads-command.md) | Wyświetla listę wątków w bieżącym programie. |
| [Dane wyjściowe okna polecenia dziennika](../../ide/reference/log-command-window-output-command.md) | Kopiuje wszystkie dane wejściowe i wyjściowe z okno Polecenie do pliku. |
| [Nowy plik](../../ide/reference/new-file-command.md) | Tworzy nowy plik i dodaje go do aktualnie wybranego projektu. |
| [Otwórz plik](../../ide/reference/open-file-command.md) | Otwiera istniejący plik i umożliwia określenie edytora. |
| [Otwórz projekt](../../ide/reference/open-project-command.md) | Otwiera istniejący projekt i umożliwia dodanie projektu do bieżącego rozwiązania. |
| [Drukuj](../../ide/reference/print-command.md) | Oblicza wyrażenie i wyświetla wyniki lub określony tekst. |
| [Szybkie czujka — polecenie](../../ide/reference/quick-watch-command.md) | Wyświetla wybrany lub określony tekst w polu **wyrażenie** w oknie dialogowym **szybkie czujka** . |
| [Stępować](../../ide/reference/replace-command.md) | Zamienia tekst w plikach za pomocą podzestawu opcji dostępnych w kontrolce **Znajdowanie i zamienianie** . |
| [Zastąp w plikach](../../ide/reference/replace-in-files-command.md) | Zamienia tekst w plikach za pomocą podzestawu opcji dostępnych w [Zamień w plikach](../../ide/replace-in-files.md). |
| [Ustaw bieżącą ramkę stosu](../../ide/reference/set-current-stack-frame-command.md) | Umożliwia wyświetlenie określonej ramki stosu. |
| [Ustaw bieżący wątek](../../ide/reference/set-current-thread-command.md) | Umożliwia wyświetlenie określonego wątku. |
| [Ustaw podstawy](../../ide/reference/set-radix-command.md) | Określa liczbę bajtów do wyświetlenia. |
| [Powłoka](../../ide/reference/shell-command.md) | Uruchamia programy z poziomu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] AS, gdy polecenie zostało wykonane z wiersza polecenia. |
| [ShowWebBrowser — — polecenie](../../ide/reference/showwebbrowser-command.md) | Wyświetla adres URL określony w oknie przeglądarki sieci Web w zintegrowanym środowisku programistycznym (IDE) lub zewnętrznym z IDE. |
| [Początek](../../ide/reference/start-command.md) | Rozpoczyna proces debugowania i pozwala określić, jak błędy są obsługiwane. |
| [Ścieżka](../../ide/reference/symbol-path-command.md) | Ustawia listę katalogów dla debugera do wyszukiwania symboli. |
| [Przełącz punkt przerwania](../../ide/reference/toggle-breakpoint-command.md) | Włącza lub wyłącza punkt przerwania w zależności od bieżącego stanu w bieżącej lokalizacji pliku. |
| [Watch — polecenie](../../ide/reference/watch-command.md) | Tworzy i otwiera określone wystąpienie okna **czujka** . |

## <a name="see-also"></a>Zobacz także

- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
