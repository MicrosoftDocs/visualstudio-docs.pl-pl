---
title: Wizualizowanie danych przy użyciu języka R
description: Jak dane z programów języka R w programie Visual Studio przy użyciu systemu windows kreślenia wykresu.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: a48ad7800f8ea2b992e848cfbf6b4fdac99b2062
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911770"
---
# <a name="create-visual-data-plots-with-r"></a>Tworzenie wykresów danych wizualnych języka r

Plotting jest kluczowym elementem analitykiem danych przepływu pracy. W R Tools for Visual Studio (RTVS) wszystkie działania wykreślania koncentruje się wokół co najmniej jeden wykres systemu windows, które są przeznaczone do poprawienia wydajności pracy z tym działaniem klucza.

![Obraz Hero wykreślania](media/plotting-hero-image.png)

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | [Obejrzyj film wideo (w witrynie youtube.com)](https://www.youtube.com/watch?v=ZTbKmz5RSgY) na wykreślania języka r (2 m 02s). |

## <a name="the-plot-window"></a>W oknie Diagram

Okno wykres zawiera szereg powierzchni, w którym każdy diagram jest generowany przez `plot` polecenia. Na przykład za pomocą `plot(1:100)` tworzy nowe okno wykresu, jeśli jeden nie jest już dostępna:

![Wykres liniowy 1 do 100](media/plotting-1-to-100.png)

Technicznie rzecz biorąc, R `plot` polecenia renderowania swoje dane wyjściowe do urządzenia graficznego R; okno kreślenia renderuje zawartość urządzenia grafiki języka R, dlatego każde okno kreślenia otrzymuje numer urządzenia.

Wykres systemu windows są niezależne od projektów programu Visual Studio i pozostają otwarte, ponieważ ładowania i zamknąć projektów.

Generowanie wykres używa okna wykres "aktywny" Zapisywanie wszystkie poprzednie wykreślania go do wykresu historii (zobacz [wykresu historii](#plot-history)). Na przykład, wprowadź `plot(100:1)` i pierwszy wykres jest zastępowany linię w dół.

Podobnie jak inne okna programu Visual Studio. w oknie Diagram obsługuje układy niestandardowe (zobacz [dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Wykres systemu windows można zadokowane w różnych lokalizacjach w ramce programu Visual Studio, zmiany rozmiaru w tej ramce lub pobierane poza ramkę, całkowicie dla niezależnie od rozmiaru.

Ponownie zmiany rozmiaru okna diagram zawsze renderuje wykres, aby zapewnić najlepszą jakość obrazu. Zwykle Aby zmienić rozmiar wykresu przed wyeksportowaniem na powierzchni do pliku lub do Schowka, przy użyciu polecenia opisane w następnej sekcji.

## <a name="plot-window-commands"></a>Wykres okna polecenia

Pasek narzędzi okna wykres zawiera odpowiednie polecenia, a większość z nich jest również dostępna za pośrednictwem **R Tools** > **powierzchni** menu.

| Przycisk | Polecenie | Opis |
| --- | --- | --- |
| ![Przycisk okno nowy wykres](media/plotting-toolbar-01-new-plot-window.png) | Nowe okno wykresu | Tworzy okno, diagram oddzielnych z własną historią. Zobacz [wiele okien kreślenia](#multiple-plot-windows). |
| ![Uaktywnij przycisk Okno wykresu](media/plotting-toolbar-02-activate-plot-window.png) | Uaktywnij okno wykresu | Ustawia bieżące okno wykresu jako aktywne okno zatem oznacza kolejne `plot` renderowania do tego okna polecenia. Zobacz [wiele okien kreślenia](#multiple-plot-windows). Zobacz [wiele okien kreślenia](#multiple-plot-windows). |
| ![Wykres historii okna](media/plotting-toolbar-03-plot-history.png) | Wykres historii okna | Otwiera okno z wszystkich powierzchni w historii wyświetlane jako miniatury. Zobacz [wykresu historii](#plot-history). |
| ![Wykres historii przycisków](media/plotting-toolbar-04-plot-history-arrows.png) | Wykres poprzednie/dalej |  Powoduje przejście do poprzedniego lub następnego kreślenia w historii. Możesz także przejść historii za pomocą klawiszy Ctrl + Alt + F11 (wstecz) i Ctrl + Alt + F12 (dalej). Zobacz [wykresu historii](#plot-history). |
| ![Zapisz jako obraz przycisku](media/plotting-toolbar-05-save-as-image.png)| Zapisz jako obraz | Monituje o podanie nazwy pliku i zapisuje bieżący diagram (zawartość okna, w rozmiarze okna) do pliku obrazu. Dostępne formaty `.png`, `.jpg`, `.bmp`, i `.tif`. |
| ![Zapisz jako plik PDF przycisku](media/plotting-toolbar-06-save-as-pdf.png)| Zapisz jako plik PDF | Zapisuje bieżący diagram do pliku PDF, przy użyciu bieżącego rozmiaru okna. Wykres będą renderowane ponownie, jeśli plik PDF jest skalowany. |
| ![Kopiuj jako przycisk mapy bitowej](media/plotting-toolbar-07-copy-as-bitmap.png)| Kopiuj jako mapy bitowej | Kopiuje wykres do Schowka jako mapę bitową rastrowych, przy użyciu bieżącego rozmiaru okna. |
| ![Kopiuj jako przycisk metaplik](media/plotting-toolbar-08-copy-as-metafile.png)| Kopiuj jako metaplik | Kopiuje wykres do Schowka jako [metaplik Windows](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipedia). |
| ![Usuwanie przycisku Wykres](media/plotting-toolbar-09-remove-plot.png)| Odebrat diagram | Usuwa bieżący diagram z historii. |
| ![Przycisk Wyczyść wszystko powierzchni](media/plotting-toolbar-10-clear-all-plots.png) | Wyczyść wszystkie powierzchnie | Usuwa wszystkie powierzchnie z historii (monituje o potwierdzenie). |

## <a name="multiple-plot-windows"></a>Wiele okien wykres

Ponieważ analityków, którzy często pracują z wielu powierzchniach z wielu różnych zestawów danych, RTVS pozwala utworzyć dowolną liczbę kreślenia niezależnie od systemu windows. Następnie można rozmieścić tych oknach, jednak chcesz całkowicie w ramce programu Visual Studio lub na zewnątrz tej ramki. (Zobacz [dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) ogólne informacje na temat dokowanie i zmiany rozmiaru okna.)

Utwórz nowe okno wykresu za pomocą przycisku paska narzędzi lub **R Tools** > **powierzchni** > **nowe okno wykresu**. Staje się nowe okno wykresu *active* okna, czyli, gdzie mają być renderowane nowych powierzchni. Aby zmienić aktywne okno, przełącz się do niego, a następnie wybierz **Aktywuj okno wykresu** przycisku paska narzędzi lub **R Tools** > **drukuje**  >  **Uaktywnij okno kreślenia**.

Powierzchnie, zbyt, są niezależne obiektów, co oznacza, można skopiować lub przenieść je między kreślenia systemu windows za pomocą obu przeciągania i upuszczania za pomocą myszy lub za pomocą **kopiowania**, **Wytnij**, i **Wklej** polecenia w kontekście kliknij prawym przyciskiem myszy i **Edytuj** menu.

Domyślne zachowanie przeciągnij i upuść to kopia; Aby przenieść, przeciągnij i upuść przytrzymując naciśnięty **Shift** klucza.

## <a name="plot-history"></a>Wykres historii

Wykres polecenia są obsługiwane w historii wykresu dla każdego okna, zapewniając, że wszystkie Twoje kreślenia w ramach sesji jest zachowywany. Przejdź do historii, użyj przycisków strzałek na pasku narzędzi okna wykres lub **Ctrl**+**Alt**+**F11** i **Ctrl** + **Alt**+**F12**. Można również usunąć jednej powierzchni lub usuń zaznaczenie wszystkich powierzchni z okna ponownie, używając przycisków paska narzędzi lub **R Tools** > **drukuje** poleceń menu.

Aby wyświetlić całą kolekcję powierzchnie, Otwórz okno Historia wykres, korzystając z przycisku paska narzędzi lub **R Tools** > **drukuje** > **okno Historia kreślenia**.
Historia zawiera listę miniatury dla wykresów, które były wyświetlane w tym oknie, pogrupowane według różnych kreślenia systemu windows (lub urządzenia). Na pasku narzędzi, za pomocą przycisków powiększenia zmienia rozmiar miniatury.

![Wykres historii okna](media/plotting-plot-history-window.png)

Aby otworzyć wykres w jego oknie skojarzone, kliknij dwukrotnie ten wykres, zaznacz go, a następnie wybierz **Pokaż wykres** przycisku paska narzędzi lub kliknij prawym przyciskiem myszy i wybierz **Pokaż wykres**. Możesz również wybrać osoba wykres i kopiowania, wycinania lub usunięcie z kontekstu kliknij prawym przyciskiem myszy lub **Edytuj** menu.

Okres istnienia historię kreślenia we wszystkich oknach jest powiązany z okresem istnienia interaktywnych sesji języka r. Resetowanie sesji języka r. lub zamknięcia i ponownego uruchomienia programu Visual Studio historię wykresu jest resetowany.

## <a name="programmatically-manipulate-plot-windows"></a>Programowe zmienianie kreślenia systemu windows

Można programowo manipulować windows wykres z kodu języka R do identyfikowania określonych kreślenia systemu windows przy użyciu numerów urządzeń.

- `dev.list()`: Wyświetl listę wszystkich urządzeń grafiki w bieżącej sesji języka R:.
- `dev.new()`: Tworzenie nowego urządzenia grafiki (nowe okno wykresu).
- `dev.set(<device number>)`: Ustaw urządzenia grafiki aktywnej.
- `dev.off()`: Usuń aktywnych urządzeń.
