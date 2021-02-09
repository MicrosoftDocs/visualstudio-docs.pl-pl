---
title: Interaktywny REPL dla języka R
description: Jak używać środowiska REPL Interactive dla programu R Visual Studio, który jest zintegrowany z oknami edytora.
ms.date: 06/28/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 0355f1017bb661b4f72325fb74f60653f69cd182
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878190"
---
# <a name="work-with-the-r-interactive-window"></a>Korzystanie z okna interaktywnego języka R

R Tools for Visual Studio (RTVS) zapewnia okno interaktywne języka R, znane także jako okno **REPL** (do odczytu-szacowania-Print-pętla), w którym można wprowadzić kod R i natychmiast zobaczyć wyniki. Wszystkie moduły, składnia i zmienne, a także IntelliSense, są dostępne w oknie interaktywnym.

Okno interaktywne jest również zintegrowane z regularnymi oknami edytorów języka R. Możesz wybrać kod i nacisnąć klawisz **Ctrl** + lub kliknąć prawym przyciskiem myszy i wybrać polecenie **wykonaj w trybie interaktywnym**, a kod jest uruchamiany wiersz po wierszu w oknie interaktywnym, tak jakby był on pisany bezpośrednio. Gdy kursor znajduje się w pojedynczym wierszu okna edytora, **klawisz Ctrl** + **Enter** wysyła ten wiersz do okna interaktywnego, a następnie przenosi kursor do następnego wiersza. W ten sposób można po prostu nacisnąć klawisz **Ctrl**, +  aby przejść przez kod.

Aby obsłużyć te funkcje, Skorzystaj z przewodnika [wprowadzenie do języka R](getting-started-with-r.md) , a także sekcji w tym artykule. [Fragmenty kodu](code-snippets-for-r.md) działają również w oknie interaktywnym, tak jak w oknach edytorów języka R.

## <a name="overview-of-the-interactive-window"></a>Przegląd okna interaktywnego

Wpisanie prawidłowego kodu R i naciśnięcie klawisza **Enter** na końcu wiersza powoduje uruchomienie kodu w tym wierszu:

```repl
> 3 + 3
[1] 6
```

Naciśnięcie klawisza **Enter** w dowolnym miejscu na wejściu w pojedynczej linii spowoduje również uruchomienie tego wiersza.

Wszystkie poprzednie dane wejściowe i wyjściowe w REPL są tylko do odczytu i nie można ich zmienić. Można jednak w dowolnym momencie zaznaczyć i skopiować tekst z okna, a także wkleić go. Wklejony kod działa tak, jakby był wprowadzany wiersz po wierszu.

Oznacza to, że po rozpoczęciu wpisywania instrukcji i naciśnięciu klawisza **Enter**, RTVS wie, gdy instrukcja musi być kontynuowana i przechodzi do trybu wielowierszowego z monitem + po lewej stronie i odpowiednim wcięciem. RTVS również uzupełnia nawiasy, nawiasy i nawiasy klamrowe:

![Wpis instrukcji wielowierszowej w oknie interaktywnym](media/repl-multiline-entry.png)

W tym trybie wielowierszowym klawisz **Enter** uruchamia blok kodu tylko wtedy, gdy jest umieszczony na końcu bloku. w przeciwnym razie wstawia nowy wiersz. Można jednak nacisnąć klawisz **Ctrl** +  w dowolnym miejscu, aby natychmiast uruchomić ten blok kodu.

### <a name="toolbar-commands"></a>Polecenia paska narzędzi

Oto okno interaktywne z paskiem narzędzi:

![Okno interaktywne z paskiem narzędzi](media/repl-window.png)

Polecenia paska narzędzi są następujące, z których większość są odpowiednikami klawiaturowymi i są również dostępne w   >   menu podfolderów środowiska r Tools i **Narzędzia r Tools**  >   (lub zanotowanych):

