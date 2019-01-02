---
title: Interaktywna pętla REPL dla języka R
description: Jak używać interaktywne środowisko REPL dla języka R inVisual Studio, który jest zintegrowany z okna edytora.
ms.date: 06/28/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 7df300a57120bec2fc93ec7433a7ea9fdd3a2fc8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947078"
---
# <a name="work-with-the-r-interactive-window"></a>Praca z oknie interaktywnym r.

Narzędzia R Tools for Visual Studio (RTVS) zawiera znany także jako okno interaktywne R **REPL** okna (odczyt-oceny-Print-Loop), można podać kod r. i od razu zobaczyć wyniki. Wszystkie moduły, składni i zmiennych, jak również funkcję IntelliSense, jest dostępna w oknie interaktywnym.

Okno interaktywne jest także zintegrowana z regularnych okna edytora języka R. Możesz wybrać kod i naciśnij klawisz **Ctrl**+**Enter**, lub kliknij prawym przyciskiem myszy i wybierz polecenie **Execute w Interactive**, i jest on uruchamiany wiersz po wierszu w trybie interaktywnym okna tak, jakby została wpisana bezpośrednio. Gdy kursor znajduje się w jednym wierszu w oknie edytora **Ctrl**+**Enter** wysyła tę linię do okna interaktywnego, a następnie przenosi kursor do następnego wiersza. W ten sposób można po prostu naciśnij **Ctrl**+**Enter** wielokrotnie do kroku za pośrednictwem kodu.

Aby te funkcje środowiska, postępuj zgodnie z [wprowadzenie do języka R](getting-started-with-r.md) wskazówki oraz sekcje w tym artykule. [Fragmenty kodu](code-snippets-for-r.md) również działać w oknie interaktywnym, podobnie jak w edytorze języka R w systemie windows.

## <a name="overview-of-the-interactive-window"></a>Przegląd okna interaktywnego

Wpisując prawidłowy kod R i naciskając klawisz **Enter** na końcu wiersza uruchamia kod w danym wierszu:

```repl
> 3 + 3
[1] 6
```

Naciśnięcie klawisza **Enter** dowolne miejsce na jeden wiersz danych wejściowych działa także tego wiersza.

Wszystkie poprzednie dane wejściowe i wyjściowe w rozwiązaniu REPL jest tylko do odczytu i nie można jej zmienić. Jednak można wybrać i skopiować tekst z okna w dowolnym momencie również wkleić. Wklejony kod działa tak, jakby zostały wprowadzone, wiersz po wierszu.

Oznacza to, po rozpoczęciu wpisywania instrukcji i naciśnij klawisz **Enter**, RTVS wie, kiedy należy kontynuować wykonywanie instrukcji i przejdzie do trybu wielowierszowego z + monit z lewej strony oraz właściwe wcięcia. RTVS wykonuje ponadto nawiasy, nawiasy i nawiasy klamrowe:

![Instrukcja wielowierszowe wpis w oknie interaktywnym](media/repl-multiline-entry.png)

W tym trybie wielowierszowe **Enter** klucz uruchamia blok kodu, tylko jeśli umieszczona na końcu bloku, w przeciwnym razie Wstawia nowy wiersz. Jednakże, możesz nacisnąć przycisk **Ctrl**+**Enter** na żadnej pozycji, aby uruchomić ten kod blokować natychmiast.

### <a name="toolbar-commands"></a>Polecenia paska narzędzi

Oto okna interaktywnego przy użyciu jego narzędzi:

![Okno interaktywne za pomocą paska narzędzi](media/repl-window.png)

Polecenia pasek narzędzi znajdują się w następujący sposób, z których większość mają odpowiedniki klawiatury i są również dostępne na **R Tools** > **sesji** i **R Tools**  >  **Katalog roboczy** menu (lub wspomniane):

