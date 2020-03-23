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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596375"
---
# <a name="visual-studio-commands"></a>Visual Studio — Polecenia

Polecenia programu Visual Studio można wprowadzić w oknie **Polecenia,** **Oknie bezpośrednim** lub **Znajdź/Polecenie.** W każdym przypadku większy niż`>`znak ( ) wskazuje, że polecenie, a nie operacja wyszukiwania lub debugowania, następuje.

Pełną listę poleceń i ich składni można znaleźć na stronie **Klawiatura** w**obszarze****Opcje** >  **narzędzi** > .

W zlokalizowanych wersjach IDE nazwy poleceń można wprowadzać w języku macierzystym IDE lub w języku angielskim. Na przykład można wpisać jeden `File.NewFile` lub `Fichier.NouveauFichier` w języku francuskim IDE, aby wykonać to samo polecenie.

Wiele poleceń ma aliasy. Aby uzyskać listę aliasów poleceń, zobacz [Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md). Aby zapoznać się ze skrótami klawiaturowymi poleceń, zobacz [Domyślne skróty klawiaturowe w programie Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md).

## <a name="escape-character"></a>Znak ucieczki

Znakiem ucieczki dla poleceń programu Visual Studio jest cieszka (^). Znak ucieczki oznacza, że znak bezpośrednio po nim jest interpretowany dosłownie, a nie jako znak kontrolny. Może to służyć do osadzania prostych cudzysłowów ("), spacji, ukośników wiodących, pasków dołek lub innych znaków literału w wartości parametru lub przełącznika, z wyjątkiem nazw przełączników. Przykład:

```
>Edit.Find ^^t /regex
```

Czyn y pielęgnacyjny działa tak samo, niezależnie od tego, czy znajduje się wewnątrz, czy poza cudzysłowami. Jeśli ciesza jest ostatnim znakiem w wierszu, jest ignorowana.

## <a name="commands-with-arguments"></a>Polecenia z argumentami

Następujące polecenia przyjmują argumenty lub przełączniki:

| Nazwa polecenia | Opis |
| - | - |
| [Dodaj istniejący element](../../ide/reference/add-existing-item-command.md) | Dodaje istniejący plik do bieżącego rozwiązania i otwiera go. |
| [Dodaj istniejący projekt](../../ide/reference/add-existing-project-command.md) | Dodaje istniejący projekt do bieżącego rozwiązania. |
| [Dodaj nowy element](../../ide/reference/add-new-item-command.md) | Dodaje nowy element rozwiązania, taki jak .htm, css, .txt lub frameset do bieżącego rozwiązania i otwiera go. |
| [Alias](../../ide/reference/alias-command.md) | Tworzy nowy alias dla pełnego polecenia, polecenia complete i argumentów, a nawet innego aliasu. |
| [Ocena instrukcji](../../ide/reference/evaluate-statement-command.md) | Ocenia i wyświetla daną instrukcję. |
| [Znaleźć](../../ide/reference/find-command.md) | Wyszukuje pliki przy użyciu podzbioru opcji dostępnych w formancie **Znajdź i Zamień.** |
| [Znajdź w plikach](../../ide/reference/find-in-files-command.md) | Wyszukuje pliki przy użyciu podzbioru opcji dostępnych w obszarze [Znajdź w plikach](../../ide/find-in-files.md). |
| [Przejdź do](../../ide/reference/go-to-command.md) | Przenosi kursor do określonego wiersza. |
| [Stos wywołań listy](../../ide/reference/list-call-stack-command.md) | Wyświetla bieżący stos wywołań. |
| [Demontaż listy](../../ide/reference/list-disassembly-command.md) | Rozpoczyna proces debugowania i pozwala określić sposób obsługi błędów. |
| [Pamięć listy](../../ide/reference/list-memory-command.md) | Wyświetla zawartość określonego zakresu pamięci. |
| [Moduły listy](../../ide/reference/list-modules-command.md) | Wyświetla listę modułów dla bieżącego procesu. |
| [Rejestry list](../../ide/reference/list-registers-command.md) | Wyświetla listę rejestrów. |
| [Źródło listy](../../ide/reference/list-source-command.md) | Wyświetla określone wiersze kodu źródłowego. |
| [Listy wątków](../../ide/reference/list-threads-command.md) | Wyświetla listę wątków w bieżącym programie. |
| [Wyjście okna polecenia dziennika](../../ide/reference/log-command-window-output-command.md) | Kopiuje wszystkie dane wejściowe i wyjściowe z okna Polecenia do pliku. |
| [Nowy plik](../../ide/reference/new-file-command.md) | Tworzy nowy plik i dodaje go do aktualnie wybranego projektu. |
| [Otwórz plik](../../ide/reference/open-file-command.md) | Otwiera istniejący plik i umożliwia określenie edytora. |
| [Otwórz projekt](../../ide/reference/open-project-command.md) | Otwiera istniejący projekt i umożliwia dodanie projektu do bieżącego rozwiązania. |
| [Drukowania](../../ide/reference/print-command.md) | Oblicza wyrażenie i wyświetla wyniki lub określony tekst. |
| [Szybka czujka — Polecenie](../../ide/reference/quick-watch-command.md) | Wyświetla zaznaczony lub określony tekst w polu **Wyrażenie** okna dialogowego **Szybki zegarek.** |
| [Zastąpić](../../ide/reference/replace-command.md) | Zastępuje tekst w plikach przy użyciu podzbioru opcji dostępnych w formancie **Znajdź i Zamień.** |
| [Zastąp w plikach](../../ide/reference/replace-in-files-command.md) | Zastępuje tekst w plikach przy użyciu podzbioru opcji dostępnych w obszarze [Zamień w plikach](../../ide/replace-in-files.md). |
| [Ustawianie bieżącej ramki stosu](../../ide/reference/set-current-stack-frame-command.md) | Umożliwia wyświetlenie określonej ramki stosu. |
| [Ustawianie bieżącego wątku](../../ide/reference/set-current-thread-command.md) | Umożliwia wyświetlenie określonego wątku. |
| [Ustaw Radixa](../../ide/reference/set-radix-command.md) | Określa liczbę bajtów do wyświetlenia. |
| [Powłoki](../../ide/reference/shell-command.md) | Uruchamia programy od [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wewnątrz, tak jakby polecenie zostało wykonane z wiersza polecenia. |
| [ShowWebBrowser — Polecenie](../../ide/reference/showwebbrowser-command.md) | Wyświetla adres URL określony w oknie przeglądarki sieci Web w zintegrowanym środowisku programistycznym (IDE) lub zewnętrznym ide. |
| [Początek](../../ide/reference/start-command.md) | Rozpoczyna proces debugowania i pozwala określić sposób obsługi błędów. |
| [Ścieżka](../../ide/reference/symbol-path-command.md) | Ustawia listę katalogów debugera do wyszukiwania symboli. |
| [Przełączanie punktu przerwania](../../ide/reference/toggle-breakpoint-command.md) | Włącza lub wyłącza punkt przerwania, w zależności od jego bieżącego stanu, w bieżącej lokalizacji w pliku. |
| [Czujka — Polecenie](../../ide/reference/watch-command.md) | Tworzy i otwiera określone wystąpienie okna **czujki.** |

## <a name="see-also"></a>Zobacz też

- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenie](../../ide/find-command-box.md)
- [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