| Przycisk | Polecenie | Kombinacja klawiszy | Opis |
| --- | --- | --- | --- |
| ![Przycisk Resetuj](media/repl-toolbar-01-reset.png) | Reset | **Ctrl** + **SHIFT** + **F10** | Resetuje sesję okna interaktywnego, czyszcząc wszystkie zmienne i historię. |
| ![Przycisk Wyczyść](media/repl-toolbar-02-clear.png) | Czyste | **Ctrl** + **L** | Czyści dane wyjściowe wyświetlane w oknie interaktywnym; nie wpływa na zmienne sesji ani historię. |
| ![Przyciski historii](media/repl-toolbar-03-history.png) | Poprzednia historia — polecenie<br/>Następne polecenie historii | W **górę**, **w dół**<br/>**Alt** + W **górę**, **Alt** + **w dół** | Przewija historię za pomocą pewnych zachowań dla bloków kodu wielowierszowego. Zobacz [historię](#history). |
| ![Przycisk Załaduj obszar roboczy](media/repl-toolbar-04-load-workspace.png) | Załaduj obszar roboczy | n/d | Ładuje poprzedni zapisany obszar roboczy (zobacz [obszary robocze i sesje](#workspaces-and-sessions)). |
| ![Zapisz obszar roboczy jako przycisk](media/repl-toolbar-05-save-workspace-as.png)| Zapisz obszar roboczy jako | n/d | Zapisuje bieżący stan sesji jako obszar roboczy (zobacz [obszary robocze i sesje](#workspaces-and-sessions). |
| ![Przycisk skryptu ze źródłem języka R](media/repl-toolbar-06-source-r-script.png) | Źródłowy skrypt języka R | **Ctrl** + **SHIFT** + **S** | Wywołuje `source` obecnie aktywny skrypt języka R w edytorze programu Visual Studio, w którym jest uruchamiany kod.  Ten przycisk jest wyświetlany tylko wtedy, gdy plik R jest otwarty w edytorze programu Visual Studio. |
| ![Źródłowy skrypt języka R z przyciskiem echo](media/repl-toolbar-07-source-r-script-with-echo.png) | Źródłowy skrypt języka R z echo | **Ctrl** + **SHIFT** + **Wprowadź** | Taki sam jak źródłowy skrypt języka R, ale wyświetla zawartość skryptu w oknie interaktywnym. |
| ![Przycisk przerwania R](media/repl-toolbar-08-interrupt-r.png)| Przerwij działanie języka R | **Esc** | Powoduje zatrzymanie dowolnego uruchomionego kodu w oknie interaktywnym, na przykład `while` Pętla na zrzutie ekranu na początku tej sekcji. |
| ![Przycisk Dołącz debuger](media/repl-toolbar-09b-attach-debugger.png)| Dołącz debuger | n/d | Dostępne również przy użyciu polecenia **Debuguj**  >  **Dołącz do R Interactive** . |
| ![Przycisk Ustaw katalog roboczy na lokalizację pliku źródłowego](media/repl-toolbar-10-set-working-directory-source.png)| Ustaw katalog roboczy na lokalizację pliku źródłowego | **Ctrl** + **SHIFT** + **E** | Ustawia katalog roboczy na ostatnio załączony plik załadowany do okna interaktywnego (przy użyciu `source` ). Zobacz [katalog roboczy](#working-directory). |
| ![Przycisk Ustaw katalog roboczy na lokalizację projektu](media/repl-toolbar-11-set-working-directory-to-project.png) | Ustaw katalog roboczy na lokalizację projektu | **Ctrl** + **SHIFT** + **P** | Ustawia katalog roboczy na katalog główny aktualnie załadowanego projektu w programie Visual Studio. Zobacz [katalog roboczy](#working-directory). |
| (Pole tekstowe) | Wybierz katalog roboczy | n/d | Pole wejściowe bezpośredniego dla katalogu roboczego. Zobacz [katalog roboczy](#working-directory). |

## <a name="workspaces-and-sessions"></a>Obszary robocze i sesje

Uruchomienie kodu w oknie interaktywnym kompiluje kontekst w bieżącej sesji. Kontekst składa się z zmiennych globalnych, definicji funkcji, obciążeń biblioteki i tak dalej. Ten kontekst jest zbiorczo nazywany *obszarem roboczym* i można w dowolnym momencie zapisywać i ładować obszary robocze.

Wybranie przycisku **Zapisz obszar roboczy jako** lub użycie obszaru roboczego zapisywania sesji **narzędzi R Tools**  >    >  **jako** polecenia powoduje wybranie lokalizacji i nazwy pliku (rozszerzenie domyślne to *. RData*).

Aby zapisać obszar roboczy przy użyciu określonej nazwy pliku (wartość domyślna to *. RData*) kliknij przycisk **Zapisz obszar roboczy** w REPL:

Aby ponownie załadować wcześniej zapisany obszar roboczy, wybierz przycisk **Załaduj obszar roboczy** lub użyj obszaru roboczego ładowanie sesji **Narzędzia R Tools**  >    >   i przejdź do pliku obszaru roboczego.

Przycisk **Reset** lub resetowanie sesji **Narzędzia R Tools**  >    >   czyści kontekst sesji. Jeśli używasz sesji zdalnej, resetowanie spowoduje również usunięcie profilu użytkownika na maszynie zdalnej w celu wyczyszczenia wszystkich przechowywanych tam plików. (Zobacz [obszary robocze](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers)).

## <a name="working-directory"></a>Katalog roboczy

Deweloperzy zwykle chcą zmienić swój katalog roboczy w sesji interaktywnej. Różne polecenia dostępne na pasku narzędzi,   >  menu **katalog roboczy** narzędzia R i menu kontekstowe projektu umożliwiają łatwą konfigurację katalogu roboczego w lokalizacji pliku źródłowego, lokalizacji lub projektu lub dowolnej innej lokalizacji. Dzięki temu można uniknąć wpisywania pełnych nazw ścieżek lub długich względnych nazw ścieżek podczas odwoływania się do plików.

## <a name="history"></a>Historia

Każdy wiersz wprowadzony w oknie interaktywnym zawiera wiersze wysyłane z edytora, które są zachowywane w historii REPL. Następnie możesz przejść przez historię za pomocą klawiszy strzałek w górę i w dół, ponieważ najkorzystniej wiesz, że w wierszu polecenia.

Różnica polega na tym, że po rozpoczęciu wpisywania w bieżącym wierszu i naciśnięciu klawisza. bieżący wiersz jest zachowywany w historii, nawet jeśli nie uruchomiono jeszcze tego wiersza.

Historia w oknie interaktywnym działa również inteligentnie przy użyciu instrukcji innych bloków kodu, które rozciągają się na wiersze. Podczas przechodzenia przez historię za pomocą klawiszy strzałek w górę i w dół, bloki kodu wielowierszowego są pobierane jako całość i wyświetlane jako bieżący wpis. W tym momencie klawisze strzałek przechodźą w ten blok kodu linia po wierszu, aż do osiągnięcia górnej lub dolnej krawędzi. W górnej części bloku kodu Strzałka w górę pobiera poprzedni element w historii; w dolnej linii Strzałka w dół pobiera następny element.

Takie zachowanie uwzględnia typowy przypadek ponownego uruchomienia ostatniego elementu w historii przy użyciu strzałki w górę i klawisza **Enter** , a jednocześnie pozwala na edytowanie wielowierszowego bloku kodu przez wciśnięcie strzałki w górę, aby przejść do niego.

Aby uniknąć przechodzenia do bloków kodu wielowierszowego, użyj przycisków paska narzędzi lub **Alt** +  i **Alt** - **w dół**, a wszystkie takie bloki są traktowane jako jeden wiersz.

Najprostszym sposobem na korzystanie z funkcji historii jest wypróbowanie ich w oknie interaktywnym. Poniższy kod zawiera kilka odpowiednich instrukcji pojedynczych i wielowierszowych. Należy jednak użyć kopiowania i wklejania osobno dla każdej instrukcji, aby utworzyć odpowiednią historię. (Można także wkleić kod do oddzielnego pliku kodu, a następnie wysłać linie do okna interaktywnego za pomocą **klawisza Ctrl** + **Wprowadź**.)

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```