| Przycisk | Polecenie | Kombinacja klawiszy | Opis | 
| --- | --- | --- | --- |
| ![Przycisk resetowania](media/repl-toolbar-01-reset.png) | Resetuj | **CTRL**+**Shift**+**F10** | Resetuje sesji okna interaktywnego, czyszcząc wszystkie zmienne i historię. |
| ![Przycisk Wyczyść](media/repl-toolbar-02-clear.png) | Clear | **CTRL**+**L** | Czyści wyświetlone w oknie interaktywnym; dane wyjściowe nie ma wpływu na zmienne sesji lub z historii. |
| ![Przyciski historii](media/repl-toolbar-03-history.png) | Poprzednie polecenie History<br/>Następne polecenie historii | **Się**, **w dół**<br/>**ALT**+**się**, **Alt**+**w dół** | Przewija historii, z pewnymi rodzajami zachowań dla bloków kodu wiele wierszy. Zobacz [historii](#history). |
| ![Przycisk obszaru roboczego obciążenia](media/repl-toolbar-04-load-workspace.png) | Załaduj obszar roboczy | n/d | Ładuje poprzedniej zapisano obszar roboczy (zobacz [obszarów roboczych i sesje](#workspaces-and-sessions). |
| ![Obszar roboczy przycisk Zapisz jako](media/repl-toolbar-05-save-workspace-as.png)| Zapisywanie obszaru roboczego jako | n/d | Zapisuje bieżący stan sesji jako obszaru roboczego (zobacz [obszarów roboczych i sesje](#workspaces-and-sessions). |
| ![Źródło języka R skryptu przycisku](media/repl-toolbar-06-source-r-script.png) | Source Skript R | **CTRL**+**Shift**+**S** | Wywołania `source` z aktualnie aktywnego skryptu języka R w edytorze programu Visual Studio, która uruchamia kod.  Ten przycisk jest wyświetlana tylko wtedy, gdy plik języka R jest otwarty w edytorze programu Visual Studio. | 
| ![Source skript R przycisk echo](media/repl-toolbar-07-source-r-script-with-echo.png) | Source Skript R Echo | **CTRL**+**Shift**+**wprowadź** | Ale takie same jak Source Skript R Wyświetla zawartość skryptu w oknie interaktywnym. |
| ![Przerwanie przycisk R](media/repl-toolbar-08-interrupt-r.png)| Przerwanie R | **ESC** | Zatrzymuje uruchamianie kodu w oknie interaktywnym, takich jak `while` pętli na zrzucie ekranu przedstawiono na początku tej sekcji. |
| ![Dołącz debuger przycisku](media/repl-toolbar-09b-attach-debugger.png)| Dołącz debuger | n/d | Również dostępne za pośrednictwem **debugowania** > **dołączyć do interaktywne R** polecenia. | 
| ![Ustaw katalog roboczy przycisk lokalizację pliku źródłowego](media/repl-toolbar-10-set-working-directory-source.png)| Ustawianie pracy katalogu do lokalizacji plików źródłowych | **CTRL**+**Shift**+**E** | Ustawia katalog roboczy najbardziej niedawno pochodzące z wyszukiwania pliku załadowane do okna interaktywnego (przy użyciu `source`). Zobacz [katalog roboczy](#working-directory). |
| ![Ustaw katalog roboczy na przycisk lokalizacji projektu](media/repl-toolbar-11-set-working-directory-to-project.png) | Ustawianie pracy katalogu do lokalizacji projektu | **CTRL**+**Shift**+**P** | Ustawia katalog roboczy w katalogu głównym projektu aktualnie załadowanych w programie Visual Studio. Zobacz [katalog roboczy](#working-directory). |
| (Pole tekstowe) | Wybierz pracy katalogu | n/d | Bezpośrednie pole wejściowe dla katalogu roboczego. Zobacz [katalog roboczy](#working-directory). |

## <a name="workspaces-and-sessions"></a>Obszary robocze i sesji

Uruchamianie kodu w oknie interaktywnym są gromadzone kontekstu w bieżącej sesji. Kontekst składa się ze zmiennych globalnych, definicje funkcji, biblioteka obciążeń i tak dalej. Tego kontekstu wspólnie nosi nazwę *obszaru roboczego*, możesz zapisać i załadować obszarów roboczych w dowolnym momencie. 

Wybieranie **Zapisywanie obszaru roboczego jako** przycisku lub przy użyciu **R Tools** > **sesji** > **Zapisywanie obszaru roboczego jako**polecenie wyświetli monit o podanie lokalizacji i nazwa pliku (domyślnym rozszerzeniem jest *. Dane_rekordu*).

Aby zapisać obszar roboczy przy użyciu określonej nazwy pliku (wartość domyślna to *. Dane_rekordu*), kliknij pozycję **Zapisz obszar roboczy** przycisku w rozwiązaniu REPL:

Aby ponownie załadować uprzednio zapisanego obszaru roboczego, wybierz **obciążenia roboczego** przycisku, lub użyj **R Tools** > **sesji** > **obciążenia Obszar roboczy** i przejdź do pliku.

**Resetowania** przycisk lub **R Tools** > **sesji** > **resetowania** czyści kontekstu sesji. Jeśli używasz sesji zdalnej, zresetowanie spowoduje również usunięcie profilu użytkownika na komputerze zdalnym, wyczyść Wyłącz wszystkie przechowywane pliki. (Zobacz [obszary robocze](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).)

## <a name="working-directory"></a>Katalog roboczy

Deweloperzy często chcą zmienić ich katalog roboczy znajduje się w interaktywnej sesji. Różne polecenia dostępne na pasku narzędzi **R Tools** > **katalog roboczy** menu i menu kontekstowego projektu pozwala łatwo ustawić katalogu roboczego do lokalizacji pliku źródłowego , lokalizacji lub w projekcie lub w dowolne miejsce. Pomoże uniknąć wpisywania pełne nazwy ścieżek lub długiej względnej nazwy ścieżek przy odwoływaniu się do plików.

## <a name="history"></a>Historia

Każdy wiersz w oknie interaktywnym zawiera wiersze wysyłane z edytora, zostaną zachowane w historii REPL. Następnie można przejść w historii z Up i klawiszy strzałek, ponieważ prawdopodobnie przyzwyczajeni do w wierszu polecenia.

Jedną różnicaą jest to, że jeśli zacznij pisać w bieżącym wierszu i naciśnij klawisz, że bieżący wiersz jest zachowywany w Twojej historii, nawet za pośrednictwem możesz nie jeszcze tego wiersza jeszcze uruchomione.

Historia w oknie interaktywnym działa inteligentnie instrukcji innych blok kodu, obejmujących wiele wierszy. Gdy okrągło historii z Up i klawiszy strzałek, bloki kodu wielowierszowe pobierana jako całą jednostkę i wyświetlane jako bieżący wpis. W tym momencie klawisze strzałek powodują przechodzenie za pośrednictwem tego bloku kodu wiersz po wierszu, aż do osiągnięcia top lub bottom. W górnej części bloku kodu strzałkę w górę pobiera poprzedni element w historii; w wierszu dolnej strzałkę w dół pobiera następny element.

To zachowanie uwzględniają wielkość liter Typowa ponowne uruchomienie ostatniego elementu w historii ze strzałką w górę i **Enter** klawiszy kombinacji, zapewniając naturalną do edycji blok kodu wielowierszowego, naciskając klawisz Strzałka w górę do Przejdź do niego.

Aby uniknąć, przechodząc do bloków kodu wielowierszowego, użyj przycisków paska narzędzi lub **Alt**+**się** i **Alt**-**wdół**, a wszystkie takie bloki są traktowane jako jeden wiersz.

Najprostszym sposobem funkcje historii środowiska jest wypróbować je samodzielnie w oknie interaktywnym. Poniższy kod zawiera kilka odpowiedniego wiersza jednym i wielu instrukcji. Kopiowanie i wklejanie z każdej instrukcji pojedynczo, jednak użyć do utworzenia odpowiednich historii. (Możesz również Wklej kod w osobnym pliku kodu i wysłać wiersze do okna interaktywnego z **Ctrl**+**Enter**.)

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