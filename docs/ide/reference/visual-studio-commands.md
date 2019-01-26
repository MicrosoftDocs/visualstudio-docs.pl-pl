---
title: Polecenia
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 015cc736ca9c6c430ca0312d55ab53b58794f01b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041220"
---
# <a name="visual-studio-commands"></a>Visual Studio — Polecenia

Polecenia programu Visual Studio umożliwiają wywołanie polecenia za pomocą **polecenia** oknie **bezpośrednie** oknie lub **Find/Command** pole. W każdym przypadku znak większości (`>`) jest używany do wskazania, że polecenia zamiast operacji wyszukiwania lub debugowania jest wykonanie czynności opisanych.

Można znaleźć pełną listę polecen i ich składnię w **Keyboard, Environment Options** okno dialogowe.

Znak ucieczki dla poleceń programu Visual Studio jest znak daszka (^), co oznacza, że znak następujący bezpośrednio po nim jest interpretowany dosłownie, a nie jako znak kontrolny. Może to służyć do osadzania prostych znaków cudzysłowu ("), spacji, ukośników wiodących, daszków lub innych znaków literałowych w wartości parametru lub przełącznika, z wyjątkiem nazw przełączników. Na przykład

```
>Edit.Find ^^t /regex
```

Daszek działa tak samo, czy wewnątrz lub poza znaki cudzysłowu. Jeśli znak daszka jest ostatnim znakiem w wierszu, jest on ignorowany.

W zlokalizowanych wersjach środowiska IDE można wprowadzać nazwy poleceń w języku macierzystym środowiska IDE lub w języku angielskim. Na przykład można wpisać albo `File.NewFile` lub `Fichier.NouveauFichier` w środowisku IDE francuskim, aby wykonać to samo polecenie.

Wiele poleceń ma aliasy. Aby uzyskać listę aliasów poleceń, zobacz [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md).

Poniższe polecenia mogą mieć, argumenty i/lub przełączników.

| Nazwa polecenia | Opis |
| - | - |
| [Dodaj istniejący element](../../ide/reference/add-existing-item-command.md) | Dodaje istniejący plik do bieżącego rozwiązania i otwiera go. |
| [Dodaj istniejący projekt](../../ide/reference/add-existing-project-command.md) | Dodaje istniejący projekt do bieżącego rozwiązania. |
| [Dodaj nowy element](../../ide/reference/add-new-item-command.md) | Dodaje nowy element rozwiązania, takie jak .htm, CSS, txt lub zestaw ramek do bieżącego rozwiązania i otwiera go. |
| [Alias](../../ide/reference/alias-command.md) | Tworzy nowy alias dla kompletnego polecenia, kompletne polecenie i argumenty lub nawet inny alias. |
| [Oceń instrukcję](../../ide/reference/evaluate-statement-command.md) | Oblicza i wyświetla daną instrukcję. |
| [Znajdź](../../ide/reference/find-command.md) | Przeszukuje pliki za pomocą podzestawu opcji dostępnych w **Znajdź i Zamień** kontroli. |
| [Znajdź w plikach](../../ide/reference/find-in-files-command.md) | Przeszukuje pliki za pomocą podzestawu opcji dostępnych w [Znajdź w plikach](../../ide/find-in-files.md). |
| [Przejdź do](../../ide/reference/go-to-command.md) | Przenosi kursor do określonego wiersza. |
| [Wyświetl stos wywołań](../../ide/reference/list-call-stack-command.md) | Wyświetla bieżący stos wywołań. |
| [Wyświetl Dezasemblację](../../ide/reference/list-disassembly-command.md) | Rozpoczyna proces debugowania i pozwala określić sposób obsługi błędów. |
| [Lista pamięci](../../ide/reference/list-memory-command.md) | Wyświetla zawartość określonego zakresu pamięci. |
| [Lista modułów](../../ide/reference/list-modules-command.md) | Wyświetla listę modułów dla bieżącego procesu. |
| [Lista rejestrów](../../ide/reference/list-registers-command.md) | Wyświetla listę rejestrów. |
| [Źródło listy](../../ide/reference/list-source-command.md) | Wyświetla określone linie kodu źródłowego. |
| [Lista wątków](../../ide/reference/list-threads-command.md) | Wyświetla listę wątków w bieżącym programem. |
| [Dane wyjściowe okna polecenia dziennika](../../ide/reference/log-command-window-output-command.md) | Kopiuje wszystkie wejścia i wyjścia z okna polecenia do pliku. |
| [Nowy plik](../../ide/reference/new-file-command.md) | Tworzy nowy plik i dodaje go do aktualnie wybranego projektu. |
| [Otwórz plik](../../ide/reference/open-file-command.md) | Otwiera istniejący plik i pozwala na określenie edytora. |
| [Otwórz projekt](../../ide/reference/open-project-command.md) | Otwiera istniejący projekt i pozwala na dodawanie projektu do bieżącego rozwiązania. |
| [Drukuj](../../ide/reference/print-command.md) | Oblicza wyrażenie i wyświetla wyniki lub określony tekst. |
| [Szybka czujka, polecenie](../../ide/reference/quick-watch-command.md) | Wyświetla zaznaczony lub określony tekst w **wyrażenie** pole **Quick Watch** okno dialogowe. |
| [Zastąp](../../ide/reference/replace-command.md) | Zastępuje tekst w plikach za pomocą podzestawu opcji dostępnych w **Znajdź i Zamień** kontroli. |
| [Zastąp w plikach](../../ide/reference/replace-in-files-command.md) | Zastępuje tekst w plikach za pomocą podzestawu opcji dostępnych w [Zamień w plikach](../../ide/replace-in-files.md). |
| [Ustaw bieżącą ramkę stosu](../../ide/reference/set-current-stack-frame-command.md) | Umożliwia wyświetlenie ramki określonego stosu. |
| [Ustaw bieżący wątek](../../ide/reference/set-current-thread-command.md) | Umożliwia wyświetlenie określonego wątku. |
| [Ustawianie podstawy](../../ide/reference/set-radix-command.md) | Określa liczbę bajtów do wyświetlenia. |
| [Powłoka](../../ide/reference/shell-command.md) | Uruchamia programy z poziomu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tak, jakby polecenie zostało wykonane z wiersza polecenia. |
| [ShowWebBrowser, polecenie](../../ide/reference/showwebbrowser-command.md) | Wyświetla adres URL w oknie przeglądarki sieci web w ramach zintegrowanego środowiska programistycznego (IDE) lub zewnętrznego dla IDE. |
| [Start](../../ide/reference/start-command.md) | Rozpoczyna proces debugowania i pozwala określić sposób obsługi błędów. |
| [Path](../../ide/reference/symbol-path-command.md) | Określa listę katalogów do wyszukiwania symboli w debugerze. |
| [Przełącz punkt przerwania](../../ide/reference/toggle-breakpoint-command.md) | Włącza punkt przerwania lub wyłączyć, w zależności od bieżącego stanu w bieżącej lokalizacji w pliku. |
| [Czujka, polecenie](../../ide/reference/watch-command.md) | Tworzy i otwiera określone wystąpienie **Obejrzyj** okna. |

## <a name="see-also"></a>Zobacz też

- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)