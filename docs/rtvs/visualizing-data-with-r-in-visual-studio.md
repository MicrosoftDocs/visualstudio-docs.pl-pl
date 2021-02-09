---
title: Wizualizowanie danych za pomocą języka R
description: Jak wykreślić dane z programów R w programie Visual Studio przy użyciu okien wykresów.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 64b5ac36edf6c5f506628f9af88ba36bd62c71c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851832"
---
# <a name="create-visual-data-plots-with-r"></a>Tworzenie wykresów danych wizualnych za pomocą języka R

Wykreślanie jest kluczową częścią przepływu pracy analityka danych. W R Tools for Visual Studio (RTVS) wszystkie Wykreślanie centrów aktywności wokół jednego lub kilku okien kreolenia, które zostały zaprojektowane w celu zwiększenia produktywności przy użyciu tego klucza działania.

![Kreślenie obrazu Hero](media/plotting-hero-image.png)

:::row:::
    :::column:::
        ![ikona aparatu filmu wideo](../install/media/video-icon.png "Obejrzyj film")
    :::column-end:::
    :::column:::
        [Obejrzyj film wideo (YouTube.com)](https://www.youtube.com/watch?v=ZTbKmz5RSgY) na Wykreślanie przy użyciu języka R (2 mln 02s).
    :::column-end:::
:::row-end:::

## <a name="the-plot-window"></a>Okno wykresu

Okno wykresu zawiera serię wykresów, w których poszczególne wykresy są generowane przez `plot` polecenie. Na przykład za pomocą `plot(1:100)` tworzenia nowego okna wykresu, jeśli jest ono jeszcze niedostępne:

![od 1 do 100 liniowego wykresu](media/plotting-1-to-100.png)

Mówiąc technicznie, `plot` polecenia języka r renderują dane wyjściowe do urządzenia graficznego języka r; w oknie wykresu są renderowane zawartość urządzenia grafiki r, co oznacza, że każde okno wykresu otrzymuje numer urządzenia.

Okna wykresów są niezależne od projektów programu Visual Studio i pozostają otwarte podczas ładowania i zamykania projektów.

Generowanie wykresu jest przy użyciu okna kreślenia "aktywne", co umożliwia zapisanie wszystkich poprzednich wykresów w historii wykresów (zobacz [historia kreślenia](#plot-history)). Na przykład wprowadź, `plot(100:1)` a pierwszy wykres jest zastępowany linią z dołu.

Podobnie jak w przypadku wszystkich innych okien programu Visual Studio. okno wykresu obsługuje niestandardowe układy (zobacz [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Okna wykresów mogą być zadokowane w różnych lokalizacjach w ramce programu Visual Studio, w których rozmiar jest zmieniany w ramach tej ramki lub całkowicie wyciągnięcie z ramki do niezależnej zmiany rozmiaru.

Zmiana rozmiarów okna wykresu zawsze powoduje ponowne renderowanie wykresu w celu zapewnienia najlepszej jakości obrazu. Zazwyczaj chcesz zmienić rozmiar wykresu przed wyeksportowaniem wykresu do pliku lub do schowka przy użyciu poleceń opisanych w następnej sekcji.

## <a name="plot-window-commands"></a>Polecenia okna wykresu

Pasek narzędzi okna wykresu zawiera odpowiednie polecenia, z których większość jest również dostępna w menu wykresy **Narzędzia R Tools**  >   .

| Przycisk | Polecenie | Opis |
| --- | --- | --- |
| ![Przycisk nowego okna wykresu](media/plotting-toolbar-01-new-plot-window.png) | Nowe okno wykresu | Tworzy osobne okno kreślenia z własną historią. Zobacz [wiele okien wykresów](#multiple-plot-windows). |
| ![Aktywuj przycisk okna kreślenia](media/plotting-toolbar-02-activate-plot-window.png) | Aktywuj okno wykresu | Ustawia bieżące okno wykresu jako aktywne okno, tak aby kolejne `plot` polecenia były renderowane do tego okna. Zobacz [wiele okien wykresów](#multiple-plot-windows). Zobacz [wiele okien wykresów](#multiple-plot-windows). |
| ![Przycisk okna historii kreślenia](media/plotting-toolbar-03-plot-history.png) | Okno historii kreślenia | Otwiera okno ze wszystkimi wykresami w historii pokazywanych jako miniatury. Zobacz [historię wykresów](#plot-history). |
| ![Przyciski historii kreślenia](media/plotting-toolbar-04-plot-history-arrows.png) | Poprzedni/następny wykres |  Przechodzi do poprzedniego lub następnego wykresu w historii. Możesz również przejść do historii przy użyciu kombinacji klawiszy CTRL + ALT + F11 (Previous) i Ctrl + Alt + F12 (dalej). Zobacz [historię wykresów](#plot-history). |
| ![Przycisk Zapisz jako obraz](media/plotting-toolbar-05-save-as-image.png)| Zapisz jako obraz | Wyświetli wiersz polecenia i zapisuje bieżącą powierzchnię (zawartość okna, w rozmiarze okna) do pliku obrazu. Dostępne formaty to `.png` , `.jpg` , `.bmp` , i `.tif` . |
| ![Przycisk Zapisz jako PDF](media/plotting-toolbar-06-save-as-pdf.png)| Zapisz jako plik PDF | Zapisuje bieżącą powierzchnię do pliku PDF przy użyciu bieżącego rozmiaru okna. Wykres będzie odtwarzany po przeskalowaniu pliku PDF. |
| ![Przycisk kopiowania jako mapy bitowej](media/plotting-toolbar-07-copy-as-bitmap.png)| Kopiuj jako mapę bitową | Kopiuje wykres do Schowka w postaci mapy bitowej rastrowej przy użyciu bieżącego rozmiaru okna. |
| ![Kopiuj jako przycisk metapliku](media/plotting-toolbar-08-copy-as-metafile.png)| Kopiuj jako metaplik | Kopiuje wykres do Schowka jako [Metaplik systemu Windows](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipedia). |
| ![Usuń przycisk kreślenia](media/plotting-toolbar-09-remove-plot.png)| Usuń wykres | Usuwa bieżącą powierzchnię z historii. |
| ![Przycisk Wyczyść wszystkie wykresy](media/plotting-toolbar-10-clear-all-plots.png) | Wyczyść wszystkie wykresy | Usuwa wszystkie wykresy z historii (monituje o potwierdzenie). |

## <a name="multiple-plot-windows"></a>Okna wielu wykresów

Ponieważ analityki danych często pracują z wieloma wykresami z wielu różnych zestawów danych, RTVS pozwala utworzyć dowolną liczbę niezależnych okien wykresów. Następnie można rozmieścić te okna w ramce programu Visual Studio lub poza tą ramką. (Zobacz [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) , aby uzyskać ogólne informacje na temat dokowania i zmiany rozmiarów okien).

Nowe okno wykresu można utworzyć za pomocą przycisku paska narzędzi lub **Narzędzia R Tools**  >    >  . Nowe okno wykresu zostanie *uaktywnione w aktywnym* oknie, w którym są renderowane nowe wykresy. Aby zmienić aktywne okno, przejdź do niego i wybierz przycisk paska narzędzi **Aktywuj okno** wykresu lub **Narzędzia R Tools**  >  **wykresy**  >  **Aktywuj okno**.

Wykresy są również obiektami niezależnymi, co oznacza, że można je skopiować lub przenieść między oknami kreolenia przy użyciu przeciągania i upuszczania za pomocą myszy albo za pomocą poleceń **kopiowania**, **wycinania** i **wklejania** w kontekście prawym przyciskiem myszy i w menu **Edycja** .

Domyślne zachowanie funkcji przeciągania i upuszczania to Copy; Aby przenieść, przeciągnij i upuść podczas naciskania klawisza **SHIFT** .

## <a name="plot-history"></a>Historia wykresów

Polecenia kreolenia są utrzymywane w historii wykresu dla każdego okna, co gwarantuje, że wszystkie wykresy w ramach sesji są zachowywane. Aby nawigować do historii, użyj przycisków strzałek na pasku narzędzi okna kreślenia lub **Ctrl** + **Alt** + **F11** i **Ctrl** + **Alt** + **F12**. Możesz również usunąć pojedyncze wykresy lub wyczyścić wszystkie wykresy z okna przy użyciu przycisków paska narzędzi lub poleceń menu **Narzędzia R Tools**  >   .

Aby wyświetlić całą kolekcję wykresów, Otwórz okno Historia kreślenia przy użyciu przycisku paska narzędzi lub wykresu **Narzędzia R** w  >    >  **oknie Historia wykresów**.
Historia zawiera listę miniatur dla wykresów, które zostały wyświetlone w tym oknie, pogrupowane według różnych okien wykresów (lub urządzeń). Za pomocą przycisków powiększenia na pasku narzędzi zmienia rozmiar miniatur.

![Okno historii kreślenia](media/plotting-plot-history-window.png)

Aby otworzyć wykres w skojarzonym oknie, kliknij dwukrotnie ten wykres, zaznacz go, a następnie wybierz przycisk paska narzędzi **Pokaż wykres** . Alternatywnie kliknij prawym przyciskiem myszy wykres i wybierz pozycję **Pokaż wykres**. Możesz również wybrać pojedynczy wykres i skopiować, wyciąć lub usunąć z menu kontekstowego lub **edycji** .

Okres istnienia historii kreślenia w całym systemie Windows jest powiązany z okresem istnienia interaktywnej sesji języka R. W przypadku zresetowania sesji języka R lub zamknięcia i ponownego uruchomienia programu Visual Studio historia wykresów zostanie zresetowana.

## <a name="programmatically-manipulate-plot-windows"></a>Programowe manipulowanie oknami wykresów

Można programistycznie manipulować oknami z kodem R przy użyciu numerów urządzeń w celu identyfikowania określonych okien wykresów.

- `dev.list()`: Wyświetla listę wszystkich urządzeń graficznych w bieżącej sesji języka R.
- `dev.new()`: Utwórz nowe urządzenie graficzne (nowe okno wykresu).
- `dev.set(<device number>)`: Ustawianie aktywnego urządzenia graficznego.
- `dev.off()`: Usuwanie aktywnego urządzenia.
