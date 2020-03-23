---
title: Interaktywny REPL dla R
description: Jak korzystać z interaktywnego środowiska REPL dla R inVisual Studio, który jest zintegrowany z oknami edytora.
ms.date: 06/28/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7109e74e858aa308b8f49e6e1e335478f801070b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62815003"
---
# <a name="work-with-the-r-interactive-window"></a>Praca z interakcyjnym oknem języka R

R Tools for Visual Studio (RTVS) udostępnia okno interaktywne języka R, znane również jako okno **REPL** (Read-Evaluate-Print-Loop), w którym można wprowadzić kod języka R i natychmiast wyświetlić wyniki. Wszystkie moduły, składnia i zmienne, a także IntelliSense, jest dostępna w oknie interaktywnym.

Interaktywne okno jest również zintegrowane ze zwykłymi oknami edytora R. Można wybrać kod i nacisnąć **klawisze Ctrl**+**Enter**lub kliknąć prawym przyciskiem myszy i wybrać polecenie Wykonaj **w trybie interaktywnym,** a kod jest uruchamiany wiersz po wierszu w oknie interaktywnym, tak jakby wpisywał go bezpośrednio. Gdy kursor znajduje się w jednym wierszu w oknie edytora, **klawisz Ctrl**+**Enter** wysyła ten wiersz do okna interaktywnego, a następnie przenosi kursor do następnego wiersza. W ten sposób można po prostu nacisnąć **klawisz Ctrl**+**Enter** wielokrotnie, aby przejść przez kod.

Aby zapoznać się [z](getting-started-with-r.md) tymi funkcjami, wykonaj przewodnik Wprowadzenie do programu R oraz sekcje w tym artykule. [Fragmenty kodu](code-snippets-for-r.md) działają również w oknie interaktywnym, tak jak w oknach edytora Języka R.

## <a name="overview-of-the-interactive-window"></a>Omówienie okna interaktywnego

Wpisanie prawidłowego kodu R i naciśnięcie **klawisza Enter** na końcu wiersza powoduje wprowadzenie kodu w tym wierszu:

```repl
> 3 + 3
[1] 6
```

Naciśnięcie **klawisza Enter** w dowolnym miejscu na wejściu jednowierszowym powoduje również, że linia ta.

Wszystkie poprzednie wejścia i wyjścia w REPL jest tylko do odczytu i nie można zmienić. Można jednak zaznaczyć i skopiować tekst z okna w dowolnym momencie, a także wkleić. Wklejony kod jest uruchamiany tak, jakby był wprowadzany wiersz po wierszu.

Oznacza to, że po rozpoczęciu wpisywania instrukcji i naciśnięciu **klawisza Enter,** RTVS wie, kiedy instrukcja musi być kontynuowana i przechodzi w tryb wieloliniowy z monitem + po lewej stronie i odpowiednim wcięciem. RTVS uzupełnia również nawiasy, nawiasy i nawiasy klamrowe:

![Wpis instrukcji wielowierszowej w oknie interaktywnym](media/repl-multiline-entry.png)

W tym trybie wielowierszowym klawisz **Enter** uruchamia blok kodu tylko wtedy, gdy znajduje się na końcu bloku, w przeciwnym razie wstawia nowy wiersz. Można jednak nacisnąć klawisz **Ctrl**+**Enter** w dowolnej pozycji, aby natychmiast uruchomić ten blok kodu.

### <a name="toolbar-commands"></a>Polecenia paska narzędzi

Oto interaktywne okno z paskiem narzędzi:

![Okno interaktywne z paskiem narzędzi](media/repl-window.png)

Polecenia paska narzędzi są następujące, z których większość ma odpowiedniki klawiatury i są również dostępne w menu **R Tools** > **Session** i **R Tools** > **Working Directory** (lub jak wspomniano):

