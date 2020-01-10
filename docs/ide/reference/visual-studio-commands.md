---
title: Polecenia
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
ms.openlocfilehash: ac0284ce274791f21c9c0f85d265d92a7097cb09
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596375"
---
# <a name="visual-studio-commands"></a>Visual Studio — Polecenia

Polecenia programu Visual Studio można wprowadzać w oknie **poleceń** , oknie **bezpośrednim** lub w polu **Znajdź/polecenie** . W każdym przypadku znak większości (`>`) wskazuje, że polecenie zamiast operacji wyszukiwania lub debugowania następuje poniżej.

Pełną listę poleceń i ich składnię można znaleźć na stronie **Klawiatura** w obszarze **narzędzia** > **Opcje** > **środowisku**.

W zlokalizowanych wersjach środowiska IDE można wprowadzać nazwy poleceń w języku macierzystym środowiska IDE lub w języku angielskim. Na przykład można wpisać `File.NewFile` lub `Fichier.NouveauFichier` w francuskim środowisku IDE, aby wykonać to samo polecenie.

Wiele poleceń ma aliasy. Aby uzyskać listę aliasów poleceń, zobacz [Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md). Aby zapoznać się z skrótami klawiaturowymi poleceń, zobacz [domyślne skróty klawiaturowe w programie Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md).

## <a name="escape-character"></a>Znak ucieczki

Znak ucieczki dla poleceń programu Visual Studio jest karetką (^). Znak ucieczki oznacza, że znak bezpośrednio po nim jest interpretowany dosłownie, a nie jako znak kontrolny. Może to służyć do osadzania prostych znaków cudzysłowu ("), spacji, ukośników wiodących, daszków lub innych znaków literałowych w wartości parametru lub przełącznika, z wyjątkiem nazw przełączników. Na przykład:

```
>Edit.Find ^^t /regex
```

Daszek działa tak samo, czy wewnątrz lub poza znaki cudzysłowu. Jeśli karetka jest ostatnim znakiem w wierszu, zostanie zignorowana.

## <a name="commands-with-arguments"></a>Polecenia z argumentami

Następujące polecenia przyjmują argumenty lub przełączniki:

| Nazwa polecenia | Opis |
| - | - |
| [Dodaj istniejący element](../../ide/reference/add-existing-item-command.md) | Dodaje istniejący plik do bieżącego rozwiązania i otwiera go. |
| [Dodaj istniejący projekt](../../ide/reference/add-existing-project-command.md) | Dodaje istniejący projekt do bieżącego rozwiązania. |
| [Dodaj nowy element](../../ide/reference/add-new-item-command.md) | Dodaje nowy element rozwiązania, takie jak .htm, CSS, txt lub zestaw ramek do bieżącego rozwiązania i otwiera go. |
| [Użyj](../../ide/reference/alias-command.md) | Tworzy nowy alias dla kompletnego polecenia, kompletne polecenie i argumenty lub nawet inny alias. |
| [Oceń instrukcję](../../ide/reference/evaluate-statement-command.md) | Oblicza i wyświetla daną instrukcję. |
| [Wyświetlić](../../ide/reference/find-command.md) | Przeszukuje pliki za pomocą podzestawu opcji dostępnych w kontrolce **Znajdowanie i zamienianie** . |
| [Znajdź w plikach](../../ide/reference/find-in-files-command.md) | Przeszukuje pliki za pomocą podzestawu opcji dostępnych na stronie [Znajdź w plikach](../../ide/find-in-files.md). |
| [Przejdź do](../../ide/reference/go-to-command.md) | Przenosi kursor do określonego wiersza. |
| [Wyświetl stos wywołań](../../ide/reference/list-call-stack-command.md) | Wyświetla bieżący stos wywołań. |
| [Demontaż listy](../../ide/reference/list-disassembly-command.md) | Rozpoczyna proces debugowania i pozwala określić sposób obsługi błędów. |
| [Wyświetl pamięć](../../ide/reference/list-memory-command.md) | Wyświetla zawartość określonego zakresu pamięci. |
| [Lista modułów](../../ide/reference/list-modules-command.md) | Wyświetla listę modułów dla bieżącego procesu. |
| [Lista rejestrów](../../ide/reference/list-registers-command.md) | Wyświetla listę rejestrów. |
| [Źródło listy](../../ide/reference/list-source-command.md) | Wyświetla określone linie kodu źródłowego. |
| [Wyświetl wątki](../../ide/reference/list-threads-command.md) | Wyświetla listę wątków w bieżącym programem. |
| [Dane wyjściowe okna polecenia dziennika](../../ide/reference/log-command-window-output-command.md) | Kopiuje wszystkie wejścia i wyjścia z okna polecenia do pliku. |
| [Nowy plik](../../ide/reference/new-file-command.md) | Tworzy nowy plik i dodaje go do aktualnie wybranego projektu. |
| [Otwórz plik](../../ide/reference/open-file-command.md) | Otwiera istniejący plik i pozwala na określenie edytora. |
| [Otwórz projekt](../../ide/reference/open-project-command.md) | Otwiera istniejący projekt i pozwala na dodawanie projektu do bieżącego rozwiązania. |
| [Drukowany](../../ide/reference/print-command.md) | Oblicza wyrażenie i wyświetla wyniki lub określony tekst. |
| [Szybka czujka, polecenie](../../ide/reference/quick-watch-command.md) | Wyświetla wybrany lub określony tekst w polu **wyrażenie** w oknie dialogowym **szybkie czujka** . |
| [Stępować](../../ide/reference/replace-command.md) | Zamienia tekst w plikach za pomocą podzestawu opcji dostępnych w kontrolce **Znajdowanie i zamienianie** . |
| [Zastąp w plikach](../../ide/reference/replace-in-files-command.md) | Zamienia tekst w plikach za pomocą podzestawu opcji dostępnych w [Zamień w plikach](../../ide/replace-in-files.md). |
| [Ustaw bieżącą ramkę stosu](../../ide/reference/set-current-stack-frame-command.md) | Umożliwia wyświetlenie ramki określonego stosu. |
| [Ustaw bieżący wątek](../../ide/reference/set-current-thread-command.md) | Umożliwia wyświetlenie określonego wątku. |
| [Ustaw podstawy](../../ide/reference/set-radix-command.md) | Określa liczbę bajtów do wyświetlenia. |
| [Powłoka](../../ide/reference/shell-command.md) | Uruchamia programy z poziomu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tak, jakby polecenie zostało wykonane z wiersza polecenia. |
| [ShowWebBrowser, polecenie](../../ide/reference/showwebbrowser-command.md) | Wyświetla adres URL w oknie przeglądarki sieci web w ramach zintegrowanego środowiska programistycznego (IDE) lub zewnętrznego dla IDE. |
| [Start](../../ide/reference/start-command.md) | Rozpoczyna proces debugowania i pozwala określić sposób obsługi błędów. |
| [Ścieżka](../../ide/reference/symbol-path-command.md) | Określa listę katalogów do wyszukiwania symboli w debugerze. |
| [Przełącz punkt przerwania](../../ide/reference/toggle-breakpoint-command.md) | Włącza punkt przerwania lub wyłączyć, w zależności od bieżącego stanu w bieżącej lokalizacji w pliku. |
| [Czujka, polecenie](../../ide/reference/watch-command.md) | Tworzy i otwiera określone wystąpienie okna **czujka** . |

## <a name="see-also"></a>Zobacz także

- [okno Polecenie](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