| Button | Polecenie | Kombinacja klawiszy | Opis |
| --- | --- | --- | --- |
| ![Przycisk Resetuj](media/repl-toolbar-01-reset.png) | Reset | **Ctrl**+**Shift**Przesunięcie+ctrl**F10** | Resetuje interaktywną sesję okna, czyszcząc wszystkie zmienne i historię. |
| ![Przycisk Wyczyść](media/repl-toolbar-02-clear.png) | Clear | **Ctrl**+**L** | Czyści dane wyjściowe wyświetlane w oknie interaktywnym; nie wpływa na zmienne sesji ani na historię. |
| ![Przyciski Historia](media/repl-toolbar-03-history.png) | Poprzednie polecenie Historia<br/>Polecenie Następna historia | **W górę**, **w dół**<br/>**Alt**+**w górę**, **Alt**+w**dół** | Przewija historię z pewnymi zachowaniami dla wielowierszowych bloków kodu. Zobacz [Historia](#history). |
| ![Przycisk Załaduj obszar roboczy](media/repl-toolbar-04-load-workspace.png) | Załaduj obszar roboczy | Nie dotyczy | Ładuje poprzedni zapisany obszar [roboczy](#workspaces-and-sessions)(zobacz Obszary robocze i sesje . |
| ![Zapisz obszar roboczy jako przycisk](media/repl-toolbar-05-save-workspace-as.png)| Zapisz obszar roboczy jako | Nie dotyczy | Zapisuje bieżący stan sesji jako obszar roboczy (zobacz [Obszary robocze i sesje](#workspaces-and-sessions). |
| ![Przycisk skryptu źródłowego R](media/repl-toolbar-06-source-r-script.png) | Skrypt źródłowy R | **Ctrl**+**Shift**Przesunięcie+Ctrl**S** | Wywołania `source` z aktualnie aktywnym skryptem języka R w edytorze programu Visual Studio, który uruchamia kod.  Ten przycisk jest wyświetlany tylko wtedy, gdy plik języka R jest otwarty w edytorze programu Visual Studio. |
| ![Skrypt źródłowy R z przyciskiem echa](media/repl-toolbar-07-source-r-script-with-echo.png) | Skrypt źródłowy R z echo | **Wprowadzanie**+**przesunięcia**+**Enter** ctrl | Tak samo jak skrypt źródłowy R, ale wyświetla zawartość skryptu w oknie interaktywnym. |
| ![Przycisk Przerwa R](media/repl-toolbar-08-interrupt-r.png)| Przerwa R | **Esc** | Zatrzymuje każdy uruchomiony kod w oknie `while` interaktywnym, na przykład pętla na zrzucie ekranu pokazuje na początku tej sekcji. |
| ![Przycisk Dołącz debuger](media/repl-toolbar-09b-attach-debugger.png)| Dołącz debuger | Nie dotyczy | Dostępne również za pomocą polecenia **Debug** > **Attach to R Interactive.** |
| ![Ustawianie przycisku lokalizacji pliku źródłowego w katalogu roboczym](media/repl-toolbar-10-set-working-directory-source.png)| Ustawianie katalogu roboczego na lokalizację pliku źródłowego | **Ctrl**+**Shift**Przesunięcie+Ctrl**E** | Ustawia katalog roboczy na ostatnio pozyskiwany plik załadowany `source`do okna interaktywnego (za pomocą ). Zobacz [Katalog roboczy](#working-directory). |
| ![Ustawianie przycisku lokalizacji projektu w katalogu roboczym](media/repl-toolbar-11-set-working-directory-to-project.png) | Ustawianie katalogu roboczego na lokalizację projektu | **Ctrl**+**Shift**Przesunięcie+ctrl**P** | Ustawia katalog roboczy do katalogu głównego aktualnie załadowanego projektu w programie Visual Studio. Zobacz [Katalog roboczy](#working-directory). |
| (Pole tekstowe) | Wybierz katalog roboczy | Nie dotyczy | Pole wprowadzania bezpośredniego dla katalogu roboczego. Zobacz [Katalog roboczy](#working-directory). |

## <a name="workspaces-and-sessions"></a>Obszary robocze i sesje

Uruchomiony kod w oknie interaktywnym tworzy kontekst w bieżącej sesji. Kontekst składa się ze zmiennych globalnych, definicji funkcji, obciążeń biblioteki i tak dalej. Ten kontekst jest zbiorczo nazywany *obszarem roboczym*i można zapisać i załadować obszary robocze w dowolnym momencie.

Wybranie przycisku **Zapisz obszar roboczy jako** lub użycie polecenia**Zapisywanie sesji** >  **R Narzędzia** > **jako** monity o lokalizację i nazwę pliku (rozszerzenie domyślne to *. RData*).

Aby zapisać obszar roboczy przy użyciu określonej nazwy pliku (wartością domyślną jest *. RData*), kliknij przycisk **Zapisz obszar roboczy** w REPL:

Aby ponownie załadować wcześniej zapisany obszar roboczy, wybierz przycisk **Załaduj obszar roboczy** lub użyj obszaru**roboczego** > R **Tools** > Session**Load Workspace** i przejdź do pliku obszaru roboczego.

Przycisk **Resetuj** lub**Resetowanie sesji** > **Reset** **narzędzi** > R czyści kontekst sesji. Jeśli używasz sesji zdalnej, resetowanie powoduje również usunięcie profilu użytkownika na komputerze zdalnym w celu usunięcia wszystkich przechowywanych tam plików. (Zobacz [Obszary robocze](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers)).)

## <a name="working-directory"></a>Katalog roboczy

Deweloperzy często chcą zmienić swój katalog roboczy podczas sesji interaktywnej. Różne polecenia dostępne na pasku narzędzi, menu katalogu **R Tools** > **Working** i menu kontekstowym projektu umożliwiają łatwe ustawienie katalogu roboczego na lokalizację pliku źródłowego, lokalizacji lub projektu lub dowolnej innej dowolnej dowolnej lokalizacji. Pomaga to uniknąć wpisywania pełnych nazwy ścieżek lub długich względnych nazwy ścieżek podczas odwoływania się do plików.

## <a name="history"></a>Historia

Każdy wiersz wprowadzony w oknie interaktywnym, zawiera wiersze wysyłane z edytora, są zachowywane w historii REPL. Następnie można poruszać się po historii za pomocą klawiszy strzałek w górę i w dół, do których prawdopodobnie jesteś przyzwyczajony w wierszu polecenia.

Jedną z różnic jest to, że jeśli zaczniesz wpisywać w bieżącym wierszu i naciśnij w górę, ta bieżąca linia zostanie zachowana w historii, nawet przez nie uruchomisz jeszcze tej linii.

Historia w oknie interaktywnym działa również inteligentnie z instrukcjami innych bloków kodu, które obejmują linie. Podczas przechodzenia przez historię za pomocą klawiszy strzałek w górę i w dół, wielowierszowe bloki kodu są pobierane jako cała jednostka i wyświetlane jako bieżący wpis. W tym momencie klawisze strzałek nawigują po tym bloku kodu wiersz po wierszu, aż do osiągnięcia górnej lub dolnej granicy. W górnej części bloku kodu strzałka w górę pobiera poprzedni element w historii; w dolnej linii, strzałka w dół pobiera następny element.

To zachowanie uwzględnia typowy przypadek ponownego uruchamiania ostatniego elementu w historii za pomocą kombinacji strzałki w górę i **klawisza Enter,** jednocześnie umożliwiając edycję bloku kodu wielowierszowego, naciskając strzałkę w górę, aby do niego przejść.

Aby uniknąć przechodzenia do wielowierszowych bloków kodu, użyj przycisków paska narzędzi lub **Alt**+**Up** i **Alt**-**Down**, a wszystkie takie bloki są traktowane jako pojedyncza linia.

Najprostszym sposobem, aby doświadczyć funkcji historii jest wypróbowanie ich dla siebie w oknie interaktywnym. Poniższy kod zawiera kilka odpowiednich instrukcji jedno- i wielowierszowych. Użyj jednak kopiowania i wklejenia z każdą instrukcją indywidualnie, aby utworzyć odpowiednią historię. (Można również wkleić kod do oddzielnego pliku kodu, a następnie wysłać wiersze do interaktywnego okna z **Ctrl**+**Enter**.)

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